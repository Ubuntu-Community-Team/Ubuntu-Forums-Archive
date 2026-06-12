---
title: "Audio to headphones stopped working abruptly"
date: 2013-03-12
forum: Multimedia Software
---

### Post by danielbrackett on 2013-03-12
It used to be that I could plug in or unplug my headphones into my headphone jack and the switch would occur rerouting sound from my integrated speakers to the headphones. Now there is no switch or rather the switch is that of no sound being produced. I am using the 10.04 distro. 

using lspci -vv I got 

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 165e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin ? routed to IRQ 16
    Region 0: Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel



and

00:01.1 Audio device: ATI Technologies Inc Device 1314
    Subsystem: Hewlett-Packard Company Device 165e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by danielbrackett on 2013-03-12
[SOLVED] it righted itself like a turtle I just had to wait.

---

