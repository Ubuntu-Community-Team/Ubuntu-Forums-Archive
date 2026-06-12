---
title: "TVtime on PixelView (conexant chipset)"
date: 2010-09-15
forum: Multimedia Software
---

### Post by abhilash82 on 2010-09-15
I have installed Tvtime and XawTv applications and I am currently trying to configure both these applications to detect my tv tuner card (pixelview play tv pro with conexant cx2388 chipset).

Can anyone help me to configure both video and audio with channel scan for my tv tuner card?

Thanks
ARK
):P

---

### Post by abhilash82 on 2010-09-18
I have given below the dmesg dump.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ef2fc00 (usable)
[    0.000000]  BIOS-e820: 000000003ef2fc00 - 000000003ef30000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ef30000 - 000000003ef40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ef40000 - 000000003eff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003eff0000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3ef2f max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
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
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ef2fc00 (usable)
[    0.000000]  modified: 000000003ef2fc00 - 000000003ef30000 (ACPI NVS)
[    0.000000]  modified: 000000003ef30000 - 000000003ef40000 (ACPI data)
[    0.000000]  modified: 000000003ef40000 - 000000003eff0000 (ACPI NVS)
[    0.000000]  modified: 000000003eff0000 - 000000003f000000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2ec0c000 - 2f3a3745
[    0.000000] ACPI: RSDP 000f61e0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ef30000 00038 (v01 INTEL  D865GBF  20050804 MSFT 00000097)
[    0.000000] ACPI: FACP 3ef30200 00081 (v02 INTEL  D865GBF  20050804 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ef30370 04305 (v01 INTEL  D865GBF  00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 3ef40000 00040
[    0.000000] ACPI: APIC 3ef30300 00068 (v01 INTEL  D865GBF  20050804 MSFT 00000097)
[    0.000000] ACPI: ASF! 3ef34680 00099 (v16 LEGEND I865PASF 00000001 MSFT 0100000D)
[    0.000000] ACPI: TCPA 3ef34719 00034 (v01 INTEL  TBLOEMID 00000001 MSFT 00000097)
[    0.000000] ACPI: WDDT 3ef3474d 00040 (v01 INTEL  OEMWDDT  00000001 MSFT 0100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [002ec0c000 - 002f3a3745]          RAMDISK ==> [002ec0c000 - 002f3a3745]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008de000 - 00008e1148]              BRK ==> [00008de000 - 00008e1148]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ef2f
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ef2f
[    0.000000] On node 0 totalpages: 257738
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30274 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:bfcf0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255723
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=47b95971-f845-4cfb-aabb-b0bbe0fb666c ro vga=792 splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5156780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ef2f)
[    0.000000] Memory: 1000444k/1031356k available (4679k kernel code, 29904k reserved, 2124k data, 660k init, 122052k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2393.935 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.87 BogoMIPS (lpj=9575740)
[    0.004032] Security Framework initialized
[    0.004061] AppArmor: AppArmor initialized
[    0.004071] Mount-cache hash table entries: 512
[    0.004259] Initializing cgroup subsys ns
[    0.004265] Initializing cgroup subsys cpuacct
[    0.004273] Initializing cgroup subsys memory
[    0.004284] Initializing cgroup subsys devices
[    0.004288] Initializing cgroup subsys freezer
[    0.004292] Initializing cgroup subsys net_cls
[    0.004324] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004329] CPU: L2 cache: 512K
[    0.004333] CPU: Physical Processor ID: 0
[    0.004335] CPU: Processor Core ID: 0
[    0.004341] mce: CPU supports 4 MCE banks
[    0.004354] CPU0: Thermal monitoring enabled (TM1)
[    0.004367] Performance Events: no PMU driver, software events only.
[    0.004377] Checking 'hlt' instruction... OK.
[    0.021004] SMP alternatives: switching to UP code
[    0.033724] ACPI: Core revision 20090903
[    0.043482] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.043489] ftrace: allocating 21780 entries in 43 pages
[    0.044086] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044380] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084563] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[    0.088001] Brought up 1 CPUs
[    0.088001] Total of 1 processors activated (4787.87 BogoMIPS).
[    0.088001] CPU0 attaching NULL sched-domain.
[    0.088001] devtmpfs: initialized
[    0.088001] regulator: core version 0.5
[    0.088001] Time:  9:59:53  Date: 09/18/10
[    0.088001] NET: Registered protocol family 16
[    0.088001] EISA bus registered
[    0.088001] ACPI: bus type pci registered
[    0.088001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.088001] PCI: Using configuration type 1 for base access
[    0.088001] bio: create slab <bio-0> at 0
[    0.088661] ACPI: EC: Look up EC in DSDT
[    0.090869] ACPI: Executed 3 blocks of module-level executable AML code
[    0.096023] ACPI: Interpreter enabled
[    0.096038] ACPI: (supports S0 S1 S4 S5)
[    0.096066] ACPI: Using IOAPIC for interrupt routing
[    0.104021] ACPI: Power Resource [URP1] (off)
[    0.104065] ACPI: Power Resource [FDDP] (off)
[    0.104107] ACPI: Power Resource [LPTP] (off)
[    0.104344] ACPI: No dock devices found.
[    0.104520] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.104572] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.104584] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.104652] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.104659] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]
[    0.104666] pci 0000:00:02.0: reg 18 io port: [0xec00-0xec07]
[    0.104716] pci 0000:00:06.0: reg 10 32bit mmio: [0xfecf0000-0xfecf0fff]
[    0.104808] pci 0000:00:1d.0: reg 20 io port: [0xc800-0xc81f]
[    0.104863] pci 0000:00:1d.1: reg 20 io port: [0xcc00-0xcc1f]
[    0.104917] pci 0000:00:1d.2: reg 20 io port: [0xd000-0xd01f]
[    0.104972] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
[    0.105036] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfeb7fc00-0xfeb7ffff]
[    0.105096] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.105102] pci 0000:00:1d.7: PME# disabled
[    0.105193] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.105199] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.105204] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH4 GPIO
[    0.105229] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.105237] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.105245] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.105252] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.105260] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.105268] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.105300] pci 0000:00:1f.2: reg 10 io port: [0xe800-0xe807]
[    0.105308] pci 0000:00:1f.2: reg 14 io port: [0xe400-0xe403]
[    0.105315] pci 0000:00:1f.2: reg 18 io port: [0xe000-0xe007]
[    0.105322] pci 0000:00:1f.2: reg 1c io port: [0xdc00-0xdc03]
[    0.105329] pci 0000:00:1f.2: reg 20 io port: [0xd800-0xd80f]
[    0.105382] pci 0000:00:1f.3: reg 20 io port: [0xc400-0xc41f]
[    0.105439] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfeb7f800-0xfeb7f9ff]
[    0.105447] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfeb7f400-0xfeb7f4ff]
[    0.105478] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.105483] pci 0000:00:1f.5: PME# disabled
[    0.105525] pci 0000:01:00.0: reg 10 io port: [0xb800-0xb8ff]
[    0.105533] pci 0000:01:00.0: reg 14 32bit mmio: [0xfe9ffc00-0xfe9ffcff]
[    0.105557] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe9e0000-0xfe9effff]
[    0.105576] pci 0000:01:00.0: supports D1 D2
[    0.105579] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.105584] pci 0000:01:00.0: PME# disabled
[    0.105621] pci 0000:01:01.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.105698] pci 0000:01:01.1: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.105784] pci 0000:00:1e.0: transparent bridge
[    0.105789] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    0.105795] pci 0000:00:1e.0: bridge 32bit mmio: [0xfa900000-0xfe9fffff]
[    0.105807] pci_bus 0000:00: on NUMA node 0
[    0.105813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.105919] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.109377] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.109552] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.109724] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.109897] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.110068] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.110242] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.110415] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.110586] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.110753] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.110765] vgaarb: loaded
[    0.110936] SCSI subsystem initialized
[    0.111021] libata version 3.00 loaded.
[    0.111121] usbcore: registered new interface driver usbfs
[    0.111142] usbcore: registered new interface driver hub
[    0.111176] usbcore: registered new device driver usb
[    0.111365] ACPI: WMI: Mapper loaded
[    0.111368] PCI: Using ACPI for IRQ routing
[    0.111551] NetLabel: Initializing
[    0.111555] NetLabel:  domain hash size = 128
[    0.111557] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.111573] NetLabel:  unlabeled traffic allowed by default
[    0.111717] hpet clockevent registered
[    0.111722] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.111728] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.111735] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.116029] Switching to clocksource tsc
[    0.118454] AppArmor: AppArmor Filesystem Enabled
[    0.118477] pnp: PnP ACPI init
[    0.118499] ACPI: bus type pnp registered
[    0.122974] pnp: PnP ACPI: found 14 devices
[    0.122977] ACPI: ACPI bus type pnp unregistered
[    0.122983] PnPBIOS: Disabled by ACPI PNP
[    0.123003] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.123014] system 00:0c: ioport range 0x400-0x47f has been reserved
[    0.123019] system 00:0c: ioport range 0x680-0x6ff has been reserved
[    0.123023] system 00:0c: ioport range 0x500-0x53f has been reserved
[    0.123029] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.123033] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.123037] system 00:0c: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.123046] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.123051] system 00:0d: iomem range 0xc0000-0xd7fff could not be reserved
[    0.123056] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.123060] system 00:0d: iomem range 0x100000-0x3effffff could not be reserved
[    0.157827] pci 0000:01:00.0: BAR 6: address space collision on of device [0xfe9e0000-0xfe9effff]
[    0.157850] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.157855] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    0.157861] pci 0000:00:1e.0:   MEM window: 0xfa900000-0xfe9fffff
[    0.157867] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x400fffff
[    0.157882] pci 0000:00:1e.0: setting latency timer to 64
[    0.157889] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.157893] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.157897] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.157901] pci_bus 0000:01: resource 1 mem: [0xfa900000-0xfe9fffff]
[    0.157904] pci_bus 0000:01: resource 2 pref mem [0x40000000-0x400fffff]
[    0.157907] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.157911] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.157958] NET: Registered protocol family 2
[    0.158087] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.158548] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.159324] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.159803] TCP: Hash tables configured (established 131072 bind 65536)
[    0.159807] TCP reno registered
[    0.160006] NET: Registered protocol family 1
[    0.160036] pci 0000:00:02.0: Boot video device
[    1.760014] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.760327] cpufreq-nforce2: No nForce2 chipset.
[    1.760367] Scanning for low memory corruption every 60 seconds
[    1.760513] audit: initializing netlink socket (disabled)
[    1.760528] type=2000 audit(1284803994.760:1): initialized
[    1.769725] Trying to unpack rootfs image as initramfs...
[    1.780277] highmem bounce pool size: 64 pages
[    1.780285] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.788310] VFS: Disk quotas dquot_6.5.2
[    1.788416] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.789271] fuse init (API version 7.13)
[    1.789396] msgmni has been set to 1716
[    1.789668] alg: No test for stdrng (krng)
[    1.789752] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.789757] io scheduler noop registered
[    1.789759] io scheduler anticipatory registered
[    1.789762] io scheduler deadline registered
[    1.789820] io scheduler cfq registered (default)
[    1.789965] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.789999] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.790140] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    1.790150] ACPI: Sleep Button [SLPB]
[    1.790212] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.790216] ACPI: Power Button [PWRF]
[    1.790475] processor LNXCPU:00: registered as cooling_device0
[    1.800073] isapnp: Scanning for PnP cards...
[    1.805875] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.805981] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.806450] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.807913] brd: module loaded
[    1.808606] loop: module loaded
[    1.808732] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.808867] ata_piix 0000:00:1f.1: version 2.13
[    1.808882] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.808893]   alloc irq_desc for 18 on node -1
[    1.808896]   alloc kstat_irqs on node -1
[    1.808905] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.808956] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.855772] scsi0 : ata_piix
[    1.855933] scsi1 : ata_piix
[    1.857773] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.857779] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.857836] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.857843] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    1.857894] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.857994] scsi2 : ata_piix
[    1.860456] scsi3 : ata_piix
[    1.861773] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 18
[    1.861777] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 18
[    1.862320] Fixed MDIO Bus: probed
[    1.862374] PPP generic driver version 2.4.2
[    1.862460] tun: Universal TUN/TAP device driver, 1.6
[    1.862464] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.862588] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.862620]   alloc irq_desc for 23 on node -1
[    1.862623]   alloc kstat_irqs on node -1
[    1.862633] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.862655] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.862660] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.862710] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.862742] ehci_hcd 0000:00:1d.7: debug port 1
[    1.866615] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    1.872440] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeb7fc00
[    1.892254] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.892427] usb usb1: configuration #1 chosen from 1 choice
[    1.892471] hub 1-0:1.0: USB hub found
[    1.892485] hub 1-0:1.0: 8 ports detected
[    1.892579] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.892603] uhci_hcd: USB Universal Host Controller Interface driver
[    1.892658]   alloc irq_desc for 16 on node -1
[    1.892662]   alloc kstat_irqs on node -1
[    1.892670] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.892681] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.892686] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.892744] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.892780] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c800
[    1.892897] usb usb2: configuration #1 chosen from 1 choice
[    1.892938] hub 2-0:1.0: USB hub found
[    1.892949] hub 2-0:1.0: 2 ports detected
[    1.893006]   alloc irq_desc for 19 on node -1
[    1.893009]   alloc kstat_irqs on node -1
[    1.893015] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.893024] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.893029] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.893078] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.893109] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000cc00
[    1.893223] usb usb3: configuration #1 chosen from 1 choice
[    1.893264] hub 3-0:1.0: USB hub found
[    1.893273] hub 3-0:1.0: 2 ports detected
[    1.893329] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.893337] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.893342] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.893389] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.893414] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[    1.893536] usb usb4: configuration #1 chosen from 1 choice
[    1.893575] hub 4-0:1.0: USB hub found
[    1.893585] hub 4-0:1.0: 2 ports detected
[    1.893641] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.893649] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.893653] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.893707] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.893731] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
[    1.893844] usb usb5: configuration #1 chosen from 1 choice
[    1.893882] hub 5-0:1.0: USB hub found
[    1.893893] hub 5-0:1.0: 2 ports detected
[    1.894021] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.901219] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.901234] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.901456] mice: PS/2 mouse device common for all mice
[    1.901629] rtc_cmos 00:02: RTC can wake from S4
[    1.901685] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.901711] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.901875] device-mapper: uevent: version 1.0.3
[    1.902026] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.904175] device-mapper: multipath: version 1.1.0 loaded
[    1.904181] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.906451] EISA: Probing bus 0 at eisa.0
[    1.906491] EISA: Detected 0 cards.
[    1.908134] cpuidle: using governor ladder
[    1.908138] cpuidle: using governor menu
[    1.908758] TCP cubic registered
[    1.908929] NET: Registered protocol family 10
[    1.909523] lo: Disabled Privacy Extensions
[    1.909999] NET: Registered protocol family 17
[    1.910077] Using IPI No-Shortcut mode
[    1.910212] PM: Resume from disk failed.
[    1.910227] registered taskstats version 1
[    1.910480]   Magic number: 10:765:980
[    1.910573] rtc_cmos 00:02: setting system clock to 2010-09-18 09:59:55 UTC (1284803995)
[    1.910577] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.910580] EDD information not available.
[    1.970219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.063801] ata3.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    2.063822] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.063917] ata1.00: ATA-6: SAMSUNG SP4002H, QU100-61, max UDMA/100
[    2.063921] ata1.00: 78242976 sectors, multi 16: LBA 
[    2.064421] ata2.00: ATAPI: SAMSUNG CD-ROM SC-152A, CA05, max MWDMA2
[    2.064472] ata2.01: ATAPI: SONY    DVD RW AW-G170A, 1.75, max UDMA/66
[    2.064507] ata2.01: limited to UDMA/33 due to 40-wire cable
[    2.073134] ata1.00: configured for UDMA/100
[    2.073189] ata3.00: configured for UDMA/133
[    2.073255] ata2.00: configured for MWDMA2
[    2.088580] ata2.01: configured for UDMA/33
[    2.362666] Freeing initrd memory: 7773k freed
[    2.456500] isapnp: No Plug & Play device found
[    2.456694] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP4002H  QU10 PQ: 0 ANSI: 5
[    2.456922] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.457170] sd 0:0:0:0: [sda] 78242976 512-byte logical blocks: (40.0 GB/37.3 GiB)
[    2.457245] sd 0:0:0:0: [sda] Write Protect is off
[    2.457249] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.457286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.457643]  sda:
[    2.457793] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-152A   CA06 PQ: 0 ANSI: 5
[    2.461966] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    2.461971] Uniform CD-ROM driver Revision: 3.20
[    2.462101] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.462180] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.463153] scsi 1:0:1:0: CD-ROM            SONY     DVD RW AW-G170A  1.75 PQ: 0 ANSI: 5
[    2.465828] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.465941] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.466014] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.466176] scsi 2:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    2.466343] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    2.466449] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.466518] sd 2:0:0:0: [sdb] Write Protect is off
[    2.466522] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.466559] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.466748]  sdb: sda1 sda2 < sdb1 sdb2 < sdb5 >
[    2.485595] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.495980]  sda5 >
[    2.496348] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.496367] Freeing unused kernel memory: 660k freed
[    2.496931] Write protecting the kernel text: 4680k
[    2.496967] Write protecting the kernel read-only data: 1844k
[    2.527628] udev: starting version 151
[    2.664074] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.853879] Floppy drive(s): fd0 is 1.44M
[    2.858939] usb 2-1: configuration #1 chosen from 1 choice
[    2.872043] FDC 0 is a post-1991 82077
[    2.886423] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.886454] 8139cp 0000:01:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.909875] 8139too Fast Ethernet driver 0.9.28
[    2.909924]   alloc irq_desc for 21 on node -1
[    2.909928]   alloc kstat_irqs on node -1
[    2.909941] 8139too 0000:01:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.911180] eth0: RealTek RTL8139 at 0xb800, 00:e0:4c:e9:62:1f, IRQ 21
[    3.100033] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    3.100369] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.314851] usb 2-2: configuration #1 chosen from 1 choice
[   15.827840] udev: starting version 151
[   15.861458] Adding 4119544k swap on /dev/sda5.  Priority:-1 extents:1 across:4119544k 
[   16.097428] intel_rng: Firmware space is locked read-only. If you can't or
[   16.097432] intel_rng: don't want to disable this in firmware setup, and if
[   16.097434] intel_rng: you are certain that your system has a functional
[   16.097436] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   16.102319] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.242713] Linux agpgart interface v0.103
[   16.287373] Linux video capture interface: v2.00
[   16.544847] lp: driver loaded but no devices found
[   16.641087] psmouse serio1: ID: 10 00 64
[   16.641788] [drm] Initialized drm 1.1.0 20060810
[   16.649818] parport_pc 00:09: reported by Plug and Play ACPI
[   16.649845] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   16.658032] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   16.658191] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   16.669534] gspca: main v2.7.0 registered
[   16.679086] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   16.707346] usbcore: registered new interface driver hiddev
[   16.720399] logips2pp: Detected unknown logitech mouse model 106
[   16.725430] gspca: probing 046d:092f
[   16.741552] lp0: using parport0 (interrupt-driven).
[   16.788515] ppdev: user-space parallel port driver
[   16.795809] gspca: probe ok
[   16.795842] usbcore: registered new interface driver spca561
[   16.795847] spca561: registered
[   16.855234] type=1505 audit(1284784210.441:2):  operation="profile_load" pid=567 name="/sbin/dhclient3"
[   16.855874] type=1505 audit(1284784210.441:3):  operation="profile_load" pid=567 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.861393] type=1505 audit(1284784210.449:4):  operation="profile_load" pid=567 name="/usr/lib/connman/scripts/dhclient-script"
[   16.989329] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.989337] i915 0000:00:02.0: setting latency timer to 64
[   17.007372] [drm] set up 15M of stolen space
[   17.008258] intel drm CRTDDC_A: Test OK
[   17.008765] intel drm DVODDC_D: SDA stuck high!
[   17.008897] [drm] initialized overlay support
[   17.199298] bttv: driver version 0.9.18 loaded
[   17.199303] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.262382] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   17.274360] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   17.274408]   alloc irq_desc for 22 on node -1
[   17.274412]   alloc kstat_irqs on node -1
[   17.274421] cx8800 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.275021] cx88[0]: subsystem: 1554:4976, board: PixelView [card=3,insmod option], frontend(s): 0
[   17.275026] cx88[0]: TV tuner type 5, Radio tuner type -1
[   17.284871] generic-usb 0003:051D:0002.0001: hiddev96,hidraw0: USB HID v1.10 Device [American Power Conversion Back-UPS ES 500 FW:850.m2.I USB FW:m2] on usb-0000:00:1d.0-2/input0
[   17.284908] usbcore: registered new interface driver usbhid
[   17.284913] usbhid: v2.6:USB HID core driver
[   17.392100] cx88[0]: Test OK
[   17.449377] type=1505 audit(1284784211.037:5):  operation="profile_load" pid=689 name="/usr/share/gdm/guest-session/Xsession"
[   17.473431] type=1505 audit(1284784211.061:6):  operation="profile_replace" pid=691 name="/sbin/dhclient3"
[   17.474088] type=1505 audit(1284784211.061:7):  operation="profile_replace" pid=691 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.474443] type=1505 audit(1284784211.061:8):  operation="profile_replace" pid=691 name="/usr/lib/connman/scripts/dhclient-script"
[   17.480164] type=1505 audit(1284784211.069:9):  operation="profile_load" pid=693 name="/usr/bin/evince"
[   17.486328] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   17.535225] cx2388x alsa driver version 0.0.7 loaded
[   17.584083] type=1505 audit(1284784211.173:10):  operation="profile_load" pid=693 name="/usr/bin/evince-previewer"
[   17.622082] type=1505 audit(1284784211.209:11):  operation="profile_load" pid=693 name="/usr/bin/evince-thumbnailer"
[   17.627060] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   17.697473] fb0: inteldrmfb frame buffer device
[   17.697478] registered panic notifier
[   17.697491] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.697525]   alloc irq_desc for 17 on node -1
[   17.697529]   alloc kstat_irqs on node -1
[   17.697538] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.701968] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.702020] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   17.717989] vga16fb: initializing
[   17.717997] vga16fb: mapped to 0xc00a0000
[   17.718003] vga16fb: not registering due to another framebuffer present
[   17.780119] Console: switching to colour frame buffer device 100x37
[   17.793053] tuner-simple 1-0061: creating new instance
[   17.793059] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   17.793847] cx88[0]/0: found at 0000:01:01.0, rev: 5, irq: 22, latency: 32, mmio: 0xfc000000
[   17.793861] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.794073] cx88[0]/0: registered device video1 [v4l2]
[   17.794165] cx88[0]/0: registered device vbi0
[   17.794258] cx88[0]/0: registered device radio0
[   17.800158] cx88_audio 0000:01:01.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.800169] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.800196] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   18.140021] intel8x0_measure_ac97_clock: measured 53900 usecs (2597 samples)
[   18.140027] intel8x0: clocking to 48000
[   19.198375] render error detected, EIR: 0x00000010
[   19.198383] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   19.198396] render error detected, EIR: 0x00000010
[   20.196514] CPU0 attaching NULL sched-domain.
[   20.196572] CPU0 attaching NULL sched-domain.
[   21.408076] CPU0 attaching NULL sched-domain.
[   21.408135] CPU0 attaching NULL sched-domain.
[   28.440022] eth0: no IPv6 routers present
[  532.292019] cx88[0]: video y / packed - dma channel status dump
[  532.292027] cx88[0]:   cmds: initial risc: 0x35312000
[  532.292031] cx88[0]:   cmds: cdt base    : 0x00180440
[  532.292035] cx88[0]:   cmds: cdt size    : 0x0000000c
[  532.292039] cx88[0]:   cmds: iq base     : 0x00180400
[  532.292044] cx88[0]:   cmds: iq size     : 0x00000010
[  532.292050] cx88[0]:   cmds: risc pc     : 0x209f2f68
[  532.292054] cx88[0]:   cmds: iq wr ptr   : 0x00000108
[  532.292058] cx88[0]:   cmds: iq rd ptr   : 0x0000010e
[  532.292062] cx88[0]:   cmds: cdt current : 0x00000458
[  532.292066] cx88[0]:   cmds: pci target  : 0x2083a540
[  532.292069] cx88[0]:   cmds: line / byte : 0x02490000
[  532.292073] cx88[0]:   risc0: 0x18000520 [ write sol count=1312 ]
[  532.292080] cx88[0]:   risc1: 0x2083aae0 [ arg #1 ]
[  532.292085] cx88[0]:   risc2: 0x14000080 [ write eol count=128 ]
[  532.292091] cx88[0]:   risc3: 0x2083b000 [ arg #1 ]
[  532.292095] cx88[0]:   iq 0: 0x1c0005a0 [ write sol eol count=1440 ]
[  532.292104] cx88[0]:   iq 1: 0x2083b620 [ arg #1 ]
[  532.292109] cx88[0]:   iq 2: 0x1c0005a0 [ write sol eol count=1440 ]
[  532.292117] cx88[0]:   iq 3: 0x2083c160 [ arg #1 ]
[  532.292120] cx88[0]:   iq 4: 0x18000360 [ write sol count=864 ]
[  532.292127] cx88[0]:   iq 5: 0x2083cca0 [ arg #1 ]
[  532.292130] cx88[0]:   iq 6: 0x14000240 [ write eol count=576 ]
[  532.292136] cx88[0]:   iq 7: 0x2083d000 [ arg #1 ]
[  532.292140] cx88[0]:   iq 8: 0x1c0005a0 [ write sol eol count=1440 ]
[  532.292147] cx88[0]:   iq 9: 0x2083d7e0 [ arg #1 ]
[  532.292150] cx88[0]:   iq a: 0x1c0005a0 [ write sol eol count=1440 ]
[  532.292160] cx88[0]:   iq b: 0x2083e320 [ arg #1 ]
[  532.292165] cx88[0]:   iq c: 0x180001a0 [ write sol count=416 ]
[  532.292172] cx88[0]:   iq d: 0x2083ee60 [ arg #1 ]
[  532.292176] cx88[0]:   iq e: 0x14000400 [ write eol count=1024 ]
[  532.292182] cx88[0]:   iq f: 0x2083f000 [ arg #1 ]
[  532.292185] cx88[0]: fifo: 0x00180c00 -> 0x183400
[  532.292188] cx88[0]: ctrl: 0x00180400 -> 0x180460
[  532.292192] cx88[0]:   ptr1_reg: 0x00181ce0
[  532.292195] cx88[0]:   ptr2_reg: 0x00180478
[  532.292198] cx88[0]:   cnt1_reg: 0x00000000
[  532.292202] cx88[0]:   cnt2_reg: 0x00000000
[  532.292211] cx88[0]/0: [f104df00/2] timeout - dma=0x209f2000
[  532.292214] cx88[0]/0: [f7004d80/3] timeout - dma=0x35314000
[ 1271.045145] NET: Registered protocol family 24
```

I did run tvtime-scanner and it returned no signal after scanning the entire range.

```
01:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: PROLINK Microsystems Corp Device 4976
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

01:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
    Subsystem: PROLINK Microsystems Corp Device 4976
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

```

Can someone help me out to detect the problems in my configuration?

---

### Post by abhilash82 on 2010-09-29
Can someone help me out on this problem? I have tried most of the solutions described in this forum (and some external links too) but haven't been able to fix my tuner card.

---

