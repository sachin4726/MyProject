# 🎨 Skribbl.io Clone - Real-Time Backend Engine

An authoritative, event-driven game server for the Skribbl multiplayer drawing and guessing game, built with **Node.js**, **Express**, and **Socket.IO**.

---

## 👨‍💻 Author & Developer

**Sachin Kumar**  
- **GitHub:** [@sachin4726](https://github.com/sachin4726)
- **Profile:** [https://github.com/sachin4726](https://github.com/sachin4726)
- **Bio:** *Software Developer | Building useful things | Always learning*
- **Live Application:** [https://skribbl-frontend-mocha.vercel.app/](https://skribbl-frontend-mocha.vercel.app/)

---

## 🛠️ Architecture & Core Components

The backend utilizes an **Object-Oriented Programming (OOP)** architecture for state isolation, concurrency, and real-time reliability:

- **`SessionEngine`** (`src/coordinators/SessionEngine.js`):
  - Singleton room manager coordinating active session lifecycles.
  - Handles room creation, socket-to-room mappings, and global routing.

- **`GameSession`** (`src/domain/GameSession.js`):
  - Manages the turn-based game loop (Lobby, Word Picking, Drawing, Reveal, Game Over).
  - Handles player rotations, word selection from curated dictionaries, dynamic turn timers, and real-time canvas state broadcast.
  - Implements the dynamic speed-based scoring algorithm.

- **`Participant`** (`src/domain/Participant.js`):
  - Encapsulates player state (socket ID, display name, points, guessing status, drawing eligibility).

---

## ⚡ Socket.IO Event Specifications

| Event | Direction | Description |
|---|---|---|
| `create_room` | Client ➔ Server | Creates a new game room with custom settings |
| `join_room` | Client ➔ Server | Joins an existing game room with alias |
| `draw_data` | Client ➔ Server ➔ Room | Streams stroke coordinates `(x0, y0, x1, y1)` and brush settings |
| `canvas_clear` | Client ➔ Server ➔ Room | Clears canvas for all participants in room |
| `undo_canvas` | Client ➔ Server ➔ Room | Restores canvas snapshot for all players |
| `send_guess` | Client ➔ Server | Evaluates player guesses against secret target word |
| `room_update` | Server ➔ Room | Emits updated participant roster, scores, and host status |
| `game_state_changed` | Server ➔ Room | Broadcasts game phase changes and timers |

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher)
- npm

### Installation & Run

```bash
# Navigate to backend directory
cd Sachin-backend

# Install dependencies
npm install

# Start the game server
node src/main.js
# or
npm start
```

Default server port: `http://localhost:4000`

---

## 📄 License
ISC License © 2026 [Sachin Kumar](https://github.com/sachin4726)
