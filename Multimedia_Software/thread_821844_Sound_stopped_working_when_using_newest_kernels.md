---
title: "Sound stopped working when using newest kernels"
date: 2008-06-07
forum: Multimedia Software
---

### Post by shaolintl on 2008-06-07
Hi,

I am using kubuntu Hardy and when using kernel:
Ubuntu 8.04, kernel 2.6.24-16-generic
The sound work perfectly

When I try to use the kernels 2.6.24-17 up to 2.6.24-19 I get an error that mixer cannot be found

When starting the computer back with the -16 kernel the sound is OK.

I have tried also to install the newest alsa drivers 1.0.17-rc1 but it didnt solve the problem.

The information below is when running the working -16 kernel.

Thanks,
Tom


sudo lspci -vvv -s 1b.0
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

---

### Post by g_rus on 2008-07-14
For me was the same problem, and i must to use the xxx.16 kernel, but in the last update, all sound work again.

---

### Post by BigT0 on 2008-07-14
hey..

check this out, it may help you

[http://ubuntuforums.org/showthread.php?t=38571](http://ubuntuforums.org/showthread.php?t=38571)

---

