---
title: "LG HD-DVD/Blu Ray Drive, only Blu ray's are browseable"
date: 2008-12-30
forum: Multimedia Software
---

### Post by jimmah6786 on 2008-12-30
Hello All,

Something strange is going on with my ubuntu 8.04.1 installation. I have patched my UDF2 to UDF2.5 via instructions from the forums. If I put in a blu ray video retail disc it reads the file structure fine. Here is the strange part I put in a HDDVD (several trys with different retail videos) and it recognizes the disc label, but not the file structure. No files show up. I know my drive can read both blu ray and hd dvd, so that is not the issue.

I am wondering if there is anything I could try to get this to work. Help, as always, is appreciated.

Hardware: 
LG Dual Formate Blu Ray/HD-DVD drive. (connected via USB 2.0 custom external bay)


Thanks, :popcorn:

Jim

---

### Post by mc4man on 2008-12-31
I was slightly curious about this and happen to have an xbox hd dvd drive and 1 hd dvd (the included kk

Even with udf 2.50 enabled same thing, nothing visible in the browser.

So I opened the mount point (media/cdrom2) as root and everything is visible.

Sorta born out here 
> doug@doug-desktop:~$ ls -l /media/cdrom2
ls: cannot access /media/cdrom2/AACS: Permission denied
ls: cannot access /media/cdrom2/HVDVD_TS: Permission denied
ls: cannot access /media/cdrom2/ADV_OBJ: Permission denied
ls: cannot access /media/cdrom2/AACS_BAK: Permission denied
total 0
?????????? ? ? ? ?                ? AACS
?????????? ? ? ? ?                ? AACS_BAK
?????????? ? ? ? ?                ? ADV_OBJ
?????????? ? ? ? ?                ? HVDVD_TS
doug@doug-desktop:~$ sudo ls -l /media/cdrom2
total 8
dr--r--r-- 2 4294967295 4294967295  616 2006-09-19 00:18 AACS
dr--r--r-- 2 4294967295 4294967295  556 2006-09-19 00:18 AACS_BAK
dr--r--r-- 2 4294967295 4294967295  256 2006-09-19 00:18 ADV_OBJ
dr--r--r-- 2 4294967295 4294967295 1028 2006-09-19 00:18 HVDVD_TS



Edit: it's also not detected as "HD DVD Video" until it's opened as root or in a bit of an 'oddity' if you have **any** directory opened as root when the disk is inserted it's recognized and you'll either get a popup or totem will open.

The auto run in this case isn't controlled by nautilus -> edit -> preferences -> media -> other media..., but by gksudo nautilus -> edit -> preferences -> media -> other media...

---

### Post by jimmah6786 on 2008-12-31
> **mc4man said:**
> I was slightly curious about this and happen to have an xbox hd dvd drive and 1 hd dvd (the included kk

Even with udf 2.50 enabled same thing, nothing visible in the browser.

So I opened the mount point (media/cdrom2) as root and everything is visible.

Sorta born out here 


Edit: it's also not detected as "HD DVD Video" until it's opened as root or in a bit of an 'oddity' if you have **any** directory opened as root when the disk is inserted it's recognized and you'll either get a popup or totem will open.

The auto run in this case isn't controlled by nautilus -> edit -> preferences -> media -> other media..., but by gksudo nautilus -> edit -> preferences -> media -> other media...

Genius!! Thank you so much.

---

