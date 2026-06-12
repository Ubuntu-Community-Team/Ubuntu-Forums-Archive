---
title: "file uploading using SFTP in filezilla"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by tbobker on 2010-04-27
I have set up a local server for testing on my home network and installed openSSH.  I can login using filezilla and SFTP and can even download files. Error messages saying cannot find directory (the directory I am trying to upload)?

Do I need to configure openSSH to allow this. I am using my usual ubuntu login. Maybe I need to set up another user for SFTP.

any advice or help appreciated.

---

### Post by 2hot6ft2 on 2010-04-27
I don't use filezilla I do it one of these ways.

Nautilus (Ubuntu)
Places > Connect to server
Service Type: SSH
Server: IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
You can check the "Add Bookmark" box and it will show up under Places as Whatever you name it so you can just click on it like a folder.
Click on Connect

krusader (Kubuntu)
Tools > New Net Connection
Protocol: fish://
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Click on Connect

gFTP
Host: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Password: Your password on the host computer
Select SSH2
Click on the icon to the left of Host that has 2 computers to connect (and disconnect)

Dolphin (also has a split view to work on 2 folders at one time)
Click on Networks on the left
Click on Add Network Folder
Select Secure shell (ssh)
Click on Next
Put in your Name
Put in your Username (username on the host computer)
Server: The IP Address of the server
Port: The port you set the server to
Folder: /home/<your-user-name-on-the-server>/
Encoding: Change to (Unicode UTF-8) or whatever works for you
Checking "Create an icon for this remote folder" is up to you
Click on Connect

Gigolo
Click on Connect
Service type: SSH
Server: IP Address of the server
Port: The port you set the server to
Username: Your username on the host computer
Click on Connect
The server will show up in the window (sftp for (username) on (IP Address of the server))

---

### Post by tbobker on 2010-04-28
Hi MAte,

Thanks for replying.

I am using filezilla because I want to upload many files and folders as well as download many files and folders?

While it is possible for me to download, I just cant upload. There is no permission error. The error just states that it cant find the folders which is should be creating.

---

### Post by tbobker on 2010-04-28
I think you might also be missing my point. My Ubuntu install is acting as a server and I have connected this to my router. I am connecting to my Ubuntu serve using another computer on the home network and want to be able to use SFTP to upload, download and edit files. 

At present all I can do is download and view.

Any help or advice appreciated.

---

### Post by tbobker on 2010-05-01
For anyone who is interested, the reason it would not work is because I needed to change the owner of the directory: from root who has no SFTP access by default (I think) to my login user. I used "chown -R username dirname"

---

