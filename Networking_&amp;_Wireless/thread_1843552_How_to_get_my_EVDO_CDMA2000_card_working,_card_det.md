---
title: "How to get my EVDO CDMA2000 card working, card detectable"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by eshant_engineer on 2011-09-13
Hi,

I have gone through ndiswrapper method, but didn't found driver to load. Now what I have tried is through network manager. I am attaching logs, please see what is wrong. 
PS: I know wvdial method but it bypass any layer due to which chat, gwibber and other services don't connect,

Thanks in advance..

dmesg:-
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e3e2e1bb-285e-40fb-901b-439b5c565826 ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000ca4e3000 (usable)
[    0.000000]  BIOS-e820: 00000000ca4e3000 - 00000000ca526000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ca526000 - 00000000ca791000 (usable)
[    0.000000]  BIOS-e820: 00000000ca791000 - 00000000ca967000 (reserved)
[    0.000000]  BIOS-e820: 00000000ca967000 - 00000000caba7000 (usable)
[    0.000000]  BIOS-e820: 00000000caba7000 - 00000000cad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000cad68000 - 00000000cafad000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafad000 - 00000000cafbb000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cafbb000 - 00000000cafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafe8000 - 00000000cb000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012fe00000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N5110/0HGG14, BIOS A07 07/18/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x12fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0CB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   6 base 12FE00000 mask FFFE00000 uncachable
[    0.000000]   7 base 130000000 mask FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cb800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcaba7 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fd220] fd220
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000caba7000
[    0.000000]  0000000000 - 00caa00000 page 2M
[    0.000000]  00caa00000 - 00caba7000 page 4k
[    0.000000] kernel direct mapping tables up to caba7000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000012fe00000
[    0.000000]  0100000000 - 012fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 12fe00000 @ caba1000-caba7000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02   DELL)
[    0.000000] ACPI: XSDT 00000000cafad080 0007C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cafb6c20 000F4 (v04   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cafad188 09A94 (v02   DELL     WN09 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cafe3f80 00040
[    0.000000] ACPI: APIC 00000000cafb6d18 00072 (v03   DELL     WN09 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000cafb6d90 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cafb6dd0 004B0 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: SLIC 00000000cafb7280 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000cafb73f8 00038 (v01   DELL     WN09 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT 00000000cafb7430 00780 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cafb7bb0 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cafb8548 00D80 (v01  SgRef   SgTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cafb92c8 014E9 (v01 OptRef  OptTabl 00001000 INTL 20091112)
[    0.000000] ACPI: OSFR 00000000cafba7b8 00086 (v01 DELL    M08     07DB0712 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000012fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000012fe00000
[    0.000000]   NODE_DATA [000000012fdfb000 - 000000012fdfffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012bc00000-ffff88012f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0012fe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000ca4e3
[    0.000000]     0: 0x000ca526 -> 0x000ca791
[    0.000000]     0: 0x000ca967 -> 0x000caba7
[    0.000000]     0: 0x00100000 -> 0x0012fe00
[    0.000000] On node 0 totalpages: 1024795
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3919 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 810438 pages, LIFO batch:31
[    0.000000]   Normal zone: 2681 pages used for memmap
[    0.000000]   Normal zone: 193415 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000ca4e3000 - 00000000ca526000
[    0.000000] PM: Registered nosave memory: 00000000ca791000 - 00000000ca967000
[    0.000000] PM: Registered nosave memory: 00000000caba7000 - 00000000cad68000
[    0.000000] PM: Registered nosave memory: 00000000cad68000 - 00000000cafad000
[    0.000000] PM: Registered nosave memory: 00000000cafad000 - 00000000cafbb000
[    0.000000] PM: Registered nosave memory: 00000000cafbb000 - 00000000cafe8000
[    0.000000] PM: Registered nosave memory: 00000000cafe8000 - 00000000cb000000
[    0.000000] PM: Registered nosave memory: 00000000cb000000 - 00000000cb800000
[    0.000000] PM: Registered nosave memory: 00000000cb800000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:28600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88001fc00000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1007772
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e3e2e1bb-285e-40fb-901b-439b5c565826 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3947004k/4978688k available (5940k kernel code, 879508k absent, 152176k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2294.912 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4589.82 BogoMIPS (lpj=22949120)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000040] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000443] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001517] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001957] Mount-cache hash table entries: 256
[    0.002054] Initializing cgroup subsys ns
[    0.002056] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.002059] Initializing cgroup subsys cpuacct
[    0.002062] Initializing cgroup subsys memory
[    0.002067] Initializing cgroup subsys devices
[    0.002069] Initializing cgroup subsys freezer
[    0.002071] Initializing cgroup subsys net_cls
[    0.002072] Initializing cgroup subsys blkio
[    0.002099] CPU: Physical Processor ID: 0
[    0.002100] CPU: Processor Core ID: 0
[    0.002106] mce: CPU supports 7 MCE banks
[    0.002117] CPU0: Thermal monitoring enabled (TM1)
[    0.002123] using mwait in idle threads.
[    0.004572] ACPI: Core revision 20110112
[    0.026762] ftrace: allocating 24314 entries in 96 pages
[    0.036516] Not enabling x2apic, Intr-remapping init failed.
[    0.036519] Setting APIC routing to flat
[    0.036872] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136835] CPU0: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz stepping 07
[    0.247825] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.247831] ... version:                3
[    0.247832] ... bit width:              48
[    0.247833] ... generic registers:      4
[    0.247834] ... value mask:             0000ffffffffffff
[    0.247835] ... max period:             000000007fffffff
[    0.247836] ... fixed-purpose events:   3
[    0.247838] ... event mask:             000000070000000f
[    0.248245] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.787599] Brought up 4 CPUs
[    0.787603] Total of 4 processors activated (18358.34 BogoMIPS).
[    0.789611] devtmpfs: initialized
[    0.790496] print_constraints: dummy: 
[    0.790522] Time:  9:36:02  Date: 09/14/11
[    0.790549] NET: Registered protocol family 16
[    0.790632] Trying to unpack rootfs image as initramfs...
[    0.790638] ACPI: bus type pci registered
[    0.790696] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.790699] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.806987] PCI: Using configuration type 1 for base access
[    0.807669] bio: create slab <bio-0> at 0
[    0.809451] ACPI: EC: Look up EC in DSDT
[    0.811244] ACPI: Executed 1 blocks of module-level executable AML code
[    0.816122] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.891071] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.892223] ACPI: SSDT 00000000cad51698 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.892653] ACPI: Dynamic OEM Table Load:
[    0.892656] ACPI: SSDT           (null) 0064F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.927746] ACPI: SSDT 00000000cad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.928215] ACPI: Dynamic OEM Table Load:
[    0.928218] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.987566] ACPI: SSDT 00000000cad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.987997] ACPI: Dynamic OEM Table Load:
[    0.987999] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.010049] Freeing initrd memory: 12828k freed
[    1.028072] ACPI: Interpreter enabled
[    1.028076] ACPI: (supports S0 S1 S3 S4 S5)
[    1.028103] ACPI: Using IOAPIC for interrupt routing
[    1.097644] ACPI: No dock devices found.
[    1.097646] HEST: Table not found.
[    1.097648] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.097963] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.098408] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.098410] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.098412] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.098415] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.098416] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.098418] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.098420] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.098422] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.098423] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.098425] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    1.098427] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.098439] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    1.098474] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    1.098499] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.098502] pci 0000:00:01.0: PME# disabled
[    1.098520] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    1.098531] pci 0000:00:02.0: reg 10: [mem 0xf6400000-0xf67fffff 64bit]
[    1.098537] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.098541] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    1.098592] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    1.098616] pci 0000:00:16.0: reg 10: [mem 0xf7b0a000-0xf7b0a00f 64bit]
[    1.098680] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.098684] pci 0000:00:16.0: PME# disabled
[    1.098718] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    1.098739] pci 0000:00:1a.0: reg 10: [mem 0xf7b08000-0xf7b083ff]
[    1.098814] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.098819] pci 0000:00:1a.0: PME# disabled
[    1.098844] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    1.098860] pci 0000:00:1b.0: reg 10: [mem 0xf7b00000-0xf7b03fff 64bit]
[    1.098916] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.098920] pci 0000:00:1b.0: PME# disabled
[    1.098941] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    1.099005] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.099009] pci 0000:00:1c.0: PME# disabled
[    1.099032] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    1.099096] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.099100] pci 0000:00:1c.1: PME# disabled
[    1.099125] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    1.099188] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.099193] pci 0000:00:1c.3: PME# disabled
[    1.099217] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
[    1.099281] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.099285] pci 0000:00:1c.4: PME# disabled
[    1.099311] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    1.099375] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    1.099379] pci 0000:00:1c.7: PME# disabled
[    1.099408] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    1.099429] pci 0000:00:1d.0: reg 10: [mem 0xf7b07000-0xf7b073ff]
[    1.099504] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.099509] pci 0000:00:1d.0: PME# disabled
[    1.099534] pci 0000:00:1f.0: [8086:1c4b] type 0 class 0x000601
[    1.099653] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    1.099672] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    1.099680] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    1.099689] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    1.099698] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    1.099706] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    1.099715] pci 0000:00:1f.2: reg 24: [mem 0xf7b06000-0xf7b067ff]
[    1.099748] pci 0000:00:1f.2: PME# supported from D3hot
[    1.099752] pci 0000:00:1f.2: PME# disabled
[    1.099770] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    1.099787] pci 0000:00:1f.3: reg 10: [mem 0xf7b05000-0xf7b050ff 64bit]
[    1.099809] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    1.099866] pci 0000:01:00.0: [10de:0df5] type 0 class 0x000300
[    1.099875] pci 0000:01:00.0: reg 10: [mem 0xf5000000-0xf5ffffff]
[    1.099884] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.099893] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    1.099899] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    1.099905] pci 0000:01:00.0: reg 30: [mem 0xf6000000-0xf607ffff pref]
[    1.099941] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    1.099949] pci 0000:01:00.1: reg 10: [mem 0xf6080000-0xf6083fff]
[    1.117389] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.117396] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    1.117403] pci 0000:00:01.0:   bridge window [mem 0xf5000000-0xf60fffff]
[    1.117413] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.117517] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    1.117522] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.117527] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.117533] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.117602] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    1.117622] pci 0000:05:00.0: reg 10: [io  0xd000-0xd0ff]
[    1.117658] pci 0000:05:00.0: reg 18: [mem 0xf3204000-0xf3204fff 64bit pref]
[    1.117680] pci 0000:05:00.0: reg 20: [mem 0xf3200000-0xf3203fff 64bit pref]
[    1.117742] pci 0000:05:00.0: supports D1 D2
[    1.117743] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.117749] pci 0000:05:00.0: PME# disabled
[    1.137381] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    1.137390] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    1.137400] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.137414] pci 0000:00:1c.1:   bridge window [mem 0xf3200000-0xf32fffff 64bit pref]
[    1.137663] pci 0000:09:00.0: [8086:008a] type 0 class 0x000280
[    1.137812] pci 0000:09:00.0: reg 10: [mem 0xf7a00000-0xf7a01fff 64bit]
[    1.138355] pci 0000:09:00.0: PME# supported from D0 D3hot D3cold
[    1.138390] pci 0000:09:00.0: PME# disabled
[    1.157492] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    1.157497] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
[    1.157501] pci 0000:00:1c.3:   bridge window [mem 0xf7a00000-0xf7afffff]
[    1.157508] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.157578] pci 0000:0b:00.0: [1033:0194] type 0 class 0x000c03
[    1.157605] pci 0000:0b:00.0: reg 10: [mem 0xf7900000-0xf7901fff 64bit]
[    1.157713] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    1.157719] pci 0000:0b:00.0: PME# disabled
[    1.177359] pci 0000:00:1c.4: PCI bridge to [bus 0b-0c]
[    1.177369] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    1.177379] pci 0000:00:1c.4:   bridge window [mem 0xf7900000-0xf79fffff]
[    1.177393] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.177491] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    1.177495] pci 0000:00:1c.7:   bridge window [io  0xb000-0xcfff]
[    1.177499] pci 0000:00:1c.7:   bridge window [mem 0xf6800000-0xf78fffff]
[    1.177506] pci 0000:00:1c.7:   bridge window [mem 0xf2100000-0xf31fffff 64bit pref]
[    1.177535] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.177672] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.177709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.177744] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.177777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.177817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    1.177849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.177976]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.178095]  pci0000:00: ACPI _OSC control (0x1d) granted
[    1.181909] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.181955] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.181999] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.182042] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.182086] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.182130] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.182173] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.182217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.182301] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.182309] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.182312] vgaarb: loaded
[    1.182446] SCSI subsystem initialized
[    1.182495] libata version 3.00 loaded.
[    1.182527] usbcore: registered new interface driver usbfs
[    1.182535] usbcore: registered new interface driver hub
[    1.182554] usbcore: registered new device driver usb
[    1.182751] wmi: Mapper loaded
[    1.182753] PCI: Using ACPI for IRQ routing
[    1.182755] PCI: pci_cache_line_size set to 64 bytes
[    1.182891] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
[    1.182893] reserve RAM buffer: 00000000ca4e3000 - 00000000cbffffff 
[    1.182896] reserve RAM buffer: 00000000ca791000 - 00000000cbffffff 
[    1.182898] reserve RAM buffer: 00000000caba7000 - 00000000cbffffff 
[    1.182901] reserve RAM buffer: 000000012fe00000 - 000000012fffffff 
[    1.182975] NetLabel: Initializing
[    1.182976] NetLabel:  domain hash size = 128
[    1.182977] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.182988] NetLabel:  unlabeled traffic allowed by default
[    1.183019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.183024] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.185039] Switching to clocksource hpet
[    1.187335] Switched to NOHz mode on CPU #0
[    1.187391] Switched to NOHz mode on CPU #3
[    1.187424] Switched to NOHz mode on CPU #1
[    1.187465] Switched to NOHz mode on CPU #2
[    1.190183] AppArmor: AppArmor Filesystem Enabled
[    1.190207] pnp: PnP ACPI init
[    1.190221] ACPI: bus type pnp registered
[    1.190479] pnp 00:00: [bus 00-3e]
[    1.190481] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.190483] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.190484] pnp 00:00: [io  0x0d00-0xffff window]
[    1.190486] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.190488] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.190490] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.190491] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.190493] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.190495] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.190496] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.190498] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.190500] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.190502] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.190503] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.190505] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.190507] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.190508] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.190510] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    1.190512] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.190584] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.190596] pnp 00:01: [io  0x0000-0x001f]
[    1.190597] pnp 00:01: [io  0x0081-0x0091]
[    1.190599] pnp 00:01: [io  0x0093-0x009f]
[    1.190600] pnp 00:01: [io  0x00c0-0x00df]
[    1.190602] pnp 00:01: [dma 4]
[    1.190622] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.190629] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.190647] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.190720] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.190739] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.190750] pnp 00:04: [io  0x002e-0x002f]
[    1.190751] pnp 00:04: [io  0x004e-0x004f]
[    1.190752] pnp 00:04: [io  0x0061]
[    1.190754] pnp 00:04: [io  0x0063]
[    1.190755] pnp 00:04: [io  0x0065]
[    1.190756] pnp 00:04: [io  0x0067]
[    1.190758] pnp 00:04: [io  0x0070]
[    1.190759] pnp 00:04: [io  0x0080]
[    1.190760] pnp 00:04: [io  0x0092]
[    1.190761] pnp 00:04: [io  0x00b2-0x00b3]
[    1.190763] pnp 00:04: [io  0x0680-0x069f]
[    1.190764] pnp 00:04: [io  0x1000-0x100f]
[    1.190766] pnp 00:04: [io  0xffff]
[    1.190769] pnp 00:04: [io  0xffff]
[    1.190770] pnp 00:04: [io  0x0400-0x0453]
[    1.190772] pnp 00:04: [io  0x0458-0x047f]
[    1.190773] pnp 00:04: [io  0x0500-0x057f]
[    1.190774] pnp 00:04: [io  0x164e-0x164f]
[    1.190822] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.190824] system 00:04: [io  0x1000-0x100f] has been reserved
[    1.190826] system 00:04: [io  0xffff] has been reserved
[    1.190828] system 00:04: [io  0xffff] has been reserved
[    1.190830] system 00:04: [io  0x0400-0x0453] has been reserved
[    1.190832] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.190833] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.190835] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.190838] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.190845] pnp 00:05: [io  0x0070-0x0077]
[    1.190854] pnp 00:05: [irq 8]
[    1.190872] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.190898] pnp 00:06: [io  0x0454-0x0457]
[    1.190931] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.190933] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.190940] pnp 00:07: [io  0x00f0-0x00ff]
[    1.190945] pnp 00:07: [irq 13]
[    1.190964] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.190979] pnp 00:08: [io  0x0010-0x001f]
[    1.190980] pnp 00:08: [io  0x0022-0x003f]
[    1.190981] pnp 00:08: [io  0x0044-0x005f]
[    1.190983] pnp 00:08: [io  0x0068-0x006f]
[    1.190984] pnp 00:08: [io  0x0072-0x007f]
[    1.190986] pnp 00:08: [io  0x0080]
[    1.190987] pnp 00:08: [io  0x0084-0x0086]
[    1.190988] pnp 00:08: [io  0x0088]
[    1.190990] pnp 00:08: [io  0x008c-0x008e]
[    1.190991] pnp 00:08: [io  0x0090-0x009f]
[    1.190992] pnp 00:08: [io  0x00a2-0x00bf]
[    1.190994] pnp 00:08: [io  0x00e0-0x00ef]
[    1.190995] pnp 00:08: [io  0x04d0-0x04d1]
[    1.190997] pnp 00:08: [mem 0xfe800000-0xfe802fff]
[    1.191038] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    1.191041] system 00:08: [mem 0xfe800000-0xfe802fff] has been reserved
[    1.191044] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.191059] pnp 00:09: [irq 12]
[    1.191080] pnp 00:09: Plug and Play ACPI device, IDs DLL04b0 SYN0600 SYN0002 PNP0f13 (active)
[    1.191092] pnp 00:0a: [io  0x0060]
[    1.191094] pnp 00:0a: [io  0x0064]
[    1.191095] pnp 00:0a: [io  0x0062]
[    1.191096] pnp 00:0a: [io  0x0066]
[    1.191101] pnp 00:0a: [irq 1]
[    1.191122] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.191322] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    1.191324] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    1.191325] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    1.191327] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    1.191328] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    1.191330] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    1.191331] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    1.191333] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    1.191334] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    1.191336] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    1.191337] pnp 00:0b: [mem 0xcfa00000-0xcfa00fff]
[    1.191390] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.191392] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.191394] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.191396] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.191398] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.191400] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.191402] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.191404] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.191406] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    1.191408] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.191411] system 00:0b: [mem 0xcfa00000-0xcfa00fff] has been reserved
[    1.191413] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.191546] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    1.191549] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    1.191603] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    1.191605] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    1.191608] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.191650] pnp: PnP ACPI: found 13 devices
[    1.191652] ACPI: ACPI bus type pnp unregistered
[    1.197446] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.197448] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    1.197451] pci 0000:00:01.0:   bridge window [mem 0xf5000000-0xf60fffff]
[    1.197454] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.197458] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    1.197459] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.197464] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.197468] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.197475] pci 0000:00:1c.1: PCI bridge to [bus 05-06]
[    1.197478] pci 0000:00:1c.1:   bridge window [io  0xd000-0xdfff]
[    1.197484] pci 0000:00:1c.1:   bridge window [mem disabled]
[    1.197487] pci 0000:00:1c.1:   bridge window [mem 0xf3200000-0xf32fffff 64bit pref]
[    1.197494] pci 0000:00:1c.3: PCI bridge to [bus 09-0a]
[    1.197496] pci 0000:00:1c.3:   bridge window [io  disabled]
[    1.197501] pci 0000:00:1c.3:   bridge window [mem 0xf7a00000-0xf7afffff]
[    1.197505] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    1.197512] pci 0000:00:1c.4: PCI bridge to [bus 0b-0c]
[    1.197513] pci 0000:00:1c.4:   bridge window [io  disabled]
[    1.197518] pci 0000:00:1c.4:   bridge window [mem 0xf7900000-0xf79fffff]
[    1.197523] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    1.197529] pci 0000:00:1c.7: PCI bridge to [bus 11-1f]
[    1.197533] pci 0000:00:1c.7:   bridge window [io  0xb000-0xcfff]
[    1.197538] pci 0000:00:1c.7:   bridge window [mem 0xf6800000-0xf78fffff]
[    1.197542] pci 0000:00:1c.7:   bridge window [mem 0xf2100000-0xf31fffff 64bit pref]
[    1.197559] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197562] pci 0000:00:01.0: setting latency timer to 64
[    1.197568] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197572] pci 0000:00:1c.0: setting latency timer to 64
[    1.197582] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.197586] pci 0000:00:1c.1: setting latency timer to 64
[    1.197596] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.197600] pci 0000:00:1c.3: setting latency timer to 64
[    1.197607] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197611] pci 0000:00:1c.4: setting latency timer to 64
[    1.197618] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.197622] pci 0000:00:1c.7: setting latency timer to 64
[    1.197626] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.197628] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.197630] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.197631] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.197633] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.197635] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.197637] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.197638] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.197640] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.197642] pci_bus 0000:00: resource 13 [mem 0xcfa00000-0xfeafffff]
[    1.197644] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    1.197646] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    1.197647] pci_bus 0000:01: resource 1 [mem 0xf5000000-0xf60fffff]
[    1.197649] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.197651] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    1.197653] pci_bus 0000:05: resource 2 [mem 0xf3200000-0xf32fffff 64bit pref]
[    1.197655] pci_bus 0000:09: resource 1 [mem 0xf7a00000-0xf7afffff]
[    1.197657] pci_bus 0000:0b: resource 1 [mem 0xf7900000-0xf79fffff]
[    1.197658] pci_bus 0000:11: resource 0 [io  0xb000-0xcfff]
[    1.197660] pci_bus 0000:11: resource 1 [mem 0xf6800000-0xf78fffff]
[    1.197662] pci_bus 0000:11: resource 2 [mem 0xf2100000-0xf31fffff 64bit pref]
[    1.197683] NET: Registered protocol family 2
[    1.197814] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.198710] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.200475] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.200695] TCP: Hash tables configured (established 524288 bind 65536)
[    1.200696] TCP reno registered
[    1.200705] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.200727] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.200806] NET: Registered protocol family 1
[    1.200820] pci 0000:00:02.0: Boot video device
[    1.445082] PCI: CLS 64 bytes, default 64
[    1.445085] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.445087] Placing 64MB software IO TLB between ffff88001bc00000 - ffff88001fc00000
[    1.445088] software IO TLB at phys 0x1bc00000 - 0x1fc00000
[    1.445483] audit: initializing netlink socket (disabled)
[    1.445490] type=2000 audit(1315992962.300:1): initialized
[    1.457517] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.458898] VFS: Disk quotas dquot_6.5.2
[    1.458940] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.459430] fuse init (API version 7.16)
[    1.459498] msgmni has been set to 7734
[    1.459682] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.459703] io scheduler noop registered
[    1.459705] io scheduler deadline registered
[    1.459735] io scheduler cfq registered (default)
[    1.459814] pcieport 0000:00:01.0: setting latency timer to 64
[    1.459839] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.459893] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.459935] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.460000] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.460040] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.460109] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.460150] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.460215] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.460256] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    1.460324] pcieport 0000:00:1c.7: setting latency timer to 64
[    1.460365] pcieport 0000:00:1c.7: irq 45 for MSI/MSI-X
[    1.460454] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.460456] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.460458] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    1.460460] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.460478] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.460483] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.460498] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.460500] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    1.460504] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    1.460520] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.460522] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
[    1.460526] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    1.460543] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    1.460545] pci 0000:0b:00.0: Signaling PME through PCIe PME interrupt
[    1.460549] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    1.460566] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
[    1.460570] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
[    1.460583] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.460620] pciehp 0000:00:1c.7:pcie04: HPC vendor_id 8086 device_id 1c1e ss_vid 1028 ss_did 4b0
[    1.460637] pciehp 0000:00:1c.7:pcie04: service driver pciehp loaded
[    1.460641] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.460675] intel_idle: MWAIT substates: 0x21120
[    1.460677] intel_idle: v0.4 model 0x2A
[    1.460678] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.460765] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.460802] ACPI: AC Adapter [AC] (on-line)
[    1.460892] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.624842] ACPI: Lid Switch [LID0]
[    1.624944] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.624953] ACPI: Power Button [PWRB]
[    1.624999] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.625002] ACPI: Sleep Button [SBTN]
[    1.625033] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.625035] ACPI: Power Button [PWRF]
[    1.625221] ACPI: acpi_idle yielding to intel_idle
[    1.633898] thermal LNXTHERM:00: registered as thermal_zone0
[    1.633901] ACPI: Thermal Zone [THM] (61 C)
[    1.633921] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.633959] ERST: Table is not found!
[    1.634007] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.725222] ACPI: Battery Slot [BAT0] (battery present)
[    1.796528] Linux agpgart interface v0.103
[    1.796603] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.796753] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.798009] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.798106] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.798927] brd: module loaded
[    1.799311] loop: module loaded
[    1.799378] i2c-core: driver [adp5520] using legacy suspend method
[    1.799379] i2c-core: driver [adp5520] using legacy resume method
[    1.799674] Fixed MDIO Bus: probed
[    1.799694] PPP generic driver version 2.4.2
[    1.799721] tun: Universal TUN/TAP device driver, 1.6
[    1.799722] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.799777] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.799793] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.799810] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.799813] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.799841] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.799899] ehci_hcd 0000:00:1a.0: debug port 2
[    1.803780] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.803798] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7b08000
[    1.824745] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.824923] hub 1-0:1.0: USB hub found
[    1.824927] hub 1-0:1.0: 2 ports detected
[    1.824986] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.824999] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.825002] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.825033] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.825079] ehci_hcd 0000:00:1d.0: debug port 2
[    1.828975] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.828988] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7b07000
[    1.844739] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.844901] hub 2-0:1.0: USB hub found
[    1.844904] hub 2-0:1.0: 2 ports detected
[    1.844951] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.844959] uhci_hcd: USB Universal Host Controller Interface driver
[    1.845043] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.847264] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.847269] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.847354] mousedev: PS/2 mouse device common for all mice
[    1.847485] rtc_cmos 00:05: RTC can wake from S4
[    1.847538] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.847567] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.847645] device-mapper: uevent: version 1.0.3
[    1.847700] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.847758] device-mapper: multipath: version 1.2.0 loaded
[    1.847760] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.847939] cpuidle: using governor ladder
[    1.848090] cpuidle: using governor menu
[    1.848267] TCP cubic registered
[    1.848357] NET: Registered protocol family 10
[    1.848701] NET: Registered protocol family 17
[    1.848711] Registering the dns_resolver key type
[    1.849619] PM: Hibernation image not present or could not be loaded.
[    1.849627] registered taskstats version 1
[    1.849906]   Magic number: 11:603:626
[    1.849926] pci 0000:00:1b.0: hash matches
[    1.849997] rtc_cmos 00:05: setting system clock to 2011-09-14 09:36:03 UTC (1315992963)
[    1.849999] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.850000] EDD information not available.
[    1.851245] Freeing unused kernel memory: 956k freed
[    1.851342] Write protecting the kernel read-only data: 10240k
[    1.851983] Freeing unused kernel memory: 184k freed
[    1.855442] Freeing unused kernel memory: 1444k freed
[    1.862475] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.869733] <30>udev[69]: starting version 167
[    1.892707] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.892747] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.892795] r8169 0000:05:00.0: setting latency timer to 64
[    1.892802] r8169 0000:05:00.0: (unregistered net_device): unknown MAC, using family default
[    1.892872] r8169 0000:05:00.0: irq 46 for MSI/MSI-X
[    1.893312] r8169 0000:05:00.0: eth0: RTL8101e at 0xffffc9000067a000, 18:03:73:72:b3:b8, XID 00a00000 IRQ 46
[    1.916514] ahci 0000:00:1f.2: version 3.0
[    1.916527] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.916570] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.916594] ahci: SSS flag set, parallel bus scan disabled
[    1.934935] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x31 impl SATA mode
[    1.934939] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.934946] ahci 0000:00:1f.2: setting latency timer to 64
[    1.975298] scsi0 : ahci
[    1.975406] scsi1 : ahci
[    1.975528] scsi2 : ahci
[    1.975659] scsi3 : ahci
[    1.975765] scsi4 : ahci
[    1.975873] scsi5 : ahci
[    1.976128] ata1: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06100 irq 47
[    1.976130] ata2: DUMMY
[    1.976131] ata3: DUMMY
[    1.976132] ata4: DUMMY
[    1.976134] ata5: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06300 irq 47
[    1.976137] ata6: SATA max UDMA/133 abar m2048@0xf7b06000 port 0xf7b06380 irq 47
[    2.144671] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.295244] hub 1-1:1.0: USB hub found
[    2.295343] hub 1-1:1.0: 6 ports detected
[    2.324574] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.327831] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.328262] ata1.00: ATA-8: WDC WD5000BPVT-75HXZT3, 01.01A01, max UDMA/133
[    2.328271] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.331636] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    2.332071] ata1.00: configured for UDMA/133
[    2.332306] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BPVT-7 01.0 PQ: 0 ANSI: 5
[    2.332455] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.332458] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.332460] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.332510] sd 0:0:0:0: [sda] Write Protect is off
[    2.332513] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.332579] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.414492] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.444498] Refined TSC clocksource calibration: 2294.786 MHz.
[    2.444508] Switching to clocksource tsc
[    2.480017]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 >
[    2.480565] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.565099] hub 2-1:1.0: USB hub found
[    2.565200] hub 2-1:1.0: 8 ports detected
[    2.644614] usb 1-1.4: new full speed USB device using ehci_hcd and address 3
[    2.834523] usb 1-1.5: new high speed USB device using ehci_hcd and address 4
[    3.074189] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.077302] ata5.00: ATAPI: PLDS DVD+/-RW DS-8A5SH, XD13, max UDMA/100
[    3.078591] ata5.00: configured for UDMA/100
[    3.085120] scsi 4:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A5SH XD13 PQ: 0 ANSI: 5
[    3.090484] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.090495] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.090697] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.090802] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.304268] usb 2-1.6: new high speed USB device using ehci_hcd and address 3
[    3.433919] ata6: SATA link down (SStatus 0 SControl 300)
[    3.435258] usbcore: registered new interface driver uas
[    3.440239] Initializing USB Mass Storage driver...
[    3.440395] scsi6 : usb-storage 2-1.6:1.0
[    3.440477] usbcore: registered new interface driver usb-storage
[    3.440479] USB Mass Storage support registered.
[    4.436534] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    4.436964] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    5.292446] sd 6:0:0:0: [sdb] 31512576 512-byte logical blocks: (16.1 GB/15.0 GiB)
[    5.293393] sd 6:0:0:0: [sdb] Write Protect is off
[    5.293403] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    5.294807] sd 6:0:0:0: [sdb] No Caching mode page present
[    5.294815] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    5.298175] sd 6:0:0:0: [sdb] No Caching mode page present
[    5.298181] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    5.299329]  sdb: sdb1
[    5.303304] sd 6:0:0:0: [sdb] No Caching mode page present
[    5.303320] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    5.303327] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    5.344105] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.639611] <30>udev[322]: starting version 167
[   10.746250] lp: driver loaded but no devices found
[   10.748798] xhci_hcd 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.748825] xhci_hcd 0000:0b:00.0: setting latency timer to 64
[   10.748829] xhci_hcd 0000:0b:00.0: xHCI Host Controller
[   10.755387] xhci_hcd 0000:0b:00.0: new USB bus registered, assigned bus number 3
[   10.760753] Linux video capture interface: v2.00
[   10.768091] type=1400 audit(1315973172.408:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=429 comm="apparmor_parser"
[   10.768909] type=1400 audit(1315973172.408:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=429 comm="apparmor_parser"
[   10.769427] type=1400 audit(1315973172.408:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=429 comm="apparmor_parser"
[   10.772906] cfg80211: Calling CRDA to update world regulatory domain
[   10.785662] [drm] Initialized drm 1.1.0 20060810
[   10.790380] xhci_hcd 0000:0b:00.0: irq 16, io mem 0xf7900000
[   10.790503] xhci_hcd 0000:0b:00.0: irq 48 for MSI/MSI-X
[   10.790509] xhci_hcd 0000:0b:00.0: irq 49 for MSI/MSI-X
[   10.790514] xhci_hcd 0000:0b:00.0: irq 50 for MSI/MSI-X
[   10.790519] xhci_hcd 0000:0b:00.0: irq 51 for MSI/MSI-X
[   10.790524] xhci_hcd 0000:0b:00.0: irq 52 for MSI/MSI-X
[   10.793816] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   10.793932] xHCI xhci_add_endpoint called for root hub
[   10.793934] xHCI xhci_check_bandwidth called for root hub
[   10.793966] hub 3-0:1.0: USB hub found
[   10.793972] hub 3-0:1.0: 4 ports detected
[   10.799223] Adding 8191996k swap on /dev/sda6.  Priority:-1 extents:1 across:8191996k 
[   10.830858] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (1bcf:2881)
[   10.836380] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.856261] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input5
[   10.856331] usbcore: registered new interface driver uvcvideo
[   10.856334] USB Video Class driver (v1.0.0)
[   10.880065] usbcore: registered new interface driver usbserial
[   10.880088] USB Serial support registered for generic
[   10.880117] usbcore: registered new interface driver usbserial_generic
[   10.880119] usbserial: USB Serial Driver core
[   10.943698] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   10.949137] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.949142] i915 0000:00:02.0: setting latency timer to 64
[   10.968770] cfg80211: World regulatory domain updated:
[   10.968773] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.968775] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.968777] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.968778] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.968780] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.968781] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.989600] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.989604] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.989696] iwlagn 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.989705] iwlagn 0000:09:00.0: setting latency timer to 64
[   10.989774] iwlagn 0000:09:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[   10.998592] VGA switcheroo: detected DSM switching method \_SB_.PCI0.PEG0.PEGP handle
[   10.998637] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   10.998644] nouveau 0000:01:00.0: power state changed by ACPI to D0
[   10.998654] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[   10.998663] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.998676] nouveau 0000:01:00.0: setting latency timer to 64
[   11.005627] iwlagn 0000:09:00.0: device EEPROM VER=0x71a, CALIB=0x6
[   11.005630] iwlagn 0000:09:00.0: Device SKU: 0X9
[   11.005632] iwlagn 0000:09:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   11.005994] Bluetooth: Core ver 2.15
[   11.006016] NET: Registered protocol family 31
[   11.006017] Bluetooth: HCI device and connection manager initialized
[   11.006020] Bluetooth: HCI socket layer initialized
[   11.006332] iwlagn 0000:09:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   11.006419] iwlagn 0000:09:00.0: irq 53 for MSI/MSI-X
[   11.027848] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   11.027850] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   11.028261] i915 0000:00:02.0: irq 54 for MSI/MSI-X
[   11.028267] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.028269] [drm] Driver supports precise vblank timestamp query.
[   11.028926] iwlagn 0000:09:00.0: loaded firmware version 17.168.5.2 build 35905
[   11.029146] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   11.038770] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.057505] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[   11.111995] alps.c: Enabled hardware quirk, falling back to psmouse-core
[   11.119549] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.119552] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[   11.125413] input: ImPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   11.140092] usb 3-3: new low speed USB device using xhci_hcd and address 2
[   11.162314] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.162551] usbcore: registered new interface driver btusb
[   11.180657] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.187666] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.192731] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.193754] usb 3-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   11.204058] Console: switching to colour frame buffer device 170x48
[   11.204081] fb0: inteldrmfb frame buffer device
[   11.204083] drm: registered panic notifier
[   11.204272] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   11.206613] xhci_hcd 0000:0b:00.0: WARN: Stalled endpoint
[   11.215992] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1c.4/0000:0b:00.0/usb3/3-3/3-3:1.0/input/input8
[   11.216161] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:0b:00.0-3/input0
[   11.216198] usbcore: registered new interface driver usbhid
[   11.216200] usbhid: USB HID core driver
[   11.240818] acpi device:1d: registered as cooling_device4
[   11.241140] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input9
[   11.241195] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   11.241929] acpi device:3c: registered as cooling_device5
[   11.242086] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[   11.242124] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.242235] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.242307] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.242367] HDA Intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[   11.242396] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.251119] [drm] nouveau 0000:01:00.0: Unsupported chipset 0xffffffff
[   11.252260] nouveau 0000:01:00.0: PCI INT A disabled
[   11.252268] nouveau: probe of 0000:01:00.0 failed with error -22
[   11.310060] usb 3-4: new high speed USB device using xhci_hcd and address 3
[   11.333505] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.334123] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.334747] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.335372] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.335696] usb 3-4: ep 0x82 - rounding interval to 256 microframes
[   11.335715] usb 3-4: ep 0x86 - rounding interval to 8192 microframes
[   11.337757] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.338372] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.338746] xhci_hcd 0000:0b:00.0: WARN: short transfer on control ep
[   11.341534] cdc_acm 3-4:4.0: This device cannot do calls on its own. It is not a modem.
[   11.341583] cdc_acm 3-4:4.0: ttyACM0: USB ACM device
[   11.342198] usbcore: registered new interface driver cdc_acm
[   11.342200] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   11.360280] input: HDA Intel PCH Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.360379] input: HDA Intel PCH HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.360588] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.360590] hda_intel: Disable MSI for Nvidia chipset
[   11.360643] HDA Intel 0000:01:00.1: setting latency timer to 64
[   13.350817] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.689937] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   13.819462] r8169 0000:05:00.0: eth0: link down
[   13.819720] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.833813] type=1400 audit(1315973175.478:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=939 comm="apparmor_parser"
[   13.834055] type=1400 audit(1315973175.478:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=940 comm="apparmor_parser"
[   13.835600] type=1400 audit(1315973175.478:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=944 comm="apparmor_parser"
[   13.836097] type=1400 audit(1315973175.478:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=943 comm="apparmor_parser"
[   13.837013] type=1400 audit(1315973175.478:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=943 comm="apparmor_parser"
[   13.839346] type=1400 audit(1315973175.488:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=940 comm="apparmor_parser"
[   13.839830] type=1400 audit(1315973175.488:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=940 comm="apparmor_parser"
[   13.957762] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.058209] ppdev: user-space parallel port driver
[   14.332567] Bluetooth: L2CAP ver 2.15
[   14.332570] Bluetooth: L2CAP socket layer initialized
[   14.422820] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.422823] Bluetooth: BNEP filters: protocol multicast
[   14.452712] Bluetooth: SCO (Voice Link) ver 0.6
[   14.452715] Bluetooth: SCO socket layer initialized
[   14.897636] Bluetooth: RFCOMM TTY layer initialized
[   14.897642] Bluetooth: RFCOMM socket layer initialized
[   14.897643] Bluetooth: RFCOMM ver 1.11
[   15.084086] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.123366] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   16.182468] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.184399] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   25.736957] wlan0: authenticate with 04:18:0f:8d:3e:37 (try 1)
[   25.787200] wlan0: authenticated
[   25.787817] wlan0: associate with 04:18:0f:8d:3e:37 (try 1)
[   25.790659] wlan0: RX AssocResp from 04:18:0f:8d:3e:37 (capab=0x411 status=0 aid=1)
[   25.790665] wlan0: associated
[   25.795390] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.670956] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   36.596926] wlan0: no IPv6 routers present
[   42.144087] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 11495, at 11495], missed IRQ?
[   46.551820] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 12407, at 12407], missed IRQ?
[   77.035363] usb 2-1.2: new full speed USB device using ehci_hcd and address 4
[   77.115279] usb 2-1.2: device descriptor read/64, error -32
[   77.338053] scsi7 : usb-storage 2-1.2:1.0
[   78.336986] scsi 7:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[   78.342399] sr1: scsi-1 drive
[   78.342705] sr 7:0:0:0: Attached scsi CD-ROM sr1
[   78.343026] sr 7:0:0:0: Attached scsi generic sg3 type 5
[   78.376053] usb 2-1.2: USB disconnect, address 4
[   78.685196] usb 2-1.2: new full speed USB device using ehci_hcd and address 5
[   78.797291] usbserial_generic 2-1.2:1.0: generic converter detected
[   78.797514] usb 2-1.2: generic converter now attached to ttyUSB0
[   78.797965] usbserial_generic 2-1.2:1.1: generic converter detected
[   78.798157] usb 2-1.2: generic converter now attached to ttyUSB1
[   82.433256] usb 2-1.2: USB disconnect, address 5
[   82.433647] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[   82.433688] usbserial_generic 2-1.2:1.0: device disconnected
[   82.434112] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[   82.434152] usbserial_generic 2-1.2:1.1: device disconnected
[   84.205090] usb 2-1.2: new full speed USB device using ehci_hcd and address 6
[   84.284985] usb 2-1.2: device descriptor read/64, error -32
[   84.508527] usbserial_generic 2-1.2:1.0: Generic device with no bulk out, not allowed.
[   84.508536] usbserial_generic: probe of 2-1.2:1.0 failed with error -5
[   84.508546] cdc_acm 2-1.2:1.0: This device cannot do calls on its own. It is not a modem.
[   84.508575] cdc_acm 2-1.2:1.0: ttyACM1: USB ACM device
[   84.509585] scsi8 : usb-storage 2-1.2:1.2
[   85.506856] scsi 8:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[   85.507836] scsi 8:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
[   85.512100] sr1: scsi-1 drive
[   85.512621] sr 8:0:0:0: Attached scsi CD-ROM sr1
[   85.514533] sr 8:0:0:0: Attached scsi generic sg3 type 5
[   85.515250] sd 8:0:0:1: Attached scsi generic sg4 type 0
[   85.528114] sd 8:0:0:1: [sdc] Attached SCSI removable disk
```

---

