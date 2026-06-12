---
title: "Sharing"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by gettensome on 2009-01-12
This is what I have on my network;

1 computer running Ubuntu 8.10 32 bit Desktop
1 computer running Ubuntu 8.10 x86_64 Server

What I want to do

1. Have both computers visible when I open 'network servers' on either machine
2. Have a folder named ~/shared for every user with 'drwxrwxr--' permissions.

I have both samba and NFS installed but I just dont know how to set either computer up to accomplish this "simple" task.  Please help.

---

### Post by Iowan on 2009-01-12
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
A couple of help pages to review.

---

### Post by gettensome on 2009-01-13
Okay I have gotten half way there... I can mount a share from one computer but I cant seem to get the other one to mount the share that my main system is broadcasting.  I'll figure that out on my own...

I still don't see the other machine when I open my network servers icon, just a "windows network" with nothing in it.

the machine that I can mount an NFS share I can only get the Icon for the mounted file system to appear on my desktop when I mount to a folder on the desktop.  Is there a way to mount to /mnt/{computer name} and still get the mounted file system to appear on my desktop?

---

### Post by gettensome on 2009-01-13
> the machine that I can mount an NFS share I can only get the Icon for the mounted file system to appear on my desktop when I mount to a folder on the desktop. Is there a way to mount to /mnt/{computer name} and still get the mounted file system to appear on my desktop?

Disregard this... I just mounted it to a folder in my ~

---

