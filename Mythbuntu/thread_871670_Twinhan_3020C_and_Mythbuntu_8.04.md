---
title: "Twinhan 3020C and Mythbuntu 8.04"
date: 2008-07-27
forum: Mythbuntu
---

### Post by ryangus on 2008-07-27
I've just installed Mythbuntu 8.04 and I'm having difficulty getting it to recognise my Twinhan 3020C.

dmesg shows the following:

    [ 38.049860] bttv: driver version 0.9.17 loaded
    [ 38.049864] bttv: using 8 buffers with 2080k (520 pages) each for capture
    [ 38.049917] bttv: Bt8xx card found (0).
    [ 38.050134] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
    [ 38.050141] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
    [ 38.050150] bttv0: Bt878 (rev 17) at 0000:02:09.0, irq: 20, latency: 32, mmio: 0xe6000000
    [ 38.050236] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
    [ 38.050239] bttv0: using: Twinhan DST + clones [card=113,autodetected]
    [ 38.050254] bttv0: gpio: en=00000000, out=00000000 in=00f500ff [init]
    [ 38.050281] bttv0: tuner absent
    [ 38.050293] bttv0: add subdevice "dvb0"
    [ 38.083395] bt878: AUDIO driver version 0.0.0 loaded
    [ 38.083436] bt878: Bt878 AUDIO function found (0).
    [ 38.083454] ACPI: PCI Interrupt 0000:02:09.1[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 20
    [ 38.083460] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
    [ 38.083466] bt878(0): Bt878 (rev 17) at 02:09.1, irq: 20, latency: 32, memory: 0xe6001000
    [ 38.161645] DVB: registering new adapter (bttv0)

It seems the card is being detected, but when I go into MythTV it doesn't see anything at all in Input Connections.

The only thing I've done so far is add the following to /etc/modules, to no avail:

    dvb-bt8xx
    dst
    dvb_core

I was having the same problem after installing the card and MythTV on my previous Ubuntu 8.04 build, so I thought perhaps starting again with Mythbuntu might fix the problem, but no luck. I'm fairly new with Linux, so any help would be most appreciated. I've searched a fair bit in OCAU and Ubuntu forums, but can't seem to find a fix.

From my research, it seems the card should just work, as others have managed to install it with MythTV with no fuss.

Any ideas?

---

### Post by laga on 2008-07-27
You need to set up your card first in mythtv-setup (second step) before you can see it in the "input connections" screen (third step).

---

