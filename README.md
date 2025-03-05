# Weatherify

Application météo React qui utilise l'API OpenWeatherMap pour afficher les conditions météorologiques actuelles.

## 📋 Description

Weatherify est une application web qui permet aux utilisateurs de rechercher la météo actuelle de n'importe quelle ville dans le monde. L'application fournit des informations détaillées comme la température, l'humidité, la vitesse du vent et plus encore.

## ✨ Fonctionnalités

- **Recherche par ville** - Trouvez la météo de n'importe quelle ville
- **Informations détaillées** - Température, ressenti, humidité, pression, vitesse du vent
- **Interface réactive** - Mise à jour instantanée des données météo
- **Design responsive** - S'adapte à tous les appareils

## 🛠️ Technologies utilisées

- React 18
- Vite
- Axios pour les requêtes API
- API OpenWeatherMap
- Variables d'environnement pour la sécurité des clés API

## 🧩 Structure du projet

```
weatherify/
├── src/
│   ├── components/
│   │   └── Weather.jsx       # Composant principal de météo
│   ├── assets/               # Images et ressources
│   ├── App.jsx               # Composant principal
│   ├── main.jsx              # Point d'entrée
│   ├── index.css             # Styles globaux
│   └── App.css               # Styles spécifiques à App
├── .env.sample               # Exemple de fichier d'environnement
├── index.html                # HTML principal
├── package.json              # Dépendances et scripts
└── vite.config.js            # Configuration de Vite
```

## 💻 Installation

1. Clonez ce dépôt
```bash
git clone git@github.com:techmefr/weatherify.git
cd weatherify
```

2. Installez les dépendances
```bash
npm install
```

3. Configurez votre clé API
```bash
cp .env.sample .env
# Éditez le fichier .env avec votre clé API OpenWeatherMap
```

4. Lancez l'application en mode développement
```bash
npm run dev
```

## 🔌 Configuration de l'API

Cette application utilise l'API OpenWeatherMap qui nécessite une clé API.
1. Inscrivez-vous sur [OpenWeatherMap](https://openweathermap.org/api)
2. Obtenez votre clé API gratuite
3. Ajoutez-la dans votre fichier `.env` :
```
VITE_WEATHER_API_KEY=votre_clé_api_ici
```

## 📊 Exemple de données

L'API renvoie des données météorologiques structurées comme :

```json
{
  "name": "Paris",
  "main": {
    "temp": 15.2,
    "feels_like": 14.8,
    "humidity": 76,
    "pressure": 1012
  },
  "weather": [
    {
      "description": "scattered clouds"
    }
  ],
  "wind": {
    "speed": 3.6
  }
}
```

## 🧠 Gestion des états React

Le composant principal utilise plusieurs hooks React :

```jsx
function Weather() {
  const [city, setCity] = useState("");
  const [weatherData, setWeatherData] = useState(null);
  
  // Utilisation de useEffect pour déclencher la requête API
  useEffect(() => {
    fetchData();
  }, [city]);
  
  // Fonction pour récupérer les données météo
  const fetchData = async () => {
    try {
      const response = await axios.get(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${API_KEY}`
      );
      setWeatherData(response.data);
    } catch (error) {
      console.error(error);
    }
  };
}
```

## 🚀 Déploiement

Pour construire l'application pour la production :

```bash
npm run build
```

Les fichiers générés seront disponibles dans le dossier `dist/`.

## 📝 Licence

[MIT](https://choosealicense.com/licenses/mit/)

---

Créé par [Gaëtan Compigni](https://github.com/techmefr)
