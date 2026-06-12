---
title: "Sound glitches with snd-hda-intel"
date: 2010-01-21
forum: Multimedia Software
---

### Post by martinmajer on 2010-01-21
Hi. Yesterday I installed Ubuntu 9.10 on my old laptop, Asus A3HF. And I have problems with sound - sound glitches - some of them appear quite randomly (I really don't know why) and many of them while playing music with mplayer - it really doesn't sound well.

I think it could be something wrong with drivers, maybe with pulse, but I can't find any way to fix this. Here is my lspci -vv for the sound card:
```
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:12c3]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 26
    Region 0: Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0100c  Data: 4191
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```I don't understand this output, but it might be helpful...

Also, there are these lines in dmesg | grep -i hda:
```
[   24.946844] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.946941] HDA Intel 0000:00:1b.0: irq 26 for MSI/MSI-X
[   24.946978] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.067591] hda_codec: ALC660: BIOS auto-probing.
[   25.068805] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   32.867440] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```I used Gentoo before Ubuntu. I never had problems with sound, it was even better than on Windows. So I don't understand why Ubuntu doesn't like my sound card.

Also, it went even worse after I installed "linux-backports-modules-alsa" (I'm not sure what it is, but I've been told it could help me...).

I would really appreciate any suggestions. Thanks in advance.

---

