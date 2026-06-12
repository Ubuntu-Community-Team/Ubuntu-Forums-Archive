---
title: "ATI Radeon Sapphire X550 with low performance"
date: 2010-05-09
forum: Multimedia Software
---

### Post by revberaldo on 2010-05-09
I've just installed Ubuntu 10.04 here and got a problem. My video card has a unusable performance when I activate the visual effects. Here is lspci -vv output for the video card:

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
    Subsystem: PC Partner Limited Device 1500
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 50
    Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at ac00 [size=256]
    Region 2: Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at dfdc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

```

As you can see it is using the open source driver for ATI video cards. I think Ubuntu 9.10 was using the proprietary driver but I'm not really sure. I tried to activate it through ‘hardware drivers’ menu but Ubuntu won't find any driver.

Also, I've searched the forum just to find nothing about it.

I'll be very glad if someone can help.

---

