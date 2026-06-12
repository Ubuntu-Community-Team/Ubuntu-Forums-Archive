---
title: "kworld mce 200 deluxe not recognized"
date: 2011-06-15
forum: Mythbuntu
---

### Post by jdefed on 2011-06-15
hi

i am attempting to make a simple dvr/pvr. at this time i do not need any tv guide as i will be setting up manual recordings. before i purchase anything i would like to use stuff i have laying around. i have installed mythbuntu 11.04 with no issues. i have seen where this tv tuner can have problems. is it worth my time to try and get it to work. i will be hooking up a converter box to it if i can get it to work. this is my first venture into linux so im not very good with terminal. to start here is the dmesg.

jd@jd-System-Product-Name:~/Desktop$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe90000 (usable)
[    0.000000]  BIOS-e820: 000000006fe90000 - 000000006fea8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fea8000 - 000000006fed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fed0000 - 000000006ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M4A785TD-M EVO, BIOS 2103    06/30/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6fe90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677c000 - 373b6000
[    0.000000] ACPI: RSDP 000fb4e0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 6fe90100 0005C (v01 063010 XSDT1927 20100630 MSFT 00000097)
[    0.000000] ACPI: FACP 6fe90290 000F4 (v03 063010 FACP1927 20100630 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110112/tbfadt-557)
[    0.000000] ACPI: DSDT 6fe90450 0DD62 (v01  A1391 A1391001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 6fea8000 00040
[    0.000000] ACPI: APIC 6fe90390 0007C (v01 063010 APIC1927 20100630 MSFT 00000097)
[    0.000000] ACPI: MCFG 6fe90410 0003C (v01 063010 OEMMCFG  20100630 MSFT 00000097)
[    0.000000] ACPI: OEMB 6fea8040 00072 (v01 063010 OEMB1927 20100630 MSFT 00000097)
[    0.000000] ACPI: SRAT 6fe9f450 00090 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 6fe9f4e0 00038 (v01 063010 OEMHPET  20100630 MSFT 00000097)
[    0.000000] ACPI: SSDT 6fe9f520 0023E (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 902MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0006fe90
[    0.000000] On node 0 totalpages: 458270
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f597c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1806 pages used for memmap
[    0.000000]   HighMem zone: 229252 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 5 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 6ff00000 (gap: 6ff00000:8f800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5400000 s28800 r0 d24448 u524288
[    0.000000] pcpu-alloc: s28800 r0 d24448 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454688
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=d238899a-8395-4193-a513-d1a213b9a77f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9167360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0006fe90)
[    0.000000] Memory: 1786756k/1833536k available (5188k kernel code, 46324k reserved, 2540k data, 700k init, 924232k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:728 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2800.310 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5600.62 BogoMIPS (lpj=11201240)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004030] Security Framework initialized
[    0.004045] AppArmor: AppArmor initialized
[    0.004046] Yama: becoming mindful.
[    0.004098] Mount-cache hash table entries: 512
[    0.004204] Initializing cgroup subsys ns
[    0.004207] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004211] Initializing cgroup subsys cpuacct
[    0.004215] Initializing cgroup subsys memory
[    0.004223] Initializing cgroup subsys devices
[    0.004226] Initializing cgroup subsys freezer
[    0.004228] Initializing cgroup subsys net_cls
[    0.004230] Initializing cgroup subsys blkio
[    0.004257] mce: CPU supports 6 MCE banks
[    0.004733] SMP alternatives: switching to UP code
[    0.012901] ACPI: Core revision 20110112
[    0.020009] ftrace: allocating 23640 entries in 47 pages
[    0.024060] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024350] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066858] CPU0: AMD Sempron(tm) 145 Processor stepping 03
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] Brought up 1 CPUs
[    0.068003] Total of 1 processors activated (5600.62 BogoMIPS).
[    0.068003] devtmpfs: initialized
[    0.068003] print_constraints: dummy: 
[    0.068003] Time: 16:48:37  Date: 06/15/11
[    0.068003] NET: Registered protocol family 16
[    0.068003] EISA bus registered
[    0.068003] node 0 link 0: io port [1000, ffffff]
[    0.068003] TOM: 0000000080000000 aka 2048M
[    0.068003] Fam 10h mmconf [e0000000, efffffff]
[    0.068003] node 0 link 0: mmio [a0000, bffff]
[    0.068003] node 0 link 0: mmio [80000000, cfffffff]
[    0.068003] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.068003] node 0 link 0: mmio [f0000000, fabfffff]
[    0.068003] node 0 link 0: mmio [fac00000, fadfffff]
[    0.068003] node 0 link 0: mmio [fae00000, ffefffff]
[    0.068003] bus: [00, 07] on node 0 link 0
[    0.068003] bus: 00 index 0 [io  0x0000-0xffff]
[    0.068003] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.068003] bus: 00 index 2 [mem 0x80000000-0xdfffffff]
[    0.068003] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.068003] Extended Config Space enabled on 1 nodes
[    0.068003] ACPI: bus type pci registered
[    0.068003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.068003] PCI: not using MMCONFIG
[    0.068003] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.068003] PCI: Using configuration type 1 for base access
[    0.068003] PCI: Using configuration type 1 for extended access
[    0.068003] bio: create slab <bio-0> at 0
[    0.068003] ACPI: EC: Look up EC in DSDT
[    0.069152] ACPI: Executed 3 blocks of module-level executable AML code
[    0.100544] ACPI: Interpreter enabled
[    0.100549] ACPI: (supports S0 S1 S3 S4 S5)
[    0.100568] ACPI: Using IOAPIC for interrupt routing
[    0.100588] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.101793] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.101795] PCI: Using MMCONFIG for extended config space
[    0.106103] ACPI: No dock devices found.
[    0.106105] HEST: Table not found.
[    0.106108] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.106171] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.106299] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.106301] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.106303] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.106305] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.106307] pci_root PNP0A03:00: host bridge window [mem 0x6ff00000-0xdfffffff]
[    0.106309] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.106321] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.106355] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.106386] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
[    0.106407] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.106410] pci 0000:00:07.0: PME# disabled
[    0.106423] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.106444] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.106446] pci 0000:00:0a.0: PME# disabled
[    0.106470] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.106489] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.106498] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.106507] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.106516] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.106525] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.106534] pci 0000:00:11.0: reg 24: [mem 0xfabffc00-0xfabfffff]
[    0.106553] pci 0000:00:11.0: set SATA to AHCI mode
[    0.106584] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.106597] pci 0000:00:12.0: reg 10: [mem 0xfabfe000-0xfabfefff]
[    0.106656] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.106669] pci 0000:00:12.1: reg 10: [mem 0xfabfd000-0xfabfdfff]
[    0.106733] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.106751] pci 0000:00:12.2: reg 10: [mem 0xfabff800-0xfabff8ff]
[    0.106817] pci 0000:00:12.2: supports D1 D2
[    0.106818] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.106822] pci 0000:00:12.2: PME# disabled
[    0.106841] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.106854] pci 0000:00:13.0: reg 10: [mem 0xfabfc000-0xfabfcfff]
[    0.106912] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.106925] pci 0000:00:13.1: reg 10: [mem 0xfabfb000-0xfabfbfff]
[    0.106989] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.107006] pci 0000:00:13.2: reg 10: [mem 0xfabff400-0xfabff4ff]
[    0.107072] pci 0000:00:13.2: supports D1 D2
[    0.107074] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.107077] pci 0000:00:13.2: PME# disabled
[    0.107099] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.107185] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.107201] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.107209] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.107218] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.107227] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.107236] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.107283] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.107303] pci 0000:00:14.2: reg 10: [mem 0xfabf4000-0xfabf7fff 64bit]
[    0.107357] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.107361] pci 0000:00:14.2: PME# disabled
[    0.107372] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.107441] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.107478] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.107491] pci 0000:00:14.5: reg 10: [mem 0xfabfa000-0xfabfafff]
[    0.107552] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.107564] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.107574] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.107584] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.107595] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.107631] pci 0000:01:05.0: [1002:9710] type 0 class 0x000300
[    0.107638] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.107643] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.107647] pci 0000:01:05.0: reg 18: [mem 0xfadf0000-0xfadfffff]
[    0.107655] pci 0000:01:05.0: reg 24: [mem 0xfac00000-0xfacfffff]
[    0.107665] pci 0000:01:05.0: supports D1 D2
[    0.107673] pci 0000:01:05.1: [1002:970f] type 0 class 0x000403
[    0.107680] pci 0000:01:05.1: reg 10: [mem 0xfade8000-0xfadebfff]
[    0.107701] pci 0000:01:05.1: supports D1 D2
[    0.107735] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.107739] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.107741] pci 0000:00:01.0:   bridge window [mem 0xfac00000-0xfadfffff]
[    0.107744] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.107778] pci 0000:02:00.0: [197b:2380] type 0 class 0x000c00
[    0.107796] pci 0000:02:00.0: reg 10: [mem 0xfaeff800-0xfaefffff]
[    0.107809] pci 0000:02:00.0: reg 14: [mem 0xfaeff400-0xfaeff47f]
[    0.107845] pci 0000:02:00.0: reg 20: [mem 0xfaeff000-0xfaeff07f]
[    0.107858] pci 0000:02:00.0: reg 24: [mem 0xfaefec00-0xfaefec7f]
[    0.112030] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.112035] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.112038] pci 0000:00:07.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    0.112042] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.112077] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.112091] pci 0000:03:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.112110] pci 0000:03:00.0: reg 18: [mem 0xf9fff000-0xf9ffffff 64bit pref]
[    0.112123] pci 0000:03:00.0: reg 20: [mem 0xf9ff8000-0xf9ffbfff 64bit pref]
[    0.112132] pci 0000:03:00.0: reg 30: [mem 0xfaff0000-0xfaffffff pref]
[    0.112160] pci 0000:03:00.0: supports D1 D2
[    0.112162] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112165] pci 0000:03:00.0: PME# disabled
[    0.120030] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.120035] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.120038] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff]
[    0.120041] pci 0000:00:0a.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.120078] pci 0000:04:05.0: [14f1:8800] type 0 class 0x000400
[    0.120102] pci 0000:04:05.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.120209] pci 0000:04:05.1: [14f1:8801] type 0 class 0x000480
[    0.120230] pci 0000:04:05.1: reg 10: [mem 0xfc000000-0xfcffffff]
[    0.120327] pci 0000:04:05.2: [14f1:8802] type 0 class 0x000480
[    0.120347] pci 0000:04:05.2: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.120478] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.120482] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.120485] pci 0000:00:14.4:   bridge window [mem 0xfb000000-0xfdffffff]
[    0.120489] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.120492] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.120494] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.120496] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.120498] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.120500] pci 0000:00:14.4:   bridge window [mem 0x6ff00000-0xdfffffff] (subtractive decode)
[    0.120502] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.120513] pci_bus 0000:00: on NUMA node 0
[    0.120518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.120694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.120725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.120749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.120780] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.120829]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.124123] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.124154] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.124181] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.124207] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.124232] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.124258] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.124286] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 *10 11 12 14 15)
[    0.124312] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.124380] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.124383] vgaarb: loaded
[    0.124510] SCSI subsystem initialized
[    0.124545] libata version 3.00 loaded.
[    0.124574] usbcore: registered new interface driver usbfs
[    0.124583] usbcore: registered new interface driver hub
[    0.124597] usbcore: registered new device driver usb
[    0.124723] wmi: Mapper loaded
[    0.124725] PCI: Using ACPI for IRQ routing
[    0.124727] PCI: pci_cache_line_size set to 64 bytes
[    0.124800] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.124802] reserve RAM buffer: 000000006fe90000 - 000000006fffffff 
[    0.124865] NetLabel: Initializing
[    0.124867] NetLabel:  domain hash size = 128
[    0.124868] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.124876] NetLabel:  unlabeled traffic allowed by default
[    0.124902] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.124905] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.126922] Switching to clocksource hpet
[    0.126927] Switched to NOHz mode on CPU #0
[    0.128015] AppArmor: AppArmor Filesystem Enabled
[    0.128037] pnp: PnP ACPI init
[    0.128052] ACPI: bus type pnp registered
[    0.128146] pnp 00:00: [bus 00-ff]
[    0.128150] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.128152] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.128154] pnp 00:00: [io  0x0d00-0xffff window]
[    0.128156] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.128157] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.128159] pnp 00:00: [mem 0x6ff00000-0xdfffffff window]
[    0.128161] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.128200] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.128268] pnp 00:01: [mem 0x00000000-0xffffffff disabled]
[    0.128270] pnp 00:01: [mem 0x70000000-0x7fffffff]
[    0.128307] system 00:01: [mem 0x70000000-0x7fffffff] has been reserved
[    0.128309] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128336] pnp 00:02: [dma 4]
[    0.128338] pnp 00:02: [io  0x0000-0x000f]
[    0.128339] pnp 00:02: [io  0x0081-0x0083]
[    0.128341] pnp 00:02: [io  0x0087]
[    0.128342] pnp 00:02: [io  0x0089-0x008b]
[    0.128344] pnp 00:02: [io  0x008f]
[    0.128345] pnp 00:02: [io  0x00c0-0x00df]
[    0.128363] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.128370] pnp 00:03: [io  0x0070-0x0071]
[    0.128378] pnp 00:03: [irq 8]
[    0.128397] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.128403] pnp 00:04: [io  0x0061]
[    0.128420] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.128426] pnp 00:05: [io  0x00f0-0x00ff]
[    0.128429] pnp 00:05: [irq 13]
[    0.128447] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.128985] pnp 00:06: [io  0x0378-0x037f]
[    0.128988] pnp 00:06: [irq 7]
[    0.128990] pnp 00:06: [dma 0 disabled]
[    0.129184] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.129209] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.129228] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.129618] pnp 00:08: [io  0x03f8-0x03ff]
[    0.129622] pnp 00:08: [irq 4]
[    0.129623] pnp 00:08: [dma 0 disabled]
[    0.129682] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.129736] pnp 00:09: [io  0x0060]
[    0.129738] pnp 00:09: [io  0x0064]
[    0.129739] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.129741] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.129774] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.129776] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.129779] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.129882] pnp 00:0a: [io  0x0010-0x001f]
[    0.129884] pnp 00:0a: [io  0x0022-0x003f]
[    0.129885] pnp 00:0a: [io  0x0062-0x0063]
[    0.129887] pnp 00:0a: [io  0x0065-0x006f]
[    0.129889] pnp 00:0a: [io  0x0072-0x007f]
[    0.129891] pnp 00:0a: [io  0x0080]
[    0.129892] pnp 00:0a: [io  0x0084-0x0086]
[    0.129893] pnp 00:0a: [io  0x0088]
[    0.129895] pnp 00:0a: [io  0x008c-0x008e]
[    0.129896] pnp 00:0a: [io  0x0090-0x009f]
[    0.129898] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.129899] pnp 00:0a: [io  0x00b1]
[    0.129900] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.129902] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.129903] pnp 00:0a: [io  0x040b]
[    0.129905] pnp 00:0a: [io  0x04d6]
[    0.129906] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.129907] pnp 00:0a: [io  0x0c14]
[    0.129909] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.129910] pnp 00:0a: [io  0x0c52]
[    0.129911] pnp 00:0a: [io  0x0c6c]
[    0.129913] pnp 00:0a: [io  0x0c6f]
[    0.129914] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.129915] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.129917] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.129918] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.129920] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.129921] pnp 00:0a: [io  0x0b00-0x0b3f]
[    0.129923] pnp 00:0a: [io  0x0800-0x089f]
[    0.129924] pnp 00:0a: [io  0x0000-0xffffffff disabled]
[    0.129926] pnp 00:0a: [io  0x0b00-0x0b0f]
[    0.129927] pnp 00:0a: [io  0x0b20-0x0b3f]
[    0.129929] pnp 00:0a: [io  0x0900-0x090f]
[    0.129930] pnp 00:0a: [io  0x0910-0x091f]
[    0.129932] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.129933] pnp 00:0a: [io  0x0060]
[    0.129934] pnp 00:0a: [io  0x0064]
[    0.129936] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.129938] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.129939] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.130010] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.130013] system 00:0a: [io  0x040b] has been reserved
[    0.130014] system 00:0a: [io  0x04d6] has been reserved
[    0.130016] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.130018] system 00:0a: [io  0x0c14] has been reserved
[    0.130020] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.130022] system 00:0a: [io  0x0c52] has been reserved
[    0.130024] system 00:0a: [io  0x0c6c] has been reserved
[    0.130026] system 00:0a: [io  0x0c6f] has been reserved
[    0.130028] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.130030] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.130032] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.130034] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.130036] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.130038] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.130040] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.130042] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
[    0.130044] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.130046] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.130048] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.130050] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.130053] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.130055] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.130057] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.130059] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130166] pnp 00:0b: [io  0x0000-0xffffffff disabled]
[    0.130168] pnp 00:0b: [io  0x0230-0x023f]
[    0.130170] pnp 00:0b: [io  0x0290-0x029f]
[    0.130171] pnp 00:0b: [io  0x0300-0x030f]
[    0.130173] pnp 00:0b: [io  0x0a30-0x0a3f]
[    0.130204] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.130206] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.130208] system 00:0b: [io  0x0300-0x030f] has been reserved
[    0.130210] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.130212] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130235] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.130265] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.130267] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130459] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.130461] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.130462] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.130464] pnp 00:0d: [mem 0x00100000-0x6fefffff]
[    0.130465] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.130501] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.130504] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.130506] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.130508] system 00:0d: [mem 0x00100000-0x6fefffff] could not be reserved
[    0.130510] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.130512] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.130585] pnp: PnP ACPI: found 14 devices
[    0.130586] ACPI: ACPI bus type pnp unregistered
[    0.130589] PnPBIOS: Disabled by ACPI PNP
[    0.166243] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.166245] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.166248] pci 0000:00:01.0:   bridge window [mem 0xfac00000-0xfadfffff]
[    0.166251] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.166254] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.166256] pci 0000:00:07.0:   bridge window [io  disabled]
[    0.166258] pci 0000:00:07.0:   bridge window [mem 0xfae00000-0xfaefffff]
[    0.166261] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.166264] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.166266] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
[    0.166268] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff]
[    0.166271] pci 0000:00:0a.0:   bridge window [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.166275] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.166276] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.166282] pci 0000:00:14.4:   bridge window [mem 0xfb000000-0xfdffffff]
[    0.166285] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.166301] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.166303] pci 0000:00:07.0: setting latency timer to 64
[    0.166309] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.166311] pci 0000:00:0a.0: setting latency timer to 64
[    0.166318] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.166320] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.166322] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.166324] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.166326] pci_bus 0000:00: resource 8 [mem 0x6ff00000-0xdfffffff]
[    0.166328] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.166330] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.166332] pci_bus 0000:01: resource 1 [mem 0xfac00000-0xfadfffff]
[    0.166334] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.166336] pci_bus 0000:02: resource 1 [mem 0xfae00000-0xfaefffff]
[    0.166338] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.166340] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfaffffff]
[    0.166342] pci_bus 0000:03: resource 2 [mem 0xf9f00000-0xf9ffffff 64bit pref]
[    0.166344] pci_bus 0000:04: resource 1 [mem 0xfb000000-0xfdffffff]
[    0.166346] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.166348] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.166350] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.166352] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.166354] pci_bus 0000:04: resource 8 [mem 0x6ff00000-0xdfffffff]
[    0.166356] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.166381] NET: Registered protocol family 2
[    0.166427] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.166580] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.166959] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.167152] TCP: Hash tables configured (established 131072 bind 65536)
[    0.167153] TCP reno registered
[    0.167156] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167162] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167235] NET: Registered protocol family 1
[    0.167244] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.328052] pci 0000:01:05.0: Boot video device
[    0.328067] PCI: CLS 64 bytes, default 64
[    0.328208] cpufreq-nforce2: No nForce2 chipset.
[    0.328297] audit: initializing netlink socket (disabled)
[    0.328304] type=2000 audit(1308156517.328:1): initialized
[    0.335595] Trying to unpack rootfs image as initramfs...
[    0.348211] highmem bounce pool size: 64 pages
[    0.348216] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.353159] VFS: Disk quotas dquot_6.5.2
[    0.353203] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.360094] fuse init (API version 7.16)
[    0.360180] msgmni has been set to 1684
[    0.364256] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.364282] io scheduler noop registered
[    0.364283] io scheduler deadline registered
[    0.364297] io scheduler cfq registered (default)
[    0.364386] pcieport 0000:00:07.0: setting latency timer to 64
[    0.364411] pcieport 0000:00:07.0: irq 40 for MSI/MSI-X
[    0.364445] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.364464] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    0.364511] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.364526] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.364628] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.364632] ACPI: Power Button [PWRB]
[    0.364666] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.364669] ACPI: Power Button [PWRF]
[    0.364775] ACPI: acpi_idle registered with cpuidle
[    0.366267] ERST: Table is not found!
[    0.366334] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.386786] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.386806] isapnp: Scanning for PnP cards...
[    0.477138] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.496264] Linux agpgart interface v0.103
[    0.497245] brd: module loaded
[    0.497610] loop: module loaded
[    0.497671] i2c-core: driver [adp5520] using legacy suspend method
[    0.497672] i2c-core: driver [adp5520] using legacy resume method
[    0.497763] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.497785] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.498009] Fixed MDIO Bus: probed
[    0.498034] PPP generic driver version 2.4.2
[    0.498058] tun: Universal TUN/TAP device driver, 1.6
[    0.498059] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.498109] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.498123] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.498131] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.498155] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.498165] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.498182] ehci_hcd 0000:00:12.2: debug port 1
[    0.498201] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfabff800
[    0.508033] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.508149] hub 1-0:1.0: USB hub found
[    0.508152] hub 1-0:1.0: 6 ports detected
[    0.508217] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.508234] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.508260] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.508269] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.508290] ehci_hcd 0000:00:13.2: debug port 1
[    0.508311] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfabff400
[    0.551894] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.551974] hub 2-0:1.0: USB hub found
[    0.551976] hub 2-0:1.0: 6 ports detected
[    0.628082] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.628101] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.628120] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.628162] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.628188] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfabfe000
[    0.708144] hub 3-0:1.0: USB hub found
[    0.708150] hub 3-0:1.0: 3 ports detected
[    0.708209] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.708227] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.708259] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.708277] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfabfd000
[    0.796314] hub 4-0:1.0: USB hub found
[    0.796320] hub 4-0:1.0: 3 ports detected
[    0.796380] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.796399] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.796428] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.796454] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfabfc000
[    0.859723] hub 5-0:1.0: USB hub found
[    0.859729] hub 5-0:1.0: 3 ports detected
[    0.859789] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.859806] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.859835] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.859851] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfabfb000
[    0.940753] Freeing initrd memory: 12520k freed
[    0.987748] isapnp: No Plug & Play device found
[    0.987772] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    0.987917] hub 6-0:1.0: USB hub found
[    0.987923] hub 6-0:1.0: 3 ports detected
[    0.987985] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.988016] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.988049] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.988066] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfabfa000
[    1.048156] hub 7-0:1.0: USB hub found
[    1.048163] hub 7-0:1.0: 2 ports detected
[    1.048221] uhci_hcd: USB Universal Host Controller Interface driver
[    1.048285] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.048631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.048636] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.048682] mousedev: PS/2 mouse device common for all mice
[    1.048758] rtc_cmos 00:03: RTC can wake from S4
[    1.048787] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.048809] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.048867] device-mapper: uevent: version 1.0.3
[    1.048921] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.048965] device-mapper: multipath: version 1.2.0 loaded
[    1.048967] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.049015] EISA: Probing bus 0 at eisa.0
[    1.049017] EISA: Cannot allocate resource for mainboard
[    1.049019] Cannot allocate resource for EISA slot 1
[    1.049020] Cannot allocate resource for EISA slot 2
[    1.049021] Cannot allocate resource for EISA slot 3
[    1.049022] Cannot allocate resource for EISA slot 4
[    1.049024] Cannot allocate resource for EISA slot 5
[    1.049025] Cannot allocate resource for EISA slot 6
[    1.049026] Cannot allocate resource for EISA slot 7
[    1.049027] Cannot allocate resource for EISA slot 8
[    1.049029] EISA: Detected 0 cards.
[    1.049058] cpuidle: using governor ladder
[    1.049060] cpuidle: using governor menu
[    1.049231] TCP cubic registered
[    1.049318] NET: Registered protocol family 10
[    1.049691] NET: Registered protocol family 17
[    1.049700] Registering the dns_resolver key type
[    1.049712] powernow-k8: Found 1 AMD Sempron(tm) 145 Processor (1 cpu cores) (version 2.20.00)
[    1.049740] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.049741] powernow-k8:    1 : pstate 1 (2000 MHz)
[    1.049742] powernow-k8:    2 : pstate 2 (1600 MHz)
[    1.049744] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.050001] Using IPI No-Shortcut mode
[    1.050058] PM: Hibernation image not present or could not be loaded.
[    1.050065] registered taskstats version 1
[    1.050290]   Magic number: 15:610:843
[    1.050358] rtc_cmos 00:03: setting system clock to 2011-06-15 16:48:38 UTC (1308156518)
[    1.050360] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.050361] EDD information not available.
[    1.050415] Freeing unused kernel memory: 700k freed
[    1.050580] Write protecting the kernel text: 5192k
[    1.050603] Write protecting the kernel read-only data: 2148k
[    1.064951] <30>udev[59]: starting version 167
[    1.117516] hub 2-1:1.0: USB hub found
[    1.117617] hub 2-1:1.0: 7 ports detected
[    1.199857] scsi0 : pata_atiixp
[    1.202216] scsi1 : pata_atiixp
[    1.202692] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.202694] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.222548] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.222565] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.222594] r8169 0000:03:00.0: setting latency timer to 64
[    1.222633] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    1.222968] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf804c000, 20:cf:30:4f:5c:0f, XID 083000c0 IRQ 42
[    1.332038] Refined TSC clocksource calibration: 2800.194 MHz.
[    1.332043] Switching to clocksource tsc
[    1.368020] ata1.00: ATA-5: QUANTUM FIREBALLP LM20.5, A35.0700, max UDMA/66
[    1.368023] ata1.00: 40132503 sectors, multi 16: LBA 
[    1.384712] ata1.00: configured for UDMA/66
[    1.384797] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A35. PQ: 0 ANSI: 5
[    1.384924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.385091] sd 0:0:0:0: [sda] 40132503 512-byte logical blocks: (20.5 GB/19.1 GiB)
[    1.385119] sd 0:0:0:0: [sda] Write Protect is off
[    1.385122] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.385134] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.413739]  sda: sda1 sda2 < sda5 >
[    1.414033] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.421789] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.421796] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    1.421854] ahci 0000:00:11.0: version 3.0
[    1.421869] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.421958] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.421961] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.422604] scsi2 : ahci
[    1.422681] scsi3 : ahci
[    1.422751] scsi4 : ahci
[    1.422819] scsi5 : ahci
[    1.422925] ata3: SATA max UDMA/133 abar m1024@0xfabffc00 port 0xfabffd00 irq 22
[    1.422928] ata4: SATA max UDMA/133 abar m1024@0xfabffc00 port 0xfabffd80 irq 22
[    1.422931] ata5: SATA max UDMA/133 abar m1024@0xfabffc00 port 0xfabffe00 irq 22
[    1.422934] ata6: SATA max UDMA/133 abar m1024@0xfabffc00 port 0xfabffe80 irq 22
[    1.436036] usb 5-2: new low speed USB device using ohci_hcd and address 2
[    1.484093] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x10
[    1.623891] input: 2.4GHz RF  KEYBOARD  AND  MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input2
[    1.623999] generic-usb 0003:1BCF:05C5.0001: input,hidraw0: USB HID v1.00 Keyboard [2.4GHz RF  KEYBOARD  AND  MOUSE] on usb-0000:00:13.0-2/input0
[    1.632052] input: 2.4GHz RF  KEYBOARD  AND  MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input3
[    1.632349] generic-usb 0003:1BCF:05C5.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [2.4GHz RF  KEYBOARD  AND  MOUSE] on usb-0000:00:13.0-2/input1
[    1.632444] usbcore: registered new interface driver usbhid
[    1.632445] usbhid: USB HID core driver
[    1.680314] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[    1.740066] ata6: SATA link down (SStatus 0 SControl 300)
[    1.740102] ata5: SATA link down (SStatus 0 SControl 300)
[    1.740150] ata3: SATA link down (SStatus 0 SControl 300)
[    1.796580] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.912029] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.914445] ata4.00: ATAPI: ATAPI   iHAS124   B, AL0F, max UDMA/100
[    1.915260] ata4.00: configured for UDMA/100
[    1.917425] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0F PQ: 0 ANSI: 5
[    1.920778] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.920782] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.920882] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.920932] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.984100] firewire_core: created device fw0: GUID 001fc6000002a00f, S400
[   17.819067] <30>udev[316]: starting version 167
[   17.845250] lp: driver loaded but no devices found
[   17.864240] Adding 1831932k swap on /dev/sda5.  Priority:-1 extents:1 across:1831932k 
[   18.014953] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.059144] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   18.059147] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.059923] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   18.060099] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   18.066789] type=1400 audit(1308156535.510:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=482 comm="apparmor_parser"
[   18.067073] type=1400 audit(1308156535.510:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=482 comm="apparmor_parser"
[   18.067253] type=1400 audit(1308156535.510:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=482 comm="apparmor_parser"
[   18.068986] type=1400 audit(1308156535.514:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=490 comm="apparmor_parser"
[   18.069277] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.390066] type=1400 audit(1308156535.834:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=634 comm="apparmor_parser"
[   18.395818] type=1400 audit(1308156535.838:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
[   18.396030] type=1400 audit(1308156535.842:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
[   18.403690] type=1400 audit(1308156535.846:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=639 comm="apparmor_parser"
[   18.408530] type=1400 audit(1308156535.854:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=640 comm="apparmor_parser"
[   18.414186] type=1400 audit(1308156535.858:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=642 comm="apparmor_parser"
[   18.468823] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   18.468826] Disabling lock debugging due to kernel taint
[   18.500751] parport_pc 00:06: reported by Plug and Play ACPI
[   18.500802] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.540553] Linux video capture interface: v2.00
[   18.636186] IR NEC protocol handler initialized
[   18.681743] r8169 0000:03:00.0: eth0: link down
[   18.682181] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.697546] IR RC5(x) protocol handler initialized
[   18.724914] IR RC6 protocol handler initialized
[   18.762367] IR JVC protocol handler initialized
[   18.787301] IR Sony protocol handler initialized
[   18.802447] lirc_dev: IR Remote Control driver registered, major 249 
[   18.803374] IR LIRC bridge handler initialized
[   18.830761] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   18.882093] lp0: using parport0 (interrupt-driven).
[   18.888448] ppdev: user-space parallel port driver
[   18.912721] r8712u: DriverVersion: v7_0.20100831
[   18.912736] r8712u: register rtl8712_netdev_ops to netdev_ops
[   18.912738] r8712u: USB_SPEED_HIGH with 4 endpoints
[   18.924922] r8712u: Boot from EFUSE: Autoload OK
[   18.941555] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   18.942850] cx88[0]: subsystem: 17de:0840, board: KWorld HardwareMpegTV XPert [card=45,autodetected], frontend(s): 0
[   18.942853] cx88[0]: TV tuner type 54, Radio tuner type -1
[   18.964558] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   19.061971] cx2388x alsa driver version 0.0.8 loaded
[   19.075309] i2c-core: driver [tuner] using legacy suspend method
[   19.075312] i2c-core: driver [tuner] using legacy resume method
[   19.124741] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.129169] [fglrx] Maximum main memory to use for locked dma buffers: 1642 MBytes.
[   19.129208] [fglrx]   vendor: 1002 device: 9710 count: 1
[   19.129439] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[   19.129450] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.129453] pci 0000:01:05.0: setting latency timer to 64
[   19.129679] [fglrx] Kernel PAT support is enabled
[   19.129694] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   19.135443] tuner 0-004b: chip found @ 0x96 (cx88[0])
[   19.212701] tda829x 0-004b: setting tuner address to 61
[   19.224564] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   19.224599] HDA Intel 0000:01:05.1: setting latency timer to 64
[   19.240079] tda829x 0-004b: type set to tda8290+75
[   19.854396] r8712u: CustomerID = 0x0000
[   19.854399] r8712u: MAC Address from efuse = 00:02:6f:98:65:3a
[   19.855544] usbcore: registered new interface driver r8712u
[   20.311178] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   20.549263] cx88[0]/2: cx2388x 8802 Driver Manager
[   20.549283] cx88-mpeg driver manager 0000:04:05.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   20.549292] cx88[0]/2: found at 0000:04:05.2, rev: 5, irq: 20, latency: 64, mmio: 0xfb000000
[   20.549347] cx8800 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   20.549354] cx88[0]/0: found at 0000:04:05.0, rev: 5, irq: 20, latency: 64, mmio: 0xfd000000
[   20.549453] cx88[0]/0: registered device video0 [v4l2]
[   20.549539] cx88[0]/0: registered device vbi0
[   20.549602] cx88[0]/0: registered device radio0
[   20.585952] r8712u: 1 RCR=0x153f00e
[   20.587331] r8712u: 2 RCR=0x553f00e
[   20.696515] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.781245] cx88_audio 0000:04:05.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.781267] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   21.869007] cx2388x blackbird driver version 0.0.8 loaded
[   21.869010] cx88/2: registering cx8802 driver, type: blackbird access: shared
[   21.869013] cx88[0]/2: subsystem: 17de:0840, board: KWorld HardwareMpegTV XPert [card=45]
[   21.869016] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[   21.869239] cx88[0]/2-bb: Firmware and/or mailbox pointer not initialized or corrupted
[   24.867375] cx88[0]/2-bb: Firmware upload successful.
[   24.874081] cx88[0]/2-bb: Firmware version is 0x02060039
[   24.883735] cx88[0]/2: registered device video1 [mpeg]
[   26.477512] vesafb: framebuffer at 0xd0000000, mapped to 0xfb300000, using 5824k, total 5824k
[   26.477516] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[   26.477518] vesafb: scrolling: redraw
[   26.477520] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   26.477682] Console: switching to colour frame buffer device 175x65
[   26.477709] fb0: VESA VGA frame buffer device
[   26.849914] [fglrx] GART Table is not in FRAME_BUFFER range 
[   26.853539] [fglrx] Could not enable MSI; System prevented initialization
[   26.854669] [fglrx] Firegl kernel thread PID: 1299
[   26.854708] [fglrx] Firegl kernel thread PID: 1300
[   26.854737] [fglrx] Firegl kernel thread PID: 1301
[   26.855032] [fglrx] IRQ 18 Enabled
[   27.461620] [fglrx] Gart USWC size:552 M.
[   27.461623] [fglrx] Gart cacheable size:215 M.
[   27.461627] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   27.461629] [fglrx] Reserved FB block: Unshared offset:16ffb000, size:5000 
[   35.313755] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.760019] wlan0: no IPv6 routers present
jd@jd-System-Product-Name:~/Desktop$ 

i have been searching for answers but get frustrated with terminal and trying to follow the instructions. any help will be appriciated. im also wondering if this program is advanced for a simple dvr/pvr, as im not going to use it for htpc setup.

thanks 
jim

---

### Post by klc5555 on 2011-06-16
This is a card that hasn't generated much traffic since around 2006. Let me state right at the beginning that this is not a card I use.

However, your dmesg output seems to indicate that the card was auto-recognized and configured by the kernel as card=45, which should have been a "KWorld HardwareMpegTV XPert". It appears that perhaps a Kworld MCE 200 Deluxe ought to have been initialized as a card=48, according to the message traffic this card sparked back years ago --relevant thread here: [http://forum.linuxmce.org/index.php?topic=5545.0;wap2](http://forum.linuxmce.org/index.php?topic=5545.0;wap2)

The method used in the thread to solve the problem is a bit obsolete. Nowadays you would need to compose a specialized .conf file placed under /etc/modprobe.d, in which would be placed the line

options cx88xx card=48

which in theory would force the kernel to load the module with the desired parameters at next boot.

Now there's been a lot of water under the bridge in kernel and particularly the V4l modules in the last few years. There might be other issues with this card. But anyway, this is a reasonable first attempt to get it running on current-ish Linux.

---

