---
title: "script to access windows share"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-10-27
i can access to my shared folder using LOCAL -> CONNECT TO A SERVER
and then i put server ip and folder share. And i don't need to be a root user

but i need to make a script that will ask for username and password and it will open that share.

Example

SERVER
     - student/12345

the script will ask for the username and i put 12345 then its password and it will open the share SERVER/student/12345

is it possible? without the root privileges?

thanks

---

### Post by albandy on 2010-10-27
This is because you cannot mount anything in the filesystem without permisions, nautilus really don't mount it, only show you the contents like smbclient.

So you have some options:
Add a reference to the script in sudoers file, so this script will be run as root 
use smbclient instead of smbmount in the script (it could be a bit difficult)
change smbclient permisions to execute it as root.

---

### Post by Morbius1 on 2010-10-27
May I ask why the need for a script?

You could just bookmark it then it would show up under Places in Nautilus.

Anyway, one simple way is this:
```
nautilus smb://Server/student/12345
```        > This is because you cannot mount anything in the filesystem without  permisions, nautilus really don't mount it, only show you the contents  like smbclient.
Nautilus does in fact really mount ( gvfs-mount smb:// ) the remote share without being root because it uses fuse. It also creates a real mountpoint but in a very unusual place ( developers humor I guess ) located at:

> /home/your_user_name/.gvfs/share_name on server_name

---

### Post by guimenez on 2010-10-27
many thanks for the reply :D

now i'm understading.

ok this is my situation:

i need to use wine for some programs.
but i can't make wine programs work in all users (shortcuts for everyone logged in).

For bypass that problem, i created a local user called "wine" that has all needed programs installed. But when the students finish they work, they need to save the work to the shared folder in the server.

For that i need a script in the desktop and when they open it, it will ask for the %username% and then fill: nautilus smb://Server/student/%username%

is it possible?

many thanks

---

### Post by albandy on 2010-10-28
> **Morbius1 said:**
> May I ask why the need for a script?

You could just bookmark it then it would show up under Places in Nautilus.

Anyway, one simple way is this:
```
nautilus smb://Server/student/12345
```        Nautilus does in fact really mount ( gvfs-mount smb:// ) the remote share without being root because it uses fuse. It also creates a real mountpoint but in a very unusual place ( developers humor I guess ) located at:

So I was wrong in the way nautilus manages windows shares. This is great,  I thought that because the mount point name is not shown in the mount list, only it's shown a reference to gvfs so if you do not enter in this folder you can't see the nautilus mount points.

Thanks a lot.

---

