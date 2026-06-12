---
title: "Alfa 500 wlan, cannot connect."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-05-06
i can't seem to get my card to connect at all.

it's an alfa 500 USB chipset:RTL8187

messages are at the very bottom.


```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
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
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffa0000 - 000000003ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffae000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3ffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ffa0000 (usable)
[    0.000000]  modified: 000000003ffa0000 - 000000003ffae000 (ACPI data)
[    0.000000]  modified: 000000003ffae000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  modified: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f870000 - 2fff7b8c
[    0.000000] ACPI: RSDP 000fad00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ffa0000 00034 (v01 A M I  OEMRSDT  03000629 MSFT 00000097)
[    0.000000] ACPI: FACP 3ffa0200 00084 (v02 A M I  OEMFACP  03000629 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ffa0430 06E7D (v01  A0466 A0466001 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 3ffae000 00040
[    0.000000] ACPI: APIC 3ffa0390 0005C (v01 A M I  OEMAPIC  03000629 MSFT 00000097)
[    0.000000] ACPI: MCFG 3ffa03f0 0003C (v01 A M I  OEMMCFG  03000629 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ffae040 0007B (v01 A M I  AMI_OEM  03000629 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ae160]    TEXT DATA BSS ==> [0000100000 - 00008ae160]
[    0.000000]   #4 [002f870000 - 002fff7b8c]          RAMDISK ==> [002f870000 - 002fff7b8c]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008af000 - 00008b2258]              BRK ==> [00008af000 - 00008b2258]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffa0
[    0.000000] On node 0 totalpages: 261935
[    0.000000] free_area_init_node: node 0, pgdat c0788d40, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34450 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bf700000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1805000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259887
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=24420e75-5730-4529-8434-f047727be5cd ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5240640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ffa0)
[    0.000000] Memory: 1017420k/1048192k available (4583k kernel code, 29852k reserved, 2142k data, 544k init, 138888k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc081a000   ( 544 kB)
[    0.000000]       .data : 0xc0579d78 - 0xc0791848   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579d78   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2405.218 MHz processor.
[    0.000012] spurious 8259A interrupt: IRQ7.
[    0.001215] Console: colour VGA+ 80x25
[    0.001217] console [tty0] enabled
[    0.001268] Calibrating delay loop (skipped), value calculated using timer frequency.. 4810.43 BogoMIPS (lpj=9620872)
[    0.001294] Security Framework initialized
[    0.001315] AppArmor: AppArmor initialized
[    0.001322] Mount-cache hash table entries: 512
[    0.001463] Initializing cgroup subsys ns
[    0.001466] Initializing cgroup subsys cpuacct
[    0.001470] Initializing cgroup subsys memory
[    0.001476] Initializing cgroup subsys devices
[    0.001478] Initializing cgroup subsys freezer
[    0.001480] Initializing cgroup subsys net_cls
[    0.001491] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001493] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.001497] mce: CPU supports 5 MCE banks
[    0.001514] Performance Counters: AMD PMU driver.
[    0.001520] ... version:                 0
[    0.001521] ... bit width:               48
[    0.001523] ... generic counters:        4
[    0.001525] ... value mask:              0000ffffffffffff
[    0.001526] ... max period:              00007fffffffffff
[    0.001528] ... fixed-purpose counters:  0
[    0.001530] ... counter mask:            000000000000000f
[    0.001533] Checking 'hlt' instruction... OK.
[    0.016582] SMP alternatives: switching to UP code
[    0.020009] ACPI: Core revision 20090521
[    0.030692] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070619] CPU0: AMD Athlon(tm) 64 Processor 4000+ stepping 01
[    0.072001] Brought up 1 CPUs
[    0.072001] Total of 1 processors activated (4810.43 BogoMIPS).
[    0.072001] CPU0 attaching NULL sched-domain.
[    0.072001] Booting paravirtualized kernel on bare hardware
[    0.072001] regulator: core version 0.5
[    0.072001] Time: 10:58:20  Date: 05/06/10
[    0.072001] NET: Registered protocol family 16
[    0.072001] EISA bus registered
[    0.072001] ACPI: bus type pci registered
[    0.072001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.072001] PCI: Not using MMCONFIG.
[    0.072001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.072001] PCI: Using configuration type 1 for base access
[    0.072001] bio: create slab <bio-0> at 0
[    0.072001] ACPI: EC: Look up EC in DSDT
[    0.080532] ACPI: Interpreter enabled
[    0.080539] ACPI: (supports S0 S1 S3 S4 S5)
[    0.080558] ACPI: Using IOAPIC for interrupt routing
[    0.080674] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.086721] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.086723] PCI: Using MMCONFIG for extended config space
[    0.094515] ACPI Warning: Incorrect checksum in table [OEMB] - 5D, should be 2F 20090521 tbutils-246
[    0.094602] ACPI: No dock devices found.
[    0.094702] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.094778] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.094781] pci 0000:00:02.0: PME# disabled
[    0.094818] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.094821] pci 0000:00:05.0: PME# disabled
[    0.094855] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.094858] pci 0000:00:06.0: PME# disabled
[    0.095023] pci 0000:00:1c.0: reg 10 32bit mmio: [0xd7ffc000-0xd7ffcfff]
[    0.095072] pci 0000:00:1c.1: reg 10 32bit mmio: [0xd7ffd000-0xd7ffdfff]
[    0.095122] pci 0000:00:1c.2: reg 10 32bit mmio: [0xd7ffe000-0xd7ffefff]
[    0.095192] pci 0000:00:1c.3: reg 10 32bit mmio: [0xd7fff800-0xd7fff8ff]
[    0.095243] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.095247] pci 0000:00:1c.3: PME# disabled
[    0.095300] pci 0000:00:1d.0: reg 10 64bit mmio: [0xd7ff4000-0xd7ff7fff]
[    0.095342] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.095346] pci 0000:00:1d.0: PME# disabled
[    0.095470] pci 0000:00:1e.1: quirk: region 0900-093f claimed by ali7101 ACPI
[    0.095537] pci 0000:00:1f.0: reg 20 io port: [0xff00-0xff0f]
[    0.095605] pci 0000:00:1f.1: reg 10 io port: [0xac00-0xac07]
[    0.095612] pci 0000:00:1f.1: reg 14 io port: [0xa880-0xa883]
[    0.095618] pci 0000:00:1f.1: reg 18 io port: [0xa800-0xa807]
[    0.095624] pci 0000:00:1f.1: reg 1c io port: [0xa480-0xa483]
[    0.095631] pci 0000:00:1f.1: reg 20 io port: [0xa400-0xa40f]
[    0.095637] pci 0000:00:1f.1: reg 24 32bit mmio: [0xd7fffc00-0xd7ffffff]
[    0.095664] pci 0000:00:1f.1: PME# supported from D3hot
[    0.095668] pci 0000:00:1f.1: PME# disabled
[    0.095711] pci 0000:04:00.0: reg 10 64bit mmio: [0xc0000000-0xcfffffff]
[    0.095720] pci 0000:04:00.0: reg 18 64bit mmio: [0xdffe0000-0xdffeffff]
[    0.095726] pci 0000:04:00.0: reg 20 io port: [0xe800-0xe8ff]
[    0.095734] pci 0000:04:00.0: reg 30 32bit mmio: [0xdffc0000-0xdffdffff]
[    0.095752] pci 0000:04:00.0: supports D1 D2
[    0.095784] pci 0000:04:00.1: reg 10 64bit mmio: [0xdfff0000-0xdfffffff]
[    0.095816] pci 0000:04:00.1: supports D1 D2
[    0.095875] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.095878] pci 0000:00:02.0: bridge 32bit mmio: [0xdff00000-0xdfffffff]
[    0.095883] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.095950] pci 0000:03:00.0: reg 10 64bit mmio: [0xdfeffc00-0xdfeffc7f]
[    0.095968] pci 0000:03:00.0: reg 18 64bit mmio: [0xdfef8000-0xdfefbfff]
[    0.095979] pci 0000:03:00.0: reg 20 io port: [0xdc00-0xdc7f]
[    0.096004] pci 0000:03:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe7ffff]
[    0.096050] pci 0000:03:00.0: supports D1 D2
[    0.096119] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
[    0.096122] pci 0000:00:05.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.096178] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfdfc000-0xdfdfffff]
[    0.096186] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.096210] pci 0000:02:00.0: reg 30 32bit mmio: [0xdfdc0000-0xdfddffff]
[    0.096248] pci 0000:02:00.0: supports D1 D2
[    0.096250] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096254] pci 0000:02:00.0: PME# disabled
[    0.096312] pci 0000:00:06.0: bridge io port: [0xc000-0xcfff]
[    0.096315] pci 0000:00:06.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.096388] pci 0000:01:11.0: reg 10 io port: [0xbc00-0xbc1f]
[    0.096402] pci 0000:01:11.0: reg 14 64bit mmio: [0xdfa00000-0xdfbfffff]
[    0.096415] pci 0000:01:11.0: reg 1c 64bit mmio: [0xd8000000-0xdbffffff]
[    0.096453] pci 0000:01:11.0: supports D1 D2
[    0.096497] pci 0000:01:13.0: reg 10 32bit mmio: [0xdfcfb800-0xdfcfbfff]
[    0.096506] pci 0000:01:13.0: reg 14 32bit mmio: [0xdfcf4000-0xdfcf7fff]
[    0.096557] pci 0000:01:13.0: supports D1 D2
[    0.096559] pci 0000:01:13.0: PME# supported from D0 D1 D2 D3hot
[    0.096563] pci 0000:01:13.0: PME# disabled
[    0.096611] pci 0000:01:14.0: reg 10 32bit mmio: [0xdfcfc000-0xdfcfffff]
[    0.096619] pci 0000:01:14.0: reg 14 io port: [0xb800-0xb8ff]
[    0.096650] pci 0000:01:14.0: reg 30 32bit mmio: [0xdfcc0000-0xdfcdffff]
[    0.096677] pci 0000:01:14.0: supports D1 D2
[    0.096679] pci 0000:01:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096684] pci 0000:01:14.0: PME# disabled
[    0.096711] pci 0000:00:1a.0: bridge io port: [0xb000-0xbfff]
[    0.096715] pci 0000:00:1a.0: bridge 32bit mmio: [0xd8000000-0xdfcfffff]
[    0.096729] pci_bus 0000:00: on NUMA node 0
[    0.096733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.096794] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.096843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.096887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.096933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[    0.099587] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[    0.099729] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.099870] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.100019] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.100160] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.100300] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.100439] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.100575] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15), disabled.
[    0.100715] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.100858] SCSI subsystem initialized
[    0.100892] libata version 3.00 loaded.
[    0.100949] usbcore: registered new interface driver usbfs
[    0.100959] usbcore: registered new interface driver hub
[    0.100979] usbcore: registered new device driver usb
[    0.101072] ACPI: WMI: Mapper loaded
[    0.101074] PCI: Using ACPI for IRQ routing
[    0.101209] Bluetooth: Core ver 2.15
[    0.101229] NET: Registered protocol family 31
[    0.101231] Bluetooth: HCI device and connection manager initialized
[    0.101233] Bluetooth: HCI socket layer initialized
[    0.101235] NetLabel: Initializing
[    0.101237] NetLabel:  domain hash size = 128
[    0.101238] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.101249] NetLabel:  unlabeled traffic allowed by default
[    0.102727] pnp: PnP ACPI init
[    0.102740] ACPI: bus type pnp registered
[    0.106764] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:00:02.0 BAR 15 (0xc0000000-0xcfffffff), disabling
[    0.106784] pnp 00:09: io resource (0x900-0x91f) overlaps 0000:00:1e.1 BAR 13 (0x900-0x93f), disabling
[    0.106797] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:04:00.0 BAR 0 (0xc0000000-0xcfffffff), disabling
[    0.108723] pnp: PnP ACPI: found 16 devices
[    0.108725] ACPI: ACPI bus type pnp unregistered
[    0.108728] PnPBIOS: Disabled by ACPI PNP
[    0.108740] system 00:09: ioport range 0x28d-0x28e has been reserved
[    0.108743] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.108746] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.108748] system 00:09: ioport range 0x900-0x9bf could not be reserved
[    0.108751] system 00:09: ioport range 0x9c0-0x9df has been reserved
[    0.108755] system 00:09: iomem range 0xff000000-0xffffffff could not be reserved
[    0.108759] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.108762] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.108767] system 00:0d: ioport range 0xc00-0xc0f has been reserved
[    0.108769] system 00:0d: ioport range 0xd00-0xd0f has been reserved
[    0.108772] system 00:0d: ioport range 0xa20-0xa2f has been reserved
[    0.108774] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.108779] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.108783] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.108786] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[    0.108788] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.108791] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[    0.108794] system 00:0f: iomem range 0xfff80000-0xffffffff has been reserved
[    0.143524] AppArmor: AppArmor Filesystem Enabled
[    0.143553] pci 0000:00:02.0: PCI bridge, secondary bus 0000:04
[    0.143555] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.143559] pci 0000:00:02.0:   MEM window: 0xdff00000-0xdfffffff
[    0.143562] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.143566] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    0.143569] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    0.143572] pci 0000:00:05.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.143575] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.143578] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.143581] pci 0000:00:06.0:   IO window: 0xc000-0xcfff
[    0.143584] pci 0000:00:06.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.143587] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.143590] pci 0000:00:1a.0: PCI bridge, secondary bus 0000:01
[    0.143593] pci 0000:00:1a.0:   IO window: 0xb000-0xbfff
[    0.143598] pci 0000:00:1a.0:   MEM window: 0xd8000000-0xdfcfffff
[    0.143601] pci 0000:00:1a.0:   PREFETCH window: disabled
[    0.143612] pci 0000:00:02.0: setting latency timer to 64
[    0.143617] pci 0000:00:05.0: setting latency timer to 64
[    0.143622] pci 0000:00:06.0: setting latency timer to 64
[    0.143628] pci 0000:00:1a.0: setting latency timer to 64
[    0.143633] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.143635] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.143638] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.143640] pci_bus 0000:04: resource 1 mem: [0xdff00000-0xdfffffff]
[    0.143642] pci_bus 0000:04: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.143645] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.143647] pci_bus 0000:03: resource 1 mem: [0xdfe00000-0xdfefffff]
[    0.143650] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.143652] pci_bus 0000:02: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.143654] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.143657] pci_bus 0000:01: resource 1 mem: [0xd8000000-0xdfcfffff]
[    0.143689] NET: Registered protocol family 2
[    0.143774] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.144019] Switched to high resolution mode on CPU 0
[    0.144149] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.145031] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.145507] TCP: Hash tables configured (established 131072 bind 65536)
[    0.145509] TCP reno registered
[    0.145606] NET: Registered protocol family 1
[    0.145671] Trying to unpack rootfs image as initramfs...
[    0.330968] Freeing initrd memory: 7710k freed
[    0.337982] cpufreq-nforce2: No nForce2 chipset.
[    0.338004] Scanning for low memory corruption every 60 seconds
[    0.338101] audit: initializing netlink socket (disabled)
[    0.338118] type=2000 audit(1273143500.336:1): initialized
[    0.345714] highmem bounce pool size: 64 pages
[    0.345718] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.346800] VFS: Disk quotas dquot_6.5.2
[    0.346844] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.347409] fuse init (API version 7.12)
[    0.347473] msgmni has been set to 1731
[    0.347629] alg: No test for stdrng (krng)
[    0.347639] io scheduler noop registered
[    0.347641] io scheduler anticipatory registered
[    0.347643] io scheduler deadline registered
[    0.347674] io scheduler cfq registered (default)
[    0.800061] pci 0000:04:00.0: Boot video device
[    0.800151]   alloc irq_desc for 24 on node -1
[    0.800153]   alloc kstat_irqs on node -1
[    0.800160] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.800166] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.800246]   alloc irq_desc for 25 on node -1
[    0.800247]   alloc kstat_irqs on node -1
[    0.800252] pcieport-driver 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.800256] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    0.800329]   alloc irq_desc for 26 on node -1
[    0.800331]   alloc kstat_irqs on node -1
[    0.800335] pcieport-driver 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.800339] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.800414] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    0.800419] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    0.800424] aer 0000:00:06.0:pcie02: AER service couldn't init device: no _OSC support
[    0.800430] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.800448] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.800545] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.800549] ACPI: Power Button [PWRF]
[    0.800593] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.800596] ACPI: Power Button [PWRB]
[    0.800835] processor LNXCPU:00: registered as cooling_device0
[    0.800838] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.803841] isapnp: Scanning for PnP cards...
[    1.158104] isapnp: No Plug & Play device found
[    1.158995] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.159117] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.159425] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.160223] brd: module loaded
[    1.160604] loop: module loaded
[    1.160659] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.160713] ahci 0000:00:1f.1: version 3.0
[    1.160725]   alloc irq_desc for 19 on node -1
[    1.160727]   alloc kstat_irqs on node -1
[    1.160732] ahci 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.160762]   alloc irq_desc for 27 on node -1
[    1.160764]   alloc kstat_irqs on node -1
[    1.160771] ahci 0000:00:1f.1: irq 27 for MSI/MSI-X
[    1.160864] ahci 0000:00:1f.1: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.160867] ahci 0000:00:1f.1: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    1.161385] scsi0 : ahci
[    1.161472] scsi1 : ahci
[    1.161514] scsi2 : ahci
[    1.161554] scsi3 : ahci
[    1.161641] ata1: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffd00 irq 27
[    1.161644] ata2: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffd80 irq 27
[    1.161647] ata3: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffe00 irq 27
[    1.161651] ata4: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffe80 irq 27
[    1.161735] sata_sil24 0000:03:00.0: version 1.1
[    1.161745]   alloc irq_desc for 17 on node -1
[    1.161747]   alloc kstat_irqs on node -1
[    1.161751] sata_sil24 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.161829] sata_sil24 0000:03:00.0: setting latency timer to 64
[    1.162158] scsi4 : sata_sil24
[    1.162228] scsi5 : sata_sil24
[    1.162259] ata5: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfef8000 irq 17
[    1.162263] ata6: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfefa000 irq 17
[    1.162351] pata_ali 0000:00:1f.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.162509] scsi6 : pata_ali
[    1.162579] scsi7 : pata_ali
[    1.164841] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.164844] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.165425] Fixed MDIO Bus: probed
[    1.165453] PPP generic driver version 2.4.2
[    1.165561] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.165575]   alloc irq_desc for 23 on node -1
[    1.165577]   alloc kstat_irqs on node -1
[    1.165582] ehci_hcd 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.165592] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[    1.165616] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 1
[    1.188025] ehci_hcd 0000:00:1c.3: debug port 1
[    1.188049] ehci_hcd 0000:00:1c.3: irq 23, io mem 0xd7fff800
[    1.200019] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00
[    1.200081] usb usb1: configuration #1 chosen from 1 choice
[    1.200105] hub 1-0:1.0: USB hub found
[    1.200115] hub 1-0:1.0: 8 ports detected
[    1.200183] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.200195] ohci_hcd 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.200202] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[    1.200225] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 2
[    1.200238] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xd7ffc000
[    1.258047] usb usb2: configuration #1 chosen from 1 choice
[    1.258070] hub 2-0:1.0: USB hub found
[    1.258078] hub 2-0:1.0: 3 ports detected
[    1.258110]   alloc irq_desc for 18 on node -1
[    1.258112]   alloc kstat_irqs on node -1
[    1.258116] ohci_hcd 0000:00:1c.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.258123] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[    1.258146] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 3
[    1.258174] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xd7ffd000
[    1.314049] usb usb3: configuration #1 chosen from 1 choice
[    1.314073] hub 3-0:1.0: USB hub found
[    1.314082] hub 3-0:1.0: 3 ports detected
[    1.314117] ohci_hcd 0000:00:1c.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.314124] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[    1.314147] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 4
[    1.314175] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xd7ffe000
[    1.328498] ata7.00: ATA-7: HDT722525DLAT80, V44OA96A, max UDMA/133
[    1.328501] ata7.00: 488397168 sectors, multi 16: LBA48 
[    1.344415] ata7.00: configured for UDMA/133
[    1.370058] usb usb4: configuration #1 chosen from 1 choice
[    1.370077] hub 4-0:1.0: USB hub found
[    1.370086] hub 4-0:1.0: 3 ports detected
[    1.370122] uhci_hcd: USB Universal Host Controller Interface driver
[    1.370196] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.370198] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.370490] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.370536] mice: PS/2 mouse device common for all mice
[    1.370616] rtc_cmos 00:02: RTC can wake from S4
[    1.370649] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.370684] rtc0: alarms up to one month, 114 bytes nvram
[    1.370792] device-mapper: uevent: version 1.0.3
[    1.370863] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.370929] device-mapper: multipath: version 1.1.0 loaded
[    1.370931] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.371029] EISA: Probing bus 0 at eisa.0
[    1.371055] Cannot allocate resource for EISA slot 5
[    1.371070] EISA: Detected 0 cards.
[    1.371114] cpuidle: using governor ladder
[    1.371116] cpuidle: using governor menu
[    1.371524] TCP cubic registered
[    1.371648] NET: Registered protocol family 10
[    1.372033] lo: Disabled Privacy Extensions
[    1.372278] NET: Registered protocol family 17
[    1.372291] Bluetooth: L2CAP ver 2.13
[    1.372292] Bluetooth: L2CAP socket layer initialized
[    1.372295] Bluetooth: SCO (Voice Link) ver 0.6
[    1.372296] Bluetooth: SCO socket layer initialized
[    1.372330] Bluetooth: RFCOMM TTY layer initialized
[    1.372332] Bluetooth: RFCOMM socket layer initialized
[    1.372334] Bluetooth: RFCOMM ver 1.11
[    1.372349] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 4000+ processors (1 cpu cores) (version 2.20.00)
[    1.380499] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.380535] Using IPI No-Shortcut mode
[    1.380587] PM: Resume from disk failed.
[    1.380598] registered taskstats version 1
[    1.380710]   Magic number: 10:943:981
[    1.380800] rtc_cmos 00:02: setting system clock to 2010-05-06 10:58:22 UTC (1273143502)
[    1.380803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.380805] EDD information not available.
[    1.396034] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.480026] ata1: SATA link down (SStatus 0 SControl 300)
[    1.480048] ata3: SATA link down (SStatus 0 SControl 300)
[    1.480066] ata2: SATA link down (SStatus 0 SControl 300)
[    1.480085] ata4: SATA link down (SStatus 0 SControl 300)
[    1.816020] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    2.037106] usb 2-1: configuration #1 chosen from 1 choice
[    3.244034] ata5: SATA link down (SStatus 0 SControl 0)
[    5.324034] ata6: SATA link down (SStatus 0 SControl 0)
[    5.324139] scsi 6:0:0:0: Direct-Access     ATA      HDT722525DLAT80  V44O PQ: 0 ANSI: 5
[    5.324220] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    5.324251] sd 6:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.324287] sd 6:0:0:0: [sda] Write Protect is off
[    5.324290] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.324309] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.324411]  sda: sda1 sda2 < sda5 > sda3 sda4
[    5.356297] sd 6:0:0:0: [sda] Attached SCSI disk
[    5.488365] ata8.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.04, max UDMA/66
[    5.488383] ata8.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    5.488385] ata8.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    5.504362] ata8.00: configured for UDMA/66
[    5.506805] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 5
[    5.508487] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.508490] Uniform CD-ROM driver Revision: 3.20
[    5.508542] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    5.508573] sr 7:0:0:0: Attached scsi generic sg1 type 5
[    5.508591] Freeing unused kernel memory: 544k freed
[    5.509006] Write protecting the kernel text: 4584k
[    5.509032] Write protecting the kernel read-only data: 1840k
[    5.623954] Linux agpgart interface v0.103
[    5.656427] Floppy drive(s): fd0 is 1.44M
[    5.698747] FDC 0 is a post-1991 82077
[    5.765346] [drm] Initialized drm 1.1.0 20060810
[    5.781548] [drm] radeon default to kernel modesetting DISABLED.
[    5.782407] pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.782412] pci 0000:04:00.0: setting latency timer to 64
[    5.782564] [drm] Initialized radeon 1.31.0 20080528 for 0000:04:00.0 on minor 0
[    5.785605] sky2 driver version 1.23
[    5.785636] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.785647] sky2 0000:02:00.0: setting latency timer to 64
[    5.785673] sky2 0000:02:00.0: Yukon-2 EC chip revision 2
[    5.785751]   alloc irq_desc for 28 on node -1
[    5.785753]   alloc kstat_irqs on node -1
[    5.785766] sky2 0000:02:00.0: irq 28 for MSI/MSI-X
[    5.786309] sky2 eth0: addr 00:17:31:95:33:1b
[    5.797176]   alloc irq_desc for 21 on node -1
[    5.797179]   alloc kstat_irqs on node -1
[    5.797185] skge 0000:01:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.797232] skge 1.13 addr 0xdfcfc000 irq 21 chip Yukon-Lite rev 9
[    5.797840] skge eth1: addr 00:17:31:95:2f:97
[    5.802523] usbcore: registered new interface driver hiddev
[    5.805335]   alloc irq_desc for 20 on node -1
[    5.805338]   alloc kstat_irqs on node -1
[    5.805344] ohci1394 0000:01:13.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.807535] input: Saitek GM3200 Laser mouse as /devices/pci0000:00/0000:00:1c.0/usb2/2-1/2-1:1.0/input/input4
[    5.807612] generic-usb 0003:06A3:0004.0001: input,hidraw0: USB HID v1.10 Mouse [Saitek GM3200 Laser mouse] on usb-0000:00:1c.0-1/input0
[    5.807627] usbcore: registered new interface driver usbhid
[    5.807629] usbhid: v2.6:USB HID core driver
[    5.860074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[dfcfb800-dfcfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.654366] xor: automatically using best checksumming function: pIII_sse
[    6.672009]    pIII_sse  :  7246.000 MB/sec
[    6.672011] xor: using function: pIII_sse (7246.000 MB/sec)
[    6.674510] device-mapper: dm-raid45: initialized v0.2594b
[    6.903090] PM: Starting manual resume from disk
[    6.903094] PM: Resume from partition 8:5
[    6.903095] PM: Checking hibernation image.
[    6.903219] PM: Resume from disk failed.
[    6.912915] EXT4-fs (sda4): barriers enabled
[    6.922123] kjournald2 starting: pid 395, dev sda4:8, commit interval 5 seconds
[    6.922149] EXT4-fs (sda4): delayed allocation enabled
[    6.922152] EXT4-fs: file extents enabled
[    6.929897] EXT4-fs: mballoc enabled
[    6.929911] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    7.148123] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000a9f7e2]
[    7.454829] type=1505 audit(1273143508.571:2): operation="profile_load" pid=419 name=/bin/ping
[    7.456385] type=1505 audit(1273143508.575:3): operation="profile_load" pid=420 name=/usr/share/gdm/guest-session/Xsession
[    7.458051] type=1505 audit(1273143508.575:4): operation="profile_load" pid=421 name=/sbin/dhclient3
[    7.458297] type=1505 audit(1273143508.575:5): operation="profile_load" pid=421 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.458436] type=1505 audit(1273143508.575:6): operation="profile_load" pid=421 name=/usr/lib/connman/scripts/dhclient-script
[    7.459685] type=1505 audit(1273143508.575:7): operation="profile_load" pid=422 name=/sbin/klogd
[    7.471390] type=1505 audit(1273143508.587:8): operation="profile_load" pid=423 name=/sbin/syslog-ng
[    7.472760] type=1505 audit(1273143508.591:9): operation="profile_load" pid=424 name=/sbin/syslogd
[    7.507602] type=1505 audit(1273143508.623:10): operation="profile_load" pid=425 name=/usr/bin/evince
[    7.511896] type=1505 audit(1273143508.627:11): operation="profile_load" pid=425 name=/usr/bin/evince-previewer
[   19.501241] udev: starting version 147
[   19.526317] Adding 2996112k swap on /dev/sda5.  Priority:-1 extents:1 across:2996112k 
[   19.973538] lp: driver loaded but no devices found
[   20.008517] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.014481] udev: renamed network interface eth1 to eth0
[   20.044770] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   20.044773] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[   20.049216] udev: renamed network interface eth0_rename to eth1
[   20.066758] gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x201, speed 596kHz
[   20.080840] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   20.080845] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[   20.229475] parport_pc 00:06: reported by Plug and Play ACPI
[   20.229555] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   20.253578] ppdev: user-space parallel port driver
[   20.316256] lp0: using parport0 (interrupt-driven).
[   20.406424] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.411921] SB-XFi 0000:01:11.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.784318] nf_conntrack version 0.5.0 (16378 buckets, 65512 max)
[   20.784584] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   20.784586] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   20.784588] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.889686]   alloc irq_desc for 22 on node -1
[   20.889690]   alloc kstat_irqs on node -1
[   20.889698] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   21.025032] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1d.0/input/input5
[   21.052273] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   44.387022] EXT4-fs (sda4): internal journal on sda4:8
[   44.547271] kjournald starting.  Commit interval 5 seconds
[   44.547285] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   44.555349] EXT3 FS on sda3, internal journal
[   44.555356] EXT3-fs: mounted filesystem with ordered data mode.
[   44.577460] __ratelimit: 54 callbacks suppressed
[   44.577463] type=1505 audit(1273139945.695:30): operation="profile_replace" pid=1227 name=/bin/ping
[   44.578609] type=1505 audit(1273139945.695:31): operation="profile_replace" pid=1228 name=/usr/share/gdm/guest-session/Xsession
[   44.579748] type=1505 audit(1273139945.695:32): operation="profile_replace" pid=1229 name=/sbin/dhclient3
[   44.580023] type=1505 audit(1273139945.699:33): operation="profile_replace" pid=1229 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   44.580165] type=1505 audit(1273139945.699:34): operation="profile_replace" pid=1229 name=/usr/lib/connman/scripts/dhclient-script
[   44.581230] type=1505 audit(1273139945.699:35): operation="profile_replace" pid=1230 name=/sbin/klogd
[   44.582252] type=1505 audit(1273139945.699:36): operation="profile_replace" pid=1231 name=/sbin/syslog-ng
[   44.583356] type=1505 audit(1273139945.699:37): operation="profile_replace" pid=1232 name=/sbin/syslogd
[   44.587794] type=1505 audit(1273139945.703:38): operation="profile_replace" pid=1233 name=/usr/bin/evince
[   44.611368] type=1505 audit(1273139945.727:39): operation="profile_replace" pid=1233 name=/usr/bin/evince-previewer
[   44.673655] sky2 eth1: enabling interface
[   44.707192] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   44.708707] skge eth0: enabling interface
[   44.712124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.974411] [drm] Setting GART location based on new memory map
[   45.975467] [drm] Loading R500 Microcode
[   45.975490] [drm] Num pipes: 4
[   45.975497] [drm] writeback test succeeded in 1 usecs
[   46.413859] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   46.414042] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   47.163002] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   47.163006] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   47.163007] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   47.163009] vboxdrv: the usage of hardware performance counters by
[   47.163010] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   47.163014] vboxdrv: Found 1 processor cores.
[   47.163126] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   47.163128] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   52.902695] CIFS: Unknown mount option cp850
[   52.916509]  CIFS VFS: Error connecting to socket. Aborting operation
[   52.916515]  CIFS VFS: cifs_mount failed w/return code = -111
[   52.916599] CIFS: Unknown mount option cp850
[   52.916898]  CIFS VFS: Error connecting to socket. Aborting operation
[   52.916901]  CIFS VFS: cifs_mount failed w/return code = -111
[   52.916946] CIFS: Unknown mount option cp850
[   52.917293]  CIFS VFS: Error connecting to socket. Aborting operation
[   52.917296]  CIFS VFS: cifs_mount failed w/return code = -111
[   57.092014] eth0: no IPv6 routers present
[  348.106260] __ratelimit: 54 callbacks suppressed
[  348.106264] type=1502 audit(1273140247.541:58): operation="mknod" pid=1968 parent=1 profile="/usr/sbin/nmbd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/var/run/samba/namelist.debug"
[  348.106277] type=1502 audit(1273140247.541:59): operation="open" pid=1968 parent=1 profile="/usr/sbin/nmbd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/var/run/samba/namelist.debug"
[  348.106542] type=1502 audit(1273140247.541:60): operation="file_perm" pid=1968 parent=1 profile="/usr/sbin/nmbd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/var/run/samba/namelist.debug"
[  794.248055] CIFS: Unknown mount option cp850
[  802.656779] UDF-fs: No VRS found
[  802.656783] UDF-fs: No partition found (1)
[  802.665688] ISO 9660 Extensions: Microsoft Joliet Level 1
[  802.667111] ISOFS: changing to secondary root
[ 2402.103627] padlock: VIA PadLock not detected.
[ 2408.770655] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2458.761614] device eth0 entered promiscuous mode
[ 5347.750016] device eth0 left promiscuous mode
[26567.222992] device eth0 entered promiscuous mode
[29261.095478] device eth0 left promiscuous mode
[36413.088032] usb 1-2: new high speed USB device using ehci_hcd and address 3
[36413.226810] usb 1-2: configuration #1 chosen from 1 choice
[36413.764023] usb 1-2: USB disconnect, address 3
[36413.859682] cfg80211: Calling CRDA to update world regulatory domain
[36413.982357] usbcore: registered new interface driver rtl8187
[36414.214462] cfg80211: World regulatory domain updated:
[36414.214466] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[36414.214469] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36414.214472] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[36414.214474] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[36414.214477] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36414.214479] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36471.512096] usb 1-2: new high speed USB device using ehci_hcd and address 4
[36471.650768] usb 1-2: configuration #1 chosen from 1 choice
[36471.978939] phy0: Selected rate control algorithm 'minstrel'
[36471.979723] phy0: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[36471.994301] rtl8187: Customer ID is 0xFF
[36471.994348] Registered led device: rtl8187-phy0::tx
[36471.994363] Registered led device: rtl8187-phy0::rx
[36474.309587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[36492.131613] usb 1-2: USB disconnect, address 4
[36493.660030] usb 1-2: new high speed USB device using ehci_hcd and address 5
[36493.798602] usb 1-2: configuration #1 chosen from 1 choice
[36494.926378] phy1: Selected rate control algorithm 'minstrel'
[36494.927197] phy1: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225
[36494.966106] udev: renamed network interface wlan0 to wlan1
[36495.291949] rtl8187: Customer ID is 0x00
[36495.291996] Registered led device: rtl8187-phy1::tx
[36495.292026] Registered led device: rtl8187-phy1::rx
[36495.292080] usb 1-2: USB disconnect, address 5
[36495.780024] phy1: Reset timeout!
[36496.628032] usb 1-2: new high speed USB device using ehci_hcd and address 6
[36496.766697] usb 1-2: configuration #1 chosen from 1 choice
[36496.936360] phy2: Selected rate control algorithm 'minstrel'
[36496.937214] phy2: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[36496.974206] udev: renamed network interface wlan0 to wlan2
[36496.994122] rtl8187: Customer ID is 0xFF
[36496.994168] Registered led device: rtl8187-phy2::tx
[36496.994183] Registered led device: rtl8187-phy2::rx
[36498.652828] usb 1-2: USB disconnect, address 6
[36498.824222] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[36500.144029] usb 1-2: new high speed USB device using ehci_hcd and address 7
[36500.282567] usb 1-2: configuration #1 chosen from 1 choice
[36500.454522] phy3: Selected rate control algorithm 'minstrel'
[36500.455262] phy3: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[36500.494739] udev: renamed network interface wlan0 to wlan3
[36500.504860] rtl8187: Customer ID is 0xFF
[36500.504909] Registered led device: rtl8187-phy3::tx
[36500.504925] Registered led device: rtl8187-phy3::rx
[36502.513654] ADDRCONF(NETDEV_UP): wlan3: link is not ready
[36766.569984] sky2 eth1: disabling interface
[36766.585607] skge eth0: disabling interface
[36769.674262] sky2 eth1: enabling interface
[36769.674454] ADDRCONF(NETDEV_UP): eth1: link is not ready
[36769.675195] skge eth0: enabling interface
[36769.697544] ADDRCONF(NETDEV_UP): eth0: link is not ready
[36771.361986] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[36771.741307] ADDRCONF(NETDEV_UP): wlan3: link is not ready
[36771.747170] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[36782.308957] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36782.324013] eth0: no IPv6 routers present
[36782.508022] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36782.708020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36782.908018] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36789.396818] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36789.596024] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36789.796020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36789.996023] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36803.609158] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36803.808020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36804.008020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36804.208017] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36810.697265] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36810.896019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36811.096025] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36811.296018] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36817.788872] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36817.988019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36818.188024] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36818.388021] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36831.981087] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36832.180019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36832.380019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36832.580019] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36839.081194] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36839.280022] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36839.481357] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36839.680022] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36842.272800] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36842.472027] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36842.672120] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36842.872023] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36856.457013] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36856.656018] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36856.856022] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36857.056021] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36861.672020]  CIFS VFS: No response for cmd 50 mid 17841
[36863.556992] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36863.756018] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36863.956019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36864.156018] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36870.652855] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36870.852027] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36871.052020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36871.252030] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36877.773087] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36877.972021] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36878.172019] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36878.372018] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36884.860946] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36885.060024] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36885.260020] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36885.460019] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36892.089056] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36892.288025] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36892.488022] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36892.688952] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36899.188914] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 1
[36899.388018] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 2
[36899.588753] wlan3: direct probe to AP 00:21:63:7a:eb:3a try 3
[36899.788019] wlan3: direct probe to AP 00:21:63:7a:eb:3a timed out
[36954.274050]  CIFS VFS: Unexpected lookup error -112
[36954.276030]  CIFS VFS: Unexpected lookup error -112
[36960.452659]  CIFS VFS: Unexpected lookup error -112
[36960.452693]  CIFS VFS: Unexpected lookup error -112
[36960.452705]  CIFS VFS: Unexpected lookup error -112
[36960.452714]  CIFS VFS: Unexpected lookup error -112
[36960.452737]  CIFS VFS: Unexpected lookup error -112
[36960.452759]  CIFS VFS: Unexpected lookup error -112
[36960.452782]  CIFS VFS: Unexpected lookup error -112
[37743.270916] Buffer I/O error on device dm-1, logical block 786433
[37743.271818] Buffer I/O error on device dm-1, logical block 786434
[37743.272717] Buffer I/O error on device dm-1, logical block 786435
[37743.273603] Buffer I/O error on device dm-1, logical block 786436
[37743.274036] Buffer I/O error on device dm-1, logical block 786433
[37743.307637] Buffer I/O error on device dm-1, logical block 786433
[37743.308207] Buffer I/O error on device dm-1, logical block 786433
[37743.308711] Buffer I/O error on device dm-1, logical block 786433
[37743.357432] Buffer I/O error on device dm-1, logical block 786433
[37743.358030] Buffer I/O error on device dm-1, logical block 786433
[37755.483739] __ratelimit: 26 callbacks suppressed
[37755.483743] Buffer I/O error on device dm-1, logical block 786433
[37755.484337] Buffer I/O error on device dm-1, logical block 786433
[37755.484860] Buffer I/O error on device dm-1, logical block 786433
[37755.485355] Buffer I/O error on device dm-1, logical block 786433
[37755.486150] Buffer I/O error on device dm-1, logical block 786433
[37755.486646] Buffer I/O error on device dm-1, logical block 786433
[37755.487152] Buffer I/O error on device dm-1, logical block 786433
[37755.487656] Buffer I/O error on device dm-1, logical block 786433
[37755.488891] Buffer I/O error on device dm-1, logical block 786433
[37755.489405] Buffer I/O error on device dm-1, logical block 786433
[37761.755339] __ratelimit: 70 callbacks suppressed
[37761.755343] Buffer I/O error on device dm-1, logical block 786433
[37761.755934] Buffer I/O error on device dm-1, logical block 786433
[37761.757854] Buffer I/O error on device dm-1, logical block 786433
[37761.758385] Buffer I/O error on device dm-1, logical block 786433
[37761.759369] Buffer I/O error on device dm-1, logical block 786433
[37761.759863] Buffer I/O error on device dm-1, logical block 786433
[37761.760368] Buffer I/O error on device dm-1, logical block 786433
[37761.760857] Buffer I/O error on device dm-1, logical block 786433
[37761.761685] Buffer I/O error on device dm-1, logical block 786433
[37761.762180] Buffer I/O error on device dm-1, logical block 786433
[37766.829731] __ratelimit: 86 callbacks suppressed
[37766.829735] Buffer I/O error on device dm-1, logical block 786433
[37766.830444] Buffer I/O error on device dm-1, logical block 786433
[37766.831012] Buffer I/O error on device dm-1, logical block 786433
[37766.831519] Buffer I/O error on device dm-1, logical block 786433
[37766.833523] Buffer I/O error on device dm-1, logical block 786433
[37766.834025] Buffer I/O error on device dm-1, logical block 786433
[37766.834532] Buffer I/O error on device dm-1, logical block 786433
[37766.835024] Buffer I/O error on device dm-1, logical block 786433
[37766.835971] Buffer I/O error on device dm-1, logical block 786433
[37766.836479] Buffer I/O error on device dm-1, logical block 786433
[37773.232671] __ratelimit: 183 callbacks suppressed
[37773.232675] Buffer I/O error on device dm-1, logical block 786433
[37773.233236] Buffer I/O error on device dm-1, logical block 786433
[37773.233767] Buffer I/O error on device dm-1, logical block 786433
[37773.234267] Buffer I/O error on device dm-1, logical block 786433
[37773.235351] Buffer I/O error on device dm-1, logical block 786433
[37773.235846] Buffer I/O error on device dm-1, logical block 786433
[37773.236352] Buffer I/O error on device dm-1, logical block 786433
[37773.236839] Buffer I/O error on device dm-1, logical block 786433
[37773.237865] Buffer I/O error on device dm-1, logical block 786433
[37773.238368] Buffer I/O error on device dm-1, logical block 786433
[37849.248617] __ratelimit: 38 callbacks suppressed
[37849.248621] Buffer I/O error on device dm-1, logical block 786433
[38629.134566] usb 1-2: USB disconnect, address 7
[38634.956024] usb 1-2: new high speed USB device using ehci_hcd and address 8
[38635.094628] usb 1-2: configuration #1 chosen from 1 choice
[38635.255096] phy4: Selected rate control algorithm 'minstrel'
[38635.255890] phy4: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[38635.288841] udev: renamed network interface wlan0 to wlan4
[38635.307930] rtl8187: Customer ID is 0xFF
[38635.307973] Registered led device: rtl8187-phy4::tx
[38635.307989] Registered led device: rtl8187-phy4::rx
[38637.273303] ADDRCONF(NETDEV_UP): wlan4: link is not ready
[39018.519882] usb 1-2: USB disconnect, address 8
[39021.184024] usb 1-2: new high speed USB device using ehci_hcd and address 9
[39021.325403] usb 1-2: configuration #1 chosen from 1 choice
[39021.484799] phy5: Selected rate control algorithm 'minstrel'
[39021.485588] phy5: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[39021.538344] udev: renamed network interface wlan0 to wlan5
[39021.557581] rtl8187: Customer ID is 0xFF
[39021.557628] Registered led device: rtl8187-phy5::tx
[39021.557645] Registered led device: rtl8187-phy5::rx
[39023.398137] phy5: RF Calibration Failed! a66
[39023.869341] ADDRCONF(NETDEV_UP): wlan5: link is not ready

```

---

### Post by NiGhtMarEs0nWax on 2010-05-07
bump, i can see the AP but i cannot connect to it. Wicd says "access point is not accessible," it is an open system, no encryption.

---

### Post by NiGhtMarEs0nWax on 2010-05-07
here is some more info for you. please help!


$ lsusb
```
Bus 002 Device 002: ID 06a3:0004 Saitek PLC 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003:** ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

$ dmesg | grep 8187
```
[19581.331244] phy0: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[19581.344422] rtl8187: Customer ID is 0xFF
[19581.344469] Registered led device: rtl8187-phy0::tx
[19581.344485] Registered led device: rtl8187-phy0::rx
[19581.344506] usbcore: registered new interface driver rtl8187

```

$ lsmod | grep 8187
```
rtl8187                50624  0 
mac80211              181140  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
snd_ctxfi              81876  3 
```


$ iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wmaster0  no wireless extensions.

wlan9     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


just thought i'd trim it down. =P

$ dmesg | grep 8187
```
[19581.331244] phy0: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[19581.344422] rtl8187: Customer ID is 0xFF
[19581.344469] Registered led device: rtl8187-phy0::tx
[19581.344485] Registered led device: rtl8187-phy0::rx
[19581.344506] usbcore: registered new interface driver rtl8187
[45019.195342] phy1: hwaddr 00:c0:ca:3a:78:26, RTL8187vB (default) V1 + rtl8225z2
[45019.212017] rtl8187: Customer ID is 0xFF
[45019.212057] Registered led device: rtl8187-phy1::tx
[45019.212072] Registered led device: rtl8187-phy1::rx

```

---

### Post by NiGhtMarEs0nWax on 2010-05-08
bump, the connection is intermittent, i managed to get it connected last night, but it won't reconnect again.

---

### Post by campanada on 2010-06-07
I have the same problem as you.
My ubuntu 9.10 detects my usb wifi adapter but I cannot see any networks. I can see the message "RF calibration failed a66" in /var/log/messages.

Sometimes times it works, but in several  minutes led is off and the connection is lost.

Any new ideas?
Thanks

---

### Post by campanada on 2010-12-09
In my case, it seems to be a HW problem with some of the joints. I have applied heat to the wifi card only  the card without the plastic and IT WORKS perfectly.

In my case I put the card in the oven 9 minutes at 190 degrees. Search in internet there  are several videos of how to do this.

Thanks and good luck.

---

