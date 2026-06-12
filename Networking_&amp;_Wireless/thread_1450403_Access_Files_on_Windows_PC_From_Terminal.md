---
title: "Access Files on Windows PC From Terminal"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by bvrclvr24 on 2010-04-09
Hi All,
I have a Windows PC that I'm trying to access from my Karmic Laptop terminal.  I've got them connected over the network and have the drive in the Windows machine mounted, but I just can't find it in the filesystem.  I'd like to write some scripts to move some files around, but am obviously off to a bad start.  Can anyone help me out?

Thanks, 
Ryan

---

### Post by prshah on 2010-04-09
> **bvrclvr24 said:**
> Windows PC that I'm trying to access from my Karmic Laptop terminal

You can check for the mount point (where the Windows share is mounted on Karmic) with the command```
mount|grep cifs
```
 
Post back if you want information on how to manually mount (access) a Windows share using the terminal.

---

