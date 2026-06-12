---
title: "aircrack suite and ndiswrapper"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by zenial on 2009-01-23
I AM RUNNING KUBUNTU 8.10
I HAVE A "WG111v2 netgear usb wireless adapter"
DOES ANYBODY KNOW WHICH DRIVER I NEED TO install in "NDISWRAPPER" to RUN THE AIRCRACK SUITE AND ALSO BE ABLE TO CONNECT to wireless networks..

---

### Post by Ayuthia on 2009-01-23
You can't use NDISwrapper with aircrack.  It is most like because NDISwrapper wraps the Windows wireless driver where aircrack needs to have a linux module to use (I think).

---

### Post by jrusso2 on 2009-01-23
My understanding is that to use aircrack you need a card that can run in promiscuous mode and even a lot of the linux drivers don't do this.

---

### Post by Ayuthia on 2009-01-24
> **jrusso2 said:**
> My understanding is that to use aircrack you need a card that can run in promiscuous mode and even a lot of the linux drivers don't do this.

I am pretty sure that you are right.  There should be a list of compatible drivers at the aircrack-ng site.

---

### Post by zenial on 2009-01-24
ok ive been reading around but
ineed a driver that is both compatible with the aircrack suite and that lets me connect to wireless networks using the manager;)
ANY IDEAS?

---

### Post by Zewbie on 2009-01-24
If you running Ubuntu 8.1 the patched drivers for your wireless card should be automatically applied when installed if your wifi card supports airmon-ng mode

---

### Post by zenial on 2009-01-24
THE DRIVER THAT IS PRE INSTALLED IN KUBUNTU ARE BUGGY SO I NEED A DIFFERENT DRIVER
"WG111v2" netgear\\:D/

---

