---
title: "tv-tuner msi"
date: 2008-10-06
forum: Multimedia Software
---

### Post by vitality on 2008-10-06
Hello! I have a tuner msi tv@nywhere with driver cx88xx. At first pc didn't saw it:

dmesg
cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
cx88[0]: be autodetected.

I've wrote info about it in flie 
/etc/modprobe.d/options
've put there - options cx88xx card-13

dmesg gave new results:

cx88[0]/0: found at 0000:01:08.0, rev: 3, irq: 21, latency: 32, mmio: 0xdf000000
cx88[0]: subsystem: 0000:0000, board: MSI TV-@nywhere [card=13,insmod option]
cx88[0]: TV tuner type 33, Radio tuner type -1

Though i had no reason to be glad 'cause tvtime showed me blue screen with such message:

No signal
Format unsupported by surfer model sn-206
Cannot capture device /dev/video0.

Could you advice me something?

---

### Post by cariboo on 2008-10-06
I have a TV@nywhere, but it is based on the saa7134 chipset, so my setup won't work for you. Have a look at this page:

[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))

The wiki was great help to get my tv tuner card to work properly.

Jim

---

