---
title: "ATI Technologies Inc IXP SB400 AC'97 Audio &quot;Not found&quot; in Alsa or anywhere"
date: 2009-03-16
forum: Multimedia Software
---

### Post by AlexTepes on 2009-03-16
Now I've tried to like this "purefailaudio" they shove down our throats but I can't use it because it uses alsa and alsa doesn't detect my sound card.
And it worked on 8.04.
(So I guess IT isn't pure fail but alsa or Ubuntu is)
Now I've spent a good 12 hours reading through Ubuntu forums and google and can't find a damn solution and Alsa says it supports my sound card "atiixp" I think they're calling it.

Heres some things you'll probably need.


```
Linux otaku 2.6.25-2-386 #1 Tue Sep 30 14:47:35 UTC 2008 i686 GNU/Linux
```


```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 64
	Kernel modules: ati-agp

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Kernel modules: shpchp

00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at ff00 [size=8]
	Region 1: I/O ports at fe00 [size=4]
	Region 2: I/O ports at fd00 [size=8]
	Region 3: I/O ports at fc00 [size=4]
	Region 4: I/O ports at fb00 [size=16]
	Region 5: Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
	Expansion ROM at fdf80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 81)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: I/O ports at 0b00 [size=16]
	Region 1: Memory at fe02b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f900 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Kernel driver in use: ATIIXP_IDE
	Kernel modules: pata_atiixp, atiixp

00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 80)
	Subsystem: Hewlett-Packard Company Device [103c:2a27]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] [1002:5954]
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at ee00 [size=256]
	Region 2: Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at dc00 [size=256]
	Region 1: Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

02:05.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device [103c:2a26]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fdcfe000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at df00 [size=128]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

```

```
[    0.000000] Linux version 2.6.25-2-386 (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:47:35 UTC 2008
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005bef0000 (usable)
[    0.000000]  BIOS-e820: 000000005bef0000 - 000000005bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005bef3000 - 000000005bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 574MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Scan SMP from c0000000 for 1024 bytes.
[    0.000000] Scan SMP from c009fc00 for 1024 bytes.
[    0.000000] Scan SMP from c00f0000 for 65536 bytes.
[    0.000000] found SMP MP-table at [c00f5ed0] 000f5ed0
[    0.000000] Entering add_active_range(0, 0, 376560) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   376560
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   376560
[    0.000000] On node 0 totalpages: 376560
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1149 pages used for memmap
[    0.000000]   HighMem zone: 146035 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7AE0, 0014 (r0 HP-CPC)
[    0.000000] ACPI: RSDT 5BEF3040, 0034 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5BEF30C0, 0074 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5BEF3180, 4B6C (r1 HP-CPC AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5BEF0000, 0040
[    0.000000] ACPI: SSDT 5BEF7E00, 00D6 (r1 HP-CPC POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 5BEF7F40, 003C (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 5BEF7D40, 0068 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5bf00000:84100000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373619
[    0.000000] Kernel command line: root=UUID=bac5930f-4203-4f7b-9492-25baf45317e8 ro quiet splash 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1989.834 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1479816k/1506240k available (2161k kernel code, 25068k reserved, 963k data, 356k init, 588736k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc0410000 - 0xc0469000   ( 356 kB)
[    0.004000]       .data : 0xc031c676 - 0xc040d620   ( 963 kB)
[    0.004000]       .text : 0xc0100000 - 0xc031c676   (2161 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    0.084007] Calibrating delay using timer specific routine.. 3983.90 BogoMIPS (lpj=7967800)
[    0.084034] Security Framework initialized
[    0.084041] SELinux:  Disabled at boot.
[    0.084046] Capability LSM initialized
[    0.084051] Mount-cache hash table entries: 512
[    0.084176] Initializing cgroup subsys ns
[    0.084179] Initializing cgroup subsys cpuacct
[    0.084191] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084193] CPU: L2 Cache: 256K (64 bytes/line)
[    0.084200] Compat vDSO mapped to ffffe000.
[    0.084205] CPU: AMD Sempron(tm) Processor 3500+ stepping 02
[    0.084210] Checking 'hlt' instruction... OK.
[    0.101177] Freeing SMP alternatives: 0k freed
[    0.101180] ACPI: Core revision 20070126
[    0.108234] ENABLING IO-APIC IRQs
[    0.108415] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.116007] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.116007] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    0.116007] ...trying to set up timer as Virtual Wire IRQ... works.
[    0.160010] net_namespace: 540 bytes
[    0.160010] Booting paravirtualized kernel on bare hardware
[    0.160010] NET: Registered protocol family 16
[    0.160010] EISA bus registered
[    0.160010] ACPI: bus type pci registered
[    0.160010] PCI: Using MMCONFIG for extended config space
[    0.160010] PCI: Using configuration type 1
[    0.160010] Setting up standard PCI resources
[    0.160010] ACPI: EC: Look up EC in DSDT
[    0.163683] ACPI: Interpreter enabled
[    0.163685] ACPI: (supports S0 S1 S3 S4 S5)
[    0.163697] ACPI: Using IOAPIC for interrupt routing
[    0.166939] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.168002] PCI: Transparent bridge - 0000:00:14.4
[    0.168067] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.168423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.181132] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181243] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181352] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181459] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181567] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181674] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[    0.181781] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.181889] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.182008] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.182030] pnp: PnP ACPI init
[    0.182036] ACPI: bus type pnp registered
[    0.184281] pnp: PnP ACPI: found 10 devices
[    0.184284] ACPI: ACPI bus type pnp unregistered
[    0.184288] PnPBIOS: Disabled by ACPI PNP
[    0.184464] PCI: Using ACPI for IRQ routing
[    0.184467] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.184605] NET: Registered protocol family 8
[    0.184607] NET: Registered protocol family 20
[    0.184661] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.184663] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.184666] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.184668] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.184671] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.184673] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.184675] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.184678] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.184680] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.184683] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.184685] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.184693] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.184695] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.184701] system 00:08: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.184707] system 00:09: iomem range 0xd0000-0xd3fff has been reserved
[    0.184709] system 00:09: iomem range 0xf0000-0xf7fff could not be reserved
[    0.184712] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
[    0.184714] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
[    0.184717] system 00:09: iomem range 0x5bf00000-0x5bffffff has been reserved
[    0.184720] system 00:09: iomem range 0x5bef0000-0x5befffff could not be reserved
[    0.184722] system 00:09: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.184725] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[    0.184728] system 00:09: iomem range 0x100000-0x5beeffff could not be reserved
[    0.184730] system 00:09: iomem range 0x5c000000-0x5fffffff has been reserved
[    0.184733] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.184736] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.184739] system 00:09: iomem range 0xfff80000-0xfffeffff could not be reserved
[    0.215054] PCI: Bridge: 0000:00:01.0
[    0.215057]   IO window: e000-efff
[    0.215060]   MEM window: 0xfdd00000-0xfddfffff
[    0.215063]   PREFETCH window: 0x00000000f0000000-0x00000000f7ffffff
[    0.215066] PCI: Bridge: 0000:00:14.4
[    0.215069]   IO window: d000-dfff
[    0.215075]   MEM window: 0xfdc00000-0xfdcfffff
[    0.215079]   PREFETCH window: 0x00000000fde00000-0x00000000fdefffff
[    0.215107] NET: Registered protocol family 2
[    0.215165] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.215399] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.216474] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.216772] TCP: Hash tables configured (established 131072 bind 65536)
[    0.216776] TCP reno registered
[    0.216961] checking if image is initramfs... it is
[    0.716070] Switched to high resolution mode on CPU 0
[    0.920936] Freeing initrd memory: 8548k freed
[    0.921458] audit: initializing netlink socket (disabled)
[    0.921472] type=2000 audit(1237159510.920:1): initialized
[    0.921605] highmem bounce pool size: 64 pages
[    0.922924] VFS: Disk quotas dquot_6.5.1
[    0.922951] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.923077] io scheduler noop registered
[    0.923079] io scheduler anticipatory registered
[    0.923080] io scheduler deadline registered
[    0.923089] io scheduler cfq registered (default)
[    0.923097] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.964061] pci 0000:01:05.0: Boot video device
[    0.964061] isapnp: Scanning for PnP cards...
[    1.314747] isapnp: No Plug & Play device found
[    1.331097] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.331942] brd: module loaded
[    1.331995] input: Macintosh mouse button emulation as /class/input/input0
[    1.332112] PNP: No PS/2 controller found. Probing ports directly.
[    1.334525] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.334530] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.334673] mice: PS/2 mouse device common for all mice
[    1.334762] EISA: Probing bus 0 at eisa.0
[    1.334782] Cannot allocate resource for EISA slot 4
[    1.334801] EISA: Detected 0 cards.
[    1.334804] cpuidle: using governor ladder
[    1.335194] NET: Registered protocol family 1
[    1.335216] Using IPI Shortcut mode
[    1.335309] registered taskstats version 1
[    1.335403] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[    1.335825] Freeing unused kernel memory: 356k freed
[    1.536161] fuse init (API version 7.9)
[    1.592122] ACPI: PNP0C0B:00 is registered as cooling_device0
[    1.592128] ACPI: Fan [FAN] (on)
[    1.619357] ACPI: ACPI0007:00 is registered as cooling_device1
[    1.619362] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.637109] ACPI: LNXTHERM:01 is registered as thermal_zone0
[    1.637708] ACPI: Thermal Zone [THRM] (40 C)
[    1.698695] device-mapper: uevent: version 1.0.3
[    1.698770] device-mapper: ioctl: 4.13.0-ioctl (2007-10-18) initialised: dm-devel@redhat.com
[    1.715451] md: linear personality registered for level -1
[    1.720178] md: multipath personality registered for level -4
[    1.724747] md: raid0 personality registered for level 0
[    1.729910] md: raid1 personality registered for level 1
[    1.734458] xor: automatically using best checksumming function: pIII_sse
[    1.752112]    pIII_sse  :  6355.000 MB/sec
[    1.752114] xor: using function: pIII_sse (6355.000 MB/sec)
[    1.752667] async_tx: api initialized (async)
[    1.820178] raid6: int32x1    968 MB/s
[    1.888128] raid6: int32x2    925 MB/s
[    1.956155] raid6: int32x4    777 MB/s
[    2.024205] raid6: int32x8    572 MB/s
[    2.092158] raid6: mmxx1     1609 MB/s
[    2.160145] raid6: mmxx2     2977 MB/s
[    2.228168] raid6: sse1x1    1497 MB/s
[    2.296156] raid6: sse1x2    2524 MB/s
[    2.364152] raid6: sse2x1    2592 MB/s
[    2.432165] raid6: sse2x2    3306 MB/s
[    2.432167] raid6: using algorithm sse2x2 (3306 MB/s)
[    2.432170] md: raid6 personality registered for level 6
[    2.432171] md: raid5 personality registered for level 5
[    2.432173] md: raid4 personality registered for level 4
[    2.462346] md: raid10 personality registered for level 10
[    3.457578] No dock devices found.
[    3.472720] SCSI subsystem initialized
[    3.512317] usbcore: registered new interface driver usbfs
[    3.512337] usbcore: registered new interface driver hub
[    3.524266] libata version 3.00 loaded.
[    3.527829] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[    3.527870] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[    3.527888] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    3.527908] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[    3.530504] sata_sil 0000:00:12.0: version 2.3
[    3.530529] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[    3.546314] usbcore: registered new device driver usb
[    3.552332] Uniform Multi-Platform E-IDE driver
[    3.553206] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.554439] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.561785] scsi0 : sata_sil
[    3.573409] scsi1 : sata_sil
[    3.573574] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    3.573578] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    3.604314] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.070445] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.128828] ata1.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    4.128828] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.201418] ata1.00: configured for UDMA/100
[    4.540360] ata2: SATA link down (SStatus 0 SControl 310)
[    4.540360] scsi 0:0:0:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5
[    4.540360] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[    4.540360] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.540360] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    4.540360] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    4.605135] usb usb1: configuration #1 chosen from 1 choice
[    4.605159] hub 1-0:1.0: USB hub found
[    4.605170] hub 1-0:1.0: 4 ports detected
[    4.718027] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[    4.718027] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.718027] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.718027] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    4.731874] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.731874] usb usb2: configuration #1 chosen from 1 choice
[    4.731874] hub 2-0:1.0: USB hub found
[    4.731874] hub 2-0:1.0: 8 ports detected
[    4.841208] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
[    4.841208] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.841208] ATIIXP: not 100% native mode: will probe irqs later
[    4.841208]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:PIO, hdb:PIO
[    4.841208]     ide1: BM-DMA at 0xf908-0xf90f, BIOS settings: hdc:PIO, hdd:PIO
[    4.841208] Probing IDE interface ide0...
[    5.146974] hda: SAMSUNG SP1604N/R, ATA DISK drive
[    5.326811] hub 2-0:1.0: unable to enumerate USB device on port 1
[    5.522662] hub 2-0:1.0: unable to enumerate USB device on port 2
[    5.723803] hub 2-0:1.0: unable to enumerate USB device on port 5
[    5.877240] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    5.877240] hda: UDMA/100 mode selected
[    5.877240] Probing IDE interface ide1...
[    5.985530] hub 2-0:1.0: unable to enumerate USB device on port 7
[    6.310459] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    6.555263] usb 1-1: configuration #1 chosen from 1 choice
[    6.673462] hdc: TSSTcorpCD/DVDW TS-H552L, ATAPI CD/DVD-ROM drive
[    6.884537] usb 1-3: new low speed USB device using ohci_hcd and address 3
[    7.113600] usb 1-3: configuration #1 chosen from 1 choice
[    7.407897] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    7.408419] hdc: UDMA/33 mode selected
[    7.408993] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.414435] ide1 at 0x170-0x177,0x376 on irq 15
[    7.449472] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    7.449472] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    7.450474] 8139too Fast Ethernet driver 0.9.28
[    7.450522] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[    7.451659] eth0: RealTek RTL8139 at 0xdc00, 00:17:31:35:c0:0f, IRQ 21
[    7.451662] eth0:  Identified 8139 chip type 'RTL-8101'
[    7.451979] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 20 (level, low) -> IRQ 20
[    7.504771] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.510176] usb 1-4: new full speed USB device using ohci_hcd and address 4
[    7.513041] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[    7.513059] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    7.513092] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    7.513111] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    7.519985] Driver 'sd' needs updating - please use bus_type methods
[    7.520074] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    7.520086] sd 0:0:0:0: [sda] Write Protect is off
[    7.520088] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.520101] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.520149] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    7.520156] sd 0:0:0:0: [sda] Write Protect is off
[    7.520158] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.520169] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.520173]  sda: sda1
[    7.537755] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.541790] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.574537] usb usb3: configuration #1 chosen from 1 choice
[    7.574561] hub 3-0:1.0: USB hub found
[    7.574573] hub 3-0:1.0: 4 ports detected
[    7.710346] hda: max request size: 512KiB
[    7.710652] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63
[    7.711058] hda: cache flushes supported
[    7.711103]  hda: hda1 hda2 hda3
[    7.735303] usb 1-4: configuration #1 chosen from 1 choice
[    7.755348] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[    7.755356] Uniform CD-ROM driver Revision: 3.20
[    7.933327] hub 2-0:1.0: unable to enumerate USB device on port 2
[    8.288344] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    8.525125] usb 3-1: configuration #1 chosen from 1 choice
[    8.526360] usbcore: registered new interface driver libusual
[    8.530485] Initializing USB Mass Storage driver...
[    8.532110] scsi2 : SCSI emulation for USB Mass Storage devices
[    8.537213] usbcore: registered new interface driver hiddev
[    8.537252] usbcore: registered new interface driver usb-storage
[    8.537255] USB Mass Storage support registered.
[    8.537353] usb-storage: device found at 4
[    8.537355] usb-storage: waiting for device to settle before scanning
[    8.549899] input:   USB Keyboard as /class/input/input1
[    8.549899] input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:13.0-1
[    8.580219] input:   USB Keyboard as /class/input/input2
[    8.580453] input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:13.0-1
[    8.599534] input: Cyp Se WitheHome as /class/input/input3
[    8.599766] input,hidraw2: USB HID v1.00 Keyboard [Cyp Se WitheHome] on usb-0000:00:13.0-3
[    8.607476] input: USB OpticalWheel Mouse as /class/input/input4
[    8.607476] input,hidraw3: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:13.1-1
[    8.607476] usbcore: registered new interface driver usbhid
[    8.607476] /build/buildd/linux-ports-2.6.25/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    8.742603] kjournald starting.  Commit interval 5 seconds
[    8.742618] EXT3-fs: mounted filesystem with ordered data mode.
[    8.959098] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000a6072b]
[   14.881254] usb-storage: device scan complete
[   14.889454] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   14.898019] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   14.911588] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   14.920336] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   14.934496] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   14.934521] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   14.948413] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   14.948413] sd 2:0:0:1: Attached scsi generic sg2 type 0
[   14.962342] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   14.962368] sd 2:0:0:2: Attached scsi generic sg3 type 0
[   14.977123] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   14.977123] sd 2:0:0:3: Attached scsi generic sg4 type 0
[   16.633258] udevd version 124 started
[   18.423839] Linux agpgart interface v0.103
[   18.453437] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.458506] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.637455] input: Power Button (FF) as /class/input/input5
[   18.665472] ACPI: Power Button (FF) [PWRF]
[   18.665535] input: Power Button (CM) as /class/input/input6
[   18.697483] ACPI: Power Button (CM) [PWRB]
[   19.688961] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   20.343643] input: PC Speaker as /class/input/input7
[   20.763965] parport_pc 00:07: reported by Plug and Play ACPI
[   20.764011] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   20.867523] lp0: using parport0 (interrupt-driven).
[   20.924492] Driver 'sr' needs updating - please use bus_type methods
[   21.206256] Adding 2048276k swap on /dev/hda3.  Priority:-1 extents:1 across:2048276k
[   21.852185] EXT3 FS on hda2, internal journal
[   25.206336] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.262980] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   26.709389] NET: Registered protocol family 17
[   27.049796] NET: Registered protocol family 10
[   27.050125] lo: Disabled Privacy Extensions
[   32.553450] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   32.881838] powernow-k8: Found 1 AMD Sempron(tm) Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   32.881868] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[   32.881870] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8
[   32.881872] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   33.886340] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   34.040818] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.040818] apm: overridden by ACPI.
[   34.446502] ppdev: user-space parallel port driver
[   35.209596] Marking TSC unstable due to: cpufreq changes.
[   35.562938] Clocksource tsc unstable (delta = -151463186 ns)
[   37.087163] Bluetooth: Core ver 2.11
[   37.088234] NET: Registered protocol family 31
[   37.088240] Bluetooth: HCI device and connection manager initialized
[   37.088245] Bluetooth: HCI socket layer initialized
[   37.133042] Bluetooth: L2CAP ver 2.9
[   37.133052] Bluetooth: L2CAP socket layer initialized
[   37.167934] Bluetooth: RFCOMM socket layer initialized
[   37.169116] Bluetooth: RFCOMM TTY layer initialized
[   37.169124] Bluetooth: RFCOMM ver 1.8
[   37.189223] Bluetooth: SCO (Voice Link) ver 0.5
[   37.189231] Bluetooth: SCO socket layer initialized
[   37.216188] Bluetooth: BNEP (Ethernet Emulation) ver 1.2
[   37.216195] Bluetooth: BNEP filters: protocol multicast
[   37.235455] Bridge firewalling registered
[   37.236581] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   39.972574] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   40.311953] [drm] Initialized drm 1.1.0 20060810
[   40.338382] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   40.780602] [drm] Setting GART location based on new memory map
[   40.782865] [drm] Loading R300 Microcode
[   40.782899] [drm] writeback test succeeded in 1 usecs
[  156.585638] ppdev0: registered pardevice
[  156.639600] ppdev0: unregistered pardevice
[  156.734633] ppdev0: registered pardevice
[  156.786636] ppdev0: unregistered pardevice
[  157.585396] ppdev0: registered pardevice
[  157.638219] ppdev0: unregistered pardevice

```


Checked "aplay"

```
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

aplay: main:583: audio open error: Connection refused

```

Some how pulseaudio killed itself and

```
aplay: device_list:215: no soundcards found...
```


Now I really don't care how good pulseaudio is or how crappy it is or whatever.
It's got bugs and Ubuntu doesn't support it properly
What I'd really like is my old 6.06 -> 8.04 audio back for another few years, and I don't care if I can't "upgrade" anymore anyways, can I have the good ole days back or do I have to put up with this noob crap or install Knoppix? lol

Solution: I'll just use Windows until the linux desktop is perfect.

---

### Post by AlexTepes on 2009-03-16
Anyways, sorry about my Windows statement was just tired and frustrated at the time, but I don't take it back because I did end up installing it lol.
And guess what? No audio problems, Windows doesn't ask me to install a graphics driver that doesn't work.


Now this is my **final** say, as long as **ANY** distro uses PulseAudio I will _NOT_ use it.
Change it back to the way it use to work!
PulseAudio is more like "server" type audio system not a desktop audio system, people who want this bulky crap should install it themselves.
I want a desktop not this server crap.
I don't wanna send my audio to someone in Japan, I don't wanna share it with other computers, it's like making a choice for _EVERYBODY_, You wouldn't like it if I discontinued Ubuntu and that was MY CHOICE for EVERYBODY, wheres the Humanity Ubuntu? Humanity has Sound. >_>

---

### Post by markbuntu on 2009-03-16
Well, your problem has nothing to do with pulseaudio but with the ALSA driver. Pulseaudio cannot connect to a non-existent alsa driver.

You probably need to add one of these options to the /etc/modprobe.d/alsa-base file according to /user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz which is a file on your computer.

```

Module snd-atiixp
  -----------------

    Module for ATI IXP 150/200/250/400 AC97 controllers.

    ac97_clock		- AC'97 clock (default = 48000)
    ac97_quirk		- AC'97 workaround for strange hardware
			  See "AC97 Quirk Option" section below.
    ac97_codec		- Workaround to specify which AC'97 codec 
			  instead of probing.  If this works for you
			  file a bug with your `lspci -vn` output.
			  -2  -- Force probing.
			  -1  -- Default behavior.
			  0-2 -- Use the specified codec.
    spdif_aclink	- S/PDIF transfer over AC-link (default = 1)

    This module supports one card and autoprobe.

    ATI IXP has two different methods to control SPDIF output.  One is
    over AC-link and another is over the "direct" SPDIF output.  The
    implementation depends on the motherboard, and you'll need to
    choose the correct one via spdif_aclink module option.

    The power-management is supported.

```

If you want some more help with that go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


If you want a distro without pulseaudio you could just use kubuntu, it comes without pulseaudio. So good luck getting anything other than a single sound hardware device working without pulseaudio. I have two sound cards, a usb headset, a usb webcam with a mic and a bluetooth headset. It would be impossible to get all these things working at the same time without pulseaudio, I know, I tried.

---

### Post by bigrob301 on 2009-10-24
try disabling the modem in bios I believe it's trying to use the sound card at the same time

---

### Post by Dinoyc on 2009-12-28
[COLOR=#000000][FONT=Verdana]Hi All,

Even i am facing the same problem with my Acer 5100 series laptop where it has the below configuration

AMD turion 64 mobile technology
MK36 (2.0 Ghz,512k L2 cache)
15.4" widescreen WXGA wide Crystal brite TFT LCD
ATI Radeon Xpress 1100 Graphics Card
60GB PATA HDD
DVD-super Multi doule layer
(support DVD+R Doule Layer /DVD += RW)
512 MB RAM

I have installed Ubuntu 9.10 and i don't see any reason why we need to upgrade to 9.10 and degrade the kernel and XORG if that was the case then it would always be good to work on 8.10. I need to know if ubuntu is working with ATI to give us a legacy driver?
If yes then when is that day coming? is there a way we can mail the technical team of ubuntu to make them understand that issue?

Could someone suggest the best ATI graphics to upgrade to right now? which has a low budget and works in this configuration?[/FONT][/COLOR]

---

