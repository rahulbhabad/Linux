# Types of Users in Linux


## 1. $${\color{red} \textbf {Root User}}$$

- The root user is the superuser in Linux with unrestricted access to the entire system.
- They can perform any administrative task, including creating and deleting users, modifying files, and configuring the system.
- user id is 0

**Common Commands for Root User:**
```bash
# Switch to root user
sudo -i
````

**Execute a command as root**
````
sudo <command>
````

## 2. $${\color{blue} \textbf {System Users}}$$
- These are service accounts created by the system to manage and run specific processes or services.
- Do not have login shells by default.
- Limited privileges, ensuring security for system services.
- user id ranges from 1 - 999

  
## 3. $${\color{green} \textbf {Local User}}$$
- These are standard users created for daily tasks and operations.
- Each user has their own home directory (e.g., /home/username) and specific permissions.
- user id 1000 - 65535

  
#### Add a new user
````
sudo useradd <username>
````
#### Set or change a user password
````
sudo passwd <username>
````

#### List All Users
````
cat /etc/passwd
```` 
#### Important Files for Users

**/etc/passwd**
- Stores user account information

![image](https://github.com/user-attachments/assets/8573faaf-b158-4699-9abd-48b9ae43c2d8)

**/etc/shadow**
1. Username
2. Encrypted Password
3. Last time password change
4. Min days between password change
5. Max days between password change
6. Warning days
7. Inactive days
8. Account Expiry
9. Future Use
- Stores encrypted password hashes and metadata for password policies.
![image](https://github.com/user-attachments/assets/01a728d8-78f9-4489-91a0-cb3c9c57da3a)

#### Modify an Existing User

**Assign a Customized UID to a User**
````
usermod -u 3000 tony
````
**Assign a No-Login Shell** (Prevents the user from logging in)
````
usermod -s /sbin/nologin steve
````
**Add a Comment**
````
usermod -c "development team" bruce
````
**Lock a User's Password** (Prevents the user from logging in.)
````
usermod -L natasha
````
**Unlock a User's Password**
````
usermod -U natasha
````

## $${\color{magenta} \textbf {Group Management}}$$

**Create a Group**
````
groupadd avengers
````

**Important Files for Groups**

![image](https://github.com/user-attachments/assets/ecd01e92-9511-4aa8-b514-7db87da1000b)

![image](https://github.com/user-attachments/assets/350fdc3b-89e7-4f6c-9a6f-462a58681d96)

![image](https://github.com/user-attachments/assets/d285f4fb-8013-494b-b553-79ec1fb7a27c)

**Add a User to a Group**
````
usermod -aG groupname username
example:
usermod -aG avengers natasha
````
````
gpasswd -a username groupname
example:
gpasswd -a steve avengers
````
**Remove a User from a Group**
````
gpasswd -d steve avengers
````

**Add Multiple Users to a Group**
````
gpasswd -M steve,thor,bruce avengers
````
**Remove a User from a Group**
````
gpasswd -d bruce avengers
````

**Assign an Admin to a Group**
````
gpasswd -A steve avengers
````
**Remove Admin from a Group**
````
gpasswd -A '' avengers
````

**Delete a Group**
````
groupdel -f avengers
````
