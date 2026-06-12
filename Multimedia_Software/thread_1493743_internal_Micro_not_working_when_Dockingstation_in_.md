---
title: "internal Micro not working when Dockingstation in use"
date: 2010-05-26
forum: Multimedia Software
---

### Post by traktour on 2010-05-26
Hello,

my internal micro don't work when i use the dockingstation. external micro doesn't work to.

both the internal and the external Micros work fine when i don't use the workingstation.

any idea?
thanks :-) 

Laptop: Samsung X22
Ubuntu: 10.04

-----------------------------------------------------------------------------------------------------
[SIZE=4]**lscpi:**[/SIZE]
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
--------------------------------------------------------------------------------------------------------------------------------
[SIZE=4]**dmesg:**[/SIZE]
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 (Ubuntu 2.6.32-22.33-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37857000 - 37fefba3
[    0.000000] Allocated new RAMDISK: 008de000 - 01076ba3
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fefba2 to 008de000 - 01076ba2
[    0.000000] ACPI: RSDP 000f6cc0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7fed6228 000A4 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fedfb37 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fed8166 0795D (v02 INTEL  CRESTLNE 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: APIC 7fedfc2b 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7fedfc93 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedfccb 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7fedfd07 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 7fedfd39 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fedfd5f 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 7fedfdc7 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: BOOT 7fedfdff 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: ASF! 7fedfe27 00063 (v16   CETP     CETP 06040000 PTL  00000001)
[    0.000000] ACPI: SLIC 7fedfe8a 00176 (v01 SECCSD LH43STAR 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7fed7b17 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed7485 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed6858 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed67b2 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed62cc 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
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
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd15c]              BRK ==> [00008da000 - 00008dd15c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 0001076ba3]      NEW RAMDISK ==> [00008de000 - 0001076ba3]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f6cf0] f6cf0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1078200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294340 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519777
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=80e67a14-f519-43f2-9094-5e0653f2bafa ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2051000k/2095936k available (4673k kernel code, 43428k reserved, 2121k data, 656k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590653 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590653   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.510 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.02 BogoMIPS (lpj=8778040)
[    0.004033] Security Framework initialized
[    0.004059] AppArmor: AppArmor initialized
[    0.004069] Mount-cache hash table entries: 512
[    0.004245] Initializing cgroup subsys ns
[    0.004251] Initializing cgroup subsys cpuacct
[    0.004258] Initializing cgroup subsys memory
[    0.004269] Initializing cgroup subsys devices
[    0.004272] Initializing cgroup subsys freezer
[    0.004277] Initializing cgroup subsys net_cls
[    0.004306] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004310] CPU: L2 cache: 4096K
[    0.004315] CPU: Physical Processor ID: 0
[    0.004318] CPU: Processor Core ID: 0
[    0.004324] mce: CPU supports 6 MCE banks
[    0.004337] CPU0: Thermal monitoring enabled (TM2)
[    0.004342] using mwait in idle threads.
[    0.004351] Performance Events: Core2 events, Intel PMU driver.
[    0.004364] ... version:                2
[    0.004367] ... bit width:              40
[    0.004370] ... generic registers:      2
[    0.004373] ... value mask:             000000ffffffffff
[    0.004377] ... max period:             000000007fffffff
[    0.004380] ... fixed-purpose events:   3
[    0.004383] ... event mask:             0000000700000003
[    0.004389] Checking 'hlt' instruction... OK.
[    0.024357] ACPI: Core revision 20090903
[    0.040014] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040022] ftrace: allocating 21771 entries in 43 pages
[    0.044067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044440] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085679] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 4096K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.172123] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.172141] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176024] Brought up 2 CPUs
[    0.176029] Total of 2 processors activated (8778.02 BogoMIPS).
[    0.177009] CPU0 attaching sched-domain:
[    0.177014]  domain 0: span 0-1 level MC
[    0.177019]   groups: 0 1
[    0.177028] CPU1 attaching sched-domain:
[    0.177032]  domain 0: span 0-1 level MC
[    0.177036]   groups: 1 0
[    0.177172] devtmpfs: initialized
[    0.177172] regulator: core version 0.5
[    0.177172] Time: 12:30:50  Date: 05/26/10
[    0.177172] NET: Registered protocol family 16
[    0.177172] Trying to unpack rootfs image as initramfs...
[    0.177172] EISA bus registered
[    0.177172] ACPI: bus type pci registered
[    0.177172] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.177172] PCI: MCFG area at e0000000 reserved in E820
[    0.177172] PCI: Using MMCONFIG for extended config space
[    0.177172] PCI: Using configuration type 1 for base access
[    0.180158] bio: create slab <bio-0> at 0
[    0.181793] ACPI: EC: Look up EC in DSDT
[    0.186126] ACPI: BIOS _OSI(Linux) query ignored
[    0.188396] ACPI: Interpreter enabled
[    0.188396] ACPI: (supports S0 S3 S4 S5)
[    0.188396] ACPI: Using IOAPIC for interrupt routing
[    0.188793] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.197507] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.197507] ACPI: Power Resource [FN00] (off)
[    0.200356] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.201228] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.201409] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.201415] pci 0000:00:01.0: PME# disabled
[    0.201523] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.201601] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.201688] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc304000-0xfc3043ff]
[    0.201766] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.201774] pci 0000:00:1a.7: PME# disabled
[    0.201840] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc300000-0xfc303fff]
[    0.201911] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.201918] pci 0000:00:1b.0: PME# disabled
[    0.202028] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.202035] pci 0000:00:1c.0: PME# disabled
[    0.202147] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.202154] pci 0000:00:1c.1: PME# disabled
[    0.202267] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.202274] pci 0000:00:1c.2: PME# disabled
[    0.202387] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.202394] pci 0000:00:1c.3: PME# disabled
[    0.202513] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.202520] pci 0000:00:1c.4: PME# disabled
[    0.202632] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.202639] pci 0000:00:1c.5: PME# disabled
[    0.202716] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.202798] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.202888] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.202978] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc304400-0xfc3047ff]
[    0.203055] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.203062] pci 0000:00:1d.7: PME# disabled
[    0.203269] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.203276] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.203283] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.203290] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.203377] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.203388] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.203400] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.203411] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.203422] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ef]
[    0.203434] pci 0000:00:1f.2: reg 24 io port: [0x18d0-0x18df]
[    0.203471] pci 0000:00:1f.2: PME# supported from D3hot
[    0.203478] pci 0000:00:1f.2: PME# disabled
[    0.203512] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.203542] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.203616] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.203626] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.203636] pci 0000:01:00.0: reg 18 32bit mmio: [0xfc000000-0xfc00ffff]
[    0.203661] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.203691] pci 0000:01:00.0: supports D1 D2
[    0.203738] pci 0000:01:00.1: reg 10 32bit mmio: [0xfc010000-0xfc013fff]
[    0.203799] pci 0000:01:00.1: supports D1 D2
[    0.203877] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.203883] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfc0fffff]
[    0.203892] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.204172] pci 0000:02:00.0: reg 10 64bit mmio: [0xca000000-0xca00ffff]
[    0.204469] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.204486] pci 0000:02:00.0: PME# disabled
[    0.204628] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.204636] pci 0000:00:1c.0: bridge 32bit mmio: [0xca000000-0xcbffffff]
[    0.204647] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xde000000-0xdfffffff]
[    0.204844] pci 0000:04:00.0: reg 10 32bit mmio: [0xfa000000-0xfa000fff]
[    0.205102] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.205117] pci 0000:04:00.0: PME# disabled
[    0.205241] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.205249] pci 0000:00:1c.1: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.205260] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf8000000-0xf9ffffff]
[    0.205327] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.205335] pci 0000:00:1c.2: bridge 32bit mmio: [0xc6000000-0xc7ffffff]
[    0.205346] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xda000000-0xdbffffff]
[    0.205456] pci 0000:08:00.0: reg 10 64bit mmio: [0xc2000000-0xc2003fff]
[    0.205471] pci 0000:08:00.0: reg 18 io port: [0x6000-0x60ff]
[    0.205519] pci 0000:08:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.205593] pci 0000:08:00.0: supports D1 D2
[    0.205597] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205606] pci 0000:08:00.0: PME# disabled
[    0.205683] pci 0000:00:1c.3: bridge io port: [0x6000-0x6fff]
[    0.205690] pci 0000:00:1c.3: bridge 32bit mmio: [0xc2000000-0xc3ffffff]
[    0.205702] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd6000000-0xd7ffffff]
[    0.205773] pci 0000:00:1c.4: bridge io port: [0x7000-0x7fff]
[    0.205780] pci 0000:00:1c.4: bridge 32bit mmio: [0xbe000000-0xbfffffff]
[    0.205791] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd2000000-0xd3ffffff]
[    0.205860] pci 0000:00:1c.5: bridge io port: [0x8000-0x8fff]
[    0.205868] pci 0000:00:1c.5: bridge 32bit mmio: [0xba000000-0xbbffffff]
[    0.205879] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xce000000-0xcfffffff]
[    0.205966] pci 0000:00:1e.0: transparent bridge
[    0.206034] pci_bus 0000:00: on NUMA node 0
[    0.206042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.206488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.206645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.206785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.206924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.207061] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.207199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.207382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.207437] ACPI Warning for \_SB_.PCI0.PCIB._PRT: Return Package has no elements (empty) (20090903/nspredef-433)
[    0.226522] ACPI: PCI Interrupt Link [LNKA] (IRQs 11) *10
[    0.226684] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.226841] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[    0.226996] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[    0.227150] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.227306] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    0.227461] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.227615] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    0.227798] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.227807] vgaarb: loaded
[    0.228009] SCSI subsystem initialized
[    0.240084] libata version 3.00 loaded.
[    0.240201] usbcore: registered new interface driver usbfs
[    0.240223] usbcore: registered new interface driver hub
[    0.240263] usbcore: registered new device driver usb
[    0.240478] ACPI: WMI: Mapper loaded
[    0.240482] PCI: Using ACPI for IRQ routing
[    0.240951] NetLabel: Initializing
[    0.240954] NetLabel:  domain hash size = 128
[    0.240957] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.240977] NetLabel:  unlabeled traffic allowed by default
[    0.241033] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.241042] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244360] Switching to clocksource tsc
[    0.247360] AppArmor: AppArmor Filesystem Enabled
[    0.247376] pnp: PnP ACPI init
[    0.247391] ACPI: bus type pnp registered
[    0.252474] pnp: PnP ACPI: found 12 devices
[    0.252479] ACPI: ACPI bus type pnp unregistered
[    0.252486] PnPBIOS: Disabled by ACPI PNP
[    0.252504] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.252509] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.252514] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.252520] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.252525] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.252530] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.252535] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.252540] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.252552] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.252563] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.252568] system 00:06: ioport range 0x900-0x90f has been reserved
[    0.252574] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.252578] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.252584] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.287490] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.287496] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.287504] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfc0fffff
[    0.287510] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.287519] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.287524] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.287533] pci 0000:00:1c.0:   MEM window: 0xca000000-0xcbffffff
[    0.287541] pci 0000:00:1c.0:   PREFETCH window: 0x000000de000000-0x000000dfffffff
[    0.287552] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.287557] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.287566] pci 0000:00:1c.1:   MEM window: 0xfa000000-0xfbffffff
[    0.287574] pci 0000:00:1c.1:   PREFETCH window: 0x000000f8000000-0x000000f9ffffff
[    0.287585] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.287590] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.287599] pci 0000:00:1c.2:   MEM window: 0xc6000000-0xc7ffffff
[    0.287607] pci 0000:00:1c.2:   PREFETCH window: 0x000000da000000-0x000000dbffffff
[    0.287618] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:08
[    0.287624] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.287633] pci 0000:00:1c.3:   MEM window: 0xc2000000-0xc3ffffff
[    0.287640] pci 0000:00:1c.3:   PREFETCH window: 0x000000d6000000-0x000000d7ffffff
[    0.287651] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0a
[    0.287657] pci 0000:00:1c.4:   IO window: 0x7000-0x7fff
[    0.287666] pci 0000:00:1c.4:   MEM window: 0xbe000000-0xbfffffff
[    0.287673] pci 0000:00:1c.4:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    0.287684] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:0c
[    0.287690] pci 0000:00:1c.5:   IO window: 0x8000-0x8fff
[    0.287698] pci 0000:00:1c.5:   MEM window: 0xba000000-0xbbffffff
[    0.287706] pci 0000:00:1c.5:   PREFETCH window: 0x000000ce000000-0x000000cfffffff
[    0.287717] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0e
[    0.287721] pci 0000:00:1e.0:   IO window: disabled
[    0.287728] pci 0000:00:1e.0:   MEM window: disabled
[    0.287735] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.287759]   alloc irq_desc for 16 on node -1
[    0.287762]   alloc kstat_irqs on node -1
[    0.287772] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.287779] pci 0000:00:01.0: setting latency timer to 64
[    0.287893] pci 0000:00:1c.0: power state changed by ACPI to D0
[    0.287902]   alloc irq_desc for 17 on node -1
[    0.287905]   alloc kstat_irqs on node -1
[    0.287912] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.287920] pci 0000:00:1c.0: setting latency timer to 64
[    0.287934] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.287941] pci 0000:00:1c.1: setting latency timer to 64
[    0.287954]   alloc irq_desc for 18 on node -1
[    0.287957]   alloc kstat_irqs on node -1
[    0.287963] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.287971] pci 0000:00:1c.2: setting latency timer to 64
[    0.287984]   alloc irq_desc for 19 on node -1
[    0.287987]   alloc kstat_irqs on node -1
[    0.287993] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.288000] pci 0000:00:1c.3: setting latency timer to 64
[    0.288014] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.288021] pci 0000:00:1c.4: setting latency timer to 64
[    0.288034] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.288042] pci 0000:00:1c.5: setting latency timer to 64
[    0.288053] pci 0000:00:1e.0: setting latency timer to 64
[    0.288060] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.288065] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.288069] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.288074] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfc0fffff]
[    0.288078] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.288083] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.288087] pci_bus 0000:02: resource 1 mem: [0xca000000-0xcbffffff]
[    0.288092] pci_bus 0000:02: resource 2 pref mem [0xde000000-0xdfffffff]
[    0.288096] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.288101] pci_bus 0000:04: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.288105] pci_bus 0000:04: resource 2 pref mem [0xf8000000-0xf9ffffff]
[    0.288109] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.288114] pci_bus 0000:06: resource 1 mem: [0xc6000000-0xc7ffffff]
[    0.288118] pci_bus 0000:06: resource 2 pref mem [0xda000000-0xdbffffff]
[    0.288122] pci_bus 0000:08: resource 0 io:  [0x6000-0x6fff]
[    0.288127] pci_bus 0000:08: resource 1 mem: [0xc2000000-0xc3ffffff]
[    0.288131] pci_bus 0000:08: resource 2 pref mem [0xd6000000-0xd7ffffff]
[    0.288135] pci_bus 0000:0a: resource 0 io:  [0x7000-0x7fff]
[    0.288139] pci_bus 0000:0a: resource 1 mem: [0xbe000000-0xbfffffff]
[    0.288144] pci_bus 0000:0a: resource 2 pref mem [0xd2000000-0xd3ffffff]
[    0.288148] pci_bus 0000:0c: resource 0 io:  [0x8000-0x8fff]
[    0.288152] pci_bus 0000:0c: resource 1 mem: [0xba000000-0xbbffffff]
[    0.288157] pci_bus 0000:0c: resource 2 pref mem [0xce000000-0xcfffffff]
[    0.288161] pci_bus 0000:0e: resource 3 io:  [0x00-0xffff]
[    0.288165] pci_bus 0000:0e: resource 4 mem: [0x000000-0xffffffff]
[    0.288223] NET: Registered protocol family 2
[    0.288375] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.288875] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.289456] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.289727] TCP: Hash tables configured (established 131072 bind 65536)
[    0.289731] TCP reno registered
[    0.289848] NET: Registered protocol family 1
[    0.290043] pci 0000:01:00.0: Boot video device
[    0.290085] Simple Boot Flag at 0x36 set to 0x1
[    0.290355] cpufreq-nforce2: No nForce2 chipset.
[    0.290397] Scanning for low memory corruption every 60 seconds
[    0.290554] audit: initializing netlink socket (disabled)
[    0.290569] type=2000 audit(1274877050.286:1): initialized
[    0.307272] highmem bounce pool size: 64 pages
[    0.307280] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.309827] VFS: Disk quotas dquot_6.5.2
[    0.309920] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.310859] fuse init (API version 7.13)
[    0.310998] msgmni has been set to 1690
[    0.311322] alg: No test for stdrng (krng)
[    0.311410] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.311415] io scheduler noop registered
[    0.311418] io scheduler anticipatory registered
[    0.311421] io scheduler deadline registered
[    0.311486] io scheduler cfq registered (default)
[    0.311722]   alloc irq_desc for 24 on node -1
[    0.311725]   alloc kstat_irqs on node -1
[    0.311738] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.311748] pcieport 0000:00:01.0: setting latency timer to 64
[    0.311939]   alloc irq_desc for 25 on node -1
[    0.311942]   alloc kstat_irqs on node -1
[    0.311954] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.311969] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.312180]   alloc irq_desc for 26 on node -1
[    0.312183]   alloc kstat_irqs on node -1
[    0.312195] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.312210] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.312419]   alloc irq_desc for 27 on node -1
[    0.312422]   alloc kstat_irqs on node -1
[    0.312434] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.312449] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.312664]   alloc irq_desc for 28 on node -1
[    0.312667]   alloc kstat_irqs on node -1
[    0.312679] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.312694] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.312905]   alloc irq_desc for 29 on node -1
[    0.312908]   alloc kstat_irqs on node -1
[    0.312920] pcieport 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.312935] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.313146]   alloc irq_desc for 30 on node -1
[    0.313149]   alloc kstat_irqs on node -1
[    0.313162] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.313176] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.313333] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.313654] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.313981] ACPI: AC Adapter [ADP1] (on-line)
[    0.314123] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.314188] ACPI: Lid Switch [LID0]
[    0.314259] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.314268] ACPI: Power Button [PWRB]
[    0.314337] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.314342] ACPI: Sleep Button [SLPB]
[    0.314412] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.314416] ACPI: Power Button [PWRF]
[    0.314599] fan PNP0C0B:00: registered as cooling_device0
[    0.314608] ACPI: Fan [FAN0] (off)
[    0.315694] ACPI: SSDT 7fed70d7 002E6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.316509] ACPI: SSDT 7fed6ab7 0059B (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.320142] Monitor-Mwait will be used to enter C-1 state
[    0.320189] Monitor-Mwait will be used to enter C-2 state
[    0.320200] Marking TSC unstable due to TSC halts in idle
[    0.320271] processor LNXCPU:00: registered as cooling_device1
[    0.320827] ACPI: SSDT 7fed73bd 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.321399] ACPI: SSDT 7fed7052 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.322258] Switching to clocksource hpet
[    0.323130] processor LNXCPU:01: registered as cooling_device2
[    0.328619] thermal LNXTHERM:01: registered as thermal_zone0
[    0.328633] ACPI: Thermal Zone [TZ00] (55 C)
[    0.329163] thermal LNXTHERM:02: registered as thermal_zone1
[    0.329176] ACPI: Thermal Zone [TZ01] (55 C)
[    0.331600] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.331806] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.332396] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.334151] brd: module loaded
[    0.334930] loop: module loaded
[    0.335053] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.335193] ata_piix 0000:00:1f.2: version 2.13
[    0.335219] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.335227] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.335573] isapnp: Scanning for PnP cards...
[    0.397467] ACPI: Battery Slot [BAT1] (battery present)
[    0.504574] Freeing initrd memory: 7778k freed
[    0.509283] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.509434] scsi0 : ata_piix
[    0.509604] scsi1 : ata_piix
[    0.511217] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18e0 irq 14
[    0.511222] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18e8 irq 15
[    0.511792] Fixed MDIO Bus: probed
[    0.511849] PPP generic driver version 2.4.2
[    0.511943] tun: Universal TUN/TAP device driver, 1.6
[    0.511946] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.512123] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.512165] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.512192] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.512197] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.512252] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.512295] ehci_hcd 0000:00:1a.7: debug port 1
[    0.516201] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.516996] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc304000
[    0.532019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.532159] usb usb1: configuration #1 chosen from 1 choice
[    0.532204] hub 1-0:1.0: USB hub found
[    0.532215] hub 1-0:1.0: 4 ports detected
[    0.532304]   alloc irq_desc for 23 on node -1
[    0.532308]   alloc kstat_irqs on node -1
[    0.532317] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.532332] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.532338] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.532388] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.532428] ehci_hcd 0000:00:1d.7: debug port 1
[    0.536313] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.536332] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc304400
[    0.552018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.552131] usb usb2: configuration #1 chosen from 1 choice
[    0.552177] hub 2-0:1.0: USB hub found
[    0.552188] hub 2-0:1.0: 6 ports detected
[    0.552275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.552300] uhci_hcd: USB Universal Host Controller Interface driver
[    0.552330] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.552341] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.552346] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.552403] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.552449] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.552592] usb usb3: configuration #1 chosen from 1 choice
[    0.552634] hub 3-0:1.0: USB hub found
[    0.552644] hub 3-0:1.0: 2 ports detected
[    0.552714]   alloc irq_desc for 21 on node -1
[    0.552717]   alloc kstat_irqs on node -1
[    0.552725] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.552735] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.552740] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.552788] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.552831] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.552975] usb usb4: configuration #1 chosen from 1 choice
[    0.553016] hub 4-0:1.0: USB hub found
[    0.553027] hub 4-0:1.0: 2 ports detected
[    0.553098] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.553107] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.553113] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.553161] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.553195] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.553336] usb usb5: configuration #1 chosen from 1 choice
[    0.553377] hub 5-0:1.0: USB hub found
[    0.553388] hub 5-0:1.0: 2 ports detected
[    0.553461] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.553471] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.553476] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.553524] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.553568] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.553709] usb usb6: configuration #1 chosen from 1 choice
[    0.553751] hub 6-0:1.0: USB hub found
[    0.553761] hub 6-0:1.0: 2 ports detected
[    0.553829] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.553839] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.553844] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.553896] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.553929] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.554072] usb usb7: configuration #1 chosen from 1 choice
[    0.554113] hub 7-0:1.0: USB hub found
[    0.554123] hub 7-0:1.0: 2 ports detected
[    0.554282] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.556745] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.558344] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.558355] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.558398] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.558434] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.558470] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.558645] mice: PS/2 mouse device common for all mice
[    0.558972] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.559011] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.559171] device-mapper: uevent: version 1.0.3
[    0.559318] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.559421] device-mapper: multipath: version 1.1.0 loaded
[    0.559425] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.559604] EISA: Probing bus 0 at eisa.0
[    0.559612] Cannot allocate resource for EISA slot 1
[    0.559616] Cannot allocate resource for EISA slot 2
[    0.559620] Cannot allocate resource for EISA slot 3
[    0.559623] Cannot allocate resource for EISA slot 4
[    0.559627] Cannot allocate resource for EISA slot 5
[    0.559630] Cannot allocate resource for EISA slot 6
[    0.559634] Cannot allocate resource for EISA slot 7
[    0.559637] Cannot allocate resource for EISA slot 8
[    0.559640] EISA: Detected 0 cards.
[    0.559843] cpuidle: using governor ladder
[    0.559986] cpuidle: using governor menu
[    0.560719] TCP cubic registered
[    0.560969] NET: Registered protocol family 10
[    0.561722] lo: Disabled Privacy Extensions
[    0.562297] NET: Registered protocol family 17
[    0.563077] Using IPI No-Shortcut mode
[    0.563179] PM: Resume from disk failed.
[    0.563190] registered taskstats version 1
[    0.563982]   Magic number: 10:696:532
[    0.563994] bdi 1:10: hash matches
[    0.564147] rtc_cmos 00:07: setting system clock to 2010-05-26 12:30:51 UTC (1274877051)
[    0.564150] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.564151] EDD information not available.
[    0.584100] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.677594] ata1.00: ATA-8: FUJITSU MHY2200BH, 0000000B, max UDMA/100
[    0.677598] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.677699] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L632H, SC03, max UDMA/33
[    0.685325] ata1.00: configured for UDMA/100
[    0.690053] isapnp: No Plug & Play device found
[    0.690168] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2200B 0000 PQ: 0 ANSI: 5
[    0.690275] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    0.690280] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.690316] sd 0:0:0:0: [sda] Write Protect is off
[    0.690318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.690339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.690454]  sda: sda1 sda2 sda3 sda4 <
[    0.693306] ata2.00: configured for UDMA/33
[    0.699303] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  SC03 PQ: 0 ANSI: 5
[    0.712057]  sda5sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.715782] Uniform CD-ROM driver Revision: 3.20
[    0.715915] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.715982] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.719746]  sda6 >
[    0.720169] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.720188] Freeing unused kernel memory: 656k freed
[    0.720568] Write protecting the kernel text: 4676k
[    0.720609] Write protecting the kernel read-only data: 1840k
[    0.735430] udev: starting version 151
[    0.801162] sky2 driver version 1.25
[    0.801211] sky2 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.801228] sky2 0000:08:00.0: setting latency timer to 64
[    0.801260] sky2 0000:08:00.0: Yukon-2 EC Ultra chip revision 3
[    0.801707]   alloc irq_desc for 31 on node -1
[    0.801709]   alloc kstat_irqs on node -1
[    0.801781] sky2 0000:08:00.0: irq 31 for MSI/MSI-X
[    0.806359] sky2 eth0: addr 00:13:77:68:da:13
[    0.825374] tg3.c:v3.102 (September 1, 2009)
[    0.825454] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.825472] tg3 0000:02:00.0: setting latency timer to 64
[    0.851000] eth1: Tigon3 [partno(BCM95751m) rev 4201] (PCI Express) MAC address 00:00:f0:95:92:a7
[    0.851004] eth1: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    0.851007] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    0.851009] eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[    0.856057] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.034814] usb 1-2: configuration #1 chosen from 1 choice
[    1.144111] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.276500] usb 2-4: configuration #1 chosen from 1 choice
[    1.276875] hub 2-4:1.0: USB hub found
[    1.277006] hub 2-4:1.0: 4 ports detected
[    1.341796] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    1.632039] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    1.807107] usb 7-2: configuration #1 chosen from 1 choice
[    1.896143] usb 2-4.1: new low speed USB device using ehci_hcd and address 4
[    2.009379] usb 2-4.1: configuration #1 chosen from 1 choice
[    2.096150] usb 2-4.3: new low speed USB device using ehci_hcd and address 5
[    2.192908] usb 2-4.3: configuration #1 chosen from 1 choice
[   18.759813] udev: starting version 151
[   18.830844] Adding 3068344k swap on /dev/sda5.  Priority:-1 extents:1 across:3068344k 
[   18.838620] lp: driver loaded but no devices found
[   18.890161] Linux agpgart interface v0.103
[   19.013602] vga16fb: initializing
[   19.013606] vga16fb: mapped to 0xc00a0000
[   19.013661] fb0: VGA16 VGA frame buffer device
[   19.102235] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   19.102239] Disabling lock debugging due to kernel taint
[   19.121180] cfg80211: Calling CRDA to update world regulatory domain
[   19.175329] type=1505 audit(1274869870.107:2):  operation="profile_load" pid=649 name="/sbin/dhclient3"
[   19.175956] type=1505 audit(1274869870.107:3):  operation="profile_load" pid=649 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.176291] type=1505 audit(1274869870.111:4):  operation="profile_load" pid=649 name="/usr/lib/connman/scripts/dhclient-script"
[   19.181714] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   19.183327] acpi device:03: registered as cooling_device3
[   19.183935] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   19.184045] ACPI: Video Device [ATIM] (multi-head: yes  rom: no  post: no)
[   19.209688] [fglrx] Maximum main memory to use for locked dma buffers: 1885 MBytes.
[   19.210004] [fglrx]   vendor: 1002 device: 94c9 count: 1
[   19.210506] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   19.210522] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.210527] pci 0000:01:00.0: setting latency timer to 64
[   19.210741] [fglrx] Kernel PAT support is enabled
[   19.210760] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   19.227601] cfg80211: World regulatory domain updated:
[   19.227604]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.227607]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.227609]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.227612]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.227614]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.227616]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.230387] Linux video capture interface: v2.00
[   19.234498] uvcvideo: Found UVC 1.00 device Vega USB 2.0 Camera. (0ac8:c302)
[   19.234573] Bluetooth: Core ver 2.15
[   19.234614] NET: Registered protocol family 31
[   19.234616] Bluetooth: HCI device and connection manager initialized
[   19.234618] Bluetooth: HCI socket layer initialized
[   19.236144] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.236243] usbcore: registered new interface driver btusb
[   19.239179] parport_pc 00:09: reported by Plug and Play ACPI
[   19.239254] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.246527] input: Vega USB 2.0 Camera. as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7
[   19.246578] usbcore: registered new interface driver uvcvideo
[   19.246581] USB Video Class driver (v0.1.0)
[   19.253015] usbcore: registered new interface driver hiddev
[   19.256732] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.3/2-4.3:1.0/input/input8
[   19.256821] generic-usb 0003:046D:C069.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1d.7-4.3/input0
[   19.256841] usbcore: registered new interface driver usbhid
[   19.256843] usbhid: v2.6:USB HID core driver
[   19.303896] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.303898] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.304044] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.304060] iwl3945 0000:04:00.0: setting latency timer to 64
[   19.306978] input: HID 046a:0023 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.0/input/input9
[   19.307071] cherry 0003:046A:0023.0001: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0023] on usb-0000:00:1d.7-4.1/input0
[   19.328107] input: HID 046a:0023 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4.1/2-4.1:1.1/input/input10
[   19.328189] cherry 0003:046A:0023.0002: input,hidraw2: USB HID v1.11 Device [HID 046a:0023] on usb-0000:00:1d.7-4.1/input1
[   19.345183] lp0: using parport0 (interrupt-driven).
[   19.374824] ppdev: user-space parallel port driver
[   19.443016] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.443019] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.443135]   alloc irq_desc for 32 on node -1
[   19.443137]   alloc kstat_irqs on node -1
[   19.443170] iwl3945 0000:04:00.0: irq 32 for MSI/MSI-X
[   19.474674] Console: switching to colour frame buffer device 80x30
[   19.494389]   alloc irq_desc for 22 on node -1
[   19.494392]   alloc kstat_irqs on node -1
[   19.494399] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.494446] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.495968] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.605367] hda_codec: ALC262: BIOS auto-probing.
[   19.606509] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   19.619035] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.619075] HDA Intel 0000:01:00.1: setting latency timer to 64
[   19.997760] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x200000
[   20.034350] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[   20.247022] type=1505 audit(1274869871.180:5):  operation="profile_load" pid=979 name="/usr/share/gdm/guest-session/Xsession"
[   20.248667] type=1505 audit(1274869871.180:6):  operation="profile_replace" pid=981 name="/sbin/dhclient3"
[   20.249306] type=1505 audit(1274869871.184:7):  operation="profile_replace" pid=981 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.249649] type=1505 audit(1274869871.184:8):  operation="profile_replace" pid=981 name="/usr/lib/connman/scripts/dhclient-script"
[   20.253002] type=1505 audit(1274869871.184:9):  operation="profile_load" pid=983 name="/usr/bin/evince"
[   20.261118] type=1505 audit(1274869871.196:10):  operation="profile_load" pid=983 name="/usr/bin/evince-previewer"
[   20.266071] type=1505 audit(1274869871.200:11):  operation="profile_load" pid=983 name="/usr/bin/evince-thumbnailer"
[   20.379171]   alloc irq_desc for 33 on node -1
[   20.379175]   alloc kstat_irqs on node -1
[   20.379213] tg3 0000:02:00.0: irq 33 for MSI/MSI-X
[   20.417204] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   20.438610] iwl3945 0000:04:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   20.462581] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   20.546199] Registered led device: iwl-phy0::radio
[   20.546421] Registered led device: iwl-phy0::assoc
[   20.546473] Registered led device: iwl-phy0::RX
[   20.546647] Registered led device: iwl-phy0::TX
[   20.557971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.562826] sky2 eth0: enabling interface
[   20.565658] ADDRCONF(NETDEV_UP): eth0: link is not ready
----------------------------------------------------------------------------------------------------------------------------------
[SIZE=4]**alsa-info.sh:**[/SIZE]
name=maalej&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed May 26 10:57:23 UTC 2010


!!Linux Distribution
!!------------------




!!DMI Information
!!---------------

Manufacturer:      SAMSUNG ELECTRONICS CO., LTD.
Product Name:      SX22S


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       No


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfc010000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 03)
    Subsystem: 144d:c033
--
01:00.1 0403: 1002:aa10
    Subsystem: 144d:c033


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
-ne     
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne     
enable_msi : 0
-ne     
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne     
power_save : 0
-ne     
power_save_controller : Y
-ne     
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
-ne     
single_cmd : N

!!Module: snd_hda_intel
-ne     
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
-ne     
enable_msi : 0
-ne     
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne     
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
-ne     
power_save : 0
-ne     
power_save_controller : Y
-ne     
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
-ne     
probe_only : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
-ne     
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC262
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0262
Subsystem Id: 0x144dc033
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=4, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1c 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x07 0x07]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00]
  Connection: 2
     0x02 0x0b
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x99a30931: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181303f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4014810d: [N/A] Speaker at Ext N/A
    Conn = RCA, Color = Purple
    DefAssociation = 0x0, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01454120: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x00
  Coefficient Index: 0x0c
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono
  Volume-Knob: delta=0, steps=32, direct=0, val=64
  Unsolicited: tag=00, enabled=0
  Connection: 0
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 9
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x2118144d
Revision Id: 0x100200
Modem Function Group: 0x1
Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--
-------------------------------------------------------------------------------------------------------------------------------------

---

