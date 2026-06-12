---
title: "Auto mounting smbfs problems"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by MrSam on 2006-06-14
I have a file server running under Centos and can auto mount them from both my XP machine and my other Centos Linux (web server) box. Ubuntu is dual boot on the original XP machine.

I have created a credentials file and edited fstab. This is how I have things setup in my web server so I can transfer files easily between boxes but I can't get it to work in Ubuntu.

Here is a copy of my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.0.25/LDrive2 /media/smbmnt1 smbfs credentials=/root/.smbcredentials    0    0
//192.168.0.25/Sata1 /media/smbmnt2 smbfs credentials=/root/.smbcredentials    0    0
//192.168.0.25/Sata2 /media/smbmnt3 smbfs credentials=/root/.smbcredentials    0    0
```

I can see the and connect to the Samba shares after Ubuntu is loaded but when I try to auto mount them at bootup they don't mount and when I try to mount using this command:
**sudo mount -a**

I get the following error:
> mount: wrong fs type, bad option, bad superblock on //192.168.0.25/LDrive2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I get the log it returns this for the smb mounts:
> [4296448.283000] smbfs: mount_data version 1684370019 is not supported

These errors are repeated for all three shares. I'm not sure what these mean, especially since I can connect to and access the shares through the Network Servers under Places on the menu, just can't mount them so they show up in the file system. I have some video files on one of them and since they don't show in the file system mplayer doesn't see them. At this point I have to copy a file I want to view to a drive that is seen in the file system before I can view it.

---

### Post by trommelhawks on 2006-06-14
Did you install smbfs?

---

### Post by MrSam on 2006-06-14
No. Didn't know you have to install it. On the other Linux distro I use I didn't have to do that. I'll look and see if I can find instructions on that. If you have a chance a pointer in the right direction would be greatly appreciated.

---

### Post by trommelhawks on 2006-06-14
Use Synaptic and search for the package smbfs (sorry I have no Ubuntu in from of me right now and can not give more details).

---

### Post by MrSam on 2006-06-14
NP - it was enough to get me going. Finally got my dual monitors working yesterday and now I have my shares mounted. I'm 90% to being able to wave goodbye to Bill and the boys in Redmond :D  Have a few more programs to find to replace what I have been using and I'm ready to cut the cord.

Thanks for the help

---

