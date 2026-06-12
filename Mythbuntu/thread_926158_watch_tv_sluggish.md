---
title: "watch tv sluggish"
date: 2008-09-21
forum: Mythbuntu
---

### Post by Dopan on 2008-09-21
hey all just rebuilt another box with mythubuntu. i finally been able to get hvr3000 card working with the help of another user here thanks! :) 


now the issue appears to be the ability to watch tv. using dvb-s and dish ive scanned and picked up all the freetoair channels, when i go into mythtv and select watch tv though its very slow, sluggish. any ideas on this ? i though it might have been machine so i reinstalled onto a much higher spec machine and still having same problem


the 1st machine was a p4 2.8ghz with 1gb ram, ati card. the 2nd machine was a quad core 2.4ghz with 2gb ram, nvida 512mb card..

is there something im missing as well ?

---

### Post by newlinux on 2008-09-21
what do you mean by slow and sluggish? Is the video slow, or response to the keyboard/remote, tuning channels?

---

### Post by Dopan on 2008-09-22
> **newlinux said:**
> what do you mean by slow and sluggish? Is the video slow, or response to the keyboard/remote, tuning channels?

yeah video slow, jerky and unwatchable..

---

### Post by newlinux on 2008-09-22
take a look at your frontend logs for any errors - beyond that you probably need to adjust your playback profiles - try CPU++. You may need to create a new one or modify an existing one.

---

### Post by house82 on 2008-09-22
Post your
```
cat /var/log/mythtv/mythfrontend.log
```

I've had the same problem with my ATI card. XV was disabled on it by default and the frontend was trying to play the video through the X sockets with symptoms exactly the same as you have described (with the addition to 90% CPU utilization by the frontend). Once I got XV to work the playback became nice and smooth at less than 10% CPU on AMD Sempron 2100+ fanless CPU.

---

