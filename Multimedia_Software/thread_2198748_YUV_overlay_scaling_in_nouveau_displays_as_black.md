---
title: "YUV overlay scaling in nouveau displays as black"
date: 2014-01-10
forum: Multimedia Software
---

### Post by fbs777 on 2014-01-10
For many years im using ubuntu (since nouveau becomes the default nvidia driver) and never have problem with the YUV overlay scaling (yuy2 scalemode in mame option), so i think there's a regression with nouveau version in ubuntu 13.10.

I cant get video when open mame with "-video soft -sm yuy2" options using the nouveau driver. The game runs with sound, but in full black screen.
Using "-video soft -sm none" the game runs with video, the problem is with YUV overlay scaling.

Tested with Ubuntu 13.10 (kernels 3.11 and 3.12 from ubuntu repos.), mame .151 and .152, nouveau driver.

Tested the same hd in a motherboard with intel graphics and the yuy2 overlay works fine.

To reproduce (dont need any rom): execute the mame (mamedev.org) with the command line "./mame -video soft -sm yuy2" and mame will open totally in black screen. With the command "./mame -video soft -sm none" will open normally (in this case with a red bar warning about no roms).


kernel_log:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.12.0-031200-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201311031935 SMP Mon Nov 4 00:46:34 UTC 2013
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfedffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfee0000-0x00000000bfee2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfee3000-0x00000000bfeeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. P35-DS3/P35-DS3, BIOS F10 11/16/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbfee0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   2 base 0BFF00000 mask FFFF00000 write-through
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f5250-0x000f525f] mapped at [c00f5250]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01bbc000, 0x01bbcfff] PGTABLE
[    0.000000] log_buf_len: 1048576
[    0.000000] early log buf free: 127528(97%)
[    0.000000] RAMDISK: [mem 0x35f3c000-0x36f95fff]
[    0.000000] ACPI: RSDP 000f6c30 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT bfee3040 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP bfee30c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT bfee3180 04B32 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS bfee0000 00040
[    0.000000] ACPI: HPET bfee7e00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG bfee7e80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC bfee7d00 00084 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: SSDT bfee7f00 0015C (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.000000] ACPI: SSDT bfee8390 00275 (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2178MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01bbd000, 0x01bbdfff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbfedffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xbfedffff]
[    0.000000] On node 0 totalpages: 786046
[    0.000000] free_area_init_node: node 0, pgdat c19c87c0, node_mem_map f473c020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4358 pages used for memmap
[    0.000000]   HighMem zone: 557794 pages, LIFO batch:31
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
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] e820: [mem 0xbff00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7ab4000 s35968 r0 d21376 u57344
[    0.000000] pcpu-alloc: s35968 r0 d21376 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 784262
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.0-031200-generic root=LABEL=maq ro log_buf_len=1M quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6289144 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfee0)
[    0.000000] Memory: 3082504K/3144184K available (6666K kernel code, 633K rwdata, 2824K rodata, 868K init, 908K bss, 61680K reserved, 2231176K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc19e6000 - 0xc1abf000   ( 868 kB)
[    0.000000]       .data : 0xc1682f27 - 0xc19e5440   (3465 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1682f27   (6667 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2666.701 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.40 BogoMIPS (lpj=10666804)
[    0.004005] pid_max: default: 32768 minimum: 301
[    0.004030] Security Framework initialized
[    0.004047] AppArmor: AppArmor initialized
[    0.004048] Yama: becoming mindful.
[    0.004092] Mount-cache hash table entries: 512
[    0.004307] Initializing cgroup subsys memory
[    0.004319] Initializing cgroup subsys devices
[    0.004322] Initializing cgroup subsys freezer
[    0.004324] Initializing cgroup subsys blkio
[    0.004327] Initializing cgroup subsys perf_event
[    0.004329] Initializing cgroup subsys hugetlb
[    0.004356] CPU: Physical Processor ID: 0
[    0.004357] CPU: Processor Core ID: 0
[    0.004361] mce: CPU supports 6 MCE banks
[    0.004368] CPU0: Thermal monitoring enabled (TM2)
[    0.004378] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004378] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004378] tlb_flushall_shift: -1
[    0.004634] Freeing SMP alternatives memory: 32K (c1abf000 - c1ac7000)
[    0.008866] ACPI: Core revision 20130725
[    0.011000] ACPI: All ACPI Tables successfully acquired
[    0.012024] ftrace: allocating 30272 entries in 60 pages
[    0.020075] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020428] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062073] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz (fam: 06, model: 0f, stepping: 0b)
[    0.064000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.064000] perf_event_intel: PEBS disabled due to CPU errata
[    0.064000] ... version:                2
[    0.064000] ... bit width:              40
[    0.064000] ... generic registers:      2
[    0.064000] ... value mask:             000000ffffffffff
[    0.064000] ... max period:             000000007fffffff
[    0.064000] ... fixed-purpose events:   3
[    0.064000] ... event mask:             0000000700000003
[    0.064000] CPU 1 irqstacks, hard=f40f2000 soft=f40f4000
[    0.064000] smpboot: Booting Node   0, Processors  #   1 OK
[    0.008000] Initializing CPU#1
[    0.076035] Brought up 2 CPUs
[    0.076039] smpboot: Total of 2 processors activated (10666.80 BogoMIPS)
[    0.076126] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.080076] devtmpfs: initialized
[    0.080235] EVM: security.selinux
[    0.080237] EVM: security.SMACK64
[    0.080238] EVM: security.capability
[    0.080250] PM: Registering ACPI NVS region [mem 0xbfee0000-0xbfee2fff] (12288 bytes)
[    0.080496] pinctrl core: initialized pinctrl subsystem
[    0.080565] regulator-dummy: no parameters
[    0.080592] RTC time: 23:02:24, date: 01/06/14
[    0.080632] NET: Registered protocol family 16
[    0.080793] EISA bus registered
[    0.080795] cpuidle: using governor ladder
[    0.080796] cpuidle: using governor menu
[    0.080879] ACPI: bus type PCI registered
[    0.080882] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.080934] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.080937] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.080938] PCI: Using MMCONFIG for extended config space
[    0.080939] PCI: Using configuration type 1 for base access
[    0.081953] bio: create slab <bio-0> at 0
[    0.081953] ACPI: Added _OSI(Module Device)
[    0.081953] ACPI: Added _OSI(Processor Device)
[    0.081953] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.081953] ACPI: Added _OSI(Processor Aggregator Device)
[    0.081953] ACPI: EC: Look up EC in DSDT
[    0.086329] ACPI: SSDT bfee8300 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.086504] ACPI: Dynamic OEM Table Load:
[    0.086507] ACPI: SSDT   (null) 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.086653] ACPI: Interpreter enabled
[    0.086672] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130725/hwxface-571)
[    0.086677] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130725/hwxface-571)
[    0.086690] ACPI: (supports S0 S3 S4 S5)
[    0.086692] ACPI: Using IOAPIC for interrupt routing
[    0.086723] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.086849] ACPI: No dock devices found.
[    0.092312] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.092318] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.092320] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.092388] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.092390] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.092392] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.092395] acpi PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.092397] acpi PNP0A03:00: host bridge window [mem 0xbff00000-0xfebfffff] (ignored)
[    0.092399] PCI: root bus 00: using default resources
[    0.092587] ACPI: \_SB_.PCI0.LNKA: can't evaluate _ADR (0x5)
[    0.092590] ACPI: \_SB_.PCI0.LNKB: can't evaluate _ADR (0x5)
[    0.092592] ACPI: \_SB_.PCI0.LNKC: can't evaluate _ADR (0x5)
[    0.092595] ACPI: \_SB_.PCI0.LNKD: can't evaluate _ADR (0x5)
[    0.092597] ACPI: \_SB_.PCI0.LNKE: can't evaluate _ADR (0x5)
[    0.092599] ACPI: \_SB_.PCI0.LNKF: can't evaluate _ADR (0x5)
[    0.092601] ACPI: \_SB_.PCI0.LNK0: can't evaluate _ADR (0x5)
[    0.092604] ACPI: \_SB_.PCI0.LNK1: can't evaluate _ADR (0x5)
[    0.092606] ACPI: \_SB_.PCI0.EXPL: can't evaluate _ADR (0x5)
[    0.092608] PCI host bridge to bus 0000:00
[    0.092610] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.092613] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.092615] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.092624] pci 0000:00:00.0: [8086:29c0] type 00 class 0x060000
[    0.092725] pci 0000:00:01.0: [8086:29c1] type 01 class 0x060400
[    0.092762] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.092860] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.092899] pci 0000:00:1a.0: reg 0x20: [io  0xe100-0xe11f]
[    0.092983] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.093019] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.093057] pci 0000:00:1a.1: reg 0x20: [io  0xe200-0xe21f]
[    0.093140] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.093175] pci 0000:00:1a.2: [8086:2939] type 00 class 0x0c0300
[    0.093213] pci 0000:00:1a.2: reg 0x20: [io  0xe000-0xe01f]
[    0.093296] pci 0000:00:1a.2: System wakeup disabled by ACPI
[    0.093334] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.093350] pci 0000:00:1a.7: reg 0x10: [mem 0xea104000-0xea1043ff]
[    0.093464] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.093503] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.093517] pci 0000:00:1b.0: reg 0x10: [mem 0xea100000-0xea103fff 64bit]
[    0.093578] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.093633] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.093669] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.093731] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.093787] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.093824] pci 0000:00:1c.3: [8086:2946] type 01 class 0x060400
[    0.093886] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.093942] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.093978] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.094040] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.094100] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.094139] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.094177] pci 0000:00:1d.0: reg 0x20: [io  0xe300-0xe31f]
[    0.094260] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.094294] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.094332] pci 0000:00:1d.1: reg 0x20: [io  0xe400-0xe41f]
[    0.094415] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.094451] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.094489] pci 0000:00:1d.2: reg 0x20: [io  0xe500-0xe51f]
[    0.094571] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.094611] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.094627] pci 0000:00:1d.7: reg 0x10: [mem 0xea105000-0xea1053ff]
[    0.094741] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.094776] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.094867] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.094904] pci 0000:00:1f.0: [8086:2918] type 00 class 0x060100
[    0.094976] pci 0000:00:1f.0: address space collision: [io  0x0400-0x047f] conflicts with ACPI CPU throttle [??? 0x00000410-0x00000415 flags 0x80000000]
[    0.094982] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.094985] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.094989] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.095092] pci 0000:00:1f.2: [8086:2921] type 00 class 0x01018a
[    0.095107] pci 0000:00:1f.2: reg 0x10: [io  0x0000-0x0007]
[    0.095114] pci 0000:00:1f.2: reg 0x14: [io  0x0000-0x0003]
[    0.095121] pci 0000:00:1f.2: reg 0x18: [io  0x0000-0x0007]
[    0.095128] pci 0000:00:1f.2: reg 0x1c: [io  0x0000-0x0003]
[    0.095136] pci 0000:00:1f.2: reg 0x20: [io  0xf000-0xf00f]
[    0.095143] pci 0000:00:1f.2: reg 0x24: [io  0xfc00-0xfc0f]
[    0.095247] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.095261] pci 0000:00:1f.3: reg 0x10: [mem 0xea106000-0xea1060ff 64bit]
[    0.095279] pci 0000:00:1f.3: reg 0x20: [io  0x0500-0x051f]
[    0.095371] pci 0000:00:1f.5: [8086:2926] type 00 class 0x010185
[    0.095385] pci 0000:00:1f.5: reg 0x10: [io  0xe700-0xe707]
[    0.095392] pci 0000:00:1f.5: reg 0x14: [io  0xe800-0xe803]
[    0.095399] pci 0000:00:1f.5: reg 0x18: [io  0xe900-0xe907]
[    0.095406] pci 0000:00:1f.5: reg 0x1c: [io  0xea00-0xea03]
[    0.095414] pci 0000:00:1f.5: reg 0x20: [io  0xeb00-0xeb0f]
[    0.095421] pci 0000:00:1f.5: reg 0x24: [io  0xec00-0xec0f]
[    0.095571] pci 0000:01:00.0: [10de:0421] type 00 class 0x030000
[    0.095581] pci 0000:01:00.0: reg 0x10: [mem 0xe6000000-0xe6ffffff]
[    0.095591] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.095601] pci 0000:01:00.0: reg 0x1c: [mem 0xe4000000-0xe5ffffff 64bit]
[    0.095608] pci 0000:01:00.0: reg 0x24: [io  0xb000-0xb07f]
[    0.095615] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.095686] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.095689] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.095692] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe7ffffff]
[    0.095696] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.095745] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.095749] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.095843] pci 0000:03:00.0: [197b:2363] type 00 class 0x010185
[    0.095926] pci 0000:03:00.0: reg 0x24: [mem 0xea000000-0xea001fff]
[    0.095987] pci 0000:03:00.0: PME# supported from D3hot
[    0.096050] pci 0000:03:00.1: [197b:2363] type 00 class 0x010185
[    0.096070] pci 0000:03:00.1: reg 0x10: [io  0xc000-0xc007]
[    0.096080] pci 0000:03:00.1: reg 0x14: [io  0xc100-0xc103]
[    0.096090] pci 0000:03:00.1: reg 0x18: [io  0xc200-0xc207]
[    0.096100] pci 0000:03:00.1: reg 0x1c: [io  0xc300-0xc303]
[    0.096110] pci 0000:03:00.1: reg 0x20: [io  0xc400-0xc40f]
[    0.096211] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.096220] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.096224] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.096228] pci 0000:00:1c.3:   bridge window [mem 0xea000000-0xea0fffff]
[    0.096304] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.096322] pci 0000:04:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.096352] pci 0000:04:00.0: reg 0x18: [mem 0xe9000000-0xe9000fff 64bit]
[    0.096386] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.096463] pci 0000:04:00.0: supports D1 D2
[    0.096465] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.096511] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.096521] pci 0000:00:1c.4: PCI bridge to [bus 04]
[    0.096524] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.096528] pci 0000:00:1c.4:   bridge window [mem 0xe8000000-0xe9ffffff]
[    0.096601] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
[    0.096604] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.096611] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.096613] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.096637] pci_bus 0000:00: on NUMA node 0
[    0.097155] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.097217] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.097278] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.097337] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.097396] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.097457] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.097516] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.097575] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.097677] ACPI: Enabled 1 GPEs in block 00 to 3F
[    0.097683] ACPI: \_SB_.PCI0: notify handler is installed
[    0.097721] Found 1 acpi root devices
[    0.097800] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.097800] vgaarb: loaded
[    0.097800] vgaarb: bridge control possible 0000:01:00.0
[    0.097800] SCSI subsystem initialized
[    0.097800] libata version 3.00 loaded.
[    0.097800] ACPI: bus type USB registered
[    0.097800] usbcore: registered new interface driver usbfs
[    0.097800] usbcore: registered new interface driver hub
[    0.097800] usbcore: registered new device driver usb
[    0.097800] PCI: Using ACPI for IRQ routing
[    0.100480] PCI: pci_cache_line_size set to 64 bytes
[    0.100535] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.100537] e820: reserve RAM buffer [mem 0xbfee0000-0xbfffffff]
[    0.100630] NetLabel: Initializing
[    0.100631] NetLabel:  domain hash size = 128
[    0.100632] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.100642] NetLabel:  unlabeled traffic allowed by default
[    0.100653] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.100653] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.100653] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.102119] Switched to clocksource hpet
[    0.106928] AppArmor: AppArmor Filesystem Enabled
[    0.106953] pnp: PnP ACPI init
[    0.106967] ACPI: bus type PNP registered
[    0.107135] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.107140] system 00:00: [io  0x0290-0x029f] has been reserved
[    0.107142] system 00:00: [io  0x0800-0x087f] has been reserved
[    0.107145] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.107147] system 00:00: [io  0x0880-0x088f] has been reserved
[    0.107151] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.107163] pnp 00:01: [dma 4]
[    0.107185] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.107263] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.107309] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.107336] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.107367] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.107620] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.107819] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.107954] system 00:08: [io  0x0400-0x04bf] could not be reserved
[    0.107958] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.108184] system 00:09: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.108187] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.108375] system 00:0a: [mem 0x000cca00-0x000cffff] has been reserved
[    0.108378] system 00:0a: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.108381] system 00:0a: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.108383] system 00:0a: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.108386] system 00:0a: [mem 0xbfee0000-0xbfefffff] could not be reserved
[    0.108388] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.108391] system 00:0a: [mem 0x00100000-0xbfedffff] could not be reserved
[    0.108394] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.108396] system 00:0a: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.108399] system 00:0a: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.108401] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.108404] system 00:0a: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.108406] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.108409] system 00:0a: [mem 0x000e0000-0x000effff] has been reserved
[    0.108412] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.108453] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.108458] pnp: PnP ACPI: found 12 devices
[    0.108460] ACPI: bus type PNP unregistered
[    0.108464] PnPBIOS: Disabled by ACPI PNP
[    0.144856] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.144859] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.144868] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.144876] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x001fffff pref] to [bus 04] add_size 200000
[    0.144886] pci 0000:00:1f.0: BAR 13: [io  0x0400-0x047f] has bogus alignment
[    0.144889] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.144892] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.144894] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.144897] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x001fffff pref] get_res_add_size add_size 200000
[    0.144902] pci 0000:00:1c.0: BAR 14: assigned [mem 0xea200000-0xea3fffff]
[    0.144906] pci 0000:00:1c.0: BAR 15: assigned [mem 0xea400000-0xea5fffff 64bit pref]
[    0.144909] pci 0000:00:1c.3: BAR 15: assigned [mem 0xea600000-0xea7fffff 64bit pref]
[    0.144912] pci 0000:00:1c.4: BAR 15: assigned [mem 0xea800000-0xeaafffff pref]
[    0.144916] pci 0000:01:00.0: BAR 6: assigned [mem 0xe7000000-0xe701ffff pref]
[    0.144919] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.144921] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.144925] pci 0000:00:01.0:   bridge window [mem 0xe4000000-0xe7ffffff]
[    0.144928] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.144932] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.144935] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.144939] pci 0000:00:1c.0:   bridge window [mem 0xea200000-0xea3fffff]
[    0.144943] pci 0000:00:1c.0:   bridge window [mem 0xea400000-0xea5fffff 64bit pref]
[    0.144948] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.144951] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.144955] pci 0000:00:1c.3:   bridge window [mem 0xea000000-0xea0fffff]
[    0.144959] pci 0000:00:1c.3:   bridge window [mem 0xea600000-0xea7fffff 64bit pref]
[    0.144965] pci 0000:04:00.0: BAR 6: assigned [mem 0xea800000-0xea80ffff pref]
[    0.144967] pci 0000:00:1c.4: PCI bridge to [bus 04]
[    0.144970] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.144974] pci 0000:00:1c.4:   bridge window [mem 0xe8000000-0xe9ffffff]
[    0.144978] pci 0000:00:1c.4:   bridge window [mem 0xea800000-0xeaafffff pref]
[    0.144983] pci 0000:00:1e.0: PCI bridge to [bus 05]
[    0.144986] pci 0000:00:1e.0:   bridge window [io  0xa000-0xafff]
[    0.144995] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.144998] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.145000] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.145002] pci_bus 0000:01: resource 1 [mem 0xe4000000-0xe7ffffff]
[    0.145005] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.145007] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.145009] pci_bus 0000:02: resource 1 [mem 0xea200000-0xea3fffff]
[    0.145011] pci_bus 0000:02: resource 2 [mem 0xea400000-0xea5fffff 64bit pref]
[    0.145013] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.145016] pci_bus 0000:03: resource 1 [mem 0xea000000-0xea0fffff]
[    0.145018] pci_bus 0000:03: resource 2 [mem 0xea600000-0xea7fffff 64bit pref]
[    0.145020] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.145022] pci_bus 0000:04: resource 1 [mem 0xe8000000-0xe9ffffff]
[    0.145024] pci_bus 0000:04: resource 2 [mem 0xea800000-0xeaafffff pref]
[    0.145026] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.145029] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
[    0.145031] pci_bus 0000:05: resource 5 [mem 0x00000000-0xfffffffff]
[    0.145061] NET: Registered protocol family 2
[    0.145207] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.145235] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.145262] TCP: Hash tables configured (established 8192 bind 8192)
[    0.145284] TCP: reno registered
[    0.145287] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.145295] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.145349] NET: Registered protocol family 1
[    0.146408] pci 0000:01:00.0: Boot video device
[    0.146418] PCI: CLS 32 bytes, default 64
[    0.146453] Trying to unpack rootfs image as initramfs...
[    0.450646] Freeing initrd memory: 16744K (f5f3c000 - f6f96000)
[    0.450869] Scanning for low memory corruption every 60 seconds
[    0.451221] Initialise module verification
[    0.451267] audit: initializing netlink socket (disabled)
[    0.451281] type=2000 audit(1389049343.448:1): initialized
[    0.473078] bounce pool size: 64 pages
[    0.473089] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.474492] zbud: loaded
[    0.474536] VFS: Disk quotas dquot_6.5.2
[    0.474581] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.475076] fuse init (API version 7.22)
[    0.475155] msgmni has been set to 1695
[    0.475569] Key type asymmetric registered
[    0.475571] Asymmetric key parser 'x509' registered
[    0.475604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.475633] io scheduler noop registered
[    0.475635] io scheduler deadline registered (default)
[    0.475663] io scheduler cfq registered
[    0.475870] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.475983] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.476122] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.476243] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.476314] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.476329] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.476403] intel_idle: does not run on family 6 model 15
[    0.476469] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.476474] ACPI: Power Button [PWRB]
[    0.476520] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.476522] ACPI: Power Button [PWRF]
[    0.476574] ACPI: Requesting acpi_cpufreq
[    0.477758] GHES: HEST is not enabled!
[    0.477772] isapnp: Scanning for PnP cards...
[    0.830606] isapnp: No Plug & Play device found
[    0.830678] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.851062] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.852441] Linux agpgart interface v0.103
[    0.853867] brd: module loaded
[    0.854548] loop: module loaded
[    0.854654] ata_piix 0000:00:1f.2: version 2.13
[    0.854728] ata_piix 0000:00:1f.2: MAP [
[    0.854730]  P0 -- P1 -- ]
[    0.854767] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.855249] scsi0 : ata_piix
[    0.855313] scsi1 : ata_piix
[    0.855349] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.855352] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.855439] ata_piix 0000:00:1f.5: MAP [
[    0.855440]  P0 -- P1 -- ]
[    0.855472] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.855931] scsi2 : ata_piix
[    0.855985] scsi3 : ata_piix
[    0.856032] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    0.856035] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    0.856326] libphy: Fixed MDIO Bus: probed
[    0.856421] tun: Universal TUN/TAP device driver, 1.6
[    0.856423] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.856467] PPP generic driver version 2.4.2
[    0.856504] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.856508] ehci-pci: EHCI PCI platform driver
[    0.856591] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.856601] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.856606] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.860523] ehci-pci 0000:00:1a.7: cache line size of 32 is not supported
[    0.860536] ehci-pci 0000:00:1a.7: irq 18, io mem 0xea104000
[    0.872025] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.872079] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.872082] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.872085] usb usb1: Product: EHCI Host Controller
[    0.872088] usb usb1: Manufacturer: Linux 3.12.0-031200-generic ehci_hcd
[    0.872091] usb usb1: SerialNumber: 0000:00:1a.7
[    0.872218] hub 1-0:1.0: USB hub found
[    0.872226] hub 1-0:1.0: 6 ports detected
[    0.872435] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.872443] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.872448] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.876361] ehci-pci 0000:00:1d.7: cache line size of 32 is not supported
[    0.876374] ehci-pci 0000:00:1d.7: irq 23, io mem 0xea105000
[    0.888021] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.888079] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.888082] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888085] usb usb2: Product: EHCI Host Controller
[    0.888087] usb usb2: Manufacturer: Linux 3.12.0-031200-generic ehci_hcd
[    0.888090] usb usb2: SerialNumber: 0000:00:1d.7
[    0.888206] hub 2-0:1.0: USB hub found
[    0.888213] hub 2-0:1.0: 6 ports detected
[    0.888348] ehci-platform: EHCI generic platform driver
[    0.888356] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.888357] ohci-platform: OHCI generic platform driver
[    0.888366] uhci_hcd: USB Universal Host Controller Interface driver
[    0.888443] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.888447] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.888451] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.888480] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[    0.888522] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.888525] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888527] usb usb3: Product: UHCI Host Controller
[    0.888529] usb usb3: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.888531] usb usb3: SerialNumber: 0000:00:1a.0
[    0.888618] hub 3-0:1.0: USB hub found
[    0.888625] hub 3-0:1.0: 2 ports detected
[    0.888771] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.888774] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.888778] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.888806] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[    0.888847] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.888850] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.888852] usb usb4: Product: UHCI Host Controller
[    0.888854] usb usb4: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.888856] usb usb4: SerialNumber: 0000:00:1a.1
[    0.888944] hub 4-0:1.0: USB hub found
[    0.888951] hub 4-0:1.0: 2 ports detected
[    0.889094] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.889097] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.889102] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.889122] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[    0.889164] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.889166] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.889168] usb usb5: Product: UHCI Host Controller
[    0.889170] usb usb5: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.889172] usb usb5: SerialNumber: 0000:00:1a.2
[    0.889259] hub 5-0:1.0: USB hub found
[    0.889266] hub 5-0:1.0: 2 ports detected
[    0.889412] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.889415] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.889419] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.889439] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    0.889482] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.889484] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.889486] usb usb6: Product: UHCI Host Controller
[    0.889488] usb usb6: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.889490] usb usb6: SerialNumber: 0000:00:1d.0
[    0.889578] hub 6-0:1.0: USB hub found
[    0.889585] hub 6-0:1.0: 2 ports detected
[    0.889728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.889731] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.889736] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.889756] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    0.889798] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.889800] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.889802] usb usb7: Product: UHCI Host Controller
[    0.889804] usb usb7: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.889806] usb usb7: SerialNumber: 0000:00:1d.1
[    0.889891] hub 7-0:1.0: USB hub found
[    0.889899] hub 7-0:1.0: 2 ports detected
[    0.890044] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.890047] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.890051] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.890071] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[    0.890112] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.890114] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.890116] usb usb8: Product: UHCI Host Controller
[    0.890118] usb usb8: Manufacturer: Linux 3.12.0-031200-generic uhci_hcd
[    0.890120] usb usb8: SerialNumber: 0000:00:1d.2
[    0.890205] hub 8-0:1.0: USB hub found
[    0.890212] hub 8-0:1.0: 2 ports detected
[    0.890348] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.890731] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.890736] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.890841] mousedev: PS/2 mouse device common for all mice
[    0.890979] rtc_cmos 00:03: RTC can wake from S4
[    0.891085] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.891107] rtc_cmos 00:03: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.891170] device-mapper: uevent: version 1.0.3
[    0.891227] device-mapper: ioctl: 4.26.0-ioctl (2013-08-15) initialised: dm-devel@redhat.com
[    0.891247] platform eisa.0: Probing EISA bus 0
[    0.891265] platform eisa.0: EISA: Detected 0 cards
[    0.891272] cpufreq-nforce2: No nForce2 chipset.
[    0.891275] ledtrig-cpu: registered to indicate activity on CPUs
[    0.891361] TCP: cubic registered
[    0.891463] NET: Registered protocol family 10
[    0.891643] NET: Registered protocol family 17
[    0.891652] Key type dns_resolver registered
[    0.891813] Using IPI No-Shortcut mode
[    0.891900] Loading module verification certificates
[    0.895364] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e2ad0a7a71344e2d393b0265729ee0ec7e8a62e6'
[    0.895380] registered taskstats version 1
[    0.897482] Key type trusted registered
[    0.899269] Key type encrypted registered
[    0.901032] AppArmor: AppArmor sha1 policy hashing enabled
[    0.901334]   Magic number: 14:819:48
[    0.901407] rtc_cmos 00:03: setting system clock to 2014-01-06 23:02:24 UTC (1389049344)
[    0.901582] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.901584] EDD information not available.
[    0.901619] PM: Hibernation image not present or could not be loaded.
[    1.182605] ata2: SATA link down (SStatus 0 SControl 300)
[    1.193226] ata1: SATA link down (SStatus 0 SControl 300)
[    1.193228] ata3: SATA link down (SStatus 0 SControl 300)
[    1.203801] ata4: SATA link down (SStatus 0 SControl 300)
[    1.203809] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.204122] Freeing unused kernel memory: 868K (c19e6000 - c1abf000)
[    1.204160] Write protecting the kernel text: 6668k
[    1.204231] Write protecting the kernel read-only data: 2832k
[    1.204232] NX-protecting the kernel data: 5620k
[    1.215261] systemd-udevd[104]: starting version 204
[    1.251006] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.251016] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.251226] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.251392] r8169 0000:04:00.0 eth0: RTL8168b/8111b at 0xf840e000, 00:1d:7d:f6:01:5d, XID 18000000 IRQ 44
[    1.251395] r8169 0000:04:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.259750] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    1.259816] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.263287] scsi4 : pata_jmicron
[    1.266796] scsi5 : pata_jmicron
[    1.266841] ata5: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[    1.266843] ata6: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16
[    1.267582] ahci 0000:03:00.0: version 3.0
[    1.280048] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.280053] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.281769] scsi6 : ahci
[    1.283254] scsi7 : ahci
[    1.283301] ata7: SATA max UDMA/133 abar m8192@0xea000000 port 0xea000100 irq 19
[    1.283305] ata8: SATA max UDMA/133 abar m8192@0xea000000 port 0xea000180 irq 19
[    1.332919] usb 2-1: New USB device found, idVendor=0781, idProduct=5567
[    1.332923] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.332926] usb 2-1: Product: Cruzer Blade
[    1.332929] usb 2-1: Manufacturer: SanDisk
[    1.332931] usb 2-1: SerialNumber: 4C530002921010100333
[    1.450514] tsc: Refined TSC clocksource calibration: 2666.666 MHz
[    1.451285] usb-storage 2-1:1.0: USB Mass Storage device detected
[    1.451345] scsi8 : usb-storage 2-1:1.0
[    1.451405] usbcore: registered new interface driver usb-storage
[    1.600042] ata8: SATA link down (SStatus 0 SControl 300)
[    1.600074] ata7: SATA link down (SStatus 0 SControl 300)
[    1.684038] usb 8-1: new low-speed USB device number 2 using uhci_hcd
[    1.895103] usb 8-1: New USB device found, idVendor=1a2c, idProduct=0002
[    1.895107] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.895111] usb 8-1: Product: USB Keykoard
[    1.895113] usb 8-1: Manufacturer: USB
[    1.905443] hidraw: raw HID events driver (C) Jiri Kosina
[    1.936491] usbcore: registered new interface driver usbhid
[    1.936493] usbhid: USB HID core driver
[    1.940788] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4
[    1.940858] hid-generic 0003:1A2C:0002.0001: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1d.2-1/input0
[    1.941733] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input5
[    1.941799] hid-generic 0003:1A2C:0002.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1d.2-1/input1
[    2.136042] usb 8-2: new low-speed USB device number 3 using uhci_hcd
[    2.303102] usb 8-2: New USB device found, idVendor=062a, idProduct=0003
[    2.303106] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.303109] usb 8-2: Product: Optical Mouse
[    2.303111] usb 8-2: Manufacturer: MosArt
[    2.319814] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6
[    2.319900] hid-generic 0003:062A:0003.0003: input,hidraw2: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.448077] Switched to clocksource tsc
[    2.448567] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.26 PQ: 0 ANSI: 6
[    2.448836] sd 8:0:0:0: Attached scsi generic sg0 type 0
[    2.449804] sd 8:0:0:0: [sda] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[    2.451673] sd 8:0:0:0: [sda] Write Protect is off
[    2.451678] sd 8:0:0:0: [sda] Mode Sense: 43 00 00 00
[    2.452674] sd 8:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.460299]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.463799] sd 8:0:0:0: [sda] Attached SCSI disk
[    2.844827] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.844831] EXT4-fs (sda1): write access will be enabled during recovery
[    4.541070] EXT4-fs (sda1): recovery complete
[    4.546923] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.297562] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.496556] EXT4-fs (sda6): warning: mounting unchecked fs, running e2fsck is recommended
[    7.502995] EXT4-fs (sda6): mounted filesystem without journal. Opts: (null)
[    7.596378] systemd-udevd[294]: starting version 204
[    7.631182] EXT4-fs (sda7): recovery complete
[    7.631188] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    7.662304] init: flush-early-job-log main process (316) terminated with status 1
[    7.785143] parport_pc 00:07: reported by Plug and Play ACPI
[    7.785189] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.848941] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GP2C 1 (20130725/utaddress-251)
[    7.848948] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.848994] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    7.861547] lp: driver loaded but no devices found
[    7.885006] lp0: using parport0 (interrupt-driven).
[    7.890304] r8169 0000:04:00.0 eth0: link down
[    7.890318] r8169 0000:04:00.0 eth0: link down
[    7.890334] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.934943] microcode: CPU0 sig=0x6fb, pf=0x1, revision=0xb6
[    7.992160] microcode: CPU1 sig=0x6fb, pf=0x1, revision=0xb6
[    8.006801] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.009588] [drm] Initialized drm 1.1.0 20060810
[    8.015051] ppdev: user-space parallel port driver
[    8.036915] gpio_ich: GPIO from 195 to 255 on gpio_ich
[    8.123557] wmi: Mapper loaded
[    8.183177] coretemp coretemp.0: Using relative temperature scale!
[    8.183193] coretemp coretemp.0: Using relative temperature scale!
[    8.332812] [drm] hdmi device  not found 1 0 1
[    8.332890] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x086100a2
[    8.332893] nouveau  [  DEVICE][0000:01:00.0] Chipset: G86 (NV86)
[    8.332895] nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[    8.333703] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[    8.381478] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[    8.381484] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[    8.381629] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    8.381635] nouveau  [   VBIOS][0000:01:00.0] version 60.86.34.00.97
[    8.412206] nouveau  [     PFB][0000:01:00.0] RAM type: DDR2
[    8.412210] nouveau  [     PFB][0000:01:00.0] RAM size: 512 MiB
[    8.412212] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 1292 tags
[    8.445347] init: alsa-restore main process (536) terminated with status 19
[    8.446186] nouveau  [  PTHERM][0000:01:00.0] FAN control: PWM
[    8.446199] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[    8.446202] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    8.446224] nouveau E[  PTHERM][0000:01:00.0] unhandled intr 0x000000e1
[    8.447532] [TTM] Zone  kernel: Available graphics memory: 434486 kiB
[    8.447534] [TTM] Zone highmem: Available graphics memory: 1550074 kiB
[    8.447536] [TTM] Initializing pool allocator
[    8.447541] [TTM] Initializing DMA pool allocator
[    8.447550] nouveau  [     DRM] VRAM: 512 MiB
[    8.447552] nouveau  [     DRM] GART: 1048576 MiB
[    8.447557] nouveau  [     DRM] TMDS table version 2.0
[    8.447559] nouveau  [     DRM] DCB version 4.0
[    8.447561] nouveau  [     DRM] DCB outp 00: 02000300 00000028
[    8.447564] nouveau  [     DRM] DCB outp 01: 04011310 00000030
[    8.447566] nouveau  [     DRM] DCB outp 02: 02011312 00020030
[    8.447568] nouveau  [     DRM] DCB outp 03: 010223f1 00c0c080
[    8.447570] nouveau  [     DRM] DCB conn 00: 0000
[    8.447572] nouveau  [     DRM] DCB conn 01: 2130
[    8.447574] nouveau  [     DRM] DCB conn 02: 0210
[    8.447576] nouveau  [     DRM] DCB conn 03: 0211
[    8.447578] nouveau  [     DRM] DCB conn 04: 0213
[    8.456616] nouveau W[     DRM] failed to create encoder 0/1/0: -19
[    8.456619] nouveau W[     DRM] TV-1 has no encoders, removing
[    8.456658] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.456660] [drm] No driver support for vblank timestamp query.
[    8.456773] nouveau  [     DRM] 1 available performance level(s)
[    8.456776] nouveau  [     DRM] 0: core 450MHz shader 918MHz memory 266MHz fanspeed 100%
[    8.456779] nouveau  [     DRM] c: core 450MHz shader 918MHz memory 265MHz voltage 1320mV
[    8.460681] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    8.489121] SKU: Nid=0x1d sku_cfg=0x4005e601
[    8.489124] SKU: port_connectivity=0x1
[    8.489126] SKU: enable_pcbeep=0x0
[    8.489127] SKU: check_sum=0x00000005
[    8.489129] SKU: customization=0x000000e6
[    8.489130] SKU: external_amp=0x0
[    8.489131] SKU: platform_type=0x0
[    8.489132] SKU: swap=0x0
[    8.489133] SKU: override=0x1
[    8.489597] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    8.489599]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.489601]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    8.489602]    mono: mono_out=0x0
[    8.489603]    dig-out=0x1e/0x0
[    8.489605]    inputs:
[    8.489606]      Rear Mic=0x18
[    8.489608]      Front Mic=0x19
[    8.489610]      Line=0x1a
[    8.489611]      CD=0x1c
[    8.489612]    dig-in=0x1f
[    8.489614] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    8.489615] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0885
[    8.503568] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    8.503740] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    8.503857] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    8.503979] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    8.504086] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    8.504209] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    8.504326] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    8.504432] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    8.716596] nouveau  [     DRM] MM: using CRYPT for buffer copies
[    8.759859] nouveau  [     DRM] allocated 1440x900 fb: 0x70000, bo f68ad000
[    8.759965] fbcon: nouveaufb (fb0) is primary device
[    8.811390] Console: switching to colour frame buffer device 180x56
[    8.812242] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    8.812243] nouveau 0000:01:00.0: registered panic notifier
[    8.812248] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[    8.843528] init: plymouth-splash main process (648) terminated with status 1
[   12.306181] r8169 0000:04:00.0 eth0: link up
[   12.306192] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

Xorg.0.log:
```
[   628.693] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[   628.693] X Protocol Version 11, Revision 0
[   628.694] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   628.694] Current Operating System: Linux fb 3.12.0-031200-generic #201311031935 SMP Mon Nov 4 00:46:34 UTC 2013 i686
[   628.694] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.0-031200-generic root=LABEL=maq ro log_buf_len=1M quiet splash vt.handoff=7
[   628.695] Build Date: 15 October 2013  09:23:29AM
[   628.695] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[   628.695] Current version of pixman: 0.30.2
[   628.696] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   628.696] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   628.697] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  6 23:13:09 2014
[   628.697] (++) Using config file: "/usr/lib/krb5/plugins/preauth/x"
[   628.698] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   628.698] (==) ServerLayout "Default Layout"
[   628.698] (**) |-->Screen "Default Screen" (0)
[   628.698] (**) |   |-->Monitor "Generic Monitor"
[   628.698] (**) Option "DontZap" "true"
[   628.698] (**) Option "DontZoom" "false"
[   628.698] (==) Automatically adding devices
[   628.698] (==) Automatically enabling devices
[   628.698] (==) Automatically adding GPU devices
[   628.698] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   628.698] 	Entry deleted from font path.
[   628.698] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   628.698] 	Entry deleted from font path.
[   628.698] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   628.698] 	Entry deleted from font path.
[   628.698] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   628.698] 	Entry deleted from font path.
[   628.698] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   628.698] 	Entry deleted from font path.
[   628.698] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   628.698] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   628.698] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   628.698] (II) Loader magic: 0xb77e36a0
[   628.698] (II) Module ABI versions:
[   628.698] 	X.Org ANSI C Emulation: 0.4
[   628.698] 	X.Org Video Driver: 14.1
[   628.698] 	X.Org XInput driver : 19.1
[   628.698] 	X.Org Server Extension : 7.0
[   628.699] (II) xfree86: Adding drm device (/dev/dri/card0)
[   628.700] (--) PCI:*(0:1:0:0) 10de:0421:1682:2302 rev 161, Mem @ 0xe6000000/16777216, 0xc0000000/536870912, 0xe4000000/33554432, I/O @ 0x0000b000/128, BIOS @ 0x????????/131072
[   628.700] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   628.701] Initializing built-in extension Generic Event Extension
[   628.701] Initializing built-in extension SHAPE
[   628.701] Initializing built-in extension MIT-SHM
[   628.701] Initializing built-in extension XInputExtension
[   628.702] Initializing built-in extension XTEST
[   628.702] Initializing built-in extension BIG-REQUESTS
[   628.702] Initializing built-in extension SYNC
[   628.702] Initializing built-in extension XKEYBOARD
[   628.703] Initializing built-in extension XC-MISC
[   628.703] Initializing built-in extension SECURITY
[   628.703] Initializing built-in extension XINERAMA
[   628.704] Initializing built-in extension XFIXES
[   628.704] Initializing built-in extension RENDER
[   628.704] Initializing built-in extension RANDR
[   628.705] Initializing built-in extension COMPOSITE
[   628.705] Initializing built-in extension DAMAGE
[   628.705] Initializing built-in extension MIT-SCREEN-SAVER
[   628.706] Initializing built-in extension DOUBLE-BUFFER
[   628.706] Initializing built-in extension RECORD
[   628.706] Initializing built-in extension DPMS
[   628.707] Initializing built-in extension X-Resource
[   628.707] Initializing built-in extension XVideo
[   628.707] Initializing built-in extension XVideo-MotionCompensation
[   628.708] Initializing built-in extension SELinux
[   628.708] Initializing built-in extension XFree86-VidModeExtension
[   628.708] Initializing built-in extension XFree86-DGA
[   628.708] Initializing built-in extension XFree86-DRI
[   628.709] Initializing built-in extension DRI2
[   628.709] (II) "glx" will be loaded by default.
[   628.709] (WW) "xmir" is not to be loaded by default. Skipping.
[   628.709] (II) LoadModule: "dri2"
[   628.709] (II) Module "dri2" already built-in
[   628.709] (II) LoadModule: "glamoregl"
[   628.709] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   628.711] (II) Module glamoregl: vendor="X.Org Foundation"
[   628.711] 	compiled for 1.14.3, module version = 0.5.1
[   628.711] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   628.711] (II) LoadModule: "glx"
[   628.711] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   628.711] (II) Module glx: vendor="X.Org Foundation"
[   628.711] 	compiled for 1.14.3, module version = 1.0.0
[   628.711] 	ABI class: X.Org Server Extension, version 7.0
[   628.711] (==) AIGLX enabled
[   628.711] Loading extension GLX
[   628.711] (==) Matched nvidia as autoconfigured driver 0
[   628.711] (==) Matched nouveau as autoconfigured driver 1
[   628.711] (==) Matched nvidia as autoconfigured driver 2
[   628.711] (==) Matched nouveau as autoconfigured driver 3
[   628.711] (==) Matched vesa as autoconfigured driver 4
[   628.711] (==) Matched modesetting as autoconfigured driver 5
[   628.711] (==) Matched fbdev as autoconfigured driver 6
[   628.711] (==) Assigned the driver to the xf86ConfigLayout
[   628.711] (II) LoadModule: "nvidia"
[   628.712] (WW) Warning, couldn't open module nvidia
[   628.712] (II) UnloadModule: "nvidia"
[   628.712] (II) Unloading nvidia
[   628.712] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   628.712] (II) LoadModule: "nouveau"
[   628.712] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   628.712] (II) Module nouveau: vendor="X.Org Foundation"
[   628.712] 	compiled for 1.14.2.901, module version = 1.0.9
[   628.712] 	Module class: X.Org Video Driver
[   628.712] 	ABI class: X.Org Video Driver, version 14.1
[   628.712] (II) LoadModule: "vesa"
[   628.713] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   628.713] (II) Module vesa: vendor="X.Org Foundation"
[   628.713] 	compiled for 1.14.1, module version = 2.3.2
[   628.713] 	Module class: X.Org Video Driver
[   628.713] 	ABI class: X.Org Video Driver, version 14.1
[   628.713] (II) LoadModule: "modesetting"
[   628.713] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   628.713] (II) Module modesetting: vendor="X.Org Foundation"
[   628.713] 	compiled for 1.14.1, module version = 0.8.0
[   628.713] 	Module class: X.Org Video Driver
[   628.713] 	ABI class: X.Org Video Driver, version 14.1
[   628.713] (II) LoadModule: "fbdev"
[   628.713] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   628.713] (II) Module fbdev: vendor="X.Org Foundation"
[   628.713] 	compiled for 1.14.1, module version = 0.4.3
[   628.713] 	Module class: X.Org Video Driver
[   628.713] 	ABI class: X.Org Video Driver, version 14.1
[   628.713] (==) Matched nvidia as autoconfigured driver 0
[   628.713] (==) Matched nouveau as autoconfigured driver 1
[   628.713] (==) Matched nvidia as autoconfigured driver 2
[   628.713] (==) Matched nouveau as autoconfigured driver 3
[   628.713] (==) Matched vesa as autoconfigured driver 4
[   628.713] (==) Matched modesetting as autoconfigured driver 5
[   628.713] (==) Matched fbdev as autoconfigured driver 6
[   628.713] (==) Assigned the driver to the xf86ConfigLayout
[   628.713] (II) LoadModule: "nvidia"
[   628.714] (WW) Warning, couldn't open module nvidia
[   628.714] (II) UnloadModule: "nvidia"
[   628.714] (II) Unloading nvidia
[   628.714] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   628.714] (II) LoadModule: "nouveau"
[   628.714] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   628.714] (II) Module nouveau: vendor="X.Org Foundation"
[   628.714] 	compiled for 1.14.2.901, module version = 1.0.9
[   628.714] 	Module class: X.Org Video Driver
[   628.714] 	ABI class: X.Org Video Driver, version 14.1
[   628.714] (II) UnloadModule: "nouveau"
[   628.714] (II) Unloading nouveau
[   628.714] (II) Failed to load module "nouveau" (already loaded, 0)
[   628.714] (II) LoadModule: "vesa"
[   628.714] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   628.714] (II) Module vesa: vendor="X.Org Foundation"
[   628.714] 	compiled for 1.14.1, module version = 2.3.2
[   628.714] 	Module class: X.Org Video Driver
[   628.714] 	ABI class: X.Org Video Driver, version 14.1
[   628.714] (II) UnloadModule: "vesa"
[   628.714] (II) Unloading vesa
[   628.714] (II) Failed to load module "vesa" (already loaded, 0)
[   628.714] (II) LoadModule: "modesetting"
[   628.715] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   628.715] (II) Module modesetting: vendor="X.Org Foundation"
[   628.715] 	compiled for 1.14.1, module version = 0.8.0
[   628.715] 	Module class: X.Org Video Driver
[   628.715] 	ABI class: X.Org Video Driver, version 14.1
[   628.715] (II) UnloadModule: "modesetting"
[   628.715] (II) Unloading modesetting
[   628.715] (II) Failed to load module "modesetting" (already loaded, 0)
[   628.715] (II) LoadModule: "fbdev"
[   628.715] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   628.715] (II) Module fbdev: vendor="X.Org Foundation"
[   628.715] 	compiled for 1.14.1, module version = 0.4.3
[   628.715] 	Module class: X.Org Video Driver
[   628.715] 	ABI class: X.Org Video Driver, version 14.1
[   628.715] (II) UnloadModule: "fbdev"
[   628.715] (II) Unloading fbdev
[   628.715] (II) Failed to load module "fbdev" (already loaded, 0)
[   628.715] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[   628.715] (II) NOUVEAU driver for NVIDIA chipset families :
[   628.715] 	RIVA TNT        (NV04)
[   628.715] 	RIVA TNT2       (NV05)
[   628.715] 	GeForce 256     (NV10)
[   628.715] 	GeForce 2       (NV11, NV15)
[   628.715] 	GeForce 4MX     (NV17, NV18)
[   628.715] 	GeForce 3       (NV20)
[   628.715] 	GeForce 4Ti     (NV25, NV28)
[   628.715] 	GeForce FX      (NV3x)
[   628.715] 	GeForce 6       (NV4x)
[   628.715] 	GeForce 7       (G7x)
[   628.715] 	GeForce 8       (G8x)
[   628.715] 	GeForce GTX 200 (NVA0)
[   628.715] 	GeForce GTX 400 (NVC0)
[   628.715] (II) VESA: driver for VESA chipsets: vesa
[   628.715] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   628.715] (II) FBDEV: driver for framebuffer: fbdev
[   628.715] (--) using VT number 7

[   628.716] (II) [drm] nouveau interface version: 1.1.1
[   628.716] (WW) Falling back to old probe method for vesa
[   628.716] (WW) Falling back to old probe method for modesetting
[   628.716] (WW) Falling back to old probe method for fbdev
[   628.716] (II) Loading sub module "fbdevhw"
[   628.716] (II) LoadModule: "fbdevhw"
[   628.717] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   628.717] (II) Module fbdevhw: vendor="X.Org Foundation"
[   628.717] 	compiled for 1.14.3, module version = 0.0.2
[   628.717] 	ABI class: X.Org Video Driver, version 14.1
[   628.717] (II) Loading sub module "dri2"
[   628.717] (II) LoadModule: "dri2"
[   628.717] (II) Module "dri2" already built-in
[   628.717] (--) NOUVEAU(0): Chipset: "NVIDIA NV86"
[   628.717] (**) NOUVEAU(0): Depth 16, (--) framebuffer bpp 16
[   628.717] (==) NOUVEAU(0): RGB weight 565
[   628.717] (==) NOUVEAU(0): Default visual is TrueColor
[   628.717] (==) NOUVEAU(0): Using HW cursor
[   628.717] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[   628.717] (==) NOUVEAU(0): Page flipping enabled
[   628.717] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[   628.747] (II) NOUVEAU(0): Output VGA-1 using monitor section Generic Monitor
[   628.776] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[   628.797] (II) NOUVEAU(0): EDID for output VGA-1
[   628.826] (II) NOUVEAU(0): EDID for output DVI-I-1
[   628.826] (II) NOUVEAU(0): Manufacturer: GSM  Model: 4491  Serial#: 16843009
[   628.826] (II) NOUVEAU(0): Year: 2008  Week: 1
[   628.826] (II) NOUVEAU(0): EDID Version: 1.3
[   628.826] (II) NOUVEAU(0): Digital Display Input
[   628.826] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 38  vert.: 23
[   628.826] (II) NOUVEAU(0): Gamma: 2.20
[   628.826] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[   628.826] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   628.826] (II) NOUVEAU(0): First detailed timing is preferred mode
[   628.826] (II) NOUVEAU(0): redX: 0.609 redY: 0.339   greenX: 0.301 greenY: 0.594
[   628.826] (II) NOUVEAU(0): blueX: 0.148 blueY: 0.089   whiteX: 0.312 whiteY: 0.329
[   628.826] (II) NOUVEAU(0): Supported established timings:
[   628.826] (II) NOUVEAU(0): 720x400@70Hz
[   628.826] (II) NOUVEAU(0): 640x480@60Hz
[   628.826] (II) NOUVEAU(0): 640x480@75Hz
[   628.826] (II) NOUVEAU(0): 800x600@56Hz
[   628.826] (II) NOUVEAU(0): 800x600@60Hz
[   628.826] (II) NOUVEAU(0): 800x600@75Hz
[   628.826] (II) NOUVEAU(0): 832x624@75Hz
[   628.826] (II) NOUVEAU(0): 1024x768@60Hz
[   628.826] (II) NOUVEAU(0): 1024x768@70Hz
[   628.826] (II) NOUVEAU(0): 1024x768@75Hz
[   628.826] (II) NOUVEAU(0): 1280x1024@75Hz
[   628.826] (II) NOUVEAU(0): 1152x864@75Hz
[   628.826] (II) NOUVEAU(0): Manufacturer's mask: 0
[   628.826] (II) NOUVEAU(0): Supported standard timings:
[   628.826] (II) NOUVEAU(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   628.826] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   628.826] (II) NOUVEAU(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   628.826] (II) NOUVEAU(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   628.827] (II) NOUVEAU(0): Supported detailed timing:
[   628.827] (II) NOUVEAU(0): clock: 106.5 MHz   Image Size:  370 x 232 mm
[   628.827] (II) NOUVEAU(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[   628.827] (II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[   628.827] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 145 MHz
[   628.827] (II) NOUVEAU(0): Monitor name: W1752
[   628.827] (II) NOUVEAU(0): Monitor name: 
[   628.827] (II) NOUVEAU(0): EDID (in hex):
[   628.827] (II) NOUVEAU(0): 	00ffffffffffff001e6d914401010101
[   628.827] (II) NOUVEAU(0): 	01120103ea261778ea30319c564d9826
[   628.827] (II) NOUVEAU(0): 	165054a76f80950081808140714f0101
[   628.827] (II) NOUVEAU(0): 	0101010101019a29a0d0518422305098
[   628.827] (II) NOUVEAU(0): 	360072e81000001c000000fd00384b1e
[   628.827] (II) NOUVEAU(0): 	530e000a202020202020000000fc0057
[   628.827] (II) NOUVEAU(0): 	313735320a20202020202020000000fc
[   628.827] (II) NOUVEAU(0): 	000a20202020202020202020202000dc
[   628.827] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[   628.827] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz UeP)
[   628.827] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[   628.827] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   628.827] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   628.827] (II) NOUVEAU(0): Output VGA-1 disconnected
[   628.827] (II) NOUVEAU(0): Output DVI-I-1 connected
[   628.827] (II) NOUVEAU(0): Using user preference for initial modes
[   628.827] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 640x480
[   628.827] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   628.827] (--) NOUVEAU(0): Virtual size is 640x480 (pitch 0)
[   628.827] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz UeP)
[   628.827] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz eP)
[   628.827] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[   628.827] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[   628.827] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[   628.827] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   628.827] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[   628.827] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   628.827] (==) NOUVEAU(0): DPI set to (96, 96)
[   628.827] (II) Loading sub module "fb"
[   628.827] (II) LoadModule: "fb"
[   628.827] (II) Loading /usr/lib/xorg/modules/libfb.so
[   628.827] (II) Module fb: vendor="X.Org Foundation"
[   628.827] 	compiled for 1.14.3, module version = 1.0.0
[   628.827] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   628.827] (II) Loading sub module "exa"
[   628.827] (II) LoadModule: "exa"
[   628.828] (II) Loading /usr/lib/xorg/modules/libexa.so
[   628.828] (II) Module exa: vendor="X.Org Foundation"
[   628.828] 	compiled for 1.14.3, module version = 2.6.0
[   628.828] 	ABI class: X.Org Video Driver, version 14.1
[   628.828] (II) Loading sub module "shadowfb"
[   628.828] (II) LoadModule: "shadowfb"
[   628.828] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   628.828] (II) Module shadowfb: vendor="X.Org Foundation"
[   628.828] 	compiled for 1.14.3, module version = 1.0.0
[   628.828] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   628.828] (II) UnloadModule: "vesa"
[   628.828] (II) Unloading vesa
[   628.828] (II) UnloadModule: "modesetting"
[   628.828] (II) Unloading modesetting
[   628.828] (II) UnloadModule: "fbdev"
[   628.828] (II) Unloading fbdev
[   628.828] (II) UnloadSubModule: "fbdevhw"
[   628.828] (II) Unloading fbdevhw
[   628.829] (II) NOUVEAU(0): Opened GPU channel 0
[   628.832] (II) NOUVEAU(0): [DRI2] Setup complete
[   628.832] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[   628.832] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[   628.833] (II) EXA(0): Driver allocated offscreen pixmaps
[   628.833] (II) EXA(0): Driver registered support for the following operations:
[   628.833] (II)         Solid
[   628.833] (II)         Copy
[   628.833] (II)         Composite (RENDER acceleration)
[   628.833] (II)         UploadToScreen
[   628.833] (II)         DownloadFromScreen
[   628.833] (==) NOUVEAU(0): Backing store disabled
[   628.833] (==) NOUVEAU(0): Silken mouse enabled
[   628.833] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[   628.833] (II) NOUVEAU(0): [XvMC] Extension initialized.
[   628.833] (==) NOUVEAU(0): DPMS enabled
[   628.833] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   628.833] (--) RandR disabled
[   628.840] (II) SELinux: Disabled on system
[   628.856] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   628.856] (II) AIGLX: enabled GLX_INTEL_swap_event
[   628.856] (II) AIGLX: enabled GLX_ARB_create_context
[   628.856] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   628.856] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   628.856] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   628.856] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   628.857] (II) AIGLX: Loaded and initialized nouveau
[   628.857] (II) GLX: Initialized DRI2 GL provider for screen 0
[   628.857] (II) NOUVEAU(0): NVEnterVT is called.
[   628.913] (II) NOUVEAU(0): Setting screen physical size to 169 x 126
[   628.913] resize called 640 480
[   628.921] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   628.923] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   628.923] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   628.923] (II) LoadModule: "evdev"
[   628.923] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   628.923] (II) Module evdev: vendor="X.Org Foundation"
[   628.923] 	compiled for 1.14.1, module version = 2.7.3
[   628.923] 	Module class: X.Org XInput Driver
[   628.923] 	ABI class: X.Org XInput driver, version 19.1
[   628.923] (II) Using input driver 'evdev' for 'Power Button'
[   628.924] (**) Power Button: always reports core events
[   628.924] (**) evdev: Power Button: Device: "/dev/input/event1"
[   628.924] (--) evdev: Power Button: Vendor 0 Product 0x1
[   628.924] (--) evdev: Power Button: Found keys
[   628.924] (II) evdev: Power Button: Configuring as keyboard
[   628.924] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   628.924] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   628.924] (**) Option "xkb_rules" "evdev"
[   628.924] (**) Option "xkb_model" "pc105"
[   628.924] (**) Option "xkb_layout" "br"
[   628.926] (II) XKB: reuse xkmfile /var/lib/xkb/server-A37B2EFB8B2398771EA3BE2A51A1034B516E3F38.xkm
[   628.926] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   628.926] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   628.926] (II) Using input driver 'evdev' for 'Power Button'
[   628.926] (**) Power Button: always reports core events
[   628.926] (**) evdev: Power Button: Device: "/dev/input/event0"
[   628.926] (--) evdev: Power Button: Vendor 0 Product 0x1
[   628.926] (--) evdev: Power Button: Found keys
[   628.926] (II) evdev: Power Button: Configuring as keyboard
[   628.926] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   628.926] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   628.926] (**) Option "xkb_rules" "evdev"
[   628.926] (**) Option "xkb_model" "pc105"
[   628.926] (**) Option "xkb_layout" "br"
[   628.926] (II) config/udev: Adding drm device (/dev/dri/card0)
[   628.926] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   628.927] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event10)
[   628.927] (II) No input driver specified, ignoring this device.
[   628.927] (II) This device may have been added with another device file.
[   628.927] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event9)
[   628.927] (II) No input driver specified, ignoring this device.
[   628.927] (II) This device may have been added with another device file.
[   628.927] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event8)
[   628.927] (II) No input driver specified, ignoring this device.
[   628.927] (II) This device may have been added with another device file.
[   628.927] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event7)
[   628.927] (II) No input driver specified, ignoring this device.
[   628.927] (II) This device may have been added with another device file.
[   628.928] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event6)
[   628.928] (II) No input driver specified, ignoring this device.
[   628.928] (II) This device may have been added with another device file.
[   628.928] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event5)
[   628.928] (II) No input driver specified, ignoring this device.
[   628.928] (II) This device may have been added with another device file.
[   628.928] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event12)
[   628.928] (II) No input driver specified, ignoring this device.
[   628.928] (II) This device may have been added with another device file.
[   628.928] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[   628.928] (II) No input driver specified, ignoring this device.
[   628.928] (II) This device may have been added with another device file.
[   628.928] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event2)
[   628.928] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[   628.928] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[   628.928] (**) USB USB Keykoard: always reports core events
[   628.928] (**) evdev: USB USB Keykoard: Device: "/dev/input/event2"
[   628.929] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x2
[   628.929] (--) evdev: USB USB Keykoard: Found keys
[   628.929] (II) evdev: USB USB Keykoard: Configuring as keyboard
[   628.929] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input4/event2"
[   628.929] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 8)
[   628.929] (**) Option "xkb_rules" "evdev"
[   628.929] (**) Option "xkb_model" "pc105"
[   628.929] (**) Option "xkb_layout" "br"
[   628.929] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event3)
[   628.929] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[   628.929] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[   628.929] (**) USB USB Keykoard: always reports core events
[   628.929] (**) evdev: USB USB Keykoard: Device: "/dev/input/event3"
[   628.929] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x2
[   628.929] (--) evdev: USB USB Keykoard: Found 1 mouse buttons
[   628.929] (--) evdev: USB USB Keykoard: Found scroll wheel(s)
[   628.929] (--) evdev: USB USB Keykoard: Found relative axes
[   628.929] (II) evdev: USB USB Keykoard: Forcing relative x/y axes to exist.
[   628.929] (--) evdev: USB USB Keykoard: Found absolute axes
[   628.929] (II) evdev: USB USB Keykoard: Forcing absolute x/y axes to exist.
[   628.929] (--) evdev: USB USB Keykoard: Found keys
[   628.929] (II) evdev: USB USB Keykoard: Configuring as mouse
[   628.929] (II) evdev: USB USB Keykoard: Configuring as keyboard
[   628.929] (II) evdev: USB USB Keykoard: Adding scrollwheel support
[   628.929] (**) evdev: USB USB Keykoard: YAxisMapping: buttons 4 and 5
[   628.929] (**) evdev: USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   628.929] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input5/event3"
[   628.929] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 9)
[   628.929] (**) Option "xkb_rules" "evdev"
[   628.929] (**) Option "xkb_model" "pc105"
[   628.929] (**) Option "xkb_layout" "br"
[   628.929] (II) evdev: USB USB Keykoard: initialized for relative axes.
[   628.929] (WW) evdev: USB USB Keykoard: ignoring absolute axes.
[   628.929] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[   628.929] (**) USB USB Keykoard: (accel) acceleration profile 0
[   628.930] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[   628.930] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[   628.930] (II) config/udev: Adding input device MosArt Optical Mouse (/dev/input/event4)
[   628.930] (**) MosArt Optical Mouse: Applying InputClass "evdev pointer catchall"
[   628.930] (II) Using input driver 'evdev' for 'MosArt Optical Mouse'
[   628.930] (**) MosArt Optical Mouse: always reports core events
[   628.930] (**) evdev: MosArt Optical Mouse: Device: "/dev/input/event4"
[   628.930] (--) evdev: MosArt Optical Mouse: Vendor 0x62a Product 0x3
[   628.930] (--) evdev: MosArt Optical Mouse: Found 3 mouse buttons
[   628.930] (--) evdev: MosArt Optical Mouse: Found scroll wheel(s)
[   628.930] (--) evdev: MosArt Optical Mouse: Found relative axes
[   628.930] (--) evdev: MosArt Optical Mouse: Found x and y relative axes
[   628.930] (II) evdev: MosArt Optical Mouse: Configuring as mouse
[   628.930] (II) evdev: MosArt Optical Mouse: Adding scrollwheel support
[   628.930] (**) evdev: MosArt Optical Mouse: YAxisMapping: buttons 4 and 5
[   628.930] (**) evdev: MosArt Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   628.930] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input6/event4"
[   628.930] (II) XINPUT: Adding extended input device "MosArt Optical Mouse" (type: MOUSE, id 10)
[   628.930] (II) evdev: MosArt Optical Mouse: initialized for relative axes.
[   628.930] (**) MosArt Optical Mouse: (accel) keeping acceleration scheme 1
[   628.930] (**) MosArt Optical Mouse: (accel) acceleration profile 0
[   628.930] (**) MosArt Optical Mouse: (accel) acceleration factor: 2.000
[   628.930] (**) MosArt Optical Mouse: (accel) acceleration threshold: 4
[   628.930] (II) config/udev: Adding input device MosArt Optical Mouse (/dev/input/mouse0)
[   628.930] (II) No input driver specified, ignoring this device.
[   628.930] (II) This device may have been added with another device file.
[   652.984] (II) evdev: MosArt Optical Mouse: Close
[   652.984] (II) UnloadModule: "evdev"
[   652.984] (II) evdev: USB USB Keykoard: Close
[   652.984] (II) UnloadModule: "evdev"
[   652.984] (II) evdev: USB USB Keykoard: Close
[   652.984] (II) UnloadModule: "evdev"
[   652.984] (II) evdev: Power Button: Close
[   652.984] (II) UnloadModule: "evdev"
[   652.984] (II) evdev: Power Button: Close
[   652.984] (II) UnloadModule: "evdev"
[   652.985] (II) NOUVEAU(0): NVLeaveVT is called.
[   652.986] (II) NOUVEAU(0): Closed GPU channel 0
[   653.048] (EE) Server terminated successfully (0). Closing log file.

```

lsmod:
```
Module                  Size  Used by
snd_seq_dummy          12686  0 
snd_hda_codec_realtek    50663  1 
snd_hda_intel          43367  3 
snd_hda_codec         169632  2 snd_hda_codec_realtek,snd_hda_intel
nouveau               874906  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                90501  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18398  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
coretemp               13352  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25198  1 snd_seq_midi
kvm_intel             133583  0 
mxm_wmi                12893  1 nouveau
snd_seq                55716  4 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
wmi                    18827  2 mxm_wmi,nouveau
kvm                   390460  1 kvm_intel
video                  19046  1 nouveau
snd_seq_device         14137  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
ttm                    72633  1 nouveau
snd_timer              28971  3 snd_pcm,snd_seq
gpio_ich               13278  0 
drm_kms_helper         47293  1 nouveau
snd                    61311  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
ppdev                  17423  0 
drm                   248440  4 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13316  1 nouveau
psmouse                92689  0 
soundcore              12600  1 snd
microcode              18938  0 
serio_raw              13230  0 
lp                     13359  0 
joydev                 17299  0 
lpc_ich                16987  0 
mac_hid                13077  0 
parport_pc             32114  1 
parport                40945  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47406  0 
hid                    87718  2 hid_generic,usbhid
pata_acpi              12886  0 
usb_storage            48754  3 
ahci                   25703  0 
libahci                30834  1 ahci
pata_jmicron           12662  0 
r8169                  62775  0 
mii                    13693  1 r8169
```

---

