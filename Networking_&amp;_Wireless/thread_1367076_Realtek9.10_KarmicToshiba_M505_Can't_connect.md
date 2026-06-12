---
title: "Realtek/9.10 Karmic/Toshiba M505: Can't connect"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by derekmbarnes on 2009-12-29
Fellow users who have probably heard this a million times:

I just loaded Ubuntu 9.10 on my new laptop, and in the process lost access to my wireless LAN. The laptop is a Toshiba Satellite M505, equipped with a Realtek wireless card (not sure on exact model). The originally installed Windows OS had no trouble locating and using my router, but now Network Connections shows no wireless connection at all. (Wired: "auto eth0" shows up fine.)

I tried to troubleshoot this myself and felt like I was in too far over my head; I think I'm missing a driver, but I'm not sure. And being high and mighty as I was about making the switch to Linux, I erased the Windows OS completely during installation instead of partitioning the drive between the two systems like I probably should have; so I no longer have that as a resource.

Code I got from Terminal after trying lshw:

```

*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd
vendor: Realtek Semiconductor Co., Ltd
physical id: 0
bus info: pci@0000:07:00.0
version: 10
width: 32 bits
clock: 33 MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: ioport:e800(size=256) memory:febfc000-febfffff

```

How do I fix this? Your help is greatly appreciated.

Derek M. Barnes
Knocking his head against the wall

---

### Post by wafflemelon on 2009-12-29
First of all...
How did you get your fan working? I have the exact same model, but linux doesn't turn it on.

---

### Post by derekmbarnes on 2009-12-30
Uh...I was lucky? I don't know. Did you check your disk for defects before installing?

In any case, problem solved:

[http://ubuntuforums.org/showthread.php?p=8580320#post8580320](http://ubuntuforums.org/showthread.php?p=8580320#post8580320)

---

