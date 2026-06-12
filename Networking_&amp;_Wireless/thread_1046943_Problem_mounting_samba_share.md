---
title: "Problem mounting samba share"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by tstack77 on 2009-01-21
I have a NAS running Intrepid Server and have no problems accessing my shared folders from my windows machine (both xp and beta7).

I have followed the link below to the letter in trying to set up my shares in order to access them easily in ubuntu.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Here is an example from my fstab file (I have already created a credentials file and made the correct mount folder in /media):

//server/Documents /media/Documents  cifs  credentials=~/.smbcredentials,dmask=777,fmask=777  0  0

Where have I gone wrong?


Side: I can connect to the shares by going through both the 'Network' and 'Connect to Server...' routes.

**[SIZE="4"]EDIT: abandoning samba, trying NFS since it's between 2 ubuntu computers.[/SIZE]**

---

