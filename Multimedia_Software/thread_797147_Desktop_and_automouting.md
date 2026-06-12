---
title: "Desktop and automouting"
date: 2008-05-17
forum: Multimedia Software
---

### Post by siddharth_moghe on 2008-05-17
Hi guys,

after installing hardy i find that my disks are not automouting. Even after explicitly specifying in the fstab file.

Also the desktop isnt coming up. Even after putting the entry as xfdesktop in the autostarted applications.

Any one faced the problem or has a solution for the same kindly let me know !

---

### Post by cor2y on 2008-05-17
First to automount rather than fool around with my fstab i used ntfs-g3 like i did for edgy and gutsy.
```
sudo apt-get install ntfs-3g ntfs-config
``` then restart fire up ntfs configuration tool and have your discs mount automatically with write support.
ntfs-3g ships with xubuntu ever since gutsy 7.10

---

### Post by siddharth_moghe on 2008-05-17
i did all that ....i am using linux since 6.04 and now its quiet some time that i have been using ubuntu...but still that doesnt answer my question....Gusty used to show me the drives on my desktop.....Heron doesnt !:confused:

---

### Post by WakkiTabakki on 2008-05-17
Actually the (probably) do get automounted, but default behaviour in Hardy is not to show mounts from mount point /mnt on the desktop, check this post out:
[http://ubuntuforums.org/showthread.php?t=766496](http://ubuntuforums.org/showthread.php?t=766496)

/N

---

### Post by gmoctav on 2008-05-17
> **cor2y said:**
> First to automount rather than fool around with my fstab i used ntfs-g3 like i did for edgy and gutsy.
```
sudo apt-get install ntfs-3g ntfs-config
``` then restart fire up ntfs configuration tool and have your discs mount automatically with write support.
ntfs-3g ships with xubuntu ever since gutsy 7.10


I use a Hardy ,and worked for me.Thanks

---

