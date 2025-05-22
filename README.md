# Simple Blockchain Implementation

A basic blockchain implementation in Python using Flask, demonstrating core blockchain concepts including blocks, transactions, mining, and smart contracts.

## Features

- Block creation and mining
- Transaction validation
- Simple smart contract implementation
- Proof of Work consensus
- RESTful API endpoints

## Smart Contract Rules

- Maximum transaction amount: 100 tokens
- Mining reward: 1 token per block

## API Endpoints

### 1. Mine a new block
```http
GET /mine
```
- Creates a new block
- Includes all pending transactions
- Rewards the miner with 1 token

### 2. Create a new transaction
```http
POST /transactions/new
Content-Type: application/json

{
    "sender": "address1",
    "recipient": "address2",
    "amount": 50
}
```
- Adds a new transaction to the pending pool
- Validates against smart contract rules
- Returns the block index where transaction will be included

### 3. View the full blockchain
```http
GET /chain
```
- Returns the complete blockchain
- Shows all blocks and their transactions

## Block Structure
```json
{
    "index": 1,
    "timestamp": 1234567890.123,
    "transactions": [
        {
            "sender": "address1",
            "recipient": "address2",
            "amount": 50
        }
    ],
    "proof": 12345,
    "previous_hash": "abc123..."
}
```

## Setup and Installation

1. Create a virtual environment:
```bash
python -m venv venv
```
This step creates an isolated Python environment for the project. Virtual environments prevent conflicts between project dependencies and system-wide Python packages. The `venv` directory will contain a separate Python installation and pip package manager.

2. Activate the virtual environment:
- Windows:
```bash
venv\Scripts\activate
```
- Unix/MacOS:
```bash
source venv/bin/activate
```
Activating the virtual environment switches your shell to use the Python installation and packages in the virtual environment. You'll know it's activated when you see `(venv)` at the beginning of your command prompt. This ensures all subsequent Python commands use the isolated environment.

3. Install dependencies:
```bash
pip install -r requirements.txt
```
This command installs all required Python packages listed in `requirements.txt`. For this project, it installs Flask, which is needed to run the web server and handle HTTP requests. The `-r` flag tells pip to read the requirements from the file.

4. Run the application:
```bash
python blockchain.py
```
This starts the Flask web server that hosts the blockchain application. The server will be accessible at `http://localhost:5000`. The application runs in development mode by default, which includes features like auto-reloading when code changes are detected.

The server will start at `http://localhost:5000`

## Testing

Use the provided `test/request.http` file to test the API endpoints. The file includes test cases for:
- Valid transactions
- Invalid transactions (amount > 100)
- Missing fields
- Mining blocks
- Viewing the chain

## Limitations

This is a simplified blockchain implementation for educational purposes. It lacks many features of production blockchains:
- No peer-to-peer network
- No wallet system
- No cryptographic signatures
- No balance checking
- No transaction fees
- No network synchronization

## Requirements

- Python 3.x
- Flask
