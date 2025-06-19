# Password-manager
SECURE VAULT – Project Solution Overview

Core Functionalities
1. Master Password Setup & Login
First-time use:
Prompt the user to create and confirm a master password.
Subsequent use:
Require the master password to decrypt the vault and access credentials.

2. Password Creation
Generate strong passwords with:
Customizable length
Option to include symbols, numbers, and uppercase/lowercase letters
Integrated password strength meter for real-time feedback.

3. Categorized Storage
Organize credentials into the following categories:
Personal
Work
Social
Finance
Others

4. CRUD Operations
Create: Add new credentials.
Read: View stored credentials securely.
Update: Edit existing credentials.
Delete: Remove credentials from the vault.


🔐 Security Features
1. Client-side Encryption 
 Encrypt all credentials before storing
Derive the encryption key from the master password 
Use a random, per-user salt stored unencrypted in localStorage

2. No Plaintext Password Storage
Passwords are never stored in plaintext
Even in memory, decrypted passwords are handled temporarily and securely

3. Secure Storage
Encrypted vault is stored in localStorage or IndexedDB
Example format:
json
Copy
Edit
{
  "vault": "ENCRYPTED_STRING",
  "salt": "base64SALT",
  "categories": {
    "personal": [...],
    "finance": [...]
  }
}
4. Master Password Hashing & Authentication
Option to store a hashed master password 
Alternatively, validate the password by attempting to decrypt the vault

5. Session Management
Decrypted data is stored only during the session (e.g., in sessionStorage)
Vault auto-locks after a fixed time of inactivity (e.g., 10 minutes)

6. Password Strength Meter
Provides real-time feedback on password strength during creation or editing

7. Clipboard Security
Passwords copied to the clipboard are automatically cleared after a short time (e.g., 15 seconds)


🔐 Advanced Security Features
8. Auto-lock on Page Refresh
Reloading or navigating away from the page automatically locks the vault
Clears session data for protection

9. Auto-lock After 2 Minutes of Inactivity
If no user interaction is detected for 2 minutes, the vault auto-locks

10. Forgot Password + Recovery Option
Recover access by answering a security question or using a recovery key/file
Allows reset of the master password without losing stored data

11. Auto-Open Website When Password is Used
If a stored credential includes a URL, it auto-opens in a new tab when the password is accessed

12. Encrypted Vault Export
Vault can be exported as a downloadable .vault file
File remains encrypted and usable only with the correct master password

13. Encrypted Vault Import
Users can import a .vault file and decrypt it using their master password to restore saved credentials

