# Sample TypeScript/Express.js

Relay Chat is a simple chat application backend built with websockets. It uses the [Daytona](https://github.com/daytonaio/daytona) framework for the development environment. For the backend, I used the [Websockets](https://www.npmjs.com/package/websocket) package.

## 📦 Prerequisites

| ![TypeScript](https://skillicons.dev/icons?i=typescript) | ![Node.js](https://skillicons.dev/icons?i=nodejs) | ![Git](https://skillicons.dev/icons?i=git) | ![Docker](https://skillicons.dev/icons?i=docker) | ![Daytona](https://github.com/user-attachments/assets/b3f0d70d-8792-420e-90f4-cecaf17d993b)|
|-----------------|---------|------|--------|---------|


## 🚀 Getting Started  

### Open Using Daytona  

1. **Install Daytona**: Follow the [Daytona installation guide](https://www.daytona.io/docs/installation/installation/).  

2. **Create the Workspace**:  
   ```bash  
   daytona create https://github.com/yashksaini-coder/relay-chat-daytona
   ``` 
3. **Start the Application**:  
   ```bash  
   npm run dev
   ```  
---

## ✨ Features  
- Create a room ID with a unique 6-character code. 🔑
- Join existing chat rooms. 🚪
- List active rooms with the number of users. 📋
- Real-time chat functionality (message polling). 💬

## 📁 Project Structure

``` markdown
.
├── lib
│   ├── utils.ts      # Utility functions like generateRoomCode
│   ├── room.ts       # Room-related logic
│   ├── chat.ts       # Chat-related logic
├── src
│   ├── index.ts      # Main ts file for WebSocket server
├── package.json      # Node.js project file
├── tsconfig.json     # TypeScript configuration
└── README.md         # Project documentation
```

### 🧪 Testing:

To test the updated functionality, you can use a Postman and use the Websocket server instance. These are the messages to check the functionality:

1. **Create Room**:
   Send a message with `type: "create_room"`:

   ```json
   { "type": "create_room" }
   ```

   Response:
   ```json
   { "type": "room_created",
     "room": "ABC123"
   }
   ```

2. **Join Room**:
   Use the generated room code in the `join_room` request:
   ```json
   { "type": "join_room",
     "room": "ABC123" 
   }
   ```

3. **List Rooms**:
   ```json
   { "type": "list_rooms" }
   ```

   Response:
   ```json
   { "type": "room_list",
     "rooms": [{ "room": "ABC123", "userCount": 1 }]
   }
   ```

4. **Message**:
   Send a message with `type: "message"` to broadcast to all users in the room:
   ```json
   { "type": "message",
     "text": "Hello, everyone!"
   }
   ```
