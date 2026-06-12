---
title: "cdrom (dvd with mp3) automount"
date: 2010-10-10
forum: Mythbuntu
---

### Post by softm on 2010-10-10
It's not work in latest version of mythbuntu
I find out in gui flag where to check, - to automount dvd drive, reboot, still did not work.
Pls can anybody write fstab line or help with this case? 

PS. Also how anyone with pc withount ethernet card (old one 633p3) can install midnight commander here? Where to find repository?

---

### Post by softm on 2010-10-10
> **softm said:**
> It's not work in latest version of mythbuntu
I find out in gui flag where to check, - to automount dvd drive, reboot, still did not work.
Pls can anybody write fstab line or help with this case? 

PS. Also how anyone with pc withount ethernet card (old one 633p3) can install midnight commander here? Where to find repository?


ok, from console this works (in fstab & mount /cdrom):
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Is here any ability to automount this device on disk inserted? 

Pls help me :)

---

