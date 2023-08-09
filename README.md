# check-my-password
This code is used to check whether a given password has been compromised in any known data breaches by querying the Have I Been Pwned API for breached passwords.The code uses the `requests` library to interact with the API and the `hashlib` library to calculate the SHA-1 hash of passwords. It takes a list of passwords as command-line arguments and reports whether each password has been compromised or not.

`def get_password_leaks_count(hashes, hash_to_check):`
   This function takes the response from the API and a hash to check as arguments. It parses the API response and looks for a match of the hash to check. If a match is found, it returns the number of times that password hash has been breached. If not found, it returns 0.

`def pwned_api_check(password):`
   This function takes a password as an argument and performs the following steps:
   
   a. Calculates the SHA-1 hash of the password and converts it to uppercase.
   
   b. Extracts the first five characters (query character) and the remaining characters (tail) from the hash.
   
   c. Calls `request_api_data` to fetch breached password hashes that match the query character.
   
   d. Calls `get_password_leaks_count` to find the count of breaches for the specific password hash.

In terms of libraries and tools:
- Libraries used: `requests`, `hashlib`, `sys`.
- No additional packages seem to be required, assuming the libraries are available.
- No specific tools are mentioned; this script can be executed from the command line by passing passwords as arguments.

To use this script, you need to run it from the command line and provide passwords as arguments. For example:
```
python script_name.py password1 password2 password3
```

Please note that the script calculates the SHA-1 hash of passwords and sends the first five characters to the API. SHA-1 is considered weak for hashing passwords, and more secure algorithms like SHA-256 or bcrypt are recommended for password storage and verification.
