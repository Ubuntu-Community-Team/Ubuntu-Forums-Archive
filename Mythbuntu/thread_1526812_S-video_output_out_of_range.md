---
title: "S-video output out of range"
date: 2010-07-08
forum: Mythbuntu
---

### Post by Gorf on 2010-07-08
Greetings all, after much poking and prodding I found that my past issues had a lot to do with my video card apparently no longer being supported by Ubuntu.  So I replaced the video card and I got the installer to run normally and the system fully installed.  However now I am a little stuck.  All through the install I was working on a monitor that was attached to the VGA output.  From the installer I changed the setting to have tv-out on the video card via the S-Video output on the card.  When the install completes and reboots the system starts up, I see the Mythbuntu spash screen (all on the monitor at this point), and then what appears to be the switch-over to the S-video output and the monitor goes blank.  There is a momentary flicker on my TV and then the tv screen is blank and stays that way.  The system clearly boots up as I have SSH access.  If I push the power button on the front of the system, it initiates a shutdown on the myth box and for just a moment I can see the Mythbuntu shutdown splash screen on my TV but it is confused... like an over driven input signal or something.  

At any rate, anyone have any suggestions for me to try out?

System dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffdf000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
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
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  modified: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]  modified: 000000007ffdf000 - 0000000080000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37856000 - 37fef888
[    0.000000] Allocated new RAMDISK: 008de000 - 01077888
[    0.000000] Move RAMDISK from 0000000037856000 - 0000000037fef887 to 008de000 - 01077887
[    0.000000] ACPI: RSDP 000fa910 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffd0000 00030 (v01 A M I  OEMRSDT  02000410 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffd0200 00081 (v02 A M I  OEMFACP  02000410 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffd03f0 036C7 (v01  A0029 A0029003 00000003 INTL 02002026)
[    0.000000] ACPI: FACS 7ffdf000 00040
[    0.000000] ACPI: APIC 7ffd0390 0005E (v01 A M I  OEMAPIC  02000410 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffdf040 00041 (v01 A M I  OEMBIOS  02000410 MSFT 00000097)
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
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd1c4]              BRK ==> [00008da000 - 00008dd1c4]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 0001077888]      NEW RAMDISK ==> [00008de000 - 0001077888]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffd0
[    0.000000] On node 0 totalpages: 524127
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1079200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294594 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520031
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=aafc5131-94c8-4949-96d4-44a22a581dee ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffd0)
[    0.000000] Memory: 2052120k/2096960k available (4673k kernel code, 43380k reserved, 2122k data, 656k init, 1187656k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2191.308 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4382.61 BogoMIPS (lpj=8765232)
[    0.004030] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004073] Mount-cache hash table entries: 512
[    0.004237] Initializing cgroup subsys ns
[    0.004242] Initializing cgroup subsys cpuacct
[    0.004247] Initializing cgroup subsys memory
[    0.004259] Initializing cgroup subsys devices
[    0.004262] Initializing cgroup subsys freezer
[    0.004265] Initializing cgroup subsys net_cls
[    0.004289] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004292] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004297] mce: CPU supports 4 MCE banks
[    0.004317] Performance Events: AMD PMU driver.
[    0.004325] ... version:                0
[    0.004327] ... bit width:              48
[    0.004329] ... generic registers:      4
[    0.004331] ... value mask:             0000ffffffffffff
[    0.004333] ... max period:             00007fffffffffff
[    0.004335] ... fixed-purpose events:   0
[    0.004337] ... event mask:             000000000000000f
[    0.004342] Checking 'hlt' instruction... OK.
[    0.020552] SMP alternatives: switching to UP code
[    0.026176] Freeing SMP alternatives: 19k freed
[    0.026203] ACPI: Core revision 20090903
[    0.031658] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.031667] ftrace: allocating 21771 entries in 43 pages
[    0.036138] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036524] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.078024] CPU0: AMD Athlon(tm) XP  3200+ stepping 00
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (4382.61 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] devtmpfs: initialized
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 18:03:42  Date: 07/08/10
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.081996] ACPI: Executed 1 blocks of module-level executable AML code
[    0.084631] ACPI: Interpreter enabled
[    0.084639] ACPI: (supports S0 S1 S3 S4 S5)
[    0.084665] ACPI: Using IOAPIC for interrupt routing
[    0.091529] ACPI Warning: Incorrect checksum in table [OEMB] - 5D, should be 50 (20090903/tbutils-314)
[    0.091611] ACPI: No dock devices found.
[    0.091722] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.091774] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xec000000-0xefffffff]
[    0.091791] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.091995] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec1f]
[    0.092036] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.092041] pci 0000:00:01.1: PME# disabled
[    0.092072] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe900000-0xfe900fff]
[    0.092106] pci 0000:00:02.0: supports D1 D2
[    0.092108] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092112] pci 0000:00:02.0: PME# disabled
[    0.092138] pci 0000:00:02.1: reg 10 32bit mmio: [0xfea00000-0xfea00fff]
[    0.092171] pci 0000:00:02.1: supports D1 D2
[    0.092174] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092178] pci 0000:00:02.1: PME# disabled
[    0.092209] pci 0000:00:02.2: reg 10 32bit mmio: [0xfeb00000-0xfeb000ff]
[    0.092249] pci 0000:00:02.2: supports D1 D2
[    0.092251] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092255] pci 0000:00:02.2: PME# disabled
[    0.092288] pci 0000:00:04.0: reg 10 32bit mmio: [0xfe800000-0xfe800fff]
[    0.092294] pci 0000:00:04.0: reg 14 io port: [0xe880-0xe887]
[    0.092325] pci 0000:00:04.0: supports D1 D2
[    0.092327] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092331] pci 0000:00:04.0: PME# disabled
[    0.092357] pci 0000:00:06.0: reg 10 io port: [0xe000-0xe0ff]
[    0.092363] pci 0000:00:06.0: reg 14 io port: [0xef00-0xef7f]
[    0.092369] pci 0000:00:06.0: reg 18 32bit mmio: [0xfe600000-0xfe600fff]
[    0.092396] pci 0000:00:06.0: supports D1 D2
[    0.092460] pci 0000:00:09.0: reg 20 io port: [0xffa0-0xffaf]
[    0.092508] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfe500000-0xfe5007ff]
[    0.092515] pci 0000:00:0d.0: reg 14 32bit mmio: [0xfe400000-0xfe40003f]
[    0.092545] pci 0000:00:0d.0: supports D1 D2
[    0.092547] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.092551] pci 0000:00:0d.0: PME# disabled
[    0.092640] pci 0000:01:07.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.092732] pci 0000:00:08.0: bridge 32bit mmio: [0xf3900000-0xfb8fffff]
[    0.092767] pci 0000:02:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.092773] pci 0000:02:00.0: reg 14 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.092793] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfda00000-0xfda0ffff]
[    0.092845] pci 0000:00:1e.0: bridge 32bit mmio: [0xfb900000-0xfdafffff]
[    0.092849] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xdb800000-0xeb7fffff]
[    0.092859] pci_bus 0000:00: on NUMA node 0
[    0.092864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.092959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.093082] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.100117] ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *11
[    0.100282] ACPI: PCI Interrupt Link [LNKB] (IRQs 18) *0, disabled.
[    0.100445] ACPI: PCI Interrupt Link [LNKC] (IRQs 18) *0, disabled.
[    0.100606] ACPI: PCI Interrupt Link [LNKD] (IRQs 19) *11
[    0.100766] ACPI: PCI Interrupt Link [LNKE] (IRQs 16) *0, disabled.
[    0.100923] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *5
[    0.101081] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *5
[    0.101238] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *5
[    0.101404] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *3
[    0.101566] ACPI: PCI Interrupt Link [LAPU] (IRQs 20 21 22) *0, disabled.
[    0.101725] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *11
[    0.101882] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[    0.102040] ACPI: PCI Interrupt Link [LKSM] (IRQs 23) *10
[    0.102201] ACPI: PCI Interrupt Link [LFWR] (IRQs 20 21 22) *11
[    0.102364] ACPI: PCI Interrupt Link [LETH] (IRQs 20 21 22) *0, disabled.
[    0.102553] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[    0.102681] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.102684] vgaarb: loaded
[    0.102829] SCSI subsystem initialized
[    0.102922] libata version 3.00 loaded.
[    0.103014] usbcore: registered new interface driver usbfs
[    0.103029] usbcore: registered new interface driver hub
[    0.103062] usbcore: registered new device driver usb
[    0.103228] ACPI: WMI: Mapper loaded
[    0.103230] PCI: Using ACPI for IRQ routing
[    0.103385] NetLabel: Initializing
[    0.103387] NetLabel:  domain hash size = 128
[    0.103389] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.103407] NetLabel:  unlabeled traffic allowed by default
[    0.103441] Switching to clocksource tsc
[    0.104001] AppArmor: AppArmor Filesystem Enabled
[    0.104001] pnp: PnP ACPI init
[    0.104001] ACPI: bus type pnp registered
[    0.106440] pnp: PnP ACPI: found 12 devices
[    0.106443] ACPI: ACPI bus type pnp unregistered
[    0.106448] PnPBIOS: Disabled by ACPI PNP
[    0.106466] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.106474] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.106478] system 00:08: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.106481] system 00:08: iomem range 0xff780000-0xff7bffff has been reserved
[    0.106487] system 00:09: ioport range 0x480-0x4ff could not be reserved
[    0.106494] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.106497] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.106501] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.106504] system 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[    0.106508] system 00:0b: iomem range 0xff7c0000-0xffffffff has been reserved
[    0.141239] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.141242] pci 0000:00:08.0:   IO window: disabled
[    0.141248] pci 0000:00:08.0:   MEM window: 0xf3900000-0xfb8fffff
[    0.141252] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.141259] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.141261] pci 0000:00:1e.0:   IO window: disabled
[    0.141265] pci 0000:00:1e.0:   MEM window: 0xfb900000-0xfdafffff
[    0.141270] pci 0000:00:1e.0:   PREFETCH window: 0xdb800000-0xeb7fffff
[    0.141283] pci 0000:00:08.0: setting latency timer to 64
[    0.141292] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.141295] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.141298] pci_bus 0000:01: resource 1 mem: [0xf3900000-0xfb8fffff]
[    0.141301] pci_bus 0000:02: resource 1 mem: [0xfb900000-0xfdafffff]
[    0.141304] pci_bus 0000:02: resource 2 pref mem [0xdb800000-0xeb7fffff]
[    0.141346] NET: Registered protocol family 2
[    0.141447] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.141864] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.143190] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.143873] TCP: Hash tables configured (established 131072 bind 65536)
[    0.143877] TCP reno registered
[    0.144002] NET: Registered protocol family 1
[    0.196570] pci 0000:02:00.0: Boot video device
[    0.196793] cpufreq-nforce2: Detected nForce2 chipset revision A2
[    0.196796] cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
[    0.196806] cpufreq-nforce2: FSB currently at 199 MHz, FID 11.0
[    0.196836] Marking TSC unstable due to cpufreq changes
[    0.197724] Scanning for low memory corruption every 60 seconds
[    0.197833] audit: initializing netlink socket (disabled)
[    0.197846] type=2000 audit(1278612221.196:1): initialized
[    0.206703] Switching to clocksource acpi_pm
[    0.206811] Trying to unpack rootfs image as initramfs...
[    0.220123] highmem bounce pool size: 64 pages
[    0.220131] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.221850] VFS: Disk quotas dquot_6.5.2
[    0.221927] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.222568] fuse init (API version 7.13)
[    0.222658] msgmni has been set to 1690
[    0.228404] alg: No test for stdrng (krng)
[    0.228485] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.228489] io scheduler noop registered
[    0.228491] io scheduler anticipatory registered
[    0.228493] io scheduler deadline registered
[    0.228550] io scheduler cfq registered (default)
[    0.228695] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.228719] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.228844] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.228850] ACPI: Power Button [PWRB]
[    0.228904] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.228908] ACPI: Power Button [PWRF]
[    0.229128] processor LNXCPU:00: registered as cooling_device0
[    0.233098] isapnp: Scanning for PnP cards...
[    0.244391] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.244511] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.244890] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.246042] brd: module loaded
[    0.246582] loop: module loaded
[    0.246682] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.246904] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.247241] Fixed MDIO Bus: probed
[    0.247278] PPP generic driver version 2.4.2
[    0.247322] tun: Universal TUN/TAP device driver, 1.6
[    0.247325] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.247405] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.247723] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.247730]   alloc irq_desc for 22 on node -1
[    0.247732]   alloc kstat_irqs on node -1
[    0.247742] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    0.247765] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.247768] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.247814] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.247848] ehci_hcd 0000:00:02.2: debug port 1
[    0.247857] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.247877] ehci_hcd 0000:00:02.2: irq 22, io mem 0xfeb00000
[    0.291534] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.291649] usb usb1: configuration #1 chosen from 1 choice
[    0.291683] hub 1-0:1.0: USB hub found
[    0.291696] hub 1-0:1.0: 6 ports detected
[    0.291756] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.291994] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    0.292016]   alloc irq_desc for 21 on node -1
[    0.292018]   alloc kstat_irqs on node -1
[    0.292023] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, high) -> IRQ 21
[    0.292033] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.292036] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.292082] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.292107] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe900000
[    0.382076] usb usb2: configuration #1 chosen from 1 choice
[    0.382114] hub 2-0:1.0: USB hub found
[    0.382134] hub 2-0:1.0: 3 ports detected
[    0.382504] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[    0.382511]   alloc irq_desc for 20 on node -1
[    0.382513]   alloc kstat_irqs on node -1
[    0.382523] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 20 (level, high) -> IRQ 20
[    0.382545] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.382549] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.382600] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.382636] ohci_hcd 0000:00:02.1: irq 20, io mem 0xfea00000
[    0.473946] usb usb3: configuration #1 chosen from 1 choice
[    0.473984] hub 3-0:1.0: USB hub found
[    0.474001] hub 3-0:1.0: 3 ports detected
[    0.474079] uhci_hcd: USB Universal Host Controller Interface driver
[    0.474193] PNP: No PS/2 controller found. Probing ports directly.
[    0.481069] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.481080] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.481306] mice: PS/2 mouse device common for all mice
[    0.481448] rtc_cmos 00:02: RTC can wake from S4
[    0.481506] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.481538] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.481653] device-mapper: uevent: version 1.0.3
[    0.481784] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.484219] device-mapper: multipath: version 1.1.0 loaded
[    0.484224] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484448] EISA: Probing bus 0 at eisa.0
[    0.484470] Cannot allocate resource for EISA slot 4
[    0.484489] EISA: Detected 0 cards.
[    0.488408] cpuidle: using governor ladder
[    0.488412] cpuidle: using governor menu
[    0.488908] TCP cubic registered
[    0.489080] NET: Registered protocol family 10
[    0.489528] lo: Disabled Privacy Extensions
[    0.489835] NET: Registered protocol family 17
[    0.489879] powernow-k8: Processor cpuid 6a0 not supported
[    0.489901] Using IPI No-Shortcut mode
[    0.490031] PM: Resume from disk failed.
[    0.490047] registered taskstats version 1
[    0.490294]   Magic number: 2:30:89
[    0.490412] rtc_cmos 00:02: setting system clock to 2010-07-08 18:03:42 UTC (1278612222)
[    0.490415] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.490417] EDD information not available.
[    0.670348] Freeing initrd memory: 7782k freed
[    0.809272] isapnp: No Plug & Play device found
[    0.809291] Freeing unused kernel memory: 656k freed
[    0.810064] Write protecting the kernel text: 4676k
[    0.810096] Write protecting the kernel read-only data: 1840k
[    0.833227] udev: starting version 151
[    0.876101] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    0.975702] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.073905] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[    1.073916] forcedeth 0000:00:04.0: PCI INT A -> Link[LKLN] -> GSI 22 (level, high) -> IRQ 22
[    1.073925] forcedeth 0000:00:04.0: setting latency timer to 64
[    1.073986] nv_probe: set workaround bit for reversed mac addr
[    1.082930] Floppy drive(s): fd0 is 1.44M
[    1.099865] FDC 0 is a post-1991 82077
[    1.100972] usb 3-1: configuration #1 chosen from 1 choice
[    1.124549] usbcore: registered new interface driver hiddev
[    1.134128] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input3
[    1.134311] generic-usb 0003:046E:52C2.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:02.1-1/input0
[    1.158836] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.1/input/input4
[    1.159219] generic-usb 0003:046E:52C2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:02.1-1/input1
[    1.159251] usbcore: registered new interface driver usbhid
[    1.159342] usbhid: v2.6:USB HID core driver
[    1.284026] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    1.503807] usb 3-2: configuration #1 chosen from 1 choice
[    1.516367] input: Microsoft Microsoft Wireless Intellimouse ExplorerÂ® 1.0A as /devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2:1.0/input/input5
[    1.516850] generic-usb 0003:045E:0059.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft Wireless Intellimouse ExplorerÂ® 1.0A] on usb-0000:00:02.1-2/input0
[    1.592994] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:0e:a6:88:14:45
[    1.593000] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    1.593162] pata_amd 0000:00:09.0: version 0.4.1
[    1.593228] pata_amd 0000:00:09.0: setting latency timer to 64
[    1.593687] scsi0 : pata_amd
[    1.593872] scsi1 : pata_amd
[    1.595505] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.595508] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.595963] ACPI: PCI Interrupt Link [LFWR] enabled at IRQ 21
[    1.595971] ohci1394 0000:00:0d.0: PCI INT A -> Link[LFWR] -> GSI 21 (level, high) -> IRQ 21
[    1.595976] ohci1394 0000:00:0d.0: setting latency timer to 64
[    1.654030] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fe500000-fe5007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.756471] ata1.00: ATA-7: SAMSUNG SP1604N, TM100-24, max UDMA/133
[    1.756475] ata1.00: 312581808 sectors, multi 16: LBA48
[    1.756501] ata1: nv_mode_filter: 0x7f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c0c0) ACPI=0x3f01f (17:900:0x11)
[    1.764383] ata1.00: configured for UDMA/100
[    1.764528] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1604N  TM10 PQ: 0 ANSI: 5
[    1.764725] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.765080] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.765137] sd 0:0:0:0: [sda] Write Protect is off
[    1.765140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.765170] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.765343]  sda: sda1 sda2 < sda5 >
[    1.804336] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.936744] ata2.00: ATAPI: HP  DVD Writer 400, Bh04, max UDMA/33
[    1.936774] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148A, B401, max UDMA/33
[    1.936800] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (54:54:0x15)
[    1.936806] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c0c0) ACPI=0x701f (54:54:0x15)
[    1.952547] ata2.00: configured for UDMA/33
[    1.968279] ata2.01: configured for UDMA/33
[    1.971850] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 400c  Bh04 PQ: 0 ANSI: 5
[    1.980029] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.980034] Uniform CD-ROM driver Revision: 3.20
[    1.980148] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.980225] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.980680] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B401 PQ: 0 ANSI: 5
[    1.983879] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.984124] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.984256] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.323282] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.769388] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[    3.040165] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00665abe00e01800]
[    4.160796] Adding 6037496k swap on /dev/sda5.  Priority:-1 extents:1 across:6037496k
[    4.209602] udev: starting version 151
[    5.305437] Linux agpgart interface v0.103
[    5.343471] agpgart: Detected NVIDIA nForce2 chipset
[    5.349038] agpgart-nvidia 0000:00:00.0: AGP aperture is 64M @ 0xec000000
[    5.380616] lp: driver loaded but no devices found
[    5.413730] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.562236] type=1505 audit(1278612227.569:2):  operation="profile_load" pid=472 name="/sbin/dhclient3"
[    5.562543] type=1505 audit(1278612227.569:3):  operation="profile_load" pid=472 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.562714] type=1505 audit(1278612227.569:4):  operation="profile_load" pid=472 name="/usr/lib/connman/scripts/dhclient-script"
[    5.639558] parport_pc 00:06: reported by Plug and Play ACPI
[    5.639650] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    5.736241] lp0: using parport0 (interrupt-driven).
[    5.745909] type=1505 audit(1278612227.753:5):  operation="profile_load" pid=572 name="/usr/sbin/ntpd"
[    5.790792] ppdev: user-space parallel port driver
[    5.880748] i2c i2c-0: nForce2 SMBus adapter at 0x4300
[    5.880851] i2c i2c-1: nForce2 SMBus adapter at 0x4340
[    6.227015] vga16fb: initializing
[    6.227022] vga16fb: mapped to 0xc00a0000
[    6.227224] fb0: VGA16 VGA frame buffer device
[    6.624888] nvidia: module license 'NVIDIA' taints kernel.
[    6.624894] Disabling lock debugging due to kernel taint
[    6.875321] Linux video capture interface: v2.00
[    7.172219] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 16
[    7.172229]   alloc irq_desc for 16 on node -1
[    7.172231]   alloc kstat_irqs on node -1
[    7.172242] nvidia 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, high) -> IRQ 16
[    7.172253] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    7.173184] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[    7.548771] Console: switching to colour frame buffer device 80x30
[    7.908424] cx18:  Start initialization, version 1.2.0
[    7.908494] cx18-0: Initializing card 0
[    7.908500] cx18-0: Autodetected Hauppauge card
[    7.908920] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    7.908928]   alloc irq_desc for 19 on node -1
[    7.908930]   alloc kstat_irqs on node -1
[    7.908940] cx18 0000:01:07.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, high) -> IRQ 19
[    7.910505] cx18-0: cx23418 revision 01010000 (B)
[    8.130019] tveeprom 2-0050: Hauppauge model 74021, rev C6B2, serial# 1740689
[    8.130024] tveeprom 2-0050: MAC address is 00-0D-FE-1A-8F-91
[    8.130028] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[    8.130031] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[    8.130034] tveeprom 2-0050: audio processor is CX23418 (idx 38)
[    8.130037] tveeprom 2-0050: decoder processor is CX23418 (idx 31)
[    8.130040] tveeprom 2-0050: has no radio, has IR receiver, has IR transmitter
[    8.130043] cx18-0: Autodetected Hauppauge HVR-1600
[    8.130046] cx18-0: Simultaneous Digital and Analog TV capture supported
[    8.194063] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[    8.194072] Intel ICH 0000:00:06.0: PCI INT A -> Link[LAUI] -> GSI 20 (level, high) -> IRQ 20
[    8.194182] Intel ICH 0000:00:06.0: setting latency timer to 64
[    8.233480] IRQ 19/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.295088] tuner 3-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[    8.350581] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[    8.516034] intel8x0_measure_ac97_clock: measured 52692 usecs (2560 samples)
[    8.516040] intel8x0: clocking to 47423
[    8.749305] tuner-simple 3-0061: creating new instance
[    8.749311] tuner-simple 3-0061: type set to 50 (TCL 2002N)
[    8.750759] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[    8.750763] DVB: registering new adapter (cx18)
[    9.376924] MXL5005S: Attached at address 0x63
[    9.376933] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    9.377083] cx18-0: DVB Frontend registered
[    9.377086] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[    9.377125] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[    9.377154] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[    9.377193] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[    9.377197] cx18-0: Initialized card: Hauppauge HVR-1600
[    9.377224] cx18:  End initialization
[    9.872089] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-cpu.fw
[   10.257307] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   10.289799] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-apu.fw
[   10.815482] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   10.821848] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   11.028033] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-cpu.fw
[   11.192735] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-apu.fw
[   11.362030] type=1505 audit(1278612233.369:6):  operation="profile_replace" pid=904 name="/sbin/dhclient3"
[   11.362658] type=1505 audit(1278612233.369:7):  operation="profile_replace" pid=904 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.362846] type=1505 audit(1278612233.369:8):  operation="profile_replace" pid=904 name="/usr/lib/connman/scripts/dhclient-script"
[   11.434751] type=1505 audit(1278612233.442:9):  operation="profile_load" pid=905 name="/usr/bin/evince"
[   11.439009] type=1505 audit(1278612233.445:10):  operation="profile_load" pid=905 name="/usr/bin/evince-previewer"
[   11.441878] type=1505 audit(1278612233.449:11):  operation="profile_load" pid=905 name="/usr/bin/evince-thumbnailer"
[   11.521719] cx18 0000:01:07.0: firmware: requesting v4l-cx23418-dig.fw
[   11.567994] type=1505 audit(1278612233.573:12):  operation="profile_load" pid=907 name="/usr/sbin/mysqld"
[   11.570352] type=1505 audit(1278612233.577:13):  operation="profile_replace" pid=911 name="/usr/sbin/ntpd"
[   11.579214] type=1505 audit(1278612233.585:14):  operation="profile_load" pid=912 name="/usr/sbin/tcpdump"
[   12.074031] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   12.098200] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   14.720587] lirc_dev: IR Remote Control driver registered, major 61
[   15.313422] bttv: driver version 0.9.18 loaded
[   15.313427] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   15.531610] ivtv: Start initialization, version 1.4.1
[   15.532434] ivtv: End initialization
[   15.888813] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   25.612028] eth0: no IPv6 routers present
[   29.373079] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   29.373096] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   29.373156] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
[   45.312060] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000001
[   49.604042] end_request: I/O error, dev fd0, sector 0
[   49.632057] end_request: I/O error, dev fd0, sector 0
[   53.312068] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000002
[   61.312075] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000003
[   69.312057] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000004
[   77.312061] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000005
[   84.056677] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[   85.312059] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000006
[   93.312060] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000007
[  101.312057] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000008
[  109.312059] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000009
[  117.312058] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000a
[  125.312062] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000b
[  133.312060] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000c
[  141.312058] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000d
[  149.312062] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000e
[  157.312061] NVRM: Xid (0002:00): 16, Head 00000000 Count 0000000f
[  165.312061] NVRM: Xid (0002:00): 16, Head 00000000 Count 00000010

```

xorg config:
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "TVOutFormat"   "SVIDEO"
        Option  "TVStandard"    "NTSC-M"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
        Option  "ConnectedMonitor"      "TV"
EndSection

```

---

### Post by nickrout on 2010-07-09
try looking at /var/log/Xorg.0.log

---

### Post by Gorf on 2010-07-10
AH!  I believe I found the issue.  It was complaining that there was no Mode set for the display so it was defaulting to 1024x768.  I added a Device subsection in the config and set the Mode to 640x480 and now I have video.

---

### Post by nickrout on 2010-07-10
It's worth reading the TV-Out chapter of the nvidia readme.

```
zless /usr/share/doc/nvidia-current/README.txt.gz
```

---

