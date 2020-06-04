
# Key Management for LoveBank


API secrets, database master passwords and other sensitive data should not be explicitly stored within the code itself for security purposes. To
get the secrets, please utilize Key Management Services by AWS. 

All secret value and secret key pair should be stored under one secret with name "lovebank-secret". AWS allows to store multiple
secret key/value pairs under one secret name (You may consider "lovebank-secret" as a connection of secrets.)
## Retrieving Secrets from KMS

### 1. Setting up credentials:
First, you would need to set up the credentials to connect to AWS from your local machine. This step is made easy thanks to 
the script provided. Within this dir, you would need to crete a file named ".env" that contains exactly two lines:
```
AWS_ACCESS_ID="ACCESS_ID_HIDDEN"
AWS_ACCESS_KEY="ACCESS_KEY_HIDDEN"
```
This sets the environment variable upon running get_secrets and will allow the program to establish a connection with AWS.

### 2. Get secrets:
Return a python dict of secret key and value pair stored in "lovebank-secret".
```
secret_name = "lovebank-secret"
response = get_secret(secret_name)

secret_dict = json.loads(response)
```

### 3. Insert new secret key/value pair:
```
secret_name = "lovebank-secret"
secret_key = "TEST1"
secret_value = "test1"

insert_new_secret_pair(secret_name, secret_key, secret_value)
```

