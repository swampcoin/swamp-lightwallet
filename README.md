# Swamp Lightwallet Client

## Introduction

The Swamp Lightwallet Client is a lightweight, user-friendly GUI wallet designed for people who want to participate in the Swamp blockchain without the complexity of a full node. It allows users to easily create, import and export Swamp addresses, manage their contacts and conduct transactions securely over a TSL-encrypted tunnel connection.

## Features

- Effortless Transaction Management: Conduct Swamp transactions or receive mining rewards without the need for a full node.
- Wallet Management: Create, import, and export your Swamp addresses for multiple user profiles with ease.
- Address Book: Save and manage your contacts in an encrypted address book.
- Secure Communication: TSL-encrypted stunnel connection to the default wallet RPC server.
- Flexible Server Configuration: Switch the wallet RPC server to a local server or a personal VPS.
  
![grafik](https://github.com/vecocoin/swamp-lightwallet/assets/155781737/f5f3e895-a295-44db-aea9-0394dc947c32)




## Custom RPC Server Usage

Ensure your VPS or local server's full-node is running with the specified settings in the config file:

```plaintext
rpcallowip=127.0.0.1
listen=1
daemon=1
server=1
rpcport=<RPC port of your choice>
txindex=1
addressindex=1
spentindex=1
```

Adjust the `.env` file in root folder of main.py (or the binary) based on the `.env-example` provided in the installation folder for configuration.
When using your own VPS, the use of SSH tunneling for secure RPC communication between server and client is highly recommended!

## Build

To compile the client locally using PyInstaller perform the following steps:

```bash
git clone https://github.com/vecocoin/swamp-lightwallet
cd swamp-lightwallet
python setup.py install
pyinstaller main.py -w --clean -n swamp-light
```

Alternatively, run `main.py` directly.

## Backup your wallet profiles and address books
The individual wallet addresses, including their private keys of a profile, are stored in a password-encrypted json file names {username}_profile.json in the root directory of the wallet. This is the only place where your keys and addresses are stored. Therefore, you should back up these files from time to time and / or store private keys of your most important addresses in a secure offline environment. You will need the file + password to restore your full wallet profile or the private keys of your individual addresses. If you lose both, all your funds (on these addresses) will be lost forever. The address books for each profile are stored in a password-encrypted file named {username}_addressbook.json.
