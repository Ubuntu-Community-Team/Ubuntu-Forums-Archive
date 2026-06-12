---
title: "Problem mounting iPod"
date: 2009-09-27
forum: Multimedia Software
---

### Post by CarlWalters on 2009-09-27
Hell all, I'm having big problems trying to mount my iPod. I'm running Ubuntu 8.10 and plugging in an iPod Nano 2nd Gen 8GByte. In a console window I type

[FONT="Courier New"]carl@carl-desktop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2009-09-27 10:54 .
drwxr-xr-x 6 root root 120 2009-09-27 10:54 ..
lrwxrwxrwx 1 root root  10 2009-09-27 10:54 CARL\x27S\x20IPOD -> ../../sdd2
[/FONT]
and if I then try to mount the iPod I get

[FONT="Courier New"]carl@carl-desktop:~$ pmount /dev/sdd2 /media/ipod
Error: device /dev/sdd2 is not removable
[/FONT]

adoes anyone have any idea what I'm doing wrong please?

---

