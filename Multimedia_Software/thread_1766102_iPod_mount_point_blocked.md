---
title: "iPod mount point blocked???"
date: 2011-05-23
forum: Multimedia Software
---

### Post by Codecaine_21 on 2011-05-23
i tied to plug my ipod in just now and it says connected on the ipod but is not mounting on my ubuntu desktop or with gtkpod. i also have a g1 plugged in via usb with an 8gb mem card mounted on the phone but that wont mount on the computer either. Oddly my usb flash drive will mount. i forgot where i seen the message but it says that my ipod is blocked from being mounted. I ran mount on the commandline and it said nothing about an ipod or android phone at all. i can see the devices in /dev/disk/by-label/. And it shows iPod my g1 and my live cd. btw i am running a live cd because of my faulty hard drive

*********!!!!!SOLVED!!!!!**********

---

### Post by backu on 2011-05-23
Try mounting it thru System -> Administration -> Disk Utility

---

### Post by Codecaine_21 on 2011-05-24
It was mounted in sys->admin->du but wasn't showing on my desktop or gtkpod or anywhere else but sys->admin->du. So I unmounted my iPod in sys->admin->du then repaired disk then re-mounted it fixed the problem. Thanks backu

---

### Post by backu on 2011-05-24
Not that I did much, but your welcome.

---

