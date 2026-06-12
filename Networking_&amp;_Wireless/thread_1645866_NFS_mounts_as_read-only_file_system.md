---
title: "NFS mounts as read-only file system"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2010-12-15
Hello!
I am trying ti set up a NFS server using the guide on [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")
However, the NFS mounts on the client side as a read-only file system, so I cannot modify nothing. Here is my /etc/export file on the server side:
```
/home/acrocephalus/ 192.168.1.35 (rw,async,no_root_squash)
```
and this is my /etc/fstab file relevant line on the client side
```
192.168.1.33:/home/acrocephalus/ /home/acrocephalus/AcrocephalusServer/ nfs rsize=8192,wsize=8192,timeo=14,intr
```
Then, I mount the system using the command ```
sudo mount /home/acrocephalus/AcrocephalusServer/
```.
Does anyone have an idea on how to mount the NFS with full read-write permissions?
Cheers!

Dani

---

### Post by dargaud on 2010-12-15
Are your usernames and userids the same on both sides ? Check in /etc/passwd

---

### Post by acrocephalus on 2010-12-15
White spaces matter on NFS, so this line in the /etc/exports ```
/home/acrocephalus/ 192.168.1.35 (rw,async,no_root_squash)
``` grants read-only permissions to 192.168.1.35 and read and write permissions to any other host, while this line (note that there is no white space between 192.168.1.35 and (rw,async,no_root_squash)```
/home/acrocephalus/ 192.168.1.35(rw,async,no_root_squash)
``` grants read and write permissions to 192.168.1.35. I hope it helps!
Cheers!

Dani

---

### Post by acrocephalus on 2010-12-15
> **acrocephalus said:**
> White spaces matter on NFS, so this line in the /etc/exports ```
/home/acrocephalus/ 192.168.1.35 (rw,async,no_root_squash)
``` grants read-only permissions to 192.168.1.35 and read and write permissions to any other host, while this line (note that there is no white space between 192.168.1.35 and (rw,async,no_root_squash)```
/home/acrocephalus/ 192.168.1.35(rw,async,no_root_squash)
``` grants read and write permissions to 192.168.1.35. I hope it helps!
Cheers!

Dani

Thank you for your reply, Dargaud. But my problem was a stupid on (see quoted post). I'm always learnin' new things!
Cheers!

Dani

---

