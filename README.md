# Odyssey

<img width="1140" height="1662" alt="image" src="https://github.com/user-attachments/assets/07143153-3fbd-467f-a0ad-197eab6ce0ab" />


Full-stack platform for discovering destinations, managing points of interest, and organizing travel experiences. The front end runs on **React + Vite**, while the backend uses **Flask + SQLAlchemy** with JWT authentication and a relational database for users, locations, and status flags (favorites/visited).

## Key features
- 🔐 **JWT authentication**: sign up, log in, and update profiles with encrypted passwords.
- 🗺️ **Destination catalog**: countries, cities, and points of interest with coordinates, descriptions, and images.
- ⭐ **Favorites and visited**: users can mark places as favorites or log them as visited.
- 🏷️ **Content tagging**: associate tags to points of interest for themed filtering and exploration.
- 🌐 **RESTful API**: clear endpoints for CRUD of users, locations, and relationships, protected by JWT when required.
- 🎨 **Responsive UI**: React Router navigation, landing hero, and a grid of popular destinations powered by the API.

## Architecture
- **Front end**: React 18 with Vite, React Router 6, FontAwesome, and custom styles in `src/front`.
- **Back end**: Flask with Blueprints, SQLAlchemy, and Flask-JWT-Extended in `src/api`.
- **Database**: PostgreSQL (recommended) with models for users, countries, cities, points of interest, images, tags, and many-to-many relationships.
- **Environment management**: variables defined in `.env` (see `.env.example`) for the database URL, Flask app key, and backend URL consumed by the front end.

## Prerequisites
- Python 3.10+
- Node.js 20+
- Pipenv
- PostgreSQL (or another engine set in `DATABASE_URL`)

## Quick setup
1. **Environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your DATABASE_URL, FLASK_APP_KEY, and VITE_BACKEND_URL
   ```

2. **Install backend dependencies**
   ```bash
   pipenv install
   ```

3. **Prepare the database**
   ```bash
   pipenv run migrate   # generate tables (if applicable)
   pipenv run upgrade   # apply migrations
   ```

4. **Start the API**
   ```bash
   pipenv run start
   ```

5. **Install and start the front end**
   ```bash
   npm install
   npm run dev  # or npm run start
   ```

## Useful scripts
- **Rollback last migration**: `pipenv run downgrade`
- **Insert test users**: `flask insert-test-users 5`
- **Front-end lint**: `npm run lint`
- **Production build (front end)**: `npm run build`

## Relevant structure
- `src/api/models.py`: SQLAlchemy models (User, Country, City, Poi, Tag, favorites/visited, and images).
- `src/api/routes.py`: authentication, catalog, and relationship endpoints (JWT protection where applicable).
- `src/front`: React app with routes (`routes.jsx`), pages, and components (jumbotron, popular-destination cards, etc.).

## Deployment
The project ships with base configs for Render (`render.yaml`, `Dockerfile.render`, `render_build.sh`) and a `Procfile` for compatible environments. Adjust environment variables and the public backend URL (`VITE_BACKEND_URL`) before publishing.

## Contributing
1. Create a branch from `main`.
2. Apply changes following existing code conventions.
3. Run checks (lint, migrations) before opening a PR.

Enjoy building new travel experiences with Odyssey!
