# Rate_Password

import re

def rate_password(password):
    """
    Rates a password based on its strength.

    password: string, the password to rate.
    returns: integer, the strength rating of the password (1 to 3).
    """
    # Check if password meets minimum length requirement.
    if len(password) < 8:
        return 1

    # Check if password contains all required character types.
    if all(re.search(pattern, password) for pattern in [r"[a-z]", r"[A-Z]", r"\d", r"\W"]):
        return 3

    # If password doesn't meet level 3 requirements but contains more than one type of character.
    if any(re.search(pattern, password) for pattern in [r"[a-z]", r"[A-Z]", r"\d", r"\W"]):
        return 2

    # If password only contains one type of character.
    return 1

# Prompt the user to enter a password.
password = input("Enter a password to rate: ")

# Rate the password.
rating = rate_password(password)

# Print the result.
if rating == 1:
    print("Weak password.")
elif rating == 2:
    print("Moderate password.")
elif rating == 3:
    print("Strong password!")
