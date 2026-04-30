# Node.js Chat

A simple real-time chat application built with Node.js using TCP sockets. This project demonstrates basic client-server architecture for a multi-user chat system.

## Features

- **Real-time messaging**: Instant message delivery between all connected clients
- **Multi-user support**: Multiple clients can connect and chat simultaneously
- **User identification**: Each client receives a unique ID upon connection
- **Join/leave notifications**: All users are notified when someone joins or leaves the chat
- **Clean terminal interface**: Uses readline for an interactive chat experience

## Architecture

The project consists of two main components:

### Server (`server.js`)
- Creates a TCP server listening on `127.0.0.1:3008`
- Manages client connections and broadcasts messages
- Handles client disconnections gracefully
- Assigns unique IDs to each connected client

### Client (`client.js`)
- Connects to the TCP server
- Provides an interactive command-line interface for chatting
- Handles message sending and receiving
- Manages terminal output for a clean chat experience

## Installation & Setup

1. **Clone or download the project**
```bash
git clone https://github.com/vasylpryimakdev/node-js-chat.git
```

2. **Navigate to the project directory**
   ```bash
   cd chat-project
   ```

3. **Install Node.js** (if not already installed)
   - Download from [nodejs.org](https://nodejs.org/)
   - Requires Node.js version 12.0 or higher

## Usage

### Starting the Server

```bash
node server.js
```

The server will start and display:
```
opened server on { address: '127.0.0.1', family: 'IPv4', port: 3008 }
```

### Connecting Clients

Open new terminal windows and run:

```bash
node client.js
```

Each client will receive a unique ID and can start chatting immediately.

### Chat Commands

- Simply type your message and press Enter to send
- All messages are broadcast to all connected users
- Use `Ctrl+C` to disconnect from the chat

## Example Session

**Terminal 1 (Server):**
```
A new connection to the server!
A new connection to the server!
```

**Terminal 2 (Client 1):**
```
Connected to the server!
Your id is 1!

Enter a message > Hello everyone!
> User 1: Hello everyone!
> User 2: Hi there!
```

**Terminal 3 (Client 2):**
```
Connected to the server!
Your id is 2!

User 1 joined!
> User 1: Hello everyone!
Enter a message > Hi there!
```

## Technical Details

### Protocol
- Messages are sent in the format: `{id}-message-{content}`
- Server assigns client IDs in the format: `id-{clientId}`
- Broadcast messages are prefixed with `> User {id}:`

### Error Handling
- Server handles client disconnections gracefully
- Notifications are sent when users leave the chat
- Socket errors are caught and handled

### Dependencies
- **net**: Built-in Node.js module for TCP networking
- **readline**: Built-in Node.js module for command-line interface

## Learning Objectives

This project demonstrates:
- TCP socket programming in Node.js
- Client-server architecture
- Real-time communication
- Event-driven programming
- Terminal interface management
- Multi-client connection handling

## Potential Improvements

- Add user nicknames instead of numeric IDs
- Implement private messaging
- Add chat history/logging
- Create a web-based client interface
- Add authentication and user management
- Implement chat rooms/channels