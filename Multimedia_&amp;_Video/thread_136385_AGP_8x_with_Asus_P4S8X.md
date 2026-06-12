---
title: "AGP 8x with Asus P4S8X"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by kepreon on 2006-02-25
Here's a problem that's plagued me since I first installed Linux on my computer and Google has been unable to resolve it.  My motherboard is an Asus P4S8X motherboard with an AGP 4x/8x slot.  I had a Nvidia Ti4200 that was an 8x AGP card, but it was never run by agpgart in 8x mode.  It recently broke, and I replaced it with an Nvidia GeForce 6800GS, also 8x AGP.  I wanted to take advantage of the higher performance of the card by having it run in 8x mode, but I am unable to do so because Linux doesn't think my motherboard is capable of it.

Here's some information:

kevin@chaos:~$ dmesg | grep agp
[4294688.996000] Linux agpgart interface v0.101 (c) Dave Jones
[4294689.049000] agpgart: Detected SiS 648 chipset
[4294689.065000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294713.794000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294713.794000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294713.794000] agpgart: SiS delay workaround: giving bridge time to recover.
[4294713.805000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[4294714.100000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294714.101000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[4294714.101000] agpgart: SiS delay workaround: giving bridge time to recover.
[4294714.112000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode

kevin@chaos:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 1039:0648
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       4x
Registers:       0x1f004e09:0x00000f01

kevin@chaos:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f004301

kevin@chaos:~$ sudo lspci -vvv
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8086
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort+ >SERR- <PERR-
        Latency: 32
        Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=256M]
        Capabilities: [c0] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=2 Cal=3 SBA+ ITACoh- GART64- HTrans- 64
bit- FW- AGP3+ Rate=x4
                Command: RQ=1 ArqSz=0 Cal=3 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
[snip]

I've tried forcing the NVIDIA AGP to be used instead of agpgart, but it still detects the same host bridge settings.  I have made sure that 8x AGP is enabled in my BIOS settings.  One problem is that it doesn't seem to detect the motherboard host bridge correctly -- it reads sis645 when it is actually sis648.

Is there any way that I can get Ubuntu to recognize the motherboard capabilities and run my card with 8x AGP?

Thanks!

Kevin

---

### Post by QUASAR_FREAK on 2006-02-26
The 8x works in any other OS?

Your BIOS is up to date?

---

### Post by kepreon on 2006-02-26
I have the Asus BIOS 1005, which is the latest, and I do believe that it worked correctly with Windows when it was installed; I will verify this shortly after I muster up a hard drive to install it on.

---

### Post by kepreon on 2006-02-26
I've installed Windows XP on a separate hard drive and the NVIDIA driver detects the AGP 8x.  Before I installed the SIS AGP driver, it put it into 4x mode, but afterwards, it is successfully detected at 8x speed.  Any ideas?

---

### Post by QUASAR_FREAK on 2006-02-26
My friend, i've searched Internet and asked friends but nowhere i can find the solution to your problem. =/

Some one with the same chipset but without this problem anywhere?

---

### Post by Ashrael on 2008-04-30
I have the same problem! so has there not been a patch or something since???

any ideas welcome...

---

