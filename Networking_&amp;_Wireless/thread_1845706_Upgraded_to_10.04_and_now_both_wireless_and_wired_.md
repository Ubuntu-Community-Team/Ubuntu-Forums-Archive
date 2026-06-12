---
title: "Upgraded to 10.04 and now both wireless and wired networking are disabled"
date: 2011-09-17
forum: Networking &amp; Wireless
---

### Post by mlebaron on 2011-09-17
Upgraded to 10.04 and now both wireless and wired networking are disabled.  Please help.

Here's some info that I see people provide in other similar threads:

eth0      Link encap:Ethernet  HWaddr 00:1c:25:3c:a2:9b  
          inet6 addr: fe80::21c:25ff:fe3c:a29b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1152 (1.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10991 (10.9 KB)  TX bytes:10991 (10.9 KB)

mark@kitchen-desktop-ubuntu64:~$ dmesg | grep -i eth
[    1.037662] sky2 eth0: addr 00:1c:25:3c:a2:9b
[   29.694715] sky2 eth0: enabling interface
[   29.695774] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.661456] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   31.662581] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.272513] eth0: no IPv6 routers present
[  156.342534] sky2 eth0: disabling interface
[  167.288237] sky2 eth0: enabling interface
[  167.290512] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  169.350316] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  169.352502] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  180.250025] eth0: no IPv6 routers present


Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

mark@kitchen-desktop-ubuntu64:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Foxconn International, Inc. Device 0e0a
	Kernel modules: shpchp

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surpise-
			Slot #  6, PowerLimit 25.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd Off, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 4149
	Capabilities: [b0] Subsystem: Foxconn International, Inc. Device 0e0a
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at ff00 [size=8]
	Region 1: I/O ports at fe00 [size=4]
	Region 2: I/O ports at fd00 [size=8]
	Region 3: I/O ports at fc00 [size=4]
	Region 4: I/O ports at fb00 [size=16]
	Region 5: Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: I/O ports at 0b00 [size=16]
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f900 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fda00000-fdafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at fdef0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at de00 [size=256]
	Region 5: Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 20)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 25
	Region 0: Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 4179
	Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 unlimited
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fdbff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fdbf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:01.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
	Subsystem: Motorola Device 3020
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (250ns min, 15500ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fdbfe000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at ce00 [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: serial

03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Foxconn International, Inc. Device 0e0a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fdbfd000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fdbf4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394


mark@kitchen-desktop-ubuntu64:~$ dmesg | grep -i eth
[    1.037662] sky2 eth0: addr 00:1c:25:3c:a2:9b
[   29.694715] sky2 eth0: enabling interface
[   29.695774] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.661456] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   31.662581] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.272513] eth0: no IPv6 routers present
[  156.342534] sky2 eth0: disabling interface
[  167.288237] sky2 eth0: enabling interface
[  167.290512] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  169.350316] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  169.352502] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  180.250025] eth0: no IPv6 routers present



mark@kitchen-desktop-ubuntu64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:3c:a2:9b  
          inet6 addr: fe80::21c:25ff:fe3c:a29b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1152 (1.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32079 (32.0 KB)  TX bytes:32079 (32.0 KB)

---

### Post by vst0rm on 2011-09-17
the wired device looks ok, if i don't overlook something. Have you tried ?```
sudo dhclient eth0
``` but I can't see your wireless device. What says ? ```
sudo iwconfig
``` I also realized that only the loopback interface is in /etc/network/interfaces > mark@kitchen-desktop-ubuntu64:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback don't know if this is normal in ubuntu cause networkmanager or something never used it yet

---

### Post by mlebaron on 2011-09-17
Thanks for your response, vst0rm.  I should have mentioned that the reason I switched to wired was because I discovered that the wireless has stopped working after the upgrade.  I moved my wireless router in closer proximity to my computer and then hard-wired it.  The Windows boot picked up the hard-wired router/DHCP server just fine.  But if I boot to Ubuntu, it tells me there is no network connection.

Here are the results:

mark@kitchen-desktop-ubuntu64:~$ sudo dhclient eth0
[sudo] password for mark: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1c:25:3c:a2:9b
Sending on   LPF/eth0/00:1c:25:3c:a2:9b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mark@kitchen-desktop-ubuntu64:~$

---

### Post by vst0rm on 2011-09-17
you could try to setup static IP but I guess this wouldn't work either
```

sudo ifconfig eth0 "IP" netmask "netmask" up
sudo route add default gw "route IP" dev eth0
ping "router IP"

```example:
```

sudo ifconfig eth0 192.168.1.66 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 dev eth0
ping 192.168.1.1

```I have no idea what this could be don't see any error ... hope someone else have some ideas sorry for my english ^^

---

### Post by pdc on 2011-09-17
here is a diagnostic script; developed by a linux wireless expert

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Schnellstart/Quickstart.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Schnellstart/Quickstart.html#English)

run this; it should offer suggestions; post the results back here;

let's see if it can get you going

---

### Post by mlebaron on 2011-09-18
```

collectNWData.sh V0.6.5.4.5 (Rev: 1.291, Build: 2011/09/17 12:11:25 UTC)
--- Which type of your network connection should be tested?
--- (1) Wired connection
--- What's the type of networktopology?
--- (1) DSL modem <---> LinuxClient
--- On which host is the script executed?
--- (1) LinuxClient

--- NWEliza is analyzing the system for common network configuration errors ...

!!! CND0120E: Network card eth0 has no IP address
!!! CND0450W: WLAN key masquerading is not fully tested on this distribution. Please check output file collectNWData.txt for visible WLAN keys and masquerade them manually

--- Go to http://www.linux-tips-and-tricks.de/CND#English to get more detailed instructions 
--- about the error/warning messages and how to fix the problems on your own.

--- If you are unsuccessful then place the contents of file collectNWData.txt in the net
--- (see http://www.linux-tips-and-tricks.de/CND_UPL#English for links) 
--- and then paste the nopaste link on your favorite Linux forum.

==================================================================================================================
===== cat /etc/*[-_]release || cat /etc/*[-_]version =============================================================
/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"
===== uname -a ===================================================================================================
Linux kitchen-desktop-ubuntu64 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
===== lspci ======================================================================================================
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 20)
	Kernel driver in use: sky2
	Kernel modules: sky2
===== lsusb | grep -v "root hub" =================================================================================
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 003: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
===== lshw -C network (filtered) =================================================================================
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
===== lsmod (filtered) ===========================================================================================
| ahci            | binfmt_misc     | bitblit         | drm             | drm_kms_helper   |
| edac_core       | edac_mce_amd    | fbcon           | font            | hid              |
| i2c_algo_bit    | i2c_piix4       | ieee1394        | k8temp          | led_class        |
| lp              | ohci1394        | ppdev           | radeon          | serio_raw        |
| shpchp          | sky2            | softcursor      | tileblit        | ttm              |
| usblp           | usb_storage     | vga16fb         | vgastate        |
===== ifconfig (filtered for eth|wlan|ra|ath|dsl) ================================================================
eth0      Link encap:Ethernet  HWaddr ##:##:##:##:##:#1  
          inet6 addr: fe80::21c:25ff:fe3c:a29b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 
===== cat /etc/network/interfaces | grep -v "=''" ================================================================
--- /etc/network/interfaces
auto lo
iface lo inet loopback
===== ping tests =================================================================================================
connect: Network is unreachable
Ping of 195.135.220.3 failed
ping: unknown host www.suse.de
Ping of www.suse.de failed
===== cat /etc/resolv | grep -i "nameserver" =====================================================================
===== cat /etc/hosts =============================================================================================
127.0.0.1	localhost
127.0.1.1	kitchen-desktop-ubuntu64
===== route -n | egrep "(eth|ath|ra|wlan|dsl)" ===================================================================
===== egrep 'eth|ath|wlan|ra' /etc/udev/rules.d/*net_persistent* /etc/udev/rules.d/*persistent-net* ==============
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#1", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="##:##:##:##:##:#2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
==================================================================================================================
*** NWElizaStates V0.6.5.4.5
IF:eth0 IM:1 DI:1 FALON:1 NIC:1 cNiC:1:1 NI:2 cNI:2 NIWD:0 IP6:0 WLW:0 RTDT:debian 

```

---

### Post by mathia on 2011-09-19
Hi,
for your wired card try the following:

**[B]Installing Marvell Yukon 88E8056 driver on Ubuntu**:[/B]

Please login as root and install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8056 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 ... v10.90.5.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by mlebaron on 2011-09-19
Running
```

$ sudo bash ./install.sh

```
Completed with no errors but it didn't enable my networking.
I logged out and logged back in: still no networking.
I rebooted: still no networking.

They should call it "notworking" instead of "networking".

Thanks all for the attempts to help.  I'm running out of patience but I'm willing to give it one more try if there is someone out there who can think of a solution.

---

### Post by mlebaron on 2011-09-20
V$torm, I tried setting up a static IP address but that didn't help.  Afterward, I tried pinging the router but it didn't even try to ping; it just said no networking available (or words to that effect).

---

### Post by mlebaron on 2011-09-20
Here's my latest ifconfig

```

mark@kitchen-desktop-ubuntu64:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:3c:a2:9b  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe3c:a29b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12914 (12.9 KB)  TX bytes:12914 (12.9 KB)

mark@kitchen-desktop-ubuntu64:~$ 

```

---

### Post by mlebaron on 2011-09-24
So, nobody can help on this?

Just to summarize...
I had Ubuntu whatever running well with wireless network.
Upgraded to 10.04 and wireless stopped working.
Figured I'd just move my router closer to my computer and use wired networking.  That didn't work either.  Tried various ideas from this thread but no luck.

This same computer dual boots to Windows Vista with no problems.  Both wired and wireless networking works fine under Vista.

Seriously, Ubuntu isn't much good to me without networking.

Also, I'm pretty much fed up with Ubuntu because some crazy thing always happens every time I run one of their upgrades.  One time the screen went black after the upgrade.

I'm going back to Windows and my two Macs.  I'm removing my "duuubuntutu?" bumper sticker.  I'm taking my "like" of Ubuntu off BOTH my LinkedIn AND FaceBook pages.

Good bye cruel Ubuntu world!

):P

---

### Post by pdc on 2011-09-25
sounds like you are really upset that no-one could offer you advice to help fix your problems;

when you ran the diagnostic script ...it said.......amongst other things..

> !!! **CND0120E**: Network card eth0 has no IP address

and it told you to go to this website 

[http://www.linux-tips-and-tricks.de/index.php/Table/Messages/#English](http://www.linux-tips-and-tricks.de/index.php/Table/Messages/#English)

and then you had to click on the button

> CND0120E

and it takes one here

[http://www.linux-tips-and-tricks.de/index.php/collectNWData/CND0120E.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData/CND0120E.html#English)

and it gives possible causes

> **Cause for error message** 
Possible causes:

    1. There **was** DCP defined for the network card ...and there doesn't exist a DHCP server ....or the server can't be contacted
    2. There was not an IP address defined for a static defined interface




.......you say "upgraded" to 10.04.......... "upgrading" in linux is still felt to be inferior to a new install ............

---

### Post by mathia on 2011-10-02
> **mlebaron said:**
> Running
```

$ sudo bash ./install.sh

```Completed with no errors but it didn't enable my networking.
I logged out and logged back in: still no networking.
I rebooted: still no networking.

They should call it "notworking" instead of "networking".

Thanks all for the attempts to help.  I'm running out of patience but I'm willing to give it one more try if there is someone out there who can think of a solution.

Hi,
sorry to answer you so late, I was in vacation!

Please post here the install.log file, which is in the same directory as install.sh.
Please send me the output of the following command:
$ sudo lsmod | grep sk

P.S.: Please think about it, now you have 2 drivers ("sky2" and " sk98lin") for your marvell device. So only one of them here: "sk98lin" must be loaded!

---

