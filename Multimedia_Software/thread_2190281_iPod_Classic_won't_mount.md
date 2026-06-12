---
title: "iPod Classic won't mount"
date: 2013-11-26
forum: Multimedia Software
---

### Post by jmelton on 2013-11-26
My iPod (80 gb 5th generation classic) shows as connected but will not mount. As per the how to, I edited fstab to include a line for the device: 
/dev/sdb1 media/ipod vfat user,noauto,umask=000 0 0
Then attempted to mount: sudo mount /dev/sdb1 and got:

mount: /dev/sdb1: can't read superblock

What do I do?

---

### Post by thatredbird on 2013-11-26
I had to add a package to get mine to load, however there may be other options out there

[http://www.wikihow.com/Manage-an-iPod-in-Linux](http://www.wikihow.com/Manage-an-iPod-in-Linux)

---

