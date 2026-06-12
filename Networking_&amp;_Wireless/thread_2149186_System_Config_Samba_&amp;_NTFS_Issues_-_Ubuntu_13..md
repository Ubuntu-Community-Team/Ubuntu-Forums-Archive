---
title: "System Config Samba &amp; NTFS Issues - Ubuntu 13.04"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by Castle_Romeo on 2013-05-28
As above......I did a sudo apt-get install system-config-samba after installing samba & samba-common on ubuntu 13.04 but it's not showing.

Also, Ubuntu doesn't see my NTFS external drive even after I install NTFS-Config (Ubuntu says that NTFS-3G is already installed).

please help, Thanx in Advance.

---

### Post by zt14427 on 2013-05-28
If I remember, system-config-samba is an old package (maybe not).  Samba is actually very easy to setup for the most part.  If you like using a gui, I recommend using gedit (instead of nano, vi, or emacs) to modify the samba configuration file. In a terminal (or from a "run" prompt) try running ```
sudo gedit /etc/samba/smb.conf
``` make your changes and save it.  Then run ```
sudo service samba restart
```  If that doesn't work, try running ```
sudo service smbd restart
``` and if that doesn't restart the service again, try ```
sudo /etc/init.d/smbd restart
``` if none of the above commands restart the samba service (I don't remember the exact name of the daemon, shame on me) try rebooting.  As far as the NTFS drive goes...  There could be a number of things that are going on.  Try mounting the second partition on it, sometimes windows creates a "system reserved" partition as the first one.  Also make sure that the external drive is powered properly, a USB port will most likely not provide enough power for a desktop HDD (but it will usually be able to spin a laptop one).  I strongly recommend using FAT32 for an external drive, but I understand that you probably have data on it you need to restore, if that is the case, you could always use a specialized "recovery live cd" to assist.

EDIT: I just remembered, try mounting your NTFS disk with```
sudo mount -t ntfs-3g /dev/sdb1 /media/external
``` assuming that your external drive is at /dev/sdb

---

