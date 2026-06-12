---
title: "TechniSat AirStar-HD-5000-USB tuner anyone?"
date: 2010-08-18
forum: Mythbuntu
---

### Post by anoldguy on 2010-08-18
Has anyone used the TechniSat AirStar-HD-5000-USB tuner? 

If you have, how did you configure it?  

I tried and Mythbuntu can't probe it.

I've searched the forum and FAQs without success. 

I'm new to Ubuntu and Mythbuntu.  I loaded Mythbuntu 10.04 on a blank hard drive and it performs fine.  I have a pair of the TechniSats that I'd love to set up on Mythbuntu.  

Mike

---

### Post by bance on 2010-08-19
Looks like you might have to do a bit of work, to get these cards to function.

See [[COLOR=Red]_here_[/COLOR]]("http://www.mythtv.org/wiki/Technisat_AirStar_HD-5000")[COLOR=Black].

If you find the link useful you might consider adding to the wikki.):P

Good luck Steve.
[/COLOR]

---

### Post by anoldguy on 2010-08-19
Thank you for the link to MythTV.  It talks about the cards being used in MythTV. My TechniSat boxes are USB, not PC cards.  Has anyone been able to use these? 

I can bring up the Mythbuntu configuration screen, but don't know how to tell it to look for the TechniSat USB box.  Do I need to remove Mythbuntu and install MythTV?  

The link talks about a kernel patch.  Is that like a Windows driver install?  Do I have to edit the kernel? 

Or, should I just throw out the TechniSats and buy a new Hauppauge tuner? 

Please forgive my ignorant questions, I'm new to Linux. 

Mike

---

### Post by bance on 2010-08-19
OK, let's see if your machine recognises the card.

In a terminal (Applications>Accessories>Terminal) type :

[HTML]stephen@stephen-backend:~$[COLOR=Red] dmesg [COLOR=Black][[/COLOR][/COLOR]/HTML]


Please post out-put. ( It helps if you wrap HTML around it.)

---

### Post by anoldguy on 2010-08-25
Thanks Steve.  I had to install gedit as a way to make a file from the terminal session. I had the Technisat Airstar powered up and plugged into the USB port when I powered on Mythbuntu. 

[html]h:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 (Ubuntu 2.6.32-24.39-generic-pae 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  modified: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  modified: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfff0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 37862000 - 37fefc31
[    0.000000] Allocated new RAMDISK: 0093f000 - 010ccc31
[    0.000000] Move RAMDISK from 0000000037862000 - 0000000037fefc30 to 0093f000 - 010ccc30
[    0.000000] ACPI: RSDP 000fa850 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT cffa0000 00044 (v01 020609 RSDT1755 20090206 MSFT 00000097)
[    0.000000] ACPI: FACP cffa0200 00084 (v01 020609 FACP1755 20090206 MSFT 00000097)
[    0.000000] ACPI: DSDT cffa0450 08816 (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS cffae000 00040
[    0.000000] ACPI: APIC cffa0390 00080 (v01 020609 APIC1755 20090206 MSFT 00000097)
[    0.000000] ACPI: MCFG cffa0410 0003C (v01 020609 OEMMCFG  20090206 MSFT 00000097)
[    0.000000] ACPI: OEMB cffae040 00073 (v01 020609 OEMB1755 20090206 MSFT 00000097)
[    0.000000] ACPI: HPET cffaa450 00038 (v01 020609 OEMHPET0 20090206 MSFT 00000097)
[    0.000000] ACPI: INFO cffae0c0 00124 (v01 020609 AMDINFO  20090206 MSFT 00000097)
[    0.000000] ACPI: NVHD cffae1f0 00284 (v01 020609  NVHDCP  20090206 MSFT 00000097)
[    0.000000] ACPI: SSDT cffaa490 002B4 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 3974MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00009367f8]    TEXT DATA BSS ==> [0000100000 - 00009367f8]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000937000 - 000093e0eb]              BRK ==> [0000937000 - 000093e0eb]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000093f000 - 00010ccc31]      NEW RAMDISK ==> [000093f000 - 00010ccc31]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048366
[    0.000000] free_area_init_node: node 0, pgdat c07d8d80, node_mem_map c10ce200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 7949 pages used for memmap
[    0.000000]   HighMem zone: 812693 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x2008
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3800000 s39480 r0 d21960 u524288
[    0.000000] pcpu-alloc: s39480 r0 d21960 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038637
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=93823d78-0173-4413-bb3e-1f8230fd1480 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 24903360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00130000)
[    0.000000] Memory: 4111764k/4980736k available (4832k kernel code, 80540k reserved, 2221k data, 676k init, 3282568k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e4000 - 0xc088d000   ( 676 kB)
[    0.000000]       .data : 0xc05b821b - 0xc07e3828   (2221 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b821b   (4832 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.740 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.48 BogoMIPS (lpj=10798960)
[    0.004018] Security Framework initialized
[    0.004032] AppArmor: AppArmor initialized
[    0.004038] Mount-cache hash table entries: 512
[    0.004129] Initializing cgroup subsys ns
[    0.004132] Initializing cgroup subsys cpuacct
[    0.004135] Initializing cgroup subsys memory
[    0.004140] Initializing cgroup subsys devices
[    0.004142] Initializing cgroup subsys freezer
[    0.004144] Initializing cgroup subsys net_cls
[    0.004157] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004160] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004161] CPU: Physical Processor ID: 0
[    0.004163] CPU: Processor Core ID: 0
[    0.004166] mce: CPU supports 6 MCE banks
[    0.004174] using C1E aware idle routine
[    0.004179] Performance Events: AMD PMU driver.
[    0.004182] ... version:                0
[    0.004183] ... bit width:              48
[    0.004185] ... generic registers:      4
[    0.004186] ... value mask:             0000ffffffffffff
[    0.004188] ... max period:             00007fffffffffff
[    0.004190] ... fixed-purpose events:   0
[    0.004191] ... event mask:             000000000000000f
[    0.004194] Checking 'hlt' instruction... OK.
[    0.021872] ACPI: Core revision 20090903
[    0.033818] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033823] ftrace: allocating 22411 entries in 44 pages
[    0.036059] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036532] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079538] CPU0: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.164109] CPU1: AMD Athlon(tm) 7750 Dual-Core Processor stepping 03
[    0.164121] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168011] Brought up 2 CPUs
[    0.168013] Total of 2 processors activated (10799.51 BogoMIPS).
[    0.168394] CPU0 attaching sched-domain:
[    0.168397]  domain 0: span 0-1 level MC
[    0.168399]   groups: 0 1
[    0.168403] CPU1 attaching sched-domain:
[    0.168405]  domain 0: span 0-1 level MC
[    0.168406]   groups: 1 0
[    0.168465] devtmpfs: initialized
[    0.168465] regulator: core version 0.5
[    0.168465] Time: 19:36:42  Date: 08/25/10
[    0.168465] NET: Registered protocol family 16
[    0.168465] EISA bus registered
[    0.168465] Trying to unpack rootfs image as initramfs...
[    0.168465] ACPI: bus type pci registered
[    0.168465] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168465] PCI: Not using MMCONFIG.
[    0.169072] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.169074] PCI: Using configuration type 1 for base access
[    0.169075] PCI: Using configuration type 1 for extended access
[    0.172071] bio: create slab <bio-0> at 0
[    0.172920] ACPI: EC: Look up EC in DSDT
[    0.178545] ACPI: Executed 1 blocks of module-level executable AML code
[    0.185651] ACPI: Interpreter enabled
[    0.185656] ACPI: (supports S0 S3 S4 S5)
[    0.185671] ACPI: Using IOAPIC for interrupt routing
[    0.185720] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.192058] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.192060] PCI: Using MMCONFIG for extended config space
[    0.205128] ACPI: No dock devices found.
[    0.205514] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.205765] pci 0000:00:01.0: reg 10 io port: [0x2f00-0x2fff]
[    0.205804] pci 0000:00:01.1: reg 10 io port: [0x2900-0x293f]
[    0.205814] pci 0000:00:01.1: reg 20 io port: [0x2d00-0x2d3f]
[    0.205819] pci 0000:00:01.1: reg 24 io port: [0x2e00-0x2e3f]
[    0.205838] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.205844] pci 0000:00:01.1: PME# disabled
[    0.205900] pci 0000:00:01.3: reg 10 32bit mmio: [0xf9f80000-0xf9ffffff]
[    0.206025] pci 0000:00:02.0: reg 10 32bit mmio: [0xf9f7f000-0xf9f7ffff]
[    0.206048] pci 0000:00:02.0: supports D1 D2
[    0.206050] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206053] pci 0000:00:02.0: PME# disabled
[    0.206075] pci 0000:00:02.1: reg 10 32bit mmio: [0xf9f7ec00-0xf9f7ecff]
[    0.206102] pci 0000:00:02.1: supports D1 D2
[    0.206104] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206107] pci 0000:00:02.1: PME# disabled
[    0.206132] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9f7d000-0xf9f7dfff]
[    0.206155] pci 0000:00:04.0: supports D1 D2
[    0.206157] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206160] pci 0000:00:04.0: PME# disabled
[    0.206182] pci 0000:00:04.1: reg 10 32bit mmio: [0xf9f7e800-0xf9f7e8ff]
[    0.206209] pci 0000:00:04.1: supports D1 D2
[    0.206211] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206214] pci 0000:00:04.1: PME# disabled
[    0.206247] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.206278] pci 0000:00:07.0: reg 10 32bit mmio: [0xf9f78000-0xf9f7bfff]
[    0.206301] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.206304] pci 0000:00:07.0: PME# disabled
[    0.206359] pci 0000:00:09.0: reg 10 io port: [0xc480-0xc487]
[    0.206363] pci 0000:00:09.0: reg 14 io port: [0xc400-0xc403]
[    0.206367] pci 0000:00:09.0: reg 18 io port: [0xc080-0xc087]
[    0.206370] pci 0000:00:09.0: reg 1c io port: [0xc000-0xc003]
[    0.206374] pci 0000:00:09.0: reg 20 io port: [0xbc00-0xbc0f]
[    0.206377] pci 0000:00:09.0: reg 24 32bit mmio: [0xf9f76000-0xf9f77fff]
[    0.206636] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206644] pci 0000:00:10.0: PME# disabled
[    0.206917] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206924] pci 0000:00:12.0: PME# disabled
[    0.207196] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.207204] pci 0000:00:13.0: PME# disabled
[    0.207475] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.207483] pci 0000:00:14.0: PME# disabled
[    0.207623] pci 0000:00:08.0: transparent bridge
[    0.207656] pci 0000:02:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.207664] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.207671] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.207676] pci 0000:02:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.207681] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfde80000-0xfdefffff]
[    0.207748] pci 0000:00:10.0: bridge io port: [0xd000-0xdfff]
[    0.207756] pci 0000:00:10.0: bridge 32bit mmio: [0xfa000000-0xfdefffff]
[    0.207769] pci 0000:00:10.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.207948] pci 0000:05:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.207962] pci 0000:05:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]
[    0.207972] pci 0000:05:00.0: reg 20 64bit mmio pref: [0xf8ff0000-0xf8ffffff]
[    0.207979] pci 0000:05:00.0: reg 30 32bit mmio pref: [0xfdfc0000-0xfdfdffff]
[    0.208011] pci 0000:05:00.0: supports D1 D2
[    0.208013] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208017] pci 0000:05:00.0: PME# disabled
[    0.208075] pci 0000:00:14.0: bridge io port: [0xe000-0xefff]
[    0.208083] pci 0000:00:14.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.208096] pci 0000:00:14.0: bridge 64bit mmio pref: [0xf8f00000-0xf8ffffff]
[    0.208147] pci_bus 0000:00: on NUMA node 0
[    0.208150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.208369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.208467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.208525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.208580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.208634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.223886] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.224117] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.224340] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.224563] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.224790] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.225013] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.225238] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.225460] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.225683] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.225906] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.226130] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.226354] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.226582] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.226803] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.227027] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.227250] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.227478] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
[    0.227700] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.227923] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.228152] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.228380] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *7
[    0.228604] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.228827] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.229053] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.229276] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.229500] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.229724] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.229947] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.230170] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.230392] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.230615] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.230839] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.231061] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.231285] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.231508] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.231731] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.231958] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.232193] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.232415] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
[    0.232642] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.232865] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.233093] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.233319] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[    0.233547] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.233806] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.234033] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *10
[    0.234260] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
[    0.234365] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.234367] vgaarb: loaded
[    0.234449] SCSI subsystem initialized
[    0.234526] libata version 3.00 loaded.
[    0.234578] usbcore: registered new interface driver usbfs
[    0.234587] usbcore: registered new interface driver hub
[    0.234605] usbcore: registered new device driver usb
[    0.234709] ACPI: WMI: Mapper loaded
[    0.234711] PCI: Using ACPI for IRQ routing
[    0.234852] NetLabel: Initializing
[    0.234853] NetLabel:  domain hash size = 128
[    0.234854] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.234865] NetLabel:  unlabeled traffic allowed by default
[    0.234891] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.234895] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.240229] Switching to clocksource tsc
[    0.241206] AppArmor: AppArmor Filesystem Enabled
[    0.241216] pnp: PnP ACPI init
[    0.241225] ACPI: bus type pnp registered
[    0.247009] pnp: PnP ACPI: found 13 devices
[    0.247011] ACPI: ACPI bus type pnp unregistered
[    0.247014] PnPBIOS: Disabled by ACPI PNP
[    0.247024] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.247027] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.247029] system 00:04: ioport range 0x2000-0x207f has been reserved
[    0.247032] system 00:04: ioport range 0x2080-0x20ff has been reserved
[    0.247034] system 00:04: ioport range 0x2400-0x247f has been reserved
[    0.247037] system 00:04: ioport range 0x2480-0x24ff has been reserved
[    0.247039] system 00:04: ioport range 0x2800-0x287f has been reserved
[    0.247041] system 00:04: ioport range 0x2880-0x28ff has been reserved
[    0.247045] system 00:04: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.247047] system 00:04: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.247052] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.247055] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.247060] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.247062] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.247068] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.247073] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.247075] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.247078] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.247080] system 00:0c: iomem range 0x100000-0xcfffffff could not be reserved
[    0.247083] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.352955] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.352957] pci 0000:00:08.0:   IO window: disabled
[    0.352960] pci 0000:00:08.0:   MEM window: disabled
[    0.352963] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.352967] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.352972] pci 0000:00:10.0:   IO window: 0xd000-0xdfff
[    0.352981] pci 0000:00:10.0:   MEM window: 0xfa000000-0xfdefffff
[    0.352989] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.353001] pci 0000:00:12.0: PCI bridge, secondary bus 0000:03
[    0.353003] pci 0000:00:12.0:   IO window: disabled
[    0.353012] pci 0000:00:12.0:   MEM window: disabled
[    0.353019] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.353031] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.353033] pci 0000:00:13.0:   IO window: disabled
[    0.353042] pci 0000:00:13.0:   MEM window: disabled
[    0.353048] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.353060] pci 0000:00:14.0: PCI bridge, secondary bus 0000:05
[    0.353065] pci 0000:00:14.0:   IO window: 0xe000-0xefff
[    0.353075] pci 0000:00:14.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.353082] pci 0000:00:14.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.353099] pci 0000:00:08.0: setting latency timer to 64
[    0.353428] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.353432]   alloc irq_desc for 19 on node -1
[    0.353434]   alloc kstat_irqs on node -1
[    0.353441] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.353449] pci 0000:00:10.0: setting latency timer to 64
[    0.353768] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.353770]   alloc irq_desc for 18 on node -1
[    0.353772]   alloc kstat_irqs on node -1
[    0.353778] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.353786] pci 0000:00:12.0: setting latency timer to 64
[    0.354103] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.354105]   alloc irq_desc for 17 on node -1
[    0.354107]   alloc kstat_irqs on node -1
[    0.354113] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.354121] pci 0000:00:13.0: setting latency timer to 64
[    0.354438] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 16
[    0.354440]   alloc irq_desc for 16 on node -1
[    0.354442]   alloc kstat_irqs on node -1
[    0.354448] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    0.354456] pci 0000:00:14.0: setting latency timer to 64
[    0.354462] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.354464] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.354467] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.354469] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.354471] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.354474] pci_bus 0000:02: resource 1 mem: [0xfa000000-0xfdefffff]
[    0.354476] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.354478] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.354480] pci_bus 0000:05: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.354483] pci_bus 0000:05: resource 2 pref mem [0xf8f00000-0xf8ffffff]
[    0.354513] NET: Registered protocol family 2
[    0.354588] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.354831] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.355309] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.355548] TCP: Hash tables configured (established 131072 bind 65536)
[    0.355550] TCP reno registered
[    0.355611] NET: Registered protocol family 1
[    0.439508] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.439610] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.439840] pci 0000:02:00.0: Boot video device
[    0.440012] cpufreq-nforce2: No nForce2 chipset.
[    0.440031] Scanning for low memory corruption every 60 seconds
[    0.440109] audit: initializing netlink socket (disabled)
[    0.440117] type=2000 audit(1282765002.439:1): initialized
[    0.447142] highmem bounce pool size: 64 pages
[    0.447146] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.448104] VFS: Disk quotas dquot_6.5.2
[    0.448148] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.448543] fuse init (API version 7.13)
[    0.448606] msgmni has been set to 1621
[    0.448770] alg: No test for stdrng (krng)
[    0.448812] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.448815] io scheduler noop registered
[    0.448816] io scheduler anticipatory registered
[    0.448818] io scheduler deadline registered
[    0.448846] io scheduler cfq registered (default)
[    0.449138]   alloc irq_desc for 24 on node -1
[    0.449139]   alloc kstat_irqs on node -1
[    0.449159] pcieport 0000:00:10.0: irq 24 for MSI/MSI-X
[    0.449178] pcieport 0000:00:10.0: setting latency timer to 64
[    0.449541]   alloc irq_desc for 25 on node -1
[    0.449543]   alloc kstat_irqs on node -1
[    0.449558] pcieport 0000:00:12.0: irq 25 for MSI/MSI-X
[    0.449576] pcieport 0000:00:12.0: setting latency timer to 64
[    0.449927]   alloc irq_desc for 26 on node -1
[    0.449929]   alloc kstat_irqs on node -1
[    0.449944] pcieport 0000:00:13.0: irq 26 for MSI/MSI-X
[    0.449962] pcieport 0000:00:13.0: setting latency timer to 64
[    0.450312]   alloc irq_desc for 27 on node -1
[    0.450313]   alloc kstat_irqs on node -1
[    0.450329] pcieport 0000:00:14.0: irq 27 for MSI/MSI-X
[    0.450347] pcieport 0000:00:14.0: setting latency timer to 64
[    0.450495] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.450513] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.450609] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.450618] ACPI: Power Button [PWRB]
[    0.450659] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.450661] ACPI: Power Button [PWRF]
[    0.450948] processor LNXCPU:00: registered as cooling_device0
[    0.450971] processor LNXCPU:01: registered as cooling_device1
[    0.456617] Freeing initrd memory: 7735k freed
[    0.456706] thermal LNXTHERM:01: registered as thermal_zone0
[    0.456712] ACPI: Thermal Zone [THRM] (30 C)
[    0.457893] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.458800] brd: module loaded
[    0.459127] loop: module loaded
[    0.459201] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.459380] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.459625] Fixed MDIO Bus: probed
[    0.459653] PPP generic driver version 2.4.2
[    0.459672] isapnp: Scanning for PnP cards...
[    0.459685] tun: Universal TUN/TAP device driver, 1.6
[    0.459687] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.459750] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.460090] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    0.460095]   alloc irq_desc for 23 on node -1
[    0.460097]   alloc kstat_irqs on node -1
[    0.460106] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    0.460117] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.460119] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.460142] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.460160] ehci_hcd 0000:00:02.1: debug port 1
[    0.460167] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.460186] ehci_hcd 0000:00:02.1: irq 23, io mem 0xf9f7ec00
[    0.471400] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.471460] usb usb1: configuration #1 chosen from 1 choice
[    0.471482] hub 1-0:1.0: USB hub found
[    0.471488] hub 1-0:1.0: 6 ports detected
[    0.471860] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 22
[    0.471863]   alloc irq_desc for 22 on node -1
[    0.471864]   alloc kstat_irqs on node -1
[    0.471870] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 22 (level, low) -> IRQ 22
[    0.471878] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.471880] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.471901] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.471916] ehci_hcd 0000:00:04.1: debug port 1
[    0.471923] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.471937] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf9f7e800
[    0.483399] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.483443] usb usb2: configuration #1 chosen from 1 choice
[    0.483461] hub 2-0:1.0: USB hub found
[    0.483466] hub 2-0:1.0: 6 ports detected
[    0.483503] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.483844] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    0.483846]   alloc irq_desc for 21 on node -1
[    0.483847]   alloc kstat_irqs on node -1
[    0.483853] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    0.483860] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.483863] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.483887] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.483906] ohci_hcd 0000:00:02.0: irq 21, io mem 0xf9f7f000
[    0.541433] usb usb3: configuration #1 chosen from 1 choice
[    0.541451] hub 3-0:1.0: USB hub found
[    0.541459] hub 3-0:1.0: 6 ports detected
[    0.541823] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 20
[    0.541825]   alloc irq_desc for 20 on node -1
[    0.541827]   alloc kstat_irqs on node -1
[    0.541833] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 20 (level, low) -> IRQ 20
[    0.541840] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.541842] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.541863] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.541881] ohci_hcd 0000:00:04.0: irq 20, io mem 0xf9f7d000
[    0.597443] usb usb4: configuration #1 chosen from 1 choice
[    0.597459] hub 4-0:1.0: USB hub found
[    0.597465] hub 4-0:1.0: 6 ports detected
[    0.597499] uhci_hcd: USB Universal Host Controller Interface driver
[    0.597552] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.600263] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.600268] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.600340] mice: PS/2 mouse device common for all mice
[    0.600425] rtc_cmos 00:06: RTC can wake from S4
[    0.600451] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.600504] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.600576] device-mapper: uevent: version 1.0.3
[    0.600661] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.600709] device-mapper: multipath: version 1.1.0 loaded
[    0.600711] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.600787] EISA: Probing bus 0 at eisa.0
[    0.600794] Cannot allocate resource for EISA slot 2
[    0.600810] EISA: Detected 0 cards.
[    0.600860] cpuidle: using governor ladder
[    0.600861] cpuidle: using governor menu
[    0.601168] TCP cubic registered
[    0.601270] NET: Registered protocol family 10
[    0.601613] lo: Disabled Privacy Extensions
[    0.601850] NET: Registered protocol family 17
[    0.601872] powernow-k8: Found 1 AMD Athlon(tm) 7750 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    0.601894] powernow-k8:    0 : pstate 0 (2700 MHz)
[    0.601896] powernow-k8:    1 : pstate 1 (1350 MHz)
[    0.618492] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.638868] Using IPI No-Shortcut mode
[    0.638944] PM: Resume from disk failed.
[    0.638958] registered taskstats version 1
[    0.639504]   Magic number: 6:488:648
[    0.639560] processor LNXCPU:01: hash matches
[    0.639620] rtc_cmos 00:06: setting system clock to 2010-08-25 19:36:43 UTC (1282765003)
[    0.639623] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.639624] EDD information not available.
[    0.812664] isapnp: No Plug & Play device found
[    0.812681] Freeing unused kernel memory: 676k freed
[    0.812993] Write protecting the kernel text: 4836k
[    0.813044] Write protecting the kernel read-only data: 1880k
[    0.824870] udev: starting version 151
[    0.835597] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    0.873447] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.873467] r8169 0000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    0.873497] r8169 0000:05:00.0: setting latency timer to 64
[    0.873528]   alloc irq_desc for 28 on node -1
[    0.873530]   alloc kstat_irqs on node -1
[    0.873541] r8169 0000:05:00.0: irq 28 for MSI/MSI-X
[    0.874003] eth0: RTL8168c/8111c at 0xf8282000, 00:25:11:08:c0:cc, XID 1c4000c0 IRQ 28
[    0.879720] pata_amd 0000:00:06.0: version 0.4.1
[    0.879754] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.890215] scsi0 : pata_amd
[    0.902722] scsi1 : pata_amd
[    0.903648] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.903651] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.903874] ahci 0000:00:09.0: version 3.0
[    0.904197] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.904201] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.904238]   alloc irq_desc for 29 on node -1
[    0.904240]   alloc kstat_irqs on node -1
[    0.904247] ahci 0000:00:09.0: irq 29 for MSI/MSI-X
[    0.904304] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.904308] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio boh 
[    0.904311] ahci 0000:00:09.0: setting latency timer to 64
[    0.909578] scsi2 : ahci
[    0.910642] scsi3 : ahci
[    0.910722] scsi4 : ahci
[    0.910771] scsi5 : ahci
[    0.910817] scsi6 : ahci
[    0.910864] scsi7 : ahci
[    0.910980] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 29
[    0.910983] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 29
[    0.910985] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 29
[    0.910988] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 29
[    0.910990] ata7: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 29
[    0.910993] ata8: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 29
[    0.972446] usb 2-4: configuration #1 chosen from 1 choice
[    1.070490] ata2: port disabled. ignoring.
[    1.132018] ata8: SATA link down (SStatus 0 SControl 300)
[    1.132041] ata7: SATA link down (SStatus 0 SControl 300)
[    1.132044] ata6: SATA link down (SStatus 0 SControl 300)
[    1.132055] ata5: SATA link down (SStatus 0 SControl 300)
[    1.296011] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.296021] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.296661] ata4.00: ATAPI: ATAPI   iHAS422   8, 4L11, max UDMA/100
[    1.296776] ata3.00: ATA-8: WDC WD3200AAKS-00V1A0, 05.01D05, max UDMA/133
[    1.296779] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.297548] ata4.00: configured for UDMA/100
[    1.297687] ata3.00: configured for UDMA/133
[    1.297767] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 05.0 PQ: 0 ANSI: 5
[    1.297880] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.297946] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.297977] sd 2:0:0:0: [sda] Write Protect is off
[    1.297979] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.297993] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.298088]  sda:
[    1.299555] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS422   8      4L11 PQ: 0 ANSI: 5
[    1.305811] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.305814] Uniform CD-ROM driver Revision: 3.20
[    1.305882] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.305924] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.308645]  sda1 sda2 < sda5 >
[    1.337884] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.554699] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.554703] EXT4-fs (sda1): write access will be enabled during recovery
[    2.488397] EXT4-fs (sda1): recovery complete
[    2.488785] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.717581] udev: starting version 151
[    9.800014] Adding 9828344k swap on /dev/sda5.  Priority:-1 extents:1 across:9828344k 
[    9.808326] i2c i2c-0: nForce2 SMBus adapter at 0x2d00
[    9.808331] ACPI: resource nForce2_smbus [0x2e00-0x2e3f] conflicts with ACPI region SM00 [0x2e00-0x2e3f]
[    9.808333] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.808335] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    9.816369] Linux agpgart interface v0.103
[    9.834179] lp: driver loaded but no devices found
[    9.918711] [drm] Initialized drm 1.1.0 20060810
[    9.925024] type=1505 audit(1282765012.784:2):  operation="profile_load" pid=650 name="/sbin/dhclient3"
[    9.925229] type=1505 audit(1282765012.784:3):  operation="profile_load" pid=650 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.925344] type=1505 audit(1282765012.784:4):  operation="profile_load" pid=650 name="/usr/lib/connman/scripts/dhclient-script"
[    9.938896] type=1505 audit(1282765012.796:5):  operation="profile_load" pid=668 name="/usr/sbin/ntpd"
[    9.963735] nouveau 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    9.963741] nouveau 0000:02:00.0: setting latency timer to 64
[    9.966918] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x096000c1)
[    9.967531] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
[   10.016936] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   10.016970] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   10.017297] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   10.017302] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   10.017305] hda_intel: Disable MSI for Nvidia chipset
[   10.017329] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.024799] [drm] nouveau 0000:02:00.0: ... appears to be valid
[   10.024804] [drm] nouveau 0000:02:00.0: BIT BIOS found
[   10.024806] [drm] nouveau 0000:02:00.0: Bios version 62.94.29.00
[   10.024809] [drm] nouveau 0000:02:00.0: TMDS table revision 2.0 not currently supported
[   10.024812] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 4.0
[   10.024815] [drm] nouveau 0000:02:00.0: DCB connector table: VHER 0x40 5 16 4
[   10.024817] [drm] nouveau 0000:02:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   10.024819] [drm] nouveau 0000:02:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   10.024822] [drm] nouveau 0000:02:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   10.024824] [drm] nouveau 0000:02:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   10.024826] [drm] nouveau 0000:02:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   10.024828] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 02000300 00000028
[   10.024831] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 01000302 00020030
[   10.024832] [drm] nouveau 0000:02:00.0: Raw DCB entry 2: 04011310 00000028
[   10.024834] [drm] nouveau 0000:02:00.0: Raw DCB entry 3: 02011312 00020030
[   10.024836] [drm] nouveau 0000:02:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   10.024844] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xD0BE
[   10.053919] RPC: Registered udp transport module.
[   10.053921] RPC: Registered tcp transport module.
[   10.053923] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   10.084154] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xD4D3
[   10.085270] psmouse serio1: ID: 10 00 14
[   10.105108] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xE4C4
[   10.105119] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xE60D
[   10.116115] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xE849
[   10.116119] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xE8AE
[   10.138063] type=1505 audit(1282765012.996:6):  operation="profile_replace" pid=815 name="/sbin/dhclient3"
[   10.138277] type=1505 audit(1282765012.996:7):  operation="profile_replace" pid=815 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.138396] type=1505 audit(1282765012.996:8):  operation="profile_replace" pid=815 name="/usr/lib/connman/scripts/dhclient-script"
[   10.142758] [drm] nouveau 0000:02:00.0: 0xE8AE: Condition still not met after 20ms, skipping following opcodes
[   10.142768] [drm] nouveau 0000:02:00.0: 0xC090: parsing output script 0
[   10.142774] [drm] nouveau 0000:02:00.0: 0xC090: parsing output script 0
[   10.142780] [drm] nouveau 0000:02:00.0: 0xAB1C: parsing output script 0
[   10.179275] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   10.181900] type=1505 audit(1282765013.040:9):  operation="profile_load" pid=821 name="/usr/bin/evince"
[   10.188457] r8169: eth0: link up
[   10.188462] r8169: eth0: link up
[   10.190021] type=1505 audit(1282765013.048:10):  operation="profile_load" pid=821 name="/usr/bin/evince-previewer"
[   10.191674] type=1505 audit(1282765013.048:11):  operation="profile_load" pid=821 name="/usr/bin/evince-thumbnailer"
[   10.244729] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   10.258783] [TTM] Zone  kernel: Available graphics memory: 419384 kiB.
[   10.258786] [TTM] Zone highmem: Available graphics memory: 2060668 kiB.
[   10.258794] [drm] nouveau 0000:02:00.0: 1024 MiB VRAM
[   10.272525] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)
[   10.273273] [drm] nouveau 0000:02:00.0: Allocating FIFO number 1
[   10.276559] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc: initialised FIFO 1
[   10.276961] [drm] nouveau 0000:02:00.0: Detected a DAC output
[   10.276963] [drm] nouveau 0000:02:00.0: Detected a TMDS output
[   10.276965] [drm] nouveau 0000:02:00.0: Detected a DAC output
[   10.276967] [drm] nouveau 0000:02:00.0: Detected a TMDS output
[   10.276969] [drm] nouveau 0000:02:00.0: DCB encoder 1 unknown
[   10.276972] [drm] nouveau 0000:02:00.0: Detected a DVI-I connector
[   10.277025] [drm] nouveau 0000:02:00.0: Detected a DVI-I connector
[   10.454796] [drm] nouveau 0000:02:00.0: allocated 1360x768 fb: 0x40250000, bo f323d800
[   10.454869] fb0: nouveaufb frame buffer device
[   10.454871] registered panic notifier
[   10.454876] [drm] Initialized nouveau 0.0.15 20090420 for 0000:02:00.0 on minor 0
[   10.457722] vga16fb: initializing
[   10.457726] vga16fb: mapped to 0xc00a0000
[   10.457730] vga16fb: not registering due to another framebuffer present
[   10.467665] [drm] nouveau 0000:02:00.0: 0x11F1: parsing clock script 0
[   10.467737] Console: switching to colour frame buffer device 170x48
[   10.468900] svc: failed to register lockdv1 RPC service (errno 97).
[   10.470659] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   10.500513] NFSD: starting 90-second grace period
[   10.726922] CPU0 attaching NULL sched-domain.
[   10.726927] CPU1 attaching NULL sched-domain.
[   10.748055] CPU0 attaching sched-domain:
[   10.748059]  domain 0: span 0-1 level MC
[   10.748061]   groups: 0 1
[   10.748066] CPU1 attaching sched-domain:
[   10.748067]  domain 0: span 0-1 level MC
[   10.748069]   groups: 1 0
[   11.048563] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input5
[   11.195455] [drm] nouveau 0000:02:00.0: Allocating FIFO number 2
[   11.198742] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc: initialised FIFO 2
[   11.452074] input: HDA NVidia Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input6
[   11.452144] input: HDA NVidia Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input7
[   11.452184] input: HDA NVidia Mic at Sep Front Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
[   11.452229] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   11.452272] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
[   11.452315] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
[   11.452359] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
[   11.452403] input: HDA NVidia HP Out at Sep Front Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
[   20.456504] eth0: no IPv6 routers present
[   24.912511] usb 1-4: new high speed USB device using ehci_hcd and address 2
[   25.048815] usb 1-4: configuration #1 chosen from 1 choice
[   25.090912] Initializing USB Mass Storage driver...
[   25.091069] scsi8 : SCSI emulation for USB Mass Storage devices
[   25.091145] usbcore: registered new interface driver usb-storage
[   25.091147] USB Mass Storage support registered.
[   25.093227] usb-storage: device found at 2
[   25.093229] usb-storage: waiting for device to settle before scanning
[   30.092190] usb-storage: device scan complete
[   30.093673] scsi 8:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS
[   30.095311] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   30.671756] sd 8:0:0:0: [sdb] 2013184 512-byte logical blocks: (1.03 GB/983 MiB)
[   30.673261] sd 8:0:0:0: [sdb] Write Protect is off
[   30.673264] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   30.673266] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   30.676247] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   30.676251]  sdb: sdb1
[   30.679260] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   30.679264] sd 8:0:0:0: [sdb] Attached SCSI removable disk
mike [/HTML]

---

### Post by bance on 2010-08-26
Ok, it doesn't look like the device is being seen.

Open a terminal and post the output of lsusb please.

---

### Post by anoldguy on 2010-08-29
Thanks Steve for the response and help. 

Here's the results of the test with both the Technisat and my thumb drive plugged into the PC:

[HTML]h:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13d0:2282  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0930:653d Toshiba Corp. Kingston DataTraveler 2.0 Stick (1GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I removed the thumb drive and inserted the Technisat into the place where the thumb drive was connected: 

h:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d0:2282  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike[/HTML]

---

