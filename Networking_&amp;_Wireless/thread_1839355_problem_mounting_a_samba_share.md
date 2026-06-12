---
title: "problem mounting a samba share"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by supportagent11 on 2011-09-05
I installed Samba recently on my Ubuntu 11.04 media center (we'll call it "server") and created a share "Backup"

I'm trying to access the share through my network, but cannot open Windows Network from my laptop's network places (also running 11.04):
**Unable to mount location: Failed to retrieve share list from server.**

However, I can see the shares listed in the terminal when running:
**user@laptop:~$ smbclient -L //server**
(no password specified)

So I installed smbfs and ran
**user@laptop:~$ ****gksu gedit /etc/fstab**
and added the line:
**//server/Backup /home/user/share smbfs username=user,password=pass 0 0**

After rebooting, I can see a "share" directory in my home directory, however it is empty... any suggestions on getting it working?

---

### Post by 2F4U on 2011-09-05
Do you use a firewall on your laptop, which may block Samba?

---

### Post by Morbius1 on 2011-09-05
>  After rebooting, I can see a "share" directory in my home directory,  however it is empty... any suggestions on getting it working?
If after you reboot you run the following command:
```
sudo mount -a
```
Does the share mount?

---

### Post by supportagent11 on 2011-09-05
**user@laptop:~$ sudo mount -a**
[sudo] password for user:
bad user name "user"

It is slightly confusing that I have a login "user" on my laptop and "User" on the server...

I opened SMB (137-139, 445) and NFS (111, 2409) ports using firestarter on both the server and the laptop, as well as updated the username in /etc/fstab:
**//server/Backup /home/user/Media smbfs username=User,password=pass 0 0**

I rebooted and... it appears to be working now.
awesome! thanks

---

