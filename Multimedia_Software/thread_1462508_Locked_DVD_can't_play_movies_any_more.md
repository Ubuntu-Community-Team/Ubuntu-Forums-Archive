---
title: "Locked DVD: can't play movies any more"
date: 2010-04-25
forum: Multimedia Software
---

### Post by insane2600tt on 2010-04-25
Hi, Everybody,

I'm writing because my DVD refuses to do the REGIONSET and let me see my dvds. I commute very often between US and Europe (ie region 1 and 2) and I have 45 dvd in region1 and 50 in region2. After using `sudo regionset` for about 5/6 times, my drive seems locked to region1. Any idea about how to watch my dvds??

:popcorn:

```

sudo lshw -C disk
  *-cdrom
       description: DVD writer
       product: UJ-822Da
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

Thank you!
Marco.

---

