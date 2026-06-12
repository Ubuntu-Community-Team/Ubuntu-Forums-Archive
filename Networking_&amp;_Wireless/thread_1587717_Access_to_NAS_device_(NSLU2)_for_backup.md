---
title: "Access to NAS device (NSLU2) for backup"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by dhochmuth on 2010-10-04
I've recently set up a Ubuntu 10.04 desktop for my home network.  I'm pretty new to Linux and find it confusing.  Anyway, I'm trying to access USB drives on my Linksys network storage device NSLU2.  I've loaded Samba and can access everything fine in Nautilus.  But none of the backup programs with GUIs I've tried (LuckyBackup, Simple Backup, Grsync) can "see" the device or it's drives.  The ones that have "browse" functions don't show it.  Why is that?

To work around this, I've tried to mount them using fstab edits but get "No such device or address."  My fstab entry is:

//lkg3162ee/disk%201/  /media/NSLU2disk1  cifs  guest,uid=1000,iocharset=utf8,  0  0

(The initial entry was cut and pasted from the nautilus address window that has access to the directory).

Any suggestions would be appreciated.  Keep it simple for a noob, please.

---

