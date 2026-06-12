---
title: "wireless drivers"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by bradpurvis on 2009-10-29
i'm using ubuntu 9.10 and it did not show that i didn't have wireless drivers for my laptop, it detected what type of network controller i have but it didn't download them like every other ubuntu version i've tried

this is what it said on the system testing app,

Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Realtek Semiconducto Co., Ltd. RTL-8139/8139C/8139C+ (REV10)


if you can help or direct me to someone who has the same problem it would be great :)

---

### Post by Crafty Kisses on 2009-10-30
Hey, some people are saying if you have access to a LAN connection you can install the following package:
```
bcmwl-kernel-source
```
Then that should solve your problem, I'm not sure though. Just what I've heard. Hope this helps.

---

### Post by maxrpowell on 2009-10-30
It did not work for me, i hit the activate button and it did nothing

---

### Post by bradpurvis on 2009-10-30
is there another thread post or anything someone could direct me to with an answer in it? if not then BUMP

---

### Post by iliketv01 on 2009-10-30
Is there anyway to install the bcmwl-kernel-source package without an internet connection?

Can I download in winxp, put it on a usb stick and then put install it on ubuntu?

---

### Post by ninjatiger422 on 2009-10-30
Try System > Administration > Hardware Drivers

Activate a driver and restart. Worked for me on Dell Inspiron 1525 w/ Broadcom drivers.

---

### Post by bradpurvis on 2009-10-30
wtf, it didn't work before and i checked anyway and now its working

the window used to not even come up lol

---

### Post by iliketv01 on 2009-10-30
I tried the hardware driver thing and it doesn't show any hardware drivers in the window. Any reason why?

---

