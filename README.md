# Herb & Hearth - Premium MERN Stack Restaurant Website

This repository contains the complete MERN stack web application for **Herb & Hearth**, an artisanal, organic plant-based restaurant. The project features a premium responsive user experience and a zero-configuration database layer.

---

## 🌟 Key Features

1. **Immersive UI/UX**: Custom typography (*Playfair Display* & *Inter*), dark-moss and terracotta color branding, sticky frosted-glass headers, hover states, and smooth slide-in notification toasts.
2. **Dynamic Menu Section**: Category filters for Small Plates, Mains, Desserts, and artisanal drinks, complete with dietary badges (`VG` for Vegan, `GF` for Gluten-Free, `NF` for Nut-Free).
3. **Table Reservation System**: A reservation modal with minimum date limits, guest counts, and Greenhouse Patio / Bar Lounge seating selectors. Submits reservations directly to the API and renders a receipt ticket.
4. **Online Order Checkout**: A sliding shopping cart basket drawer that tracks quantities, calculates taxes/totals, and opens a checkout form simulator allowing users to submit pickup or delivery orders.
5. **Gourmet Recipes Blog**: A blog grid that pulls articles and recipes from the database, opening them in a modal reader.
6. **Zero-Setup Database Architecture**: Features a custom-built database layer. If `MONGO_URI` is specified in environment settings, it connects to MongoDB. Otherwise, it automatically defaults to a local JSON file database under `backend/data/`.

---

## 📁 Repository Structure

```
websi/
├── backend/
│   ├── data/                   # Fallback JSON database folder
│   ├── models/                 # Database models
│   │   ├── MenuItem.js         # Menu schemas
│   │   ├── Reservation.js      # Booking schemas
│   │   ├── Order.js            # Customer checkout orders
│   │   ├── Subscriber.js       # Email newsletter signups
│   │   └── BlogPost.js         # Articles and recipes
│   ├── routes/
│   │   └── api.js              # Express API route endpoints
│   ├── db.js                   # Mongoose / Local storage bridge
│   ├── seed.js                 # Seeder to populate initial data
│   ├── server.js               # Entry Express server file
│   ├── package.json            # Backend node packages
│   └── .env.example            # Environment variables template
├── frontend/
│   ├── dist/                   # Compiled production React build output
│   ├── public/assets/          # Product images and headers
│   ├── src/
│   │   ├── components/         # Reusable React components
│   │   │   ├── Header.jsx      # Navigation header with scroll effect
│   │   │   ├── Hero.jsx        # Premium hero banner
│   │   │   ├── OurStory.jsx    # About us roots philosophy
│   │   │   ├── Menu.jsx        # Filterable menu grid
│   │   │   ├── Blog.jsx        # Recipes and article viewer
│   │   │   ├── Footer.jsx      # Footer with newsletter form
│   │   │   ├── ReservationModal.jsx # Table booking
│   │   │   ├── CartDrawer.jsx  # Order basket and checkout simulator
│   │   │   └── Toast.jsx       # Temporary status messages
│   │   ├── App.jsx             # Top-level state coordinator
│   │   ├── index.css           # Premium vanilla CSS styling system
│   │   └── main.jsx            # Entry react bootstrap
│   ├── package.json            # React node packages
│   └── vite.config.js          # Vite config (includes API proxies)
└── README.md                   # This instruction file
```

---

## 🚀 How to Run Locally

This project includes a **portable Node.js v20.11.1** environment folder (`node-v20.11.1-win-x64`) inside the workspace. **You do not need to install Node or npm to run this application!**

### 1. Launch the Backend Server
Open your PowerShell terminal in the workspace directory and execute:
```powershell
$env:PATH = "$pwd\node-v20.11.1-win-x64;" + $env:PATH
cd backend
node server.js
```
The server will boot and display:
`🚀 Server listening on http://localhost:5000`

### 2. Launch the Frontend Dev Server (Optional)
If you want to edit code and test hot-reloading:
Open a second PowerShell terminal in the workspace and execute:
```powershell
$env:PATH = "$pwd\node-v20.11.1-win-x64;" + $env:PATH
cd frontend
npm run dev
```
Open `http://localhost:5173` in your browser. All API requests are proxied automatically to port `5000`.

*Note: The backend Express server automatically serves the compiled production files located in `frontend/dist/` on `http://localhost:5000` by default, so you can preview the fully built website directly from port 5000.*

---

## 🛢️ Connecting to MongoDB (Optional)
To use a real MongoDB server instead of the local JSON file fallback:
1. Rename `backend/.env.example` to `backend/.env`.
2. Edit `backend/.env` and update the `MONGO_URI` string to point to your local MongoDB server or a MongoDB Atlas cluster.
3. Seed the MongoDB database by running:
   ```powershell
   cd backend
   node seed.js
   ```
4. Restart the server. It will display `✅ Connected to MongoDB successfully`.
