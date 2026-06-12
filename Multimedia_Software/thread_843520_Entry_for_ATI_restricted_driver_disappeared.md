---
title: "Entry for ATI restricted driver disappeared"
date: 2008-06-28
forum: Multimedia Software
---

### Post by MrMatt2532 on 2008-06-28
The entry for the ATI restricted driver disappeared from the "Hardware Drivers" program ever since I started using the new kernel 2.6.24-19. In addition, video acceleration is clearly not running correctly/running at full speed. I can fix all of this by picking kernel 2.6.24-18 from grub. That is, the entry shows up in "Hardware Drivers" and video acceleration works correctly. 

So your probably thinking that I should just not use kernel 2.6.24-19. This seems reasonable, but upon further investigation, i went to an even older kernel, 2.6.24-16, which definitely worked correctly in the past. I found that it now behaves the same as 2.6.24-19, i.e. no entry in "Hardware Drivers" and video acceleration is not working correctly.

Anyways, this leads me to believe that this is some sort of software problem, and that something needs the be reinstalled/recompiled to fix things up correctly. Please help me out. Thank you.

---

### Post by MrMatt2532 on 2008-06-28
bump!!

---

### Post by markbuntu on 2008-06-28
Ok. How about a little more info. What ATI card are you using and which driver?

---

### Post by MrMatt2532 on 2008-06-28
> **markbuntu said:**
> Ok. How about a little more info. What ATI card are you using and which driver?
It's an X600 mobile. The driver is the one that is installed after a clean installation from "Hardware Drivers". So i guess that's the fglrx restricted driver. Thanks.

---

### Post by markbuntu on 2008-06-29
Ok, does the Xorg.o.log say that fglrx is being loaded?
You can see that by going to System/Adminstration/System Logs. If it is not there then use edit/open that will open in the var/log directory where many of the logs reside.

---

### Post by MrMatt2532 on 2008-06-29
> **markbuntu said:**
> Ok, does the Xorg.o.log say that fglrx is being loaded?
You can see that by going to System/Adminstration/System Logs. If it is not there then use edit/open that will open in the var/log directory where many of the logs reside.

Ok, it attempts to load it, but it eventually says that it failed to load kernel module fglrx. Then it goes on to say that 2d and 3d acceleration is unavailable.

---

### Post by MrMatt2532 on 2008-06-29
bump

---

### Post by markbuntu on 2008-06-30
Well, the ATI driver release site says your mobility x600 is supported. so something very weird is going on.

Please post any(EE) messages from the Xorg.0.log.

---

