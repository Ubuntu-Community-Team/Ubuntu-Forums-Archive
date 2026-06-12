---
title: "Wireless not working on HP dv6000 and dv3"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by kakyoism on 2009-11-14
Wireless worked ok on both Hardy and Jaunty, and initially OK on Karmic.
It stopped working like two days ago with Karmic on two laptops of mine. I didn't remember if there were a system update but it was certainly all of a sudden.

Now it just keeps prompting WEP/WPA on corresponding network with no luck.

lshw -C network as follows:
```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:24:dd:7b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:99:1b:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.104 latency=0 multicast=yes
       resources: irq:28 ioport:c000(size=256) memory:f8200000-f8200fff memory:c0000000-c001ffff(prefetchable)

```

dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 (Ubuntu 2.6.31-14.48-generic-pae)
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D7FFF write-protect
[    0.000000]   D8000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   4 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bf700000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  modified: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 378a0000 - 37fef227
[    0.000000] Allocated new RAMDISK: 008b5000 - 01004227
[    0.000000] Move RAMDISK from 00000000378a0000 - 0000000037fef226 to 008b5000 - 01004226
[    0.000000] ACPI: RSDP 000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT bf6d5aeb 00084 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP bf6dfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bf6d703c 08BBC (v01 HP     30CC     06040000 INTL 20061109)
[    0.000000] ACPI: FACS bf6e2fc0 00040
[    0.000000] ACPI: HPET bf6dfd60 00038 (v01 HP     30CC     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bf6dfd98 0003C (v01 HP     30CC     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR bf6dfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC bf6dfdfa 00068 (v01 HP     30CC     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bf6dfe62 00028 (v01 HP     30CC     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bf6dfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT bf6d6d5f 002DD (v01 HP     30CC     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT bf6d6cb7 000A8 (v01 HP     30CC     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT bf6d60fb 0025F (v01  HP    30CC     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bf6d6055 000A6 (v01  HP    30CC     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT bf6d5b6f 004E6 (v01  HP     30CC    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b4150]              BRK ==> [00008ae000 - 00008b4150]
[    0.000000]   #6 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #7 [00008b5000 - 0001004227]      NEW RAMDISK ==> [00008b5000 - 0001004227]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f8520] f8520
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf6d0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1046123
[    0.000000] free_area_init_node: node 0, pgdat c078bce0, node_mem_map c1005000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 809925 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c3815000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1035882
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=6325364a-a839-42ba-9d84-fd54c68fa347 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 4100700k/5242880k available (4588k kernel code, 82940k reserved, 2148k data, 544k init, 3273544k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
[    0.000000]       .data : 0xc057b314 - 0xc07946e8   (2148 kB)
[    0.000000]       .text : 0xc0100000 - 0xc057b314   (4588 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.181 MHz processor.
[    0.001359] Console: colour VGA+ 80x25
[    0.001362] console [tty0] enabled
[    0.001531] hpet clockevent registered
[    0.001534] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.001541] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.36 BogoMIPS (lpj=7980724)
[    0.001561] Security Framework initialized
[    0.001582] AppArmor: AppArmor initialized
[    0.001589] Mount-cache hash table entries: 512
[    0.001720] Initializing cgroup subsys ns
[    0.001725] Initializing cgroup subsys cpuacct
[    0.001729] Initializing cgroup subsys memory
[    0.001735] Initializing cgroup subsys freezer
[    0.001738] Initializing cgroup subsys net_cls
[    0.001752] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001755] CPU: L2 cache: 2048K
[    0.001757] CPU: Physical Processor ID: 0
[    0.001759] CPU: Processor Core ID: 0
[    0.001763] mce: CPU supports 6 MCE banks
[    0.001771] CPU0: Thermal monitoring enabled (TM2)
[    0.001775] using mwait in idle threads.
[    0.001782] Performance Counters: Core2 events, Intel PMU driver.
[    0.001788] ... version:                 2
[    0.001789] ... bit width:               40
[    0.001791] ... generic counters:        2
[    0.001793] ... value mask:              000000ffffffffff
[    0.001795] ... max period:              000000007fffffff
[    0.001797] ... fixed-purpose counters:  3
[    0.001798] ... counter mask:            0000000700000003
[    0.001803] Checking 'hlt' instruction... OK.
[    0.019136] ACPI: Core revision 20090521
[    0.032406] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075323] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.39 BogoMIPS (lpj=7980782)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.161436] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[    0.161449] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164022] Brought up 2 CPUs
[    0.164025] Total of 2 processors activated (7980.75 BogoMIPS).
[    0.164075] CPU0 attaching sched-domain:
[    0.164078]  domain 0: span 0-1 level MC
[    0.164080]   groups: 0 1
[    0.164086] CPU1 attaching sched-domain:
[    0.164088]  domain 0: span 0-1 level MC
[    0.164091]   groups: 1 0
[    0.164167] Booting paravirtualized kernel on bare hardware
[    0.164211] regulator: core version 0.5
[    0.164211] Time: 15:15:18  Date: 11/14/09
[    0.164211] NET: Registered protocol family 16
[    0.164212] EISA bus registered
[    0.164222] ACPI: bus type pci registered
[    0.164294] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164297] PCI: MCFG area at e0000000 reserved in E820
[    0.164299] PCI: Using MMCONFIG for extended config space
[    0.164301] PCI: Using configuration type 1 for base access
[    0.165332] bio: create slab <bio-0> at 0
[    0.168468] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.168470] ACPI: EC: Look up EC in DSDT
[    0.171706] ACPI: BIOS _OSI(Linux) query ignored
[    0.172842] ACPI: Interpreter enabled
[    0.172849] ACPI: (supports S0 S3 S4 S5)
[    0.172871] ACPI: Using IOAPIC for interrupt routing
[    0.174517] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.200155] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.200158] ACPI: EC: driver started in interrupt mode
[    0.200477] ACPI: No dock devices found.
[    0.201064] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.201164] pci 0000:00:02.0: reg 10 64bit mmio: [0xf8000000-0xf80fffff]
[    0.201173] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.201178] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.201225] pci 0000:00:02.1: reg 10 64bit mmio: [0xf8100000-0xf81fffff]
[    0.201350] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.201424] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.201504] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8604800-0xf8604bff]
[    0.201575] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.201580] pci 0000:00:1a.7: PME# disabled
[    0.201641] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8600000-0xf8603fff]
[    0.201711] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.201716] pci 0000:00:1b.0: PME# disabled
[    0.201815] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.201821] pci 0000:00:1c.0: PME# disabled
[    0.201922] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.201927] pci 0000:00:1c.1: PME# disabled
[    0.202034] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.202040] pci 0000:00:1c.5: PME# disabled
[    0.202111] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.202185] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.202259] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.202338] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8604c00-0xf8604fff]
[    0.202409] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.202414] pci 0000:00:1d.7: PME# disabled
[    0.202593] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.202598] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.202606] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0380 (mask 0007)
[    0.202663] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.202672] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.202680] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.202689] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.202698] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.202782] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
[    0.202791] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
[    0.202800] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
[    0.202809] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
[    0.202819] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.202828] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8604000-0xf86047ff]
[    0.202876] pci 0000:00:1f.2: PME# supported from D3hot
[    0.202881] pci 0000:00:1f.2: PME# disabled
[    0.202918] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.202947] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
[    0.203075] pci 0000:02:00.0: reg 10 64bit mmio: [0xf4000000-0xf4001fff]
[    0.203203] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.203211] pci 0000:02:00.0: PME# disabled
[    0.203301] pci 0000:00:1c.0: bridge io port: [0x4000-0x7fff]
[    0.203307] pci 0000:00:1c.0: bridge 32bit mmio: [0xf4000000-0xf5ffffff]
[    0.203316] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.203384] pci 0000:00:1c.1: bridge io port: [0x8000-0xbfff]
[    0.203390] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.203399] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.203478] pci 0000:08:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.203509] pci 0000:08:00.0: reg 18 64bit mmio: [0xf8200000-0xf8200fff]
[    0.203540] pci 0000:08:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.203606] pci 0000:08:00.0: supports D1 D2
[    0.203608] pci 0000:08:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.203614] pci 0000:08:00.0: PME# disabled
[    0.203699] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.203705] pci 0000:00:1c.5: bridge 32bit mmio: [0xf8200000-0xf82fffff]
[    0.203774] pci 0000:09:09.0: reg 10 32bit mmio: [0xf8300000-0xf83007ff]
[    0.203838] pci 0000:09:09.0: supports D1 D2
[    0.203840] pci 0000:09:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203845] pci 0000:09:09.0: PME# disabled
[    0.203889] pci 0000:09:09.1: reg 10 32bit mmio: [0xf8300800-0xf83008ff]
[    0.203953] pci 0000:09:09.1: supports D1 D2
[    0.203955] pci 0000:09:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203961] pci 0000:09:09.1: PME# disabled
[    0.204010] pci 0000:09:09.2: reg 10 32bit mmio: [0xf8300c00-0xf8300cff]
[    0.204074] pci 0000:09:09.2: supports D1 D2
[    0.204076] pci 0000:09:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204081] pci 0000:09:09.2: PME# disabled
[    0.204126] pci 0000:09:09.3: reg 10 32bit mmio: [0xf8301000-0xf83010ff]
[    0.204189] pci 0000:09:09.3: supports D1 D2
[    0.204191] pci 0000:09:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204196] pci 0000:09:09.3: PME# disabled
[    0.204240] pci 0000:09:09.4: reg 10 32bit mmio: [0xf8301400-0xf83014ff]
[    0.204304] pci 0000:09:09.4: supports D1 D2
[    0.204307] pci 0000:09:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.204312] pci 0000:09:09.4: PME# disabled
[    0.204365] pci 0000:00:1e.0: transparent bridge
[    0.204373] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8300000-0xf83fffff]
[    0.204410] pci_bus 0000:00: on NUMA node 0
[    0.204415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.204640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.204726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.204803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.204909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.213932] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.214041] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.214150] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.214255] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.214361] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.214467] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.214572] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.214678] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.214852] SCSI subsystem initialized
[    0.214872] libata version 3.00 loaded.
[    0.214872] usbcore: registered new interface driver usbfs
[    0.214872] usbcore: registered new interface driver hub
[    0.214872] usbcore: registered new device driver usb
[    0.214872] ACPI: WMI: Mapper loaded
[    0.214872] PCI: Using ACPI for IRQ routing
[    0.224008] Bluetooth: Core ver 2.15
[    0.224021] NET: Registered protocol family 31
[    0.224021] Bluetooth: HCI device and connection manager initialized
[    0.224021] Bluetooth: HCI socket layer initialized
[    0.224021] NetLabel: Initializing
[    0.224021] NetLabel:  domain hash size = 128
[    0.224021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224033] NetLabel:  unlabeled traffic allowed by default
[    0.224061] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.224067] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.240008] pnp: PnP ACPI init
[    0.240017] ACPI: bus type pnp registered
[    0.245218] pnp: PnP ACPI: found 11 devices
[    0.245221] ACPI: ACPI bus type pnp unregistered
[    0.245224] PnPBIOS: Disabled by ACPI PNP
[    0.245235] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.245239] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.245245] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.245248] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.245251] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.245254] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.245257] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.245260] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.245267] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.245274] system 00:06: ioport range 0x380-0x383 has been reserved
[    0.245277] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.245280] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.245283] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.245286] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.245289] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.245292] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.245297] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.245300] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.279964] AppArmor: AppArmor Filesystem Enabled
[    0.280041] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.280046] pci 0000:00:1c.0:   IO window: 0x4000-0x7fff
[    0.280054] pci 0000:00:1c.0:   MEM window: 0xf4000000-0xf5ffffff
[    0.280061] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.280071] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.280075] pci 0000:00:1c.1:   IO window: 0x8000-0xbfff
[    0.280083] pci 0000:00:1c.1:   MEM window: 0xf6000000-0xf7ffffff
[    0.280089] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.280100] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.280104] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.280112] pci 0000:00:1c.5:   MEM window: 0xf8200000-0xf82fffff
[    0.280118] pci 0000:00:1c.5:   PREFETCH window: 0xc0000000-0xc00fffff
[    0.280124] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.280127] pci 0000:00:1e.0:   IO window: disabled
[    0.280134] pci 0000:00:1e.0:   MEM window: 0xf8300000-0xf83fffff
[    0.280140] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.280155]   alloc irq_desc for 17 on node -1
[    0.280157]   alloc kstat_irqs on node -1
[    0.280162] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.280168] pci 0000:00:1c.0: setting latency timer to 64
[    0.280177]   alloc irq_desc for 16 on node -1
[    0.280179]   alloc kstat_irqs on node -1
[    0.280182] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.280188] pci 0000:00:1c.1: setting latency timer to 64
[    0.280197] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.280202] pci 0000:00:1c.5: setting latency timer to 64
[    0.280211] pci 0000:00:1e.0: setting latency timer to 64
[    0.280216] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.280218] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.280221] pci_bus 0000:02: resource 0 io:  [0x4000-0x7fff]
[    0.280224] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xf5ffffff]
[    0.280226] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.280229] pci_bus 0000:04: resource 0 io:  [0x8000-0xbfff]
[    0.280232] pci_bus 0000:04: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.280234] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.280237] pci_bus 0000:08: resource 0 io:  [0xc000-0xcfff]
[    0.280240] pci_bus 0000:08: resource 1 mem: [0xf8200000-0xf82fffff]
[    0.280242] pci_bus 0000:08: resource 2 pref mem [0xc0000000-0xc00fffff]
[    0.280245] pci_bus 0000:09: resource 1 mem: [0xf8300000-0xf83fffff]
[    0.280248] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.280250] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.280284] NET: Registered protocol family 2
[    0.280378] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.280706] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.281188] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.281414] TCP: Hash tables configured (established 131072 bind 65536)
[    0.281416] TCP reno registered
[    0.281483] NET: Registered protocol family 1
[    0.281543] Trying to unpack rootfs image as initramfs...
[    0.471328] Freeing initrd memory: 7484k freed
[    0.475715] Simple Boot Flag at 0x35 set to 0x1
[    0.475897] cpufreq-nforce2: No nForce2 chipset.
[    0.475925] Scanning for low memory corruption every 60 seconds
[    0.476073] audit: initializing netlink socket (disabled)
[    0.476091] type=2000 audit(1258211718.476:1): initialized
[    0.484847] highmem bounce pool size: 64 pages
[    0.484853] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.486285] VFS: Disk quotas dquot_6.5.2
[    0.486345] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.486887] fuse init (API version 7.12)
[    0.486967] msgmni has been set to 1631
[    0.487178] alg: No test for stdrng (krng)
[    0.487192] io scheduler noop registered
[    0.487194] io scheduler anticipatory registered
[    0.487196] io scheduler deadline registered
[    0.487236] io scheduler cfq registered (default)
[    0.487249] pci 0000:00:02.0: Boot video device
[    0.487549]   alloc irq_desc for 24 on node -1
[    0.487551]   alloc kstat_irqs on node -1
[    0.487564] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.487577] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.487744]   alloc irq_desc for 25 on node -1
[    0.487746]   alloc kstat_irqs on node -1
[    0.487756] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.487768] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.487936]   alloc irq_desc for 26 on node -1
[    0.487938]   alloc kstat_irqs on node -1
[    0.487947] pcieport-driver 0000:00:1c.5: irq 26 for MSI/MSI-X
[    0.487959] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.488075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.488185] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.492429] ACPI: AC Adapter [ACAD] (on-line)
[    0.492505] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.492509] ACPI: Power Button [PWRF]
[    0.492559] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.492566] ACPI: Power Button [PWRB]
[    0.492609] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.492612] ACPI: Sleep Button [SLPB]
[    0.492661] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.495616] ACPI: Lid Switch [LID]
[    0.496273] ACPI: SSDT bf6d69b7 00238 (v01  HP    30CC     00003000 INTL 20061109)
[    0.496821] ACPI: SSDT bf6d635a 005D8 (v01  HP    30CC     00003001 INTL 20061109)
[    0.499036] Monitor-Mwait will be used to enter C-1 state
[    0.499061] Monitor-Mwait will be used to enter C-2 state
[    0.499084] Monitor-Mwait will be used to enter C-3 state
[    0.499092] Marking TSC unstable due to TSC halts in idle
[    0.499121] Switched to high resolution mode on CPU 0
[    0.499136] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.499161] processor LNXCPU:00: registered as cooling_device0
[    0.499165] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.499530] ACPI: SSDT bf6d6bef 000C8 (v01  HP    30CC     00003000 INTL 20061109)
[    0.499901] ACPI: SSDT bf6d6932 00085 (v01  HP    30CC     00003000 INTL 20061109)
[    0.500890] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.500914] processor LNXCPU:01: registered as cooling_device1
[    0.500918] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.501473] Switched to high resolution mode on CPU 1
[    0.509828] ACPI Exception: AE_OK, No or invalid critical threshold 20090521 thermal-384
[    0.509896] isapnp: Scanning for PnP cards...
[    0.665335] ACPI: Battery Slot [BAT0] (battery present)
[    0.864246] isapnp: No Plug & Play device found
[    0.865403] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.866741] brd: module loaded
[    0.867187] loop: module loaded
[    0.867255] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.867326] ahci 0000:00:1f.2: version 3.0
[    0.867340]   alloc irq_desc for 19 on node -1
[    0.867342]   alloc kstat_irqs on node -1
[    0.867348] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.867381]   alloc irq_desc for 27 on node -1
[    0.867383]   alloc kstat_irqs on node -1
[    0.867393] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    0.867468] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.867471] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    0.867477] ahci 0000:00:1f.2: setting latency timer to 64
[    0.867707] scsi0 : ahci
[    0.867791] scsi1 : ahci
[    0.867851] scsi2 : ahci
[    0.867957] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 27
[    0.867961] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 27
[    0.867964] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 27
[    0.868026] ata_piix 0000:00:1f.1: version 2.13
[    0.868036] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.868073] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.868151] scsi3 : ata_piix
[    0.868208] scsi4 : ata_piix
[    0.868795] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.868798] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.869728] Fixed MDIO Bus: probed
[    0.869761] PPP generic driver version 2.4.2
[    0.869847] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.869865]   alloc irq_desc for 18 on node -1
[    0.869867]   alloc kstat_irqs on node -1
[    0.869872] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.869883] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.869887] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.869936] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.873848] ehci_hcd 0000:00:1a.7: debug port 1
[    0.873855] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.873869] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8604800
[    0.888015] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.888094] usb usb1: configuration #1 chosen from 1 choice
[    0.888123] hub 1-0:1.0: USB hub found
[    0.888131] hub 1-0:1.0: 4 ports detected
[    0.888187]   alloc irq_desc for 23 on node -1
[    0.888189]   alloc kstat_irqs on node -1
[    0.888194] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.888204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.888208] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.888241] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.892159] ehci_hcd 0000:00:1d.7: debug port 1
[    0.892166] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.892179] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8604c00
[    0.908019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.908090] usb usb2: configuration #1 chosen from 1 choice
[    0.908116] hub 2-0:1.0: USB hub found
[    0.908122] hub 2-0:1.0: 6 ports detected
[    0.908184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.908204] uhci_hcd: USB Universal Host Controller Interface driver
[    0.908226] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.908234] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.908237] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.908266] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.908303] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.908381] usb usb3: configuration #1 chosen from 1 choice
[    0.908407] hub 3-0:1.0: USB hub found
[    0.908414] hub 3-0:1.0: 2 ports detected
[    0.908463]   alloc irq_desc for 21 on node -1
[    0.908465]   alloc kstat_irqs on node -1
[    0.908469] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.908476] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.908480] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.908510] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.908546] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.908622] usb usb4: configuration #1 chosen from 1 choice
[    0.908648] hub 4-0:1.0: USB hub found
[    0.908654] hub 4-0:1.0: 2 ports detected
[    0.908706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.908713] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.908716] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.908745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.908774] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.908853] usb usb5: configuration #1 chosen from 1 choice
[    0.908880] hub 5-0:1.0: USB hub found
[    0.908887] hub 5-0:1.0: 2 ports detected
[    0.908934] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.908941] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.908945] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.908973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.909009] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.909087] usb usb6: configuration #1 chosen from 1 choice
[    0.909114] hub 6-0:1.0: USB hub found
[    0.909121] hub 6-0:1.0: 2 ports detected
[    0.909175] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.909182] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.909185] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.909214] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.909244] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.909327] usb usb7: configuration #1 chosen from 1 choice
[    0.909353] hub 7-0:1.0: USB hub found
[    0.909359] hub 7-0:1.0: 2 ports detected
[    0.909461] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.953244] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.953249] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.953310] mice: PS/2 mouse device common for all mice
[    0.953441] rtc_cmos 00:08: RTC can wake from S4
[    0.953474] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.953508] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.953601] device-mapper: uevent: version 1.0.3
[    0.953679] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.953741] device-mapper: multipath: version 1.1.0 loaded
[    0.953743] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.953849] EISA: Probing bus 0 at eisa.0
[    0.953857] Cannot allocate resource for EISA slot 1
[    0.953869] Cannot allocate resource for EISA slot 4
[    0.953871] Cannot allocate resource for EISA slot 5
[    0.953873] Cannot allocate resource for EISA slot 6
[    0.953875] Cannot allocate resource for EISA slot 7
[    0.953877] Cannot allocate resource for EISA slot 8
[    0.953879] EISA: Detected 0 cards.
[    0.954018] cpuidle: using governor ladder
[    0.955370] cpuidle: using governor menu
[    0.955855] TCP cubic registered
[    0.956019] NET: Registered protocol family 10
[    0.956476] lo: Disabled Privacy Extensions
[    0.956824] NET: Registered protocol family 17
[    0.956842] Bluetooth: L2CAP ver 2.13
[    0.956843] Bluetooth: L2CAP socket layer initialized
[    0.956846] Bluetooth: SCO (Voice Link) ver 0.6
[    0.956848] Bluetooth: SCO socket layer initialized
[    0.956880] Bluetooth: RFCOMM TTY layer initialized
[    0.956882] Bluetooth: RFCOMM socket layer initialized
[    0.956884] Bluetooth: RFCOMM ver 1.11
[    0.957442] Using IPI No-Shortcut mode
[    0.957499] PM: Resume from disk failed.
[    0.957510] registered taskstats version 1
[    0.957637]   Magic number: 1:393:285
[    0.957668] acpi PNP0C04:00: hash matches
[    0.957729] rtc_cmos 00:08: setting system clock to 2009-11-14 15:15:19 UTC (1258211719)
[    0.957732] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.957733] EDD information not available.
[    0.984842] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.043937] ata4.00: ATAPI: Optiarc DVD RW AD-7561A, GH09, max MWDMA2
[    1.060391] ata4.00: configured for MWDMA2
[    1.184170] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.185072] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.185076] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[    1.185079] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.186127] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.186153] ata1.00: configured for UDMA/100
[    1.189161] ata2: SATA link down (SStatus 0 SControl 300)
[    1.189191] ata3: SATA link down (SStatus 0 SControl 300)
[    1.200322] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[    1.200457] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.200494] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.200540] sd 0:0:0:0: [sda] Write Protect is off
[    1.200543] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.200566] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.200691]  sda:
[    1.206245] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
[    1.211712] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.211717] Uniform CD-ROM driver Revision: 3.20
[    1.211857] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.211943] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.227381]  sda1 sda2
[    1.252070] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.252099] Freeing unused kernel memory: 544k freed
[    1.252460] Write protecting the kernel text: 4592k
[    1.252562] Write protecting the kernel read-only data: 1836k
[    1.313055] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.367381] Linux agpgart interface v0.103
[    1.387286] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    1.387893] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    1.390805] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.392347] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.392369] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.392420] r8169 0000:08:00.0: setting latency timer to 64
[    1.392502]   alloc irq_desc for 28 on node -1
[    1.392504]   alloc kstat_irqs on node -1
[    1.392522] r8169 0000:08:00.0: irq 28 for MSI/MSI-X
[    1.393241] eth0: RTL8101e at 0xf82b4000, 00:1e:68:99:1b:73, XID 34200000 IRQ 28
[    1.436772] [drm] Initialized drm 1.1.0 20060810
[    1.484336] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.484342] i915 0000:00:02.0: setting latency timer to 64
[    1.485985] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    1.485989] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.486097]   alloc irq_desc for 29 on node -1
[    1.486099]   alloc kstat_irqs on node -1
[    1.486110] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    1.488855] usb 2-4: configuration #1 chosen from 1 choice
[    1.500009] Clocksource tsc unstable (delta = -169895518 ns)
[    1.604195]   alloc irq_desc for 20 on node -1
[    1.604199]   alloc kstat_irqs on node -1
[    1.604206] ohci1394 0000:09:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.715216] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.729033] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.907672] usb 4-2: configuration #1 chosen from 1 choice
[    1.918738] usbcore: registered new interface driver hiddev
[    1.920824] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input6
[    1.920902] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2/input0
[    1.926685] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input7
[    1.926783] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-2/input1
[    1.926801] usbcore: registered new interface driver usbhid
[    1.926804] usbhid: v2.6:USB HID core driver
[    2.000234] [drm] TV-14: set mode NTSC 480i 0
[    2.125895] [drm] fb0: inteldrmfb frame buffer device
[    2.144609] acpi device:0b: registered as cooling_device2
[    2.144834] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input8
[    2.144863] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.144887] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.212512] [drm] LVDS-8: set mode 1280x800 17
[    2.401284] Console: switching to colour frame buffer device 160x50
[    2.765190] PM: Starting manual resume from disk
[    2.765194] PM: Resume from partition 8:2
[    2.765196] PM: Checking hibernation image.
[    2.765364] PM: Resume from disk failed.
[    2.771240] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.771245] EXT4-fs (sda1): write access will be enabled during recovery
[    2.819086] EXT4-fs (sda1): barriers enabled
[    3.068483] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e96f1601]
[    4.784600] kjournald2 starting: pid 440, dev sda1:8, commit interval 5 seconds
[    4.784623] EXT4-fs (sda1): delayed allocation enabled
[    4.784630] EXT4-fs: file extents enabled
[    4.796580] EXT4-fs: mballoc enabled
[    4.796594] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.824357] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393911
[    4.824485] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393910
[    4.824521] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393909
[    4.824555] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393908
[    4.824579] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 393907
[    4.824595] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2993
[    4.837044] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 982
[    4.882567] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1313112
[    4.883353] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1313099
[    4.899218] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1313090
[    4.899292] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1313073
[    4.899332] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 657
[    4.899420] EXT4-fs (sda1): 12 orphan inodes deleted
[    4.899424] EXT4-fs (sda1): recovery complete
[    5.592701] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.181332] type=1505 audit(1258211724.722:2): operation="profile_load" pid=463 name=/usr/share/gdm/guest-session/Xsession
[    6.184359] type=1505 audit(1258211724.726:3): operation="profile_load" pid=464 name=/sbin/dhclient3
[    6.185222] type=1505 audit(1258211724.726:4): operation="profile_load" pid=464 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.185622] type=1505 audit(1258211724.726:5): operation="profile_load" pid=464 name=/usr/lib/connman/scripts/dhclient-script
[    6.252368] type=1505 audit(1258211724.794:6): operation="profile_load" pid=465 name=/usr/bin/evince
[    6.263954] type=1505 audit(1258211724.802:7): operation="profile_load" pid=465 name=/usr/bin/evince-previewer
[    6.270774] type=1505 audit(1258211724.810:8): operation="profile_load" pid=465 name=/usr/bin/evince-thumbnailer
[    6.309170] type=1505 audit(1258211724.850:9): operation="profile_load" pid=467 name=/usr/lib/cups/backend/cups-pdf
[    6.310027] type=1505 audit(1258211724.850:10): operation="profile_load" pid=467 name=/usr/sbin/cupsd
[    6.337942] type=1505 audit(1258211724.878:11): operation="profile_load" pid=468 name=/usr/sbin/mysqld-akonadi
[    7.196681] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k 
[    7.543109] EXT4-fs (sda1): internal journal on sda1:8
[    7.957296] udev: starting version 147
[    9.042727] lp: driver loaded but no devices found
[    9.995593] Linux video capture interface: v2.00
[   10.881116] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   10.884921] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
[   10.885005] usbcore: registered new interface driver uvcvideo
[   10.885008] USB Video Class driver (v0.1.0)
[   11.050393] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   11.159289] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   11.350440] ricoh-mmc: Ricoh MMC Controller disabling driver
[   11.350443] ricoh-mmc: Copyright(c) Philip Langdale
[   11.350476] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   11.350495] ricoh-mmc: Controller is now disabled.
[   11.404117] cfg80211: Calling CRDA to update world regulatory domain
[   11.852421] cfg80211: World regulatory domain updated:
[   11.852424] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.852427] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.852430] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.852433] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.852435] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.852438] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.882379] sdhci: Secure Digital Host Controller Interface driver
[   11.882382] sdhci: Copyright(c) Pierre Ossman
[   12.077700] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.079144] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[   12.079163] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   12.081216] Registered led device: mmc0::
[   12.082243] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[   12.331860] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   12.331864] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   12.331956] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.331966] iwlagn 0000:02:00.0: setting latency timer to 64
[   12.332015] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   12.375649] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.375715]   alloc irq_desc for 30 on node -1
[   12.375718]   alloc kstat_irqs on node -1
[   12.375738] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   12.702181] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.977573] __ratelimit: 3 callbacks suppressed
[   12.977577] type=1505 audit(1258211731.518:13): operation="profile_replace" pid=889 name=/usr/share/gdm/guest-session/Xsession
[   12.979367] type=1505 audit(1258211731.518:14): operation="profile_replace" pid=890 name=/sbin/dhclient3
[   12.980143] type=1505 audit(1258211731.522:15): operation="profile_replace" pid=890 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.980543] type=1505 audit(1258211731.522:16): operation="profile_replace" pid=890 name=/usr/lib/connman/scripts/dhclient-script
[   12.984495] type=1505 audit(1258211731.526:17): operation="profile_replace" pid=891 name=/usr/bin/evince
[   12.996485] type=1505 audit(1258211731.538:18): operation="profile_replace" pid=891 name=/usr/bin/evince-previewer
[   13.003308] type=1505 audit(1258211731.542:19): operation="profile_replace" pid=891 name=/usr/bin/evince-thumbnailer
[   13.012816] type=1505 audit(1258211731.554:20): operation="profile_replace" pid=893 name=/usr/lib/cups/backend/cups-pdf
[   13.013679] type=1505 audit(1258211731.554:21): operation="profile_replace" pid=893 name=/usr/sbin/cupsd
[   13.016213] type=1505 audit(1258211731.558:22): operation="profile_replace" pid=894 name=/usr/sbin/mysqld-akonadi
[   16.061183]   alloc irq_desc for 22 on node -1
[   16.061187]   alloc kstat_irqs on node -1
[   16.061195] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.061236] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.299224] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.437033] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   16.465508] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   16.674526] Registered led device: iwl-phy0::radio
[   16.674565] Registered led device: iwl-phy0::assoc
[   16.674600] Registered led device: iwl-phy0::RX
[   16.674630] Registered led device: iwl-phy0::TX
[   16.712346] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.882974] r8169: eth0: link up
[   16.882982] r8169: eth0: link up
[   19.447719] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   19.770046] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[   22.678371] [drm] TV-14: set mode NTSC 480i 0
[   22.853581] [drm] TV-14: set mode NTSC 480i 0
[   23.033726] ppdev: user-space parallel port driver
[   23.289406] [drm] TV-14: set mode NTSC 480i 0
[   23.429591] [drm] TV-14: set mode NTSC 480i 0
[   33.779330] [drm] TV-14: set mode NTSC 480i 0
[   33.919249] [drm] TV-14: set mode NTSC 480i 0
[   34.188444] [drm] TV-14: set mode NTSC 480i 0
[   34.329010] [drm] TV-14: set mode NTSC 480i 0
[   34.628208] [drm] TV-14: set mode NTSC 480i 0
[   34.769416] [drm] TV-14: set mode NTSC 480i 0
[   37.703409] [drm] TV-14: set mode NTSC 480i 0
[   37.843317] [drm] TV-14: set mode NTSC 480i 0
[  126.524158] CE: hpet increasing min_delta_ns to 15000 nsec
[  138.073457] wlan0: authenticate with AP 00:22:b0:ca:b9:c3
[  138.076788] wlan0: authenticated
[  138.076795] wlan0: associate with AP 00:22:b0:ca:b9:c3
[  138.080919] wlan0: RX AssocResp from 00:22:b0:ca:b9:c3 (capab=0x31 status=0 aid=1)
[  138.080923] wlan0: associated
[  138.108962] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  138.361751] padlock: VIA PadLock not detected.
[  138.586146] cfg80211: Calling CRDA for country: US
[  138.590267] cfg80211: Received country IE:
[  138.590273] cfg80211: Regulatory domain: US
[  138.590277] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590283] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  138.590287] cfg80211: CRDA thinks this should applied:
[  138.590290] cfg80211: Regulatory domain: US
[  138.590294] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590299] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  138.590304] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  138.590310] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  138.590315] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  138.590320] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  138.590324] cfg80211: We intersect both of these and get:
[  138.590328] cfg80211: Regulatory domain: 98
[  138.590331] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590336] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  138.590345] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[  138.590350] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[  138.590355] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[  138.590360] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[  138.590364] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[  138.590370] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[  138.590375] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[  138.590380] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[  138.590385] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[  138.590390] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[  138.590395] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[  138.590400] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[  138.590405] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[  138.590413] cfg80211: Current regulatory domain updated by AP to: US
[  138.590417] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590422] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  148.737014] wlan0: no IPv6 routers present
[  183.668736] wlan0: disassociating by local choice (reason=3)
[  217.169202] CE: hpet increasing min_delta_ns to 22500 nsec
[  660.165264] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 5 bytes away.
[  661.315957] psmouse.c: resync failed, issuing reconnect request

```

---

### Post by kakyoism on 2009-11-14
bump

me and my family are in deep trouble because of this...

---

### Post by kakyoism on 2009-11-15
bump again

---

### Post by kakyoism on 2009-11-15
Tried with WICD, not working.
Tried installing backports karmic, not working.
Tried modprob iwlagn, not working.

---

### Post by raygj on 2009-11-15
> [   11.404117] cfg80211: Calling CRDA to update world regulatory domain
[   11.852421] cfg80211: World regulatory domain updated:
[   11.852424] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.852427] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.852430] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.852433] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.852435] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.852438] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

> [  138.586146] cfg80211: **Calling CRDA for country: US**
[  138.590267] cfg80211: **Received country IE:**
[  138.590273] cfg80211: **Regulatory domain: US**
[  138.590277] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590283] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[B][  138.590287] cfg80211: CRDA thinks this should applied:
[  138.590290] cfg80211: Regulatory domain: US[/B]
[  138.590294] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590299] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  138.590304] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  138.590310] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  138.590315] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  138.590320] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[B][  138.590324] cfg80211: We intersect both of these and get:
[  138.590328] cfg80211: Regulatory domain: 98[/B]
[  138.590331] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590336] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
**[  138.590345] cfg80211: [COLOR="Black"]Leaving channel 5180 MHz intact[/COLOR] on phy0 - [B]no rule found in band on Country IE**
[  138.590350] cfg80211:** Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE**
[  138.590355] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[  138.590360] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[  138.590364] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[  138.590370] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[  138.590375] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[  138.590380] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[  138.590385] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[  138.590390] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[  138.590395] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[  138.590400] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[  138.590405] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[  138.590413] cfg80211: **Current regulatory domain updated by AP to: US**
[  138.590417] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  138.590422] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)

try entering 
> sudo iw reg get
this will print out your wireless cards
**world wireless domain zone**(a 2 capital letter country code(zone) ie US (for USA) or AU (for Australia)or GB(for Great Britain)etc.etc,followed by your frequencies,channel bandwidth,RX antenna gain setting,TX power setting.this COUNTRY CODE must be the same as your wireless network that you are trying to connect to or keep connected to.
 you must set your wireless card to the same zone(country)as your wireless router for proper wireless network operation..
enter the following
> sudo iw reg set {insert your 2 capital letter country code}
a few example country codes
 Australian zone =AU
        USA zone =US
      China zone =CN
      Japon zone =JP
i used 'sudo iw reg get' and found
my computer was set to CN  (China)
so i set it to (Australian zone) AU
by using '[COLOR="Black"]sudo iw reg set **AU**[/COLOR]'
this only works till reboot.
you will need to write a startup bash script containing
> #!/bin/bash
iw reg set  **XX**          ## {replace **XX** with your routers country code}

and set it to run on computer startup.
see this post for more info 
[http://ubuntuforums.org/showpost.php...53&postcount=6]("http://ubuntuforums.org/showpost.php...53&postcount=6")

---

### Post by kakyoism on 2009-11-15
Thanks for the tip.
However I found that the "iw reg set" does not change my wireless country code as expected...

(11:08) me@me-laptop:/etc/init.d $sudo iw reg set CA
(11:09) me@me-laptop:/etc/init.d $sudo iw reg get
country 98:
	(2402 - 2472 @ 40), (3, 27)
(11:09) me@me-laptop:/etc/init.d $sudo iw reg set US
(11:10) me@me-laptop:/etc/init.d $sudo iw reg get
country 98:
	(2402 - 2472 @ 40), (3, 27)
(11:10) me@me-laptop:/etc/init.d $sudo iw reg set CN
(11:10) me@me-laptop:/etc/init.d $sudo iw reg get
country 98:
	(2402 - 2472 @ 40), (3, 27)

---

### Post by kakyoism on 2009-11-15
I also found that the country code is not in capital letter but two-digit number...

---

### Post by kakyoism on 2009-11-19
Problem solved.

The problem was the blacklisted driver in 
```
/etc/modprobe.d/blacklist-ath_pci.conf
```

commenting it out (i.e. removing it from blackist) solved my problem.

---

