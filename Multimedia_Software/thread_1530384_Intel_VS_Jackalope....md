---
title: "Intel VS Jackalope..."
date: 2010-07-13
forum: Multimedia Software
---

### Post by Catfishsushi on 2010-07-13
Hi,

I know that this isn't a new bug, but as I'm still trying to solve it after a few days (without any success)... well.... I guess that I need some help ?

I installed Jaunty some time ago, and all worked fine. But recently, I just had the brilliant idea to plug in a second screen. Since that time, my graphic card seems to have vanished.

When I go in System > Administrator > Drivers, nothing's displayed. But here's what I got when I do a lspci -v | grep -A 12 VGA


00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0


I tried to use compiz, but it doesn't work anymore; same when I try to change the visual effects. What should I do ? Thanks to anyone who might help me bring my graphic card back !! [-o<

---

