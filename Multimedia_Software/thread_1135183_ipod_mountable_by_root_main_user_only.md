---
title: "ipod mountable by root main user only"
date: 2009-04-24
forum: Multimedia Software
---

### Post by hollowhead on 2009-04-24
I want to make all the ipods plugged into both linux machines mountable by me the administrator user or root.  On this machine my fstab has this entry

/dev/sda2 /media/ipod vfat user,sync,rw,noauto,umask=000 0 0

I changed this to 

/dev/sda2 /media/ipod vfat nouser,sync,rw,noauto,umask=000 0 0

although it obviously requires a reboot on my system to take effect.

On the desktop machine there is no entry for ipods in fstab.  The system log sees ipods as dev/sdb1 on media/ipod.  Can I create an entry analogous to above?  Why the difference on identical versions of intrepid? Also how do I access the pod?

sudo mount /dev/sdb1 /media/ipod ?

then sudo rhythmbox to delete or sync files?

Ta.

---

