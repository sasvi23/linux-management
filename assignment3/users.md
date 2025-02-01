# Linux Management 

### Student
- Sasvi Vidunadi Ranasinghe, sasvi23, amk1005778@student.hamk.fi

## Summary
This notebook describes the activities and tasks related with the microsoft azure, in the course Linux Management of the Degree program ICT and Robotics at Häme University of Applied Sciences. 


## 2025-01-24

Present in the lab:
- Sasvi Vidunadi Ranasinghe

## Create users and use created users to test out file access permissions

####  Task point 1
- Created the tupu user using the adduser script.

<br><img src="images\adduser-tupu.png" width="2000" height="150"><br/>

- given a new password and skip on the additional details.

<br><img src="images\adduser-tupu2.png" width="800" height="200"><br/>


#### Task point 2
- Created the Lupu user using the useradd command.
- Created a user profile, home directory, and user group similar to Tupu.

<br><img src="images\adduser-lupu.png" width="800" height="300"><br/>

- Since I have created the lupu user like the way I made the tupu, i had to ensure that the lupu group exists.

<br><img src="images\lupu-existance.png" width="2000" height="30"><br/>

- With the detour I did previously, I had to Check if the home directory exists and has the correct ownership.

    - *Verify the lupu user's home directory and permissions*:
    ```
    1. First command - Check if the home directory exists and has the correct ownership and permissions.
        This command creates the home directory /home/lupu if it doesn't already exist.
    ```

    ```
    2. Second Command - This command changes the ownership of the /home/lupu directory and all its contents (recursively, due to the -R flag) to the user lupu and the group lupu.
    ```

    ```
     3. Third command - This command sets the permissions of the /home/lupu directory to 755. This means the owner (lupu) has read, write, and execute permissions, while the group and others have read and execute permissions.
     ````
<br><img src="images\lupu-groupadd.png" width="2000" height="25"><br/>


- Ensure the lupu user is part of the lupu group.

<br><img src="images\lupu-home-directory-and-permissions.png" width="2000" height="50"><br/>

#### Task point 3
- Created the Hupu system user with the login shell set to /bin/false.

<br><img src="images\adduser-hupu.png" width="2000" height="30"><br/>

```
To verify that the user hupu has been created correctly, you can check the /etc/passwd file or use the id command:
```

    - Check the /etc/passwd file
    - Check the ID

<br><img src="images\hupu-existance.png" width="2000" height="40"><br/>

<br><img src="images\id-hupu.png" width="2000" height="40"><br/>

- This confirms that hupu was created successfully.

#### Task point 4
- Added the users Tupu and Lupu to the sudo users.

<br><img src="images\adding-users-to-sudo.png" width="2000" height="30"><br/>

#### Task point 5
- Created a directory /opt/projekti and add both users (Tupu and Lupu) as owners,with Only Tupu and Lupu should have access to list files in the directory, read, and modify them.

```
- Created the /opt/projekti directory:
- Created the projekti group:
- Added Tupu and Lupu to the projekti group:
- Change the group ownership of the /opt/projekti directory:
- Set the directory permissions to ensure only Tupu and Lupu can list, read, and modify files:
- Set the setgid bit on the directory to ensure new files and directories inherit the projekti group:
```

**How These Steps Match the Requirements**

*Create the directory:*

    > The command sudo mkdir -p /opt/projekti creates the /opt/projekti directory.

*Create a group of users:*

    > The command sudo groupadd projekti creates a group named projekti.

*Add users to the group:*

    > The commands sudo usermod -aG projekti tupu and sudo usermod -aG projekti lupu add Tupu and Lupu to the projekti group.

*Assign the group to the owner of the folder and files:*

    > The command sudo chown :projekti /opt/projekti changes the group ownership of the directory to projekti.

*Ensure only Tupu and Lupu have access:*

    > The command sudo chmod 770 /opt/projekti sets the permissions so that only the owner (root) and group members (Tupu and Lupu) have full access, while others have no access.

*Maintain the permission structure for new files and folders:*

    > The command sudo chmod g+s /opt/projekti sets the setgid bit, ensuring that any new files or directories created within /opt/projekti inherit the projekti group ownership.


<br><img src="images\create-directory-and-add-users.png" width="2000" height="150"><br/>
