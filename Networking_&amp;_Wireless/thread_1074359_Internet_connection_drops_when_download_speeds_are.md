---
title: "Internet connection drops when download speeds are high."
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by JasonDFR on 2009-02-19
Downloads at 500K - 1MB / sec cause my internet connection to fail. Sometimes almost immediately. Other times after 30 - 60 seconds.

We have a XP machine connected to the same DSL/Router and this problem does not occur.

I installed the r8168 kernal driver as suggested by another poster on this forum. This did not solve the problem.

I think the problem may be with my Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111, but I really have no idea...

This problem occurs on other distributions as well, fedora, mint, debian...

I can post any more information that is necessary. Thanks!

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at d000 [size=256]
	Memory at e9000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8168
	Kernel modules: r8168

```

```
jasondeb@jasondeb-desktop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5b:03:0b  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1842695 (1.8 MB)  TX bytes:289065 (289.0 KB)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2728 (2.7 KB)  TX bytes:2728 (2.7 KB)
```

---

### Post by JasonDFR on 2009-02-19
[http://ubuntuforums.org/showthread.php?t=582453](http://ubuntuforums.org/showthread.php?t=582453)

Found the above post on these forums. Seems to be the same problem, but no solution. The last poster says he made a script to fix the problem, but I am concerned about running his script without knowing any more than I do.

---

### Post by JasonDFR on 2009-02-19
I have done absolutely everything I could think of or read about including updating my motherboard bios to the latest version, but nothing works.

Anytime download speeds are high, the internet connection is lost.

---

### Post by JasonDFR on 2009-02-20
I think the router is at fault.

Hooked up the ethernet cable to my wife's WinXP laptop and the exact same thing happened.

What could cause an ASDL modem / router to do this?

Thanks everyone!

---

### Post by superprash2003 on 2009-02-20
you could try resetting your router!!

---

### Post by JasonDFR on 2009-02-21
> **superprash2003 said:**
> you could try resetting your router!!

That's the first thing I tried!!

The router was bad. Exchanged it for a new one and the problem has gone away.

---

### Post by wadesmart on 2009-02-21
You said that is the first thing you tried but how is ANYONE to know what you tried. 

You need to post your router make and model and modem make and model for any real help.

Wade

---

