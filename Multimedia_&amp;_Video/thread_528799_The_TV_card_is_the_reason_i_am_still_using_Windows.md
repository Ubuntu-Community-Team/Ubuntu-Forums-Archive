---
title: "The TV card is the reason i am still using Windows"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by rubab on 2007-08-18
I installed Ubuntu for the first time.
Now i have a TV card "AVerTV GO 007 Plus-FM Plus" .
I cannot find the Necessary driver and Software for Ubuntu . It is working fine on WindowsXP.
But in Ubuntu i don't even know that was Ubuntu able to detect my TV card. The line in from the TV card to the Sound card is also connected.
Just look at this post:
[http://ubuntuforums.org/showthread.php?t=523479&goto=newpost]("http://ubuntuforums.org/showthread.php?t=523479&goto=newpost")

I did lspci -vv in the terminal and it showed:

> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
Subsystem: Intel Corporation Unknown device 4156
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
Latency: 0
Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000a000-0000afff
Memory behind bridge: ffa00000-ffafffff
Prefetchable memory behind bridge: c0000000-dfffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
Capabilities: [88] Subsystem: Intel Corporation Unknown device 0000
Capabilities: [80] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0300c Data: 41c9
Capabilities: [a0] Express Root Port (Slot+) IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
Device: Latency L0s <64ns, L1 <1us
Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 2
Link: Latency L0s <256ns, L1 <4us
Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
Link: Speed 2.5Gb/s, Width x16
Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
Slot: Number 0, PowerLimit 75.000000
Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
Slot: AttnInd Off, PwrInd On, Power-
Root: Correctable- Non-Fatal- Fatal- PME-

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
Subsystem: Intel Corporation Unknown device e203
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 16
Region 0: Memory at ff4fc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Address: 0000000000000000 Data: 0000
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

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
Memory behind bridge: ff600000-ff6fffff
Prefetchable memory behind bridge: 00000000bfc00000-00000000bfcfffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
Capabilities: [40] Express Root Port (Slot+) IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
Device: Latency L0s unlimited, L1 unlimited
Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
Link: Latency L0s <1us, L1 <4us
Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x0
Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
Slot: Number 1, PowerLimit 0.000000
Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
Slot: AttnInd Unknown, PwrInd Unknown, Power-
Root: Correctable- Non-Fatal- Fatal- PME-
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0300c Data: 41d1
Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
Capabilities: [a0] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
Memory behind bridge: ff700000-ff7fffff
Prefetchable memory behind bridge: 00000000bfd00000-00000000bfdfffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
Capabilities: [40] Express Root Port (Slot+) IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
Device: Latency L0s unlimited, L1 unlimited
Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
Link: Latency L0s <1us, L1 <4us
Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x0
Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
Slot: Number 2, PowerLimit 0.000000
Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
Slot: AttnInd Unknown, PwrInd Unknown, Power-
Root: Correctable- Non-Fatal- Fatal- PME-
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0300c Data: 41d9
Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
Capabilities: [a0] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
Memory behind bridge: ff800000-ff8fffff
Prefetchable memory behind bridge: 00000000bfe00000-00000000bfefffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
Capabilities: [40] Express Root Port (Slot+) IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
Device: Latency L0s unlimited, L1 unlimited
Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 3
Link: Latency L0s <1us, L1 <4us
Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x0
Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
Slot: Number 3, PowerLimit 0.000000
Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
Slot: AttnInd Unknown, PwrInd Unknown, Power-
Root: Correctable- Non-Fatal- Fatal- PME-
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0300c Data: 41e1
Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
Capabilities: [a0] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Memory behind bridge: ff900000-ff9fffff
Prefetchable memory behind bridge: 00000000bff00000-00000000bfffffff
Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
Capabilities: [40] Express Root Port (Slot+) IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
Device: Latency L0s unlimited, L1 unlimited
Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 4
Link: Latency L0s <1us, L1 <4us
Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x0
Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
Slot: Number 4, PowerLimit 0.000000
Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
Slot: AttnInd Unknown, PwrInd Unknown, Power-
Root: Correctable- Non-Fatal- Fatal- PME-
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Address: fee0300c Data: 41e9
Capabilities: [90] Subsystem: Gammagraphx, Inc. Unknown device 0000
Capabilities: [a0] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin A routed to IRQ 20
Region 4: I/O ports at cc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin B routed to IRQ 19
Region 4: I/O ports at d000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin C routed to IRQ 18
Region 4: I/O ports at d400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin D routed to IRQ 16
Region 4: I/O ports at d800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin A routed to IRQ 20
Region 0: Memory at ff4fbc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: ff500000-ff5fffff
Prefetchable memory behind bridge: 00000000bfb00000-00000000bfbfffff
Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device 0000

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin A routed to IRQ 18
Region 0: I/O ports at 01f0 [size=8]
Region 1: I/O ports at 03f4 [size=1]
Region 2: I/O ports at 0170 [size=8]
Region 3: I/O ports at 0374 [size=1]
Region 4: I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin B routed to IRQ 19
Region 0: I/O ports at ec00 [size=8]
Region 1: I/O ports at e800 [size=4]
Region 2: I/O ports at e400 [size=8]
Region 3: I/O ports at e000 [size=4]
Region 4: I/O ports at dc00 [size=16]
Capabilities: [70] Power Management version 2
Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
Subsystem: Intel Corporation Unknown device 4156
Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Interrupt: pin B routed to IRQ 10
Region 4: I/O ports at c800 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600] (prog-if 00 [VGA])
Subsystem: PC Partner Limited Unknown device 0880
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 16
Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
Region 2: Memory at ffa20000 (64-bit, non-prefetchable) [size=64K]
Region 4: I/O ports at a800 [size=256]
Expansion ROM at ffa00000 [disabled] [size=128K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [58] Express Endpoint IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
Device: Latency L0s <4us, L1 unlimited
Device: AtnBtn- AtnInd- PwrInd-
Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
Device: RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
Link: Latency L0s <64ns, L1 <1us
Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
Link: Speed 2.5Gb/s, Width x16
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Address: 0000000000000000 Data: 0000

01:00.1 Display controller: ATI Technologies Inc Unknown device 71e6
Subsystem: PC Partner Limited Unknown device 0881
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Region 0: Memory at ffa30000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [58] Express Endpoint IRQ 0
Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
Device: Latency L0s <4us, L1 unlimited
Device: AtnBtn- AtnInd- PwrInd-
Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
Link: Latency L0s <64ns, L1 <1us
Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
Link: Speed 2.5Gb/s, Width x16

06:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
Subsystem: Avermedia Technologies Inc Unknown device d109
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (63750ns min, 63750ns max)
Interrupt: pin A routed to IRQ 21
Region 0: Memory at ff520000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [40] Power Management version 1
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=3 PME-

06:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
Subsystem: Conexant Unknown device 2000
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32
Interrupt: pin A routed to IRQ 5
Region 0: Memory at ff500000 (32-bit, non-prefetchable) [size=64K]
Region 1: I/O ports at bc00 [size=8]
Capabilities: [40] Power Management version 2
Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

06:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RT8139
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (8000ns min, 16000ns max)
Interrupt: pin A routed to IRQ 19
Region 0: I/O ports at b800 [size=256]
Region 1: Memory at ff520400 (32-bit, non-prefetchable) [size=256]
Expansion ROM at bfb00000 [disabled] [size=64K]
Capabilities: [50] Power Management version 2
Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by mocha on 2007-08-18
Get a Hauppauge PVR card, they're awesome in Linux with MythTV.  They're also about $50 on Ebay

---

### Post by crispy_420 on 2007-08-18
Did you search the forums on how to setup a Phillips SAA7130 chipset? Or even debain + SAA7130 on google?

---

### Post by wolfen69 on 2007-08-19
hauppauge is the way to go. supported out of the box.

---

