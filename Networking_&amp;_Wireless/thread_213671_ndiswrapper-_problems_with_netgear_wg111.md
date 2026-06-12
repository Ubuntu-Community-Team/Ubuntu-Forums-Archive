---
title: "ndiswrapper- problems with netgear wg111"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by el_ricardo on 2006-07-11
hello, just yesterday i conquered installing the drivers for a wg111 wireless dongle, i found it much easier than it had proved in the past, but it seems to have stopped working. I turned my computer on today to find that i was no longer connected to my home network, apprantly the hardware wasn't present or something, so i deleted, and reinstalled the driver, in hope that this would solve things, unfortunately not, when i gave the command "sudo ndisrwapper -m" the modprobe told me:

```
module configuration contains directive install usb:vo846p4330d*dc*dsc*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc**ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule config already contains alias directive
```

frankly i'm stumped

---

### Post by el_ricardo on 2006-07-12
bump

come on, someone must have an idea

---

### Post by eternalsword on 2006-07-15
please post the results of lsmod

---

### Post by eternalsword on 2006-07-15
you might also want to try

sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

---

