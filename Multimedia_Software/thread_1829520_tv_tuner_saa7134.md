---
title: "tv tuner saa7134"
date: 2011-08-20
forum: Multimedia Software
---

### Post by konsta82 on 2011-08-20
I have videomate gold+ pal tv tuner with saa7134 on kubuntu natty.After I found correct card&tuner options,it worked perfectly on ubuntu maverick.
Now on kubuntu after tvtime-scanner it says
```
tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/nikola/.tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Cannot open capture device /dev/video0: No such file or directory

```
It look's recognized correctly in lspci```
05:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

```
and lspci -vv
```
05:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
        Subsystem: Compro Technology, Inc. Compro VideoMate Gold+ Pal
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (63750ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=3 PME-
        Kernel modules: saa7134

```
I didn't saw this before,what should I do ?
Thanks in advance

---

### Post by konsta82 on 2011-08-21
bump !

---

