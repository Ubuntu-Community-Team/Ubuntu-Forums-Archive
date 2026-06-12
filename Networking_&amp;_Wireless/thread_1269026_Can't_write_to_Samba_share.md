---
title: "Can't write to Samba share"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by vegaramos on 2009-09-17
I'm sorry, but I've tried several configurations of the smb.conf file, and I can't get it to allow me to write access in the share I want.   

I have Ubuntu (Intrepid Ibex) running on an old laptop, that I want to use as a file and print server.  The folder I want to share is on an external hard drive (Western Digital My Book 500 Gb) connected via USB.  I have four computers in the house that I want to back themselves up to the Ubuntu server.  Two are iMacs (one running Tiger, one running Leopard), and two are Windows 7 (one a 32bit, the other a 64 bit). 

I updated the fstab file to mount the drive in my user account folder, that works without a hitch, but while I can see the server and the files on it, I can't write to the folders.

/home/alvin/backup/

The folder on the external hard drive that I want to share is called Backups.  Here are the permissions for this folder.

drwxr-xr-x 7 root root 32768 2009-09-12 12:15 Backups



Here is my smb.conf file, what am I missing?

[global]
        workgroup = myHome


[Backups]
        path = /home/alvin/backup/Backups
        writeable = yes
        read only = no	
        guest ok = no
        browseable = yes

---

### Post by Whiffle on 2009-09-17
drwxr-xr-x 7 root root 32768 2009-09-12 12:15 Backups

Looks like its only writable by root.  If you chmod 777 it, it'll be writable by anyone.

---

### Post by swerdna on 2009-09-18
You haven't shared /home/alvin/backup/
You've shared only the folder inside that, the folder Backups, justb in case you didn't realise.

---

