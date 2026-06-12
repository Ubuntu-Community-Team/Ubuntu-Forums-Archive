---
title: "permission denied on Windows FAT32 network share"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2006-07-11
There are a few things in Ubuntu, which drives me crazy sometimes. Printing to a network printer and mounting samba shares. I do not use it very often and when I do not need it they work ok, but every time I need it, it fails me.

Ok, I let the steam go...

I am trying to transfer a file from my laptop to my desktop FAT32 Windows samba share and got permission denied. I tried to mount it, change permissions and all the stuff but still no luck. I wonder how it can be if there is no permission system on FAT32?

The last thing I tried was:
```
sudo mount -t smbfs -o username=user,password=mypassword,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //192.168.1.3/WinD /home/`whoami`/Network
```
it mounted fine by still "permission denied"

---

