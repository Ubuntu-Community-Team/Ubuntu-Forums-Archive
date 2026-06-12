---
title: "My microphone works with lots of noise."
date: 2009-11-08
forum: Multimedia Software
---

### Post by fr0d0 on 2009-11-08
Hi! I have a problem with my microphone. It works with lots of noise and recorded sound is very-very quiet or simply there is no sound but only rhythmical crack. This result changes when I change in alsamixer L R Capture parameter (Capture [dB gain=6.00, 6.00] - lots of noise and quite sound, Capture [dB gain=30.00, 30.00] - rhythmical crack). Maybe this is a problem of bad configuration. Who can help?
I have not only one parameter but two parameters L R Capture and now I was talking about the first of them. When I turn the second parameter a bit up from null than that is a loud siren. Who knows this problem?

This happens with my inner microphone in Acer 5220 and with my Microsoft Lifecam under Ubuntu 9.04 (Mint 7).
This is about my sound card:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 011f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Thanks,
Theodore

---

