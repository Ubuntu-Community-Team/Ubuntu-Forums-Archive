---
title: "Installed 12.04 today, Wireless doesn't connect"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by gary4gar on 2012-04-26
Today,
I have installed 12.04 & my wifi stopped working. Wireless gets detected as **RT2790** &  show available network but doesn't not connect to any wireless network(tried secured & unsecured) for some strange reason. 

here are my debug logs:
lspci -vv
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
	Subsystem: Giga-byte Technology Device 5000
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10) (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device d000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 43
	Region 0: Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ff00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fdc00000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at fe00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at fd00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at fc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at fb00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Device 5006
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Giga-byte Technology Device 5001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device b001
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f800 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device b002
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at f700 [size=8]
	Region 1: I/O ports at f600 [size=4]
	Region 2: I/O ports at f500 [size=8]
	Region 3: I/O ports at f400 [size=4]
	Region 4: I/O ports at f300 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: Giga-byte Technology GA-8I945PG-RH Mainboard
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
	Subsystem: ASUSTeK Computer Inc. Device 130f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 42
	Region 0: I/O ports at be00 [size=256]
	Region 2: Memory at fddff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fdde0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic-pae (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 (Ubuntu 3.2.0-23.36-generic-pae 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5e0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5e0000 - 000000007f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5e3000 - 000000007f5f0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5f0000 - 000000007f600000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. G31M-ES2L/G31M-S2L, BIOS F10 09/29/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f5e0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CAFFF write-protect
[    0.000000]   CB000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 07F600000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
[    0.000000] reg 2, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 3, base: 2038MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2038M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2038MB, range: 2MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f5230] f5230
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
[    0.000000] RAMDISK: 37279000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 36502000 - 37278052
[    0.000000] Move RAMDISK from 0000000037279000 - 0000000037fef051 to 36502000 - 37278051
[    0.000000] ACPI: RSDP 000f6c20 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 7f5e3040 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 7f5e30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 7f5e3180 040E8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 7f5e0000 00040
[    0.000000] ACPI: HPET 7f5e73c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7f5e7440 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 7f5e72c0 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 7f5e7ae0 003AB (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1145MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007f5e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f5e0
[    0.000000] On node 0 totalpages: 521583
[    0.000000] free_area_init_node: node 0, pgdat c186b480, node_mem_map f5512200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2292 pages used for memmap
[    0.000000]   HighMem zone: 291054 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7f600000 (gap: 7f600000:60a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7800000 s34240 r0 d23104 u524288
[    0.000000] pcpu-alloc: s34240 r0 d23104 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517507
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=ae55b340-4aa1-48e3-8367-89fc9fb00da7 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 8346880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f5e0)
[    0.000000] Memory: 2036620k/2086784k available (5825k kernel code, 49712k reserved, 2850k data, 740k init, 1173384k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
[    0.000000]       .data : 0xc15b04bc - 0xc1878d00   (2850 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b04bc   (5825 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2600.082 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5200.16 BogoMIPS (lpj=10400328)
[    0.008005] pid_max: default: 32768 minimum: 301
[    0.008031] Security Framework initialized
[    0.008047] AppArmor: AppArmor initialized
[    0.008048] Yama: becoming mindful.
[    0.008107] Mount-cache hash table entries: 512
[    0.008247] Initializing cgroup subsys cpuacct
[    0.008254] Initializing cgroup subsys memory
[    0.008262] Initializing cgroup subsys devices
[    0.008265] Initializing cgroup subsys freezer
[    0.008267] Initializing cgroup subsys blkio
[    0.008274] Initializing cgroup subsys perf_event
[    0.008302] CPU: Physical Processor ID: 0
[    0.008303] CPU: Processor Core ID: 0
[    0.008307] mce: CPU supports 6 MCE banks
[    0.008315] CPU0: Thermal monitoring enabled (TM2)
[    0.008318] using mwait in idle threads.
[    0.010684] ACPI: Core revision 20110623
[    0.013980] ftrace: allocating 26594 entries in 53 pages
[    0.016051] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016415] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058240] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f74f2000 soft=f74f4000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148039] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148078] Brought up 2 CPUs
[    0.148081] Total of 2 processors activated (10400.12 BogoMIPS).
[    0.149696] devtmpfs: initialized
[    0.149696] EVM: security.selinux
[    0.149696] EVM: security.SMACK64
[    0.149696] EVM: security.capability
[    0.149696] PM: Registering ACPI NVS region at 7f5e0000 (12288 bytes)
[    0.149696] print_constraints: dummy: 
[    0.149696] RTC time: 19:51:44, date: 04/26/12
[    0.149696] NET: Registered protocol family 16
[    0.149696] Trying to unpack rootfs image as initramfs...
[    0.149696] EISA bus registered
[    0.149696] ACPI: bus type pci registered
[    0.149696] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149696] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149696] PCI: Using MMCONFIG for extended config space
[    0.149696] PCI: Using configuration type 1 for base access
[    0.152810] bio: create slab <bio-0> at 0
[    0.152900] ACPI: Added _OSI(Module Device)
[    0.152903] ACPI: Added _OSI(Processor Device)
[    0.152905] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.152908] ACPI: Added _OSI(Processor Aggregator Device)
[    0.153787] ACPI: EC: Look up EC in DSDT
[    0.158077] ACPI: SSDT 7f5e74c0 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.158301] ACPI: Dynamic OEM Table Load:
[    0.158305] ACPI: SSDT   (null) 0026C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.158471] ACPI: SSDT 7f5e7980 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.158680] ACPI: Dynamic OEM Table Load:
[    0.158684] ACPI: SSDT   (null) 00152 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.158844] ACPI: Interpreter enabled
[    0.158863] ACPI: (supports S0 S3 S4 S5)
[    0.158885] ACPI: Using IOAPIC for interrupt routing
[    0.163024] ACPI: No dock devices found.
[    0.163027] HEST: Table not found.
[    0.163033] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.163092] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.163219] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.163223] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.163226] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.163229] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.163231] pci_root PNP0A03:00: host bridge window [mem 0x7f600000-0xfebfffff]
[    0.163249] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    0.163303] pci 0000:00:02.0: [8086:29c2] type 0 class 0x000300
[    0.163315] pci 0000:00:02.0: reg 10: [mem 0xfdf00000-0xfdf7ffff]
[    0.163322] pci 0000:00:02.0: reg 14: [io  0xff00-0xff07]
[    0.163329] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.163336] pci 0000:00:02.0: reg 1c: [mem 0xfdc00000-0xfdcfffff]
[    0.163409] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.163425] pci 0000:00:1b.0: reg 10: [mem 0xfdff8000-0xfdffbfff 64bit]
[    0.163497] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.163502] pci 0000:00:1b.0: PME# disabled
[    0.163523] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.163596] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.163600] pci 0000:00:1c.0: PME# disabled
[    0.163622] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.163698] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.163702] pci 0000:00:1c.1: PME# disabled
[    0.163727] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.163768] pci 0000:00:1d.0: reg 20: [io  0xfe00-0xfe1f]
[    0.163800] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.163842] pci 0000:00:1d.1: reg 20: [io  0xfd00-0xfd1f]
[    0.163874] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.163916] pci 0000:00:1d.2: reg 20: [io  0xfc00-0xfc1f]
[    0.163948] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.163989] pci 0000:00:1d.3: reg 20: [io  0xfb00-0xfb1f]
[    0.164043] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.164061] pci 0000:00:1d.7: reg 10: [mem 0xfdfff000-0xfdfff3ff]
[    0.164152] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.164217] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.164302] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.164306] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.164349] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.164362] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.164372] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.164382] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.164392] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.164401] pci 0000:00:1f.1: reg 20: [io  0xf800-0xf80f]
[    0.164438] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.164453] pci 0000:00:1f.2: reg 10: [io  0xf700-0xf707]
[    0.164463] pci 0000:00:1f.2: reg 14: [io  0xf600-0xf603]
[    0.164472] pci 0000:00:1f.2: reg 18: [io  0xf500-0xf507]
[    0.164480] pci 0000:00:1f.2: reg 1c: [io  0xf400-0xf403]
[    0.164489] pci 0000:00:1f.2: reg 20: [io  0xf300-0xf30f]
[    0.164526] pci 0000:00:1f.2: PME# supported from D3hot
[    0.164530] pci 0000:00:1f.2: PME# disabled
[    0.164545] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.164597] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.164691] pci 0000:01:00.0: [1814:0781] type 0 class 0x000280
[    0.164709] pci 0000:01:00.0: reg 10: [mem 0xfd9f0000-0xfd9fffff]
[    0.164827] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.164832] pci 0000:01:00.0: PME# disabled
[    0.172034] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.172039] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.172044] pci 0000:00:1c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.172051] pci 0000:00:1c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.172117] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.172136] pci 0000:02:00.0: reg 10: [io  0xbe00-0xbeff]
[    0.172166] pci 0000:02:00.0: reg 18: [mem 0xfddff000-0xfddfffff 64bit pref]
[    0.172186] pci 0000:02:00.0: reg 20: [mem 0xfdde0000-0xfddeffff 64bit pref]
[    0.172199] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.172270] pci 0000:02:00.0: supports D1 D2
[    0.172272] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172278] pci 0000:02:00.0: PME# disabled
[    0.180031] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.180037] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.180041] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.180048] pci 0000:00:1c.1:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.180117] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.180122] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.180126] pci 0000:00:1e.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.180132] pci 0000:00:1e.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.180135] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.180138] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.180141] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.180144] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.180147] pci 0000:00:1e.0:   bridge window [mem 0x7f600000-0xfebfffff] (subtractive decode)
[    0.180164] pci_bus 0000:00: on NUMA node 0
[    0.180171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180380] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.180428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.180485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.180600]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.180603]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.180605] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.189044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.189100] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.189154] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.189206] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.189258] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.189311] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.189365] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.189419] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.189558] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.189570] vgaarb: loaded
[    0.189572] vgaarb: bridge control possible 0000:00:02.0
[    0.189703] i2c-core: driver [aat2870] using legacy suspend method
[    0.189704] i2c-core: driver [aat2870] using legacy resume method
[    0.189796] SCSI subsystem initialized
[    0.189857] libata version 3.00 loaded.
[    0.189919] usbcore: registered new interface driver usbfs
[    0.189932] usbcore: registered new interface driver hub
[    0.189963] usbcore: registered new device driver usb
[    0.190066] PCI: Using ACPI for IRQ routing
[    0.196414] PCI: pci_cache_line_size set to 64 bytes
[    0.196492] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.196495] reserve RAM buffer: 000000007f5e0000 - 000000007fffffff 
[    0.196620] NetLabel: Initializing
[    0.196623] NetLabel:  domain hash size = 128
[    0.196624] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.196639] NetLabel:  unlabeled traffic allowed by default
[    0.196699] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.196708] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.196713] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.204076] Switching to clocksource hpet
[    0.213336] AppArmor: AppArmor Filesystem Enabled
[    0.213386] pnp: PnP ACPI init
[    0.213407] ACPI: bus type pnp registered
[    0.213511] pnp 00:00: [bus 00-ff]
[    0.213514] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.213517] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.213522] pnp 00:00: [io  0x0d00-0xffff window]
[    0.213524] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.213527] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.213530] pnp 00:00: [mem 0x7f600000-0xfebfffff window]
[    0.213595] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.213664] pnp 00:01: [io  0x0010-0x001f]
[    0.213666] pnp 00:01: [io  0x0022-0x003f]
[    0.213669] pnp 00:01: [io  0x0044-0x005f]
[    0.213671] pnp 00:01: [io  0x0062-0x0063]
[    0.213673] pnp 00:01: [io  0x0065-0x006f]
[    0.213675] pnp 00:01: [io  0x0074-0x007f]
[    0.213677] pnp 00:01: [io  0x0091-0x0093]
[    0.213679] pnp 00:01: [io  0x00a2-0x00bf]
[    0.213681] pnp 00:01: [io  0x00e0-0x00ef]
[    0.213684] pnp 00:01: [io  0x04d0-0x04d1]
[    0.213686] pnp 00:01: [io  0x0290-0x029f]
[    0.213688] pnp 00:01: [io  0x0800-0x087f]
[    0.213690] pnp 00:01: [io  0x0290-0x0294]
[    0.213692] pnp 00:01: [io  0x0880-0x088f]
[    0.213759] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.213763] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.213766] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.213768] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.213771] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.213775] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.213789] pnp 00:02: [dma 4]
[    0.213791] pnp 00:02: [io  0x0000-0x000f]
[    0.213793] pnp 00:02: [io  0x0080-0x0090]
[    0.213796] pnp 00:02: [io  0x0094-0x009f]
[    0.213798] pnp 00:02: [io  0x00c0-0x00df]
[    0.213833] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.213886] pnp 00:03: [irq 0 disabled]
[    0.213898] pnp 00:03: [irq 8]
[    0.213901] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.213937] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.213966] pnp 00:04: [io  0x0070-0x0073]
[    0.214005] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.214015] pnp 00:05: [io  0x0061]
[    0.214048] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.214058] pnp 00:06: [io  0x00f0-0x00ff]
[    0.214064] pnp 00:06: [irq 13]
[    0.214097] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.214419] pnp 00:07: [io  0x0400-0x04cf]
[    0.214474] system 00:07: [io  0x0400-0x04cf] has been reserved
[    0.214478] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214682] pnp 00:08: [mem 0xe0000000-0xefffffff]
[    0.214746] system 00:08: [mem 0xe0000000-0xefffffff] has been reserved
[    0.214750] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.214916] pnp 00:09: [mem 0x000cb400-0x000cbfff]
[    0.214918] pnp 00:09: [mem 0x000f0000-0x000f7fff]
[    0.214921] pnp 00:09: [mem 0x000f8000-0x000fbfff]
[    0.214923] pnp 00:09: [mem 0x000fc000-0x000fffff]
[    0.214926] pnp 00:09: [mem 0x7f5e0000-0x7f5fffff]
[    0.214928] pnp 00:09: [mem 0x00000000-0x0009ffff]
[    0.214931] pnp 00:09: [mem 0x00100000-0x7f5dffff]
[    0.214933] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.214935] pnp 00:09: [mem 0xfed13000-0xfed1dfff]
[    0.214937] pnp 00:09: [mem 0xfed20000-0xfed8ffff]
[    0.214940] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.214942] pnp 00:09: [mem 0xffb00000-0xffb7ffff]
[    0.214944] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.214947] pnp 00:09: [mem 0x000e0000-0x000effff]
[    0.215025] system 00:09: [mem 0x000cb400-0x000cbfff] has been reserved
[    0.215028] system 00:09: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.215031] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.215034] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.215037] system 00:09: [mem 0x7f5e0000-0x7f5fffff] could not be reserved
[    0.215041] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.215044] system 00:09: [mem 0x00100000-0x7f5dffff] could not be reserved
[    0.215047] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.215050] system 00:09: [mem 0xfed13000-0xfed1dfff] has been reserved
[    0.215053] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.215056] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.215059] system 00:09: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.215062] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
[    0.215065] system 00:09: [mem 0x000e0000-0x000effff] has been reserved
[    0.215069] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.215090] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.215137] pnp 00:0a: Plug and Play ACPI device, IDs INT0800 (active)
[    0.215144] pnp: PnP ACPI: found 11 devices
[    0.215145] ACPI: ACPI bus type pnp unregistered
[    0.215151] PnPBIOS: Disabled by ACPI PNP
[    0.251774] PCI: max bus depth: 1 pci_try_num: 2
[    0.251805] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.251810] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.251815] pci 0000:00:1c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.251820] pci 0000:00:1c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.251830] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdd00000-0xfdd0ffff pref]
[    0.251833] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.251836] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.251842] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.251846] pci 0000:00:1c.1:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.251853] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.251856] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.251861] pci 0000:00:1e.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.251866] pci 0000:00:1e.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.251893] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.251899] pci 0000:00:1c.0: setting latency timer to 64
[    0.251910] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.251914] pci 0000:00:1c.1: setting latency timer to 64
[    0.251921] pci 0000:00:1e.0: setting latency timer to 64
[    0.251925] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.251928] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.251930] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.251933] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.251935] pci_bus 0000:00: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.251938] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.251941] pci_bus 0000:01: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.251944] pci_bus 0000:01: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.251946] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.251949] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.251952] pci_bus 0000:02: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.251955] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.251957] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.251960] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.251963] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.251966] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.251968] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.251971] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.251973] pci_bus 0000:03: resource 8 [mem 0x7f600000-0xfebfffff]
[    0.252040] NET: Registered protocol family 2
[    0.252122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.252384] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.252859] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253108] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253110] TCP reno registered
[    0.253113] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.253124] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.253210] NET: Registered protocol family 1
[    0.253230] pci 0000:00:02.0: Boot video device
[    0.253260] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.253278] pci 0000:00:1d.0: PCI INT A disabled
[    0.253289] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.253305] pci 0000:00:1d.1: PCI INT B disabled
[    0.253317] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.253333] pci 0000:00:1d.2: PCI INT C disabled
[    0.253340] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.253356] pci 0000:00:1d.3: PCI INT D disabled
[    0.253365] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.253402] pci 0000:00:1d.7: PCI INT A disabled
[    0.253423] PCI: CLS 4 bytes, default 64
[    0.253797] audit: initializing netlink socket (disabled)
[    0.253808] type=2000 audit(1335469903.248:1): initialized
[    0.281605] highmem bounce pool size: 64 pages
[    0.281614] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.291208] VFS: Disk quotas dquot_6.5.2
[    0.291287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.291902] fuse init (API version 7.17)
[    0.292027] msgmni has been set to 1686
[    0.292364] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.292392] io scheduler noop registered
[    0.292394] io scheduler deadline registered
[    0.292402] io scheduler cfq registered (default)
[    0.292533] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.292577] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.292643] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.292680] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.292770] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.292797] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.292900] intel_idle: MWAIT substates: 0x22220
[    0.292902] intel_idle: does not run on family 6 model 23
[    0.292984] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.292989] ACPI: Power Button [PWRB]
[    0.293049] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.293052] ACPI: Power Button [PWRF]
[    0.294518] ERST: Table is not found!
[    0.294520] GHES: HEST is not enabled!
[    0.294601] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.294730] isapnp: Scanning for PnP cards...
[    0.471720] Freeing initrd memory: 13788k freed
[    0.647800] isapnp: No Plug & Play device found
[    0.696511] Linux agpgart interface v0.103
[    0.696613] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.696686] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.697388] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.697525] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.699252] brd: module loaded
[    0.700157] loop: module loaded
[    0.700342] ata_piix 0000:00:1f.1: version 2.13
[    0.700358] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.700393] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.700736] scsi0 : ata_piix
[    0.700827] scsi1 : ata_piix
[    0.701298] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    0.701301] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    0.701322] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.701327] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.701346] ata2: port disabled--ignoring
[    0.701360] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.701753] scsi2 : ata_piix
[    0.701829] scsi3 : ata_piix
[    0.702368] ata3: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.702371] ata4: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.702798] Fixed MDIO Bus: probed
[    0.702821] tun: Universal TUN/TAP device driver, 1.6
[    0.702823] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.702927] PPP generic driver version 2.4.2
[    0.703046] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.703065] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.703081] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.703085] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.703139] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.703155] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.707030] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    0.707046] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.720021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.720250] hub 1-0:1.0: USB hub found
[    0.720255] hub 1-0:1.0: 8 ports detected
[    0.720343] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.720357] uhci_hcd: USB Universal Host Controller Interface driver
[    0.720375] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.720384] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.720387] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.720435] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.720460] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    0.720595] hub 2-0:1.0: USB hub found
[    0.720599] hub 2-0:1.0: 2 ports detected
[    0.720668] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.720675] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.720678] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.720731] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.720753] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    0.720889] hub 3-0:1.0: USB hub found
[    0.720893] hub 3-0:1.0: 2 ports detected
[    0.720959] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.720966] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.720969] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.721016] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.721047] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    0.721181] hub 4-0:1.0: USB hub found
[    0.721185] hub 4-0:1.0: 2 ports detected
[    0.721253] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.721260] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.721263] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.721309] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.721340] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    0.721473] hub 5-0:1.0: USB hub found
[    0.721477] hub 5-0:1.0: 2 ports detected
[    0.721592] usbcore: registered new interface driver libusual
[    0.721647] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.722081] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.722091] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.722334] mousedev: PS/2 mouse device common for all mice
[    0.722510] rtc_cmos 00:04: RTC can wake from S4
[    0.722610] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.722636] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.722698] device-mapper: uevent: version 1.0.3
[    0.722776] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.722813] EISA: Probing bus 0 at eisa.0
[    0.722816] EISA: Cannot allocate resource for mainboard
[    0.722818] Cannot allocate resource for EISA slot 1
[    0.722820] Cannot allocate resource for EISA slot 2
[    0.722822] Cannot allocate resource for EISA slot 3
[    0.722824] Cannot allocate resource for EISA slot 4
[    0.722826] Cannot allocate resource for EISA slot 5
[    0.722828] Cannot allocate resource for EISA slot 6
[    0.722830] Cannot allocate resource for EISA slot 7
[    0.722832] Cannot allocate resource for EISA slot 8
[    0.722834] EISA: Detected 0 cards.
[    0.722844] cpufreq-nforce2: No nForce2 chipset.
[    0.722846] cpuidle: using governor ladder
[    0.722848] cpuidle: using governor menu
[    0.722850] EFI Variables Facility v0.08 2004-May-17
[    0.723138] TCP cubic registered
[    0.723271] NET: Registered protocol family 10
[    0.723879] NET: Registered protocol family 17
[    0.723894] Registering the dns_resolver key type
[    0.723915] Using IPI No-Shortcut mode
[    0.724035] PM: Hibernation image not present or could not be loaded.
[    0.724051] registered taskstats version 1
[    0.733946]   Magic number: 8:297:901
[    0.734035] rtc_cmos 00:04: setting system clock to 2012-04-26 19:51:44 UTC (1335469904)
[    0.735616] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.735620] EDD information not available.
[    0.872377] ata3.00: ATA-8: ST3500413AS, JC4B, max UDMA/133
[    0.872384] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.872394] ata3.01: ATAPI: HL-DT-ST DVDRAM GH24NS71, WN00, max UDMA/100
[    0.888377] ata3.00: configured for UDMA/133
[    0.904147] ata3.01: configured for UDMA/100
[    0.909760] scsi 2:0:0:0: Direct-Access     ATA      ST3500413AS      JC4B PQ: 0 ANSI: 5
[    0.909899] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.909938] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.909953] sd 2:0:0:0: [sda] Write Protect is off
[    0.909956] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.909980] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.912999] scsi 2:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH24NS71  WN00 PQ: 0 ANSI: 5
[    0.946898] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.946903] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.947072] sr 2:0:1:0: Attached scsi CD-ROM sr0
[    0.947137] sr 2:0:1:0: Attached scsi generic sg1 type 5
[    0.966996]  sda: sda1 sda2 < sda5 sda6 >
[    0.968299] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.968370] Freeing unused kernel memory: 740k freed
[    0.968638] Write protecting the kernel text: 5828k
[    0.968657] Write protecting the kernel read-only data: 2376k
[    0.968659] NX-protecting the kernel data: 4412k
[    0.985723] udevd[93]: starting version 175
[    1.039762] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.039785] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.039815] r8169 0000:02:00.0: setting latency timer to 64
[    1.039875] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.040641] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8416000, 00:24:1d:f6:32:e2, XID 1c4000c0 IRQ 42
[    1.040645] r8169 0000:02:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.216025] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    1.252023] Refined TSC clocksource calibration: 2599.999 MHz.
[    1.252032] Switching to clocksource tsc
[    1.369053] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    3.321051] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.399348] udevd[339]: starting version 175
[    3.500054] Adding 6141948k swap on /dev/sda5.  Priority:-1 extents:1 across:6141948k 
[    3.847744] type=1400 audit(1335469907.609:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
[    3.848226] type=1400 audit(1335469907.613:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
[    3.848491] type=1400 audit(1335469907.613:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
[    4.321591] lp: driver loaded but no devices found
[    4.451282] intel_rng: FWH not detected
[    4.525582] cfg80211: Calling CRDA to update world regulatory domain
[    4.575474] usbcore: registered new interface driver usbhid
[    4.575477] usbhid: USB HID core driver
[    4.618558] [drm] Initialized drm 1.1.0 20060810
[    4.976028] leds_ss4200: no LED devices found
[    5.221980] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2
[    5.222078] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.3-1/input0
[    5.254862] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input3
[    5.256271] logitech 0003:046D:C512.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.3-1/input1
[    5.362379] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.362385] i915 0000:00:02.0: setting latency timer to 64
[    5.378345] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    5.378353] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.378355] [drm] Driver supports precise vblank timestamp query.
[    5.378394] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.394880] [drm] initialized overlay support
[    5.409288] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.409298] rt2800pci 0000:01:00.0: setting latency timer to 64
[    5.424623] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.424627] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424630] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.424633] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424636] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.424639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424641] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.424644] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424647] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.424650] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424652] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.424655] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424658] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.424661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424663] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.424666] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424669] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.424672] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424674] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.424677] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424680] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.424683] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[    5.424685] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.424688] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[    5.424691] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.424694] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[    5.424696] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    5.424699] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[    5.471787] fbcon: inteldrmfb (fb0) is primary device
[    5.511656] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    5.512384] Registered led device: rt2800pci-phy0::radio
[    5.512407] Registered led device: rt2800pci-phy0::assoc
[    5.512429] Registered led device: rt2800pci-phy0::quality
[    5.523275] Console: switching to colour frame buffer device 240x67
[    5.531781] fb0: inteldrmfb frame buffer device
[    5.531784] drm: registered panic notifier
[    5.532255] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    5.532301] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.532366] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    5.532397] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    5.694813] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    5.694818] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694821] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    5.694824] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694827] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    5.694830] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694833] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    5.694836] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694838] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    5.694841] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694844] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    5.694846] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694849] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    5.694852] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694854] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    5.694857] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694860] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    5.694863] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694865] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    5.694868] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694871] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    5.694874] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694876] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    5.694879] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.694882] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    5.694885] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.694887] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    5.694890] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.694893] cfg80211: World regulatory domain updated:
[    5.694895] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.694898] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694901] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.694904] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.694907] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.694909] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.839293] hda_codec: ALC883: BIOS auto-probing.
[    5.846153] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    5.846379] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    5.846575] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    5.846771] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    5.846966] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    6.742037] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.704700] init: failsafe main process (655) killed by TERM signal
[    8.611358] ppdev: user-space parallel port driver
[    8.867985] Bluetooth: Core ver 2.16
[    8.868158] NET: Registered protocol family 31
[    8.868161] Bluetooth: HCI device and connection manager initialized
[    8.868164] Bluetooth: HCI socket layer initialized
[    8.868166] Bluetooth: L2CAP socket layer initialized
[    8.868172] Bluetooth: SCO socket layer initialized
[    8.869360] type=1400 audit(1335469912.633:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=726 comm="apparmor_parser"
[    8.869902] type=1400 audit(1335469912.633:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=726 comm="apparmor_parser"
[    8.879384] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.879387] Bluetooth: BNEP filters: protocol multicast
[    8.990432] Bluetooth: RFCOMM TTY layer initialized
[    8.990438] Bluetooth: RFCOMM socket layer initialized
[    8.990440] Bluetooth: RFCOMM ver 1.11
[   10.373218] type=1400 audit(1335469914.137:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[   10.373713] type=1400 audit(1335469914.137:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[   10.373986] type=1400 audit(1335469914.137:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[   10.376745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.377050] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.382818] r8169 0000:02:00.0: eth0: link down
[   10.382999] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.383320] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.399893] type=1400 audit(1335469914.161:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=770 comm="apparmor_parser"
[   10.466654] type=1400 audit(1335469914.229:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=777 comm="apparmor_parser"
[   10.467258] type=1400 audit(1335469914.229:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=777 comm="apparmor_parser"
[   10.471790] type=1400 audit(1335469914.233:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=778 comm="apparmor_parser"
[   10.472486] type=1400 audit(1335469914.237:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=778 comm="apparmor_parser"
[   10.813041] init: alsa-restore main process (814) terminated with status 99
[   36.626240] audit_printk_skb: 27 callbacks suppressed
[   36.626245] type=1400 audit(1335469940.389:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1594 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   68.040170] wlan0: authenticate with 00:14:78:19:8f:da (try 1)
[   68.041544] wlan0: authenticated
[   68.056069] wlan0: associate with 00:14:78:19:8f:da (try 1)
[   68.057737] wlan0: deauthenticated from 00:14:78:19:8f:da (Reason: 6)
[  197.784490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  207.812147] wlan0: authenticate with 00:14:78:19:8f:da (try 1)
[  207.813561] wlan0: authenticated
[  207.828142] wlan0: associate with 00:14:78:19:8f:da (try 1)
[  207.829666] wlan0: deauthenticated from 00:14:78:19:8f:da (Reason: 6)
[  271.148245] wlan0: authenticate with 00:14:78:19:8f:da (try 1)
[  271.149599] wlan0: authenticated
[  271.149779] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  334.140512] wlan0: deauthenticating from 00:14:78:19:8f:da by local choice (reason=2)
[  334.148263] wlan0: authenticate with 00:14:78:19:8f:da (try 1)
[  334.149624] wlan0: authenticated
[  334.149843] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  397.136541] wlan0: deauthenticating from 00:14:78:19:8f:da by local choice (reason=2)
[  399.272147] wlan0: authenticate with 00:14:78:19:8f:da (try 1)
[  399.472028] wlan0: authenticate with 00:14:78:19:8f:da (try 2)
[  399.473423] wlan0: authenticated
[  399.473654] wlan0: failed to insert Dummy STA entry for the AP (error -17)
```

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
```



Now, I am also running Ubuntu 10.10 on this same machine, in that my wireless gets detected as RaLink **RT2860** chipset & works perfectly). I can connect to internet:)  

here is the lspci output from Ubuntu 10.10
```
01:00.0 Network controller: RaLink RT2860
	Subsystem: ASUSTeK Computer Inc. Device 130f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci
	Kernel modules: rt2860sta, rt2800pci
```



Interesting thing to notice here is: 
[SIZE="2"]the same card gets detected as two different chipsets(RT2790 vs RT2860)[/SIZE]:lolflag:


the Wireless card in question here is:
[Asus PCE-N10 Wireless PCI Express Adapter]("http://www.asus.com/Networks/Wireless_Adapters/PCEN10/"). And I think chipset in this card is RT2860(not RT2790). I further suspect this wrong detection in Ubuntu 12.04 is the reason that it doesn't connect. 

So,
Please let me know if my suspicion is correct? If yes, then what I need to do to fix this mess & get my wireless card working in Ubuntu 12.04

---

### Post by wildmanne39 on 2012-04-26
Hi please post the output of:
```
lspci -nnk | grep -iA2 net
rfkill list all
dmesg | grep rt2
lsmod
```
Thanks

---

### Post by gary4gar on 2012-04-26
Output is below
```

$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
    Subsystem: ASUSTeK Computer Inc. Device [1043:130f]
    Kernel driver in use: rt2800pci
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169


$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

$ dmesg | grep rt2
[    0.000000] KERNEL supported cpus:
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 7f600000 (gap: 7f600000:60a00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] virtual kernel memory layout:
[    0.008307] mce: CPU supports 6 MCE banks
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.158859] ACPI: (supports S0 S3 S4 S5)
[    0.163032] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.163495] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.163595] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.163695] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.164527] pci 0000:00:1f.2: PME# supported from D3hot
[    0.164829] pci 0000:01:00.0: PME# supported from D0 D3hot
[    0.172272] pci 0000:02:00.0: supports D1 D2
[    0.172274] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.292545] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.292589] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.292655] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.292692] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.294613] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.696511] Linux agpgart interface v0.103
[    0.696613] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.696687] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.697389] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.697526] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.701343] ata2: port disabled--ignoring
[    0.707040] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    0.720021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.720254] hub 1-0:1.0: 8 ports detected
[    0.720598] hub 2-0:1.0: 2 ports detected
[    0.720890] hub 3-0:1.0: 2 ports detected
[    0.721181] hub 4-0:1.0: 2 ports detected
[    0.721474] hub 5-0:1.0: 2 ports detected
[    0.721644] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.722065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.722076] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.722500] rtc_cmos 00:04: RTC can wake from S4
[    0.722600] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.722626] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.723906] Using IPI No-Shortcut mode
[    0.734001] rtc_cmos 00:04: setting system clock to 2012-04-27 02:29:32 UTC (1335493772)
[    0.909990] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.974195] udevd[93]: starting version 175
[    8.800346] udevd[302]: starting version 175
[    8.954387] rt2800pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.954399] rt2800pci 0000:01:00.0: setting latency timer to 64
[    9.021651] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.021654] [drm] Driver supports precise vblank timestamp query.
[    9.038729] [drm] initialized overlay support
[    9.146154] Registered led device: rt2800pci-phy0::radio
[    9.146204] Registered led device: rt2800pci-phy0::assoc
[    9.146255] Registered led device: rt2800pci-phy0::quality
[    9.254068] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.316942] ppdev: user-space parallel port driver
[   10.430601] init: plymouth-stop pre-start process (1004) terminated with status 1
[  379.201844] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  521.885818] wlan0: failed to insert Dummy STA entry for the AP (error -17)


$lsmod
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
snd_hda_codec_realtek   174055  1 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
joydev                 17393  0 
ppdev                  12849  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
usbhid                 41906  1 hid_logitech
psmouse                72846  0 
snd_seq_midi_event     14475  1 snd_seq_midi
hid                    77367  2 hid_logitech,usbhid
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
serio_raw              13027  0 
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414603  3 
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
cfg80211              178679  2 rt2x00lib,mac80211
drm                   197692  4 i915,drm_kms_helper
eeprom_93cx6           12653  1 rt2800pci
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```

---

### Post by wildmanne39 on 2012-04-27
Hi, you can give this a try:
```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800pci
sudo modprobe rt2800pci nohwcrypt=1
sudo ifconfig wlan0 up
```
do not reboot and make sure to unplug wired connection.
Thanks

---

### Post by gary4gar on 2012-04-30
**[Update]**
I had reported this bug & found out that its broken in precise but works in latest kernel. so if anyone else if facing the similar issue. Temp workaround is to install a bleeding edge kernel
[https://bugs.launchpad.net/bugs/989473](https://bugs.launchpad.net/bugs/989473)

---

