# Blind-SQLI 🔓

# Overview
This is a Python-based tool designed to demonstrate and execute a boolean-based blind SQL injection attack. It extracts data (specifically, user password hashes) from a vulnerable web application database by asking a series of true/false questions. The script automates the process of identifying a user, determining their password hash length, and extracting the hash character-by-character. This tool is intended strictly for educational purposes and penetration testing in controlled environments.

# Note
- Security and Ethical Notice: This script is intended for educational and ethical hacking purposes only. It must only be used in environments you own or have explicit permission to test. Do not use the provided code and techniques for illegal activities.

# Features
- Boolean-Based Logic: Infers data by analyzing the application's binary (true/false) response to injected SQL queries.
- User Validation: Checks if a target `user_id` exists in the database before proceeding with the attack.
- Automated Hash Length Detection: Automatically discovers the exact length of the target user's password hash.
- Character-by-Character Extraction: Reconstructs the full password hash by testing one character at a time against a defined charset.
- Query Counter: Tracks and displays the total number of HTTP requests sent for each major step of the attack.

# How It Works
1. The script targets a local web server (default: http://127.0.0.1:5000).

2. It sends a `POST` request with a payload crafted to manipulate the backend SQL query, like `admin' and {CONDITION}--`. The `{CONDITION}` is a subquery that asks a question about the database.

3. The script determines if the `{CONDITION}` was true or false by checking for a specific message in the server's response (e.g., "Welcome back"). In this boolean-based attack, a failed login response can signify that the injected SQL condition was true.

4. If the response contains the success message (Welcome back), the script reports the valid credentials and exits.

5. If no valid password is found for a username, it notifies and moves on to the next one.

# Tools and Technologies Used
Python – Main programming language.

`sys` – Used for output handling and termination.

`requests` – For sending HTTP POST requests.

Linux (Kali) – Typical environment for running hash-cracking tools.

# Files
`brute_force_login.py`: Main Python script that performs the brute-force attack.

`rockyou.txt`: A wordlist file containing millions of commonly used passwords (You can use any .txt wordlist).

# How to Run
1. Clone or download this repository
2. Install the libraries: pip install requests (sys doesn't need to be installed, it's part of Python's standard library)
3. Place your wordlist file in the same directory as the script, or update the file path in the code.
4. Run the script using one of the following methods:
   - Terminal (macOS/Linux): 'python3 brute_force_login.py'
   - Windows (or IDEs like VS Code, PyCharm): 'python brute_force_login.py' or use the Run button

# Disclaimer
This project is created for research, ethical hacking, and educational purposes only. Unauthorized access to computer systems is illegal. Always ensure you have explicit permission before testing any systems. The developer is not responsible for any misuse of this code.

# Contribution and Feedback
Contributions, feedback, and issues can be submitted via the GitHub repository. Ensure that your interactions adhere to the GitHub Community Guidelines to maintain a respectful and collaborative environment.

# License
This project is licensed under the MIT License. Feel free to use or modify it for personal use or learning.
<br>**Stay safe and have fun! 😊**
