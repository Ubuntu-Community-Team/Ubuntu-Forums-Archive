---
title: "Automount of CDs in Hardy"
date: 2008-07-27
forum: Multimedia Software
---

### Post by fattom23 on 2008-07-27
I'm using Hardy Heron at home.  This isn't a huge problem, more of an annoyance.  when Ubuntu automounts a CD-ROM, it mounts it under the /media directory with the name of the CD.  I would really like it to auto-mount any disc that's in that drive as /media/cdrom0.  My fstab has this instruction, but something somewhere is informing the system that it should be mounting the disc as its title.  Anyone out there got any ideas of how to fix this?  Thanks a million for your help.

---

### Post by mc4man on 2008-07-27
Having data cds mount in /media/<volume name> is the default when there is no fstab entry for the device (drive)
Maybe post your fstab and what running this shows ```
sudo lshw -C disk
```

---

### Post by fattom23 on 2008-07-28
Hey, I figured it out.  My fstab was configured with the wrong device name.  Once I changed that, it works like a charm.  Thanks again for the help.

---

