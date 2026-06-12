---
title: "Finding the correct path"
date: 2012-09-13
forum: Multimedia Software
---

### Post by LaughingHorse on 2012-09-13
Hi!

I'm trying to rip a dvd I recorded using Acidrip
It is asking for a path. It defaults to 
/dev/dvd but that is not the correct path.

So I did some research and first used 
System Monitor and saw

Device: /dev/sr0
Directory: /media/VRD_VC30

I tried entering:
/sr0/media/dvd
/sr0/media/VRD_VC30
/media/dvd
 /media/VRD_VC30

And each time got an error [path name] does not exist!

So I opened a terminal and typed: df
My output was: 
Filesystem      1K-blocks      Used               Available           Use%    Mounted on
/dev/sdb6        98429572   7983204          85446432             9%            /
udev              8186332         4                           8186328              1%          /dev
tmpfs             3278092      1008                     3277084                1%        /run
none                        5120               0                          5120              0%       /run/lock
none                 8195224                      388            8194836          1%      /run/shm
/dev/sdb1              235115             47334               175237        22%    /boot
/dev/sdb7      1792683288    211158960     1490461240      13%     /home
/dev/sr0          4586974                 4586974          0                 100%     /media/VRD_VC30

Can someone please tell me the correct path I need to enter?

Thanks!

---

### Post by cjhabs on 2012-09-13
Did you try /dev/sr0

---

### Post by LaughingHorse on 2012-09-13
That worked.
Thank You!

---

