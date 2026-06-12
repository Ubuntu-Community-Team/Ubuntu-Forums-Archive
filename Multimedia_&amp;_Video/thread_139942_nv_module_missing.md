---
title: "nv module missing"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by Haegin on 2006-03-05
My graphics card is complicated as its semi-broken when using the nvidia official drivers so I have a shell script to change between the official driver, the official with tvout and the open source nv driver (for work).
This was working fine with just nv and official (no tv out) but when I was setting up tv-out (I used a guide on here and then tried nvtv, ddnt work so rebooted and now just use nvidia module and a tv section as described in the guide which works fine) something happened and when I now try to load my nv config (for work) it comes up with a message saying it cant find the nv module.
lsmod doesn't pick it up and I cant modprobe it but when I do a locate "nv" there is a file "/usr/X11R6/lib/modules/drivers/nv_drv.o" but X doesnt seem to be able to load it.

Any ideas?

---

