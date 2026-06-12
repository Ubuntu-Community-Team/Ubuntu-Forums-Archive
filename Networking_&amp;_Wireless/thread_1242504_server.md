---
title: "server"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by anv on 2009-08-17
There's a windows server on my workplace and I use Ubuntu myself, I'd like to be able to reach file server from my Ubuntu computer, how do I do it.

---

### Post by VipX1 on 2009-08-17
You need to mount which ever drive that it is you want to see from your Ubuntu machine. However Ubuntu, and Linux in general uses ext3 file system and Windows uses NTFS or FAT32. Linux can see FAT32 but not NTFS. I'd say if it's a new file server it's using NTFS so you might find it hard to mount directly. You can configure a Samba share but it might mean you'd have to configure some stuff on the file server and your i.t. admin might not be to happy about that..

---

### Post by dmizer on 2009-08-17
> **VipX1 said:**
> You need to mount which ever drive that it is you want to see from your Ubuntu machine. However Ubuntu, and Linux in general uses ext3 file system and Windows uses NTFS or FAT32. Linux can see FAT32 but not NTFS. I'd say if it's a new file server it's using NTFS so you might find it hard to mount directly. You can configure a Samba share but it might mean you'd have to configure some stuff on the file server and your i.t. admin might not be to happy about that..

This is only true if Windows and Ubuntu exist on the same hard drive.

> **anv said:**
> There's a windows server on my workplace and I use Ubuntu myself, I'd like to be able to reach file server from my Ubuntu computer, how do I do it.

If you want to access a Windows server, please see the 6th link in my sig. If that doesn't get you access to your work files, then try the 2nd link in my sig.

---

