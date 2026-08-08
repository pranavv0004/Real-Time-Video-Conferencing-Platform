# Real-Time Video Conferencing Platform

A modern, scalable video conferencing application built with Node.js, React, and Socket.IO. Enable seamless real-time video communication with authentication, meeting management, and persistent history tracking.

## 🎯 Features

- **Real-Time Video Communication** — Peer-to-peer video streaming with low-latency Socket.IO connections
- **User Authentication** — Secure registration and login with bcrypt password hashing
- **Meeting Management** — Create, join, and manage video meetings
- **Meeting History** — Track and review past meeting records
- **Responsive Design** — Mobile-friendly interface using Material-UI
- **CORS Enabled** — Secure cross-origin requests between frontend and backend
- **Token-Based Sessions** — Secure session management with cryptographic tokens

## 🛠️ Tech Stack

### Backend
- **Runtime:** Node.js with ES modules
- **Framework:** Express.js
- **Real-Time Communication:** Socket.IO
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** bcrypt for password hashing
- **Security:** CORS, dotenv for environment variables
- **Development:** Nodemon for hot-reloading

### Frontend
- **Library:** React 18
- **Build Tool:** Create React App
- **Routing:** React Router v6
- **HTTP Client:** Axios
- **UI Framework:** Material-UI (MUI) v5
- **Real-Time Client:** Socket.IO Client
- **Styling:** CSS Modules

## 📁 Project Structure

```
Real-Time-Video-Conferencing-Platform/
├── backend/
│   ├── src/
│   │   ├── app.js                 # Express server setup
│   │   ├── controllers/
│   │   │   ├── socketManager.js   # WebSocket event handlers
│   │   │   └── user.controller.js # User authentication logic
│   │   ├── models/
│   │   │   ├── user.model.js      # User schema
│   │   │   └── meeting.model.js   # Meeting schema
│   │   └── routes/
│   │       └── users.routes.js    # User endpoints
│   ├── .env.example               # Environment variables template
│   └── package.json
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── App.js                 # Main app component
│   │   ├── contexts/
│   │   │   └── AuthContext.jsx    # Authentication context
│   │   ├── pages/
│   │   │   ├── landing.jsx        # Landing page
│   │   │   ├── authentication.jsx # Login/Register
│   │   │   ├── home.jsx           # Dashboard
│   │   │   ├── history.jsx        # Meeting history
│   │   │   └── VideoMeet.jsx      # Video conference
│   │   ├── utils/
│   │   │   └── withAuth.jsx       # Route protection HOC
│   │   └── styles/
│   │       └── videoComponent.module.css
│   └── package.json
│
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- MongoDB instance (local or MongoDB Atlas)

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure environment variables:**
   - Copy `.env.example` to `.env`
   - Update the MongoDB URI with your connection string:
     ```env
     MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/dbname
     PORT=5000
     ```

4. **Start the server:**
   ```bash
   # Development with hot reload
   npm run dev

   # Production
   npm start
   ```

   The backend server will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm start
   ```

   The frontend will open at `http://localhost:3000`

## 🔐 Environment Variables

Create a `.env` file in the backend directory with the following variables:

```env
# MongoDB Connection String
MONGODB_URI=mongodb+srv://username:password@cluster0.xxxxx.mongodb.net/database

# Server Port
PORT=5000
```

**Note:** Never commit the `.env` file to version control. Use `.env.example` as a template for your team.

## 📡 API Endpoints

### Authentication Routes

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/users/register` | Register a new user |
| POST | `/api/v1/users/login` | Login user |
| GET | `/api/v1/users/history` | Get meeting history |

### WebSocket Events

- `user-joined` — Broadcast when user joins a meeting
- `user-left` — Broadcast when user leaves a meeting
- `video-signal` — Relay video stream signals
- `message` — Send real-time messages

## 🎮 Usage

1. **Register/Login:**
   - Open the application at `http://localhost:3000`
   - Navigate to the authentication page
   - Create a new account or login with existing credentials

2. **Create/Join Meeting:**
   - Go to the dashboard
   - Create a new meeting or join an existing one using the meeting ID
   - Allow camera and microphone access when prompted

3. **Video Conference:**
   - Enable/disable video and audio
   - View participant streams
   - End meeting when complete

4. **View History:**
   - Navigate to the history section
   - Review past meetings and details

## 🔒 Security Features

- **Password Hashing:** bcrypt with salt rounds
- **CORS Protection:** Whitelist allowed origins
- **Session Tokens:** Cryptographically secure token generation
- **Environment Variables:** Sensitive data stored securely
- **HTTP-Only Cookies:** Recommended for token storage

## 📦 Dependencies Overview

### Backend Dependencies
- `express` — Web framework
- `socket.io` — Real-time communication
- `mongoose` — MongoDB ODM
- `bcrypt` — Password hashing
- `cors` — Cross-origin requests
- `dotenv` — Environment variables
- `http-status` — HTTP status codes

### Frontend Dependencies
- `react` — UI library
- `react-router-dom` — Client-side routing
- `axios` — HTTP requests
- `@mui/material` — Component library
- `socket.io-client` — Real-time client
- `react-scripts` — Build tools

## 🚦 Running Both Services Simultaneously

### Option 1: Two Terminal Windows

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
```

### Option 2: Using npm-run-all (Optional)

In the root directory, create a `package.json`:
```bash
npm install -D npm-run-all
```

Then run:
```bash
npm-run-all --parallel start:backend start:frontend
```

## 🐛 Troubleshooting

### MongoDB Connection Error
- Verify your MongoDB URI is correct
- Ensure MongoDB service is running
- Check network connectivity and firewall settings

### Port Already in Use
```bash
# Windows - Kill process on port 5000
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# macOS/Linux
lsof -ti:5000 | xargs kill -9
```

### Video/Audio Not Working
- Check browser permissions for camera and microphone
- Ensure HTTPS is used in production (WebRTC requirement)
- Verify Socket.IO connection is established

## 🤝 Contributing

1. Create a feature branch: `git checkout -b feature/your-feature`
2. Commit changes: `git commit -m 'Add your feature'`
3. Push to branch: `git push origin feature/your-feature`
4. Open a pull request with a detailed description

## 📄 License

This project is licensed under the ISC License. See the LICENSE file for details.

## 👥 Authors

- **apnacollege** — Original author
- Contributors welcome!

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review the API endpoint specifications

## 🔄 Deployment

### Heroku/Cloud Deployment Considerations
- Set production environment variables
- Use PM2 for process management: `npm run prod`
- Enable HTTPS for WebRTC
- Configure CDN for media delivery
- Set up MongoDB Atlas for production database

### Docker Support (Future)
Consider containerizing the application for easier deployment.

---

**Last Updated:** August 2026  
**Version:** 1.0.0
