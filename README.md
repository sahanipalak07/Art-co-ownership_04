# 🎨 ArtShare - Revolutionary Blockchain Art Co-Ownership

<div align="center">
  <img src="art-co-ownership-frontend/public/websitelogo.png" alt="ArtShare Logo" width="200"/>
  
  [![Built with ICP](https://img.shields.io/badge/Built%20with-Internet%20Computer-blue.svg)](https://internetcomputer.org/)
  [![React](https://img.shields.io/badge/React-18.x-61dafb.svg)](https://reactjs.org/)
  [![Rust](https://img.shields.io/badge/Rust-1.7x-orange.svg)](https://www.rust-lang.org/)
</div>

## 🌟 Overview

ArtShare revolutionizes the art market by enabling fractional ownership of digital artworks through blockchain technology. Built on the Internet Computer Protocol (ICP), our platform democratizes art investment by allowing users to:

- 🖼️ Purchase shares in valuable digital artworks
- 💱 Trade art tokens in a secure, decentralized marketplace
- 📊 Track and manage art investments in real-time
- 🎯 Participate in exclusive art offerings

## ✨ Features

### Core Functionality
- **Fractional Art Ownership**: Purchase tokens representing fractional ownership in digital artworks
- **Secure Trading**: Buy and sell ownership tokens through a decentralized marketplace
- **Artist Onboarding**: Artists can tokenize their artworks and enable fractional ownership
- **Portfolio Management**: Track your art investments and ownership percentages
- **Verification System**: Verified artists and artworks for authenticity

### Technical Features
- **Internet Computer Integration**: Built on ICP for true decentralization
- **Internet Identity Authentication**: Secure, privacy-preserving login
- **Stable Memory**: Persistent data storage across canister upgrades
- **Real-time Updates**: Live trading and ownership data
- **Responsive Design**: Works seamlessly on desktop and mobile devices

## 🏗️ Architecture

### Backend (Rust Canister)
- **Smart Contracts**: Rust-based canisters handling all business logic
- **Data Management**: Stable structures for persistent storage
- **Token Economics**: Fractional ownership token system
- **Trading Engine**: Peer-to-peer token trading functionality

### Frontend (React Application)
- **Modern UI**: Built with React, Tailwind CSS, and shadcn/ui components
- **ICP Integration**: Direct communication with backend canisters
- **Wallet Integration**: Internet Identity authentication
- **Responsive Design**: Mobile-first approach

## 🚀 Quick Start

### Prerequisites
- Node.js (v18 or higher)
- Rust (latest stable)
- dfx (Internet Computer SDK)
- pnpm (package manager)

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd art_co_ownership
   ```

2. **Install dependencies**
   ```bash
   # Install Rust dependencies
   cargo update
   
   # Install frontend dependencies
   cd art-co-ownership-frontend
   pnpm install
   cd ..
   ```

3. **Start local Internet Computer replica**
   ```bash
   dfx start --background
   ```

4. **Deploy canisters**
   ```bash
   # Deploy backend canister
   dfx deploy art_co_ownership_backend
   
   # Build and deploy frontend
   cd art-co-ownership-frontend
   pnpm run build
   cd ..
   dfx deploy art_co_ownership_frontend
   ```

5. **Access the application**
   ```bash
   # Get the frontend canister URL
   dfx canister call art_co_ownership_frontend http_request '(record{url="/"; method="GET"; body=vec{}; headers=vec{}})'
   
   # Or check the local URL
   echo "http://localhost:4943/?canisterId=$(dfx canister id art_co_ownership_frontend)"
   ```

## 🛠️ Development

### 🔧 Backend Development

The backend infrastructure is built with Rust, providing a robust and secure foundation for the platform:

#### Core Data Structures
- `ArtPiece` 🖼️
  - Manages artwork metadata and tokenization
  - Handles ownership distribution
  - Tracks artwork history and provenance

- `TokenOwnership` 🎫
  - Implements ERC-721 compatible token standards
  - Manages fractional ownership records
  - Tracks token transfer history

- `TradeOffer` 💱
  - Handles peer-to-peer trading mechanics
  - Implements automated price discovery
  - Manages order matching and execution

- `UserProfile` 👤
  - Secure user authentication and authorization
  - Portfolio tracking and management
  - Integrated wallet functionality

#### Key Functions
- `create_art_piece()`: Tokenize new artworks
- `purchase_tokens()`: Buy fractional ownership tokens
- `create_trade_offer()`: List tokens for sale
- `accept_trade_offer()`: Execute trades

### 🎨 Frontend Development

Our modern, intuitive frontend is crafted with React and cutting-edge web technologies:

#### Key Components
- **🏠 HomePage**
  - Curated artwork discovery
  - Real-time trending artworks
  - Featured collections showcase
  - Advanced search and filtering

- **📊 PortfolioPage**
  - Interactive investment dashboard
  - Real-time portfolio valuation
  - Performance analytics
  - Transaction history

- **🎨 CreateArtPage**
  - Streamlined artwork tokenization
  - Batch upload capabilities
  - Customizable token economics
  - Automated verification system

- **🧭 Navigation**
  - Seamless user authentication
  - Personalized user experience
  - Multi-wallet integration
  - Intuitive interface design

#### Key Features
- Real-time data from ICP backend
- Internet Identity integration
- Responsive design with Tailwind CSS
- Modern UI components from shadcn/ui

### Running in Development Mode

1. **Start the local replica**
   ```bash
   dfx start --clean
   ```

2. **Deploy backend in watch mode**
   ```bash
   dfx deploy art_co_ownership_backend
   ```

3. **Start frontend development server**
   ```bash
   cd art-co-ownership-frontend
   pnpm run dev
   ```

4. **Access the development server**
   - Frontend: `http://localhost:5173`
   - Backend Candid UI: `http://localhost:4943/?canisterId=<backend-canister-id>&id=<backend-canister-id>`

## 📦 Project Structure

```
art_co_ownership/
├── src/
│   └── art_co_ownership_backend/
│       ├── src/
│       │   └── lib.rs                 # Main backend logic
│       ├── Cargo.toml                 # Rust dependencies
│       └── art_co_ownership_backend.did # Candid interface
├── art-co-ownership-frontend/
│   ├── src/
│   │   ├── components/                # React components
│   │   ├── lib/
│   │   │   └── icp.js                # ICP integration service
│   │   ├── App.jsx                   # Main React application
│   │   └── main.jsx                  # React entry point
│   ├── public/                       # Static assets
│   ├── package.json                  # Frontend dependencies
│   └── vite.config.js               # Vite configuration
├── dfx.json                          # dfx configuration
├── Cargo.toml                        # Workspace configuration
└── README.md                         # This file
```

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the frontend directory:

```env
REACT_APP_BACKEND_CANISTER_ID=your-backend-canister-id
REACT_APP_INTERNET_IDENTITY_CANISTER_ID=your-ii-canister-id
NODE_ENV=development
```

### dfx.json Configuration

The `dfx.json` file configures both backend and frontend canisters:

- **Backend**: Rust canister with Candid interface
- **Frontend**: Asset canister serving the React build

## 🚀 Deployment

### Local Deployment

1. **Start local replica**
   ```bash
   dfx start --background
   ```

2. **Deploy all canisters**
   ```bash
   dfx deploy
   ```

### Mainnet Deployment

1. **Add cycles to your wallet**
   ```bash
   dfx wallet --network ic balance
   ```

2. **Deploy to mainnet**
   ```bash
   dfx deploy --network ic
   ```

3. **Update frontend environment variables**
   ```bash
   # Update canister IDs in .env file
   REACT_APP_BACKEND_CANISTER_ID=$(dfx canister --network ic id art_co_ownership_backend)
   ```

## 🧪 Testing

### Backend Tests
```bash
cargo test
```

### Frontend Tests
```bash
cd art-co-ownership-frontend
pnpm test
```

### Integration Tests
```bash
# Deploy locally and run integration tests
dfx start --background
dfx deploy
# Run your integration test suite
```

## 📊 Usage Examples

### Creating an Art Piece

```javascript
import icpService from './lib/icp.js';

const artData = {
  title: "Digital Masterpiece",
  artist: "CryptoArtist",
  description: "A stunning digital artwork...",
  image_url: "https://example.com/image.jpg",
  total_tokens: 1000,
  price_per_token: 100000 // 0.001 ICP in e8s
};

const result = await icpService.createArtPiece(artData);
```

### Purchasing Tokens

```javascript
const artId = 1;
const tokenAmount = 50;

const ownership = await icpService.purchaseTokens(artId, tokenAmount);
console.log(`Purchased ${tokenAmount} tokens for art piece ${artId}`);
```

### Creating a Trade Offer

```javascript
const offerData = {
  art_id: 1,
  tokens_for_sale: 25,
  price_per_token: 110000 // 0.0011 ICP in e8s
};

const offer = await icpService.createTradeOffer(offerData);
```

## 🔐 Security & Best Practices

### Platform Security
- **🛡️ Internet Identity**
  - State-of-the-art authentication system
  - Privacy-preserving user identification
  - Biometric authentication support
  - Multi-factor authentication options

- **🔒 Canister Security**
  - Memory-safe Rust implementation
  - Regular security audits
  - Automated vulnerability scanning
  - Real-time threat detection

- **🚦 Access Control**
  - Role-based authorization system
  - Granular permission management
  - Activity monitoring and logging
  - Automated compliance checks

- **✅ Data Validation**
  - Comprehensive input sanitization
  - Cross-platform validation rules
  - Error handling and reporting
  - Data integrity checks

- **💾 Data Persistence**
  - Secure stable memory implementation
  - Automated backup systems
  - Version control for upgrades
  - Data recovery protocols

## � Community & Support

### Connect With Us
- [📱 Twitter](https://twitter.com/ArtShareICP)
- [💬 Discord](https://discord.gg/artshare)
- [📘 Documentation](https://docs.artshare.io)
- [📧 Support](mailto:support@artshare.io)

### Contributing
We welcome contributions from the community! Whether you're fixing bugs, adding features, or improving documentation, check out our [Contributing Guidelines](CONTRIBUTING.md).

## �🏆 Acknowledgments

We extend our gratitude to:

- **🌐 DFINITY Foundation** - For creating the revolutionary Internet Computer Protocol
- **⚙️ Rust Community** - For maintaining exceptional development tools and libraries
- **⚛️ React Team** - For the powerful frontend framework
- **🎨 shadcn/ui** - For the beautiful UI components that enhance our platform

---

<div align="center">
  <h3>Built with 💝 on the Internet Computer</h3>
  <p>Join us in revolutionizing the digital art marketplace!</p>
</div>
