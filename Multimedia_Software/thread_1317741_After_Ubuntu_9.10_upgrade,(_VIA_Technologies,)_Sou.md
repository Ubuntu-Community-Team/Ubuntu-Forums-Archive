---
title: "After Ubuntu 9.10 upgrade,( VIA Technologies,) Sound system is not working"
date: 2009-11-07
forum: Multimedia Software
---

### Post by binukavumkal on 2009-11-07
After Ubuntu 9.10 upgrade,( VIA Technologies,) Sound system is not working
=========================================================

I upgraded Ubuntu 9.04 to 9.10. After upgrade sound system is completely broken. 
I am not able to here any sound either from Multimedia Stereo Speakers, PC Speaker.

I went thru the Comprehensice guide in this section.

aplay -l in the command prompt complains

No sound card found in your system

lspci -v gives the following information

..............
.
.
.
.

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: VIA Technologies, Inc. Device 4161
	Flags: medium devsel, IRQ 5
	I/O ports at dc00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx



Any idea to fix this?

---

### Post by M3xital on 2009-11-07
I have the same problem, after the upgrade to 9.10 sound is not working anymore.

```
 aplay: device_list:223: No sound card found on your system...
```
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0096
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 

```

---

### Post by binukavumkal on 2009-11-07
Hi All,

It seems there IS a problem with 9.10 Distribution.  I reverted the distribution back to 9.04 as follows.

In root privilege :

1. Make copy of existing sources.list at /etc/apt/
2. Go thru the different versions of sources.list to see the jaunty version
3. Copy the content to of 2 sources.list

3. Restart the Ubuntu in recovery mode.

4. Select the option: Repair the packages

5. Press Y to install the packages


Once it is completed again restart the machine and once after logged in I am able to see sound system is working fine.

---

