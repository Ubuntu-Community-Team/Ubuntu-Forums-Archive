---
title: "Don't recognizes the usb webcamera"
date: 2011-05-03
forum: Multimedia Software
---

### Post by basoula on 2011-05-03
Good afternoon! I instal Xubuntu 10.04 in an old pc (Pentium4 2Ghz cpu,512MB ram) I install cheese from ubuntu center,but when i open cheese,search for few second and then close! Skype in video prefernces tell me that dosn't exist camera! Then light in my camera is open when i connect in usb! What happen?
 lsusb:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 125f:c93a A-DATA Technology Co., Ltd.
Bus 001 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 003: ID 0c45:613b Microdia Win2 PC Camera
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[     0.000000] Linux version 2.6.32-30-generic (buildd@vernadsky) (gcc  version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1  21:30:21 UTC 2011 (Ubuntu 2.6.32-30.59-generic 2.6.32.29+drm33.13)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CCFFF write-protect
[    0.000000]   CD000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
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
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  modified: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  modified: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001fff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 7000-c000
[    0.000000] RAMDISK: 1789b000 - 18033b92
[    0.000000] ACPI: RSDP 000f6570 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 1fff3000 0002C (v01 GBT    AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: FACP 1fff3040 00074 (v01 GBT    AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: DSDT 1fff30c0 0365B (v01 GBT    AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS 1fff0000 00040
[    0.000000] ACPI: APIC 1fff6740 0005A (v01 GBT    AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 0 - 1fff0000
[    0.000000]   node 0 low ram: 00000000 - 1fff0000
[    0.000000]   node 0 bootmap 00008000 - 0000c000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [001789b000 - 0018033b92]          RAMDISK ==> [001789b000 - 0018033b92]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [00008e2000 - 00008e5092]              BRK ==> [00008e2000 - 00008e5092]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
[    0.000000] found SMP MP-table at [c00f4a90] f4a90
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130956
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129932
[     0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic  root=UUID=db6a5088-8f1c-43b8-926c-37e8618f7de7 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2621120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500404k/524224k available (4689k kernel code, 23028k reserved, 2122k data, 664k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07f0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc0594467 - 0xc07a6f08   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0594467   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2019.285 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4038.57 BogoMIPS (lpj=8077140)
[    0.004055] Security Framework initialized
[    0.004099] AppArmor: AppArmor initialized
[    0.004115] Mount-cache hash table entries: 512
[    0.004369] Initializing cgroup subsys ns
[    0.004380] Initializing cgroup subsys cpuacct
[    0.004392] Initializing cgroup subsys memory
[    0.004411] Initializing cgroup subsys devices
[    0.004418] Initializing cgroup subsys freezer
[    0.004425] Initializing cgroup subsys net_cls
[    0.004471] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004478] CPU: L2 cache: 512K
[    0.004483] CPU: Hyper-Threading is disabled
[    0.004490] mce: CPU supports 4 MCE banks
[    0.004509] CPU0: Thermal monitoring enabled (TM1)
[    0.004529] Performance Events: no PMU driver, software events only.
[    0.004544] Checking 'hlt' instruction... OK.
[    0.021435] SMP alternatives: switching to UP code
[    0.037264] Freeing SMP alternatives: 19k freed
[    0.037320] ACPI: Core revision 20090903
[    0.048017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048033] ftrace: allocating 21799 entries in 43 pages
[    0.052202] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052532] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.092519] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (4038.57 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 17:44:28  Date: 04/21/11
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.120485] PCI: PCI BIOS revision 2.10 entry at 0xf9d70, last bus=2
[    0.120490] PCI: Using configuration type 1 for base access
[    0.122253] bio: create slab <bio-0> at 0
[    0.123064] ACPI: EC: Look up EC in DSDT
[    0.129905] ACPI: Interpreter enabled
[    0.129914] ACPI: (supports S0 S1 S4 S5)
[    0.129952] ACPI: Using IOAPIC for interrupt routing
[    0.136332] ACPI: No dock devices found.
[    0.136498] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.136577] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.136810] pci 0000:00:1f.0: quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
[    0.136817] pci 0000:00:1f.0: quirk: region 4080-40bf claimed by ICH4 GPIO
[    0.136873] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.136945] pci 0000:00:1f.2: reg 20 io port: [0xb000-0xb01f]
[    0.137022] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x500f]
[    0.137092] pci 0000:00:1f.4: reg 20 io port: [0xb800-0xb81f]
[    0.137141] pci 0000:00:1f.5: reg 10 io port: [0xbc00-0xbcff]
[    0.137152] pci 0000:00:1f.5: reg 14 io port: [0xc000-0xc03f]
[    0.137241] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.137250] pci 0000:01:00.0: reg 14 io port: [0x9000-0x90ff]
[    0.137259] pci 0000:01:00.0: reg 18 32bit mmio: [0xe9000000-0xe900ffff]
[    0.137281] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.137308] pci 0000:01:00.0: supports D1 D2
[    0.137346] pci 0000:01:00.1: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.137356] pci 0000:01:00.1: reg 14 32bit mmio: [0xe9010000-0xe901ffff]
[    0.137397] pci 0000:01:00.1: supports D1 D2
[    0.137451] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.137457] pci 0000:00:01.0: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
[    0.137463] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xe7ffffff]
[    0.137500] pci 0000:02:01.0: reg 10 32bit mmio: [0xea000000-0xea001fff]
[    0.137580] pci 0000:02:02.0: reg 10 io port: [0xa000-0xa0ff]
[    0.137636] pci 0000:02:02.0: supports D1 D2
[    0.137687] pci 0000:00:1e.0: transparent bridge
[    0.137693] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.137700] pci 0000:00:1e.0: bridge 32bit mmio: [0xea000000-0xea0fffff]
[    0.137720] pci_bus 0000:00: on NUMA node 0
[    0.137730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.137876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.159350] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.159508] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.159661] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.159817] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.159971] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.160135] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.160289] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.160442] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.160665] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.160672] vgaarb: loaded
[    0.160918] SCSI subsystem initialized
[    0.161090] libata version 3.00 loaded.
[    0.161241] usbcore: registered new interface driver usbfs
[    0.161265] usbcore: registered new interface driver hub
[    0.161314] usbcore: registered new device driver usb
[    0.161563] ACPI: WMI: Mapper loaded
[    0.161567] PCI: Using ACPI for IRQ routing
[    0.161830] NetLabel: Initializing
[    0.161835] NetLabel:  domain hash size = 128
[    0.161837] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.161868] NetLabel:  unlabeled traffic allowed by default
[    0.161951] Switching to clocksource tsc
[    0.164001] AppArmor: AppArmor Filesystem Enabled
[    0.164001] pnp: PnP ACPI init
[    0.164001] ACPI: bus type pnp registered
[    0.169156] pnp: PnP ACPI: found 14 devices
[    0.169161] ACPI: ACPI bus type pnp unregistered
[    0.169170] PnPBIOS: Disabled by ACPI PNP
[    0.169195] system 00:00: iomem range 0xcd000-0xcffff has been reserved
[    0.169201] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.169206] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.169212] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.169217] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.169223] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.169228] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.169234] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.169239] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.169245] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.169250] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.169256] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.169269] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.169275] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.204177] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.204183] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.204190] pci 0000:00:01.0:   MEM window: 0xe8000000-0xe9ffffff
[    0.204196] pci 0000:00:01.0:   PREFETCH window: 0xd8000000-0xe7ffffff
[    0.204205] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.204210] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.204218] pci 0000:00:1e.0:   MEM window: 0xea000000-0xea0fffff
[    0.204224] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.204250] pci 0000:00:1e.0: setting latency timer to 64
[    0.204259] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.204264] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.204269] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.204273] pci_bus 0000:01: resource 1 mem: [0xe8000000-0xe9ffffff]
[    0.204278] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xe7ffffff]
[    0.204283] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.204287] pci_bus 0000:02: resource 1 mem: [0xea000000-0xea0fffff]
[    0.204292] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.204297] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.204374] NET: Registered protocol family 2
[    0.204558] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.205073] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.205267] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.205450] TCP: Hash tables configured (established 16384 bind 16384)
[    0.205454] TCP reno registered
[    0.205610] NET: Registered protocol family 1
[    0.205695] pci 0000:01:00.0: Boot video device
[    0.206135] cpufreq-nforce2: No nForce2 chipset.
[    0.206195] Scanning for low memory corruption every 60 seconds
[    0.206448] audit: initializing netlink socket (disabled)
[    0.206476] type=2000 audit(1303407868.205:1): initialized
[    0.218157] Trying to unpack rootfs image as initramfs...
[    0.230382] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.236785] VFS: Disk quotas dquot_6.5.2
[    0.236921] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.238083] fuse init (API version 7.13)
[    0.238247] msgmni has been set to 978
[    0.242938] alg: No test for stdrng (krng)
[    0.243127] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.243134] io scheduler noop registered
[    0.243138] io scheduler anticipatory registered
[    0.243143] io scheduler deadline registered
[    0.243217] io scheduler cfq registered (default)
[    0.243445] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.243487] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.243674] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.243683] ACPI: Power Button [PWRB]
[    0.243766] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.243779] ACPI: Sleep Button [SLPB]
[    0.243884] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.243889] ACPI: Power Button [PWRF]
[    0.244332] processor LNXCPU:00: registered as cooling_device0
[    0.252891] isapnp: Scanning for PnP cards...
[    0.258834] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.258973] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.259109] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.259626] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.259796] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.261681] brd: module loaded
[    0.267072] loop: module loaded
[    0.267314] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.267556] ata_piix 0000:00:1f.1: version 2.13
[    0.267689] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.314208] scsi0 : ata_piix
[    0.314520] scsi1 : ata_piix
[    0.315927] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.315933] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.316646] Fixed MDIO Bus: probed
[    0.316714] PPP generic driver version 2.4.2
[    0.316876] tun: Universal TUN/TAP device driver, 1.6
[    0.316880] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.317069] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.317102] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.317125] uhci_hcd: USB Universal Host Controller Interface driver
[    0.317214]   alloc irq_desc for 19 on node -1
[    0.317219]   alloc kstat_irqs on node -1
[    0.317233] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.317249] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.317255] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.317325] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.317376] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000b000
[    0.317573] usb usb1: configuration #1 chosen from 1 choice
[    0.317627] hub 1-0:1.0: USB hub found
[    0.317643] hub 1-0:1.0: 2 ports detected
[    0.317727]   alloc irq_desc for 23 on node -1
[    0.317731]   alloc kstat_irqs on node -1
[    0.317740] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.317750] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    0.317756] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    0.317813] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    0.317856] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000b800
[    0.322478] usb usb2: configuration #1 chosen from 1 choice
[    0.322554] hub 2-0:1.0: USB hub found
[    0.322580] hub 2-0:1.0: 2 ports detected
[    0.322770] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.322774] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.323613] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.323888] mice: PS/2 mouse device common for all mice
[    0.324155] rtc_cmos 00:04: RTC can wake from S4
[    0.324247] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.324280] rtc0: alarms up to one month, 242 bytes nvram
[    0.324513] device-mapper: uevent: version 1.0.3
[    0.329520] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.329697] device-mapper: multipath: version 1.1.0 loaded
[    0.329704] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.330003] EISA: Probing bus 0 at eisa.0
[    0.330029] Cannot allocate resource for EISA slot 4
[    0.330032] Cannot allocate resource for EISA slot 5
[    0.330048] EISA: Detected 0 cards.
[    0.331550] cpuidle: using governor ladder
[    0.331556] cpuidle: using governor menu
[    0.332345] TCP cubic registered
[    0.332612] NET: Registered protocol family 10
[    0.333408] lo: Disabled Privacy Extensions
[    0.334030] NET: Registered protocol family 17
[    0.334185] Using IPI No-Shortcut mode
[    0.334402] PM: Resume from disk failed.
[    0.334427] registered taskstats version 1
[    0.334690]   Magic number: 7:54:745
[    0.334828] rtc_cmos 00:04: setting system clock to 2011-04-21 17:44:29 UTC (1303407869)
[    0.334833] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.334836] EDD information not available.
[    0.352301] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.514715] ata2.00: ATAPI: SONY    CD-RW  CRX210E1, 2YS1, max UDMA/33
[    0.514781] ata2.01: ATAPI: TOSHIBA DVD-ROM SD-M1712, 1004, max UDMA/33
[    0.514961] ata1.00: HPA unlocked: 156250000 -> 156301488, native 156301488
[    0.514969] ata1.00: ATA-5: WDC WD800BB-75CAA0, 16.06V16, max UDMA/100
[    0.514975] ata1.00: 156301488 sectors, multi 16: LBA 
[    0.530481] ata2.00: configured for UDMA/33
[    0.531798] ata1.00: configured for UDMA/100
[    0.546584] ata2.01: configured for UDMA/33
[    0.678120] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    0.937689] isapnp: No Plug & Play device found
[    0.937969] usb 1-1: configuration #1 chosen from 1 choice
[    0.938255] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-75CA 16.0 PQ: 0 ANSI: 5
[    0.938514] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.938823] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.938911] sd 0:0:0:0: [sda] Write Protect is off
[    0.938917] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.938960] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.939224]  sda:
[    0.942272] hub 1-1:1.0: USB hub found
[    0.943948] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX210E1  2YS1 PQ: 0 ANSI: 5
[    0.944253] hub 1-1:1.0: 4 ports detected
[    0.963622]  sda1 sda2 <
[    0.968987] Freeing initrd memory: 7778k freed
[    0.990504]  sda5 sda6 >
[    1.004782] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.011797] sr0: scsi3-mmc drive: 124x/40x writer cd/rw xa/form2 cdda tray
[    1.011806] Uniform CD-ROM driver Revision: 3.20
[    1.011969] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.012110] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.064877] scsi 1:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1712 1004 PQ: 0 ANSI: 5
[    1.071946] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.072139] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.072240] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.072329] Freeing unused kernel memory: 664k freed
[    1.074108] Write protecting the kernel text: 4692k
[    1.074159] Write protecting the kernel read-only data: 1844k
[    1.117251] udev: starting version 151
[    1.229513] usb 1-1.4: new low speed USB device using uhci_hcd and address 3
[    1.372837] usb 1-1.4: configuration #1 chosen from 1 choice
[    1.455610] Floppy drive(s): fd0 is 1.44M
[    1.543483] FDC 0 is a post-1991 82077
[    1.577711]   alloc irq_desc for 21 on node -1
[    1.577718]   alloc kstat_irqs on node -1
[    1.577734] b43-pci-bridge 0000:02:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.587925] usbcore: registered new interface driver hiddev
[    1.636169] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[     1.641088] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as  /devices/pci0000:00/0000:00:1f.2/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
[     1.641516] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID  v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on  usb-0000:00:1f.2-1.4/input0
[    1.641588] usbcore: registered new interface driver usbhid
[    1.641818] usbhid: v2.6:USB HID core driver
[    1.917100] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   16.669808] Adding 1192952k swap on /dev/sda6.  Priority:-1 extents:1 across:1192952k 
[   16.737891] udev: starting version 151
[   16.979242] lp: driver loaded but no devices found
[   17.061939] Linux agpgart interface v0.103
[   17.065659] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.113136] intel_rng: FWH not detected
[   17.233869] parport_pc 00:0a: reported by Plug and Play ACPI
[   17.233921] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   17.307299] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   17.329345] lp0: using parport0 (interrupt-driven).
[   17.601259] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   17.865546] [drm] Initialized drm 1.1.0 20060810
[   17.977617] cfg80211: Calling CRDA to update world regulatory domain
[   18.060700] cfg80211: World regulatory domain updated:
[   18.060709]    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.060715]    (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.060720]    (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.060725]    (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.060730]    (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.060735]    (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.084276] ppdev: user-space parallel port driver
[   18.166828] type=1505 audit(1303397087.329:2):  operation="profile_load" pid=523 name="/sbin/dhclient3"
[    18.167667] type=1505 audit(1303397087.329:3):   operation="profile_load" pid=523  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.190775]  type=1505 audit(1303397087.353:4):  operation="profile_load" pid=523  name="/usr/lib/connman/scripts/dhclient-script"
[   18.193432] gameport: NS558 PnP Gameport is pnp00:0d/gameport0, io 0x201, speed 817kHz
[   18.408456] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   18.590655] [drm] radeon defaulting to kernel modesetting.
[   18.590666] [drm] radeon kernel modesetting enabled.
[   18.590781]   alloc irq_desc for 16 on node -1
[   18.590785]   alloc kstat_irqs on node -1
[   18.590801] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.623270] [drm] radeon: Initializing kernel modesetting.
[   18.636107] [drm] register mmio base: 0xE9000000
[   18.636114] [drm] register mmio size: 65536
[   18.636508] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   18.636530] [drm] Generation 2 PCI interface, using max accessible memory
[   18.636552] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   18.636580] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   18.636607] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   18.636628] [drm] radeon: VRAM 128M
[   18.636632] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   18.636635] [drm] radeon: GTT 128M
[   18.636638] [drm] radeon: GTT from 0xD0000000 to 0xD7FFFFFF
[   18.636704] [drm] radeon: irq initialized.
[   18.636927] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.636935] [drm] RAM width 64bits DDR
[   18.647511] [TTM] Zone  kernel: Available graphics memory: 254628 kiB.
[   18.647557] [drm] radeon: 128M of VRAM memory ready
[   18.647563] [drm] radeon: 128M of GTT memory ready.
[   18.647829] [drm] radeon: cp idle (0x02000603)
[   18.648109] [drm] Loading R200 Microcode
[   18.648748] platform radeon_cp.0: firmware: requesting radeon/R200_cp.bin
[   18.658364] phy0: Selected rate control algorithm 'minstrel'
[   18.659623] Registered led device: b43-phy0::tx
[   18.659655] Registered led device: b43-phy0::rx
[   18.659688] Registered led device: b43-phy0::assoc
[   18.659727] Registered led device: b43-phy0::radio
[   18.659896] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   18.706576] [drm] radeon: ring at 0x00000000D0000000
[   18.706607] [drm] ring test succeeded in 1 usecs
[   18.749860] [drm] radeon: ib pool ready.
[   18.750021] [drm] ib test succeeded in 0 usecs
[   18.751561] [drm] Default TV standard: PAL
[   18.751567] [drm] 27.000000000 MHz TV ref clk
[   18.751574] [drm] DFP table revision: 4
[   18.752795] [drm] Default TV standard: PAL
[   18.752801] [drm] 27.000000000 MHz TV ref clk
[   18.753004] [drm] Radeon Display Connectors
[   18.753009] [drm] Connector 0:
[   18.753012] [drm]   VGA
[   18.753018] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   18.753021] [drm]   Encoders:
[   18.753024] [drm]     CRT1: INTERNAL_DAC1
[   18.753027] [drm] Connector 1:
[   18.753030] [drm]   DVI-I
[   18.753032] [drm]   HPD1
[   18.753037] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   18.753040] [drm]   Encoders:
[   18.753042] [drm]     CRT2: INTERNAL_DAC2
[   18.753045] [drm]     DFP1: INTERNAL_TMDS1
[   18.753048] [drm] Connector 2:
[   18.753051] [drm]   S-video
[   18.753053] [drm]   Encoders:
[   18.753056] [drm]     TV1: INTERNAL_DAC2
[   18.956807] type=1505 audit(1303397088.121:5):  operation="profile_replace" pid=663 name="/sbin/dhclient3"
[    18.957702] type=1505 audit(1303397088.121:6):   operation="profile_replace" pid=663  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.958194]  type=1505 audit(1303397088.121:7):  operation="profile_replace" pid=663  name="/usr/lib/connman/scripts/dhclient-script"
[   19.115550] type=1505 audit(1303397088.277:8):  operation="profile_load" pid=670 name="/usr/bin/evince"
[   19.247488] type=1505 audit(1303397088.409:9):  operation="profile_load" pid=670 name="/usr/bin/evince-previewer"
[   19.248260] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.271021]   alloc irq_desc for 22 on node -1
[   19.271028]   alloc kstat_irqs on node -1
[   19.271042] C-Media PCI 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.294392] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.318220] type=1505 audit(1303397088.481:10):  operation="profile_load" pid=670 name="/usr/bin/evince-thumbnailer"
[   19.336996] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.390521] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.599761] type=1505 audit(1303397088.761:11):  operation="profile_load" pid=702 name="/usr/lib/cups/backend/cups-pdf"
[   19.647380]   alloc irq_desc for 17 on node -1
[   19.647387]   alloc kstat_irqs on node -1
[   19.647402] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.647436] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.721597] [drm] fb mappable at 0xD8040000
[   19.721604] [drm] vram apper at 0xD8000000
[   19.721607] [drm] size 5242880
[   19.721610] [drm] fb depth is 24
[   19.721612] [drm]    pitch is 5120
[   19.770977] fb0: radeondrmfb frame buffer device
[   19.770983] registered panic notifier
[   19.770998] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   19.783559] vga16fb: initializing
[   19.783572] vga16fb: mapped to 0xc00a0000
[   19.783582] vga16fb: not registering due to another framebuffer present
[   19.948093] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.012215] intel8x0_measure_ac97_clock: measured 70864 usecs (3406 samples)
[   20.012222] intel8x0: clocking to 48000
[   20.044513] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.171431] Console: switching to colour frame buffer device 160x64
[   80.860141] wlan0: deauthenticating from 00:26:44:09:95:55 by local choice (reason=3)
[   80.867496] wlan0: direct probe to AP 00:26:44:09:95:55 (try 1)
[   80.870237] wlan0: direct probe responded
[   80.870247] wlan0: authenticate with AP 00:26:44:09:95:55 (try 1)
[   80.872367] wlan0: authenticated
[   80.872424] wlan0: associate with AP 00:26:44:09:95:55 (try 1)
[   80.874912] wlan0: RX AssocResp from 00:26:44:09:95:55 (capab=0x411 status=0 aid=2)
[   80.874921] wlan0: associated
[   80.876057] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   91.380023] wlan0: no IPv6 routers present
[  101.709700] usb 1-1.1: new full speed USB device using uhci_hcd and address 4
[  101.831009] usb 1-1.1: configuration #1 chosen from 1 choice
[  101.886434] Linux video capture interface: v2.00
[  101.905588] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[  101.907772] usb 1-1.1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[  102.026456] usb 1-1.1: OV7660 image sensor detected
[  102.822717] usb 1-1.1: Initialization succeeded
[  102.823788] usb 1-1.1: V4L2 device registered as /dev/video0
[  102.823796] usb 1-1.1: Optional device control through 'sysfs' interface disabled
[  102.823882] usbcore: registered new interface driver sn9c102
[  102.841086] usb 1-1.1: usb_submit_urb() failed, error -28
[  102.889794] usb 1-1.1: usb_submit_urb() failed, error -28
```
lsmod
```
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39841  1 
sn9c102               137320  0 
videodev               34361  1 sn9c102
v4l1_compat            13251  1 videodev
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25652  4 
snd_wavefront          33066  0 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_cs4236             25514  0 
snd_pcm_oss            35308  0 
snd_wss_lib            23410  2 snd_wavefront,snd_cs4236
snd_mixer_oss          13746  3 snd_pcm_oss
snd_cmipci             30437  6 
snd_opl3_lib            8966  3 snd_wavefront,snd_cs4236,snd_cmipci
snd_hwdep               5412  2 snd_wavefront,snd_opl3_lib
snd_mpu401              5123  0 
snd_mpu401_uart         5617  4 snd_wavefront,snd_cs4236,snd_cmipci,snd_mpu401
snd_pcm                70694  6 snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_pcm_oss,snd_wss_lib,snd_cmipci
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                676897  2 
b43                   163524  0 
snd_timer              19098  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          5700  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
mac80211              205402  1 b43
drm_kms_helper         29329  1 radeon
ppdev                   5259  0 
snd                     54180  34  snd_intel8x0,snd_wavefront,snd_ac97_codec,snd_cs4236,snd_pcm_oss,snd_wss_lib,snd_mixer_oss,snd_cmipci,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ns558                   3056  0 
cfg80211              126528  2 b43,mac80211
drm                   162345  4 radeon,ttm,drm_kms_helper
gameport                9089  3 snd_cmipci,ns558
soundcore               6620  3 snd
led_class               2864  1 b43
i2c_algo_bit            5028  1 radeon
snd_page_alloc          7076  3 snd_intel8x0,snd_wss_lib,snd_pcm
intel_agp              24375  1 
parport_pc             25962  1 
shpchp                 28835  0 
agpgart                31724  3 ttm,drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
ssb                    38934  1 b43
floppy                 53016  0 
```
Sorry for me english! Thank you for your help!

---

