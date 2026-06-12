---
title: "cannot enable wireless?"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by EvoFX on 2010-08-26
i have recently installed ubuntu and my wireless card broadcom BCM4318 for my desktop will not enable to connect

i have used 

sudo ifup wlan0

and i get ignoring unknown interface wlan0=wlan0.


i have searched and found some other people having hte same problem and not really any answers. or atleast something that i could find

---

### Post by BkkBonanza on 2010-08-26
Post output from **sudo ifconfig -a**
If the interface isn't listed then likely the drivers aren't getting loaded correctly.

---

