---
title: "Audio is not working"
date: 2011-08-28
forum: Multimedia Software
---

### Post by anvsrk on 2011-08-28
Hello,

I've installed Ubuntu 11.04 in my desktop, it is amazing but the only issue I see is audio is not working. I am using Intel chipset, can anyone help me how to fix it.

---

### Post by fdrake on 2011-08-28
in the terminal:
```

sudo lspci -vvvs $(lspci | grep Audio | cut -d " " -f 1)

```
post the output.

---

### Post by anvsrk on 2011-09-01
here is the output.

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8415
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at feaf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0300c  Data: 4191
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
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
            Ctrl:    Enable- ID=0 ArbSelect=Fixed TC/VC=00
            Status:    NegoPending- InProgress-
    Capabilities: [130 v1] Root Complex Link
        Desc:    PortNumber=0f ComponentID=00 EltType=Config
        Link0:    Desc:    TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
            Addr:    00000000fed1c000
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by fdrake on 2011-09-01
the driver is installed and is right. nothing interesting here.

can you post 
```
dmesg
less /var/log/syslog
less /etc/modprobe.d/alsa-base.conf
```

also check if this help: [http://antix.freeforums.org/no-audio-intel-n10-ich-7-hd-audio-t2564.html](http://antix.freeforums.org/no-audio-intel-n10-ich-7-hd-audio-t2564.html) ==> related to this post  [http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database](http://ubuntuforums.org/showthread.php?t=1043568&highlight=intel+sound+database) 
(this post is pretty old so keep in mind that the right path to alsa in the modules folder now is:
/etc/modprobe.d/alsa-base.conf)

---

### Post by lidex on 2011-09-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by anvsrk on 2011-09-07
Here are the details uploaded to

[http://www.alsa-project.org/db/?f=c56e3cf485e1024f8aa42cbb298bea3454ca81a1](http://www.alsa-project.org/db/?f=c56e3cf485e1024f8aa42cbb298bea3454ca81a1)

---

### Post by JD8182 on 2011-09-07
> **anvsrk said:**
> Here are the details uploaded to

[http://www.alsa-project.org/db/?f=c56e3cf485e1024f8aa42cbb298bea3454ca81a1](http://www.alsa-project.org/db/?f=c56e3cf485e1024f8aa42cbb298bea3454ca81a1)

Is your volume turned up? open a terminal and type the command: alsamixer (when the pages appears use your directional keys to navigate around), increasing the volume and such, also hit F6 while you have the alsamixer page still opened and choose your other device if there is one and make sure everything is enabled and volume is set..

---

