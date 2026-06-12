---
title: "Generic Bt878 TV tuner + FM with PAL_BG LG tuner"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by endangst on 2006-01-01
Hi.  I am a newbie to Linux, but have been reading a lot on Google about my TV tuner card.

My TV tuner card works in Windows XP in DScaler as "Pixelview PlayTV Pro", yet this card is a "MuchTV" brand with bt878 chip and LG tuner (PAL-BG) + FM.

It has composite and s-video inputs, but I use the composite video input for watching TV from my Satellite decoder box.
 
**Here is the output of lspci -vvn:**
 
endangst@ubuntu:~$ sudo lspci -vvn
Password:
0000:00:00.0 0600: 10de:01e0 (rev c1)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [40] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=2 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=x4        Capabilities: [60] #08 [2001]

0000:00:00.1 0500: 10de:01ea (rev c1)
        Subsystem: 1297:0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.2 0500: 10de:01ee (rev c1)
        Subsystem: 1297:0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.3 0500: 10de:01ed (rev c1)
        Subsystem: 1297:0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.4 0500: 10de:01ec (rev c1)
        Subsystem: 1297:0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.5 0500: 10de:01ef (rev c1)
        Subsystem: 1297:0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:01.0 0601: 10de:0060 (rev a4)
        Subsystem: 1297:0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [48] #08 [01e1]

0000:00:01.1 0c05: 10de:0064 (rev a2)
        Subsystem: 1297:0531
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at e800 [size=32]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:02.0 0c03: 10de:0067 (rev a4) (prog-if 10)
        Subsystem: 1297:0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at e3001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:02.1 0c03: 10de:0067 (rev a4) (prog-if 10)
        Subsystem: 1297:0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 21
        Region 0: Memory at e3002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:08.0 0604: 10de:006c (rev a3)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Prefetchable memory behind bridge: e2000000-e2ffffff
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

0000:00:09.0 0101: 10de:0065 (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: 1297:0531
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 4: I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:1e.0 0604: 10de:01e8 (rev c1)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-

0000:01:04.0 0401: 1102:0006
        Subsystem: 1102:1004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at d000 [size=32]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:06.0 0400: 109e:036e (rev 11)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (4000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e2000000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:06.1 0480: 109e:0878 (rev 11)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1000ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e2001000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:00.0 0300: 10de:0181 (rev a4)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

---

### Post by endangst on 2006-01-01
**Here is lspci -vv:**
 
endangst@ubuntu:~$ sudo lspci -vv
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [40] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=2 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=x4        Capabilities: [60] #08 [2001]

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [48] #08 [01e1]

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at e800 [size=32]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at e3001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 21
        Region 0: Memory at e3002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Prefetchable memory behind bridge: e2000000-e2ffffff
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 0531
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 4: I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-

0000:01:04.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
        Subsystem: Creative Labs: Unknown device 1004
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at d000 [size=32]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (4000ns min, 10000ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e2000000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1000ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e2001000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
 
**And finally here is dmesg:**
 
endangst@ubuntu:~$ dmesg

[4303862.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303862.310000] bttv0: reset, reinitialize
[4303862.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303862.810000] bttv0: reset, reinitialize
[4303863.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303863.310000] bttv0: reset, reinitialize
[4303863.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303863.810000] bttv0: reset, reinitialize
[4303864.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303864.310000] bttv0: reset, reinitialize
[4303864.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303864.810000] bttv0: reset, reinitialize
[4303865.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303865.310000] bttv0: reset, reinitialize
[4303865.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303865.810000] bttv0: reset, reinitialize
[4303866.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303866.310000] bttv0: reset, reinitialize
[4303866.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303866.810000] bttv0: reset, reinitialize
[4303867.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303867.310000] bttv0: reset, reinitialize
[4303867.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303867.810000] bttv0: reset, reinitialize
[4303868.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303868.310000] bttv0: reset, reinitialize
[4303868.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303868.810000] bttv0: reset, reinitialize
[4303869.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303869.310000] bttv0: reset, reinitialize
[4303869.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303869.810000] bttv0: reset, reinitialize
[4303870.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303870.310000] bttv0: reset, reinitialize
[4303870.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303870.810000] bttv0: reset, reinitialize
[4303871.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303871.310000] bttv0: reset, reinitialize
[4303871.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303871.810000] bttv0: reset, reinitialize
[4303872.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303872.310000] bttv0: reset, reinitialize
[4303872.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303872.810000] bttv0: reset, reinitialize
[4303873.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303873.310000] bttv0: reset, reinitialize
[4303873.810000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303873.810000] bttv0: reset, reinitialize
[4303874.310000] bttv0: timeout: drop=51 irq=40380/40380, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303874.310000] bttv0: reset, reinitialize
[4303876.337000] bttv0: timeout: drop=51 irq=40404/40404, risc=00eb122c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303876.337000] bttv0: reset, reinitialize
[4303876.837000] bttv0: timeout: drop=51 irq=40404/40404, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303876.837000] bttv0: reset, reinitialize
[4303882.725000] bttv0: timeout: drop=56 irq=40483/40483, risc=00416574, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303882.725000] bttv0: reset, reinitialize
[4303886.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=00eb1884, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303886.712000] bttv0: reset, reinitialize
[4303887.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303887.212000] bttv0: reset, reinitialize
[4303887.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303887.712000] bttv0: reset, reinitialize
[4303888.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303888.212000] bttv0: reset, reinitialize
[4303888.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303888.712000] bttv0: reset, reinitialize
[4303889.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303889.212000] bttv0: reset, reinitialize
[4303889.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303889.712000] bttv0: reset, reinitialize
[4303890.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303890.212000] bttv0: reset, reinitialize
[4303890.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303890.712000] bttv0: reset, reinitialize
[4303891.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303891.212000] bttv0: reset, reinitialize
[4303891.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303891.712000] bttv0: reset, reinitialize
[4303892.212000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303892.212000] bttv0: reset, reinitialize
[4303892.712000] bttv0: timeout: drop=57 irq=40534/40534, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303892.712000] bttv0: reset, reinitialize
[4303893.600000] bttv0: timeout: drop=57 irq=40537/40537, risc=00eb089c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303893.600000] bttv0: reset, reinitialize
[4303894.100000] bttv0: timeout: drop=57 irq=40537/40537, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303894.100000] bttv0: reset, reinitialize
[4303894.600000] bttv0: timeout: drop=57 irq=40537/40537, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303894.600000] bttv0: reset, reinitialize
[4303895.100000] bttv0: timeout: drop=57 irq=40537/40537, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303895.100000] bttv0: reset, reinitialize
[4303895.600000] bttv0: timeout: drop=57 irq=40537/40537, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303895.600000] bttv0: reset, reinitialize
[4303896.100000] bttv0: timeout: drop=57 irq=40537/40537, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303896.100000] bttv0: reset, reinitialize
[4303898.581000] bttv0: timeout: drop=58 irq=40568/40568, risc=0041bbd4, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303898.581000] bttv0: reset, reinitialize
[4303899.081000] bttv0: timeout: drop=58 irq=40568/40568, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303899.081000] bttv0: reset, reinitialize
[4303899.915000] bttv0: timeout: drop=58 irq=40573/40573, risc=199dc03c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303899.915000] bttv0: reset, reinitialize
[4303901.255000] bttv0: timeout: drop=58 irq=40584/40584, risc=00416894, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303901.255000] bttv0: reset, reinitialize
[4303901.755000] bttv0: timeout: drop=58 irq=40584/40584, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303901.755000] bttv0: reset, reinitialize
[4303902.255000] bttv0: timeout: drop=58 irq=40584/40584, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303902.255000] bttv0: reset, reinitialize
[4303902.755000] bttv0: timeout: drop=58 irq=40584/40584, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303902.755000] bttv0: reset, reinitialize
[4303903.255000] bttv0: timeout: drop=58 irq=40584/40584, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303903.255000] bttv0: reset, reinitialize
[4303903.755000] bttv0: timeout: drop=58 irq=40584/40584, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303903.755000] bttv0: reset, reinitialize
[4303905.970000] bttv0: timeout: drop=58 irq=40613/40613, risc=0055901c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303905.970000] bttv0: reset, reinitialize
[4303907.916000] bttv0: timeout: drop=58 irq=40635/40635, risc=00544534, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303907.916000] bttv0: reset, reinitialize
[4303908.416000] bttv0: timeout: drop=58 irq=40635/40635, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303908.416000] bttv0: reset, reinitialize
[4303908.916000] bttv0: timeout: drop=58 irq=40635/40635, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303908.916000] bttv0: reset, reinitialize
[4303909.416000] bttv0: timeout: drop=58 irq=40635/40635, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303909.416000] bttv0: reset, reinitialize
[4303909.916000] bttv0: timeout: drop=58 irq=40635/40635, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303909.916000] bttv0: reset, reinitialize
[4303910.870000] bttv0: timeout: drop=58 irq=40639/40639, risc=00544884, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303910.870000] bttv0: reset, reinitialize
[4303913.652000] bttv0: timeout: drop=59 irq=40667/40667, risc=199dc01c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303913.652000] bttv0: reset, reinitialize
[4303914.152000] bttv0: timeout: drop=59 irq=40667/40667, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303914.152000] bttv0: reset, reinitialize
[4303915.791000] bttv0: timeout: drop=59 irq=40680/40680, risc=0054488c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303915.791000] bttv0: reset, reinitialize
[4303916.291000] bttv0: timeout: drop=59 irq=40680/40680, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303916.291000] bttv0: reset, reinitialize
[4303916.791000] bttv0: timeout: drop=59 irq=40680/40680, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303916.791000] bttv0: reset, reinitialize
[4303918.992000] bttv0: timeout: drop=59 irq=40699/40699, risc=199dc01c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303918.992000] bttv0: reset, reinitialize
[4303919.492000] bttv0: timeout: drop=59 irq=40699/40699, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303919.492000] bttv0: reset, reinitialize
[4303919.992000] bttv0: timeout: drop=59 irq=40699/40699, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303919.992000] bttv0: reset, reinitialize
[4303920.492000] bttv0: timeout: drop=59 irq=40699/40699, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303920.492000] bttv0: reset, reinitialize
[4303922.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303922.494000] bttv0: reset, reinitialize
[4303922.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303922.994000] bttv0: reset, reinitialize
[4303923.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303923.494000] bttv0: reset, reinitialize
[4303923.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303923.994000] bttv0: reset, reinitialize
[4303924.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303924.494000] bttv0: reset, reinitialize
[4303924.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303924.994000] bttv0: reset, reinitialize
[4303925.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW VPRES RISCI
[4303925.494000] bttv0: reset, reinitialize
[4303925.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303925.994000] bttv0: reset, reinitialize
[4303926.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW VPRES RISCI
[4303926.494000] bttv0: reset, reinitialize
[4303926.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303926.994000] bttv0: reset, reinitialize
[4303927.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303927.494000] bttv0: reset, reinitialize
[4303927.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303927.994000] bttv0: reset, reinitialize
[4303928.494000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303928.494000] bttv0: reset, reinitialize
[4303928.994000] bttv0: timeout: drop=60 irq=40716/40716, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303928.994000] bttv0: reset, reinitialize
[4303934.021000] bttv0: timeout: drop=60 irq=40781/40781, risc=004161e4, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303934.021000] bttv0: reset, reinitialize
[4303934.521000] bttv0: timeout: drop=60 irq=40781/40781, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303934.521000] bttv0: reset, reinitialize
[4303935.436000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc03c, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303935.436000] bttv0: reset, reinitialize
[4303935.936000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303935.936000] bttv0: reset, reinitialize
[4303936.436000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303936.436000] bttv0: reset, reinitialize
[4303936.936000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303936.936000] bttv0: reset, reinitialize
[4303937.436000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303937.436000] bttv0: reset, reinitialize
[4303937.936000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303937.936000] bttv0: reset, reinitialize
[4303938.436000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303938.436000] bttv0: reset, reinitialize
[4303938.936000] bttv0: timeout: drop=60 irq=40784/40784, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303938.936000] bttv0: reset, reinitialize
[4303939.877000] bttv0: timeout: drop=60 irq=40789/40789, risc=00559934, bits: VSYNC HSYNC OFLOW RISCI FBUS FDSR
[4303939.877000] bttv0: reset, reinitialize
[4303940.377000] bttv0: timeout: drop=60 irq=40789/40789, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303940.377000] bttv0: reset, reinitialize
[4303940.877000] bttv0: timeout: drop=60 irq=40789/40789, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303940.877000] bttv0: reset, reinitialize
[4303941.377000] bttv0: timeout: drop=60 irq=40789/40789, risc=199dc03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303941.377000] bttv0: reset, reinitialize
[4303941.877000] bttv0: timeout: drop=60 irq=40789/40789, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303941.877000] bttv0: reset, reinitialize
[4303942.377000] bttv0: timeout: drop=60 irq=40789/40789, risc=199dc01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[4303942.377000] bttv0: reset, reinitialize
 
I tried using modprobe, but to no avail.
 
What I see on the screen is several, black & white, fuzzy and jumpy pictures when selecting "Composite 1".
 
Any help is greatly, greatly appreciated.  It works just fine in Windows as PlayTV Pro, so if there is a way to force it to be detected as PlayTV Pro (with LG PAL-BG + FM tuner), maybe it will work.... I hope.
 
Thanks!!

Endang

---

### Post by endangst on 2006-01-01
Ok, I did this as another page on this website suggested:

sudo gedit /etc/modprobe.d/bttv

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=37 tuner=28 radio=1 pll=1 adc_crush=0

I also sudo modprobe -r bttv and sudo modprobe bttv

**I now get video!**  But...it hangs after 10 or 15 seconds.
**No sound** when watching video and I adjusted my sound card settings such as Line-In.  (My TV tuner has a line out jack for the audio that I connect to the line-in on my soundcard.  Creative Ectiva 5.1 soundcard.)

I hear static even as I am typing to you now, even though the Tvtime isn't running.
But when I run Tvtime, then the sound stops.
 
I guess I just have to figure out how to get audio working.
 
Any help is greatly appreciated. ;)

---

### Post by endangst on 2006-01-02
### BtSpy Report ###



General information:

 Name:MuchTV Fusion

 Chip: Bt878 , Rev: 0x00

 Subsystem: 0x00000000

 Vendor: Gammagraphx, Inc.

 Values to MUTE audio:

  Mute_GPOE  : 0x1c800f

  Mute_GPDATA: 0x08000d

 Has TV Tuner: Yes

  TV_Mux   : 2

  TV_GPOE  : 0x1c800f

  TV_GPDATA: 0x080008

 Number of Composite Ins: 1

  Composite in #1

   Composite1_Mux   : 3

   Composite1_GPOE  : 0x1c800f

   Composite1_GPDATA: 0x08000a

 Has SVideo: Yes

  SVideo_Mux   : 1

  SVideo_GPOE  : 0x1c800f

  SVideo_GPDATA: 0x08000a

 Has Radio: Yes

  Radio_GPOE  : 0x1c800f

  Radio_GPDATA: 0x080009


Does anyone know how to use these values with /etc/modprobe.d/bttv?
:confused:

---

### Post by endangst on 2006-01-08
I could never get the audio working, but I found a setting (card=16) where the video works just fine in Tvtime.

Then I figured out that since I don't use it as a TV tuner, but rather to watch video through composite only, that I can just plug the audio from the satellite decoder box straight into my soundcard.  

Problem solved! hehheh.  (As long as I don't try to use it as a tuner)

---

