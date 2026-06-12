---
title: "linksys wusb100 v2 issue"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Fr Ted on 2010-11-20
Hi, new to ubuntu and having difficultly connecting to my wireless router.

It can see the router but will not connect keeps asking for password.

usb adapter is working 100% as i can connect with it using xp 64bit

here is my ubuntu enviorment

ted@ted-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9714
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
ted@ted-laptop:~$ 


ted@ted-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 (Ubuntu 2.6.32-25.45-generic 2.6.32.21+drm33.7)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfed0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x100000
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
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  modified: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
[    0.000000]  modified: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfed0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37857000 - 37fef4c1
[    0.000000] Allocated new RAMDISK: 008e1000 - 010794c1
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef4c0 to 008e1000 - 010794c0
[    0.000000] ACPI: RSDP 000fba90 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT cfe90100 0005C (v01 082410 XSDT1918 20100824 MSFT 00000097)
[    0.000000] ACPI: FACP cfe90290 000F4 (v03 082410 FACP1918 20100824 MSFT 00000097)
[    0.000000] ACPI: DSDT cfe90450 0F1F1 (v01  A1504 A1504000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS cfea8000 00040
[    0.000000] ACPI: APIC cfe90390 0007C (v01 082410 APIC1918 20100824 MSFT 00000097)
[    0.000000] ACPI: MCFG cfe90410 0003C (v01 082410 OEMMCFG  20100824 MSFT 00000097)
[    0.000000] ACPI: OEMB cfea8040 00072 (v01 082410 OEMB1918 20100824 MSFT 00000097)
[    0.000000] ACPI: SRAT cfe9f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET cfe9f990 00038 (v01 082410 OEMHPET  20100824 MSFT 00000097)
[    0.000000] ACPI: SSDT cfe9f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2438MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e026d]              BRK ==> [00008dd000 - 00008e026d]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e1000 - 00010794c1]      NEW RAMDISK ==> [00008e1000 - 00010794c1]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cfe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfe90
[    0.000000] On node 0 totalpages: 851487
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c107b200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4878 pages used for memmap
[    0.000000]   HighMem zone: 619396 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:2ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u524288
[    0.000000] pcpu-alloc: s36056 r0 d21288 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 844833
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-25-generic root=UUID=13f74c2e-21bb-41ba-a260-9374155cb7ea ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 17031680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000cfe90)
[    0.000000] Memory: 3344280k/3406400k available (4680k kernel code, 60328k reserved, 2122k data, 656k init, 2497096k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592317 - 0xc07a4e68   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592317   (4680 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:456
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3110.420 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6220.84 BogoMIPS (lpj=12441680)
[    0.004064] Security Framework initialized
[    0.004099] AppArmor: AppArmor initialized
[    0.004129] Mount-cache hash table entries: 512
[    0.004222] Initializing cgroup subsys ns
[    0.004249] Initializing cgroup subsys cpuacct
[    0.004276] Initializing cgroup subsys memory
[    0.004304] Initializing cgroup subsys devices
[    0.004331] Initializing cgroup subsys freezer
[    0.004357] Initializing cgroup subsys net_cls
[    0.004391] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004419] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004445] CPU: Physical Processor ID: 0
[    0.004471] CPU: Processor Core ID: 0
[    0.004498] mce: CPU supports 6 MCE banks
[    0.004528] using C1E aware idle routine
[    0.004556] Performance Events: AMD PMU driver.
[    0.004606] ... version:                0
[    0.004633] ... bit width:              48
[    0.004658] ... generic registers:      4
[    0.004684] ... value mask:             0000ffffffffffff
[    0.004711] ... max period:             00007fffffffffff
[    0.004737] ... fixed-purpose events:   0
[    0.004763] ... event mask:             000000000000000f
[    0.004790] Checking 'hlt' instruction... OK.
[    0.021466] ACPI: Core revision 20090903
[    0.036006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036034] ftrace: allocating 21789 entries in 43 pages
[    0.040055] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040339] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080279] CPU0: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.168093] CPU1: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.168292] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172017] System has AMD C1E enabled
[    0.172051] Switch to broadcast mode on CPU1
[    0.172096] Booting processor 2 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 2
[    0.260037] CPU2: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.260244] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.264018] Switch to broadcast mode on CPU2
[    0.264073] Booting processor 3 APIC 0x3 ip 0x6000
[    0.008000] Initializing CPU#3
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 3
[    0.352045] CPU3: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.352258] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.356019] Brought up 4 CPUs
[    0.356018] Switch to broadcast mode on CPU3
[    0.356070] Total of 4 processors activated (24883.40 BogoMIPS).
[    0.356361] CPU0 attaching sched-domain:
[    0.356363]  domain 0: span 0-3 level MC
[    0.356365]   groups: 0 1 2 3
[    0.356369] CPU1 attaching sched-domain:
[    0.356371]  domain 0: span 0-3 level MC
[    0.356372]   groups: 1 2 3 0
[    0.356375] CPU2 attaching sched-domain:
[    0.356376]  domain 0: span 0-3 level MC
[    0.356378]   groups: 2 3 0 1
[    0.356381] CPU3 attaching sched-domain:
[    0.356382]  domain 0: span 0-3 level MC
[    0.356383]   groups: 3 0 1 2
[    0.356455] Switch to broadcast mode on CPU0
[    0.356455] devtmpfs: initialized
[    0.356455] regulator: core version 0.5
[    0.356455] Time:  9:59:08  Date: 11/20/10
[    0.356455] NET: Registered protocol family 16
[    0.356455] EISA bus registered
[    0.356455] Trying to unpack rootfs image as initramfs...
[    0.356455] ACPI: bus type pci registered
[    0.356455] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.356455] PCI: Not using MMCONFIG.
[    0.357006] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.357033] PCI: Using configuration type 1 for base access
[    0.357059] PCI: Using configuration type 1 for extended access
[    0.357540] bio: create slab <bio-0> at 0
[    0.357619] ACPI: EC: Look up EC in DSDT
[    0.357619] ACPI Error (dswload-0781): [PRID] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.360033] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
[    0.360107] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node c08d1804), AE_ALREADY_EXISTS
[    0.360203] ACPI: Marking method \___ as Serialized because of AE_ALREADY_EXISTS error
[    0.360284] ACPI Error (dswload-0659): [PCI0] Namespace lookup failure, AE_NOT_FOUND
[    0.360357] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20090903/psloop-230)
[    0.360431] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node c08d1804), AE_NOT_FOUND
[    0.360561] ACPI: Executed 3 blocks of module-level executable AML code
[    0.466743] ACPI: Interpreter enabled
[    0.466801] ACPI: (supports S0 S1 S3 S4 S5)
[    0.466951] ACPI: Using IOAPIC for interrupt routing
[    0.467018] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.469991] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.470052] PCI: Using MMCONFIG for extended config space
[    0.475509] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.475633] ACPI Warning: Incorrect checksum in table [OEMB] - C2, should be C1 (20090903/tbutils-314)
[    0.475812] ACPI: No dock devices found.
[    0.475986] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.476101] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.476129] pci 0000:00:0a.0: PME# disabled
[    0.476194] pci 0000:00:11.0: reg 10 io port: [0xa000-0xa007]
[    0.476200] pci 0000:00:11.0: reg 14 io port: [0x9000-0x9003]
[    0.476204] pci 0000:00:11.0: reg 18 io port: [0x8000-0x8007]
[    0.476209] pci 0000:00:11.0: reg 1c io port: [0x7000-0x7003]
[    0.476214] pci 0000:00:11.0: reg 20 io port: [0x6000-0x600f]
[    0.476219] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe5ffc00-0xfe5fffff]
[    0.476232] pci 0000:00:11.0: set SATA to AHCI mode
[    0.476296] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe5fe000-0xfe5fefff]
[    0.476347] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe5ff800-0xfe5ff8ff]
[    0.476383] pci 0000:00:12.2: supports D1 D2
[    0.476385] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.476413] pci 0000:00:12.2: PME# disabled
[    0.476459] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe5fd000-0xfe5fdfff]
[    0.476510] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe5ff400-0xfe5ff4ff]
[    0.476546] pci 0000:00:13.2: supports D1 D2
[    0.476547] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.476576] pci 0000:00:13.2: PME# disabled
[    0.476656] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.476661] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.476666] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.476671] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.476675] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.476711] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe5f8000-0xfe5fbfff]
[    0.476741] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.476769] pci 0000:00:14.2: PME# disabled
[    0.476867] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe5fc000-0xfe5fcfff]
[    0.476934] pci 0000:00:15.0: supports D1 D2
[    0.476961] pci 0000:00:16.0: reg 10 32bit mmio: [0xfe5f7000-0xfe5f7fff]
[    0.477011] pci 0000:00:16.2: reg 10 32bit mmio: [0xfe5ff000-0xfe5ff0ff]
[    0.477047] pci 0000:00:16.2: supports D1 D2
[    0.477049] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.477077] pci 0000:00:16.2: PME# disabled
[    0.477215] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.477218] pci 0000:01:05.0: reg 14 io port: [0xb000-0xb0ff]
[    0.477221] pci 0000:01:05.0: reg 18 32bit mmio: [0xfe7f0000-0xfe7fffff]
[    0.477227] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe600000-0xfe6fffff]
[    0.477236] pci 0000:01:05.0: supports D1 D2
[    0.477250] pci 0000:01:05.1: reg 10 32bit mmio: [0xfe7e8000-0xfe7ebfff]
[    0.477266] pci 0000:01:05.1: supports D1 D2
[    0.477324] pci 0000:00:01.0: bridge io port: [0xb000-0xbfff]
[    0.477326] pci 0000:00:01.0: bridge 32bit mmio: [0xfe600000-0xfe7fffff]
[    0.477329] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.477391] pci 0000:02:00.0: reg 24 32bit mmio: [0xfe8fe000-0xfe8fffff]
[    0.477419] pci 0000:02:00.0: PME# supported from D3hot
[    0.477481] pci 0000:02:00.0: PME# disabled
[    0.477544] pci 0000:02:00.1: reg 10 io port: [0xcc00-0xcc07]
[    0.477550] pci 0000:02:00.1: reg 14 io port: [0xc880-0xc883]
[    0.477556] pci 0000:02:00.1: reg 18 io port: [0xc800-0xc807]
[    0.477563] pci 0000:02:00.1: reg 1c io port: [0xc480-0xc483]
[    0.477569] pci 0000:02:00.1: reg 20 io port: [0xc400-0xc40f]
[    0.477652] pci 0000:00:0a.0: bridge io port: [0xc000-0xcfff]
[    0.477654] pci 0000:00:0a.0: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.477697] pci 0000:03:07.0: reg 10 32bit mmio: [0xfe9fb800-0xfe9fbfff]
[    0.477704] pci 0000:03:07.0: reg 14 io port: [0xdc00-0xdc7f]
[    0.477748] pci 0000:03:07.0: supports D2
[    0.477750] pci 0000:03:07.0: PME# supported from D2 D3hot D3cold
[    0.477779] pci 0000:03:07.0: PME# disabled
[    0.477838] pci 0000:00:14.4: transparent bridge
[    0.477865] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.477868] pci 0000:00:14.4: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.477909] pci 0000:04:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.477927] pci 0000:04:00.0: reg 18 64bit mmio pref: [0xfdfff000-0xfdffffff]
[    0.477939] pci 0000:04:00.0: reg 20 64bit mmio pref: [0xfdff8000-0xfdffbfff]
[    0.477978] pci 0000:04:00.0: supports D1 D2
[    0.477980] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.478009] pci 0000:04:00.0: PME# disabled
[    0.478086] pci 0000:00:15.0: bridge io port: [0xe000-0xefff]
[    0.478091] pci 0000:00:15.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.478102] pci_bus 0000:00: on NUMA node 0
[    0.478105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.478262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.478323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.478383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.478451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE20._PRT]
[    0.482364] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 14 15)
[    0.482683] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 *7 10 11 14 15)
[    0.483002] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 14 15)
[    0.483339] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 14 15)
[    0.483663] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0, disabled.
[    0.483988] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0, disabled.
[    0.484303] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 14 15)
[    0.484582] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0, disabled.
[    0.484901] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.484932] vgaarb: loaded
[    0.485028] SCSI subsystem initialized
[    0.485093] libata version 3.00 loaded.
[    0.485093] usbcore: registered new interface driver usbfs
[    0.485093] usbcore: registered new interface driver hub
[    0.485093] usbcore: registered new device driver usb
[    0.485093] ACPI: WMI: Mapper loaded
[    0.485093] PCI: Using ACPI for IRQ routing
[    0.485093] NetLabel: Initializing
[    0.485093] NetLabel:  domain hash size = 128
[    0.485093] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.485093] NetLabel:  unlabeled traffic allowed by default
[    0.485093] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.485093] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.486506] Switching to clocksource tsc
[    0.489000] AppArmor: AppArmor Filesystem Enabled
[    0.489071] pnp: PnP ACPI init
[    0.489107] ACPI: bus type pnp registered
[    0.491591] pnp: PnP ACPI: found 13 devices
[    0.491617] ACPI: ACPI bus type pnp unregistered
[    0.491644] PnPBIOS: Disabled by ACPI PNP
[    0.491678] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.491708] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.491737] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.491764] system 00:09: ioport range 0x40b-0x40b has been reserved
[    0.491792] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[    0.491833] system 00:09: ioport range 0xc00-0xc01 has been reserved
[    0.491860] system 00:09: ioport range 0xc14-0xc14 has been reserved
[    0.491888] system 00:09: ioport range 0xc50-0xc51 has been reserved
[    0.491915] system 00:09: ioport range 0xc52-0xc52 has been reserved
[    0.491942] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[    0.491969] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[    0.491996] system 00:09: ioport range 0xcd0-0xcd1 has been reserved
[    0.492023] system 00:09: ioport range 0xcd2-0xcd3 has been reserved
[    0.492050] system 00:09: ioport range 0xcd4-0xcd5 has been reserved
[    0.492077] system 00:09: ioport range 0xcd6-0xcd7 has been reserved
[    0.492104] system 00:09: ioport range 0xcd8-0xcdf has been reserved
[    0.492131] system 00:09: ioport range 0x800-0x89f has been reserved
[    0.492158] system 00:09: ioport range 0xb00-0xb1f has been reserved
[    0.492185] system 00:09: ioport range 0xb20-0xb3f has been reserved
[    0.492212] system 00:09: ioport range 0x900-0x90f has been reserved
[    0.492239] system 00:09: ioport range 0x910-0x91f has been reserved
[    0.492266] system 00:09: ioport range 0xfe00-0xfefe has been reserved
[    0.492294] system 00:09: iomem range 0xcff00000-0xcfffffff could not be reserved
[    0.492324] system 00:09: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.492351] system 00:09: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.492379] system 00:09: iomem range 0xfed80000-0xfed80fff has been reserved
[    0.492408] system 00:0a: ioport range 0x230-0x23f has been reserved
[    0.492435] system 00:0a: ioport range 0x290-0x29f has been reserved
[    0.492462] system 00:0a: ioport range 0xf40-0xf4f has been reserved
[    0.492489] system 00:0a: ioport range 0xa30-0xa3f has been reserved
[    0.492517] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.492546] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.492574] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.492601] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.492628] system 00:0c: iomem range 0x100000-0xcfefffff could not be reserved
[    0.492657] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.506899] Freeing initrd memory: 7777k freed
[    0.527427] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.527455] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.527482] pci 0000:00:01.0:   MEM window: 0xfe600000-0xfe7fffff
[    0.527510] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.527540] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.527567] pci 0000:00:0a.0:   IO window: 0xc000-0xcfff
[    0.527594] pci 0000:00:0a.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.527621] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.527649] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.527676] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.527705] pci 0000:00:14.4:   MEM window: 0xfe900000-0xfe9fffff
[    0.527733] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.527763] pci 0000:00:15.0: PCI bridge, secondary bus 0000:04
[    0.527790] pci 0000:00:15.0:   IO window: 0xe000-0xefff
[    0.527832] pci 0000:00:15.0:   MEM window: disabled
[    0.527860] pci 0000:00:15.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.527900]   alloc irq_desc for 18 on node -1
[    0.527902]   alloc kstat_irqs on node -1
[    0.527906] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.527934] pci 0000:00:0a.0: setting latency timer to 64
[    0.527942]   alloc irq_desc for 16 on node -1
[    0.527943]   alloc kstat_irqs on node -1
[    0.527945] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.527974] pci 0000:00:15.0: setting latency timer to 64
[    0.527977] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.527979] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.527981] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.527983] pci_bus 0000:01: resource 1 mem: [0xfe600000-0xfe7fffff]
[    0.527985] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.527986] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.527988] pci_bus 0000:02: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.527990] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.527992] pci_bus 0000:03: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.527993] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.527995] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.527997] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.527998] pci_bus 0000:04: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.528023] NET: Registered protocol family 2
[    0.528109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.528352] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.528731] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.528932] TCP: Hash tables configured (established 131072 bind 65536)
[    0.528983] TCP reno registered
[    0.529070] NET: Registered protocol family 1
[    1.387949] pci 0000:01:05.0: Boot video device
[    1.388159] cpufreq-nforce2: No nForce2 chipset.
[    1.388744] Scanning for low memory corruption every 60 seconds
[    1.388831] audit: initializing netlink socket (disabled)
[    1.388896] type=2000 audit(1290247148.387:1): initialized
[    1.394700] highmem bounce pool size: 64 pages
[    1.394729] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.395673] VFS: Disk quotas dquot_6.5.2
[    1.395738] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.396135] fuse init (API version 7.13)
[    1.396237] msgmni has been set to 1672
[    1.396496] alg: No test for stdrng (krng)
[    1.396560] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.396590] io scheduler noop registered
[    1.396616] io scheduler anticipatory registered
[    1.396642] io scheduler deadline registered
[    1.396690] io scheduler cfq registered (default)
[    1.396808]   alloc irq_desc for 24 on node -1
[    1.396809]   alloc kstat_irqs on node -1
[    1.396815] pcieport 0000:00:0a.0: irq 24 for MSI/MSI-X
[    1.396819] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.396956]   alloc irq_desc for 25 on node -1
[    1.396958]   alloc kstat_irqs on node -1
[    1.396963] pcieport 0000:00:15.0: irq 25 for MSI/MSI-X
[    1.396968] pcieport 0000:00:15.0: setting latency timer to 64
[    1.397012] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.397051] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.397137] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.397201] ACPI: Power Button [PWRB]
[    1.397254] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.397283] ACPI: Power Button [PWRF]
[    1.397822] processor LNXCPU:00: registered as cooling_device0
[    1.398054] processor LNXCPU:01: registered as cooling_device1
[    1.398284] processor LNXCPU:02: registered as cooling_device2
[    1.398516] processor LNXCPU:03: registered as cooling_device3
[    1.400163] isapnp: Scanning for PnP cards...
[    1.400914] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.401089] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.401347] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.401960] brd: module loaded
[    1.402240] loop: module loaded
[    1.402383] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.402564]   alloc irq_desc for 17 on node -1
[    1.402566]   alloc kstat_irqs on node -1
[    1.402571] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.402620] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.402637] pata_acpi 0000:02:00.1: enabling device (0000 -> 0001)
[    1.402667]   alloc irq_desc for 19 on node -1
[    1.402668]   alloc kstat_irqs on node -1
[    1.402670] pata_acpi 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.402711] pata_acpi 0000:02:00.1: setting latency timer to 64
[    1.402719] pata_acpi 0000:02:00.1: PCI INT B disabled
[    1.402913] Fixed MDIO Bus: probed
[    1.403023] PPP generic driver version 2.4.2
[    1.403067] tun: Universal TUN/TAP device driver, 1.6
[    1.403093] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.403163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.403232] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.403270] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.403313] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.403363] ehci_hcd 0000:00:12.2: debug port 1
[    1.403402] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe5ff800
[    1.411864] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.411969] usb usb1: configuration #1 chosen from 1 choice
[    1.412044] hub 1-0:1.0: USB hub found
[    1.412076] hub 1-0:1.0: 5 ports detected
[    1.412143] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.412181] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.412226] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.412273] ehci_hcd 0000:00:13.2: debug port 1
[    1.412309] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe5ff400
[    1.423841] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.423947] usb usb2: configuration #1 chosen from 1 choice
[    1.424021] hub 2-0:1.0: USB hub found
[    1.424052] hub 2-0:1.0: 5 ports detected
[    1.424119] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.424157] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.424202] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.424249] ehci_hcd 0000:00:16.2: debug port 1
[    1.424284] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe5ff000
[    1.435866] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.435971] usb usb3: configuration #1 chosen from 1 choice
[    1.436047] hub 3-0:1.0: USB hub found
[    1.436077] hub 3-0:1.0: 4 ports detected
[    1.436138] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.436176] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.436214] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.436261] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.436308] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe5fe000
[    1.495959] usb usb4: configuration #1 chosen from 1 choice
[    1.496004] hub 4-0:1.0: USB hub found
[    1.496035] hub 4-0:1.0: 5 ports detected
[    1.496099] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.496137] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.496183] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.496225] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe5fd000
[    1.555900] usb usb5: configuration #1 chosen from 1 choice
[    1.555944] hub 5-0:1.0: USB hub found
[    1.555975] hub 5-0:1.0: 5 ports detected
[    1.556040] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.556078] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.556127] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.556168] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe5fc000
[    1.615960] usb usb6: configuration #1 chosen from 1 choice
[    1.616004] hub 6-0:1.0: USB hub found
[    1.616036] hub 6-0:1.0: 2 ports detected
[    1.616096] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.616134] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.616180] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.616223] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe5f7000
[    1.675952] usb usb7: configuration #1 chosen from 1 choice
[    1.675996] hub 7-0:1.0: USB hub found
[    1.676027] hub 7-0:1.0: 4 ports detected
[    1.676091] uhci_hcd: USB Universal Host Controller Interface driver
[    1.676169] PNP: No PS/2 controller found. Probing ports directly.
[    1.676663] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.676697] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.676773] mice: PS/2 mouse device common for all mice
[    1.676862] rtc_cmos 00:03: RTC can wake from S4
[    1.676917] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.676960] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.677043] device-mapper: uevent: version 1.0.3
[    1.677185] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.677313] device-mapper: multipath: version 1.1.0 loaded
[    1.677339] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.677448] EISA: Probing bus 0 at eisa.0
[    1.677492] Cannot allocate resource for EISA slot 6
[    1.677518] Cannot allocate resource for EISA slot 7
[    1.677544] Cannot allocate resource for EISA slot 8
[    1.677570] EISA: Detected 0 cards.
[    1.677728] cpuidle: using governor ladder
[    1.677754] cpuidle: using governor menu
[    1.678042] TCP cubic registered
[    1.678185] NET: Registered protocol family 10
[    1.678531] lo: Disabled Privacy Extensions
[    1.678822] NET: Registered protocol family 17
[    1.678941] powernow-k8: Found 1 AMD Athlon(tm) II X4 645 Processor processors (4 cpu cores) (version 2.20.00)
[    1.679000] powernow-k8:    0 : pstate 0 (3100 MHz)
[    1.679026] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.679052] powernow-k8:    2 : pstate 2 (1900 MHz)
[    1.679078] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.753377] Using IPI No-Shortcut mode
[    1.753484] PM: Resume from disk failed.
[    1.753493] registered taskstats version 1
[    1.753891]   Magic number: 2:928:980
[    1.754023] rtc_cmos 00:03: setting system clock to 2010-11-20 09:59:09 UTC (1290247149)
[    1.754052] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.754079] EDD information not available.
[    1.805135] isapnp: No Plug & Play device found
[    1.805206] Freeing unused kernel memory: 656k freed
[    1.805481] Write protecting the kernel text: 4684k
[    1.805545] Write protecting the kernel read-only data: 1840k
[    1.819258] udev: starting version 151
[    1.833853] pata_jmicron 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.833981] pata_jmicron 0000:02:00.1: setting latency timer to 64
[    1.839924] scsi0 : pata_atiixp
[    1.841312] scsi1 : pata_jmicron
[    1.848307] scsi2 : pata_atiixp
[    1.849604] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.849697] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.849763] ahci 0000:00:11.0: version 3.0
[    1.849805] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.849863]   alloc irq_desc for 26 on node -1
[    1.849865]   alloc kstat_irqs on node -1
[    1.849873] ahci 0000:00:11.0: irq 26 for MSI/MSI-X
[    1.849937] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.849967] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.853616] scsi3 : pata_jmicron
[    1.854133] ata3: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
[    1.854226] ata4: PATA max UDMA/100 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
[    1.859113] scsi4 : ahci
[    1.863154] scsi5 : ahci
[    1.865811] scsi6 : ahci
[    1.866193] scsi7 : ahci
[    1.866325] ata5: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffd00 irq 26
[    1.866907] ata6: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffd80 irq 26
[    1.866937] ata7: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffe00 irq 26
[    1.866967] ata8: SATA max UDMA/133 abar m1024@0xfe5ffc00 port 0xfe5ffe80 irq 26
[    1.867041] ahci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.867137] ahci 0000:02:00.0: JMB361 has only one port, port_map 0x3 -> 0x1
[    1.880787] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x1 impl SATA mode
[    1.880854] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.880884] ahci 0000:02:00.0: setting latency timer to 64
[    1.880979] scsi8 : ahci
[    1.881096] scsi9 : ahci
[    1.881183] ata9: SATA max UDMA/133 abar m8192@0xfe8fe000 port 0xfe8fe100 irq 18
[    1.881212] ata10: DUMMY
[    1.928066] usb 4-5: new low speed USB device using ohci_hcd and address 2
[    2.104122] usb 4-5: configuration #1 chosen from 1 choice
[    2.112880] usbcore: registered new interface driver hiddev
[    2.118173] input: Novatek Ultra Flat Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input3
[    2.118287] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [Novatek Ultra Flat Keyboard] on usb-0000:00:12.0-5/input0
[    2.130089] input: Novatek Ultra Flat Keyboard as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.1/input/input4
[    2.130207] generic-usb 0003:0603:00F2.0002: input,hidraw1: USB HID v1.10 Device [Novatek Ultra Flat Keyboard] on usb-0000:00:12.0-5/input1
[    2.130253] usbcore: registered new interface driver usbhid
[    2.130280] usbhid: v2.6:USB HID core driver
[    2.188078] ata8: SATA link down (SStatus 0 SControl 300)
[    2.204093] ata9: SATA link down (SStatus 0 SControl 300)
[    2.272071] usb 3-3: new high speed USB device using ehci_hcd and address 2
[    2.352075] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.352124] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.352164] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.352793] ata6.00: ATA-8: FUJITSU MHY2200BH, 0000000B, max UDMA/100
[    2.352823] ata6.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.353606] ata6.00: configured for UDMA/100
[    2.354916] ata7.00: ATA-8: WDC WD5001AALS-00E3A0, 05.01D05, max UDMA/133
[    2.354938] ata5.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    2.354974] ata7.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.357060] ata7.00: configured for UDMA/133
[    2.358891] ata5.00: configured for UDMA/100
[    2.379549] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    2.383864] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.383897] Uniform CD-ROM driver Revision: 3.20
[    2.384011] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.384065] sr 4:0:0:0: Attached scsi generic sg0 type 5
[    2.384203] scsi 5:0:0:0: Direct-Access     ATA      FUJITSU MHY2200B 0000 PQ: 0 ANSI: 5
[    2.384324] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.384370] sd 5:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    2.384461] scsi 6:0:0:0: Direct-Access     ATA      WDC WD5001AALS-0 05.0 PQ: 0 ANSI: 5
[    2.384610] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.384615] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.384688] sd 5:0:0:0: [sda] Write Protect is off
[    2.384689] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.384702] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.384858] sd 6:0:0:0: [sdb] Write Protect is off
[    2.384920] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.384934] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.385057]  sda:
[    2.385124]  sdb: sdb1 sdb2 < sdb5 >
[    2.407196] sd 6:0:0:0: [sdb] Attached SCSI disk
[    2.423814]  sda1 sda2 <
[    2.432457] usb 3-3: configuration #1 chosen from 1 choice
[    2.440058]  sda5 sda6 sda7 sda8 sda9 >
[    2.496483] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.498431] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.498488] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.498547] r8169 0000:04:00.0: setting latency timer to 64
[    2.498552] r8169 0000:04:00.0: unknown MAC, using family default
[    2.498613]   alloc irq_desc for 27 on node -1
[    2.498615]   alloc kstat_irqs on node -1
[    2.498626] r8169 0000:04:00.0: irq 27 for MSI/MSI-X
[    2.499081] eth0: RTL8168b/8111b at 0xf81b4000, 20:cf:30:4e:1b:66, XID 0c200000 IRQ 27
[    2.500484]   alloc irq_desc for 22 on node -1
[    2.500487]   alloc kstat_irqs on node -1
[    2.500492] ohci1394 0000:03:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.548069] usb 3-4: new high speed USB device using ehci_hcd and address 3
[    2.558081] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fe9fb800-fe9fbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.682786] usb 3-4: configuration #1 chosen from 1 choice
[    2.687880] Initializing USB Mass Storage driver...
[    2.688067] scsi10 : SCSI emulation for USB Mass Storage devices
[    2.688201] usb-storage: device found at 3
[    2.688203] usb-storage: waiting for device to settle before scanning
[    2.688216] usbcore: registered new interface driver usb-storage
[    2.688246] USB Mass Storage support registered.
[    2.948071] usb 5-1: new low speed USB device using ohci_hcd and address 2
[    3.121289] usb 5-1: configuration #1 chosen from 1 choice
[    3.131434] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input5
[    3.131577] generic-usb 0003:045E:00CB.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:13.0-1/input0
[    3.553931] EXT4-fs (sda8): mounted filesystem with ordered data mode
[    3.832197] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001fc6000002ef70]
[    7.688314] usb-storage: device scan complete
[    7.689158] scsi 10:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[    7.689456] sd 10:0:0:0: Attached scsi generic sg3 type 0
[    7.691182] sd 10:0:0:0: [sdc] 4018176 512-byte logical blocks: (2.05 GB/1.91 GiB)
[    7.692309] sd 10:0:0:0: [sdc] Write Protect is off
[    7.692347] sd 10:0:0:0: [sdc] Mode Sense: 43 00 00 00
[    7.692349] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    7.696062] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    7.696094]  sdc: sdc1
[    7.698919] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[    7.698950] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[   14.769305] Adding 1311736k swap on /dev/sda9.  Priority:-1 extents:1 across:1311736k 
[   14.771781] udev: starting version 151
[   14.802490] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   14.802493] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   14.802604] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.804949] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SMRG [0xb00-0xb2f]
[   14.804952] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.814937] udev: renamed network interface eth0 to eth1
[   14.834001] lp: driver loaded but no devices found
[   14.854117] Linux agpgart interface v0.103
[   14.884916] [drm] Initialized drm 1.1.0 20060810
[   14.887897] type=1505 audit(1290247162.630:2):  operation="profile_load" pid=765 name="/sbin/dhclient3"
[   14.888076] type=1505 audit(1290247162.630:3):  operation="profile_load" pid=765 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.888175] type=1505 audit(1290247162.630:4):  operation="profile_load" pid=765 name="/usr/lib/connman/scripts/dhclient-script"
[   14.892796] ATK0110 ATK0110:00: EC enabled
[   14.916715] [drm] radeon defaulting to kernel modesetting.
[   14.916717] [drm] radeon kernel modesetting enabled.
[   14.916787] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.916790] radeon 0000:01:05.0: setting latency timer to 64
[   14.918018] [drm] radeon: Initializing kernel modesetting.
[   14.918239] [drm] register mmio base: 0xFE7F0000
[   14.918240] [drm] register mmio size: 65536
[   14.919415] ATOM BIOS: B43106_DVI
[   14.919429] [drm] Clocks initialized !
[   14.919648] [drm] Detected VRAM RAM=256M, BAR=256M
[   14.919652] [drm] RAM width 32bits DDR
[   14.919723] [TTM] Zone  kernel: Available graphics memory: 428480 kiB.
[   14.919724] [TTM] Zone highmem: Available graphics memory: 1677028 kiB.
[   14.919736] [drm] radeon: 256M of VRAM memory ready
[   14.919738] [drm] radeon: 512M of GTT memory ready.
[   14.919766] [drm] radeon: irq initialized.
[   14.919768] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.920043] [drm] Loading RS780 Microcode
[   14.920046] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   14.951669] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.967185] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.972141] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   14.973535] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   14.974956] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.975229] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.975231] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   14.975232] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   15.008535] [drm] ring test succeeded in 1 usecs
[   15.008638] [drm] radeon: ib pool ready.
[   15.008681] [drm] ib test succeeded in 0 usecs
[   15.008683] [drm] Enabling audio support
[   15.008798] [drm] Radeon Display Connectors
[   15.008800] [drm] Connector 0:
[   15.008801] [drm]   VGA
[   15.008803] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.008804] [drm]   Encoders:
[   15.008805] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.008806] [drm] Connector 1:
[   15.008807] [drm]   DVI-D
[   15.008808] [drm]   HPD3
[   15.008809] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.008810] [drm]   Encoders:
[   15.008811] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   15.043480] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.048017] rtusb init --->
[   15.048056] usbcore: registered new interface driver rt2870
[   15.048247] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.049138] 
[   15.049139] 
[   15.049139] === pAd = f8c3f000, size = 566748 ===
[   15.049140] 
[   15.049141] <-- RTMPAllocAdapterBlock, Status=0
[   15.147944] [drm] fb mappable at 0xD0141000
[   15.147946] [drm] vram apper at 0xD0000000
[   15.147947] [drm] size 8294400
[   15.147948] [drm] fb depth is 24
[   15.147949] [drm]    pitch is 7680
[   15.148020] fb0: radeondrmfb frame buffer device
[   15.148021] registered panic notifier
[   15.148025] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   15.148079] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.148104] HDA Intel 0000:01:05.1: setting latency timer to 64
[   15.149206] vga16fb: initializing
[   15.149208] vga16fb: mapped to 0xc00a0000
[   15.149212] vga16fb: not registering due to another framebuffer present
[   15.181456] Console: switching to colour frame buffer device 240x67
[   16.403984] r8169: eth1: link down
[   16.404125] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.404446] type=1505 audit(1290247164.149:5):  operation="profile_load" pid=1148 name="/usr/share/gdm/guest-session/Xsession"
[   16.405546] type=1505 audit(1290247164.149:6):  operation="profile_replace" pid=1155 name="/sbin/dhclient3"
[   16.405732] type=1505 audit(1290247164.149:7):  operation="profile_replace" pid=1155 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.405838] type=1505 audit(1290247164.149:8):  operation="profile_replace" pid=1155 name="/usr/lib/connman/scripts/dhclient-script"
[   16.407798] type=1505 audit(1290247164.149:9):  operation="profile_load" pid=1212 name="/usr/bin/evince"
[   16.410126] type=1505 audit(1290247164.153:10):  operation="profile_load" pid=1212 name="/usr/bin/evince-previewer"
[   16.411568] type=1505 audit(1290247164.153:11):  operation="profile_load" pid=1212 name="/usr/bin/evince-thumbnailer"
[   16.683926] <-- RTMPAllocTxRxRingMemory, Status=0
[   16.686162] -->RTUSBVenderReset
[   16.686284] <--RTUSBVenderReset
[   17.000648] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat
[   17.000651] 1. Phy Mode = 0
[   17.000652] 2. Phy Mode = 0
[   17.030510] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   17.045612] 3. Phy Mode = 0
[   17.053245] MCS Set = 00 00 00 00 00
[   17.093084] <==== RTMPInitialize, Status=0
[   17.094715] 0x1300 = 000a4360
[   17.255308] ppdev: user-space parallel port driver
[   17.771077] CPU0 attaching NULL sched-domain.
[   17.771081] CPU1 attaching NULL sched-domain.
[   17.771083] CPU2 attaching NULL sched-domain.
[   17.771085] CPU3 attaching NULL sched-domain.
[   17.796418] CPU0 attaching sched-domain:
[   17.796421]  domain 0: span 0-3 level MC
[   17.796423]   groups: 0 1 2 3
[   17.796428] CPU1 attaching sched-domain:
[   17.796429]  domain 0: span 0-3 level MC
[   17.796431]   groups: 1 2 3 0
[   17.796434] CPU2 attaching sched-domain:
[   17.796435]  domain 0: span 0-3 level MC
[   17.796436]   groups: 2 3 0 1
[   17.796439] CPU3 attaching sched-domain:
[   17.796440]  domain 0: span 0-3 level MC
[   17.796442]   groups: 3 0 1 2
[   18.155466] CPU0 attaching NULL sched-domain.
[   18.155471] CPU1 attaching NULL sched-domain.
[   18.155473] CPU2 attaching NULL sched-domain.
[   18.155474] CPU3 attaching NULL sched-domain.
[   18.184299] CPU0 attaching sched-domain:
[   18.184303]  domain 0: span 0-3 level MC
[   18.184305]   groups: 0 1 2 3
[   18.184310] CPU1 attaching sched-domain:
[   18.184311]  domain 0: span 0-3 level MC
[   18.184313]   groups: 1 2 3 0
[   18.184316] CPU2 attaching sched-domain:
[   18.184317]  domain 0: span 0-3 level MC
[   18.184319]   groups: 2 3 0 1
[   18.184322] CPU3 attaching sched-domain:
[   18.184323]  domain 0: span 0-3 level MC
[   18.184324]   groups: 3 0 1 2
[   18.719980] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   22.547523] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[   27.128049] wlan0: no IPv6 routers present
[   34.972053] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   34.972268] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   35.099936] DRS: unkown mode,default use 11N 1S AP 
[   35.099939] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   50.102433] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   50.102562] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   50.152768] DRS: unkown mode,default use 11N 1S AP 
[   50.152772] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   65.153332] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   65.153464] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   65.205861] DRS: unkown mode,default use 11N 1S AP 
[   65.205865] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   80.206523] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 246
[   80.206853] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[   80.258986] DRS: unkown mode,default use 11N 1S AP 
[   80.258996] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  103.666136] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  103.666460] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  103.708548] DRS: unkown mode,default use 11N 1S AP 
[  103.708558] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  118.710616] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  118.710938] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  118.761643] DRS: unkown mode,default use 11N 1S AP 
[  118.761652] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  133.763799] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  133.764158] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  133.814328] DRS: unkown mode,default use 11N 1S AP 
[  133.814338] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  148.816140] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  148.816465] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  148.867324] DRS: unkown mode,default use 11N 1S AP 
[  148.867334] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  168.311174] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  168.311498] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  168.333431] DRS: unkown mode,default use 11N 1S AP 
[  168.333441] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  183.334643] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  183.334968] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  183.376407] DRS: unkown mode,default use 11N 1S AP 
[  183.376417] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  198.377752] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  198.378088] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  198.429484] DRS: unkown mode,default use 11N 1S AP 
[  198.429495] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  213.430823] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  213.431158] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  213.482448] DRS: unkown mode,default use 11N 1S AP 
[  213.482458] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  229.907068] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  229.907404] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  229.969034] DRS: unkown mode,default use 11N 1S AP 
[  229.969044] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  244.971404] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  244.971734] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  245.021797] DRS: unkown mode,default use 11N 1S AP 
[  245.021807] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  260.024251] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  260.024585] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  260.177268] DRS: unkown mode,default use 11N 1S AP 
[  260.177278] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  275.180038] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  275.180355] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  275.230225] DRS: unkown mode,default use 11N 1S AP 
[  275.230235] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  290.233062] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  290.233387] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  290.283184] DRS: unkown mode,default use 11N 1S AP 
[  290.283194] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  298.373848] DRS: unkown mode,default use 11N 1S AP 
[  298.373858] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  301.378188] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  313.374958] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  313.375286] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  313.425680] DRS: unkown mode,default use 11N 1S AP 
[  313.425690] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  328.426734] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  328.426878] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  328.478524] DRS: unkown mode,default use 11N 1S AP 
[  328.478534] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  343.479569] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 143
[  343.479893] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  343.531614] DRS: unkown mode,default use 11N 1S AP 
[  343.531624] DRS: unkown mode (SupRateLen=4, ExtRateLen=8, MCSSet[0]=0x0, MCSSet[1]=0x0)
ted@ted-laptop:~$ 


ted@ted-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 003 Device 002: ID 1737:0078 Linksys 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ted@ted-laptop:~$ 

ted@ted-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 20:cf:30:4e:1b:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9456 (9.4 KB)  TX bytes:9456 (9.4 KB)

wlan0     Link encap:Ethernet  HWaddr 68:7f:74:84:e7:46  
          inet6 addr: fe80::6a7f:74ff:fe84:e746/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1265932 (1.2 MB)  TX bytes:34568 (34.5 KB)

ted@ted-laptop:

ted@ted-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"UPC075350"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 90:E6:BA:35:75:D3   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=95/100  Signal level:-69 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ted@ted-laptop:~$ 


any help would be greatly appreciated.

ted

---

### Post by ajgreeny on 2010-11-20
If your network is protected with either WEP or WPA try disabling the encryption to see if that is part of the problem.

Some adapters are not able to connect with WPA but can with WEP, so you may have to accept that as your default.

---

### Post by tooCanad on 2010-11-23
I just picked up a refurbished wusb100 from Tiger direct for $10.00.

Followed this post:

[http://ubuntuforums.org/showpost.php...48&postcount=6](http://ubuntuforums.org/showpost.php...48&postcount=6)


It is working fine with WPA encryption.

TC

---

### Post by LinksysWUSB100 on 2011-07-03
It says on my Linksys Wireless thing, "Connected (Secure) with 54.0 Mbps" but I'm not able to connect to the Internet for some mysterious reason. :confused: Also this website sucks when you can't contact staff members. [-(

---

### Post by chili555 on 2011-07-04
> **LinksysWUSB100 said:**
> It says on my Linksys Wireless thing, "Connected (Secure) with 54.0 Mbps" but I'm not able to connect to the Internet for some mysterious reason. :confused: Also this website sucks when you can't contact staff members. [-(You can contact most non-staff members, however. You will, by me, at least be asked for a link to your thread. 

Let's see, from a terminal:> ifconfig
cat /etc/resolv.conf
lsusbThanks.

---

