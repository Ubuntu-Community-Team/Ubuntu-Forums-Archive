---
title: "How Do I Copy DVD's? (to ISO's)"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by denson on 2008-01-12
Hey, What Program do you all use to rip DVD's to ISO files?
Thanks!

---

### Post by acuozzo on 2008-01-12
I use the CLI program "vobcopy" to extract large vob files from DVD discs.

---

### Post by gerbman on 2008-01-12
> **denson said:**
> Hey, What Program do you all use to rip DVD's to ISO files?
Thanks!Check out the "dvdrip" package. In addition to ripping the VOBs, it also provides for creating AVI movies for VCDs...plus a lot of other stuff in a nice GUI.

---

### Post by rechick on 2008-01-12
Simple command line:

dd if=cdromdev of=isoname bs=1024

Replace cdromdev with the device for your CDROM/DVD. usually /dev/dvd
replace Isoname with whatever filename you would like: aka myrip.iso

---

