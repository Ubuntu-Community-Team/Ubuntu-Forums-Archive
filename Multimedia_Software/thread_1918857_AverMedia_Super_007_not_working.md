---
title: "AverMedia Super 007 not working"
date: 2012-02-01
forum: Multimedia Software
---

### Post by adashiu on 2012-02-01
Hi guys !
I wanted to defintely switch to Ubuntu and discover his functions. Im totally green with Unix based OS so please be tolerant.

I installed TvTime, it does not work.
I tried with Me-Tv - it tells that there is no device available.

Could someone guide me step by step how to make it work ?

Thanks in advance
adashiu

---

### Post by adashiu on 2012-02-02
Maybe someone could help me with this 
[http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

How to make all the drivers and other stuff working ?

---

### Post by adashiu on 2012-02-02
I installed firmware and drivers from 
[http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007](http://linuxtv.org/wiki/index.php/AVerMedia_AVerTV_DVB-T_Super_007)

I have folowing output from lspci -vv :
```
04:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: Avermedia Technologies Inc Device f11d
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```

from dmesg :

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. P31-DS3L/P31-DS3L, BIOS F9b 12/31/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00f4fc0] f4fc0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365f6000 - 372f3000
[    0.000000] ACPI: RSDP 000f6990 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 7fee3040 00034 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 7fee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 7fee3180 03955 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: HPET 7fee6c40 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7fee6cc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 7fee6b40 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f55f6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294356 pages, LIFO batch:31
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
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:70100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5000000 s26240 r0 d22912 u1048576
[    0.000000] pcpu-alloc: s26240 r0 d22912 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519793
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=d663be64-a4fd-49a4-8480-9dd5771ea032 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8383744 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fee0)
[    0.000000] Memory: 2047100k/2096000k available (5329k kernel code, 48448k reserved, 2589k data, 696k init, 1186696k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f440a000 soft=f440c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2533.005 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5066.01 BogoMIPS (lpj=10132020)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004026] Security Framework initialized
[    0.004040] AppArmor: AppArmor initialized
[    0.004041] Yama: becoming mindful.
[    0.004089] Mount-cache hash table entries: 512
[    0.004203] Initializing cgroup subsys cpuacct
[    0.004208] Initializing cgroup subsys memory
[    0.004215] Initializing cgroup subsys devices
[    0.004217] Initializing cgroup subsys freezer
[    0.004219] Initializing cgroup subsys net_cls
[    0.004221] Initializing cgroup subsys blkio
[    0.004226] Initializing cgroup subsys perf_event
[    0.004253] CPU: Physical Processor ID: 0
[    0.004254] CPU: Processor Core ID: 0
[    0.004257] mce: CPU supports 6 MCE banks
[    0.004265] CPU0: Thermal monitoring enabled (TM2)
[    0.004268] using mwait in idle threads.
[    0.006049] ACPI: Core revision 20110413
[    0.012026] ftrace: allocating 24885 entries in 49 pages
[    0.016042] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016340] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057929] CPU0: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz stepping 06
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f44b2000 soft=f44b4000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148020] Brought up 2 CPUs
[    0.148022] Total of 2 processors activated (10132.66 BogoMIPS).
[    0.149123] devtmpfs: initialized
[    0.149123] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
[    0.149709] print_constraints: dummy: 
[    0.149731] Time: 14:23:07  Date: 02/02/12
[    0.149767] NET: Registered protocol family 16
[    0.149791] Trying to unpack rootfs image as initramfs...
[    0.149878] EISA bus registered
[    0.149884] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.149887] ACPI: bus type pci registered
[    0.149940] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149943] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.149944] PCI: Using MMCONFIG for extended config space
[    0.149946] PCI: Using configuration type 1 for base access
[    0.152283] bio: create slab <bio-0> at 0
[    0.152975] ACPI: EC: Look up EC in DSDT
[    0.156083] ACPI: Interpreter enabled
[    0.156093] ACPI: (supports S0 S3 S4 S5)
[    0.156111] ACPI: Using IOAPIC for interrupt routing
[    0.159565] ACPI: No dock devices found.
[    0.159568] HEST: Table not found.
[    0.159571] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.159619] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.159717] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.159720] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.159722] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.159724] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.159727] pci_root PNP0A03:00: host bridge window [mem 0x7ff00000-0xfebfffff] (ignored)
[    0.159736] pci 0000:00:00.0: [8086:29c0] type 0 class 0x000600
[    0.159775] pci 0000:00:01.0: [8086:29c1] type 1 class 0x000604
[    0.159804] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.159807] pci 0000:00:01.0: PME# disabled
[    0.159846] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.159860] pci 0000:00:1b.0: reg 10: [mem 0xfa100000-0xfa103fff 64bit]
[    0.159909] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.159913] pci 0000:00:1b.0: PME# disabled
[    0.159930] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.159980] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.159983] pci 0000:00:1c.0: PME# disabled
[    0.160021] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.160072] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.160076] pci 0000:00:1c.3: PME# disabled
[    0.160095] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.160132] pci 0000:00:1d.0: reg 20: [io  0xe300-0xe31f]
[    0.160158] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.160195] pci 0000:00:1d.1: reg 20: [io  0xe000-0xe01f]
[    0.160221] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.160257] pci 0000:00:1d.2: reg 20: [io  0xe100-0xe11f]
[    0.160283] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.160319] pci 0000:00:1d.3: reg 20: [io  0xe200-0xe21f]
[    0.160351] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.160367] pci 0000:00:1d.7: reg 10: [mem 0xfa104000-0xfa1043ff]
[    0.160438] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.160489] pci 0000:00:1f.0: [8086:27b8] type 0 class 0x000601
[    0.160565] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.160568] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.160601] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.160614] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.160621] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.160629] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.160636] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.160643] pci 0000:00:1f.2: reg 20: [io  0xf000-0xf00f]
[    0.160668] pci 0000:00:1f.2: PME# supported from D3hot
[    0.160672] pci 0000:00:1f.2: PME# disabled
[    0.160683] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.160731] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.160793] pci 0000:01:00.0: [10de:0622] type 0 class 0x000300
[    0.160802] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.160813] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.160823] pci 0000:01:00.0: reg 1c: [mem 0xf4000000-0xf5ffffff 64bit]
[    0.160831] pci 0000:01:00.0: reg 24: [io  0xb000-0xb07f]
[    0.160838] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.160874] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.160877] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.160880] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.160884] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.160920] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.160923] pci 0000:00:1c.0:   bridge window [io  0xa000-0xafff]
[    0.160927] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.160933] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.160989] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.161007] pci 0000:03:00.0: reg 10: [io  0xc000-0xc0ff]
[    0.161037] pci 0000:03:00.0: reg 18: [mem 0xf9000000-0xf9000fff 64bit]
[    0.161071] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.161115] pci 0000:03:00.0: supports D1 D2
[    0.161117] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.161122] pci 0000:03:00.0: PME# disabled
[    0.161149] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.161153] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.161156] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.161162] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.161192] pci 0000:04:01.0: [1131:7133] type 0 class 0x000480
[    0.161208] pci 0000:04:01.0: reg 10: [mem 0xfa000000-0xfa0007ff]
[    0.161270] pci 0000:04:01.0: supports D1 D2
[    0.161286] pci 0000:04:02.0: [10ec:8139] type 0 class 0x000200
[    0.161301] pci 0000:04:02.0: reg 10: [io  0xd000-0xd0ff]
[    0.161311] pci 0000:04:02.0: reg 14: [mem 0xfa001000-0xfa0010ff]
[    0.161366] pci 0000:04:02.0: supports D1 D2
[    0.161367] pci 0000:04:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.161372] pci 0000:04:02.0: PME# disabled
[    0.161411] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.161415] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.161418] pci 0000:00:1e.0:   bridge window [mem 0xfa000000-0xfa0fffff]
[    0.161424] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.161426] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.161428] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.161443] pci_bus 0000:00: on NUMA node 0
[    0.161446] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.161568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.161612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.161655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.161766]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.161769]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.161771] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.167980] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.168032] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.168076] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.168119] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.168161] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.168205] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.168248] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.168291] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.168384] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.168388] vgaarb: loaded
[    0.168390] vgaarb: bridge control possible 0000:01:00.0
[    0.168587] SCSI subsystem initialized
[    0.168639] libata version 3.00 loaded.
[    0.168680] usbcore: registered new interface driver usbfs
[    0.168690] usbcore: registered new interface driver hub
[    0.168714] usbcore: registered new device driver usb
[    0.168790] PCI: Using ACPI for IRQ routing
[    0.170078] PCI: pci_cache_line_size set to 64 bytes
[    0.170140] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.170142] reserve RAM buffer: 000000007fee0000 - 000000007fffffff 
[    0.170228] NetLabel: Initializing
[    0.170230] NetLabel:  domain hash size = 128
[    0.170231] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.170240] NetLabel:  unlabeled traffic allowed by default
[    0.170273] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.170277] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.170281] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.176109] Switching to clocksource hpet
[    0.179788] Switched to NOHz mode on CPU #0
[    0.179892] Switched to NOHz mode on CPU #1
[    0.182610] AppArmor: AppArmor Filesystem Enabled
[    0.182637] pnp: PnP ACPI init
[    0.182653] ACPI: bus type pnp registered
[    0.182737] pnp 00:00: [bus 00-3f]
[    0.182740] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.182742] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.182744] pnp 00:00: [io  0x0d00-0xffff window]
[    0.182746] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.182748] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.182750] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
[    0.182805] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.182859] pnp 00:01: [io  0x0010-0x001f]
[    0.182863] pnp 00:01: [io  0x0022-0x003f]
[    0.182865] pnp 00:01: [io  0x0044-0x005f]
[    0.182867] pnp 00:01: [io  0x0062-0x0063]
[    0.182869] pnp 00:01: [io  0x0065-0x006f]
[    0.182870] pnp 00:01: [io  0x0074-0x007f]
[    0.182872] pnp 00:01: [io  0x0091-0x0093]
[    0.182874] pnp 00:01: [io  0x00a2-0x00bf]
[    0.182875] pnp 00:01: [io  0x00e0-0x00ef]
[    0.182877] pnp 00:01: [io  0x04d0-0x04d1]
[    0.182879] pnp 00:01: [io  0x0290-0x029f]
[    0.182881] pnp 00:01: [io  0x0800-0x087f]
[    0.182883] pnp 00:01: [io  0x0290-0x0294]
[    0.182884] pnp 00:01: [io  0x0880-0x088f]
[    0.182941] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.182943] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.182946] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.182948] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.182951] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.182953] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.182965] pnp 00:02: [dma 4]
[    0.182967] pnp 00:02: [io  0x0000-0x000f]
[    0.182968] pnp 00:02: [io  0x0080-0x0090]
[    0.182970] pnp 00:02: [io  0x0094-0x009f]
[    0.182972] pnp 00:02: [io  0x00c0-0x00df]
[    0.182995] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.183039] pnp 00:03: [irq 0 disabled]
[    0.183048] pnp 00:03: [irq 8]
[    0.183050] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.183077] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.183101] pnp 00:04: [io  0x0070-0x0073]
[    0.183126] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.183134] pnp 00:05: [io  0x0061]
[    0.183161] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.183169] pnp 00:06: [io  0x00f0-0x00ff]
[    0.183174] pnp 00:06: [irq 13]
[    0.183199] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.183396] pnp 00:07: [io  0x03f8-0x03ff]
[    0.183401] pnp 00:07: [irq 4]
[    0.183453] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.183614] pnp 00:08: [io  0x0378-0x037f]
[    0.183618] pnp 00:08: [irq 7]
[    0.183660] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.183738] pnp 00:09: [io  0x0060]
[    0.183740] pnp 00:09: [io  0x0064]
[    0.183745] pnp 00:09: [irq 1]
[    0.183771] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.183799] pnp 00:0a: [io  0x0400-0x04bf]
[    0.183839] system 00:0a: [io  0x0400-0x04bf] has been reserved
[    0.183843] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.184028] pnp 00:0b: [mem 0xf0000000-0xf3ffffff]
[    0.184078] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.184081] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.184219] pnp 00:0c: [mem 0x000cdc00-0x000cffff]
[    0.184221] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
[    0.184223] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
[    0.184225] pnp 00:0c: [mem 0x000fc000-0x000fffff]
[    0.184227] pnp 00:0c: [mem 0x7fee0000-0x7fefffff]
[    0.184228] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.184230] pnp 00:0c: [mem 0x00100000-0x7fedffff]
[    0.184232] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.184234] pnp 00:0c: [mem 0xfed13000-0xfed1dfff]
[    0.184236] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
[    0.184238] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.184239] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
[    0.184241] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.184243] pnp 00:0c: [mem 0x000e0000-0x000effff]
[    0.184299] system 00:0c: [mem 0x000cdc00-0x000cffff] has been reserved
[    0.184302] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.184304] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.184306] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.184309] system 00:0c: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.184311] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.184314] system 00:0c: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.184316] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.184319] system 00:0c: [mem 0xfed13000-0xfed1dfff] has been reserved
[    0.184321] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.184323] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.184326] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.184328] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.184330] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.184333] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.184351] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
[    0.184394] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
[    0.184400] pnp: PnP ACPI: found 14 devices
[    0.184401] ACPI: ACPI bus type pnp unregistered
[    0.184405] PnPBIOS: Disabled by ACPI PNP
[    0.220319] PCI: max bus depth: 1 pci_try_num: 2
[    0.220358] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80000000-0x800fffff pref]
[    0.220362] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.220366] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.220369] pci 0000:01:00.0: BAR 6: assigned [mem 0xf7000000-0xf707ffff pref]
[    0.220371] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.220374] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.220377] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff]
[    0.220380] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.220384] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.220387] pci 0000:00:1c.0:   bridge window [io  0xa000-0xafff]
[    0.220391] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff]
[    0.220395] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.220401] pci 0000:03:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.220403] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.220406] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.220410] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.220414] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff pref]
[    0.220419] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.220422] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.220426] pci 0000:00:1e.0:   bridge window [mem 0xfa000000-0xfa0fffff]
[    0.220430] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.220450] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.220453] pci 0000:00:01.0: setting latency timer to 64
[    0.220460] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.220464] pci 0000:00:1c.0: setting latency timer to 64
[    0.220472] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.220476] pci 0000:00:1c.3: setting latency timer to 64
[    0.220482] pci 0000:00:1e.0: setting latency timer to 64
[    0.220485] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.220487] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.220489] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.220491] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf7ffffff]
[    0.220494] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.220496] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    0.220498] pci_bus 0000:02: resource 1 [mem 0x80200000-0x803fffff]
[    0.220500] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.220502] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.220504] pci_bus 0000:03: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.220506] pci_bus 0000:03: resource 2 [mem 0x80000000-0x801fffff pref]
[    0.220508] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.220510] pci_bus 0000:04: resource 1 [mem 0xfa000000-0xfa0fffff]
[    0.220513] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.220515] pci_bus 0000:04: resource 5 [mem 0x00000000-0xffffffff]
[    0.220557] NET: Registered protocol family 2
[    0.220627] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.220839] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.221249] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.221439] TCP: Hash tables configured (established 131072 bind 65536)
[    0.221441] TCP reno registered
[    0.221443] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.221451] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.221535] NET: Registered protocol family 1
[    0.221645] pci 0000:01:00.0: Boot video device
[    0.221654] PCI: CLS 32 bytes, default 64
[    0.221935] audit: initializing netlink socket (disabled)
[    0.221943] type=2000 audit(1328192587.216:1): initialized
[    0.242414] highmem bounce pool size: 64 pages
[    0.242419] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.249770] VFS: Disk quotas dquot_6.5.2
[    0.249834] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.250444] fuse init (API version 7.16)
[    0.250528] msgmni has been set to 1680
[    0.250809] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.250832] io scheduler noop registered
[    0.250834] io scheduler deadline registered
[    0.250846] io scheduler cfq registered (default)
[    0.250946] pcieport 0000:00:01.0: setting latency timer to 64
[    0.250974] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.251018] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.251051] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.251102] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.251135] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.251206] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.251227] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.251295] intel_idle: MWAIT substates: 0x22220
[    0.251297] intel_idle: does not run on family 6 model 23
[    0.251361] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.251365] ACPI: Power Button [PWRB]
[    0.251410] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.251413] ACPI: Power Button [PWRF]
[    0.251437] ACPI: acpi_idle registered with cpuidle
[    0.252615] ERST: Table is not found!
[    0.252664] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.273008] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.273059] isapnp: Scanning for PnP cards...
[    0.413037] Freeing initrd memory: 13300k freed
[    0.625853] isapnp: No Plug & Play device found
[    0.688523] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.688816] Linux agpgart interface v0.103
[    0.690041] brd: module loaded
[    0.690574] loop: module loaded
[    0.690699] ata_piix 0000:00:1f.2: version 2.13
[    0.690713] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.690718] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.690750] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.691019] scsi0 : ata_piix
[    0.691093] scsi1 : ata_piix
[    0.691547] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.691549] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.691866] Fixed MDIO Bus: probed
[    0.691889] PPP generic driver version 2.4.2
[    0.691920] tun: Universal TUN/TAP device driver, 1.6
[    0.691922] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.691989] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.692016] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.692026] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.692029] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.692059] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.692075] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.695948] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.695961] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa104000
[    0.708014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.708154] hub 1-0:1.0: USB hub found
[    0.708158] hub 1-0:1.0: 8 ports detected
[    0.708224] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.708235] uhci_hcd: USB Universal Host Controller Interface driver
[    0.708252] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.708257] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.708260] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.708291] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.708312] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    0.708413] hub 2-0:1.0: USB hub found
[    0.708416] hub 2-0:1.0: 2 ports detected
[    0.708470] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.708475] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.708477] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.708509] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.708537] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
[    0.708641] hub 3-0:1.0: USB hub found
[    0.708644] hub 3-0:1.0: 2 ports detected
[    0.708701] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.708706] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.708709] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.708739] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.708769] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e100
[    0.708868] hub 4-0:1.0: USB hub found
[    0.708871] hub 4-0:1.0: 2 ports detected
[    0.708923] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.708928] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.708930] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.708958] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.708986] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e200
[    0.709088] hub 5-0:1.0: USB hub found
[    0.709092] hub 5-0:1.0: 2 ports detected
[    0.709189] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.709190] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.709346] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.709424] mousedev: PS/2 mouse device common for all mice
[    0.709534] rtc_cmos 00:04: RTC can wake from S4
[    0.709619] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.709640] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.709715] device-mapper: uevent: version 1.0.3
[    0.709783] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.709809] EISA: Probing bus 0 at eisa.0
[    0.709832] EISA: Detected 0 cards.
[    0.709840] cpufreq-nforce2: No nForce2 chipset.
[    0.709842] cpuidle: using governor ladder
[    0.709843] cpuidle: using governor menu
[    0.709845] EFI Variables Facility v0.08 2004-May-17
[    0.710108] TCP cubic registered
[    0.710230] NET: Registered protocol family 10
[    0.710769] NET: Registered protocol family 17
[    0.710782] Registering the dns_resolver key type
[    0.710799] Using IPI No-Shortcut mode
[    0.710867] PM: Hibernation image not present or could not be loaded.
[    0.710877] registered taskstats version 1
[    0.719348]   Magic number: 0:431:383
[    0.719357] usb usb1: hash matches
[    0.719419] rtc_cmos 00:04: setting system clock to 2012-02-02 14:23:07 UTC (1328192587)
[    0.719436] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.719437] EDD information not available.
[    0.739387] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.852777] ata1.00: HPA detected: current 976771055, native 976773168
[    0.852783] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    0.852787] ata1.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.853352] ata2.00: HPA detected: current 156299375, native 156301488
[    0.853358] ata2.00: ATA-5: WDC WD800BB-00CAA1, 17.07W17, max UDMA/100
[    0.853361] ata2.00: 156299375 sectors, multi 16: LBA 
[    0.853367] ata2.00: limited to UDMA/33 due to 40-wire cable
[    0.868670] ata1.00: configured for UDMA/133
[    0.868800] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    0.868895] sd 0:0:0:0: [sda] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    0.868913] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.868940] sd 0:0:0:0: [sda] Write Protect is off
[    0.868943] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.868965] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.869313] ata2.00: configured for UDMA/33
[    0.869419] scsi 1:0:0:0: Direct-Access     ATA      WDC WD800BB-00CA 17.0 PQ: 0 ANSI: 5
[    0.869525] sd 1:0:0:0: [sdb] 156299375 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.869543] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.869568] sd 1:0:0:0: [sdb] Write Protect is off
[    0.869571] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.869601] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.882132]  sda: sda1 sda2
[    0.882335] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.904612]  sdb: sdb1 sdb2 < sdb5 >
[    0.904891] sd 1:0:0:0: [sdb] Attached SCSI disk
[    0.904925] Freeing unused kernel memory: 696k freed
[    0.905097] Write protecting the kernel text: 5332k
[    0.905138] Write protecting the kernel read-only data: 2188k
[    0.918542] udevd[84]: starting version 173
[    0.983779] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.983796] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.983833] r8169 0000:03:00.0: setting latency timer to 64
[    0.983898] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    0.990635] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.990654] 8139cp 0000:04:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.990970] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.990992] 8139too 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.998526] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf800e000, 00:1d:7d:94:ad:47, XID 18000000 IRQ 43
[    0.999684] 8139too 0000:04:02.0: eth1: RealTek RTL8139 at 0xd000, 00:02:44:6d:b8:aa, IRQ 18
[    1.220019] Refined TSC clocksource calibration: 2533.332 MHz.
[    1.220025] Switching to clocksource tsc
[    1.323334] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    1.384023] usb 4-2: new full speed USB device number 2 using uhci_hcd
[    1.788016] usb 5-1: new full speed USB device number 2 using uhci_hcd
[   19.548917] udevd[334]: starting version 173
[   19.657352] intel_rng: FWH not detected
[   19.659158] lp: driver loaded but no devices found
[   19.668651] leds_ss4200: no LED devices found
[   19.710319] Adding 2093052k swap on /dev/sdb5.  Priority:-1 extents:1 across:2093052k 
[   19.710466] type=1400 audit(1328192606.486:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=497 comm="apparmor_parser"
[   19.710845] type=1400 audit(1328192606.486:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=497 comm="apparmor_parser"
[   19.711078] type=1400 audit(1328192606.486:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=497 comm="apparmor_parser"
[   19.712381] type=1400 audit(1328192606.490:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=504 comm="apparmor_parser"
[   19.712748] type=1400 audit(1328192606.490:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=504 comm="apparmor_parser"
[   19.712978] type=1400 audit(1328192606.490:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=504 comm="apparmor_parser"
[   19.730600] Linux media interface: v0.10
[   19.738108] parport_pc 00:08: reported by Plug and Play ACPI
[   19.738152] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   19.794801] Linux video capture interface: v2.00
[   19.794804] WARNING: You are using an experimental version of the media stack.
[   19.794805]     As the driver is backported to an older kernel, it doesn't offer
[   19.794806]     enough quality for its usage in production.
[   19.794807]     Use it with care.
[   19.794807] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   19.794808]     59b30294e14fa6a370fdd2bc2921cca1f977ef16 Merge branch 'v4l_for_linus' into staging/for_v3.4
[   19.794809]     72565224609a23a60d10fcdf42f87a2fa8f7b16d [media] cxd2820r: sleep on DVB-T/T2 delivery system switch
[   19.794811]     46de20a78ae4b122b79fc02633e9a6c3d539ecad [media] anysee: fix CI init
[   19.795797] WARNING: You are using an experimental version of the media stack.
[   19.795799]     As the driver is backported to an older kernel, it doesn't offer
[   19.795800]     enough quality for its usage in production.
[   19.795800]     Use it with care.
[   19.795801] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   19.795802]     59b30294e14fa6a370fdd2bc2921cca1f977ef16 Merge branch 'v4l_for_linus' into staging/for_v3.4
[   19.795803]     72565224609a23a60d10fcdf42f87a2fa8f7b16d [media] cxd2820r: sleep on DVB-T/T2 delivery system switch
[   19.795805]     46de20a78ae4b122b79fc02633e9a6c3d539ecad [media] anysee: fix CI init
[   19.798710] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   19.798747] saa7134 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.798751] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 19, latency: 32, mmio: 0xfa000000
[   19.798757] saa7133[0]: subsystem: 1461:f11d, board: Avermedia PCI pure analog (M135A) [card=149,insmod option]
[   19.798768] saa7133[0]: board init: gpio is 40000
[   19.808585] IR NEC protocol handler initialized
[   19.814271] IR RC5(x) protocol handler initialized
[   19.822946] IR RC6 protocol handler initialized
[   19.832020] Registered IR keymap rc-avermedia-m135a
[   19.832095] input: saa7134 IR (Avermedia PCI pure  as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/rc/rc0/input3
[   19.832128] rc0: saa7134 IR (Avermedia PCI pure  as /devices/pci0000:00/0000:00:1e.0/0000:04:01.0/rc/rc0
[   19.832164] lp0: using parport0 (interrupt-driven).
[   19.841387] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.841430] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   19.841452] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.848480] ppdev: user-space parallel port driver
[   19.865630] IR JVC protocol handler initialized
[   19.866204] gspca_main: v2.14.0 registered
[   19.866469] gspca_main: STV06xx-2.14.0 probing 046d:0870
[   19.868302] IR Sony protocol handler initialized
[   19.868603] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input4
[   19.868683] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-1/input0
[   19.871953] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input5
[   19.872133] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-1/input1
[   19.875808] gspca_stv06xx: HDCS-1020 sensor detected
[   19.878204] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.3-1/input2
[   19.878720] usbcore: registered new interface driver usbhid
[   19.878722] usbhid: USB HID core driver
[   19.984019] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   19.984034] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.984048] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[   19.984061] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984075] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[   19.984088] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984101] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984118] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984127] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984135] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984143] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984152] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984160] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984168] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984177] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.984185] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.985395] i2c-core: driver [tuner] using legacy suspend method
[   19.985397] i2c-core: driver [tuner] using legacy resume method
[   20.002815] IR SANYO protocol handler initialized
[   20.153884] input: STV06xx as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/input/input6
[   20.153999] usbcore: registered new interface driver STV06xx
[   20.302555] input: MCE IR Keyboard/Mouse (saa7134) as /devices/virtual/input/input7
[   20.302635] IR MCE Keyboard/mouse protocol handler initialized
[   20.304444] lirc_dev: IR Remote Control driver registered, major 249 
[   20.304808] rc rc0: lirc_dev: driver ir-lirc-codec (saa7134) registered at minor = 0
[   20.304810] IR LIRC bridge handler initialized
[   20.328019] tuner 0-004b: Tuner -1 found with type(s) Radio TV.
[   20.408012] tda829x 0-004b: setting tuner address to 60
[   20.472010] tda829x 0-004b: type set to tda8290+75a
[   20.743776] nvidia: module license 'NVIDIA' taints kernel.
[   20.743780] Disabling lock debugging due to kernel taint
[   20.888023] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   21.033676] type=1400 audit(1328192607.810:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=822 comm="apparmor_parser"
[   21.035163] type=1400 audit(1328192607.810:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=821 comm="apparmor_parser"
[   21.035874] type=1400 audit(1328192607.810:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=822 comm="apparmor_parser"
[   21.036111] type=1400 audit(1328192607.814:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=822 comm="apparmor_parser"
[   21.215231] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.215238] nvidia 0000:01:00.0: setting latency timer to 64
[   21.215242] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.215703] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   21.323751] init: failsafe main process (787) killed by TERM signal
[   21.325647] init: apport pre-start process (876) terminated with status 1
[   21.331790] init: apport post-stop process (904) terminated with status 1
[   21.485030] Bluetooth: Core ver 2.16
[   21.485074] NET: Registered protocol family 31
[   21.485076] Bluetooth: HCI device and connection manager initialized
[   21.485078] Bluetooth: HCI socket layer initialized
[   21.485080] Bluetooth: L2CAP socket layer initialized
[   21.485663] Bluetooth: SCO socket layer initialized
[   21.489784] Bluetooth: RFCOMM TTY layer initialized
[   21.489792] Bluetooth: RFCOMM socket layer initialized
[   21.489794] Bluetooth: RFCOMM ver 1.11
[   21.491757] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.491760] Bluetooth: BNEP filters: protocol multicast
[   21.534241] r8169 0000:03:00.0: eth0: link down
[   21.534248] r8169 0000:03:00.0: eth0: link down
[   21.534396] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.600217] 8139too 0000:04:02.0: eth1: link down
[   21.600391] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.884229] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.420826] r8169 0000:03:00.0: eth0: link up
[   23.420999] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.852090] saa7133[0]: registered device video1 [v4l2]
[   23.852133] saa7133[0]: registered device vbi0
[   23.852159] saa7133[0]: registered device radio0
[   23.854343] saa7134 ALSA driver for DMA sound loaded
[   23.854369] saa7133[0]/alsa: saa7133[0] at 0xfa000000 irq 19 registered as card -2
[   25.594400] audit_printk_skb: 24 callbacks suppressed
[   25.594403] type=1400 audit(1328192612.370:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1147 comm="apparmor_parser"
[   25.594865] type=1400 audit(1328192612.370:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1147 comm="apparmor_parser"
[   25.611138] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   25.611140] vesafb: scrolling: redraw
[   25.611143] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   25.612411] vesafb: framebuffer at 0xf5000000, mapped to 0xf8280000, using 5120k, total 5120k
[   25.612570] Console: switching to colour frame buffer device 160x64
[   25.612599] fb0: VESA VGA frame buffer device
[   25.625396] init: plymouth-splash main process (1152) terminated with status 1
[   31.534857] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   33.632010] eth0: no IPv6 routers present
```

Do you have any ideas? PLEASE its crucial for me

---

