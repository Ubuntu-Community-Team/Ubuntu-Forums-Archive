---
title: "new folder access denied samba share with multiple users"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by jag17 on 2009-01-19
Hi

I am using Ubuntu server platform with Samba as file server for up to five windows xp clients.

In the ubuntu server I have two folders

ADMIN
FILESHARE

I have created two users in the ubuntu server

sgadmin, sgadmin
sguser, sguser

In samba I have given RW access as follows

ADMIN - sgadmin - RW
FILESHARE - sguser,sgadmin - RW

WINXP CLIENT A
Uses sgadmin login to access \\server\ADMIN folder
Uses sgadmin login to access \\server\FILESHARE folder

WINXP CLIENT B
Uses sguser login to access \\server\FILESHARE folder

PROBLEM:
When WINXP CLIENT B creates a new folder FOLDER1 as \\server\FILESHARE\FOLDER1, it is created with sguser as owner. Due to this when WINXP CLIENT A (using sgadmin login) is unable to copy any files to \\server\FILESHARE\FOLDER1. When trying to copy files it is prompted with Access Denied message

I would like to keep \\server\ADMIN folder only accessible by certain users and \\server\FILESHARE  to be accessible by everyone.

Please let me know how can accomplish this.

Cheers
-Jag

---

### Post by jag17 on 2009-01-19
any ideas?

---

