---
title: "Can't install nvidia drivers"
date: 2008-10-25
forum: Multimedia Software
---

### Post by lingenfr on 2008-10-25
I purchased a new machine sans O/S. I am trying to set up 8.10rc 32-bit on my Core 2 nvidia based system. I added an MSI (nvidia) 9600 GSO graphics card. I went into the bios to have it init the PCI-E video first (I have tried it both ways). I get video just find using vesa, but I have not been able to get any of the nvidia drivers working. I tried the restricted drivers and envy but it seems to be something more fundamental in my setup. Here is my dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000cffee000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000d0100000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] last_pfn = 0xcffa0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37820000 - 37fef4f3
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F9D10, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFFA0000, 0040 (r1 040708 RSDT1429 20080407 MSFT       97)
[    0.000000] ACPI: FACP CFFA0200, 0084 (r1 040708 FACP1429 20080407 MSFT       97)
[    0.000000] ACPI: DSDT CFFA04A0, 576F (r1  1AAAA 1AAAA000        0 INTL 20051117)
[    0.000000] ACPI: FACS CFFAE000, 0040
[    0.000000] ACPI: APIC CFFA0390, 0080 (r1 040708 APIC1429 20080407 MSFT       97)
[    0.000000] ACPI: MCFG CFFA0410, 003C (r1 040708 OEMMCFG  20080407 MSFT       97)
[    0.000000] ACPI: WDRT CFFA0450, 0047 (r1 040708 NV-WDRT  20080407 MSFT       97)
[    0.000000] ACPI: OEMB CFFAE040, 0071 (r1 040708 OEMB1429 20080407 MSFT       97)
[    0.000000] ACPI: HPET CFFA5C10, 0038 (r1 040708 OEMHPET0 20080407 MSFT       97)
[    0.000000] ACPI: NVHD CFFAE0C0, 0554 (r1 040708  NVHDCP  20080407 MSFT       97)
[    0.000000] 2431MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037820000 - 0037fef4f3]          RAMDISK ==> [0037820000 - 0037fef4f3]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000cffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000] On node 0 totalpages: 851775
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 617024 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0100000:2eb00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 844287
[    0.000000] Kernel command line: root=UUID=75cede7c-5258-4c85-b0e0-224e9d069804 ro xforcevesa quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2999.915 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3362332k/3407488k available (2572k kernel code, 43892k reserved, 1160k data, 424k init, 2489984k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.83 BogoMIPS (lpj=11999660)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017408] ACPI: Core revision 20080609
[    0.018254] ACPI: Checking initramfs for custom DSDT
[    0.241344] ENABLING IO-APIC IRQs
[    0.241543] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.281239] CPU0: Intel(R) Core(TM)2 CPU         E8400  @ 3.00GHz stepping 0a
[    0.284017] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5999.94 BogoMIPS (lpj=11999887)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.368715] CPU1: Intel(R) Core(TM)2 CPU         E8400  @ 3.00GHz stepping 0a
[    0.368728] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.372041] Brought up 2 CPUs
[    0.372043] Total of 2 processors activated (11999.77 BogoMIPS).
[    0.372063] CPU0 attaching sched-domain:
[    0.372065]  domain 0: span 0-1 level MC
[    0.372067]   groups: 0 1
[    0.372071] CPU1 attaching sched-domain:
[    0.372072]  domain 0: span 0-1 level MC
[    0.372074]   groups: 1 0
[    0.372131] net_namespace: 840 bytes
[    0.372131] Booting paravirtualized kernel on bare hardware
[    0.372209] Time: 20:02:16  Date: 10/25/08
[    0.372227] NET: Registered protocol family 16
[    0.372240] EISA bus registered
[    0.372240] ACPI: bus type pci registered
[    0.372240] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.372240] PCI: Not using MMCONFIG.
[    0.372240] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.372240] PCI: Using configuration type 1 for base access
[    0.372726] ACPI: EC: Look up EC in DSDT
[    0.381353] ACPI: Interpreter enabled
[    0.381356] ACPI: (supports S0 S1 S3 S4 S5)
[    0.381366] ACPI: Using IOAPIC for interrupt routing
[    0.381403] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.385010] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.385012] PCI: Using MMCONFIG for extended config space
[    0.388701] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.392294] PCI: 0000:00:03.0 reg 10 io port: [4f00, 4fff]
[    0.392333] PCI: 0000:00:03.1 reg 10 io port: [4900, 493f]
[    0.392345] PCI: 0000:00:03.1 reg 20 io port: [4d00, 4d3f]
[    0.392349] PCI: 0000:00:03.1 reg 24 io port: [4e00, 4e3f]
[    0.392364] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.392369] pci 0000:00:03.1: PME# disabled
[    0.392501] PCI: 0000:00:04.0 reg 10 32bit mmio: [f9fff000, f9ffffff]
[    0.392524] pci 0000:00:04.0: supports D1
[    0.392525] pci 0000:00:04.0: supports D2
[    0.392526] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392529] pci 0000:00:04.0: PME# disabled
[    0.392549] PCI: 0000:00:04.1 reg 10 32bit mmio: [f9ffec00, f9ffecff]
[    0.392575] pci 0000:00:04.1: supports D1
[    0.392577] pci 0000:00:04.1: supports D2
[    0.392578] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392581] pci 0000:00:04.1: PME# disabled
[    0.392614] PCI: 0000:00:08.0 reg 20 io port: [ffa0, ffaf]
[    0.392647] PCI: 0000:00:09.0 reg 10 32bit mmio: [f9ff8000, f9ffbfff]
[    0.392671] pci 0000:00:09.0: PME# supported from D3hot D3cold
[    0.392674] pci 0000:00:09.0: PME# disabled
[    0.392720] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392722] pci 0000:00:0b.0: PME# disabled
[    0.392747] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392749] pci 0000:00:0c.0: PME# disabled
[    0.392774] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392776] pci 0000:00:0d.0: PME# disabled
[    0.392793] PCI: 0000:00:0e.0 reg 10 io port: [d480, d487]
[    0.392796] PCI: 0000:00:0e.0 reg 14 io port: [d400, d403]
[    0.392799] PCI: 0000:00:0e.0 reg 18 io port: [d080, d087]
[    0.392802] PCI: 0000:00:0e.0 reg 1c io port: [d000, d003]
[    0.392806] PCI: 0000:00:0e.0 reg 20 io port: [cc00, cc0f]
[    0.392809] PCI: 0000:00:0e.0 reg 24 32bit mmio: [f9ffc000, f9ffdfff]
[    0.392838] PCI: 0000:00:0f.0 reg 10 32bit mmio: [f9ff7000, f9ff7fff]
[    0.392842] PCI: 0000:00:0f.0 reg 14 io port: [c880, c887]
[    0.392845] PCI: 0000:00:0f.0 reg 18 32bit mmio: [f9ffe800, f9ffe8ff]
[    0.392848] PCI: 0000:00:0f.0 reg 1c 32bit mmio: [f9ffe400, f9ffe40f]
[    0.392865] pci 0000:00:0f.0: supports D1
[    0.392866] pci 0000:00:0f.0: supports D2
[    0.392867] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.392871] pci 0000:00:0f.0: PME# disabled
[    0.392923] pci 0000:00:0a.0: transparent bridge
[    0.392949] PCI: 0000:02:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.392954] PCI: 0000:02:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.392964] PCI: 0000:02:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.392968] PCI: 0000:02:00.0 reg 24 io port: [ec00, ec7f]
[    0.392972] PCI: 0000:02:00.0 reg 30 32bit mmio: [febe0000, febfffff]
[    0.393017] PCI: bridge 0000:00:0b.0 io port: [e000, efff]
[    0.393019] PCI: bridge 0000:00:0b.0 32bit mmio: [fa000000, febfffff]
[    0.393023] PCI: bridge 0000:00:0b.0 64bit mmio pref: [d0000000, dfffffff]
[    0.393109] bus 00 -> node 0
[    0.393114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.393307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.393419] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.393500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.393580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.400315] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.400378] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.400558] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.400736] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.400915] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.401097] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *10
[    0.401275] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.401454] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.401636] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.401818] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.401999] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.402180] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.402362] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.402543] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.402724] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.402906] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.404147] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.404188] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 31, should be 2C [20080609]
[    0.404188] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.404188] pnp: PnP ACPI init
[    0.404188] ACPI: bus type pnp registered
[    0.408342] pnp: PnP ACPI: found 13 devices
[    0.408344] ACPI: ACPI bus type pnp unregistered
[    0.408346] PnPBIOS: Disabled by ACPI PNP
[    0.408355] PCI: Using ACPI for IRQ routing
[    0.408355] pci 0000:00:0b.0: BAR 9: can't allocate resource
[    0.408355] pci 0000:02:00.0: BAR 1: can't allocate resource
[    0.412034] NET: Registered protocol family 8
[    0.412036] NET: Registered protocol family 20
[    0.412051] NetLabel: Initializing
[    0.412051] NetLabel:  domain hash size = 128
[    0.412051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.412058] NetLabel:  unlabeled traffic allowed by default
[    0.412064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.412069] hpet0: 3 32-bit timers, 25000000 Hz
[    0.413677] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.413679]    actual entries 65620
[    0.413731] AppArmor: AppArmor Filesystem Enabled
[    0.413754] ACPI: RTC can wake from S4
[    0.420037] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.420040] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.420043] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.420046] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.420049] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.420052] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.420054] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.420057] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.420060] system 00:06: iomem range 0xfec80000-0xfd93ffff could not be reserved
[    0.420064] system 00:06: iomem range 0xfed02000-0xfed03fff has been reserved
[    0.420067] system 00:06: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.420069] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.420077] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.420080] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.420086] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.420088] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.420096] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.420102] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.420105] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.420107] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.420110] system 00:0c: iomem range 0x100000-0xcfffffff could not be reserved
[    0.420113] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.454995] pci 0000:00:0b.0: BAR 9: can't allocate mem resource [0x0-0xfffffff]
[    0.454997] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
[    0.454998] pci 0000:00:0a.0:   IO window: disabled
[    0.455001] pci 0000:00:0a.0:   MEM window: disabled
[    0.455003] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.455008] pci 0000:02:00.0: BAR 1: can't allocate mem resource [0x0-0xfffffff]
[    0.455009] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.455011] pci 0000:00:0b.0:   IO window: 0xe000-0xefff
[    0.455014] pci 0000:00:0b.0:   MEM window: 0xfa000000-0xfebfffff
[    0.455016] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.455019] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.455020] pci 0000:00:0c.0:   IO window: disabled
[    0.455023] pci 0000:00:0c.0:   MEM window: disabled
[    0.455025] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.455028] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.455029] pci 0000:00:0d.0:   IO window: disabled
[    0.455032] pci 0000:00:0d.0:   MEM window: disabled
[    0.455034] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.455040] pci 0000:00:0a.0: setting latency timer to 64
[    0.455045] pci 0000:00:0b.0: setting latency timer to 64
[    0.455050] pci 0000:00:0c.0: setting latency timer to 64
[    0.455054] pci 0000:00:0d.0: setting latency timer to 64
[    0.455056] bus: 00 index 0 io port: [0, ffff]
[    0.455057] bus: 00 index 1 mmio: [0, ffffffff]
[    0.455059] bus: 01 index 0 mmio: [0, 0]
[    0.455060] bus: 01 index 1 mmio: [0, 0]
[    0.455061] bus: 01 index 2 mmio: [0, 0]
[    0.455062] bus: 01 index 3 io port: [0, ffff]
[    0.455064] bus: 01 index 4 mmio: [0, ffffffff]
[    0.455065] bus: 02 index 0 io port: [e000, efff]
[    0.455066] bus: 02 index 1 mmio: [fa000000, febfffff]
[    0.455068] bus: 02 index 2 mmio: [0, 0]
[    0.455069] bus: 02 index 3 mmio: [0, 0]
[    0.455070] bus: 03 index 0 mmio: [0, 0]
[    0.455071] bus: 03 index 1 mmio: [0, 0]
[    0.455072] bus: 03 index 2 mmio: [0, 0]
[    0.455073] bus: 03 index 3 mmio: [0, 0]
[    0.455074] bus: 04 index 0 mmio: [0, 0]
[    0.455076] bus: 04 index 1 mmio: [0, 0]
[    0.455077] bus: 04 index 2 mmio: [0, 0]
[    0.455078] bus: 04 index 3 mmio: [0, 0]
[    0.455083] NET: Registered protocol family 2
[    0.468030] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.468215] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.468457] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.468576] TCP: Hash tables configured (established 131072 bind 65536)
[    0.468579] TCP reno registered
[    0.472039] NET: Registered protocol family 1
[    0.472132] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.503975] Switched to high resolution mode on CPU 0
[    0.691266]  it is
[    0.929272] Freeing initrd memory: 7997k freed
[    0.930170] audit: initializing netlink socket (disabled)
[    0.930196] type=2000 audit(1224964935.928:1): initialized
[    0.934337] highmem bounce pool size: 64 pages
[    0.934342] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.935870] VFS: Disk quotas dquot_6.5.1
[    0.935926] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.936008] msgmni has been set to 1721
[    0.936099] io scheduler noop registered
[    0.936101] io scheduler anticipatory registered
[    0.936102] io scheduler deadline registered
[    0.936110] io scheduler cfq registered (default)
[    0.958379] pci 0000:02:00.0: Boot video device
[    0.958463] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.958488] pcieport-driver 0000:00:0b.0: found MSI capability
[    0.958511] pci_express 0000:00:0b.0:pcie00: allocate port service
[    0.958538] pci_express 0000:00:0b.0:pcie03: allocate port service
[    0.958594] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.958617] pcieport-driver 0000:00:0c.0: found MSI capability
[    0.958636] pci_express 0000:00:0c.0:pcie00: allocate port service
[    0.958665] pci_express 0000:00:0c.0:pcie03: allocate port service
[    0.958720] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    0.958743] pcieport-driver 0000:00:0d.0: found MSI capability
[    0.958762] pci_express 0000:00:0d.0:pcie00: allocate port service
[    0.958788] pci_express 0000:00:0d.0:pcie03: allocate port service
[    0.958990] isapnp: Scanning for PnP cards...
[    1.311735] isapnp: No Plug & Play device found
[    1.332898] hpet_resources: 0xfed00000 is busy
[    1.332960] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.333058] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.333470] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.334574] brd: module loaded
[    1.334616] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.334725] PNP: No PS/2 controller found. Probing ports directly.
[    1.337315] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.337319] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.340103] mice: PS/2 mouse device common for all mice
[    1.340208] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.340237] rtc0: alarms up to one year, y3k, hpet irqs
[    1.340314] EISA: Probing bus 0 at eisa.0
[    1.340324] Cannot allocate resource for EISA slot 4
[    1.340334] EISA: Detected 0 cards.
[    1.340337] cpuidle: using governor ladder
[    1.340339] cpuidle: using governor menu
[    1.340681] TCP cubic registered
[    1.340700] Using IPI No-Shortcut mode
[    1.340805] registered taskstats version 1
[    1.340894]   Magic number: 12:985:43
[    1.340897] tty ttyec: hash matches
[    1.340946] rtc_cmos 00:08: setting system clock to 2008-10-25 20:02:17 UTC (1224964937)
[    1.340948] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.340949] EDD information not available.
[    1.341355] Freeing unused kernel memory: 424k freed
[    1.341379] Write protecting the kernel text: 2576k
[    1.341396] Write protecting the kernel read-only data: 936k
[    1.469948] fuse init (API version 7.9)
[    1.544131] processor ACPI0007:00: registered as cooling_device0
[    1.544134] ACPI: Processor [P001] (supports 8 throttling states)
[    1.544177] processor ACPI0007:01: registered as cooling_device1
[    1.545815] thermal LNXTHERM:01: registered as thermal_zone0
[    1.545939] ACPI: Thermal Zone [THRM] (30 C)
[    1.805782] usbcore: registered new interface driver usbfs
[    1.805797] usbcore: registered new interface driver hub
[    1.806147] usbcore: registered new device driver usb
[    1.806250] No dock devices found.
[    1.820943] SCSI subsystem initialized
[    1.822169] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.822476] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    1.822483] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    1.822494] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.822496] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.822523] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
[    1.822535] ohci_hcd 0000:00:04.0: irq 23, io mem 0xf9fff000
[    1.839138] libata version 3.00 loaded.
[    1.878611] usb usb1: configuration #1 chosen from 1 choice
[    1.878629] hub 1-0:1.0: USB hub found
[    1.878635] hub 1-0:1.0: 8 ports detected
[    2.085356] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    2.085364] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    2.085374] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.085376] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.085397] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    2.085413] ehci_hcd 0000:00:04.1: debug port 1
[    2.085416] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    2.085427] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf9ffec00
[    2.266671] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    2.276506] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.276588] usb usb2: configuration #1 chosen from 1 choice
[    2.276606] hub 2-0:1.0: USB hub found
[    2.276610] hub 2-0:1.0: 8 ports detected
[    2.336014] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.484248] ahci 0000:00:0e.0: version 3.0
[    2.484535] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[    2.484541] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[    2.484630] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.484632] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
[    2.484635] ahci 0000:00:0e.0: setting latency timer to 64
[    2.485003] scsi0 : ahci
[    2.485074] scsi1 : ahci
[    2.485112] scsi2 : ahci
[    2.485151] scsi3 : ahci
[    2.485210] ata1: SATA max UDMA/133 abar m8192@0xf9ffc000 port 0xf9ffc100 irq 220
[    2.485212] ata2: SATA max UDMA/133 abar m8192@0xf9ffc000 port 0xf9ffc180 irq 220
[    2.485214] ata3: SATA max UDMA/133 abar m8192@0xf9ffc000 port 0xf9ffc200 irq 220
[    2.485215] ata4: SATA max UDMA/133 abar m8192@0xf9ffc000 port 0xf9ffc280 irq 220
[    2.828010] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.965395] usb 2-1: configuration #1 chosen from 1 choice
[    2.968010] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.974308] ata1.00: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    2.974311] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.980662] ata1.00: configured for UDMA/133
[    3.300009] ata2: SATA link down (SStatus 0 SControl 300)
[    3.380009] usb 1-3: new low speed USB device using ohci_hcd and address 3
[    3.598787] usb 1-3: configuration #1 chosen from 1 choice
[    3.620011] ata3: SATA link down (SStatus 0 SControl 300)
[    3.904011] usb 1-4: new low speed USB device using ohci_hcd and address 4
[    3.940014] ata4: SATA link down (SStatus 0 SControl 300)
[    3.940118] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    3.940193] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.940469] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    3.940473] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    3.940476] forcedeth 0000:00:0f.0: setting latency timer to 64
[    4.103655] usb 1-4: configuration #1 chosen from 1 choice
[    4.107108] usbcore: registered new interface driver hiddev
[    4.119830] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb1/1-3/1-3:1.0/input/input1
[    4.120557] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:04.0-3
[    4.126827] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:04.0/usb1/1-4/1-4:1.0/input/input2
[    4.126948] input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:04.0-4
[    4.139784] input: Microsoft Microsoft&#65533; Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:04.0/usb1/1-4/1-4:1.1/input/input3
[    4.139910] input,hidraw2: USB HID v1.11 Device [Microsoft Microsoft&#65533; Digital Media Pro Keyboard] on usb-0000:00:04.0-4
[    4.139921] usbcore: registered new interface driver usbhid
[    4.139922] usbhid: v2.6:USB HID core driver
[    4.460615] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:90:e9:90:36
[    4.460618] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    4.460643] pata_amd 0000:00:08.0: version 0.3.10
[    4.460680] pata_amd 0000:00:08.0: setting latency timer to 64
[    4.461217] scsi4 : pata_amd
[    4.461261] scsi5 : pata_amd
[    4.462086] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.462089] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.624277] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB02, max UDMA/66
[    4.624288] ata5: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    4.640216] ata5.00: configured for UDMA/33
[    4.640234] ata6: port disabled. ignoring.
[    4.640787] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB02 PQ: 0 ANSI: 5
[    4.650708] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.650733] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    4.661522] Driver 'sr' needs updating - please use bus_type methods
[    4.663363] sr0: scsi3-mmc drive: 16x/16x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.663365] Uniform CD-ROM driver Revision: 3.20
[    4.663420] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.664620] Driver 'sd' needs updating - please use bus_type methods
[    4.665360] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    4.665378] sd 0:0:0:0: [sda] Write Protect is off
[    4.665380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.665398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.665439] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[    4.665449] sd 0:0:0:0: [sda] Write Protect is off
[    4.665451] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.665470] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.665473]  sda: sda1 sda2 < sda5 >
[    4.706812] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.107548] PM: Starting manual resume from disk
[    7.107550] PM: Resume from partition 8:5
[    7.107551] PM: Checking hibernation image.
[    7.107630] PM: Resume from disk failed.
[    7.163831] kjournald starting.  Commit interval 5 seconds
[    7.163836] EXT3-fs: mounted filesystem with ordered data mode.
[   11.945483] udevd version 124 started
[   12.250639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.268372] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.395187] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.412512] ACPI: Power Button (FF) [PWRF]
[   12.412581] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.444522] ACPI: Power Button (CM) [PWRB]
[   12.699756] parport_pc 00:05: reported by Plug and Play ACPI
[   12.699797] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   12.704044] ACPI: WMI: Mapper loaded
[   12.759953] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   12.760224] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   12.760227] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   12.760242] HDA Intel 0000:00:09.0: setting latency timer to 64
[   12.893334] usbcore: registered new interface driver lmpcm_usb
[   12.893346] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   12.947426] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.984386] Linux agpgart interface v0.103
[   13.121267] nvidia: module license 'NVIDIA' taints kernel.
[   13.377527] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[   13.377535] nvidia 0000:02:00.0: PCI INT A -> Link[LNEB] -> GSI 19 (level, low) -> IRQ 19
[   13.377538] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[   13.377539] NVRM: BAR1 is 0M @ 0x00000000 (PCI:0002:00.0)
[   13.377540] NVRM: The system BIOS may have misconfigured your graphics card.
[   13.377626] nvidia: probe of 0000:02:00.0 failed with error -1
[   13.377638] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   13.377640] NVRM: None of the NVIDIA graphics adapters were initialized!
[   14.917636] lp0: using parport0 (interrupt-driven).
[   14.938377] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.096011] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[   15.236342] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,09/29/2006,1.0.3.7) loaded
[   15.956271] wlan0: ethernet device 00:1c:10:e7:e9:94 using NDIS driver: netmw245, version: 0x1000206, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 13B1:0029.F.conf
[   15.956282] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.956304] usbcore: registered new interface driver ndiswrapper
[   16.009527] Adding 9871900k swap on /dev/sda5.  Priority:-1 extents:1 across:9871900k
[   16.552121] EXT3 FS on sda1, internal journal
[   17.445369] type=1505 audit(1224964953.589:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4035
[   17.445471] type=1505 audit(1224964953.589:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4035
[   17.570595] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.442808] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.471476] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.471480] apm: disabled - APM is not SMP safe.
[   18.564607] ppdev: user-space parallel port driver
[   20.006860] Bluetooth: Core ver 2.13
[   20.007541] NET: Registered protocol family 31
[   20.007543] Bluetooth: HCI device and connection manager initialized
[   20.007545] Bluetooth: HCI socket layer initialized
[   20.013529] Bluetooth: L2CAP ver 2.11
[   20.013532] Bluetooth: L2CAP socket layer initialized
[   20.027347] Bluetooth: RFCOMM socket layer initialized
[   20.027355] Bluetooth: RFCOMM TTY layer initialized
[   20.027357] Bluetooth: RFCOMM ver 1.10
[   20.037850] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.037853] Bluetooth: BNEP filters: protocol multicast
[   20.071482] Bridge firewalling registered
[   20.071838] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   20.077429] Bluetooth: SCO (Voice Link) ver 0.6
[   20.077432] Bluetooth: SCO socket layer initialized
[   21.637475] mtrr: base(0xfb000000) is not aligned on a size(0xe00000) boundary
[   24.077373] eth0: no link during initialization.
[   26.370248] NET: Registered protocol family 17
[  272.783109] NET: Registered protocol family 10
[  272.784267] lo: Disabled Privacy Extensions
[  272.785085] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  280.416444] ppdev0: registered pardevice
[  280.464190] ppdev0: unregistered pardevice
[  280.670262] ppdev0: registered pardevice
[  280.712140] ppdev0: unregistered pardevice
[  281.738426] ppdev0: registered pardevice
[  281.784019] ppdev0: unregistered pardevice
[  281.921332] type=1503 audit(1224965218.064:4): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5592/net/" pid=5592 profile="/usr/sbin/cupsd"
[  282.943771] type=1503 audit(1224965219.084:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5597/net/" pid=5597 profile="/usr/sbin/cupsd"
[  282.943789] type=1503 audit(1224965219.084:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943793] type=1503 audit(1224965219.084:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943797] type=1503 audit(1224965219.084:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943801] type=1503 audit(1224965219.084:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943805] type=1503 audit(1224965219.084:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943809] type=1503 audit(1224965219.084:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943813] type=1503 audit(1224965219.084:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5597 profile="/usr/sbin/cupsd"
[  282.943817] type=1503 audit(1224965219.084:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5597 profile="/usr/sbin/cupsd"

Here is the output of lspci:

00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600 GSO (rev a2)

Any ideas? My next step is to revert back to Hardy, but I have a feeling that won't help until I sort out the issues that are showing up in dmesg. The mobo is an ECS GF7050VT-M. I am going to check on updating the bios. I just don't know what else to do. Thanks.

---

### Post by Amarsingh0793 on 2008-10-26
I recommend you go to Hardy (or just wait for a few days for Intrepid to be fully stable and released to the public). Remember that Intrepid has a few days left before release for a reason - it's not completely "finished", so by installing it now, you should expect maybe something to go wrong (unless you're lucky:)).

---

### Post by lingenfr on 2008-10-26
I may try that as a last resort. Unfortunately, I think this is a problem with the motherboard. I would expect similar issues with any version of Linux or even windows. For the heck of it, I may try loading windows. I ordered an ATI 4670 based card to see if I get a different result. I went the Nvidia route as they seem to have better linux support. I guess their mobos aren't as high in quality. While I appreciate the response, you are really saying don't use anything other than LTS or if you do, don't ask questions on the forum. That's probably the wrong message. Thanks anyway.

---

### Post by Amarsingh0793 on 2008-10-26
> **lingenfr said:**
> I may try that as a last resort. Unfortunately, I think this is a problem with the motherboard. I would expect similar issues with any version of Linux or even windows. For the heck of it, I may try loading windows. I ordered an ATI 4670 based card to see if I get a different result. I went the Nvidia route as they seem to have better linux support. I guess their mobos aren't as high in quality. While I appreciate the response, you are really saying don't use anything other than LTS or if you do, don't ask questions on the forum. That's probably the wrong message. Thanks anyway.

Lol I didn't mean it in that sense. Basically I'm repeating whats on ubuntu.com. They encourage you to stay with the current stable release for standard desktop use. The betas are usually for people who want to test it, find bugs and report them.

---

