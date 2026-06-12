---
title: "Sharing a CD/DVD drive over network, and..."
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by omelette on 2011-08-20
Hi.  Sorry if this has been answered, but after an hour of searching, I'm still clueless!  I will start by saying with Samba, I have no problem sharing any particular CD/DVD that I insert into the drive.  What I'm trying to figure out is how do I share the drive itself for general usage, so that whatever CD/DVD is inserted into the drive, it will be accessible on the remote machine without having to keep assigning new shares for every disk that has a different name?

The 'old' way of mounting shares seems to have been to use a known & unchanging folder-name ie. 'cdrom0', but Ubuntu names the folder after the disk so it can be anything.  Anyone?

---

### Post by omelette on 2011-08-22
* bump *

---

### Post by Cheesehead on 2011-08-22
Edit your /etc/samba/smb.conf
Instructions to enable a shared CD drive are in the file.

---

### Post by omelette on 2011-08-22
Wow, that simple - already done!  Thanks!!!

---

### Post by omelette on 2011-08-22
Or maybe not, a little problem.  Ubuntu mounts everything at /media.  If I add the following to smb.conf;

> [dvd]
        comment = dvd drive on linux
        writable = No
        locking = No
        path = /media

Although I can now access the drive ok from the 'DVD' share, Ubuntu also mounts everything else in /media as well, making them all accessible from 'DVD' - this I don't want.

---

