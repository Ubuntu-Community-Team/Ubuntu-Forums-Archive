---
title: "Cant mount my samba drives"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by venturax on 2009-11-28
Hi,

I have a Buffalo Live link station 1TB, which is connected to my lan.

From my windows laptop theres no problem accessing the samba drive.
From my Linux laptop, i can access the samba drive from Krusader, by selecting network connect to smb://192.168.1.34/

However I would like to mount the drive on startup or just be able to mount it from the command line (so i can add it to fstab later).

I have used the following command:
```
sudo mount -t cifs //192.168.1.34/share /mnt/linkstation/
```
I use cifs, since syslog complains that smbfs is deprecated.

But is doesnt work :-( I get the following error:
```
mount: wrong fs type, bad option, bad superblock on //192.168.1.34/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Syslog tells me:
```
Nov 28 09:41:58 lundtor-laptop kernel: [ 1620.337709]  CIFS VFS: cifs_mount failed w/return code = -22
```

Any pointers what to do next?!?

---

### Post by capscrew on 2009-11-28
Do you have the *smbfs *package installed?

---

### Post by venturax on 2009-11-28
> **capscrew said:**
> Do you have the *smbfs *package installed?
no I didn't and after installing, it works.

Thanks!!!;)

---

