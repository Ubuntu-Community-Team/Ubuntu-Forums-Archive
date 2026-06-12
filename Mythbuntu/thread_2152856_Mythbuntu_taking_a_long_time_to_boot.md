---
title: "Mythbuntu taking a long time to boot"
date: 2013-06-09
forum: Mythbuntu
---

### Post by mickaus on 2013-06-09
I am running a combined front end and backend on 64 bit Mythbuntu 12.04 with Mythtv 0.26 and am disappointed with the length of time it takes from a cold boot for the Mythfrontend GUI to appear and Mythbackend started  - currently this takes around 70 seconds. Some hardware details: CPU Intel i3-2130, 4GB RAM, OS resides on 60GB SSD, 2TB WD Green drive for recordings, 2 x Hauppage WinTV-HVR-2200 DVB-T cards.
I have tried suspending the PC rather than shutting down with no improvement to the boot time. 

I guess what I'm trying to find out should the boot time be better for this setup? Is this the time I should expect?

I have attached a bootchart image which I can't see anything obvious that is causing the long boot time.

It seems that the 2 Hauppage cards may be causing some of this delay looking at the output from dmesg there are many occurances of 'saa7164' and 'tda10048':
```

[COLOR=#0000cd]michael@michael-Z68MA-D2H-B3:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-45-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 (Ubuntu 3.2.0-45.70-generic 3.2.44)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-45-generic root=UUID=ffcfc58a-47b3-4725-9024-16e0577b6252 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df780000 (usable)
[    0.000000]  BIOS-e820: 00000000df780000 - 00000000df7a3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000df7a3000 - 00000000df7e0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000df7e0000 - 00000000df800000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000011f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. Z68MA-D2H-B3/Z68MA-D2H-B3, BIOS F9 10/12/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x11f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-CDFFF uncachable
[    0.000000]   CE000-D0FFF write-protect
[    0.000000]   D1000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 100000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 4GB, range: 512MB, type WB
[    0.000000] total RAM covered: 4096M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 1G  num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 4GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf780 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f58d0] f58d0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000df780000
[    0.000000]  0000000000 - 00df600000 page 2M
[    0.000000]  00df600000 - 00df780000 page 4k
[    0.000000] kernel direct mapping tables up to df780000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000011f800000
[    0.000000]  0100000000 - 011f800000 page 2M
[    0.000000] kernel direct mapping tables up to 11f800000 @ df77e000-df780000
[    0.000000] RAMDISK: 364c2000 - 37259000
[    0.000000] ACPI: RSDP 00000000000f74c0 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000df7a3040 00054 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000df7a3100 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000df7a31c0 04B3C (v01 GBT    GBTUACPI 00001000 MSFT 04000000)
[    0.000000] ACPI: FACS 00000000df780000 00040
[    0.000000] ACPI: MSDM 00000000df7a7e40 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: HPET 00000000df7a7f00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000df7a7f80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: ASPT 00000000df7a8100 00034 (v07 GBT    PerfTune 312E3042 UTBG 01010101)
[    0.000000] ACPI: SSPT 00000000df7a8140 02324 (v01 GBT    SsptHead 312E3042 UTBG 01010101)
[    0.000000] ACPI: EUDS 00000000df7aa470 000C0 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: MATS 00000000df7aa530 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000df7aa590 00392 (v01 GBT    GBT   B0 5455312E BG?? 45240101)
[    0.000000] ACPI: APIC 00000000df7a7d40 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT 00000000df7aa940 01F4C (v01  INTEL PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: MATS 00000000df7ac8c0 0995B (v01        MATS RCM 80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000011f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000011f800000
[    0.000000]   NODE_DATA [000000011f7fb000 - 000000011f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00047fffff] PMD -> [ffff88011ae00000-ffff88011edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0011f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000df780
[    0.000000]     0: 0x00100000 -> 0x0011f800
[    0.000000] On node 0 totalpages: 1044237
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 894912 pages, LIFO batch:31
[    0.000000]   Normal zone: 2016 pages used for memmap
[    0.000000]   Normal zone: 127008 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df780000 - 00000000df7a3000
[    0.000000] PM: Registered nosave memory: 00000000df7a3000 - 00000000df7e0000
[    0.000000] PM: Registered nosave memory: 00000000df7e0000 - 00000000df800000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at df800000 (gap: df800000:14800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011f400000 s83136 r8192 d23360 u262144
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1025832
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-45-generic root=UUID=ffcfc58a-47b3-4725-9024-16e0577b6252 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4014708k/4710400k available (6579k kernel code, 533452k absent, 162240k reserved, 6626k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3392.155 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.31 BogoMIPS (lpj=13568620)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000020] Security Framework initialized
[    0.000029] AppArmor: AppArmor initialized
[    0.000030] Yama: becoming mindful.
[    0.000235] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001190] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001623] Mount-cache hash table entries: 256
[    0.001707] Initializing cgroup subsys cpuacct
[    0.001710] Initializing cgroup subsys memory
[    0.001716] Initializing cgroup subsys devices
[    0.001717] Initializing cgroup subsys freezer
[    0.001718] Initializing cgroup subsys blkio
[    0.001722] Initializing cgroup subsys perf_event
[    0.001741] CPU: Physical Processor ID: 0
[    0.001742] CPU: Processor Core ID: 0
[    0.001745] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.001745] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.001748] mce: CPU supports 7 MCE banks
[    0.001756] CPU0: Thermal monitoring enabled (TM1)
[    0.001762] using mwait in idle threads.
[    0.003497] ACPI: Core revision 20110623
[    0.006191] ftrace: allocating 26570 entries in 105 pages
[    0.013412] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.052981] CPU0: Intel(R) Core(TM) i3-2130 CPU @ 3.40GHz stepping 07
[    0.160552] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.160556] PEBS disabled due to CPU errata.
[    0.160557] ... version:                3
[    0.160558] ... bit width:              48
[    0.160559] ... generic registers:      4
[    0.160560] ... value mask:             0000ffffffffffff
[    0.160561] ... max period:             000000007fffffff
[    0.160561] ... fixed-purpose events:   3
[    0.160562] ... event mask:             000000070000000f
[    0.160668] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160716] Booting Node   0, Processors  #1
[    0.160718] smpboot cpu 1: start_ip = 98000
[    0.268340] NMI watchdog enabled, takes one hw-pmu counter.
[    0.268400]  #2
[    0.268401] smpboot cpu 2: start_ip = 98000
[    0.375996] NMI watchdog enabled, takes one hw-pmu counter.
[    0.376058]  #3
[    0.376059] smpboot cpu 3: start_ip = 98000
[    0.483677] NMI watchdog enabled, takes one hw-pmu counter.
[    0.483700] Brought up 4 CPUs
[    0.483702] Total of 4 processors activated (27137.08 BogoMIPS).
[    0.486322] devtmpfs: initialized
[    0.486782] EVM: security.selinux
[    0.486783] EVM: security.SMACK64
[    0.486784] EVM: security.capability
[    0.486800] PM: Registering ACPI NVS region at df780000 (143360 bytes)
[    0.487301] print_constraints: dummy:
[    0.487326] RTC time:  9:22:34, date: 06/09/13
[    0.487348] NET: Registered protocol family 16
[    0.487411] Trying to unpack rootfs image as initramfs...
[    0.487416] ACPI: bus type pci registered
[    0.487453] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.487455] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.493622] PCI: Using configuration type 1 for base access
[    0.494210] bio: create slab <bio-0> at 0
[    0.494268] ACPI: Added _OSI(Module Device)
[    0.494270] ACPI: Added _OSI(Processor Device)
[    0.494271] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.494272] ACPI: Added _OSI(Processor Aggregator Device)
[    0.494757] ACPI: EC: Look up EC in DSDT
[    0.497254] ACPI: Interpreter enabled
[    0.497257] ACPI: (supports S0 S3 S4 S5)
[    0.497267] ACPI: Using IOAPIC for interrupt routing
[    0.499258] ACPI: No dock devices found.
[    0.499260] HEST: Table not found.
[    0.499262] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.499292] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.499349] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.499351] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.499352] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.499353] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.499355] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.499356] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfebfffff]
[    0.499364] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
[    0.499391] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    0.499413] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.499415] pci 0000:00:01.0: PME# disabled
[    0.499425] pci 0000:00:01.1: [8086:0105] type 1 class 0x000604
[    0.499446] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
[    0.499448] pci 0000:00:01.1: PME# disabled
[    0.499483] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    0.499503] pci 0000:00:16.0: reg 10: [mem 0xfbfff000-0xfbfff00f 64bit]
[    0.499578] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.499581] pci 0000:00:16.0: PME# disabled
[    0.499609] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    0.499628] pci 0000:00:1a.0: reg 10: [mem 0xfbffe000-0xfbffe3ff]
[    0.499713] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.499717] pci 0000:00:1a.0: PME# disabled
[    0.499737] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    0.499750] pci 0000:00:1b.0: reg 10: [mem 0xfbff4000-0xfbff7fff 64bit]
[    0.499812] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.499815] pci 0000:00:1b.0: PME# disabled
[    0.499833] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    0.499906] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.499909] pci 0000:00:1c.0: PME# disabled
[    0.499934] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
[    0.500006] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.500009] pci 0000:00:1c.6: PME# disabled
[    0.500029] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
[    0.500101] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.500104] pci 0000:00:1c.7: PME# disabled
[    0.500128] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    0.500147] pci 0000:00:1d.0: reg 10: [mem 0xfbffd000-0xfbffd3ff]
[    0.500231] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.500234] pci 0000:00:1d.0: PME# disabled
[    0.500250] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.500307] pci 0000:00:1f.0: [8086:1c44] type 0 class 0x000601
[    0.500422] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
[    0.500438] pci 0000:00:1f.2: reg 10: [io  0xff00-0xff07]
[    0.500444] pci 0000:00:1f.2: reg 14: [io  0xfe00-0xfe03]
[    0.500451] pci 0000:00:1f.2: reg 18: [io  0xfd00-0xfd07]
[    0.500457] pci 0000:00:1f.2: reg 1c: [io  0xfc00-0xfc03]
[    0.500464] pci 0000:00:1f.2: reg 20: [io  0xfb00-0xfb1f]
[    0.500471] pci 0000:00:1f.2: reg 24: [mem 0xfbffc000-0xfbffc7ff]
[    0.500511] pci 0000:00:1f.2: PME# supported from D3hot
[    0.500513] pci 0000:00:1f.2: PME# disabled
[    0.500526] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    0.500539] pci 0000:00:1f.3: reg 10: [mem 0xfbffb000-0xfbffb0ff 64bit]
[    0.500558] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.500604] pci 0000:01:00.0: [10de:0de1] type 0 class 0x000300
[    0.500612] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf8ffffff]
[    0.500620] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff 64bit pref]
[    0.500628] pci 0000:01:00.0: reg 1c: [mem 0xee000000-0xefffffff 64bit pref]
[    0.500634] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.500640] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.500686] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    0.500694] pci 0000:01:00.1: reg 10: [mem 0xf9ffc000-0xf9ffffff]
[    0.507561] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.507563] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.507565] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.507568] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.507597] pci 0000:02:00.0: [1131:7164] type 0 class 0x000480
[    0.507616] pci 0000:02:00.0: reg 10: [mem 0xfb000000-0xfb3fffff 64bit]
[    0.507630] pci 0000:02:00.0: reg 18: [mem 0xfac00000-0xfaffffff 64bit]
[    0.507704] pci 0000:02:00.0: supports D1 D2
[    0.507705] pci 0000:02:00.0: PME# supported from D0 D1 D2
[    0.507709] pci 0000:02:00.0: PME# disabled
[    0.515537] pci 0000:00:01.1: PCI bridge to [bus 02-02]
[    0.515540] pci 0000:00:01.1:   bridge window [mem 0xfac00000-0xfb3fffff]
[    0.515604] pci 0000:03:00.0: [1131:7164] type 0 class 0x000480
[    0.515634] pci 0000:03:00.0: reg 10: [mem 0xfb800000-0xfbbfffff 64bit]
[    0.515657] pci 0000:03:00.0: reg 18: [mem 0xfb400000-0xfb7fffff 64bit]
[    0.515782] pci 0000:03:00.0: supports D1 D2
[    0.515783] pci 0000:03:00.0: PME# supported from D0 D1 D2
[    0.515789] pci 0000:03:00.0: PME# disabled
[    0.523516] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.523522] pci 0000:00:1c.0:   bridge window [mem 0xfb400000-0xfbbfffff]
[    0.523591] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
[    0.523610] pci 0000:04:00.0: reg 10: [io  0xde00-0xdeff]
[    0.523643] pci 0000:04:00.0: reg 18: [mem 0xfbdff000-0xfbdfffff 64bit pref]
[    0.523663] pci 0000:04:00.0: reg 20: [mem 0xfbdf8000-0xfbdfbfff 64bit pref]
[    0.523754] pci 0000:04:00.0: supports D1 D2
[    0.523755] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.523760] pci 0000:04:00.0: PME# disabled
[    0.531496] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    0.531501] pci 0000:00:1c.6:   bridge window [io  0xd000-0xdfff]
[    0.531507] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.531571] pci 0000:05:00.0: [1b6f:7023] type 0 class 0x000c03
[    0.531597] pci 0000:05:00.0: reg 10: [mem 0xfbef8000-0xfbefffff 64bit]
[    0.531719] pci 0000:05:00.0: supports D1 D2
[    0.531720] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.531725] pci 0000:05:00.0: PME# disabled
[    0.539471] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
[    0.539478] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.539539] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.539547] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.539548] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.539550] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.539551] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.539553] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.539554] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xfebfffff] (subtractive decode)
[    0.539578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.539662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.539679] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG1._PRT]
[    0.539697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.539718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
[    0.539733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
[    0.539766]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.539767]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.539768] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.543385] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.543412] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.543445] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.543470] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.543495] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.543522] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.543547] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.543572] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.543653] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.543655] vgaarb: loaded
[    0.543656] vgaarb: bridge control possible 0000:01:00.0
[    0.543712] i2c-core: driver [aat2870] using legacy suspend method
[    0.543713] i2c-core: driver [aat2870] using legacy resume method
[    0.543748] SCSI subsystem initialized
[    0.543787] libata version 3.00 loaded.
[    0.543813] usbcore: registered new interface driver usbfs
[    0.543819] usbcore: registered new interface driver hub
[    0.543834] usbcore: registered new device driver usb
[    0.543882] PCI: Using ACPI for IRQ routing
[    0.545268] PCI: pci_cache_line_size set to 64 bytes
[    0.545325] reserve RAM buffer: 000000000009dc00 - 000000000009ffff
[    0.545326] reserve RAM buffer: 00000000df780000 - 00000000dfffffff
[    0.545328] reserve RAM buffer: 000000011f800000 - 000000011fffffff
[    0.545388] NetLabel: Initializing
[    0.545389] NetLabel:  domain hash size = 128
[    0.545390] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.545397] NetLabel:  unlabeled traffic allowed by default
[    0.545428] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.545432] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.547441] Switching to clocksource hpet
[    0.551379] AppArmor: AppArmor Filesystem Enabled
[    0.551398] pnp: PnP ACPI init
[    0.551409] ACPI: bus type pnp registered
[    0.551492] pnp 00:00: [bus 00-3f]
[    0.551494] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.551495] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.551496] pnp 00:00: [io  0x0d00-0xffff window]
[    0.551498] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.551499] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.551500] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.551501] pnp 00:00: [mem 0xe0000000-0xfebfffff window]
[    0.551539] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.551587] pnp 00:01: [io  0x0010-0x001f]
[    0.551588] pnp 00:01: [io  0x0022-0x003f]
[    0.551589] pnp 00:01: [io  0x0044-0x004d]
[    0.551590] pnp 00:01: [io  0x0050-0x005f]
[    0.551591] pnp 00:01: [io  0x0062-0x0063]
[    0.551592] pnp 00:01: [io  0x0065-0x006f]
[    0.551593] pnp 00:01: [io  0x0074-0x007f]
[    0.551594] pnp 00:01: [io  0x0091-0x0093]
[    0.551595] pnp 00:01: [io  0x00a2-0x00bf]
[    0.551596] pnp 00:01: [io  0x00e0-0x00ef]
[    0.551597] pnp 00:01: [io  0x04d0-0x04d1]
[    0.551598] pnp 00:01: [io  0x0290-0x029f]
[    0.551599] pnp 00:01: [io  0x0800-0x0805]
[    0.551600] pnp 00:01: [io  0x0290-0x0294]
[    0.551600] pnp 00:01: [io  0x0880-0x088f]
[    0.551635] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.551636] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.551637] system 00:01: [io  0x0800-0x0805] has been reserved
[    0.551639] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.551640] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.551642] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.551649] pnp 00:02: [dma 4]
[    0.551650] pnp 00:02: [io  0x0000-0x000f]
[    0.551651] pnp 00:02: [io  0x0080-0x0090]
[    0.551652] pnp 00:02: [io  0x0094-0x009f]
[    0.551652] pnp 00:02: [io  0x00c0-0x00df]
[    0.551667] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.551696] pnp 00:03: [irq 0 disabled]
[    0.551704] pnp 00:03: [irq 8]
[    0.551705] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.551720] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.551734] pnp 00:04: [io  0x0070-0x0073]
[    0.551748] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.551752] pnp 00:05: [io  0x0061]
[    0.551767] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.551771] pnp 00:06: [io  0x00f0-0x00ff]
[    0.551775] pnp 00:06: [irq 13]
[    0.551790] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.551934] pnp 00:07: [io  0x03f8-0x03ff]
[    0.551938] pnp 00:07: [irq 4]
[    0.551971] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.552005] pnp 00:08: [io  0x0400-0x04cf]
[    0.552006] pnp 00:08: [io  0x04d2-0x04ff]
[    0.552028] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.552030] system 00:08: [io  0x04d2-0x04ff] has been reserved
[    0.552031] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.552037] pnp 00:09: [io  0x1000-0x107f]
[    0.552038] pnp 00:09: [io  0x1080-0x10ff]
[    0.552041] pnp 00:09: [io  0x1100-0x117f]
[    0.552042] pnp 00:09: [io  0x1180-0x11ff]
[    0.552064] system 00:09: [io  0x1000-0x107f] has been reserved
[    0.552066] system 00:09: [io  0x1080-0x10ff] has been reserved
[    0.552067] system 00:09: [io  0x1100-0x117f] has been reserved
[    0.552068] system 00:09: [io  0x1180-0x11ff] has been reserved
[    0.552070] system 00:09: Plug and Play ACPI device, IDs ICD0001 PNP0c02 (active)
[    0.552166] pnp 00:0a: [io  0x0454-0x0457]
[    0.552193] system 00:0a: [io  0x0454-0x0457] has been reserved
[    0.552195] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.552204] pnp 00:0b: [mem 0xf4000000-0xf7ffffff]
[    0.552232] system 00:0b: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.552234] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.552328] pnp 00:0c: [mem 0x000d0a00-0x000d3fff]
[    0.552329] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
[    0.552330] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
[    0.552331] pnp 00:0c: [mem 0x000fc000-0x000fffff]
[    0.552332] pnp 00:0c: [mem 0xdf780000-0xdf7dffff]
[    0.552333] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.552335] pnp 00:0c: [mem 0x00100000-0xdf77ffff]
[    0.552336] pnp 00:0c: [mem 0xdf7e0000-0xdf7fffff]
[    0.552337] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.552338] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
[    0.552339] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
[    0.552340] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.552341] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
[    0.552342] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.552343] pnp 00:0c: [mem 0x000e0000-0x000effff]
[    0.552344] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    0.552345] pnp 00:0c: [mem 0x40000000-0x400fffff]
[    0.552346] pnp 00:0c: [mem 0xdf800000-0xdfffffff]
[    0.552379] system 00:0c: [mem 0x000d0a00-0x000d3fff] has been reserved
[    0.552381] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.552382] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.552384] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.552385] system 00:0c: [mem 0xdf780000-0xdf7dffff] could not be reserved
[    0.552386] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.552388] system 00:0c: [mem 0x00100000-0xdf77ffff] could not be reserved
[    0.552389] system 00:0c: [mem 0xdf7e0000-0xdf7fffff] has been reserved
[    0.552391] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.552392] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.552394] system 00:0c: [mem 0xfed20000-0xfed8ffff] could not be reserved
[    0.552395] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.552397] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.552398] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.552399] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.552401] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    0.552402] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
[    0.552404] system 00:0c: [mem 0xdf800000-0xdfffffff] could not be reserved
[    0.552405] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.552415] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
[    0.552435] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
[    0.552438] pnp: PnP ACPI: found 14 devices
[    0.552439] ACPI: ACPI bus type pnp unregistered
[    0.558367] PCI: max bus depth: 1 pci_try_num: 2
[    0.558407] pci 0000:01:00.0: BAR 6: assigned [mem 0xe8000000-0xe807ffff pref]
[    0.558409] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.558410] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.558413] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.558415] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.558417] pci 0000:00:01.1: PCI bridge to [bus 02-02]
[    0.558419] pci 0000:00:01.1:   bridge window [mem 0xfac00000-0xfb3fffff]
[    0.558422] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.558426] pci 0000:00:1c.0:   bridge window [mem 0xfb400000-0xfbbfffff]
[    0.558433] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    0.558435] pci 0000:00:1c.6:   bridge window [io  0xd000-0xdfff]
[    0.558441] pci 0000:00:1c.6:   bridge window [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.558446] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
[    0.558450] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.558457] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.558477] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.558480] pci 0000:00:01.0: setting latency timer to 64
[    0.558483] pci 0000:00:01.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.558484] pci 0000:00:01.1: setting latency timer to 64
[    0.558489] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.558492] pci 0000:00:1c.0: setting latency timer to 64
[    0.558499] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.558502] pci 0000:00:1c.6: setting latency timer to 64
[    0.558508] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.558511] pci 0000:00:1c.7: setting latency timer to 64
[    0.558517] pci 0000:00:1e.0: setting latency timer to 64
[    0.558520] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.558521] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.558522] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.558524] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.558525] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.558526] pci_bus 0000:00: resource 9 [mem 0xe0000000-0xfebfffff]
[    0.558528] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.558529] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.558530] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.558532] pci_bus 0000:02: resource 1 [mem 0xfac00000-0xfb3fffff]
[    0.558533] pci_bus 0000:03: resource 1 [mem 0xfb400000-0xfbbfffff]
[    0.558535] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.558536] pci_bus 0000:04: resource 2 [mem 0xfbd00000-0xfbdfffff 64bit pref]
[    0.558538] pci_bus 0000:05: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.558539] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.558540] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.558542] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.558543] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000dffff]
[    0.558544] pci_bus 0000:06: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.558546] pci_bus 0000:06: resource 9 [mem 0xe0000000-0xfebfffff]
[    0.558568] NET: Registered protocol family 2
[    0.558649] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.559137] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.560998] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.561234] TCP: Hash tables configured (established 524288 bind 65536)
[    0.561235] TCP reno registered
[    0.561241] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.561260] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.561333] NET: Registered protocol family 1
[    0.561354] pci 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.575435] pci 0000:00:1a.0: PCI INT C disabled
[    0.575461] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.591385] pci 0000:00:1d.0: PCI INT A disabled
[    0.591406] pci 0000:01:00.0: Boot video device
[    0.591428] pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.591466] pci 0000:05:00.0: PCI INT A disabled
[    0.591469] PCI: CLS 4 bytes, default 64
[    0.591471] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.591472] Placing 64MB software IO TLB between ffff8800db77e000 - ffff8800df77e000
[    0.591473] software IO TLB at phys 0xdb77e000 - 0xdf77e000
[    0.591784] audit: initializing netlink socket (disabled)
[    0.591795] type=2000 audit(1370769753.436:1): initialized
[    0.607009] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.608153] VFS: Disk quotas dquot_6.5.2
[    0.608185] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.608464] fuse init (API version 7.17)
[    0.608513] msgmni has been set to 7841
[    0.608728] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.608745] io scheduler noop registered
[    0.608747] io scheduler deadline registered
[    0.608764] io scheduler cfq registered (default)
[    0.608824] pcieport 0000:00:01.0: setting latency timer to 64
[    0.608843] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.608869] pcieport 0000:00:01.1: setting latency timer to 64
[    0.608883] pcieport 0000:00:01.1: irq 41 for MSI/MSI-X
[    0.609031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.609041] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609072] intel_idle: MWAIT substates: 0x1120
[    0.609073] intel_idle: v0.4 model 0x2A
[    0.609074] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.609129] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.609133] ACPI: Power Button [PWRB]
[    0.609160] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.609162] ACPI: Power Button [PWRF]
[    0.612527] ERST: Table is not found!
[    0.612529] GHES: HEST is not enabled!
[    0.612591] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.632948] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.653067] Freeing initrd memory: 13916k freed
[    0.815338] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.838891] Linux agpgart interface v0.103
[    0.839731] brd: module loaded
[    0.840145] loop: module loaded
[    0.840219] ahci 0000:00:1f.2: version 3.0
[    0.840228] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.840265] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.840288] ahci: SSS flag set, parallel bus scan disabled
[    0.854643] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.854648] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems apst
[    0.854653] ahci 0000:00:1f.2: setting latency timer to 64
[    0.894832] scsi0 : ahci
[    0.894881] scsi1 : ahci
[    0.894921] scsi2 : ahci
[    0.894960] scsi3 : ahci
[    0.895000] scsi4 : ahci
[    0.895041] scsi5 : ahci
[    0.895115] ata1: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 42
[    0.895117] ata2: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 42
[    0.895119] ata3: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 42
[    0.895121] ata4: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 42
[    0.895123] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 42
[    0.895125] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 42
[    0.895346] Fixed MDIO Bus: probed
[    0.895357] tun: Universal TUN/TAP device driver, 1.6
[    0.895358] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.895390] PPP generic driver version 2.4.2
[    0.895443] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.895454] ehci_hcd 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.895466] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.895468] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.895495] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.895517] ehci_hcd 0000:00:1a.0: debug port 2
[    0.899380] ehci_hcd 0000:00:1a.0: cache line size of 4 is not supported
[    0.899391] ehci_hcd 0000:00:1a.0: irq 18, io mem 0xfbffe000
[    0.914446] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.914575] hub 1-0:1.0: USB hub found
[    0.914577] hub 1-0:1.0: 2 ports detected
[    0.914615] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.914624] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.914626] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.914650] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.914667] ehci_hcd 0000:00:1d.0: debug port 2
[    0.918552] ehci_hcd 0000:00:1d.0: cache line size of 4 is not supported
[    0.918561] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbffd000
[    0.934389] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.934508] hub 2-0:1.0: USB hub found
[    0.934510] hub 2-0:1.0: 2 ports detected
[    0.934544] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.934551] uhci_hcd: USB Universal Host Controller Interface driver
[    0.934569] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.934582] xhci_hcd 0000:05:00.0: setting latency timer to 64
[    0.934585] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.934614] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 3
[    0.934781] xhci_hcd 0000:05:00.0: irq 43 for MSI/MSI-X
[    0.934869] xHCI xhci_add_endpoint called for root hub
[    0.934870] xHCI xhci_check_bandwidth called for root hub
[    0.934883] hub 3-0:1.0: USB hub found
[    0.934889] hub 3-0:1.0: 2 ports detected
[    0.934922] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    0.934945] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 4
[    0.934994] xHCI xhci_add_endpoint called for root hub
[    0.934995] xHCI xhci_check_bandwidth called for root hub
[    0.935007] hub 4-0:1.0: USB hub found
[    0.935012] hub 4-0:1.0: 2 ports detected
[    0.986277] usbcore: registered new interface driver libusual
[    0.986321] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.019595] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.019597] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.229549] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.269511] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.269581] mousedev: PS/2 mouse device common for all mice
[    1.269670] rtc_cmos 00:04: RTC can wake from S4
[    1.269757] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.269782] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.269827] device-mapper: uevent: version 1.0.3
[    1.269865] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.269923] cpuidle: using governor ladder
[    1.270006] cpuidle: using governor menu
[    1.270007] EFI Variables Facility v0.08 2004-May-17
[    1.270118] TCP cubic registered
[    1.270172] NET: Registered protocol family 10
[    1.270407] NET: Registered protocol family 17
[    1.270410] Registering the dns_resolver key type
[    1.270493] PM: Hibernation image not present or could not be loaded.
[    1.270500] registered taskstats version 1
[    1.274777]   Magic number: 1:451:373
[    1.274805] vc vcsa1: hash matches
[    1.274879] rtc_cmos 00:04: setting system clock to 2013-06-09 09:22:34 UTC (1370769754)
[    1.275466] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.275467] EDD information not available.
[    1.361949] hub 1-1:1.0: USB hub found
[    1.362031] hub 1-1:1.0: 6 ports detected
[    1.385148] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.397313] ata1.00: ATA-8: OCZ-AGILITY3, 2.25, max UDMA/133
[    1.397318] ata1.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.407225] ata1.00: configured for UDMA/133
[    1.407455] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.25 PQ: 0 ANSI: 5
[    1.407591] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.407619] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.407687] sd 0:0:0:0: [sda] Write Protect is off
[    1.407689] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.407769] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.408626]  sda: sda1 sda2 < >
[    1.408971] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.472901] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.588557] Refined TSC clocksource calibration: 3392.293 MHz.
[    1.588563] Switching to clocksource tsc
[    1.605248] hub 2-1:1.0: USB hub found
[    1.605328] hub 2-1:1.0: 8 ports detected
[    1.875966] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
[    1.895671] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.043484] usb 2-1.3: new low-speed USB device number 4 using ehci_hcd
[    2.306197] ata2.00: ATA-8: WDC WD20EARX-00PASB0, 51.0AB51, max UDMA/133
[    2.306202] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.313189] ata2.00: configured for UDMA/133
[    2.313388] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EARX-00P 51.0 PQ: 0 ANSI: 5
[    2.313504] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.313506] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.313515] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.313562] sd 1:0:0:0: [sdb] Write Protect is off
[    2.313564] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.313638] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.412843]  sdb: sdb1 sdb2 < sdb5 >
[    2.413361] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.801082] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.803794] ata3.00: ATAPI: HL-DT-ST BDDVDRW CH12LS28, 1.00, max UDMA/133
[    2.807683] ata3.00: configured for UDMA/133
[    2.813654] scsi 2:0:0:0: CD-ROM            HL-DT-ST BDDVDRW CH12LS28 1.00 PQ: 0 ANSI: 5
[    2.817673] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.817678] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.817793] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.817836] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    3.136137] ata4: SATA link down (SStatus 0 SControl 300)
[    3.455225] ata5: SATA link down (SStatus 0 SControl 300)
[    3.774312] ata6: SATA link down (SStatus 0 SControl 300)
[    3.775299] Freeing unused kernel memory: 924k freed
[    3.775377] Write protecting the kernel read-only data: 12288k
[    3.778296] Freeing unused kernel memory: 1596k freed
[    3.780546] Freeing unused kernel memory: 1188k freed
[    3.797137] udevd[122]: starting version 175
[    3.818552] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.818572] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.818611] r8169 0000:04:00.0: setting latency timer to 64
[    3.818693] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    3.819034] r8169 0000:04:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000656000, 50:e5:49:e9:22:40, XID 0c900800 IRQ 44
[    3.819038] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.823384] usbcore: registered new interface driver usbhid
[    3.823386] usbhid: USB HID core driver
[    3.848701] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.1/input2
[    3.851385] input: Logitech Unifying Device. Wireless PID:400e as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:046D:C52B.0003/input/input2
[    3.851593] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:400e] on usb-0000:00:1d.0-1.1:1
[    3.895841] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.616068] Adding 4176864k swap on /dev/sdb5.  Priority:-1 extents:1 across:4176864k
[    4.637124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.641220] udevd[382]: starting version 175
[    4.658982] lp: driver loaded but no devices found
[    4.699523] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    4.701124] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.701130] mei 0000:00:16.0: setting latency timer to 64
[    4.701426] mei 0000:00:16.0: irq 45 for MSI/MSI-X
[    4.707359] Linux video capture interface: v2.00
[    4.710946] saa7164 driver loaded
[    4.710995] saa7164 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.712078] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[    4.712084] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb000000
[    4.712090] saa7164 0000:02:00.0: setting latency timer to 64
[    4.731395] wmi: Mapper loaded
[    4.745504] nvidia: module license 'NVIDIA' taints kernel.
[    4.745508] Disabling lock debugging due to kernel taint
[    4.748405] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    4.798879] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.798885] nvidia 0000:01:00.0: setting latency timer to 64
[    4.798889] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    4.798955] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
[    4.828520] input: iMON Panel, Knob and Mouse(15c2:0038) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
[    4.833786] IR NEC protocol handler initialized
[    4.835023] type=1400 audit(1370769758.064:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=718 comm="apparmor_parser"
[    4.835386] type=1400 audit(1370769758.068:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=718 comm="apparmor_parser"
[    4.835554] type=1400 audit(1370769758.068:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=718 comm="apparmor_parser"
[    4.836562] type=1400 audit(1370769758.068:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=598 comm="apparmor_parser"
[    4.836855] type=1400 audit(1370769758.068:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
[    4.837019] type=1400 audit(1370769758.068:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=598 comm="apparmor_parser"
[    4.842349] IR RC5(x) protocol handler initialized
[    4.842909] type=1400 audit(1370769758.072:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=729 comm="apparmor_parser"
[    4.843433] type=1400 audit(1370769758.076:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=731 comm="apparmor_parser"
[    4.850406] IR RC6 protocol handler initialized
[    4.854135] IR JVC protocol handler initialized
[    4.858275] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.858328] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    4.858353] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    4.860712] IR Sony protocol handler initialized
[    4.863581] IR MCE Keyboard/mouse protocol handler initialized
[    4.867453] lirc_dev: IR Remote Control driver registered, major 249
[    4.867543] Registered IR keymap rc-imon-pad
[    4.867627] input: iMON Remote (15c2:0038) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/rc/rc0/input4
[    4.867671] rc0: iMON Remote (15c2:0038) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/rc/rc0
[    4.869997] IR LIRC bridge handler initialized
[    4.871272] saa7164_downloadfirmware() no first image
[    4.871281] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[    4.877094] imon 2-1.3:1.0: iMON device (15c2:0038, intf0) on usb<2:4> initialized
[    4.877127] imon 2-1.3:1.1: iMON device (15c2:0038, intf1) on usb<2:4> initialized
[    4.877168] usbcore: registered new interface driver imon
[    4.897754] saa7164_downloadfirmware() firmware read 4019072 bytes.
[    4.897756] saa7164_downloadfirmware() firmware loaded.
[    4.897757] Firmware file header part 1:
[    4.897759]  .FirmwareSize = 0x0
[    4.897760]  .BSLSize = 0x0
[    4.897761]  .Reserved = 0x3d538
[    4.897762]  .Version = 0x3
[    4.897763] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[    4.897769] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[    4.897770] saa7164_downloadfirmware() BSLSize = 0x0
[    4.897771] saa7164_downloadfirmware() Reserved = 0x0
[    4.897773] saa7164_downloadfirmware() Version = 0x1661c00
[    4.899993] hda_codec: ALC889: BIOS auto-probing.
[    4.906796] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    4.906857] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    4.906909] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    4.906958] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    4.907006] input: HDA Intel PCH Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.907206] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.907208] hda_intel: Disabling MSI
[    4.907236] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[    4.910586] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    4.983791] r8169 0000:04:00.0: eth0: link down
[    4.983797] r8169 0000:04:00.0: eth0: link down
[    4.984030] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.740649] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.764580] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.788522] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.812452] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    5.812557] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    5.812622] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    5.812665] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    5.812706] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    6.577763] r8169 0000:04:00.0: eth0: link up
[    6.577974] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    7.173365] init: failsafe main process (870) killed by TERM signal
[    7.201288] type=1400 audit(1370769760.440:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1159 comm="apparmor_parser"
[    7.201461] type=1400 audit(1370769760.440:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1157 comm="apparmor_parser"
[    7.202508] type=1400 audit(1370769760.440:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1157 comm="apparmor_parser"
[    7.202675] type=1400 audit(1370769760.440:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1157 comm="apparmor_parser"
[    7.202945] type=1400 audit(1370769760.440:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1156 comm="apparmor_parser"
[    7.202954] type=1400 audit(1370769760.440:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1160 comm="apparmor_parser"
[    7.203815] type=1400 audit(1370769760.440:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1162 comm="apparmor_parser"
[    7.237772] imon 2-1.3:1.0: Looks like you're trying to use an IR protocol this device does not support
[    7.237774] imon 2-1.3:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[    7.251660] type=1400 audit(1370769760.488:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1254 comm="apparmor_parser"
[   11.731524] saa7164_downloadimage() Image downloaded, booting...
[   11.835204] saa7164_downloadimage() Image booted successfully.
[   11.835222] starting firmware download(2)
[   13.873333] saa7164_downloadimage() Image downloaded, booting...
[   15.532566] saa7164_downloadimage() Image booted successfully.
[   15.532584] firmware download complete.
[   15.576868] tveeprom 0-0000: Hauppauge model 89619, rev D3F2, serial# 8420621
[   15.576871] tveeprom 0-0000: MAC address is 00:0d:fe:80:7d:0d
[   15.576872] tveeprom 0-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   15.576874] tveeprom 0-0000: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   15.576875] tveeprom 0-0000: audio processor is SAA7164 (idx 43)
[   15.576877] tveeprom 0-0000: decoder processor is SAA7164 (idx 40)
[   15.576878] tveeprom 0-0000: has radio
[   15.576879] saa7164[0]: Hauppauge eeprom: model=89619
[   15.629621] tda18271 1-0060: creating new instance
[   15.634212] TDA18271HD/C2 detected @ 1-0060
[   15.885161] DVB: registering new adapter (saa7164)
[   15.885164] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   15.915533] tda18271 2-0060: creating new instance
[   15.919858] TDA18271HD/C2 detected @ 2-0060
[   16.171402] tda18271: performing RF tracking filter calibration
[   17.494908] eth0: no IPv6 routers present
[   18.509591] tda18271: RF tracking filter calibration complete
[   18.510092] DVB: registering new adapter (saa7164)
[   18.510095] DVB: registering adapter 1 frontend 0 (NXP TDA10048HN DVB-T)...
[   18.510520] saa7164[0]: registered device video0 [mpeg]
[   18.741034] saa7164[0]: registered device video1 [mpeg]
[   18.951392] saa7164[0]: registered device vbi0 [vbi]
[   18.951442] saa7164[0]: registered device vbi1 [vbi]
[   18.953330] saa7164 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.954183] CORE saa7164[1]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[   18.954187] saa7164[1]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   18.954192] saa7164 0000:03:00.0: setting latency timer to 64
[   19.110302] saa7164_downloadfirmware() no first image
[   19.110315] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   19.114573] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   19.114576] saa7164_downloadfirmware() firmware loaded.
[   19.114577] Firmware file header part 1:
[   19.114578]  .FirmwareSize = 0x0
[   19.114579]  .BSLSize = 0x0
[   19.114580]  .Reserved = 0x3d538
[   19.114581]  .Version = 0x3
[   19.114582] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   19.114589] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   19.114590] saa7164_downloadfirmware() BSLSize = 0x0
[   19.114591] saa7164_downloadfirmware() Reserved = 0x0
[   19.114593] saa7164_downloadfirmware() Version = 0x1661c00
[   25.950603] saa7164_downloadimage() Image downloaded, booting...
[   26.054300] saa7164_downloadimage() Image booted successfully.
[   26.054318] starting firmware download(2)
[   27.988764] saa7164_downloadimage() Image downloaded, booting...
[   29.647996] saa7164_downloadimage() Image booted successfully.
[   29.648013] firmware download complete.
[   29.696364] tveeprom 3-0000: Hauppauge model 89619, rev D3F2, serial# 7937320
[   29.696366] tveeprom 3-0000: MAC address is 00:0d:fe:79:1d:28
[   29.696368] tveeprom 3-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   29.696369] tveeprom 3-0000: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   29.696371] tveeprom 3-0000: audio processor is SAA7164 (idx 43)
[   29.696372] tveeprom 3-0000: decoder processor is SAA7164 (idx 40)
[   29.696373] tveeprom 3-0000: has radio
[   29.696374] saa7164[1]: Hauppauge eeprom: model=89619
[   29.747872] tda18271 4-0060: creating new instance
[   29.752463] TDA18271HD/C2 detected @ 4-0060
[   30.004555] DVB: registering new adapter (saa7164)
[   30.004558] DVB: registering adapter 2 frontend 0 (NXP TDA10048HN DVB-T)...
[   30.035281] tda18271 5-0060: creating new instance
[   30.039977] TDA18271HD/C2 detected @ 5-0060
[   30.290729] tda18271: performing RF tracking filter calibration
[   32.629187] tda18271: RF tracking filter calibration complete
[   32.629690] DVB: registering new adapter (saa7164)
[   32.629693] DVB: registering adapter 3 frontend 0 (NXP TDA10048HN DVB-T)...
[   32.629992] saa7164[1]: registered device video2 [mpeg]
[   32.860395] saa7164[1]: registered device video3 [mpeg]
[   33.070218] saa7164[1]: registered device vbi2 [vbi]
[   33.070261] saa7164[1]: registered device vbi3 [vbi]
[   33.180967] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   33.180970] vesafb: scrolling: redraw
[   33.180972] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   33.180980] mtrr: type mismatch for ef000000,200000 old: write-back new: write-combining
[   33.180983] mtrr: type mismatch for ef000000,100000 old: write-back new: write-combining
[   33.180985] mtrr: type mismatch for ef000000,80000 old: write-back new: write-combining
[   33.180987] mtrr: type mismatch for ef000000,40000 old: write-back new: write-combining
[   33.180990] mtrr: type mismatch for ef000000,20000 old: write-back new: write-combining
[   33.180992] mtrr: type mismatch for ef000000,10000 old: write-back new: write-combining
[   33.180995] mtrr: type mismatch for ef000000,8000 old: write-back new: write-combining
[   33.180997] mtrr: type mismatch for ef000000,4000 old: write-back new: write-combining
[   33.180999] mtrr: type mismatch for ef000000,2000 old: write-back new: write-combining
[   33.181002] mtrr: type mismatch for ef000000,1000 old: write-back new: write-combining
[   33.181187] vesafb: framebuffer at 0xef000000, mapped to 0xffffc90006980000, using 1216k, total 1216k
[   33.181434] Console: switching to colour frame buffer device 80x30
[   33.181445] fb0: VESA VGA frame buffer device
[   33.197385] init: plymouth-splash main process (1933) terminated with status 1
[   33.384215] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   33.385213] tda10048_firmware_upload: firmware read 24878 bytes.
[   33.385215] tda10048_firmware_upload: firmware uploading
[   33.792191] NVRM: Your system is not currently configured to drive a VGA console
[   33.792194] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   33.792195] NVRM: requires the use of a text-mode VGA console. Use of other console
[   33.792196] NVRM: drivers including, but not limited to, vesafb, may result in
[   33.792198] NVRM: corruption and stability problems, and is not supported.
[   33.872793] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[   33.879778] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[   33.890926] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[   33.895735] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[   34.669537] HDMI: detected monitor SONY TV XV
[   34.669540]    at connection type HDMI
[   34.669543] HDMI: available speakers: FL/FR
[   34.669548] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
[   36.458635] tda10048_firmware_upload: firmware uploaded
[   36.513983] tda18271: performing RF tracking filter calibration
[   38.855234] tda18271: RF tracking filter calibration complete
[   39.090698] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   39.091769] tda10048_firmware_upload: firmware read 24878 bytes.
[   39.091771] tda10048_firmware_upload: firmware uploading
[   42.046584] tda10048_firmware_upload: firmware uploaded
[   42.322409] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   42.323455] tda10048_firmware_upload: firmware read 24878 bytes.
[   42.323457] tda10048_firmware_upload: firmware uploading
[   45.273438] tda10048_firmware_upload: firmware uploaded
[   45.326844] tda18271: performing RF tracking filter calibration
[   47.677656] tda18271: RF tracking filter calibration complete
[   47.897358] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   47.898418] tda10048_firmware_upload: firmware read 24878 bytes.
[   47.898420] tda10048_firmware_upload: firmware uploading
[   50.853609] tda10048_firmware_upload: firmware uploaded
[   51.158855] tda18271: performing RF tracking filter calibration
[   53.504951] tda18271: RF tracking filter calibration complete




[/COLOR]
```

---

### Post by 2F4U on 2013-06-09
Your hardware should not be the problem. I am thinking about whether your SSD is configured for optimal performance. Which scheduler do you use on the SSD? For a good discussion on SSD performance see here:

[http://ubuntuforums.org/showthread.php?t=2082182](http://ubuntuforums.org/showthread.php?t=2082182)

---

### Post by alien878 on 2013-06-10
Scanning your log, it seems a lot (most?) of the time seems to be spent uploading firmware to the two DVB-T cards.  You might want to do a web search to see if this is necessary and if there is a way to stop it from happening every boot.

---

### Post by BicyclerBoy on 2013-06-10
A core2duo with SSD & one dvb-t card boots in 29sec

There is something very wrong with the firmware loading &/or dvb driver..
My experience is that the f/w should only take 0.5 sec to load.

With a sandybridge mobo etc I would be running a more recent kernel but can't see that having any bearing on this problem..
Unless there is some kernel power governor regression & the CPU is slowing down to lowest idle (ice age slow)..

---

### Post by mickaus on 2013-06-10
The schedular I have running is:

michael@michael-Z68MA-D2H-B3:~$ cat /sys/block/sda/queue/scheduler
[noop] deadline cfq

Is this OK?

---

### Post by mickaus on 2013-06-10
> **alien878 said:**
> Scanning your log, it seems a lot (most?) of the time seems to be spent uploading firmware to the two DVB-T cards.  You might want to do a web search to see if this is necessary and if there is a way to stop it from happening every boot.

I havent had much luck finding any info on this problem - maybe I need to try a fresh mythbuntu install to see if there is any difference?

---

