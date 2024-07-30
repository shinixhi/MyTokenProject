# MyTokenProject

## Overview
MyToken is an ERC20 token implemented in Solidity. This smart contract includes functionalities to mint, burn, and transfer tokens. The mint function is restricted to the contract owner, while the burn and transfer functions are accessible by any token holder.

## Features
- **Minting:** Only the contract owner can mint new tokens.
- **Burning:** Any token holder can burn their own tokens.
- **Transferring:** Standard ERC20 transfer functionality.

## How to Deploy and Interact with the Contract using Remix

### Deploying the Contract

1. **Open Remix IDE:**
   - Go to [Remix IDE](https://remix.ethereum.org/).

2. **Create a New File:**
   - In the Remix file explorer, create a new file named `MyToken.sol`.

3. **Paste the Smart Contract Code:**
   - Copy and paste the following Solidity code into `MyToken.sol`:

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.0;

   import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
   import "@openzeppelin/contracts/access/Ownable.sol";

   contract MyToken is ERC20, Ownable {
       constructor(string memory name, string memory symbol, address _owner) ERC20(name, symbol) Ownable(_owner) {}

       function mint(address to, uint256 amount) public onlyOwner {
           _mint(to, amount);
       }

       function burn(uint256 amount) public {
           _burn(msg.sender, amount);
       }
   }
4. **Compile the Contract:**

Go to the "Solidity Compiler" tab.
-Ensure the compiler version is set to 0.8.0 or later.
-Click the "Compile MyToken.sol" button.
-Deploy the Contract:

5. **Go to the "Deploy & Run Transactions" tab.**
-Select "Injected Web3" if you are using MetaMask, or "JavaScript VM" for local testing.
-Choose the MyToken contract.
Enter the constructor parameters:
Name: "MyToken"
Symbol: "MTK"
Owner Address: 0xYourMetaMaskAddress (replace with your actual MetaMask address)
Click the "Deploy" button.

## Interacting with the Contract
Mint Tokens:

After deployment, use the mint function to create new tokens.
Provide the recipient's address and the amount of tokens to mint.
Click "transact".
Burn Tokens:

Use the burn function to destroy tokens.
Provide the amount of tokens to burn.
Click "transact".
Transfer Tokens:

Use the standard ERC20 transfer function to transfer tokens between addresses.
Provide the recipient's address and the amount of tokens to transfer.
Click "transact".

## License
This project is licensed under the MIT License.
