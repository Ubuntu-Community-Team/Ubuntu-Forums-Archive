---
title: "HVR-1800 locking up system. HELP!?"
date: 2009-06-06
forum: Mythbuntu
---

### Post by ktuimala on 2009-06-06
I am relatively new to Ubuntu and Linux at large. I have a HVR-1800 that is driving me insane. I followed all of the directions I could find on LinuxTV.org and for all intensive purposes it is installed. However, my HVR-1800 is causing a system wide lockup as soon as MythTV attempts to fire up the hardware. The odd thing is that the MythTV backend is able to scan all cable channels and add them to channel lists without locking up the entire system.

Any help would be greatly appreciated. I really don't know what you would need to see to help me diagnose it, so please let me know what will help you help me and I will post it.

I am using Ubuntu 9.04.

Thanks

---

### Post by ktuimala on 2009-06-06
I managed to pull some information on my system's configuration. I hope this can help solve my system locking issue with my HVR-1800.

Thanks!

dmesg:
```
[    0.000000] BIOS EBDA/lowmem at: 0009ec00/0009ec00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  modified: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  modified: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef5bd
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb25bd
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef5bc to 00881000 - 00fb25bc
[    0.000000] ACPI: RSDP 000FB6A0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF80000, 0040 (r1 NEC             20090409 MSFT       97)
[    0.000000] ACPI: FACP CFF80200, 0084 (r1 040909 FACP2049 20090409 MSFT       97)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080926]
[    0.000000] ACPI: DSDT CFF805C0, D4E7 (r1  A1256 A1256001        1 INTL 20060113)
[    0.000000] ACPI: FACS CFF98000, 0040
[    0.000000] ACPI: APIC CFF80390, 006C (r1 040909 APIC2049 20090409 MSFT       97)
[    0.000000] ACPI: MCFG CFF80400, 003C (r1 040909 OEMMCFG  20090409 MSFT       97)
[    0.000000] ACPI: SLIC CFF80440, 0176 (r1 NEC             20090409 MSFT       97)
[    0.000000] ACPI: OEMB CFF98040, 0072 (r1 040909 OEMB2049 20090409 MSFT       97)
[    0.000000] ACPI: HPET CFF8F5C0, 0038 (r1 040909 OEMHPET  20090409 MSFT       97)
[    0.000000] ACPI: SSDT CFF8F600, 02B4 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2443MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb25bd]      NEW RAMDISK ==> [0000881000 - 0000fb25bd]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000cff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000] On node 0 totalpages: 851726
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4888 pages used for memmap
[    0.000000]   HighMem zone: 620650 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2f700000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845070
[    0.000000] Kernel command line: root=UUID=43d4f476-58b6-4b04-911f-8c5b6279328b ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2707.675 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 17036480 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3346588k/3407360k available (4126k kernel code, 59376k reserved, 2208k data, 532k init, 2502152k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5415.35 BogoMIPS (lpj=10830700)
[    0.004019] Security Framework initialized
[    0.004024] SELinux:  Disabled at boot.
[    0.004034] AppArmor: AppArmor initialized
[    0.004040] Mount-cache hash table entries: 512
[    0.004126] Initializing cgroup subsys ns
[    0.004129] Initializing cgroup subsys cpuacct
[    0.004131] Initializing cgroup subsys memory
[    0.004134] Initializing cgroup subsys freezer
[    0.004142] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004144] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004146] CPU: Physical Processor ID: 0
[    0.004147] CPU: Processor Core ID: 0
[    0.004150] using C1E aware idle routine
[    0.004156] Checking 'hlt' instruction... OK.
[    0.021507] ACPI: Core revision 20080926
[    0.025828] ACPI: Checking initramfs for custom DSDT
[    0.232373] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.273813] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.276001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5415.25 BogoMIPS (lpj=10830510)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.360370] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.360383] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.364025] Brought up 2 CPUs
[    0.364027] Total of 2 processors activated (10830.60 BogoMIPS).
[    0.364067] CPU0 attaching sched-domain:
[    0.364069]  domain 0: span 0-1 level CPU
[    0.364071]   groups: 0 1
[    0.364075] CPU1 attaching sched-domain:
[    0.364077]  domain 0: span 0-1 level CPU
[    0.364078]   groups: 1 0
[    0.364120] net_namespace: 776 bytes
[    0.364120] Booting paravirtualized kernel on bare hardware
[    0.364233] Time:  7:37:13  Date: 06/06/09
[    0.364233] regulator: core version 0.5
[    0.364233] NET: Registered protocol family 16
[    0.364233] EISA bus registered
[    0.364233] ACPI: bus type pci registered
[    0.364233] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.364233] PCI: Not using MMCONFIG.
[    0.364872] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.364874] PCI: Using configuration type 1 for base access
[    0.364875] PCI: Using configuration type 1 for extended access
[    0.365375] ACPI: EC: Look up EC in DSDT
[    0.403437] ACPI: Interpreter enabled
[    0.403440] ACPI: (supports S0 S1 S3 S4 S5)
[    0.403456] ACPI: Using IOAPIC for interrupt routing
[    0.403511] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.409507] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.409509] PCI: Using MMCONFIG for extended config space
[    0.418431] ACPI: No dock devices found.
[    0.418501] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.418570] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.418572] pci 0000:00:02.0: PME# disabled
[    0.418593] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.418595] pci 0000:00:04.0: PME# disabled
[    0.418620] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.418622] pci 0000:00:09.0: PME# disabled
[    0.418642] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.418644] pci 0000:00:0a.0: PME# disabled
[    0.418689] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.418695] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.418701] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.418707] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.418713] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.418720] pci 0000:00:11.0: reg 24 32bit mmio: [0xf7fffc00-0xf7ffffff]
[    0.418736] pci 0000:00:11.0: set SATA to AHCI mode
[    0.418764] pci 0000:00:12.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffefff]
[    0.418812] pci 0000:00:12.1: reg 10 32bit mmio: [0xf7ffd000-0xf7ffdfff]
[    0.418877] pci 0000:00:12.2: reg 10 32bit mmio: [0xf7fff800-0xf7fff8ff]
[    0.418912] pci 0000:00:12.2: supports D1 D2
[    0.418914] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.418917] pci 0000:00:12.2: PME# disabled
[    0.418945] pci 0000:00:13.0: reg 10 32bit mmio: [0xf7ffc000-0xf7ffcfff]
[    0.418993] pci 0000:00:13.1: reg 10 32bit mmio: [0xf7ffb000-0xf7ffbfff]
[    0.419057] pci 0000:00:13.2: reg 10 32bit mmio: [0xf7fff400-0xf7fff4ff]
[    0.419093] pci 0000:00:13.2: supports D1 D2
[    0.419094] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.419098] pci 0000:00:13.2: PME# disabled
[    0.419196] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.419202] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.419208] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.419214] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.419220] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.419272] pci 0000:00:14.2: reg 10 64bit mmio: [0xf7ff4000-0xf7ff7fff]
[    0.419303] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.419307] pci 0000:00:14.2: PME# disabled
[    0.419396] pci 0000:00:14.5: reg 10 32bit mmio: [0xf7ffa000-0xf7ffafff]
[    0.419516] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.419524] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.419531] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.419536] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.419541] pci 0000:01:00.0: reg 30 32bit mmio: [0xfb380000-0xfb3fffff]
[    0.419594] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.419596] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfb3fffff]
[    0.419599] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.419673] pci 0000:02:00.0: reg 10 64bit mmio: [0xfb800000-0xfbbfffff]
[    0.419685] pci 0000:02:00.0: reg 18 64bit mmio: [0xfb400000-0xfb7fffff]
[    0.419715] pci 0000:02:00.0: supports D1 D2
[    0.419716] pci 0000:02:00.0: PME# supported from D0 D1 D2
[    0.419720] pci 0000:02:00.0: PME# disabled
[    0.419773] pci 0000:00:04.0: bridge 32bit mmio: [0xfb400000-0xfbbfffff]
[    0.419826] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbc00000-0xfbdfffff]
[    0.419884] pci 0000:03:00.0: supports D1 D2
[    0.419885] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.419890] pci 0000:03:00.0: PME# disabled
[    0.419947] pci 0000:00:09.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.419988] pci 0000:04:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.420008] pci 0000:04:00.0: reg 18 64bit mmio: [0xfbfff000-0xfbffffff]
[    0.420024] pci 0000:04:00.0: reg 30 32bit mmio: [0xfbfc0000-0xfbfdffff]
[    0.420033] pci 0000:04:00.0: supports D1 D2
[    0.420035] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.420039] pci 0000:04:00.0: PME# disabled
[    0.420087] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.420094] pci 0000:00:0a.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.420148] pci 0000:00:14.4: transparent bridge
[    0.420168] bus 00 -> node 0
[    0.420173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.420480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.420583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.420689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.420788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.420900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.424469] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.424601] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.424731] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.424859] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.424987] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425120] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425250] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11 12 14 15)
[    0.425379] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.425520] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - AE, should be A9 [20080926]
[    0.425580] ACPI: WMI: Mapper loaded
[    0.425612] SCSI subsystem initialized
[    0.425612] libata version 3.00 loaded.
[    0.425612] usbcore: registered new interface driver usbfs
[    0.425612] usbcore: registered new interface driver hub
[    0.425612] usbcore: registered new device driver usb
[    0.425612] PCI: Using ACPI for IRQ routing
[    0.432007] Bluetooth: Core ver 2.13
[    0.432016] NET: Registered protocol family 31
[    0.432016] Bluetooth: HCI device and connection manager initialized
[    0.432016] Bluetooth: HCI socket layer initialized
[    0.432018] NET: Registered protocol family 8
[    0.432019] NET: Registered protocol family 20
[    0.432026] NetLabel: Initializing
[    0.432027] NetLabel:  domain hash size = 128
[    0.432028] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.432038] NetLabel:  unlabeled traffic allowed by default
[    0.432051] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    0.432055] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.436016] hpet: hpet2 irq 2303 for MSI
[    0.436040] AppArmor: AppArmor Filesystem Enabled
[    0.444005] pnp: PnP ACPI init
[    0.444010] ACPI: bus type pnp registered
[    0.449085] pnp: PnP ACPI: found 15 devices
[    0.449086] ACPI: ACPI bus type pnp unregistered
[    0.449089] PnPBIOS: Disabled by ACPI PNP
[    0.449097] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.449099] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.449104] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[    0.449106] system 00:0b: ioport range 0x40b-0x40b has been reserved
[    0.449108] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
[    0.449110] system 00:0b: ioport range 0xc00-0xc01 has been reserved
[    0.449112] system 00:0b: ioport range 0xc14-0xc14 has been reserved
[    0.449114] system 00:0b: ioport range 0xc50-0xc51 has been reserved
[    0.449115] system 00:0b: ioport range 0xc52-0xc52 has been reserved
[    0.449117] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
[    0.449119] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
[    0.449121] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
[    0.449123] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
[    0.449125] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
[    0.449127] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
[    0.449128] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
[    0.449130] system 00:0b: ioport range 0x800-0x89f has been reserved
[    0.449132] system 00:0b: ioport range 0xb00-0xb0f has been reserved
[    0.449134] system 00:0b: ioport range 0xb20-0xb3f has been reserved
[    0.449136] system 00:0b: ioport range 0x900-0x90f has been reserved
[    0.449138] system 00:0b: ioport range 0x910-0x91f has been reserved
[    0.449140] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
[    0.449142] system 00:0b: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.449145] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.449148] system 00:0c: ioport range 0x230-0x23f has been reserved
[    0.449150] system 00:0c: ioport range 0x290-0x29f has been reserved
[    0.449152] system 00:0c: ioport range 0x300-0x30f has been reserved
[    0.449154] system 00:0c: ioport range 0xa30-0xa3f has been reserved
[    0.449158] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.449162] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.449164] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.449166] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.449168] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.449170] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.483803] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.483806] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.483809] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfb3fffff
[    0.483811] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.483815] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.483816] pci 0000:00:04.0:   IO window: disabled
[    0.483819] pci 0000:00:04.0:   MEM window: 0xfb400000-0xfbbfffff
[    0.483821] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.483824] pci 0000:00:09.0: PCI bridge, secondary bus 0000:03
[    0.483825] pci 0000:00:09.0:   IO window: disabled
[    0.483828] pci 0000:00:09.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.483830] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.483832] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:04
[    0.483834] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.483837] pci 0000:00:0a.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.483839] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.483842] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    0.483843] pci 0000:00:14.4:   IO window: disabled
[    0.483848] pci 0000:00:14.4:   MEM window: disabled
[    0.483851] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.483862] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.483865] pci 0000:00:02.0: setting latency timer to 64
[    0.483869] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.483871] pci 0000:00:04.0: setting latency timer to 64
[    0.483875] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.483878] pci 0000:00:09.0: setting latency timer to 64
[    0.483881] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.483884] pci 0000:00:0a.0: setting latency timer to 64
[    0.483890] bus: 00 index 0 io port: [0x00-0xffff]
[    0.483892] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.483893] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.483895] bus: 01 index 1 mmio: [0xf8000000-0xfb3fffff]
[    0.483897] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.483899] bus: 01 index 3 mmio: [0x0-0x0]
[    0.483901] bus: 02 index 0 mmio: [0x0-0x0]
[    0.483902] bus: 02 index 1 mmio: [0xfb400000-0xfbbfffff]
[    0.483904] bus: 02 index 2 mmio: [0x0-0x0]
[    0.483905] bus: 02 index 3 mmio: [0x0-0x0]
[    0.483906] bus: 03 index 0 mmio: [0x0-0x0]
[    0.483908] bus: 03 index 1 mmio: [0xfbc00000-0xfbdfffff]
[    0.483909] bus: 03 index 2 mmio: [0x0-0x0]
[    0.483911] bus: 03 index 3 mmio: [0x0-0x0]
[    0.483912] bus: 04 index 0 io port: [0xe000-0xefff]
[    0.483914] bus: 04 index 1 mmio: [0xfbf00000-0xfbffffff]
[    0.483915] bus: 04 index 2 mmio: [0x0-0x0]
[    0.483916] bus: 04 index 3 mmio: [0x0-0x0]
[    0.483918] bus: 05 index 0 mmio: [0x0-0x0]
[    0.483919] bus: 05 index 1 mmio: [0x0-0x0]
[    0.483920] bus: 05 index 2 mmio: [0x0-0x0]
[    0.483922] bus: 05 index 3 io port: [0x00-0xffff]
[    0.483923] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.483930] NET: Registered protocol family 2
[    0.496039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.496212] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.496541] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.496724] TCP: Hash tables configured (established 131072 bind 65536)
[    0.496726] TCP reno registered
[    0.500391] Switched to high resolution mode on CPU 1
[    0.504011] Switched to high resolution mode on CPU 0
[    0.504066] NET: Registered protocol family 1
[    0.504152] checking if image is initramfs... it is
[    0.909856] Freeing initrd memory: 7365k freed
[    0.910022] cpufreq: No nForce2 chipset.
[    0.910110] audit: initializing netlink socket (disabled)
[    0.910124] type=2000 audit(1244273832.908:1): initialized
[    0.915632] highmem bounce pool size: 64 pages
[    0.915635] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.916528] VFS: Disk quotas dquot_6.5.1
[    0.916569] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.916966] fuse init (API version 7.10)
[    0.917021] msgmni has been set to 1665
[    0.917166] alg: No test for stdrng (krng)
[    0.917176] io scheduler noop registered
[    0.917178] io scheduler anticipatory registered
[    0.917180] io scheduler deadline registered
[    0.917192] io scheduler cfq registered (default)
[    1.080028] pci 0000:01:00.0: Boot video device
[    1.085511] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.085531] pcieport-driver 0000:00:02.0: found MSI capability
[    1.085547] pcieport-driver 0000:00:02.0: irq 2302 for MSI/MSI-X
[    1.085553] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.085562] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.085590] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.085607] pcieport-driver 0000:00:04.0: found MSI capability
[    1.085619] pcieport-driver 0000:00:04.0: irq 2301 for MSI/MSI-X
[    1.085625] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.085632] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.085659] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.085676] pcieport-driver 0000:00:09.0: found MSI capability
[    1.085688] pcieport-driver 0000:00:09.0: irq 2300 for MSI/MSI-X
[    1.085694] pci_express 0000:00:09.0:pcie00: allocate port service
[    1.085704] pci_express 0000:00:09.0:pcie03: allocate port service
[    1.085731] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.085748] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.085760] pcieport-driver 0000:00:0a.0: irq 2299 for MSI/MSI-X
[    1.085766] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.085773] pci_express 0000:00:0a.0:pcie03: allocate port service
[    1.085808] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.085814] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.085909] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.085911] ACPI: Power Button (FF) [PWRF]
[    1.085947] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.085949] ACPI: Power Button (CM) [PWRB]
[    1.086201] processor ACPI_CPU:00: registered as cooling_device0
[    1.086205] ACPI: Processor [P001] (supports 8 throttling states)
[    1.086241] processor ACPI_CPU:01: registered as cooling_device1
[    1.089386] isapnp: Scanning for PnP cards...
[    1.443301] isapnp: No Plug & Play device found
[    1.452179] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.452280] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.452559] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.453062] brd: module loaded
[    1.453258] loop: module loaded
[    1.453305] Fixed MDIO Bus: probed
[    1.453309] PPP generic driver version 2.4.2
[    1.453349] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.453369] Driver 'sd' needs updating - please use bus_type methods
[    1.453374] Driver 'sr' needs updating - please use bus_type methods
[    1.453399] ahci 0000:00:11.0: version 3.0
[    1.453415] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.453517] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.453520] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.453794] scsi0 : ahci
[    1.453866] scsi1 : ahci
[    1.453911] scsi2 : ahci
[    1.453954] scsi3 : ahci
[    1.454015] ata1: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 22
[    1.454018] ata2: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffd80 irq 22
[    1.454021] ata3: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffe00 irq 22
[    1.454024] ata4: SATA max UDMA/133 abar m1024@0xf7fffc00 port 0xf7fffe80 irq 22
[    2.340011] ata1: softreset failed (device not ready)
[    2.340057] ata1: failed due to HW bug, retry pmp=0
[    2.504523] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.506465] ata1.00: ATAPI: PIONEER DVD-RW  DVR-217D, 1.07, max UDMA/66
[    2.508814] ata1.00: configured for UDMA/66
[    3.008012] ata2: softreset failed (device not ready)
[    3.008056] ata2: failed due to HW bug, retry pmp=0
[    3.172016] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.172490] ata2.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
[    3.172492] ata2.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.173033] ata2.00: configured for UDMA/133
[    3.672007] ata3: softreset failed (device not ready)
[    3.672053] ata3: failed due to HW bug, retry pmp=0
[    3.836016] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.836757] ata3.00: ATA-8: WDC WD6400AACS-00G8B1, 05.04C05, max UDMA/133
[    3.836759] ata3.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.837572] ata3.00: configured for UDMA/133
[    4.172021] ata4: SATA link down (SStatus 0 SControl 300)
[    4.191307] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-217D 1.07 PQ: 0 ANSI: 5
[    4.194245] sr0: scsi3-mmc drive: 94x/94x writer cd/rw xa/form2 cdda tray
[    4.194248] Uniform CD-ROM driver Revision: 3.20
[    4.194312] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.194342] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.194394] scsi 1:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
[    4.194453] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.194463] sd 1:0:0:0: [sda] Write Protect is off
[    4.194465] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194481] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.194520] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.194529] sd 1:0:0:0: [sda] Write Protect is off
[    4.194531] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.194544] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.194548]  sda: sda1
[    4.691777] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.691799] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.691835] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AACS-0 05.0 PQ: 0 ANSI: 5
[    4.691885] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.691895] sd 2:0:0:0: [sdb] Write Protect is off
[    4.691897] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.691912] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.691942] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
[    4.691951] sd 2:0:0:0: [sdb] Write Protect is off
[    4.691953] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.691966] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.691968]  sdb: sdb1 sdb2 < sdb5 >
[    4.730504] sd 2:0:0:0: [sdb] Attached SCSI disk
[    4.730526] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.730712] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.730729] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    4.730791] scsi4 : pata_atiixp
[    4.730839] scsi5 : pata_atiixp
[    4.732033] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.732036] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.063399] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.063412] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.063423] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    5.063460] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    5.063480] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    5.063497] ehci_hcd 0000:00:12.2: debug port 1
[    5.063510] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf7fff800
[    5.072013] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    5.072055] usb usb1: configuration #1 chosen from 1 choice
[    5.072074] hub 1-0:1.0: USB hub found
[    5.072079] hub 1-0:1.0: 6 ports detected
[    5.072156] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.072163] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.072188] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    5.072203] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    5.072219] ehci_hcd 0000:00:13.2: debug port 1
[    5.072230] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf7fff400
[    5.084010] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    5.084058] usb usb2: configuration #1 chosen from 1 choice
[    5.084073] hub 2-0:1.0: USB hub found
[    5.084077] hub 2-0:1.0: 6 ports detected
[    5.084146] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.084157] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.084166] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    5.084196] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    5.084216] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf7ffe000
[    5.144032] usb usb3: configuration #1 chosen from 1 choice
[    5.144051] hub 3-0:1.0: USB hub found
[    5.144060] hub 3-0:1.0: 3 ports detected
[    5.144121] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.144130] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    5.144154] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    5.144167] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf7ffd000
[    5.200027] usb usb4: configuration #1 chosen from 1 choice
[    5.200045] hub 4-0:1.0: USB hub found
[    5.200052] hub 4-0:1.0: 3 ports detected
[    5.200110] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.200119] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.200146] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    5.200163] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf7ffc000
[    5.256035] usb usb5: configuration #1 chosen from 1 choice
[    5.256049] hub 5-0:1.0: USB hub found
[    5.256057] hub 5-0:1.0: 3 ports detected
[    5.256118] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.256126] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.256151] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    5.256164] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf7ffb000
[    5.312030] usb usb6: configuration #1 chosen from 1 choice
[    5.312044] hub 6-0:1.0: USB hub found
[    5.312051] hub 6-0:1.0: 3 ports detected
[    5.312113] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.312122] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.312150] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.312163] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf7ffa000
[    5.368031] usb usb7: configuration #1 chosen from 1 choice
[    5.368047] hub 7-0:1.0: USB hub found
[    5.368055] hub 7-0:1.0: 2 ports detected
[    5.368118] uhci_hcd: USB Universal Host Controller Interface driver
[    5.368166] usbcore: registered new interface driver libusual
[    5.368187] usbcore: registered new interface driver usbserial
[    5.368194] USB Serial support registered for generic
[    5.396014] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    5.529588] usb 2-6: configuration #1 chosen from 1 choice
[    5.529828] hub 2-6:1.0: USB hub found
[    5.530190] hub 2-6:1.0: 4 ports detected
[    5.531615] usbcore: registered new interface driver usbserial_generic
[    5.531617] usbserial: USB Serial Driver core
[    5.531651] PNP: PS/2 Controller [PNP0303:PSKE,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
[    5.531933] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.531937] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.532004] mice: PS/2 mouse device common for all mice
[    5.532088] rtc_cmos 00:04: RTC can wake from S4
[    5.532109] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    5.532132] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    5.532176] device-mapper: uevent: version 1.0.3
[    5.532236] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.532325] device-mapper: multipath: version 1.0.5 loaded
[    5.532327] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.532394] EISA: Probing bus 0 at eisa.0
[    5.532423] Cannot allocate resource for EISA slot 8
[    5.532425] EISA: Detected 0 cards.
[    5.532478] cpuidle: using governor ladder
[    5.532479] cpuidle: using governor menu
[    5.532818] TCP cubic registered
[    5.532888] NET: Registered protocol family 10
[    5.533176] lo: Disabled Privacy Extensions
[    5.533395] NET: Registered protocol family 17
[    5.533405] Bluetooth: L2CAP ver 2.11
[    5.533407] Bluetooth: L2CAP socket layer initialized
[    5.533409] Bluetooth: SCO (Voice Link) ver 0.6
[    5.533410] Bluetooth: SCO socket layer initialized
[    5.533435] Bluetooth: RFCOMM socket layer initialized
[    5.533440] Bluetooth: RFCOMM TTY layer initialized
[    5.533441] Bluetooth: RFCOMM ver 1.10
[    5.533476] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    5.533507] powernow-k8:    0 : pstate 0 (2700 MHz)
[    5.533509] powernow-k8:    1 : pstate 1 (1400 MHz)
[    5.533586] Using IPI No-Shortcut mode
[    5.533630] registered taskstats version 1
[    5.533725]   Magic number: 13:769:621
[    5.533794] rtc_cmos 00:04: setting system clock to 2009-06-06 07:37:18 UTC (1244273838)
[    5.533798] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.533800] EDD information not available.
[    5.534002] Freeing unused kernel memory: 532k freed
[    5.534108] Write protecting the kernel text: 4128k
[    5.534147] Write protecting the kernel read-only data: 1532k
[    5.682006] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.682020] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.682034] r8169 0000:04:00.0: setting latency timer to 64
[    5.682122] r8169 0000:04:00.0: irq 2298 for MSI/MSI-X
[    5.682546] eth0: RTL8168b/8111b at 0xf7c80000, 00:24:8c:db:53:2a, XID 38000000 IRQ 2298
[    5.913285] usb 2-6.1: new low speed USB device using ehci_hcd and address 3
[    5.962458] PM: Starting manual resume from disk
[    5.962460] PM: Resume from partition 8:21
[    5.962462] PM: Checking hibernation image.
[    5.962618] PM: Resume from disk failed.
[    5.968123] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.968125] EXT3-fs: write access will be enabled during recovery.
[    5.984899] usb 2-6.1: device descriptor read/64, error -32
[    6.225166] usb 2-6.1: configuration #1 chosen from 1 choice
[    6.229039] usbcore: registered new interface driver hiddev
[    6.233775] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6.1/2-6.1:1.0/input/input3
[    6.240045] generic-usb 0003:1241:F767.0001: input,hidraw0: USB HID v1.10 Keyboard [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:13.2-6.1/input0
[    6.248640] input: HOLTEK Wireless 2.4GHz TouchPad Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6.1/2-6.1:1.1/input/input4
[    6.253753] generic-usb 0003:1241:F767.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [HOLTEK Wireless 2.4GHz TouchPad Keyboard] on usb-0000:00:13.2-6.1/input1
[    6.253767] usbcore: registered new interface driver usbhid
[    6.253770] usbhid: v2.6:USB HID core driver
[    6.297490] usb 2-6.4: new high speed USB device using ehci_hcd and address 4
[    6.444052] kjournald starting.  Commit interval 5 seconds
[    6.444063] EXT3-fs: sdb1: orphan cleanup on readonly fs
[    6.444068] ext3_orphan_cleanup: deleting unreferenced inode 23150600
[    6.444089] ext3_orphan_cleanup: deleting unreferenced inode 23150599
[    6.444093] ext3_orphan_cleanup: deleting unreferenced inode 23150598
[    6.444096] ext3_orphan_cleanup: deleting unreferenced inode 23150597
[    6.444100] ext3_orphan_cleanup: deleting unreferenced inode 23150596
[    6.444103] EXT3-fs: sdb1: 5 orphan inodes deleted
[    6.444104] EXT3-fs: recovery complete.
[    6.445730] EXT3-fs: mounted filesystem with ordered data mode.
[    7.028325] usb 2-6.4: configuration #1 chosen from 1 choice
[    7.223705] Initializing USB Mass Storage driver...
[    7.223830] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.223894] usbcore: registered new interface driver usb-storage
[    7.223897] USB Mass Storage support registered.
[    7.223948] usb-storage: device found at 4
[    7.223949] usb-storage: waiting for device to settle before scanning
[   11.580672] udev: starting version 141
[   11.784483] Linux agpgart interface v0.103
[   11.786608] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   11.786610] ACPI: Device needs an ACPI driver
[   11.786616] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.789502] parport_pc 00:07: reported by Plug and Play ACPI
[   11.789554] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.800861] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   11.867433] ppdev: user-space parallel port driver
[   12.026194] nvidia: module license 'NVIDIA' taints kernel.
[   12.115937] saa7164 driver loaded
[   12.116019] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.116365] CORE saa7164[0]: dev->lmmio  = 0xf8e80000
[   12.116367] CORE saa7164[0]: dev->lmmio2 = 0xf7f80000
[   12.116369] CORE saa7164[0]: dev->bmmio  = 0xf8e80000
[   12.116370] CORE saa7164[0]: dev->bmmio2 = 0xf7f80000
[   12.116372] CORE saa7164[0]: subsystem: 0070:8880, board: Hauppauge WinTV-HVR2250 [card=3,autodetected]
[   12.116377] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   12.116382] saa7164 0000:02:00.0: setting latency timer to 64
[   12.122243] Linux video capture interface: v2.00
[   12.172866] cx23885 driver version 0.0.2 loaded
[   12.172907] cx23885 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.172993] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   12.284518] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.284526] nvidia 0000:01:00.0: setting latency timer to 64
[   12.284683] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.308529] usb-storage: device scan complete
[   12.315277] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   12.321525] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   12.327774] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   12.334025] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   12.336298] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   12.336374] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   12.339117] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   12.339181] sd 6:0:0:1: Attached scsi generic sg4 type 0
[   12.340104] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   12.340166] sd 6:0:0:2: Attached scsi generic sg5 type 0
[   12.341115] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   12.341177] sd 6:0:0:3: Attached scsi generic sg6 type 0
[   12.362302] tveeprom 1-0050: Hauppauge model 78521, rev C1E9, serial# 4851581
[   12.362306] tveeprom 1-0050: MAC address is 00-0D-FE-4A-07-7D
[   12.362308] tveeprom 1-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   12.362310] tveeprom 1-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   12.362312] tveeprom 1-0050: audio processor is CX23887 (idx 42)
[   12.362314] tveeprom 1-0050: decoder processor is CX23887 (idx 37)
[   12.362315] tveeprom 1-0050: has radio
[   12.362316] cx23885[0]: hauppauge eeprom: model=78521
[   12.384523] saa7164_downloadfirmware() no first image
[   12.384569] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.384572] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   12.455988] cx25840 3-0044: cx25  0-21 found @ 0x88 (cx23885[0])
[   12.460339] cx25840 3-0044: firmware: requesting v4l-cx23885-avcore-01.fw
[   12.631276] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.663226] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.189745] cx25840 3-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   13.293656] tuner 2-0042: chip found @ 0x84 (cx23885[0])
[   13.337014] tda829x 2-0042: could not clearly identify tuner address, defaulting to 60
[   13.372324] tda18271 2-0060: creating new instance
[   13.417409] TDA18271HD/C1 detected @ 2-0060
[   13.592082] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   13.592085] saa7164_downloadfirmware() firmware loaded.
[   13.592086] Firmware file header part 1:
[   13.592089]  .FirmwareSize = 0x0
[   13.592090]  .BSLSize = 0x0
[   13.592091]  .Reserved = 0x3cb57
[   13.592092]  .Version = 0x3
[   13.592093] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   13.592134] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.592135] saa7164_downloadfirmware() BSLSize = 0x0
[   13.592136] saa7164_downloadfirmware() Reserved = 0x0
[   13.592138] saa7164_downloadfirmware() Version = 0x51cc1
[   14.616394] tda829x 2-0042: type set to tda8295+18271
[   15.720500] cx23885[0]/0: registered device video0 [v4l2]
[   16.808561] cx23885[0]: registered device video1 [mpeg]
[   16.808563] cx23885_dvb_register() allocating 1 frontend(s)
[   16.808566] cx23885[0]: cx23885 based dvb card
[   16.897948] MT2131: successfully identified at address 0x61
[   16.899591] DVB: registering new adapter (cx23885[0])
[   16.899594] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   16.899781] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   16.899788] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfbc00000
[   16.899795] cx23885 0000:03:00.0: setting latency timer to 64
[   17.336049] saa7164_downloadimage() Image downloaded, booting...
[   17.336053] saa7164_downloadimage() Image booted successfully.
[   17.336096] starting firmware download(2)
[   19.456010] saa7164_downloadimage() Image downloaded, booting...
[   21.328041] saa7164_downloadimage() Image booted successfully.
[   21.328085] firmware download complete.
[   21.329052] saa7164[0]: i2c bus 0 registered
[   21.329099] saa7164[0]: i2c bus 1 registered
[   21.329141] saa7164[0]: i2c bus 2 registered
[   21.364440] tveeprom 4-0000: Hauppauge model 88041, rev C1F2, serial# 5185686
[   21.364443] tveeprom 4-0000: MAC address is 00-0D-FE-4F-20-96
[   21.364444] tveeprom 4-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   21.364447] tveeprom 4-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   21.364448] tveeprom 4-0000: audio processor is SAA7164 (idx 43)
[   21.364450] tveeprom 4-0000: decoder processor is SAA7164 (idx 40)
[   21.364452] tveeprom 4-0000: has radio
[   21.364453] saa7164[0]: Hauppauge eeprom: model=88041
[   21.708374] tda18271 5-0060: creating new instance
[   21.712861] TDA18271HD/C2 detected @ 5-0060
[   21.964806] DVB: registering new adapter (saa7164)
[   21.964810] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.249805] tda18271 6-0060: creating new instance
[   22.253895] TDA18271HD/C2 detected @ 6-0060
[   22.504742] DVB: registering new adapter (saa7164)
[   22.504745] DVB: registering adapter 2 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   22.605944] lp0: using parport0 (interrupt-driven).
[   22.653952] Adding 9068652k swap on /dev/sdb5.  Priority:-1 extents:1 across:9068652k
[   23.177186] EXT3 FS on sdb1, internal journal
[   24.047009] type=1505 audit(1244273857.010:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2259
[   24.081016] type=1505 audit(1244273857.046:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2263
[   24.081089] type=1505 audit(1244273857.046:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2263
[   24.081118] type=1505 audit(1244273857.046:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2263
[   24.081144] type=1505 audit(1244273857.046:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2263
[   24.177159] type=1505 audit(1244273857.142:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2268
[   24.177285] type=1505 audit(1244273857.142:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2268
[   24.202730] type=1505 audit(1244273857.166:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2272
[   24.221566] type=1505 audit(1244273857.186:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2276
[   30.984818] r8169: eth0: link up
[   30.984823] r8169: eth0: link up
[   33.237931] r8169: eth0: link up
[   34.568873] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.568876] Bluetooth: BNEP filters: protocol multicast
[   34.575114] Bridge firewalling registered
[   35.178580] tda18271: performing RF tracking filter calibration
[   37.849532] tda18271: RF tracking filter calibration complete
[   44.148010] eth0: no IPv6 routers present
[   64.966481] UDF-fs: Partition marked readonly; forcing readonly mount
[   65.024228] UDF-fs INFO UDF: Mounting volume 'SHREK_2_US_4X3', timestamp 2004/06/29 06:16 (1000)
[  650.112940] usb 2-6.4: reset high speed USB device using ehci_hcd and address 4
```

lspci:
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a
    Kernel modules: ati-agp

00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f8000000-fb3fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) [1002:597a]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fb400000-fbbfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E) [1002:597e]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fbc00000-fbdfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [110] Virtual Channel <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390] (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at c000 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=16]
    Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
    Capabilities: [70] SATA HBA <?>
    Kernel driver in use: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f7fff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f7fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: 66MHz, medium devsel
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
    Kernel driver in use: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:837b]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399] (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f7ffa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
    Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control [1022:1204]
    Flags: fast devsel

01:00.0 VGA compatible controller [0300]: nVidia Corporation D9M-20 [GeForce 9400 GT] [10de:0641] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:1571]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fb380000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

02:00.0 Multimedia controller [0480]: Philips Semiconductors Device [1131:7164] (rev 81)
    Subsystem: Hauppauge computer works Inc. Device [0070:8880]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
    Memory at fb400000 (64-bit, non-prefetchable) [size=4M]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
    Capabilities: [50] Express Endpoint, MSI 00
    Capabilities: [74] Power Management version 3
    Capabilities: [7c] Vendor Specific Information <?>
    Capabilities: [100] Vendor Specific Information <?>
    Capabilities: [160] Virtual Channel <?>
    Kernel driver in use: saa7164
    Kernel modules: saa7164

03:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. Device [14f1:8880] (rev 0f)
    Subsystem: Hauppauge computer works Inc. Device [0070:7801]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data <?>
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [200] Virtual Channel <?>
    Kernel driver in use: cx23885
    Kernel modules: cx23885

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8385]
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at e800 [size=256]
    Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at fbfc0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Vital Product Data <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] Express Endpoint, MSI 00
    Capabilities: [84] Vendor Specific Information <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [12c] Virtual Channel <?>
    Capabilities: [148] Device Serial Number 00-e0-4c-68-00-00-00-40
    Capabilities: [154] Power Budgeting <?>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

lsmod
```
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
s5h1411                17668  2 
mt2131                 13444  1 
s5h1409                16772  1 
tda18271               42888  3 
tda8290                21000  1 
tuner                  29960  1 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
cx25840                35444  1 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
cx23885               104084  0 
cx2341x                22020  1 cx23885
videobuf_dma_sg        20484  1 cx23885
v4l2_common            23808  4 tuner,cx25840,cx23885,cx2341x
videodev               44704  4 tuner,cx25840,cx23885,v4l2_common
v4l1_compat            21764  1 videodev
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
videobuf_dvb           15108  1 cx23885
saa7164                67336  1 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videobuf_core          26244  3 cx23885,videobuf_dma_sg,videobuf_dvb
nvidia               7233756  36 
snd_timer              29704  2 snd_pcm,snd_seq
dvb_core               93440  3 cx23885,videobuf_dvb,saa7164
btcx_risc              13064  1 cx23885
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
psmouse                61972  0 
tveeprom               20228  2 cx23885,saa7164
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13316  0 
pcspkr                 10496  0 
parport_pc             40100  1 
i2c_piix4              18448  0 
ati_agp                14988  0 
agpgart                42696  2 nvidia,ati_agp
soundcore              15200  1 snd
parport                42220  3 lp,ppdev,parport_pc
joydev                 18368  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usb_storage            82880  0 
usbhid                 42336  0 
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

### Post by ianhaycox on 2009-06-07
Some things you could try,

If you have another pc/laptop can you ssh to the machine and look about once it's hung. E.g.

```

$ sudo apt-get install openssh-server  # once, on the mythbox to setup ssh
$ ssh user@host

```

Then from the other pc login to the myth pc.

```

$ ssh user@host

```

Try looking at the results from top and any log files. Mythbackend, or system logs.


On linuxtv.org did you try the section about testing your hardware with mplayer for example. Depending on the results it may eliminate mythtv

---

### Post by ktuimala on 2009-06-08
I have already eliminated mythtv. My HVR-1800 dies and locks the system the moment it is initialized. I have tried it with mythtv, xine, vlc, and mplayer. I have also attempted it through cat. All of them cause a complete system lock within 10 seconds of initializing the hardware with no picture and a blank screen. Scanning channels with the card in mythtv is flawless.....

So far I have pulled all other tuner's out of my system and left only the HVR-1800. I have reinstalled all drivers from the v4l repository. I followed steven toth's instructions on the firmware and placed them in my kernel folder under /lib/firmware. Now I get about 5 seconds of greenish or purpleish video before it locks up my whole system after 10 seconds.

I tryed the SSH tip to see if I coudl tell what is wrong, and I can't connect. When this locks the system, it really locks the system. The only thing left at that point is the reset button or pulling the plug!!

Thanks for the tips. Any other ideas?

---

### Post by ianhaycox on 2009-06-09
It does seem odd that the card can scan channels but then locks up on display. Kind of hints to a video problem.

Try different NVidia drivers, turn off desktop effects, or uninstall and use Vesa driver as a test.

Try removing the NVidia card completely and use the onboard card with basic 640x480 res.

I think you are just going to have to pare the system down to a working minimum then add hardware and drivers until you identify then problem.

Good luck.

BTW - If you do fix it report back for others

---

### Post by ktuimala on 2009-06-09
I never would have fathomed my graphics card. I am being whisked off to California tomorrow afternoon and working late tonight, but next week when I return this will be the first thing that I attempt. 

I will let you know either way... I am hoping it works!!

---

### Post by ktuimala on 2009-06-09
There is one thing that I would like to note. I decided to remove my HVR-2250 and my PVR-250 from the box. I managed to get some greenish/purplish video on the HVR-1800 before the card locked up the system.

I don't know if that gives any other clues?

---

### Post by ianhaycox on 2009-06-09
I don't know if it's related to graphics it was just an elimination process.

If you do have a spare Ubuntu box try putting just the Myth Frontend on it and see if it successfully plays TV streamed from the HVR-1800 backend.

---

