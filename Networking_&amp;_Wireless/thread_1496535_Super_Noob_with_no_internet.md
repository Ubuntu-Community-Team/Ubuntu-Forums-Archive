---
title: "Super Noob with no internet"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by dean_the_great on 2010-05-29
Hey everybody, I just installed 10.04 LTS onto an older laptop, and I've got no internet connection at all, neither wired or wireless.

I found some guides online that I think will help with the wireless driver setup, but they all require the internet to work. 

Also, I'd love to give you the outputs of commands, but I can't seem to copy text onto my external hard drive and transfer to this computer. Everytime I try to copy the output to a text file, it doesn't seem to save any of it when I put it back into this machine.

Help? Anyone?

---

### Post by timnic on 2010-05-29
I am not sure how you are trying to copy the output. The easiest way is to pipe it to a file on your remote drive.

for example:

$ lspci > /media/{drive_name}/lspci.log.txt

where {drive_name} is the name of you remote drive (ls /media will show you what it has been mounted as)

This will save the output of the lspci command to a file called lspci.log.txt (the file name is not important) on your remote drive. 

It is easier than messing about with cut and paste.

posting the output of dmesg would be a good place to start.

$ dmesg > /media/{drive_name}/dmesg.txt


Tim

---

### Post by dean_the_great on 2010-05-29
Thanks Tim! Here it is:

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1fef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-CFFFF uncachable
[    0.000000]   D0000-D5FFF write-back
[    0.000000]   D6000-D7FFF uncachable
[    0.000000]   D8000-DBFFF write-protect
[    0.000000]   DC000-DEFFF uncachable
[    0.000000]   DF000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
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
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  modified: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  modified: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  modified: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001fef0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fef0000 page 4k
[    0.000000] kernel direct mapping tables up to 1fef0000 @ 7000-c000
[    0.000000] RAMDISK: 177db000 - 17f731f0
[    0.000000] ACPI: RSDP 000f7df0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 1fef94f0 00034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 1fefee06 00074 (v01 HP     Piranha  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 1fef9524 058E2 (v01     HP     3085 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1fefffc0 00040
[    0.000000] ACPI: MCFG 1fefee7a 0003C (v01 ATI    Piranha  06040000 LOHR 0000005F)
[    0.000000] ACPI: SSDT 1fefeeb6 000F0 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 1fefefa6 0005A (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fef0000
[    0.000000]   low ram: 0 - 1fef0000
[    0.000000]   node 0 low ram: 00000000 - 1fef0000
[    0.000000]   node 0 bootmap 00008000 - 0000bfe0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [00177db000 - 0017f731f0]          RAMDISK ==> [00177db000 - 0017f731f0]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd110]              BRK ==> [00008da000 - 00008dd110]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00f7e20] f7e20
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fef0
[    0.000000]   HighMem  0x0001fef0 -> 0x0001fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fef0
[    0.000000] On node 0 totalpages: 130699
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125714 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x10
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129677
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=22e61910-c11d-4816-8251-f0b62bb2cf93 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2616000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 499412k/523200k available (4673k kernel code, 22988k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe06f0000 - 0xff7fe000   ( 497 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfef0000   ( 510 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 994.769 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 1989.53 BogoMIPS (lpj=3979076)
[    0.004040] Security Framework initialized
[    0.004079] AppArmor: AppArmor initialized
[    0.004093] Mount-cache hash table entries: 512
[    0.004279] Initializing cgroup subsys ns
[    0.004286] Initializing cgroup subsys cpuacct
[    0.004294] Initializing cgroup subsys memory
[    0.004308] Initializing cgroup subsys devices
[    0.004313] Initializing cgroup subsys freezer
[    0.004318] Initializing cgroup subsys net_cls
[    0.004346] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004351] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004358] mce: CPU supports 5 MCE banks
[    0.004381] Performance Events: AMD PMU driver.
[    0.004403] ... version:                0
[    0.004407] ... bit width:              48
[    0.004411] ... generic registers:      4
[    0.004415] ... value mask:             0000ffffffffffff
[    0.004419] ... max period:             00007fffffffffff
[    0.004424] ... fixed-purpose events:   0
[    0.004427] ... event mask:             000000000000000f
[    0.004434] Checking 'hlt' instruction... OK.
[    0.021224] SMP alternatives: switching to UP code
[    0.032894] Freeing SMP alternatives: 19k freed
[    0.032925] ACPI: Core revision 20090903
[    0.044015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044024] ftrace: allocating 21771 entries in 43 pages
[    0.052149] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052382]   alloc irq_desc for 21 on node 0
[    0.052386]   alloc kstat_irqs on node 0
[    0.052533] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.095035] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 00
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (1989.53 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time:  8:48:47  Date: 05/29/10
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.096001] PCI: MCFG area at e0000000 reserved in E820
[    0.096001] PCI: Using MMCONFIG for extended config space
[    0.096001] PCI: Using configuration type 1 for base access
[    0.096001] bio: create slab <bio-0> at 0
[    0.096354] ACPI: EC: Look up EC in DSDT
[    0.100395] ACPI: Interpreter enabled
[    0.100413] ACPI: (supports S0 S3 S4 S5)
[    0.100448] ACPI: Using IOAPIC for interrupt routing
[    0.164931] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
[    0.165180] ACPI: No dock devices found.
[    0.168469] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.168645] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.168652] pci 0000:00:04.0: PME# disabled
[    0.168734] pci 0000:00:13.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.168857] pci 0000:00:13.1: reg 10 32bit mmio: [0xb0001000-0xb0001fff]
[    0.168989] pci 0000:00:13.2: reg 10 32bit mmio: [0xb0002000-0xb0002fff]
[    0.169068] pci 0000:00:13.2: supports D1 D2
[    0.169074] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.169082] pci 0000:00:13.2: PME# disabled
[    0.169149] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.169163] pci 0000:00:14.0: reg 14 32bit mmio: [0xb0003000-0xb00033ff]
[    0.169205] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.169282] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.169295] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.169308] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.169321] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.169335] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.169554] pci 0000:00:14.5: reg 10 32bit mmio: [0xb0003400-0xb00034ff]
[    0.169674] pci 0000:00:14.6: reg 10 32bit mmio: [0xb0003800-0xb00038ff]
[    0.169908] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.169918] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.169927] pci 0000:01:05.0: reg 18 32bit mmio: [0xb0100000-0xb010ffff]
[    0.169943] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.169957] pci 0000:01:05.0: supports D1 D2
[    0.169982] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.169989] pci 0000:00:01.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.169998] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.172065] pci 0000:00:04.0: bridge io port: [0x00-0xfff]
[    0.172072] pci 0000:00:04.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.172141] pci 0000:03:00.0: reg 10 32bit mmio: [0xb0208000-0xb02087ff]
[    0.172157] pci 0000:03:00.0: reg 14 32bit mmio: [0xb0200000-0xb0203fff]
[    0.172239] pci 0000:03:00.0: supports D1 D2
[    0.172244] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.172254] pci 0000:03:00.0: PME# disabled
[    0.172302] pci 0000:03:02.0: reg 10 32bit mmio: [0xb0204000-0xb0205fff]
[    0.172426] pci 0000:03:04.0: reg 10 32bit mmio: [0xb0209000-0xb0209fff]
[    0.172465] pci 0000:03:04.0: supports D1 D2
[    0.172470] pci 0000:03:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.172480] pci 0000:03:04.0: PME# disabled
[    0.172550] pci 0000:03:04.3: reg 10 32bit mmio: [0xb0206000-0xb0207fff]
[    0.172638] pci 0000:03:04.3: supports D1 D2
[    0.172644] pci 0000:03:04.3: PME# supported from D0 D1 D2 D3hot
[    0.172653] pci 0000:03:04.3: PME# disabled
[    0.172718] pci 0000:03:04.4: reg 10 32bit mmio: [0xb020a000-0xb020a0ff]
[    0.172734] pci 0000:03:04.4: reg 14 32bit mmio: [0xb0208c00-0xb0208cff]
[    0.172749] pci 0000:03:04.4: reg 18 32bit mmio: [0xb0208800-0xb02088ff]
[    0.172820] pci 0000:03:04.4: supports D1 D2
[    0.172825] pci 0000:03:04.4: PME# supported from D0 D1 D2 D3hot
[    0.172835] pci 0000:03:04.4: PME# disabled
[    0.172911] pci 0000:03:06.0: reg 10 io port: [0xa000-0xa0ff]
[    0.176007] pci 0000:03:06.0: reg 14 32bit mmio: [0xb020a400-0xb020a4ff]
[    0.176086] pci 0000:03:06.0: supports D1 D2
[    0.176092] pci 0000:03:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.176102] pci 0000:03:06.0: PME# disabled
[    0.176172] pci 0000:00:14.4: transparent bridge
[    0.176184] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.176194] pci 0000:00:14.4: bridge 32bit mmio: [0xb0200000-0xb02fffff]
[    0.176246] pci_bus 0000:00: on NUMA node 0
[    0.176254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.176448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.176575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.176761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.181400] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.181603] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.181803] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.182002] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.182201] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.182401] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.182600] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.182799] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.182997] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.183009] vgaarb: loaded
[    0.183226] SCSI subsystem initialized
[    0.183336] libata version 3.00 loaded.
[    0.183460] usbcore: registered new interface driver usbfs
[    0.183484] usbcore: registered new interface driver hub
[    0.183529] usbcore: registered new device driver usb
[    0.183797] ACPI: WMI: Mapper loaded
[    0.183801] PCI: Using ACPI for IRQ routing
[    0.183812] pci 0000:00:04.0: BAR 13: can't allocate resource
[    0.183818] pci 0000:00:04.0: BAR 14: can't allocate resource
[    0.184102] NetLabel: Initializing
[    0.184106] NetLabel:  domain hash size = 128
[    0.184110] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.184135] NetLabel:  unlabeled traffic allowed by default
[    0.184187] Switching to clocksource tsc
[    0.187591] AppArmor: AppArmor Filesystem Enabled
[    0.187624] pnp: PnP ACPI init
[    0.187654] ACPI: bus type pnp registered
[    0.190038] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.236981] pnp: PnP ACPI: found 10 devices
[    0.236985] ACPI: ACPI bus type pnp unregistered
[    0.236991] PnPBIOS: Disabled by ACPI PNP
[    0.237014] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.237021] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.237028] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.237045] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.237052] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.237058] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.237064] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.237071] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.237077] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.237083] system 00:08: ioport range 0x870-0x87f has been reserved
[    0.237090] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.237096] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.237102] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.237109] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.237115] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.237121] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.237128] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.237134] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.237141] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.237147] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.237154] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.237166] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.237173] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.237179] system 00:09: iomem range 0xe0000000-0xe03fffff has been reserved
[    0.272067] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.272073] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.272080] pci 0000:00:01.0:   MEM window: 0xb0100000-0xb01fffff
[    0.272086] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.272094] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.272098] pci 0000:00:04.0:   IO window: disabled
[    0.272103] pci 0000:00:04.0:   MEM window: disabled
[    0.272108] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.272121] pci 0000:03:04.0: CardBus bridge, secondary bus 0000:04
[    0.272126] pci 0000:03:04.0:   IO window: 0x00a400-0x00a4ff
[    0.272135] pci 0000:03:04.0:   IO window: 0x00a800-0x00a8ff
[    0.272144] pci 0000:03:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.272153] pci 0000:03:04.0:   MEM window: 0x24000000-0x27ffffff
[    0.272162] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.272169] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.272179] pci 0000:00:14.4:   MEM window: 0xb0200000-0xb02fffff
[    0.272187] pci 0000:00:14.4:   PREFETCH window: 0x20000000-0x23ffffff
[    0.272212] pci 0000:00:04.0: setting latency timer to 64
[    0.272236]   alloc irq_desc for 20 on node -1
[    0.272241]   alloc kstat_irqs on node -1
[    0.272250] pci 0000:03:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.272263] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.272269] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.272275] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.272280] pci_bus 0000:01: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.272286] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.272292] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]
[    0.272297] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.272303] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.272308] pci_bus 0000:03: resource 1 mem: [0xb0200000-0xb02fffff]
[    0.272314] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.272319] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.272325] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.272330] pci_bus 0000:04: resource 0 io:  [0xa400-0xa4ff]
[    0.272336] pci_bus 0000:04: resource 1 io:  [0xa800-0xa8ff]
[    0.272341] pci_bus 0000:04: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.272347] pci_bus 0000:04: resource 3 mem: [0x24000000-0x27ffffff]
[    0.272414] NET: Registered protocol family 2
[    0.272584] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.273115] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.273284] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.273441] TCP: Hash tables configured (established 16384 bind 16384)
[    0.273448] TCP reno registered
[    0.273563] NET: Registered protocol family 1
[    0.273586] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.273596] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.273682] pci 0000:01:05.0: Boot video device
[    0.273999] cpufreq-nforce2: No nForce2 chipset.
[    0.274046] Scanning for low memory corruption every 60 seconds
[    0.274243] audit: initializing netlink socket (disabled)
[    0.274266] type=2000 audit(1275122926.271:1): initialized
[    0.294574] Trying to unpack rootfs image as initramfs...
[    0.316296] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.324498] VFS: Disk quotas dquot_6.5.2
[    0.324638] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.325779] fuse init (API version 7.13)
[    0.325941] msgmni has been set to 976
[    0.326303] alg: No test for stdrng (krng)
[    0.326411] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.326419] io scheduler noop registered
[    0.326423] io scheduler anticipatory registered
[    0.326428] io scheduler deadline registered
[    0.326503] io scheduler cfq registered (default)
[    0.326740] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.326783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.328929] ACPI: AC Adapter [ACAD] (on-line)
[    0.329040] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.329117] ACPI: Lid Switch [LID]
[    0.329201] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.329207] ACPI: Power Button [PWRB]
[    0.329312] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.329317] ACPI: Power Button [PWRF]
[    0.329628] processor LNXCPU:00: registered as cooling_device0
[    0.408710] ACPI: Invalid active0 threshold
[    0.410821] thermal LNXTHERM:01: registered as thermal_zone0
[    0.410838] ACPI: Thermal Zone [THRM] (47 C)
[    0.413707] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.414246]   alloc irq_desc for 17 on node -1
[    0.414252]   alloc kstat_irqs on node -1
[    0.414266] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.414279] serial 0000:00:14.6: PCI INT B disabled
[    0.420396] isapnp: Scanning for PnP cards...
[    0.426455] brd: module loaded
[    0.427463] loop: module loaded
[    0.427670] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.427958]   alloc irq_desc for 16 on node -1
[    0.427963]   alloc kstat_irqs on node -1
[    0.427975] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.428047] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.428657] Fixed MDIO Bus: probed
[    0.428725] PPP generic driver version 2.4.2
[    0.428793] tun: Universal TUN/TAP device driver, 1.6
[    0.428798] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.428937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.428964]   alloc irq_desc for 19 on node -1
[    0.428968]   alloc kstat_irqs on node -1
[    0.428977] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.429008] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.429067] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.429156] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0002000
[    0.476246] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.476434] usb usb1: configuration #1 chosen from 1 choice
[    0.476490] hub 1-0:1.0: USB hub found
[    0.476509] hub 1-0:1.0: 8 ports detected
[    0.476637] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.476663] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.476686] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.476754] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.476787] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0000000
[    0.572609] usb usb2: configuration #1 chosen from 1 choice
[    0.572669] hub 2-0:1.0: USB hub found
[    0.572692] hub 2-0:1.0: 4 ports detected
[    0.572805] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.572836] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.572905] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.572944] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0001000
[    0.662856] usb usb3: configuration #1 chosen from 1 choice
[    0.662922] hub 3-0:1.0: USB hub found
[    0.662946] hub 3-0:1.0: 4 ports detected
[    0.663060] uhci_hcd: USB Universal Host Controller Interface driver
[    0.663214] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.683917] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.683936] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.684234] mice: PS/2 mouse device common for all mice
[    0.684502] rtc_cmos 00:04: RTC can wake from S4
[    0.684580] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.684617] rtc0: alarms up to one month, 114 bytes nvram
[    0.684832] device-mapper: uevent: version 1.0.3
[    0.685073] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.685929] device-mapper: multipath: version 1.1.0 loaded
[    0.685934] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.686906] EISA: Probing bus 0 at eisa.0
[    0.686918] Cannot allocate resource for EISA slot 1
[    0.686956] Cannot allocate resource for EISA slot 8
[    0.686960] EISA: Detected 0 cards.
[    0.689456] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.689569] cpuidle: using governor ladder
[    0.689574] cpuidle: using governor menu
[    0.690411] TCP cubic registered
[    0.690704] NET: Registered protocol family 10
[    0.691533] lo: Disabled Privacy Extensions
[    0.692169] NET: Registered protocol family 17
[    0.692222] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[    0.692301] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2
[    0.692306] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6
[    0.692311] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    0.692316] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x10
[    0.692364] Marking TSC unstable due to cpufreq changes
[    0.727118] Using IPI No-Shortcut mode
[    0.727255] PM: Resume from disk failed.
[    0.727275] registered taskstats version 1
[    0.727635]   Magic number: 10:806:827
[    0.727760] rtc_cmos 00:04: setting system clock to 2010-05-29 08:48:47 UTC (1275122927)
[    0.727763] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.727765] EDD information not available.
[    1.012572] ACPI: Battery Slot [BAT1] (battery present)
[    1.257921] Freeing initrd memory: 7776k freed
[    1.379163] Switching to clocksource acpi_pm
[    1.423954] isapnp: No Plug & Play device found
[    1.423970] Freeing unused kernel memory: 656k freed
[    1.424831] Write protecting the kernel text: 4676k
[    1.424863] Write protecting the kernel read-only data: 1840k
[    1.443581] udev: starting version 151
[    1.644176] scsi0 : pata_atiixp
[    1.649471] scsi1 : pata_atiixp
[    1.650598] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.650601] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.663130] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.720072] ssb: Sonics Silicon Backplane found on PCI device 0000:03:02.0
[    1.812586] ata1.00: ATA-6: ST9100822A, 3.02, max UDMA/100
[    1.812590] ata1.00: 195371568 sectors, multi 16: LBA48 
[    1.828531] ata1.00: configured for UDMA/100
[    1.828662] scsi 0:0:0:0: Direct-Access     ATA      ST9100822A       3.02 PQ: 0 ANSI: 5
[    1.828826] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.829165] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    1.829209] sd 0:0:0:0: [sda] Write Protect is off
[    1.829213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.829235] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.829365]  sda: sda1 sda2 < sda5 >
[    1.872181] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.008676] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L532L, HP12, max MWDMA2
[    2.040638] ata2.00: configured for MWDMA2
[    2.048190] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L532L HP12 PQ: 0 ANSI: 5
[    2.057836] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.057839] Uniform CD-ROM driver Revision: 3.20
[    2.057934] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.057990] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.066453] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.066492] 8139cp 0000:03:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.069514] ohci1394 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.072161] 8139too Fast Ethernet driver 0.9.28
[    2.124087] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.124331]   alloc irq_desc for 22 on node -1
[    2.124334]   alloc kstat_irqs on node -1
[    2.124343] 8139too 0000:03:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.125844] eth0: RealTek RTL8139 at 0xa000, 00:0f:b0:72:e2:a7, IRQ 22
[    2.540030] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.396158] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[573f0200a2224079]
[   16.535606] udev: starting version 151
[   16.596193] lp: driver loaded but no devices found
[   16.637396] Adding 1486840k swap on /dev/sda5.  Priority:-1 extents:1 across:1486840k 
[   16.869769] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.933826] sdhci: Secure Digital Host Controller Interface driver
[   16.933830] sdhci: Copyright(c) Pierre Ossman
[   16.935189] sdhci-pci 0000:03:04.4: SDHCI controller found [104c:8034] (rev 0)
[   16.935214]   alloc irq_desc for 23 on node -1
[   16.935217]   alloc kstat_irqs on node -1
[   16.935226] sdhci-pci 0000:03:04.4: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   16.935311] Registered led device: mmc0::
[   16.935365] mmc0: SDHCI controller on PCI [0000:03:04.4] using PIO
[   16.940495] Registered led device: mmc1::
[   16.940522] mmc1: SDHCI controller on PCI [0000:03:04.4] using PIO
[   16.940558] Registered led device: mmc2::
[   16.940583] mmc2: SDHCI controller on PCI [0000:03:04.4] using PIO
[   16.940734] Linux agpgart interface v0.103
[   16.964189] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   16.967960] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input5
[   16.982311] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.104458] cfg80211: Calling CRDA to update world regulatory domain
[   17.162482] [drm] Initialized drm 1.1.0 20060810
[   17.180036] tifm_7xx1 0000:03:04.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   17.180562] yenta_cardbus 0000:03:04.0: CardBus bridge found [103c:3085]
[   17.180586] yenta_cardbus 0000:03:04.0: Enabling burst memory read transactions
[   17.180594] yenta_cardbus 0000:03:04.0: Using INTVAL to route CSC interrupts to PCI
[   17.180597] yenta_cardbus 0000:03:04.0: Routing CardBus interrupts to ISA
[   17.180604] yenta_cardbus 0000:03:04.0: TI: mfunc 0x00aa1b22, devctl 0x64
[   17.188858] type=1505 audit(1275122943.959:2):  operation="profile_load" pid=545 name="/sbin/dhclient3"
[   17.189136] type=1505 audit(1275122943.959:3):  operation="profile_load" pid=545 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.189287] type=1505 audit(1275122943.959:4):  operation="profile_load" pid=545 name="/usr/lib/connman/scripts/dhclient-script"
[   17.190825] cfg80211: World regulatory domain updated:
[   17.190829] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.190832] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.190835] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.190838] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.190840] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.190843] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.301123] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   17.368663] [drm] radeon defaulting to kernel modesetting.
[   17.368670] [drm] radeon kernel modesetting enabled.
[   17.368764] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.368775] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.376496] [drm] radeon: Initializing kernel modesetting.
[   17.381587] [drm] register mmio base: 0xB0100000
[   17.381590] [drm] register mmio size: 65536
[   17.381936] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   17.381950] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   17.381994] [drm] Generation 2 PCI interface, using max accessible memory
[   17.381996] [drm] radeon: VRAM 128M
[   17.381998] [drm] radeon: VRAM from 0x20000000 to 0x27FFFFFF
[   17.382000] [drm] radeon: GTT 32M
[   17.382002] [drm] radeon: GTT from 0x28000000 to 0x29FFFFFF
[   17.382037] [drm] radeon: irq initialized.
[   17.382205] [drm] Detected VRAM RAM=128M, BAR=256M
[   17.382211] [drm] RAM width 128bits DDR
[   17.383863] [TTM] Zone  kernel: Available graphics memory: 254130 kiB.
[   17.383886] [drm] radeon: 128M of VRAM memory ready
[   17.383889] [drm] radeon: 32M of GTT memory ready.
[   17.383904] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   17.384476] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   17.384489] [drm] radeon: cp idle (0x10000C03)
[   17.384617] [drm] Loading R300 Microcode
[   17.384985] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   17.389893] [drm] radeon: ring at 0x0000000028000000
[   17.389916] [drm] ring test succeeded in 1 usecs
[   17.390034] [drm] radeon: ib pool ready.
[   17.390106] [drm] ib test succeeded in 0 usecs
[   17.390148] [drm] Default TV standard: NTSC
[   17.390149] [drm] 14.318180000 MHz TV ref clk
[   17.390225] [drm] Panel ID String: SEC                     
[   17.390228] [drm] Panel Size 1280x800
[   17.390271] [drm] Default TV standard: NTSC
[   17.390272] [drm] 14.318180000 MHz TV ref clk
[   17.390297] [drm] Radeon Display Connectors
[   17.390298] [drm] Connector 0:
[   17.390300] [drm]   VGA
[   17.390302] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   17.390304] [drm]   Encoders:
[   17.390306] [drm]     CRT1: INTERNAL_DAC2
[   17.390307] [drm] Connector 1:
[   17.390309] [drm]   LVDS
[   17.390311] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   17.390312] [drm]   Encoders:
[   17.390314] [drm]     LCD1: INTERNAL_LVDS
[   17.390315] [drm] Connector 2:
[   17.390317] [drm]   S-video
[   17.390318] [drm]   Encoders:
[   17.390319] [drm]     TV1: INTERNAL_DAC2
[   17.412928] yenta_cardbus 0000:03:04.0: ISA IRQ mask 0x0ef8, PCI irq 20
[   17.412934] yenta_cardbus 0000:03:04.0: Socket status: 30000006
[   17.412938] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   17.412948] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   17.412952] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   17.413212] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   17.413216] yenta_cardbus 0000:03:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   17.494564] phy0: Selected rate control algorithm 'minstrel'
[   17.495268] Registered led device: b43-phy0::radio
[   17.495348] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   17.553740] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
[   17.588396] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   17.643685] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.691189] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.695523] type=1505 audit(1275122944.463:5):  operation="profile_load" pid=712 name="/usr/share/gdm/guest-session/Xsession"
[   17.726759] type=1505 audit(1275122944.495:6):  operation="profile_replace" pid=715 name="/sbin/dhclient3"
[   17.727040] type=1505 audit(1275122944.495:7):  operation="profile_replace" pid=715 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.727199] type=1505 audit(1275122944.495:8):  operation="profile_replace" pid=715 name="/usr/lib/connman/scripts/dhclient-script"
[   17.741700] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.743913] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.745201] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.745957] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.746795] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.757206] type=1505 audit(1275122944.527:9):  operation="profile_load" pid=722 name="/usr/bin/evince"
[   17.789468] type=1505 audit(1275122944.559:10):  operation="profile_load" pid=722 name="/usr/bin/evince-previewer"
[   17.791808] type=1505 audit(1275122944.559:11):  operation="profile_load" pid=722 name="/usr/bin/evince-thumbnailer"
[   17.800102] MC'97 0 converters and GPIO not ready (0x1)
[   17.912920] [drm] fb mappable at 0xC0040000
[   17.912924] [drm] vram apper at 0xC0000000
[   17.912926] [drm] size 4096000
[   17.912928] [drm] fb depth is 24
[   17.912929] [drm]    pitch is 5120
[   17.915828] fb0: radeondrmfb frame buffer device
[   17.915832] registered panic notifier
[   17.915840] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   17.923112] vga16fb: initializing
[   17.923119] vga16fb: mapped to 0xc00a0000
[   17.923126] vga16fb: not registering due to another framebuffer present
[   17.936107] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   17.954198] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   17.998656] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.998660] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   17.998663] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.001695] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[   18.049032] Console: switching to colour frame buffer device 160x50
[   18.152104] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.160272] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   18.170529] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   18.170599] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   18.170656] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.427189] ppdev: user-space parallel port driver
[   28.720021] eth0: no IPv6 routers present
[   93.141537] eth0: link down
[  232.244704] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[  288.310399] eth0: link down
[  441.046427] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 1306.744342] eth0: link down
[ 2101.576935] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 2512.923062] eth0: link down
[ 3393.432047] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 3393.569775] usb 1-3: configuration #1 chosen from 1 choice
[ 3393.643613] Initializing USB Mass Storage driver...
[ 3393.643806] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3393.644486] usbcore: registered new interface driver usb-storage
[ 3393.644493] USB Mass Storage support registered.
[ 3393.653320] usb-storage: device found at 2
[ 3393.653326] usb-storage: waiting for device to settle before scanning
[ 3398.652336] usb-storage: device scan complete
[ 3400.702297] scsi 2:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[ 3400.706239] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3400.708765] sd 2:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 3400.709375] sd 2:0:0:0: [sdb] Write Protect is off
[ 3400.709382] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3400.709387] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3400.710995] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3400.711003]  sdb: sdb1
[ 3400.739513] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3400.739524] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 3582.274722] usb 1-3: USB disconnect, address 2
[ 3632.388051] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 3632.524898] usb 1-3: configuration #1 chosen from 1 choice
[ 3632.526419] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3632.526723] usb-storage: device found at 3
[ 3632.526727] usb-storage: waiting for device to settle before scanning
[ 3637.524370] usb-storage: device scan complete
[ 3637.525088] scsi 3:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[ 3637.529365] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3637.542469] sd 3:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 3637.543071] sd 3:0:0:0: [sdb] Write Protect is off
[ 3637.543078] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3637.543084] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3637.545449] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3637.545458]  sdb: sdb1
[ 3637.557956] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3637.557968] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3714.223216] usb 1-3: USB disconnect, address 3
[ 3748.960052] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 3749.096953] usb 1-3: configuration #1 chosen from 1 choice
[ 3749.099779] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3749.116378] usb-storage: device found at 4
[ 3749.116383] usb-storage: waiting for device to settle before scanning
[ 3754.116306] usb-storage: device scan complete
[ 3754.117144] scsi 4:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[ 3754.121478] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3754.134400] sd 4:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 3754.135003] sd 4:0:0:0: [sdb] Write Protect is off
[ 3754.135010] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3754.135015] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3754.136751] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3754.136759]  sdb: sdb1
[ 3754.156063] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3754.156075] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3900.499716] usb 1-3: USB disconnect, address 4
[ 3974.764052] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 3974.900912] usb 1-3: configuration #1 chosen from 1 choice
[ 3974.902446] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3974.902743] usb-storage: device found at 5
[ 3974.902747] usb-storage: waiting for device to settle before scanning
[ 3979.900381] usb-storage: device scan complete
[ 3979.901226] scsi 5:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[ 3979.906151] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3979.907825] sd 5:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 3979.908417] sd 5:0:0:0: [sdb] Write Protect is off
[ 3979.908424] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3979.908429] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3979.910066] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3979.910073]  sdb: sdb1
[ 3979.925823] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3979.925833] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 7041.282462] usb 1-3: USB disconnect, address 5
[12785.038211] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[12830.596046] usb 1-3: new high speed USB device using ehci_hcd and address 6
[12830.732904] usb 1-3: configuration #1 chosen from 1 choice
[12830.735827] scsi6 : SCSI emulation for USB Mass Storage devices
[12830.752556] usb-storage: device found at 6
[12830.752562] usb-storage: waiting for device to settle before scanning
[12835.752374] usb-storage: device scan complete
[12835.753224] scsi 6:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[12835.757563] sd 6:0:0:0: Attached scsi generic sg2 type 0
[12835.761072] sd 6:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[12835.761682] sd 6:0:0:0: [sdb] Write Protect is off
[12835.761689] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[12835.761695] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[12835.763059] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[12835.763066]  sdb: sdb1
[12835.779694] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[12835.779704] sd 6:0:0:0: [sdb] Attached SCSI disk
[12851.765151] usb 1-3: USB disconnect, address 6
[12881.007615] eth0: link down
[12929.708046] usb 1-3: new high speed USB device using ehci_hcd and address 7
[12929.845028] usb 1-3: configuration #1 chosen from 1 choice
[12929.847826] scsi7 : SCSI emulation for USB Mass Storage devices
[12929.864501] usb-storage: device found at 7
[12929.864507] usb-storage: waiting for device to settle before scanning
[12934.864343] usb-storage: device scan complete
[12934.865193] scsi 7:0:0:0: Direct-Access     ST332062 0A               3.AA PQ: 0 ANSI: 2
[12934.869467] sd 7:0:0:0: Attached scsi generic sg2 type 0
[12934.882435] sd 7:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[12934.883040] sd 7:0:0:0: [sdb] Write Protect is off
[12934.883047] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[12934.883052] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12934.885039] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12934.885047]  sdb: sdb1
[12934.896418] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[12934.896430] sd 7:0:0:0: [sdb] Attached SCSI disk
[12938.201500] eth0: link up, 10Mbps, half-duplex, lpa 0x0000


Any ideas?

---

### Post by dean_the_great on 2010-05-29
I've been trying different guides on installing my wireless firmware, which is for my Broadcom BCM4318, but I've had no success there either.

---

### Post by timnic on 2010-05-29
Looking at the output, it would appear that the network interface is working, albeit at on 10Mhz, but that is fast enough for most internet. 

Try the following...

right click on the network icon in the tool tray
select Edit Connections...
select the Wired Tab
Click on Eth0 and then click the Edit button
Click on IPv6 Settings Tab
Set Method to Ignore
Click apply

Does that fix it?

if not, could you post the output of ifconfig


As for the wireless, again, the driver would appear to have loaded...
[ 17.495348] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]

But I do not know if that is the correct firmware! - The only way I have ever got a broadcom wireless interface to work on a laptop is by using the ndiswrapper which basically provides a wrapper for the vendors Windows driver. If you have not done so already, you could try hitting Google with ***ndiswrapper***. There are plenty of how-to's out there for that - It is not my area of expertise.


Regards


Tim

---

### Post by dean_the_great on 2010-05-29
Thanks! I've installed the drivers with ndiswrapper successfully, and checked the Pv6 setting, but still no internet, wired or otherwise.

Here is ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:0f:b0:72:e2:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26568 (26.5 KB)  TX bytes:26568 (26.5 KB)



Here is iwconfig:
> wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
        

Any ideas?

---

