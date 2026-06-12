---
title: "bttv/hauppage video capture card IRQ 0"
date: 2011-08-12
forum: Multimedia Software
---

### Post by Noccy on 2011-08-12
Hi all,

I just installed a Hauppage video capture card in my box, but it fails to initialize. For some reason the card seem to want to claim IRQ 0 which causes the driver to frown.

Nothing shows up for any V4L applications, and for all intents and purposes it's like the card isn't even there.

How can I get this thing working properly?

uname -a
```

Linux noccy-desktop 2.6.39.4-zen+ #18 ZEN SMP PREEMPT Fri Aug 12 02:03:03 CEST 2011 i686 i686 i386 GNU/Linux
```

dmesg | grep bttv
```

[   33.148152] bttv: driver version 0.9.18 loaded
[   33.148156] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   33.148209] bttv: Bt8xx card found (0).
[   33.148223] bttv 0000:04:01.0: enabling device (0004 -> 0006)
[   33.148234] bttv 0000:04:01.0: setting latency timer to 64
[   33.148241] bttv0: Bt878 (rev 8) at 0000:04:01.0, irq: 0, latency: 0, mmio: 0x80000000
[   33.148286] bttv0: subsystem: 002c:0002 (UNKNOWN)
[   33.148292] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   33.148297] bttv0: can't get IRQ 0
[   33.148615] bttv: probe of 0000:04:01.0 failed with error -16
```

lspci -v
```


04:01.0 Unclassified device [0002]: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Pinnacle Systems Inc. PCTV pro (TV + FM stereo receiver)
	Flags: medium devsel
	Memory at 80000000 (32-bit, prefetchable) [disabled] [size=4K]
	Capabilities: [04] #00 [8290]
	Kernel modules: bttv
```

---

### Post by tkteun on 2012-04-24
Did you solve this?

I'm running into the same problem:

```
[   12.013806] bttv: driver version 0.9.19 loaded
[   12.013812] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   12.015050] bttv: Bt8xx card found (0)
[   12.015079] bttv 0000:02:07.0: setting latency timer to 64
[   12.015086] bttv: 0: Bt878 (rev 17) at 0000:02:07.0, irq: 0, latency: 64, mmio: 0xe70d0000
[   12.015118] bttv: 0: subsystem: 2020:0080 (UNKNOWN)
[   12.015121] bttv: 0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   12.015127] bttv: 0: can't get IRQ 0
[   12.019540] bttv: probe of 0000:02:07.0 failed with error -16
```

```
02:07.1 Multimedia video controller: Fujitsu Microelectronics Ltd. Device 036e (rev 11)
	Subsystem: Device 0020:0080
	Flags: bus master, medium devsel, latency 0, IRQ 32
	Memory at e70d3000 (32-bit, prefetchable) [size=256]
	Memory at e70d3110 (type 3, prefetchable) [size=16]
	Memory at e5000000 (type 3, non-prefetchable) [size=32]
	[virtual] Expansion ROM at e70d2000 [disabled] [size=4K]
	Capabilities: [20] #be [0878]
	Capabilities: [10] HyperTransport: Slave or Primary Interface
```

---

### Post by Noccy on 2012-04-24
I was unable to find a solution to this problem, so I ended up reaching the conclusion that the card itself was faulty or damaged and removed it from my system as it seemed to cause intermittent system lockups. But seeing as your error is pretty much identical to mine I will dig it out again and see if there's any other solution.

You could try to go into your BIOS setup and see if changing the setting for "Plug-and-Play OS" has any effect, and if it makes it try to request another IRQ besides IRQ 0.

Hopefully your bump on this topic will get some attention from the kernel hackers on here :)

---

