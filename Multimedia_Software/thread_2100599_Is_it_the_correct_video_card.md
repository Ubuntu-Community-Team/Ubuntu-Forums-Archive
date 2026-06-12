---
title: "Is it the correct video card?"
date: 2013-01-02
forum: Multimedia Software
---

### Post by Graham C Williams on 2013-01-02
Ubuntu 12.10 64bit Acer Aspire 8935G ATI 4670.
Well the Video is a bit slow at times and the HDMI O/P don't work correctly or works for only a few seconds when closing down. I decided to investigate.

1) Looking at System Settings / Details I get:

Processor: Mobile Intel GM45 Express Chipset 
Experiance: Standard

With no mention of ATI..

2) Running lspci|grep VGA gives me:
> Aspire-8935G:~$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV730 XT [Mobility Radeon HD 4670]

Are things as they should be or am I running the chipset video instead of the ATI? How should I change it if need be.

Wishing everyone a happy new year.
G.

---

### Post by Graham C Williams on 2013-01-02
That site gives me a load of advertising rubbish. I use Linux to get away from all the sh.. that came with Uncle Bills products.
There must be a better way.

G.

---

### Post by coffeecat on 2013-01-02
> **Graham C Williams said:**
> That site gives me a load of advertising rubbish.

I've removed the spam post.

---

### Post by Graham C Williams on 2013-01-02
Oh Thanks Coffeecat.

---

