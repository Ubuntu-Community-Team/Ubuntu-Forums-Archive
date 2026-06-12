---
title: "Unknown header type 7f"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by .con on 2011-06-11
Hello, 
I recently switched from Vista to Maverick, or 2.6.35-28-generic. I'm very satisfied except for one issue which has arisen with my Atheros AR5001. For whatever reason, the wireless function only works properly once in every hundred or so system boots. Sometimes when it does work, it will stop working shortly after and lspci -vv yields: 

04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev ff) (prog-if ff)
!!! Unknown Header type 7f
Kernel driver in use: ath5k
Kernel modules: ath5k

Most of the time the system boots, the Atheros card is not even recognized in lspci, and the interface (wlan1) is not present in ifconfig or iwconfig despite commands to bring it up. 

This is a recent development; the card worked beautifully for about a month after I installed it, replacing the factory Broadcom card in my Acer Aspire 4207z. (I have not yet had the opportunity to switch back to the Broadcom card to troubleshoot for hardware issues, which I suspect this may be). 

When the card works properly, lspci -vv yields: 

04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Fujitsu Limited. Device 139c
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at 80400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <128ns, L1 <2us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Kernel driver in use: ath5k
    Kernel modules: ath5k



Furthermore, the wireless light is either on or off at the time of boot, and doesn't respond to pressing the button associated with it. 

I've scoured the forums already for anything that could shed light on this issue, but I've come up empty-handed. Any advice you could offer will be greatly appreciated.

---

### Post by .con on 2011-06-30
I was able to retrieve my Broadcom BCM4312 (original) card and swap it back in, no more problems with wireless. I was also able to troubleshoot the Atheros card in a laptop running Windows 7, and it did not pick up any signals either. 
So, logically concluding that an error of this type (thread title) in this case just means the card went bad. It was purchased used on Ebay, so I'm not entirely surprised.

---

