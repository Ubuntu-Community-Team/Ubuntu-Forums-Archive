---
title: "advise for forcing the exec bit for read only?"
date: 2011-04-28
forum: Multimedia Software
---

### Post by ToFue on 2011-04-28
I hope this is the right forum for this, if not please forgive me! :p

I was pondering the issue of trying to run stuff from CD or DVD ROMS >without< copying to my cluttered hard drive, and came to a thought that I'd like evaluated:

 Would it work to perhaps use sed during the cd-rom auto-mount or some other point to enable the executable bit for *.exe and other 'executables' to somehow override the read only factor? 

I'm not too familiar with sed except that i know it can insert/replace new patterns of data for defined patterns of existing data.. so would something like this work? 

 Could it be implemented as permanent function of Ubuntu to 'checkbox' cd/dvd mounts to insert the exec' bit on all, known, or choice files as a sort of 'virtual' permissions that can be placed on RO mounts?

---

### Post by mc4man on 2011-04-28
There is really no need to force anything - you just have to stop using the cautious-launcher.
You could create a r. click using wine as the command or edit the wine.desktop, [plenty of ex.'s here]("http://ubuntuforums.org/showthread.php?t=1740105")

Or if just for optical drives then create the mountpoint  and return the typical fstab entry for a cd/dvd drive(s) 

Ex. /dev/sr0
```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0 

```

---

### Post by ToFue on 2011-05-13
Thanks for that!

---

