---
title: "Intel ICH5 with CMI9761A+ Surround Sound"
date: 2011-02-04
forum: Multimedia Software
---

### Post by argoth on 2011-02-04
Hi,

I have an integrated sound card which is supposed to support 5.1 by using mic and line in as the additional 4 channels. I'm able to get stereo working just fine but I haven't had any luck getting any sound out of the other channels. Any help would be appreciated!

/proc/asound/cards
```

0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with CMI9761A+ at irq 17

```lspci -vvv
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [e4] Vendor Specific Information: Len=06 <?>
    Capabilities: [a0] AGP version 3.0
        Status: RQ=32 Iso- ArqSz=2 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: efc00000-efcfffff
    Prefetchable memory behind bridge: afa00000-cf9fffff
    Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at e000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at ec00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=32
    I/O behind bridge: 0000a000-0000bfff
    Memory behind bridge: efd00000-f7efffff
    Prefetchable memory behind bridge: cfa00000-efafffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at fc00 [size=16]
    Region 5: Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Elitegroup Computer Systems Device a101
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at d800 [size=256]
    Region 1: I/O ports at dc00 [size=64]
    Region 2: Memory at f7fff800 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at f7fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA controller])
    Subsystem: ATI Technologies Inc Radeon 9600XT
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at b8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at 9800 [size=256]
    Region 2: Memory at efce0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at efcc0000 [disabled] [size=128K]
    Capabilities: [58] AGP version 3.0
        Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=32 ArqSz=2 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
    Subsystem: ATI Technologies Inc Radeon 9600XT (Secondary)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at efcf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

02:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: ATI Technologies Inc ATI TV Wonder Pro
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: [44] Vital Product Data
        No end tag found
    Capabilities: [4c] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: cx8800
    Kernel modules: cx8800

02:03.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Region 0: Memory at f5e00000 (64-bit, prefetchable) [size=64K]
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: efd00000-f5dfffff
    Prefetchable memory behind bridge: cfa00000-efafffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [60] Express (v1) PCI/PCI-X to PCI-Express Bridge, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop- BrConfRtry-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <16us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Kernel modules: shpchp

02:04.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
    Subsystem: PCTel Inc HSP MicroModem 56
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at bc00 [size=64]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=55mA PME(D0+,D1-,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: serial

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at b800 [size=256]
    Region 1: Memory at f7effc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

03:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 19f1:0a5e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at ac00 [size=128]
    [virtual] Expansion ROM at f5de0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb
```dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-25-generic-pae (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 (Ubuntu 2.6.35-25.44-generic-pae 2.6.35.10)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ff40 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  modified: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  modified: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000]  modified: 00000000ffbc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 2f572000 - 2ffb0000
[    0.000000] ACPI: RSDP 000f6b70 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ff40000 00030 (v01 A M I  OEMRSDT  03000430 MSFT 00000097)
[    0.000000] ACPI: FACP 3ff40200 00081 (v02 A M I  OEMFACP  03000430 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ff40360 0352C (v01    P4I    P4IPE 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 3ff50000 00040
[    0.000000] ACPI: APIC 3ff40300 0005C (v01 A M I  OEMAPIC  03000430 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ff50040 00040 (v01 A M I  OEMBIOS  03000430 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 131MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003ff40
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff40
[    0.000000] On node 0 totalpages: 261839
[    0.000000] free_area_init_node: node 0, pgdat c083ecc0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 263 pages used for memmap
[    0.000000]   HighMem zone: 33339 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bfbc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1a00000 s39872 r0 d21568 u1048576
[    0.000000] pcpu-alloc: s39872 r0 d21568 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=d49cc2ed-18d6-4622-bf91-104a4e5db472 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5238720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (45 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009fb65c]   TEXT DATA BSS
[    0.000000]   #3 [002f572000 - 002ffb0000]         RAMDISK
[    0.000000]   #4 [00009fc000 - 0000a03198]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fa250]   BIOS reserved
[    0.000000]   #8 [00000fa378 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fa250 - 00000fa378]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
[    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
[    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
[    0.000000]   #17 [0001801100 - 00018011a8]         BOOTMEM
[    0.000000]   #18 [00018011c0 - 00018041c0]         BOOTMEM
[    0.000000]   #19 [00018041c0 - 00018041dc]         BOOTMEM
[    0.000000]   #20 [0001804200 - 0001804e00]         BOOTMEM
[    0.000000]   #21 [0001804e00 - 0001804e2f]         BOOTMEM
[    0.000000]   #22 [0001804e40 - 0001804f60]         BOOTMEM
[    0.000000]   #23 [0001804f80 - 0001804fc0]         BOOTMEM
[    0.000000]   #24 [0001804fc0 - 0001805000]         BOOTMEM
[    0.000000]   #25 [0001805000 - 0001805040]         BOOTMEM
[    0.000000]   #26 [0001805040 - 0001805080]         BOOTMEM
[    0.000000]   #27 [0001805080 - 00018050c0]         BOOTMEM
[    0.000000]   #28 [00018050c0 - 0001805100]         BOOTMEM
[    0.000000]   #29 [0001805100 - 0001805140]         BOOTMEM
[    0.000000]   #30 [0001805140 - 0001805150]         BOOTMEM
[    0.000000]   #31 [0001805180 - 00018051ee]         BOOTMEM
[    0.000000]   #32 [0001805200 - 000180526e]         BOOTMEM
[    0.000000]   #33 [0001a00000 - 0001a0f000]         BOOTMEM
[    0.000000]   #34 [0001b00000 - 0001b0f000]         BOOTMEM
[    0.000000]   #35 [0001807280 - 0001807284]         BOOTMEM
[    0.000000]   #36 [00018072c0 - 00018072c4]         BOOTMEM
[    0.000000]   #37 [0001807300 - 0001807308]         BOOTMEM
[    0.000000]   #38 [0001807340 - 0001807348]         BOOTMEM
[    0.000000]   #39 [0001807380 - 0001807420]         BOOTMEM
[    0.000000]   #40 [0001807440 - 0001807488]         BOOTMEM
[    0.000000]   #41 [00018074c0 - 000180b4c0]         BOOTMEM
[    0.000000]   #42 [000180b4c0 - 000188b4c0]         BOOTMEM
[    0.000000]   #43 [000188b4c0 - 00018cb4c0]         BOOTMEM
[    0.000000]   #44 [0001b0f000 - 000200dfc0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003ff40)
[    0.000000] Memory: 1013372k/1047808k available (5090k kernel code, 33984k reserved, 2427k data, 708k init, 134408k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0909000   ( 708 kB)
[    0.000000]       .data : 0xc05f8a1a - 0xc0857908   (2427 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f8a1a   (5090 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3192.144 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.28 BogoMIPS (lpj=12768576)
[    0.004014] pid_max: default: 32768 minimum: 301
[    0.004038] Security Framework initialized
[    0.004066] AppArmor: AppArmor initialized
[    0.004069] Yama: becoming mindful.
[    0.004150] Mount-cache hash table entries: 512
[    0.004334] Initializing cgroup subsys ns
[    0.004342] Initializing cgroup subsys cpuacct
[    0.004350] Initializing cgroup subsys memory
[    0.004364] Initializing cgroup subsys devices
[    0.004368] Initializing cgroup subsys freezer
[    0.004373] Initializing cgroup subsys net_cls
[    0.004417] CPU: Physical Processor ID: 0
[    0.004421] CPU: Processor Core ID: 0
[    0.004425] mce: CPU supports 4 MCE banks
[    0.004440] CPU0: Thermal monitoring enabled (TM1)
[    0.004447] using mwait in idle threads.
[    0.004456] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.004466] ... version:                0
[    0.004469] ... bit width:              40
[    0.004473] ... generic registers:      18
[    0.004477] ... value mask:             000000ffffffffff
[    0.004481] ... max period:             0000007fffffffff
[    0.004485] ... fixed-purpose events:   0
[    0.004488] ... event mask:             000000000003ffff
[    0.009250] ACPI: Core revision 20100428
[    0.015459] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.015467] ftrace: allocating 22392 entries in 44 pages
[    0.016081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016380] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058521] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.060000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148021] Brought up 2 CPUs
[    0.148027] Total of 2 processors activated (12768.81 BogoMIPS).
[    0.148452] devtmpfs: initialized
[    0.149393] regulator: core version 0.5
[    0.149418] Time: 12:10:52  Date: 02/04/11
[    0.149467] NET: Registered protocol family 16
[    0.149482] Trying to unpack rootfs image as initramfs...
[    0.149692] EISA bus registered
[    0.149707] ACPI: bus type pci registered
[    0.149882] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[    0.149886] PCI: Using configuration type 1 for base access
[    0.153102] bio: create slab <bio-0> at 0
[    0.154822] ACPI: EC: Look up EC in DSDT
[    0.157296] ACPI: Executed 1 blocks of module-level executable AML code
[    0.166847] ACPI: Interpreter enabled
[    0.166857] ACPI: (supports S0 S1 S4 S5)
[    0.166900] ACPI: Using IOAPIC for interrupt routing
[    0.178738] ACPI Warning: Incorrect checksum in table [OEMB] - 0x04, should be 0xFB (20100428/tbutils-314)
[    0.178951] ACPI: No dock devices found.
[    0.178960] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.179167] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.179575] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.179581] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.179588] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.179594] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffefffff] (ignored)
[    0.179618] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.179633] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.179749] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.179861] pci 0000:00:1d.0: reg 20: [io  0xe000-0xe01f]
[    0.179939] pci 0000:00:1d.1: reg 20: [io  0xe400-0xe41f]
[    0.180028] pci 0000:00:1d.2: reg 20: [io  0xe800-0xe81f]
[    0.180095] pci 0000:00:1d.3: reg 20: [io  0xec00-0xec1f]
[    0.180163] pci 0000:00:1d.7: reg 10: [mem 0xf7fffc00-0xf7ffffff]
[    0.180234] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.180242] pci 0000:00:1d.7: PME# disabled
[    0.180350] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.180361] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH4 ACPI/GPIO/TCO
[    0.180370] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH4 GPIO
[    0.180402] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.180413] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.180425] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.180436] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.180450] pci 0000:00:1f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.180464] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.180522] pci 0000:00:1f.5: reg 10: [io  0xd800-0xd8ff]
[    0.180533] pci 0000:00:1f.5: reg 14: [io  0xdc00-0xdc3f]
[    0.180544] pci 0000:00:1f.5: reg 18: [mem 0xf7fff800-0xf7fff9ff]
[    0.180555] pci 0000:00:1f.5: reg 1c: [mem 0xf7fff400-0xf7fff4ff]
[    0.180594] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.180601] pci 0000:00:1f.5: PME# disabled
[    0.180659] pci 0000:01:00.0: reg 10: [mem 0xb8000000-0xbfffffff pref]
[    0.180670] pci 0000:01:00.0: reg 14: [io  0x9800-0x98ff]
[    0.180680] pci 0000:01:00.0: reg 18: [mem 0xefce0000-0xefceffff]
[    0.180702] pci 0000:01:00.0: reg 30: [mem 0xefcc0000-0xefcdffff pref]
[    0.180732] pci 0000:01:00.0: supports D1 D2
[    0.180769] pci 0000:01:00.1: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.180779] pci 0000:01:00.1: reg 14: [mem 0xefcf0000-0xefcfffff]
[    0.180821] pci 0000:01:00.1: supports D1 D2
[    0.180876] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.180884] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.180892] pci 0000:00:01.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.180900] pci 0000:00:01.0:   bridge window [mem 0xafa00000-0xcf9fffff pref]
[    0.180953] pci 0000:02:02.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.181072] pci 0000:02:03.0: reg 10: [mem 0x00000000-0x0000ffff 64bit pref]
[    0.181122] pci 0000:02:03.0: supports D1
[    0.181126] pci 0000:02:03.0: PME# supported from D0 D1 D3hot
[    0.181134] pci 0000:02:03.0: PME# disabled
[    0.181177] pci 0000:02:04.0: reg 10: [io  0xbc00-0xbc3f]
[    0.181231] pci 0000:02:04.0: supports D2
[    0.181236] pci 0000:02:04.0: PME# supported from D0 D2 D3hot D3cold
[    0.181244] pci 0000:02:04.0: PME# disabled
[    0.181280] pci 0000:02:05.0: reg 10: [io  0xb800-0xb8ff]
[    0.181292] pci 0000:02:05.0: reg 14: [mem 0xf7effc00-0xf7effcff]
[    0.181341] pci 0000:02:05.0: supports D1 D2
[    0.181346] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.181353] pci 0000:02:05.0: PME# disabled
[    0.181400] pci 0000:00:1e.0: PCI bridge to [bus 02-03] (subtractive decode)
[    0.181409] pci 0000:00:1e.0:   bridge window [io  0xa000-0xbfff]
[    0.181418] pci 0000:00:1e.0:   bridge window [mem 0xefd00000-0xf7efffff]
[    0.181426] pci 0000:00:1e.0:   bridge window [mem 0xcfa00000-0xefafffff pref]
[    0.181432] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.181439] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    0.181547] pci 0000:03:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
[    0.181579] pci 0000:03:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.181607] pci 0000:03:00.0: reg 1c: [mem 0xf2000000-0xf3ffffff 64bit]
[    0.181624] pci 0000:03:00.0: reg 24: [io  0xac00-0xac7f]
[    0.181640] pci 0000:03:00.0: reg 30: [mem 0xf5de0000-0xf5dfffff pref]
[    0.181769] pci 0000:02:03.0: PCI bridge to [bus 03-03]
[    0.181777] pci 0000:02:03.0:   bridge window [io  0xa000-0xafff]
[    0.181785] pci 0000:02:03.0:   bridge window [mem 0xefd00000-0xf5dfffff]
[    0.181794] pci 0000:02:03.0:   bridge window [mem 0xcfa00000-0xefafffff pref]
[    0.181819] pci_bus 0000:00: on NUMA node 0
[    0.181828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.182006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.186626] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.186801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.186972] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.187156] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.187333] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.187503] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.187691] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.187864] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.187945] HEST: Table is not found!
[    0.188117] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.188137] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.188143] vgaarb: loaded
[    0.188473] SCSI subsystem initialized
[    0.188630] libata version 3.00 loaded.
[    0.188735] usbcore: registered new interface driver usbfs
[    0.188776] usbcore: registered new interface driver hub
[    0.188828] usbcore: registered new device driver usb
[    0.189081] ACPI: WMI: Mapper loaded
[    0.189086] PCI: Using ACPI for IRQ routing
[    0.189094] PCI: pci_cache_line_size set to 64 bytes
[    0.189223] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.189229] reserve RAM buffer: 000000003ff40000 - 000000003fffffff 
[    0.189415] NetLabel: Initializing
[    0.189420] NetLabel:  domain hash size = 128
[    0.189423] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.189446] NetLabel:  unlabeled traffic allowed by default
[    0.189587] hpet clockevent registered
[    0.189594] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.189602] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.189613] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192222] Switching to clocksource tsc
[    0.212500] AppArmor: AppArmor Filesystem Enabled
[    0.212526] pnp: PnP ACPI init
[    0.212574] ACPI: bus type pnp registered
[    0.218482] pnp: PnP ACPI: found 12 devices
[    0.218488] ACPI: ACPI bus type pnp unregistered
[    0.218496] PnPBIOS: Disabled by ACPI PNP
[    0.218524] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.218532] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.218538] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.218545] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.218553] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.218561] system 00:07: [mem 0xffb00000-0xffbfffff] could not be reserved
[    0.218574] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.218581] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.218594] system 00:0a: [io  0x0680-0x06ff] has been reserved
[    0.218601] system 00:0a: [io  0x0295-0x0296] has been reserved
[    0.218614] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.218624] system 00:0b: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.218633] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.218642] system 00:0b: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.218652] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.256445] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40000000-0x400003ff]
[    0.256458] pci 0000:00:1f.1: BAR 5: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff]
[    0.256466] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.256473] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.256482] pci 0000:00:01.0:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.256490] pci 0000:00:01.0:   bridge window [mem 0xafa00000-0xcf9fffff pref]
[    0.256504] pci 0000:02:03.0: BAR 0: assigned [mem 0xf5e00000-0xf5e0ffff 64bit pref]
[    0.256516] pci 0000:02:03.0: BAR 0: set to [mem 0xf5e00000-0xf5e0ffff 64bit pref] (PCI address [0xf5e00000-0xf5e0ffff]
[    0.256523] pci 0000:02:03.0: PCI bridge to [bus 03-03]
[    0.256530] pci 0000:02:03.0:   bridge window [io  0xa000-0xafff]
[    0.256540] pci 0000:02:03.0:   bridge window [mem 0xefd00000-0xf5dfffff]
[    0.256548] pci 0000:02:03.0:   bridge window [mem 0xcfa00000-0xefafffff pref]
[    0.256559] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.256566] pci 0000:00:1e.0:   bridge window [io  0xa000-0xbfff]
[    0.256575] pci 0000:00:1e.0:   bridge window [mem 0xefd00000-0xf7efffff]
[    0.256583] pci 0000:00:1e.0:   bridge window [mem 0xcfa00000-0xefafffff pref]
[    0.256611] pci 0000:00:1e.0: setting latency timer to 64
[    0.256631]   alloc irq_desc for 21 on node -1
[    0.256636]   alloc kstat_irqs on node -1
[    0.256648] pci 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.256661] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.256669] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.256678] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.256687] pci_bus 0000:01: resource 1 [mem 0xefc00000-0xefcfffff]
[    0.256697] pci_bus 0000:01: resource 2 [mem 0xafa00000-0xcf9fffff pref]
[    0.256704] pci_bus 0000:02: resource 0 [io  0xa000-0xbfff]
[    0.256710] pci_bus 0000:02: resource 1 [mem 0xefd00000-0xf7efffff]
[    0.256716] pci_bus 0000:02: resource 2 [mem 0xcfa00000-0xefafffff pref]
[    0.256722] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.256728] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    0.256735] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.256741] pci_bus 0000:03: resource 1 [mem 0xefd00000-0xf5dfffff]
[    0.256747] pci_bus 0000:03: resource 2 [mem 0xcfa00000-0xefafffff pref]
[    0.256818] NET: Registered protocol family 2
[    0.256935] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.257408] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.258260] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258798] TCP: Hash tables configured (established 131072 bind 65536)
[    0.258804] TCP reno registered
[    0.258812] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.258835] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.259029] NET: Registered protocol family 1
[    0.259250] pci 0000:03:00.0: Boot video device
[    0.259259] PCI: CLS 32 bytes, default 64
[    0.259591] cpufreq-nforce2: No nForce2 chipset.
[    0.259701] Scanning for low memory corruption every 60 seconds
[    0.259923] audit: initializing netlink socket (disabled)
[    0.259942] type=2000 audit(1296821452.256:1): initialized
[    0.273393] highmem bounce pool size: 64 pages
[    0.273404] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.276258] VFS: Disk quotas dquot_6.5.2
[    0.276381] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.277651] fuse init (API version 7.14)
[    0.277832] msgmni has been set to 1716
[    0.278493] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.278500] io scheduler noop registered
[    0.278505] io scheduler deadline registered
[    0.278534] io scheduler cfq registered (default)
[    0.278804] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.278850] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.279221] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.279239] ACPI: Power Button [PWRB]
[    0.279336] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.279348] ACPI: Sleep Button [SLPB]
[    0.279434] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.279442] ACPI: Power Button [PWRF]
[    0.279723] ACPI: acpi_idle registered with cpuidle
[    0.284038] ERST: Table is not found!
[    0.284382] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.284517] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.285039] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.285288]   alloc irq_desc for 19 on node -1
[    0.285292]   alloc kstat_irqs on node -1
[    0.285305] serial 0000:02:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.288468] brd: module loaded
[    0.289593] loop: module loaded
[    0.290043] ata_piix 0000:00:1f.1: version 2.13
[    0.290061] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.290073]   alloc irq_desc for 18 on node -1
[    0.290077]   alloc kstat_irqs on node -1
[    0.290089] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.290156] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.290329] scsi0 : ata_piix
[    0.290360] isapnp: Scanning for PnP cards...
[    0.339696] scsi1 : ata_piix
[    0.343090] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.343099] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.343873] Fixed MDIO Bus: probed
[    0.343943] PPP generic driver version 2.4.2
[    0.344062] tun: Universal TUN/TAP device driver, 1.6
[    0.344066] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.344256] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.344296]   alloc irq_desc for 23 on node -1
[    0.344301]   alloc kstat_irqs on node -1
[    0.344314] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.344344] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.344351] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.344414] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.344453] ehci_hcd 0000:00:1d.7: debug port 1
[    0.348334] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.348378] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7fffc00
[    0.395952] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.396247] hub 1-0:1.0: USB hub found
[    0.396257] hub 1-0:1.0: 8 ports detected
[    0.396434] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.396472] uhci_hcd: USB Universal Host Controller Interface driver
[    0.396554]   alloc irq_desc for 16 on node -1
[    0.396559]   alloc kstat_irqs on node -1
[    0.396571] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.396585] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.396592] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.396669] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.396715] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[    0.396945] hub 2-0:1.0: USB hub found
[    0.396956] hub 2-0:1.0: 2 ports detected
[    0.397076] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.397087] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.397094] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.397160] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.397203] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    0.397430] hub 3-0:1.0: USB hub found
[    0.397441] hub 3-0:1.0: 2 ports detected
[    0.397562] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.397573] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.397580] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.397649] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.397689] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.397931] hub 4-0:1.0: USB hub found
[    0.397939] hub 4-0:1.0: 2 ports detected
[    0.398044] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398054] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.398061] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.398128] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.398156] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    0.398389] hub 5-0:1.0: USB hub found
[    0.398397] hub 5-0:1.0: 2 ports detected
[    0.398624] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.398628] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.399478] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.399733] mice: PS/2 mouse device common for all mice
[    0.399999] rtc_cmos 00:02: RTC can wake from S4
[    0.400076] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.400106] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.400341] device-mapper: uevent: version 1.0.3
[    0.444231] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.517813] ata1.00: ATA-6: WDC WD1600JB-22GVA0, 08.02D08, max UDMA/100
[    0.517819] ata1.00: 312581808 sectors, multi 16: LBA48 
[    0.533593] ata1.00: configured for UDMA/100
[    0.560025] ata2.00: ATAPI: DVDRW DRW-3S163, BSG2, max UDMA/66
[    0.560065] ata2.00: limited to UDMA/33 due to 40-wire cable
[    0.571268] Freeing initrd memory: 10488k freed
[    0.575516] device-mapper: multipath: version 1.1.1 loaded
[    0.575543] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.582200] ata2.00: configured for UDMA/33
[    0.582505] EISA: Probing bus 0 at eisa.0
[    0.582557] EISA: Detected 0 cards.
[    0.582756] cpuidle: using governor ladder
[    0.582761] cpuidle: using governor menu
[    0.583358] TCP cubic registered
[    0.583605] NET: Registered protocol family 10
[    0.584290] lo: Disabled Privacy Extensions
[    0.584741] NET: Registered protocol family 17
[    0.584827] Using IPI No-Shortcut mode
[    0.585002] PM: Resume from disk failed.
[    0.585027] registered taskstats version 1
[    0.585352]   Magic number: 15:162:177
[    0.585416] acpi device:0d: hash matches
[    0.585456] rtc_cmos 00:02: setting system clock to 2011-02-04 12:10:53 UTC (1296821453)
[    0.585462] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.585466] EDD information not available.
[    0.588513] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.663122] isapnp: No Plug & Play device found
[    0.663304] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-22G 08.0 PQ: 0 ANSI: 5
[    0.663484] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.663541] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.663587] sd 0:0:0:0: [sda] Write Protect is off
[    0.663593] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.663679] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.663969]  sda:
[    0.664518] scsi 1:0:0:0: CD-ROM            DVDRW    DRW-3S163        BSG2 PQ: 0 ANSI: 5
[    0.668511] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.668515] Uniform CD-ROM driver Revision: 3.20
[    0.668631] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.668704] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.669405]  sda1 sda2 sda3 < sda5 >
[    0.690636] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.690658] Freeing unused kernel memory: 708k freed
[    0.691374] Write protecting the kernel text: 5092k
[    0.691476] Write protecting the kernel read-only data: 2012k
[    0.718828] udev[79]: starting version 163
[    0.923728] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    0.942082] Floppy drive(s): fd0 is 1.44M
[    0.948854] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.948893] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.955157] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.955222]   alloc irq_desc for 22 on node -1
[    0.955227]   alloc kstat_irqs on node -1
[    0.955242] 8139too 0000:02:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.956816] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xb800, 00:50:2c:a4:98:7a, IRQ 22
[    0.959472] FDC 0 is a post-1991 82077
[    1.123300] usbcore: registered new interface driver hiddev
[    1.158019] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[    1.158253] generic-usb 0003:045E:008C.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:1d.1-1/input0
[    1.158292] usbcore: registered new interface driver usbhid
[    1.158296] usbhid: USB HID core driver
[    1.375770] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.431623] udev[317]: starting version 163
[    8.506315] Adding 6384636k swap on /dev/sda5.  Priority:-1 extents:1 across:6384636k 
[    8.514525] Linux agpgart interface v0.103
[    8.547130] intel_rng: FWH not detected
[    8.601601] lp: driver loaded but no devices found
[    8.602762] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.656919] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    8.771900] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.772706] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    9.056368] Linux video capture interface: v2.00
[    9.127461] [drm] Initialized drm 1.1.0 20060810
[    9.133202] IR NEC protocol handler initialized
[    9.189172] IR RC5(x) protocol handler initialized
[    9.211508] type=1400 audit(1296843062.120:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=564 comm="apparmor_parser"
[    9.212342] type=1400 audit(1296843062.124:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=564 comm="apparmor_parser"
[    9.212807] type=1400 audit(1296843062.124:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=564 comm="apparmor_parser"
[    9.223129] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[    9.223187]   alloc irq_desc for 20 on node -1
[    9.223193]   alloc kstat_irqs on node -1
[    9.223207] cx8800 0000:02:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    9.227535] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected], frontend(s): 0
[    9.227543] cx88[0]: TV tuner type 44, Radio tuner type -1
[    9.227608] IR RC6 protocol handler initialized
[    9.235652] nvidia: module license 'NVIDIA' taints kernel.
[    9.235659] Disabling lock debugging due to kernel taint
[    9.385520] [drm] radeon defaulting to kernel modesetting.
[    9.385526] [drm] radeon kernel modesetting enabled.
[    9.385598] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    9.385613] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.812329] IR JVC protocol handler initialized
[   10.814410] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.816728] All bytes are equal. It is not a TEA5767
[   10.816978] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   10.840906] IR Sony protocol handler initialized
[   10.863483] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   10.884993] [drm] initializing kernel modesetting (RV350 0x1002:0x4152).
[   10.892123] [drm] register mmio base: 0xEFCE0000
[   10.892128] [drm] register mmio size: 65536
[   10.897159] tda9887 0-0043: creating new instance
[   10.897165] tda9887 0-0043: tda988[5/6/7] found
[   10.903872]   alloc irq_desc for 17 on node -1
[   10.903878]   alloc kstat_irqs on node -1
[   10.903890] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.903957] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   10.953814] lirc_dev: IR Remote Control driver registered, major 250 
[   10.957843] IR LIRC bridge handler initialized
[   10.961215] nf_conntrack version 0.5.0 (16008 buckets, 64032 max)
[   10.962725] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.962732] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   10.962736] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   10.997017] [drm] GPU not posted. posting now...
[   11.044575] tuner-simple 0-0060: creating new instance
[   11.044583] tuner-simple 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   11.049282] cx88[0]/0: found at 0000:02:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xf6000000
[   11.049570] cx88[0]/0: registered device video0 [v4l2]
[   11.049718] cx88[0]/0: registered device vbi0
[   11.102162] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   11.127128] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   11.129554] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   11.129610] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   11.129684] radeon 0000:01:00.0: GTT: 64M 0xF8000000 - 0xFBFFFFFF
[   11.129691] [drm] Generation 2 PCI interface, using max accessible memory
[   11.129699] radeon 0000:01:00.0: VRAM: 128M 0xB8000000 - 0xBFFFFFFF (128M used)
[   11.129740] [drm] radeon: irq initialized.
[   11.130395] [drm] Detected VRAM RAM=128M, BAR=128M
[   11.130403] [drm] RAM width 128bits DDR
[   11.136449] [TTM] Zone  kernel: Available graphics memory: 445080 kiB.
[   11.136456] [TTM] Zone highmem: Available graphics memory: 512284 kiB.
[   11.136461] [TTM] Initializing pool allocator.
[   11.136504] [drm] radeon: 128M of VRAM memory ready
[   11.136510] [drm] radeon: 64M of GTT memory ready.
[   11.136561] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   11.136645] [drm] Loading R300 Microcode
[   11.225031] intel8x0_measure_ac97_clock: measured 55298 usecs (2664 samples)
[   11.225037] intel8x0: clocking to 48000
[   11.408618] [drm] radeon: ring at 0x00000000F8000000
[   11.408796] [drm] ring test succeeded in 0 usecs
[   11.409842] [drm] radeon: ib pool ready.
[   11.410238] [drm] ib test succeeded in 0 usecs
[   11.410582] [drm] DFP table revision: 4
[   11.410685] [drm] Radeon Display Connectors
[   11.410690] [drm] Connector 0:
[   11.410693] [drm]   VGA
[   11.410698] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   11.410701] [drm]   Encoders:
[   11.410704] [drm]     CRT1: INTERNAL_DAC1
[   11.410708] [drm] Connector 1:
[   11.410711] [drm]   DVI-I
[   11.410713] [drm]   HPD1
[   11.410718] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   11.410721] [drm]   Encoders:
[   11.410725] [drm]     CRT2: INTERNAL_DAC2
[   11.410729] [drm]     DFP1: INTERNAL_TMDS1
[   11.495884] nvidia 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.495901] nvidia 0000:03:00.0: setting latency timer to 64
[   11.495911] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   11.495917] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.497507] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   11.669047] [drm] fb mappable at 0xB8040000
[   11.669051] [drm] vram apper at 0xB8000000
[   11.669054] [drm] size 4177920
[   11.669057] [drm] fb depth is 24
[   11.669059] [drm]    pitch is 5440
[   11.743948] Console: switching to colour frame buffer device 170x48
[   11.766193] fb0: radeondrmfb frame buffer device
[   11.766196] drm: registered panic notifier
[   11.766202] Slow work thread pool: Starting up
[   11.766298] Slow work thread pool: Ready
[   11.766311] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   26.714081] atkbd serio0: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[   26.714088] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
[   70.295360] atkbd serio0: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[   70.295366] atkbd serio0: Use 'setkeycodes e059 <keycode>' to make it known.
[   72.569017] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   72.569022] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   72.570998] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[   72.571003] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[   72.787106] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   72.787110] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   72.789309] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[   72.789312] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[   77.477300] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   77.477305] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   77.479304] atkbd serio0: Unknown key released (translated set 2, code 0x74 on isa0060/serio0).
[   77.479308] atkbd serio0: Use 'setkeycodes 74 <keycode>' to make it known.
[   77.932623] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   77.932627] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   77.934796] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[   77.934799] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[   77.990221] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   77.990225] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   77.992119] atkbd serio0: Unknown key pressed (translated set 2, code 0x74 on isa0060/serio0).
[   77.992123] atkbd serio0: Use 'setkeycodes 74 <keycode>' to make it known.
[   77.994149] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
[   77.994152] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[   78.016498] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[   78.016502] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[   78.018546] atkbd serio0: Unknown key pressed (translated set 2, code 0x55 on isa0060/serio0).
[   78.018550] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[   94.174248] atkbd serio0: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[   94.174253] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
[  100.260016] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  100.459948] Initializing USB Mass Storage driver...
[  100.460189] scsi2 : usb-storage 1-1:1.0
[  100.460364] usbcore: registered new interface driver usb-storage
[  100.460368] USB Mass Storage support registered.
[  101.461059] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[  101.461833] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  101.464657] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
[  101.466055] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  101.466065] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  101.472281] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  101.472287] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  101.475874]  sdb: sdb1
[  101.492927] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  101.492935] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  101.496548] sd 2:0:0:0: [sdb] Attached SCSI disk
[  114.245544] type=1400 audit(1296864767.155:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1116 comm="apparmor_parser"
[  114.246650] type=1400 audit(1296864767.155:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1116 comm="apparmor_parser"
[  114.306635] type=1400 audit(1296864767.215:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1137 comm="apparmor_parser"
[  114.307495] type=1400 audit(1296864767.215:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1137 comm="apparmor_parser"
[  114.307979] type=1400 audit(1296864767.215:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1137 comm="apparmor_parser"
[  114.342535] type=1400 audit(1296864767.251:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1138 comm="apparmor_parser"
[  114.349297] ppdev: user-space parallel port driver
[  114.357001] type=1400 audit(1296864767.267:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1150 comm="apparmor_parser"
[  114.358115] type=1400 audit(1296864767.267:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1150 comm="apparmor_parser"
[  114.376152] type=1400 audit(1296864767.287:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1155 comm="apparmor_parser"
[  114.376263] type=1400 audit(1296864767.287:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1138 comm="apparmor_parser"
[  114.438567] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  114.897138] RPC: Registered udp transport module.
[  114.897143] RPC: Registered tcp transport module.
[  114.897146] RPC: Registered tcp NFSv4.1 backchannel transport module.
[  114.955660] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  116.017714] svc: failed to register lockdv1 RPC service (errno 97).
[  116.019006] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  116.036188] NFSD: starting 90-second grace period
[  117.829505] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  124.576009] eth0: no IPv6 routers present
[  124.742060] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  594.074171] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=129 TOS=0x00 PREC=0x00 TTL=255 ID=1470 PROTO=UDP SPT=5353 DPT=5353 LEN=109 
[  597.146489] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=238 TOS=0x00 PREC=0x00 TTL=255 ID=1484 PROTO=UDP SPT=5353 DPT=5353 LEN=218 
[  774.674259] atkbd serio0: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[  774.674267] atkbd serio0: Use 'setkeycodes e001 <keycode>' to make it known.
[  774.677945] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[  774.677949] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[  774.679772] atkbd serio0: Unknown key released (translated set 2, code 0x74 on isa0060/serio0).
[  774.679777] atkbd serio0: Use 'setkeycodes 74 <keycode>' to make it known.
[  774.681569] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[  774.681573] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[  774.700160] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[  774.700166] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[  774.702094] atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
[  774.702098] atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
[  774.727197] atkbd serio0: Unknown key released (translated set 2, code 0xa5 on isa0060/serio0).
[  774.727203] atkbd serio0: Use 'setkeycodes e025 <keycode>' to make it known.
[  774.729365] atkbd serio0: Unknown key released (translated set 2, code 0x75 on isa0060/serio0).
[  774.729370] atkbd serio0: Use 'setkeycodes 75 <keycode>' to make it known.
[  824.611204] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=124 TOS=0x00 PREC=0x00 TTL=255 ID=20237 PROTO=UDP SPT=5353 DPT=5353 LEN=104 
[  825.511019] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=228 TOS=0x00 PREC=0x00 TTL=255 ID=31321 PROTO=UDP SPT=5353 DPT=5353 LEN=208 
[  826.510990] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=282 TOS=0x00 PREC=0x00 TTL=255 ID=21306 PROTO=UDP SPT=5353 DPT=5353 LEN=262 
[  830.510069] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=282 TOS=0x00 PREC=0x00 TTL=255 ID=9285 PROTO=UDP SPT=5353 DPT=5353 LEN=262 
[  838.517974] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=226 TOS=0x00 PREC=0x00 TTL=255 ID=28795 PROTO=UDP SPT=5353 DPT=5353 LEN=206 
[ 1339.216529] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=939 TOS=0x00 PREC=0x00 TTL=255 ID=24196 PROTO=UDP SPT=5353 DPT=5353 LEN=919 
[ 1339.319789] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=344 TOS=0x00 PREC=0x00 TTL=255 ID=22669 PROTO=UDP SPT=5353 DPT=5353 LEN=324 
[ 1348.337342] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=344 TOS=0x00 PREC=0x00 TTL=255 ID=55197 PROTO=UDP SPT=5353 DPT=5353 LEN=324 
[ 1351.217319] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=939 TOS=0x00 PREC=0x00 TTL=255 ID=53237 PROTO=UDP SPT=5353 DPT=5353 LEN=919 
[ 1375.394625] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=344 TOS=0x00 PREC=0x00 TTL=255 ID=64697 PROTO=UDP SPT=5353 DPT=5353 LEN=324 
[ 1499.865915] [UFW BLOCK] IN=eth0 OUT= MAC=00:50:2c:a4:98:7a:00:1f:fe:84:e3:00:08:00 SRC=199.7.178.41 DST=152.65.95.52 LEN=1500 TOS=0x00 PREC=0x00 TTL=63 ID=40362 DF PROTO=TCP SPT=80 DPT=41450 WINDOW=6936 RES=0x00 ACK URGP=0 
[ 1499.866363] [UFW BLOCK] IN=eth0 OUT= MAC=00:50:2c:a4:98:7a:00:1f:fe:84:e3:00:08:00 SRC=199.7.178.41 DST=152.65.95.52 LEN=1500 TOS=0x00 PREC=0x00 TTL=63 ID=40364 DF PROTO=TCP SPT=80 DPT=41450 WINDOW=6936 RES=0x00 ACK URGP=0 
[ 1499.866814] [UFW BLOCK] IN=eth0 OUT= MAC=00:50:2c:a4:98:7a:00:1f:fe:84:e3:00:08:00 SRC=69.5.93.19 DST=152.65.95.52 LEN=1500 TOS=0x00 PREC=0x00 TTL=63 ID=55317 DF PROTO=TCP SPT=80 DPT=58450 WINDOW=6528 RES=0x00 ACK URGP=0 
[ 1521.444487] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=115 TOS=0x00 PREC=0x00 TTL=255 ID=15748 PROTO=UDP SPT=5353 DPT=5353 LEN=95 
[ 1521.694262] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=245 TOS=0x00 PREC=0x00 TTL=255 ID=7599 PROTO=UDP SPT=5353 DPT=5353 LEN=225 
[ 1522.695081] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=245 TOS=0x00 PREC=0x00 TTL=255 ID=64149 PROTO=UDP SPT=5353 DPT=5353 LEN=225 
[ 1524.694359] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=245 TOS=0x00 PREC=0x00 TTL=255 ID=55944 PROTO=UDP SPT=5353 DPT=5353 LEN=225 
[ 1528.694393] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=245 TOS=0x00 PREC=0x00 TTL=255 ID=37359 PROTO=UDP SPT=5353 DPT=5353 LEN=225 
[ 1536.701627] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=245 TOS=0x00 PREC=0x00 TTL=255 ID=58040 PROTO=UDP SPT=5353 DPT=5353 LEN=225 
[ 1714.681958] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=124 TOS=0x00 PREC=0x00 TTL=255 ID=464 PROTO=UDP SPT=5353 DPT=5353 LEN=104 
[ 1715.576996] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=228 TOS=0x00 PREC=0x00 TTL=255 ID=30871 PROTO=UDP SPT=5353 DPT=5353 LEN=208 
[ 1716.577209] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=282 TOS=0x00 PREC=0x00 TTL=255 ID=23545 PROTO=UDP SPT=5353 DPT=5353 LEN=262 
[ 1720.587720] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:0d:88:c2:85:9e:08:00 SRC=152.65.94.140 DST=224.0.0.251 LEN=282 TOS=0x00 PREC=0x00 TTL=255 ID=47537 PROTO=UDP SPT=5353 DPT=5353 LEN=262 

```

---

### Post by entw on 2011-09-04
Have you solved this issue?

---

### Post by argoth on 2011-09-05
No, never did. I've since parted with the machine so it's not much of an issue for me (and I'll be no help troubleshooting). Hope you can find answer (if you're having the same problem)!

---

