---
title: "RTL8185B and r8185b not working"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by w2vy on 2010-09-12
I have followed the [Wireless Troubleshooting wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and I find what looks like a name mismatch

```
tom@w2vy:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 20
       serial: 00:06:4f:81:1f:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8185B latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=802.11bg
       resources: irq:19 ioport:b000(size=256) memory:e6000000-e60001ff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:83:62:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.3.10 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:e6003000-e60030ff

```

configuration: broadcast=yes driver=**rtl8185B** latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=802.11bg

and

```
tom@w2vy:~$ lsmod |grep 8185
r8185b                172928  0 
tom@w2vy:~$ 

```
 I see the pid==0 so not being used.

How can I get them to connect?

What is strange is the same compiled code works fine on a different system.

I downloaded the driver from RealTek in source form.

tom
---

Ok now it is even stranger (to me)

The card does seem to be working since

sudo iwlist scan

does return a list of valid networks I can hear

What to check next?
Nothing in dmesg jumps out at me. (below)

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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 00E0000000 mask FFFC000000 write-combining
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
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  modified: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  modified: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37858000 - 37fefc35
[    0.000000] Allocated new RAMDISK: 008e2000 - 01079c35
[    0.000000] Move RAMDISK from 0000000037858000 - 0000000037fefc34 to 008e2000 - 01079c34
[    0.000000] ACPI: RSDP 000f6ed0 00014 (v00 FIC   )
[    0.000000] ACPI: RSDT 7fff3000 00030 (v01 FIC    K8-800T  42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 7fff3040 00074 (v01 FIC    K8-800T  42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 7fff30c0 04AF4 (v01 FIC    AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fff0000 00040
[    0.000000] ACPI: DBGP 7fff7c40 00034 (v01 FIC    K8-800T  42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 7fff7bc0 0005A (v01 FIC    K8-800T  42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e1082]              BRK ==> [00008de000 - 00008e1082]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e2000 - 0001079c35]      NEW RAMDISK ==> [00008e2000 - 0001079c35]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f54b0] f54b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524159
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c107b200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294626 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520063
[    0.000000] Kernel command line: root=UUID=62c51c75-0752-4405-b6dc-ff3ef7e97208 ro nomodeset quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10485120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fff0)
[    0.000000] Memory: 2052244k/2097088k available (4679k kernel code, 43388k reserved, 2124k data, 660k init, 1187784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2200.231 MHz processor.
[    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.46 BogoMIPS (lpj=8800924)
[    0.008024] Security Framework initialized
[    0.008050] AppArmor: AppArmor initialized
[    0.008058] Mount-cache hash table entries: 512
[    0.008180] Initializing cgroup subsys ns
[    0.008184] Initializing cgroup subsys cpuacct
[    0.008187] Initializing cgroup subsys memory
[    0.008195] Initializing cgroup subsys devices
[    0.008198] Initializing cgroup subsys freezer
[    0.008200] Initializing cgroup subsys net_cls
[    0.008218] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008220] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.008224] mce: CPU supports 5 MCE banks
[    0.008240] Performance Events: AMD PMU driver.
[    0.008247] ... version:                0
[    0.008249] ... bit width:              48
[    0.008250] ... generic registers:      4
[    0.008252] ... value mask:             0000ffffffffffff
[    0.008255] ... max period:             00007fffffffffff
[    0.008256] ... fixed-purpose events:   0
[    0.008258] ... event mask:             000000000000000f
[    0.008262] Checking 'hlt' instruction... OK.
[    0.024694] SMP alternatives: switching to UP code
[    0.030292] Freeing SMP alternatives: 19k freed
[    0.030304] ACPI: Core revision 20090903
[    0.036031] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036039] ftrace: allocating 21780 entries in 43 pages
[    0.040098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040923] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.082912] CPU0: AMD Athlon(tm) 64 Processor 3400+ stepping 0a
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (4400.46 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] devtmpfs: initialized
[    0.084001] regulator: core version 0.5
[    0.084001] Time:  3:19:59  Date: 09/13/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: PCI BIOS revision 2.10 entry at 0xfbc80, last bus=1
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084001] ACPI: EC: Look up EC in DSDT
[    0.088232] ACPI: Interpreter enabled
[    0.088240] ACPI: (supports S0 S3 S4 S5)
[    0.088264] ACPI: Using IOAPIC for interrupt routing
[    0.093131] ACPI: No dock devices found.
[    0.093210] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.093252] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[    0.093327] pci 0000:00:01.0: supports D1
[    0.093359] pci 0000:00:0c.0: reg 10 io port: [0xb000-0xb0ff]
[    0.093365] pci 0000:00:0c.0: reg 14 32bit mmio: [0xe6000000-0xe60001ff]
[    0.093394] pci 0000:00:0c.0: supports D1 D2
[    0.093397] pci 0000:00:0c.0: PME# supported from D1 D2 D3hot D3cold
[    0.093400] pci 0000:00:0c.0: PME# disabled
[    0.093426] pci 0000:00:0e.0: reg 10 32bit mmio: [0xe6001000-0xe60017ff]
[    0.093432] pci 0000:00:0e.0: reg 14 io port: [0xb400-0xb47f]
[    0.093462] pci 0000:00:0e.0: supports D2
[    0.093464] pci 0000:00:0e.0: PME# supported from D2 D3hot D3cold
[    0.093468] pci 0000:00:0e.0: PME# disabled
[    0.093493] pci 0000:00:0f.0: reg 10 io port: [0xb800-0xb807]
[    0.093499] pci 0000:00:0f.0: reg 14 io port: [0xbc00-0xbc03]
[    0.093504] pci 0000:00:0f.0: reg 18 io port: [0xc000-0xc007]
[    0.093510] pci 0000:00:0f.0: reg 1c io port: [0xc400-0xc403]
[    0.093516] pci 0000:00:0f.0: reg 20 io port: [0xc800-0xc80f]
[    0.093521] pci 0000:00:0f.0: reg 24 io port: [0xcc00-0xccff]
[    0.093576] pci 0000:00:0f.1: reg 20 io port: [0xd000-0xd00f]
[    0.093637] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[    0.093657] pci 0000:00:10.0: supports D1 D2
[    0.093659] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093662] pci 0000:00:10.0: PME# disabled
[    0.093698] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[    0.093717] pci 0000:00:10.1: supports D1 D2
[    0.093719] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093722] pci 0000:00:10.1: PME# disabled
[    0.093758] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[    0.093777] pci 0000:00:10.2: supports D1 D2
[    0.093779] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093782] pci 0000:00:10.2: PME# disabled
[    0.093818] pci 0000:00:10.3: reg 20 io port: [0xe000-0xe01f]
[    0.093837] pci 0000:00:10.3: supports D1 D2
[    0.093839] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093842] pci 0000:00:10.3: PME# disabled
[    0.093866] pci 0000:00:10.4: reg 10 32bit mmio: [0xe6002000-0xe60020ff]
[    0.093897] pci 0000:00:10.4: supports D1 D2
[    0.093899] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.093903] pci 0000:00:10.4: PME# disabled
[    0.093950] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.093989] pci 0000:00:11.5: reg 10 io port: [0xe400-0xe4ff]
[    0.094023] pci 0000:00:11.5: supports D1 D2
[    0.094050] pci 0000:00:13.0: reg 10 io port: [0xe800-0xe8ff]
[    0.094055] pci 0000:00:13.0: reg 14 32bit mmio: [0xe6003000-0xe60030ff]
[    0.094085] pci 0000:00:13.0: supports D1 D2
[    0.094087] pci 0000:00:13.0: PME# supported from D1 D2 D3hot D3cold
[    0.094090] pci 0000:00:13.0: PME# disabled
[    0.094167] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.094172] pci 0000:01:00.0: reg 14 io port: [0xa000-0xa0ff]
[    0.094176] pci 0000:01:00.0: reg 18 32bit mmio: [0xe5000000-0xe500ffff]
[    0.094186] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.094197] pci 0000:01:00.0: supports D1 D2
[    0.094213] pci 0000:01:00.1: reg 10 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.094218] pci 0000:01:00.1: reg 14 32bit mmio: [0xe5010000-0xe501ffff]
[    0.094235] pci 0000:01:00.1: supports D1 D2
[    0.094259] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.094262] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.094267] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.094273] pci_bus 0000:00: on NUMA node 0
[    0.094277] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.129038] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 *12)
[    0.129169] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.129302] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.129435] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[    0.129546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.129652] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.129758] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.129864] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.129989] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.130115] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.130257] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.130381] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.130482] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.130485] vgaarb: loaded
[    0.130589] SCSI subsystem initialized
[    0.130658] libata version 3.00 loaded.
[    0.130718] usbcore: registered new interface driver usbfs
[    0.130729] usbcore: registered new interface driver hub
[    0.130751] usbcore: registered new device driver usb
[    0.130857] ACPI: WMI: Mapper loaded
[    0.130859] PCI: Using ACPI for IRQ routing
[    0.130977] NetLabel: Initializing
[    0.130978] NetLabel:  domain hash size = 128
[    0.130980] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130992] NetLabel:  unlabeled traffic allowed by default
[    0.131035] Switching to clocksource tsc
[    0.131998] AppArmor: AppArmor Filesystem Enabled
[    0.131998] pnp: PnP ACPI init
[    0.131998] ACPI: bus type pnp registered
[    0.132606] pnp: PnP ACPI: found 13 devices
[    0.132608] ACPI: ACPI bus type pnp unregistered
[    0.132611] PnPBIOS: Disabled by ACPI PNP
[    0.132621] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    0.132624] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    0.132627] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.132630] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.132633] system 00:00: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.132637] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.132640] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.132643] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.132646] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.132649] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.132652] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.132658] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.132661] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.132666] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.132669] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.132672] system 00:03: ioport range 0x290-0x297 has been reserved
[    0.167330] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.167333] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.167338] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.167342] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.167355] pci 0000:00:01.0: setting latency timer to 64
[    0.167360] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.167363] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.167366] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.167368] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.167371] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.167403] NET: Registered protocol family 2
[    0.167486] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.167828] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.168686] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.169145] TCP: Hash tables configured (established 131072 bind 65536)
[    0.169148] TCP reno registered
[    0.169234] NET: Registered protocol family 1
[    0.169249] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.169329] pci 0000:01:00.0: Boot video device
[    0.169514] cpufreq-nforce2: No nForce2 chipset.
[    0.169538] Scanning for low memory corruption every 60 seconds
[    0.169638] audit: initializing netlink socket (disabled)
[    0.169651] type=2000 audit(1284347999.168:1): initialized
[    0.178843] Trying to unpack rootfs image as initramfs...
[    0.189319] highmem bounce pool size: 64 pages
[    0.189325] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.197226] VFS: Disk quotas dquot_6.5.2
[    0.197306] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.197858] fuse init (API version 7.13)
[    0.197937] msgmni has been set to 1690
[    0.198121] alg: No test for stdrng (krng)
[    0.198173] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.198176] io scheduler noop registered
[    0.198178] io scheduler anticipatory registered
[    0.198180] io scheduler deadline registered
[    0.198217] io scheduler cfq registered (default)
[    0.198319] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.198337] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.198420] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.198424] ACPI: Power Button [PWRB]
[    0.198472] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.198474] ACPI: Power Button [PWRF]
[    0.198510] fan PNP0C0B:00: registered as cooling_device0
[    0.198515] ACPI: Fan [FAN] (on)
[    0.198746] processor LNXCPU:00: registered as cooling_device1
[    0.201324] thermal LNXTHERM:01: registered as thermal_zone0
[    0.201333] ACPI: Thermal Zone [THRM] (40 C)
[    0.205106] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.205197] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.205282] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.205541] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.205651] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.206546] brd: module loaded
[    0.206958] loop: module loaded
[    0.207037] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.207393] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.207396] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.207401]   alloc irq_desc for 20 on node -1
[    0.207403]   alloc kstat_irqs on node -1
[    0.207411] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.207463] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.207476] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.207494] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.207750] Fixed MDIO Bus: probed
[    0.207783] PPP generic driver version 2.4.2
[    0.207815] tun: Universal TUN/TAP device driver, 1.6
[    0.207817] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.207883] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.208073] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.208076] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.208078]   alloc irq_desc for 21 on node -1
[    0.208080]   alloc kstat_irqs on node -1
[    0.208084] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.208100] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.208131] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.208191] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe6002000
[    0.208220] isapnp: Scanning for PnP cards...
[    0.217010] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.217102] usb usb1: configuration #1 chosen from 1 choice
[    0.217128] hub 1-0:1.0: USB hub found
[    0.217137] hub 1-0:1.0: 8 ports detected
[    0.217191] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.217204] uhci_hcd: USB Universal Host Controller Interface driver
[    0.217240] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.217247] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.217280] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.217300] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    0.217381] usb usb2: configuration #1 chosen from 1 choice
[    0.217402] hub 2-0:1.0: USB hub found
[    0.217409] hub 2-0:1.0: 2 ports detected
[    0.217446] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.217451] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.217476] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.217493] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    0.217577] usb usb3: configuration #1 chosen from 1 choice
[    0.217598] hub 3-0:1.0: USB hub found
[    0.217612] hub 3-0:1.0: 2 ports detected
[    0.217647] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.217652] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.217680] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.217698] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.217781] usb usb4: configuration #1 chosen from 1 choice
[    0.217803] hub 4-0:1.0: USB hub found
[    0.217809] hub 4-0:1.0: 2 ports detected
[    0.217844] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.217849] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.217875] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.217892] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    0.217973] usb usb5: configuration #1 chosen from 1 choice
[    0.217995] hub 5-0:1.0: USB hub found
[    0.218002] hub 5-0:1.0: 2 ports detected
[    0.218077] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.218079] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.218241] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.218331] mice: PS/2 mouse device common for all mice
[    0.218435] rtc_cmos 00:05: RTC can wake from S4
[    0.218470] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.218520] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.218614] device-mapper: uevent: version 1.0.3
[    0.264888] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.268477] device-mapper: multipath: version 1.1.0 loaded
[    0.268480] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.268613] EISA: Probing bus 0 at eisa.0
[    0.268631] Cannot allocate resource for EISA slot 4
[    0.268633] Cannot allocate resource for EISA slot 5
[    0.268646] EISA: Detected 0 cards.
[    0.268687] cpuidle: using governor ladder
[    0.268689] cpuidle: using governor menu
[    0.269083] TCP cubic registered
[    0.269225] NET: Registered protocol family 10
[    0.269616] lo: Disabled Privacy Extensions
[    0.269888] NET: Registered protocol family 17
[    0.269915] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[    0.269947] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20090903/processor_perflib-264)
[    0.275130] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.280959] ACPI Exception: AE_NOT_FOUND, Evaluating _PSS (20090903/processor_perflib-264)
[    0.280970] Using IPI No-Shortcut mode
[    0.281074] PM: Resume from disk failed.
[    0.281090] registered taskstats version 1
[    0.281338]   Magic number: 10:580:310
[    0.281364] tty tty39: hash matches
[    0.281434] rtc_cmos 00:05: setting system clock to 2010-09-13 03:20:00 UTC (1284348000)
[    0.281437] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.281438] EDD information not available.
[    0.285238] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.625306] Freeing initrd memory: 7775k freed
[    0.761955] isapnp: No Plug & Play device found
[    0.761966] Freeing unused kernel memory: 660k freed
[    0.762624] Write protecting the kernel text: 4680k
[    0.762654] Write protecting the kernel read-only data: 1844k
[    0.779661] udev: starting version 151
[    0.828961] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    0.956583] sata_via 0000:00:0f.0: version 2.4
[    0.956602] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.956642] sata_via 0000:00:0f.0: routed to hard irq line 11
[    0.956924] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.963330] scsi0 : sata_via
[    0.963503] scsi1 : sata_via
[    0.963545] ata1: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    0.963548] ata2: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    0.963597] pata_via 0000:00:0f.1: version 0.3.4
[    0.963611] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.963900] scsi2 : pata_via
[    0.963986] scsi3 : pata_via
[    0.965157] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    0.965159] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    0.965281] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.967668] Floppy drive(s): fd0 is 1.44M
[    0.984790] FDC 0 is a post-1991 82077
[    1.009221] usb 2-2: configuration #1 chosen from 1 choice
[    1.168010] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.380008] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.544335] ata2.00: ATA-8: WDC WD3200AAKS-00L9A0, 01.03E01, max UDMA/133
[    1.544338] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.560345] ata2.00: configured for UDMA/133
[    1.560447] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.560583] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.560882] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.560923] sd 1:0:0:0: [sda] Write Protect is off
[    1.560926] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.560947] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.561066]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.601600] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.724336] ata4.00: ATAPI: SONY    DVD RW DW-U18A, UYS1, max UDMA/33
[    1.740221] ata4.00: configured for UDMA/33
[    1.741404] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DW-U18A   UYS1 PQ: 0 ANSI: 5
[    1.745193] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.745196] Uniform CD-ROM driver Revision: 3.20
[    1.745270] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.745310] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.751378] 8139too Fast Ethernet driver 0.9.28
[    1.751412]   alloc irq_desc for 17 on node -1
[    1.751414]   alloc kstat_irqs on node -1
[    1.751421] 8139too 0000:00:13.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.758633] eth0: RealTek RTL8139 at 0xe800, 00:40:ca:83:62:b3, IRQ 17
[    1.758762]   alloc irq_desc for 16 on node -1
[    1.758765]   alloc kstat_irqs on node -1
[    1.758772] ohci1394 0000:00:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.762058] usbcore: registered new interface driver hiddev
[    1.775230] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/input/input4
[    1.775320] generic-usb 0003:045E:0084.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:10.0-2/input0
[    1.775348] usbcore: registered new interface driver usbhid
[    1.775350] usbhid: v2.6:USB HID core driver
[    1.814050] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[e6001000-e60017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.088112] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca070109fe31]
[    7.185515] kjournald starting.  Commit interval 5 seconds
[    7.185526] EXT3-fs: mounted filesystem with ordered data mode.
[    8.876595] Adding 4192924k swap on /dev/sda6.  Priority:-1 extents:1 across:4192924k 
[    9.029952] udev: starting version 151
[   10.103816] lp: driver loaded but no devices found
[   10.499348] parport_pc 00:0b: reported by Plug and Play ACPI
[   10.499430] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   10.593448] ieee80211_crypt: registered algorithm 'NULL'
[   10.593453] ieee80211_crypt: registered algorithm 'TKIP'
[   10.593455] ieee80211_crypt: registered algorithm 'CCMP'
[   10.593457] ieee80211_crypt: registered algorithm 'WEP'
[   10.593458] 
[   10.593459] Linux kernel driver for RTL8180 RTL8185 based WLAN cards
[   10.593461] Copyright (c) 2004-2005, Andrea Merello
[   10.593462] rtl8185B: Initializing module
[   10.593464] rtl8185B: Wireless extensions version 22
[   10.593466] rtl8185B: Initializing proc filesystem
[   10.593484] rtl8185B: Configuring chip resources
[   10.593498]   alloc irq_desc for 19 on node -1
[   10.593500]   alloc kstat_irqs on node -1
[   10.593507] rtl8185B 0000:00:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.596163] lp0: using parport0 (interrupt-driven).
[   10.598589] rtl8185B: Memory mapped space @ 0xe6000000 
[   10.598613] rtl8185B: MAC controller is a RTL8185 b/g (V. D)
[   10.598616] rtl8185B: This is a PCI NIC
[   10.598618] rtl8185B: Reported EEPROM chip is a 93c46 (1Kbit)
[   10.614493] rtl8185B: Card MAC address is 00:06:4f:81:1f:c2
[   10.650563] rtl8185B: EEPROM version 105
[   10.655067] rtl8185B: Card reports RF frontend Realtek 8225
[   10.655069] rtl8185B: WW:This driver has EXPERIMENTAL support for this chipset.
[   10.655071] rtl8185B: WW:use it with care and at your own risk and
[   10.655073] rtl8185B: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[   10.760423] rtl8185B: This seems a new V2 radio
[   10.760425] rtl8185B: Energy threshold: b
[   10.760427] rtl8185B: PAPE from CONFIG2: 6
[   10.771985] ppdev: user-space parallel port driver
[   10.776262] Linux agpgart interface v0.103
[   10.776930] rtl8185B: IRQ 19
[   10.777679] rtl8185B: Driver probe completed
[   10.777681] 
[   10.777981] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.783003] type=1505 audit(1284348010.998:2):  operation="profile_load" pid=430 name="/sbin/dhclient3"
[   10.783269] type=1505 audit(1284348010.998:3):  operation="profile_load" pid=430 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.783417] type=1505 audit(1284348010.998:4):  operation="profile_load" pid=430 name="/usr/lib/connman/scripts/dhclient-script"
[   10.814220] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[   10.817198] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   10.877347] [drm] Initialized drm 1.1.0 20060810
[   10.921493] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   11.003863] type=1505 audit(1284348011.218:5):  operation="profile_load" pid=548 name="/usr/sbin/ntpd"
[   11.258538] [drm] VGACON disable radeon kernel modesetting.
[   11.258655] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.258864] [drm] Initialized radeon 1.32.0 20080528 for 0000:01:00.0 on minor 0
[   11.366784] vga16fb: initializing
[   11.366790] vga16fb: mapped to 0xc00a0000
[   11.366921] fb0: VGA16 VGA frame buffer device
[   11.645518] Console: switching to colour frame buffer device 80x30
[   12.509482] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   12.509486] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   12.509491]   alloc irq_desc for 22 on node -1
[   12.509494]   alloc kstat_irqs on node -1
[   12.509501] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   12.509656] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   14.708996] EXT3 FS on sda2, internal journal
[   14.790069] kjournald starting.  Commit interval 5 seconds
[   14.790350] EXT3 FS on sda1, internal journal
[   14.790356] EXT3-fs: mounted filesystem with ordered data mode.
[   15.272411] kjournald starting.  Commit interval 5 seconds
[   15.272756] EXT3 FS on sda3, internal journal
[   15.272762] EXT3-fs: mounted filesystem with ordered data mode.
[   15.485453] kjournald starting.  Commit interval 5 seconds
[   15.485758] EXT3 FS on sda5, internal journal
[   15.485763] EXT3-fs: mounted filesystem with ordered data mode.
[   19.238188] type=1505 audit(1284348019.026:6):  operation="profile_load" pid=961 name="/usr/share/gdm/guest-session/Xsession"
[   19.239964] type=1505 audit(1284348019.026:7):  operation="profile_replace" pid=965 name="/sbin/dhclient3"
[   19.240519] type=1505 audit(1284348019.028:8):  operation="profile_replace" pid=965 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.240675] type=1505 audit(1284348019.028:9):  operation="profile_replace" pid=965 name="/usr/lib/connman/scripts/dhclient-script"
[   19.666474] type=1505 audit(1284348019.452:10):  operation="profile_load" pid=966 name="/usr/bin/evince"
[   19.670227] type=1505 audit(1284348019.456:11):  operation="profile_load" pid=966 name="/usr/bin/evince-previewer"
[   19.672664] type=1505 audit(1284348019.460:12):  operation="profile_load" pid=966 name="/usr/bin/evince-thumbnailer"
[   19.750771] type=1505 audit(1284348019.537:13):  operation="profile_load" pid=1037 name="/usr/lib/cups/backend/cups-pdf"
[   19.751106] type=1505 audit(1284348019.537:14):  operation="profile_load" pid=1037 name="/usr/sbin/cupsd"
[   19.763071] rtl8185B: Bringing up iface
[   19.971469] rtl8185B: Card successfully reset
[   21.568003] eth0: no IPv6 routers present
[   24.407989] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.482369] type=1505 audit(1284348024.268:15):  operation="profile_load" pid=1038 name="/usr/sbin/mysqld"
[   24.485817] type=1505 audit(1284348024.272:16):  operation="profile_replace" pid=1042 name="/usr/sbin/ntpd"
[   24.536333] type=1505 audit(1284348024.324:17):  operation="profile_load" pid=1044 name="/usr/sbin/tcpdump"
[   26.181581] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   26.181586] apm: overridden by ACPI.
[   26.955762] type=1505 audit(1284348026.740:18):  operation="profile_replace" pid=1143 name="/usr/sbin/mysqld"
[   27.039515] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   27.039532] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   27.039586] pci 0000:01:00.0: putting AGP V3 device into 8x mode
```

Here are the 8185 and wlan0 lines from syslog

```
Sep 12 23:20:19 w2vy NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Sep 12 23:20:19 w2vy NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Sep 12 23:20:19 w2vy kernel: [   19.750771] type=1505 audit(1284348019.537:13):  operation="profile_load" pid=1037 name="/usr/lib/cups/backend/cups-pdf"
Sep 12 23:20:19 w2vy kernel: [   19.751106] type=1505 audit(1284348019.537:14):  operation="profile_load" pid=1037 name="/usr/sbin/cupsd"
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8185B')
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): now managed
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): bringing up device.
Sep 12 23:20:24 w2vy kernel: [   19.763071] rtl8185B: Bringing up iface
Sep 12 23:20:24 w2vy kernel: [   19.971469] rtl8185B: Card successfully reset
Sep 12 23:20:24 w2vy kernel: [   21.568003] eth0: no IPv6 routers present
Sep 12 23:20:24 w2vy kernel: [   24.407989] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 12 23:20:24 w2vy NetworkManager: <info>  (wlan0): preparing device.
Sep 12 23:20:24 w2vy NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Sep 12 23:20:24 w2vy NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Sep 12 23:20:24 w2vy NetworkManager: <info>  (eth0): carrier is OFF
Sep 12 23:20:24 w2vy NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too')
Sep 12 23:20:24 w2vy NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 12 23:20:24 w2vy NetworkManager: <info>  modem-manager is now available
Sep 12 23:20:24 w2vy NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep 12 23:20:24 w2vy NetworkManager: <info>  (eth0): carrier now ON (device state 1)
Sep 12 23:20:24 w2vy NetworkManager: <info>  Trying to start the supplicant...
Sep 12 23:20:24 w2vy modem-manager: Loaded plugin MotoC
Sep 12 23:20:24 w2vy ntpd_initres[929]: host name not found: libra.rice.edu
Sep 12 23:20:24 w2vy kernel: [   24.482369] type=1505 audit(1284348024.268:15):  operation="profile_load" pid=1038 name="/usr/sbin/mysqld"
Sep 12 23:20:24 w2vy kernel: [   24.485817] type=1505 audit(1284348024.272:16):  operation="profile_replace" pid=1042 name="/usr/sbin/ntpd"
Sep 12 23:20:24 w2vy kernel: [   24.536333] type=1505 audit(1284348024.324:17):  operation="profile_load" pid=1044 name="/usr/sbin/tcpdump"
Sep 12 23:20:24 w2vy avahi-daemon[968]: Server startup complete. Host name is w2vy.local. Local service cookie is 818007028.
Sep 12 23:20:24 w2vy NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Sep 12 23:20:24 w2vy modem-manager: Loaded plugin Ericsson MBM
Sep 12 23:20:24 w2vy NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Sep 12 23:20:24 w2vy NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 12 23:20:24 w2vy NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Sep 12 23:20:24 w2vy NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Sep 12 23:20:25 w2vy cron[1100]: (CRON) INFO (pidfile fd = 3)
Sep 12 23:20:25 w2vy acpid: starting up with proc fs
Sep 12 23:20:25 w2vy init: apport pre-start process (1096) terminated with status 1
Sep 12 23:20:25 w2vy init: apport post-stop process (1112) terminated with status 1
Sep 12 23:20:25 w2vy anacron[1115]: Anacron 2.3 started on 2010-09-12

```

I do find it odd that I see

Sep 12 23:20:19 w2vy NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).

But iwlist scan works...

tom

---

### Post by MaindotC on 2010-09-13
I don't see what the problem is.  Left-click on Network Manager in the top right of your screen and select the network you want to join.

---

### Post by w2vy on 2010-09-13
> **strAlan said:**
> I don't see what the problem is.  Left-click on Network Manager in the top right of your screen and select the network you want to join.

I have been fighting this for a while and had given up on the no nm-applet icon threads assuming it was something else...

here is my icon panel

[IMG]http://moulton.us/no_nm-applet.png[/IMG]

So yes my real problem is no NetworkManager icon to click...

sorry for the confusion

tom
ps when I go to System->Preferences->Network Connections and select the Wireless Tab
No networks are displayed, will any discovered networks show up there?

This is strange... this fixed it for this session... now to reboot...
[restart NetworkManager]("http://ubuntuforums.org/showpost.php?p=9711202&postcount=4")

---

### Post by MaindotC on 2010-09-13
I'm not sure why your network-manager icon isn't showing.  The other day mine just stopped working altogether and I've been trying to get it to come back but nm-applet keeps on saying "NetworkManager is not running..."

So, a work-around, not a solution, is to edit /etc/network/interfaces file to say the following:```
auto lo eth0 wlan0
iface lo inet loopback
iface eth0 inet dhcp
iface wlan inet dhcp
```Then issue the following command:```
sudo /etc/init.d/networking restart[/url] or if it complains about using the "service" command then try that:[code]sudo service networking restart
```

As for connecting to a wireless network - my work-around suggestion is to completely remove gnome-network-manager and network-manager with Synaptic, then install the application named "Wicd"  Then after you reboot you can use wicd to find a wireless network.

Again, this is a work-around and not a solution.

---

### Post by w2vy on 2010-09-13
> **strAlan said:**
> I'm not sure why your network-manager icon isn't showing.  The other day mine just stopped working altogether and I've been trying to get it to come back but nm-applet keeps on saying "NetworkManager is not running..."

So, a work-around, not a solution, is to edit /etc/network/interfaces file to say the following:```
auto lo eth0 wlan0
iface lo inet loopback
iface eth0 inet dhcp
iface wlan inet dhcp
```Then issue the following command:```
sudo /etc/init.d/networking restart[/url] or if it complains about using the "service" command then try that:[code]sudo service networking restart
```

As for connecting to a wireless network - my work-around suggestion is to completely remove gnome-network-manager and network-manager with Synaptic, then install the application named "Wicd"  Then after you reboot you can use wicd to find a wireless network.

Again, this is a work-around and not a solution.

There seems to be some unseen pattern to the missing nm-applet

The restart of NetworkManager did fix the missing icon for me.
I also realized I needed to remove all references to wlan0 from
/etc/network/interfaces for NM to Manage the interface.
(Wireless was showing up as 'Not Managed")

And since I run services and use automatic login, I needed to
manually edit the connection with fixed IP and made the connection
available to all users.
(Because my Key Ring was not unlocked at auto-login) 

So it looks like I am ok now
Thanks!

---

### Post by MaindotC on 2010-09-13
Really well it [didn't help me!](http://ubuntuforums.org/showthread.php?p=9840412)  I'm glad your system is working now.  Please mark the thread as solved and edit your first post to state "Update:" and the solution so other users do not have to read the entire thread.

---

