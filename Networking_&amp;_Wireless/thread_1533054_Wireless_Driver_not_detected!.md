---
title: "Wireless Driver not detected!"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by WitchBlade on 2010-07-17
im on compaq presario cq40 (amd64 turion x2) and recently install ubuntu.10.04 using wubi with dual os.. im installed wireless braodcom BCM4312 802.11b/g LP-PHY 'bcm43xx-fwcutter_006-3_amd64.deb' driver for my laptop and restart my machine.. when i go to > hardware dirver, there is no driver installed.. any suggestion? or lists any driver compatible with my laptop.. tq in advanced!

---

### Post by gnulab on 2010-10-08
try using ndiswrapper method. Google it.

I'm a newbie too, but I don't think just because you CPU is amd64, that means you should be using _amd64.deb driver. The '64' simply means that it can support 64-bit OS.

Anyway, upon further reading about ndiswrapper method, you'll see that the ndiswrapper method is more recommended rather than using bcm43xx.

One caveat about Windows Broadcom driver, assuming that your laptop is using the same wireless card as my CQ40-324TU which is using this 

```

lspci -vnn

2:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

You MUST download the Windows XP driver, not the Vista nor Win7 driver. The XP driver is no longer available at [www.hp.com](www.hp.com), you should download it from here [ftp://ftp.hp.com/pub/softpaq/sp39501-40000/sp39912.exe]("ftp://ftp.hp.com/pub/softpaq/sp39501-40000/sp39912.exe")

Hope this helps in someway.
Henry

---

