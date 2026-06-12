---
title: "How to share NTFS storage partitions on HDD over network with Windows 7"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by vin0 on 2010-10-20
I have a desktop with Ubuntu and I've set up Samba to share files with my Windows 7 laptop.  I can access my home folder just fine except for my NTFS storage partitions on the desktop's HDD and my home folder's Downloads folder (which times out whenever I try and open it).  

Is there an alternative way to share files between Linux and Windows 7?

---

### Post by P4man on 2010-10-20
By default you cant share what you dont own (makes sense when you think of it :) ). Thats probably whats preventing you from sharing the ntfs volumes. You could try this:

```
gksudo gedit /etc/samba/smb.conf
```

add this line in the [global] section:

```
usershare owner only = false
```

Or fix your fstab and mount the ntfs volumes in to mountpoints you own.

That you cant share Downloads seems odd though. You didnt make a mistake in capitalization? Have you tried accessing it from windows by IP?

---

