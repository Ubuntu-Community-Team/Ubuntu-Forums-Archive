---
title: "Soundcard (HDA-Intel ALC662) not recognized"
date: 2010-12-12
forum: Multimedia Software
---

### Post by bullpup on 2010-12-12
Hi,

my onboard soundcard (hda-intel ALC662) is not recognized in my new computer. It works fine with other distros, but ubuntu just does not seem to find it:

cat /proc/asound/cards 
--- no soundcards ---

lspci -vvnn:

```

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Foxconn International, Inc. Device [105b:0dd5]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 15
    Region 0: Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=1 ArbSelect=Fixed TC/VC=02
            Status:    NegoPending- InProgress-
    Capabilities: [130 v1] Root Complex Link
        Desc:    PortNumber=0f ComponentID=00 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed1c000
    Kernel modules: snd-hda-intel

```

I'm not sure if this is an alsa or kernel problem, but I hope you can give me some advice/ideas how to fix it.
Thanks!

---

### Post by bullpup on 2010-12-12
FYI: upgrading to 2.6.37-020637rc2 solved the problem.

---

### Post by lidex on 2010-12-12
Good to know they got it fixed upstream. Just out of curiosity, can you post this output from terminal:
```
aplay -l
dpkg -l | grep "alsa"
```

---

### Post by bullpup on 2010-12-14
aplay -l:
```

**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 7: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 8: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 9: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

``` dpkg -l | grep "alsa"
```

ii  alsa-base                              1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-source                            1.0.23+dfsg-1ubuntu4                              ALSA driver sources
ii  alsa-utils                             1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                             4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.30-2                                         GStreamer plugin for ALSA

```I tried compiling ALSA from source (did not work, and was not necessary in the end anyways).

This is with the new kernel. If I use "aplay -l" with the other kernel, it tells me that there is no soundcard. 
```

aplay: device_list:235: keine Soundkarten gefunden ...

```

P.S.: I was a bit unclear in earlier post, I am using the mainline kernel now, not ubuntu kernel. Unfortunately that brings other problems (no PAE), so I am still looking for the right kernel.

---

