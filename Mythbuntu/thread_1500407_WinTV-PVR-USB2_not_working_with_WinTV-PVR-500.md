---
title: "WinTV-PVR-USB2 not working with WinTV-PVR-500"
date: 2010-06-03
forum: Mythbuntu
---

### Post by ybreton on 2010-06-03
Hi everyone,
     I've recently upgraded mythbuntu from 9.10 to 10.04. Everything is fine except for a major factor for the girlfriend and the roommates. The remote won't work. I've tracked down the problem to 10.04 not recognizing/loading/using the WinTV-PVR-USB2 I have set up. Everything worked great in 9.10, but now that I've distro-upgraded, the system doesn't appear to see the USB tuner, though it correctly recognizes the tuner card (a WinTV-PVR-500). I've been up all night trying to fix this myself, but I'm biting the bullet now and seeking advice from the professionals--i.e., you.

Any and all help is greatly appreciated!

Thanks!
Yannick.

*Edit:*

```
@mythtv:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bff0000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff3000 - 000000003c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI not present or invalid.
[    0.000000] last_pfn = 0x3bff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-EFFFF uncachable
[    0.000000]   F0000-F7FFF write-through
[    0.000000]   F8000-F8FFF uncachable
[    0.000000]   F9000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03C000000 mask FFC000000 uncachable
[    0.000000]   2 base 0C0000000 mask FE0000000 write-combining
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
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bff0000 (usable)
[    0.000000]  modified: 000000003bff0000 - 000000003bff3000 (ACPI NVS)
[    0.000000]  modified: 000000003bff3000 - 000000003c000000 (ACPI data)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2c89b000 - 2d03351e
[    0.000000] ACPI: RSDP 000f6aa0 00014 (v00 CN400 )
[    0.000000] ACPI: RSDT 3bff3000 00028 (v01 CN400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 3bff3040 00074 (v01 CN400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 3bff30c0 041DE (v01 CN400  AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3bff0000 00040
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002c89b000 - 002d03351e]          RAMDISK ==> [002c89b000 - 002d03351e]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd000]              BRK ==> [00008da000 - 00008dd000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bff0
[    0.000000] On node 0 totalpages: 245643
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 144 pages used for memmap
[    0.000000]   HighMem zone: 18274 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.7 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] No local APIC present or hardware disabled
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c3ff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243723
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=71991f50-b389-4e32-89f5-b9cf5e9bbde4 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4914880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bff0)
[    0.000000] Memory: 952928k/982976k available (4673k kernel code, 29212k reserved, 2121k data, 656k init, 73672k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1333.213 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 2666.42 BogoMIPS (lpj=5332852)
[    0.004081] Security Framework initialized
[    0.004188] AppArmor: AppArmor initialized
[    0.004210] Mount-cache hash table entries: 512
[    0.004619] Initializing cgroup subsys ns
[    0.004632] Initializing cgroup subsys cpuacct
[    0.004647] Initializing cgroup subsys memory
[    0.004679] Initializing cgroup subsys devices
[    0.004688] Initializing cgroup subsys freezer
[    0.004696] Initializing cgroup subsys net_cls
[    0.004752] CPU: L1 I Cache: 64K (32 bytes/line), D cache 64K (32 bytes/line)
[    0.004762] CPU: L2 Cache: 64K (32 bytes/line)
[    0.004805] Performance Events: 
[    0.004819] Checking 'hlt' instruction... OK.
[    0.021147] SMP alternatives: switching to UP code
[    0.044109] Freeing SMP alternatives: 19k freed
[    0.044226] ftrace: converting mcount calls to 66 66 66 66 90
[    0.044256] ftrace: allocating 21771 entries in 43 pages
[    0.048301] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.048311] weird, boot CPU (#0) not listed by the BIOS.
[    0.048317] SMP motherboard not detected.
[    0.048324] Local APIC not detected. Using dummy APIC emulation.
[    0.048329] SMP disabled
[    0.049144] Brought up 1 CPUs
[    0.049155] Total of 1 processors activated (2666.42 BogoMIPS).
[    0.049903] CPU0 attaching NULL sched-domain.
[    0.050305] devtmpfs: initialized
[    0.052198] regulator: core version 0.5
[    0.052256] Time: 14:59:27  Date: 06/04/10
[    0.052424] NET: Registered protocol family 16
[    0.052758] EISA bus registered
[    0.060468] PCI: PCI BIOS revision 2.10 entry at 0xfad70, last bus=2
[    0.060476] PCI: Using configuration type 1 for base access
[    0.063064] bio: create slab <bio-0> at 0
[    0.063227] ACPI: Interpreter disabled.
[    0.063418] vgaarb: loaded
[    0.063735] SCSI subsystem initialized
[    0.063928] libata version 3.00 loaded.
[    0.064174] usbcore: registered new interface driver usbfs
[    0.064207] usbcore: registered new interface driver hub
[    0.064287] usbcore: registered new device driver usb
[    0.064601] PCI: Probing PCI hardware
[    0.064609] PCI: Probing PCI hardware (bus 00)
[    0.064739] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xc0000000-0xdfffffff]
[    0.065159] pci 0000:00:01.0: supports D1
[    0.065226] pci 0000:00:0d.0: reg 10 32bit mmio: [0xee002000-0xee0027ff]
[    0.065240] pci 0000:00:0d.0: reg 14 io port: [0xb000-0xb07f]
[    0.065292] pci 0000:00:0d.0: supports D2
[    0.065299] pci 0000:00:0d.0: PME# supported from D2 D3hot D3cold
[    0.065310] pci 0000:00:0d.0: PME# disabled
[    0.065362] pci 0000:00:0f.0: reg 10 io port: [0xb400-0xb407]
[    0.065375] pci 0000:00:0f.0: reg 14 io port: [0xb800-0xb803]
[    0.065389] pci 0000:00:0f.0: reg 18 io port: [0xbc00-0xbc07]
[    0.065402] pci 0000:00:0f.0: reg 1c io port: [0xc000-0xc003]
[    0.065415] pci 0000:00:0f.0: reg 20 io port: [0xc400-0xc40f]
[    0.065429] pci 0000:00:0f.0: reg 24 io port: [0xc800-0xc8ff]
[    0.065528] pci 0000:00:0f.1: reg 20 io port: [0xcc00-0xcc0f]
[    0.065637] pci 0000:00:10.0: reg 20 io port: [0xd000-0xd01f]
[    0.065672] pci 0000:00:10.0: supports D1 D2
[    0.065679] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.065688] pci 0000:00:10.0: PME# disabled
[    0.065757] pci 0000:00:10.1: reg 20 io port: [0xd400-0xd41f]
[    0.065792] pci 0000:00:10.1: supports D1 D2
[    0.065799] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.065808] pci 0000:00:10.1: PME# disabled
[    0.065875] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
[    0.065910] pci 0000:00:10.2: supports D1 D2
[    0.065917] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.065926] pci 0000:00:10.2: PME# disabled
[    0.065994] pci 0000:00:10.3: reg 20 io port: [0xdc00-0xdc1f]
[    0.066030] pci 0000:00:10.3: supports D1 D2
[    0.066036] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.066046] pci 0000:00:10.3: PME# disabled
[    0.066098] pci 0000:00:10.4: reg 10 32bit mmio: [0xee000000-0xee0000ff]
[    0.066153] pci 0000:00:10.4: supports D1 D2
[    0.066160] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.066169] pci 0000:00:10.4: PME# disabled
[    0.066255] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.066333] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.066390] pci 0000:00:11.5: supports D1 D2
[    0.066443] pci 0000:00:12.0: reg 10 io port: [0xe800-0xe8ff]
[    0.066457] pci 0000:00:12.0: reg 14 32bit mmio: [0xee001000-0xee0010ff]
[    0.066509] pci 0000:00:12.0: supports D1 D2
[    0.066516] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.066525] pci 0000:00:12.0: PME# disabled
[    0.066618] pci 0000:00:14.0: supports D1 D2
[    0.066625] pci 0000:00:14.0: PME# supported from D1 D2 D3hot D3cold
[    0.066634] pci 0000:00:14.0: PME# disabled
[    0.066715] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xe8000000-0xebffffff]
[    0.066729] pci 0000:01:00.0: reg 14 32bit mmio: [0xec000000-0xecffffff]
[    0.066758] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.066786] pci 0000:01:00.0: supports D1 D2
[    0.066841] pci 0000:00:01.0: bridge 32bit mmio: [0xec000000-0xedffffff]
[    0.066853] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe8000000-0xebffffff]
[    0.066929] pci 0000:02:08.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[    0.067048] pci 0000:02:09.0: reg 10 32bit mmio pref: [0xe4000000-0xe7ffffff]
[    0.067171] pci 0000:00:14.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.068402] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.068997] pci 0000:00:11.0: VIA IRQ router [1106:3227]
[    0.069543] NetLabel: Initializing
[    0.069549] NetLabel:  domain hash size = 128
[    0.069554] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.069598] NetLabel:  unlabeled traffic allowed by default
[    0.069704] Switching to clocksource tsc
[    0.073581] AppArmor: AppArmor Filesystem Enabled
[    0.073600] pnp: PnP ACPI: disabled
[    0.073609] PnPBIOS: Scanning system for PnP BIOS support...
[    0.073933] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb7d0
[    0.073943] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb800, dseg 0xf0000
[    0.075069] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.075106] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.075119] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[    0.075129] system 00:07: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.075140] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.075157] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.075167] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[    0.075177] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[    0.075187] system 00:08: iomem range 0xd0000-0xd3fff has been reserved
[    0.075717] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.075725] pci 0000:00:01.0:   IO window: disabled
[    0.075738] pci 0000:00:01.0:   MEM window: 0xec000000-0xedffffff
[    0.075749] pci 0000:00:01.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.075763] pci 0000:00:14.0: PCI bridge, secondary bus 0000:02
[    0.075769] pci 0000:00:14.0:   IO window: disabled
[    0.075779] pci 0000:00:14.0:   MEM window: disabled
[    0.075789] pci 0000:00:14.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.075818] pci 0000:00:01.0: setting latency timer to 64
[    0.075841] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.075850] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.075860] pci_bus 0000:01: resource 1 mem: [0xec000000-0xedffffff]
[    0.075869] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.075879] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.075993] NET: Registered protocol family 2
[    0.076293] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.077794] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.086251] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.090524] TCP: Hash tables configured (established 131072 bind 65536)
[    0.090534] TCP reno registered
[    0.090893] NET: Registered protocol family 1
[    0.090968] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.091137] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.091165] pci 0000:01:00.0: Boot video device
[    0.091491] cpufreq-nforce2: No nForce2 chipset.
[    0.091574] Scanning for low memory corruption every 60 seconds
[    0.092035] audit: initializing netlink socket (disabled)
[    0.092072] type=2000 audit(1275663567.090:1): initialized
[    0.120224] Trying to unpack rootfs image as initramfs...
[    0.151346] highmem bounce pool size: 64 pages
[    0.151366] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.163011] VFS: Disk quotas dquot_6.5.2
[    0.163361] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.165335] fuse init (API version 7.13)
[    0.165614] msgmni has been set to 1718
[    0.170705] alg: No test for stdrng (krng)
[    0.170987] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.170997] io scheduler noop registered
[    0.171003] io scheduler anticipatory registered
[    0.171009] io scheduler deadline registered
[    0.171163] io scheduler cfq registered (default)
[    0.171545] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.171608] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.175990] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.176174] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.176320] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.176918] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.177155] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.182917] isapnp: Scanning for PnP cards...
[    0.190954] brd: module loaded
[    0.192460] loop: module loaded
[    0.192882] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.243122] Fixed MDIO Bus: probed
[    0.243229] PPP generic driver version 2.4.2
[    0.243435] tun: Universal TUN/TAP device driver, 1.6
[    0.243442] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.243768] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.243851] PCI: setting IRQ 12 as level-triggered
[    0.243861] ehci_hcd 0000:00:10.4: found PCI INT C -> IRQ 12
[    0.243921] ehci_hcd 0000:00:10.4: sharing IRQ 12 with 0000:00:11.5
[    0.244008] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.244098] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.244229] ehci_hcd 0000:00:10.4: irq 12, io mem 0xee000000
[    0.254711] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.255149] usb usb1: configuration #1 chosen from 1 choice
[    0.255241] hub 1-0:1.0: USB hub found
[    0.255288] hub 1-0:1.0: 8 ports detected
[    0.255478] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.255536] uhci_hcd: USB Universal Host Controller Interface driver
[    0.255720] PCI: setting IRQ 10 as level-triggered
[    0.255730] uhci_hcd 0000:00:10.0: found PCI INT A -> IRQ 10
[    0.255774] uhci_hcd 0000:00:10.0: sharing IRQ 10 with 0000:00:10.1
[    0.255799] uhci_hcd 0000:00:10.0: sharing IRQ 10 with 0000:00:12.0
[    0.255839] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.256004] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.256061] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000d000
[    0.256417] usb usb2: configuration #1 chosen from 1 choice
[    0.256510] hub 2-0:1.0: USB hub found
[    0.256539] hub 2-0:1.0: 2 ports detected
[    0.256680] uhci_hcd 0000:00:10.1: found PCI INT A -> IRQ 10
[    0.256723] uhci_hcd 0000:00:10.1: sharing IRQ 10 with 0000:00:10.0
[    0.256751] uhci_hcd 0000:00:10.1: sharing IRQ 10 with 0000:00:12.0
[    0.256784] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.256914] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.256957] uhci_hcd 0000:00:10.1: irq 10, io base 0x0000d400
[    0.257311] usb usb3: configuration #1 chosen from 1 choice
[    0.257395] hub 3-0:1.0: USB hub found
[    0.257428] hub 3-0:1.0: 2 ports detected
[    0.257556] PCI: setting IRQ 11 as level-triggered
[    0.257565] uhci_hcd 0000:00:10.2: found PCI INT B -> IRQ 11
[    0.257598] uhci_hcd 0000:00:10.2: sharing IRQ 11 with 0000:00:0d.0
[    0.257623] uhci_hcd 0000:00:10.2: sharing IRQ 11 with 0000:00:10.3
[    0.257671] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.257778] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.257823] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000d800
[    0.262991] usb usb4: configuration #1 chosen from 1 choice
[    0.263101] hub 4-0:1.0: USB hub found
[    0.263152] hub 4-0:1.0: 2 ports detected
[    0.263313] uhci_hcd 0000:00:10.3: found PCI INT B -> IRQ 11
[    0.263353] uhci_hcd 0000:00:10.3: sharing IRQ 11 with 0000:00:0d.0
[    0.263377] uhci_hcd 0000:00:10.3: sharing IRQ 11 with 0000:00:10.2
[    0.263437] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.263634] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.263685] uhci_hcd 0000:00:10.3: irq 11, io base 0x0000dc00
[    0.264081] usb usb5: configuration #1 chosen from 1 choice
[    0.264163] hub 5-0:1.0: USB hub found
[    0.264198] hub 5-0:1.0: 2 ports detected
[    0.264451] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    0.264458] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.264659] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.265013] mice: PS/2 mouse device common for all mice
[    0.265286] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.265331] rtc0: alarms up to one day, 114 bytes nvram
[    0.265654] device-mapper: uevent: version 1.0.3
[    0.266082] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.270675] device-mapper: multipath: version 1.1.0 loaded
[    0.270690] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.271285] EISA: Probing bus 0 at eisa.0
[    0.271349] EISA: Detected 0 cards.
[    0.274594] cpuidle: using governor ladder
[    0.274603] cpuidle: using governor menu
[    0.276141] TCP cubic registered
[    0.276622] NET: Registered protocol family 10
[    0.278017] lo: Disabled Privacy Extensions
[    0.279045] NET: Registered protocol family 17
[    0.279181] longhaul: VIA C3 'Nehemiah C' [C5P] CPU detected.  Powersaver supported.
[    0.279230] longhaul: ACPI I/O at 0x400
[    0.279272] longhaul: Using northbridge support.
[    0.279371] Using IPI No-Shortcut mode
[    0.279674] PM: Resume from disk failed.
[    0.279708] registered taskstats version 1
[    0.280438]   Magic number: 14:226:990
[    0.280623] rtc_cmos 00:03: setting system clock to 2010-06-04 14:59:28 UTC (1275663568)
[    0.280633] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.280639] EDD information not available.
[    0.606254] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.870416] isapnp: No Plug & Play device found
[    1.342850] Freeing initrd memory: 7777k freed
[    1.390251] Freeing unused kernel memory: 656k freed
[    1.394627] Write protecting the kernel text: 4676k
[    1.394734] Write protecting the kernel read-only data: 1840k
[    1.491673] udev: starting version 151
[    2.121398] pata_via 0000:00:0f.1: version 0.3.4
[    2.121850] scsi0 : pata_via
[    2.122775] scsi1 : pata_via
[    2.123114] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xcc00 irq 14
[    2.123126] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xcc08 irq 15
[    2.130177] sata_via 0000:00:0f.0: version 2.4
[    2.130341] sata_via 0000:00:0f.0: routed to hard irq line 11
[    2.146808] scsi2 : sata_via
[    2.147468] scsi3 : sata_via
[    2.147822] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 11
[    2.147834] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 11
[    2.149467] ohci1394 0000:00:0d.0: found PCI INT A -> IRQ 11
[    2.149525] ohci1394 0000:00:0d.0: sharing IRQ 11 with 0000:00:10.2
[    2.149536] ohci1394 0000:00:0d.0: sharing IRQ 11 with 0000:00:10.3
[    2.208527] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[ee002000-ee0027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.338790] ata1.00: ATA-7: ST3500641A, 3.AAE, max UDMA/100
[    2.338803] ata1.00: 976773168 sectors, multi 16: LBA48 
[    2.338877] ata1.01: ATAPI: PIONEER DVD-RW  DVR-111D, 1.19, max UDMA/66
[    2.350516] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.413779] ata1.00: configured for UDMA/100
[    2.426850] ata1.01: configured for UDMA/66
[    2.433389] scsi 0:0:0:0: Direct-Access     ATA      ST3500641A       3.AA PQ: 0 ANSI: 5
[    2.434384] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.439794] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.19 PQ: 0 ANSI: 5
[    2.441252] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.462752] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.462765] Uniform CD-ROM driver Revision: 3.20
[    2.463789] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.464399] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.464903] sd 0:0:0:0: [sda] Write Protect is off
[    2.464918] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.465077] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.465513]  sda: sda1 sda2 < sda5 >
[    2.508900] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.628566] ata2.00: ATA-7: Maxtor 6L300R0, BAJ41G20, max UDMA/133
[    2.628576] ata2.00: 586114704 sectors, multi 16: LBA48 
[    2.644410] ata2.00: configured for UDMA/133
[    2.644724] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6L300R0   BAJ4 PQ: 0 ANSI: 5
[    2.645264] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    2.646225] sd 1:0:0:0: [sdb] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    2.646344] sd 1:0:0:0: [sdb] Write Protect is off
[    2.646353] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.646411] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.646920]  sdb: sdb1
[    2.666859] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.846607] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.901780] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.901897] via-rhine 0000:00:12.0: found PCI INT A -> IRQ 10
[    2.901942] via-rhine 0000:00:12.0: sharing IRQ 10 with 0000:00:10.0
[    2.901954] via-rhine 0000:00:12.0: sharing IRQ 10 with 0000:00:10.1
[    2.916604] eth0: VIA Rhine II at 0xee001000, 00:40:63:e7:1a:1c, IRQ 10.
[    2.917327] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[    3.228354] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.228373] EXT4-fs (sda1): write access will be enabled during recovery
[    3.495099] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[004063500007bbde]
[    9.022372] EXT4-fs (sda1): recovery complete
[    9.023241] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.729012] usb 1-1: device descriptor read/64, error -110
[   27.728981] Adding 2819368k swap on /dev/sda5.  Priority:-1 extents:1 across:2819368k 
[   27.860263] udev: starting version 151
[   28.320357] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.792558] Linux agpgart interface v0.103
[   29.173991] lp: driver loaded but no devices found
[   29.247575] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[   29.455667] Linux video capture interface: v2.00
[   29.570613] agpgart-via 0000:00:00.0: AGP aperture is 512M @ 0xc0000000
[   29.597959] type=1505 audit(1275663597.814:2):  operation="profile_load" pid=398 name="/sbin/dhclient3"
[   29.598815] type=1505 audit(1275663597.814:3):  operation="profile_load" pid=398 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   29.599248] type=1505 audit(1275663597.814:4):  operation="profile_load" pid=398 name="/usr/lib/connman/scripts/dhclient-script"
[   29.661184] type=1505 audit(1275663597.878:5):  operation="profile_load" pid=419 name="/usr/sbin/ntpd"
[   29.731466] vga16fb: initializing
[   29.731491] vga16fb: mapped to 0xc00a0000
[   29.732338] fb0: VGA16 VGA frame buffer device
[   30.083497] ivtv: Start initialization, version 1.4.1
[   30.084145] ivtv0: Initializing card 0
[   30.084161] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   30.092412] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   30.188544] tveeprom 1-0050: Hauppauge model 23552, rev E492, serial# 9646529
[   30.188558] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   30.188569] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   30.188579] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   30.188589] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   30.188598] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   30.188606] tveeprom 1-0050: has radio
[   30.188615] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   30.746748] Console: switching to colour frame buffer device 80x30
[   30.770454] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   30.797908] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   30.830594] SGI XFS Quota Management subsystem
[   31.066811] RPC: Registered udp transport module.
[   31.066823] RPC: Registered tcp transport module.
[   31.066829] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   31.072392] usb 1-1: device descriptor read/64, error -110
[   31.103064] XFS mounting filesystem sdb1
[   31.228455] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   31.230458] tea5767 1-0060: type set to Philips TEA5767HN FM Radio
[   31.288004] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   31.303276] Ending clean XFS mount for filesystem: sdb1
[   31.388567] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   32.307633] tda9887 1-0043: creating new instance
[   32.307645] tda9887 1-0043: tda988[5/6/7] found
[   32.388889] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   32.485878] type=1505 audit(1275663600.703:6):  operation="profile_replace" pid=596 name="/sbin/dhclient3"
[   32.486828] type=1505 audit(1275663600.703:7):  operation="profile_replace" pid=596 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   32.487337] type=1505 audit(1275663600.703:8):  operation="profile_replace" pid=596 name="/usr/lib/connman/scripts/dhclient-script"
[   32.747860] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   32.757780] type=1505 audit(1275663600.975:9):  operation="profile_load" pid=601 name="/usr/bin/evince"
[   32.890579] type=1505 audit(1275663601.107:10):  operation="profile_load" pid=666 name="/usr/sbin/mysqld"
[   32.934681] type=1505 audit(1275663601.151:11):  operation="profile_load" pid=601 name="/usr/bin/evince-previewer"
[   33.742002] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   34.629699] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   34.690092] tuner-simple 1-0061: creating new instance
[   34.690108] tuner-simple 1-0061: type set to 57 (Philips FQ1236A MK4)
[   34.691162] IRQ 11/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   34.697354] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   34.697825] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   34.698251] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   34.698705] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   34.699125] ivtv0: Registered device radio0 for encoder radio
[   34.699138] ivtv0: Initialized card: WinTV PVR 500 (unit #1)
[B][   34.699655] ivtv1: Initializing card 1
[   34.699671] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   34.700336] lirc_dev: IR Remote Control driver registered, major 61 
[   34.715399] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   34.814858] tveeprom 2-0050: Hauppauge model 23552, rev E492, serial# 9646529
[   34.814871] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   34.814882] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   34.814892] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   34.814902] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   34.814911] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   34.814919] tveeprom 2-0050: has radio[/B]
[   34.814927] ivtv1: Correcting tveeprom data: no radio present on second unit
[   34.814935] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   34.960298] VIA 82xx Audio 0000:00:11.5: found PCI INT C -> IRQ 12
[   34.960359] VIA 82xx Audio 0000:00:11.5: sharing IRQ 12 with 0000:00:10.4
[   34.961129] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   35.060927] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   35.131179] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   35.131855] tda9887 2-0043: creating new instance
[   35.131863] tda9887 2-0043: tda988[5/6/7] found
[   35.182169] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   35.202306] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   35.228588] tuner-simple 2-0061: creating new instance
[   35.228604] tuner-simple 2-0061: type set to 57 (Philips FQ1236A MK4)
[   35.229658] IRQ 12/ivtv1: IRQF_DISABLED is not guaranteed on shared IRQs
[   35.234075] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   35.241196] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   35.243464] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   35.246437] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   35.246452] ivtv1: Initialized card: WinTV PVR 500 (unit #2)
[   35.250640] ivtv: End initialization
[   35.937840] ivtv 0000:02:09.0: firmware: requesting v4l-cx2341x-enc.fw
[   36.015905] bttv: driver version 0.9.18 loaded
[   36.015917] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   36.102785] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   36.257852] ivtv 0000:02:08.0: firmware: requesting v4l-cx2341x-enc.fw
[   36.300909] ivtv1: Encoder revision: 0x02060039
[   36.325449] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   36.373016] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
[   36.525007] ivtv0: Encoder revision: 0x02060039
[   36.611536] cx25840 1-0044: firmware: requesting v4l-cx25840.fw
[   36.810403] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   42.772953] [drm] Initialized drm 1.1.0 20060810
[   42.862743] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   42.905339] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   42.905398] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   42.905525] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   42.944205] eth0: no IPv6 routers present
[   43.332449] svc: failed to register lockdv1 RPC service (errno 97).
[   43.341032] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   43.346801] NFSD: starting 90-second grace period
[   46.398824] usb 1-1: device descriptor read/64, error -110
[   56.708572] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   57.531794] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   61.608568] usb 1-1: device descriptor read/64, error -110
[   61.824493] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   66.842715] usb 1-1: device descriptor read/8, error -110
[   71.960379] usb 1-1: device descriptor read/8, error -110
[   72.176432] usb 1-1: new high speed USB device using ehci_hcd and address 5
[   77.194508] usb 1-1: device descriptor read/8, error -110
[   82.312178] usb 1-1: device descriptor read/8, error -110
[   82.416008] hub 1-0:1.0: unable to enumerate USB device on port 1
[   82.723962] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   97.829617] usb 2-1: device descriptor read/64, error -110
[  107.207431] Marking TSC unstable due to cpufreq changes
[  107.207660] Switching to clocksource pit
[  113.036131] usb 2-1: device descriptor read/64, error -110
[  113.251929] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  128.355898] usb 2-1: device descriptor read/64, error -110
[  143.563789] usb 2-1: device descriptor read/64, error -110
[  143.787742] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  148.806141] usb 2-1: device descriptor read/8, error -110
[  153.924273] usb 2-1: device descriptor read/8, error -110
[  154.138141] usb 2-1: new full speed USB device using uhci_hcd and address 5
[  159.157290] usb 2-1: device descriptor read/8, error -110
[  164.274425] usb 2-1: device descriptor read/8, error -110
[  164.376694] hub 2-0:1.0: unable to enumerate USB device on port 1
[  164.616543] usb 3-2: new low speed USB device using uhci_hcd and address 2
[  164.776047] usb 3-2: configuration #1 chosen from 1 choice
[  165.081228] usbcore: registered new interface driver hiddev
[  165.099499] input: HID 1267:0103 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input1
[  165.101437] generic-usb 0003:1267:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:10.1-2/input0
[  165.130320] input: HID 1267:0103 as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input2
[  165.130659] generic-usb 0003:1267:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:10.1-2/input1
[  165.130751] usbcore: registered new interface driver usbhid
[  165.130760] usbhid: v2.6:USB HID core driver
```

Devices found:

```

@mythtv:~$ ls -l /dev
total 0
crw-rw----+ 1 root audio    14,  12 2010-06-04 11:00 adsp
crw-------  1 root video    10, 175 2010-06-04 10:59 agpgart
crw-rw----+ 1 root audio    14,   4 2010-06-04 11:00 audio
drwxr-xr-x  2 root root         660 2010-06-04 10:59 block
drwxr-xr-x  2 root root         100 2010-06-04 10:59 bsg
drwxr-xr-x  3 root root          60 2010-06-04 10:59 bus
lrwxrwxrwx  1 root root           3 2010-06-04 10:59 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2010-06-04 10:59 cdrw -> sr0
drwxr-xr-x  2 root root        3240 2010-06-04 11:02 char
crw-------  1 root root      5,   1 2010-06-04 11:00 console
lrwxrwxrwx  1 root root          11 2010-06-04 10:59 core -> /proc/kcore
crw-rw----  1 root root     10,  58 2010-06-04 10:59 cpu_dma_latency
drwxr-xr-x  5 root root         100 2010-06-04 10:59 disk
drwxr-xr-x  2 root root          60 2010-06-04 11:00 dri
crw-rw----+ 1 root audio    14,   3 2010-06-04 11:00 dsp
lrwxrwxrwx  1 root root           3 2010-06-04 10:59 dvd -> sr0
lrwxrwxrwx  1 root root           3 2010-06-04 10:59 dvdrw -> sr0
crw-rw----  1 root root     10,  61 2010-06-04 10:59 ecryptfs
crw-rw----  1 root video    29,   0 2010-06-04 10:59 fb0
lrwxrwxrwx  1 root root          13 2010-06-04 10:59 fd -> /proc/self/fd
crw-rw-rw-  1 root root      1,   7 2010-06-04 10:59 full
crw-rw-rw-  1 root fuse     10, 229 2010-06-04 10:59 fuse
crw-rw----  1 root root    251,   0 2010-06-04 11:02 hidraw0
crw-rw----  1 root root    251,   1 2010-06-04 11:02 hidraw1
drwxr-xr-x  4 root root         180 2010-06-04 11:02 input
crw-rw----  1 root root      1,  11 2010-06-04 10:59 kmsg
lrwxrwxrwx  1 root root          19 2010-06-04 11:00 lircd -> /var/run/lirc/lircd
srw-rw-rw-  1 root root           0 2010-06-04 11:00 log
brw-rw----  1 root disk      7,   0 2010-06-04 10:59 loop0
brw-rw----  1 root disk      7,   1 2010-06-04 10:59 loop1
brw-rw----  1 root disk      7,   2 2010-06-04 10:59 loop2
brw-rw----  1 root disk      7,   3 2010-06-04 10:59 loop3
brw-rw----  1 root disk      7,   4 2010-06-04 10:59 loop4
brw-rw----  1 root disk      7,   5 2010-06-04 10:59 loop5
brw-rw----  1 root disk      7,   6 2010-06-04 10:59 loop6
brw-rw----  1 root disk      7,   7 2010-06-04 10:59 loop7
drwxr-xr-x  2 root root          60 2010-06-04 10:59 mapper
crw-r-----  1 root kmem      1,   1 2010-06-04 10:59 mem
crw-rw----+ 1 root audio    14,   0 2010-06-04 11:00 mixer
drwxr-xr-x  2 root root          60 2010-06-03 02:51 net
crw-rw----  1 root root     10,  57 2010-06-04 10:59 network_latency
crw-rw----  1 root root     10,  56 2010-06-04 10:59 network_throughput
crw-rw-rw-  1 root root      1,   3 2010-06-04 10:59 null
crw-rw----  1 root root      1,  12 2010-06-04 10:59 oldmem
drwxr-xr-x  2 root root          60 2010-06-04 10:59 pktcdvd
crw-r-----  1 root kmem      1,   4 2010-06-04 10:59 port
crw-------  1 root root    108,   0 2010-06-04 10:59 ppp
crw-rw----  1 root root     10,   1 2010-06-04 10:59 psaux
crw-rw-rw-  1 root tty       5,   2 2010-06-04 11:07 ptmx
drwxr-xr-x  2 root root           0 2009-10-16 02:01 pts
crw-rw----+ 1 root video    81,   4 2010-06-04 11:00 radio0
brw-rw----  1 root disk      1,   0 2010-06-04 10:59 ram0
brw-rw----  1 root disk      1,   1 2010-06-04 10:59 ram1
brw-rw----  1 root disk      1,  10 2010-06-04 10:59 ram10
brw-rw----  1 root disk      1,  11 2010-06-04 10:59 ram11
brw-rw----  1 root disk      1,  12 2010-06-04 10:59 ram12
brw-rw----  1 root disk      1,  13 2010-06-04 10:59 ram13
brw-rw----  1 root disk      1,  14 2010-06-04 10:59 ram14
brw-rw----  1 root disk      1,  15 2010-06-04 10:59 ram15
brw-rw----  1 root disk      1,   2 2010-06-04 10:59 ram2
brw-rw----  1 root disk      1,   3 2010-06-04 10:59 ram3
brw-rw----  1 root disk      1,   4 2010-06-04 10:59 ram4
brw-rw----  1 root disk      1,   5 2010-06-04 10:59 ram5
brw-rw----  1 root disk      1,   6 2010-06-04 10:59 ram6
brw-rw----  1 root disk      1,   7 2010-06-04 10:59 ram7
brw-rw----  1 root disk      1,   8 2010-06-04 10:59 ram8
brw-rw----  1 root disk      1,   9 2010-06-04 10:59 ram9
crw-rw-rw-  1 root root      1,   8 2010-06-04 10:59 random
crw-rw-r--+ 1 root root     10,  62 2010-06-04 10:59 rfkill
lrwxrwxrwx  1 root root           4 2010-06-04 10:59 root -> sda1
lrwxrwxrwx  1 root root           4 2010-06-04 10:59 rtc -> rtc0
crw-rw----  1 root root    254,   0 2010-06-04 10:59 rtc0
lrwxrwxrwx  1 root root           3 2010-06-04 10:59 scd0 -> sr0
brw-rw----  1 root disk      8,   0 2010-06-04 10:59 sda
brw-rw----  1 root disk      8,   1 2010-06-04 10:59 sda1
brw-rw----  1 root disk      8,   2 2010-06-04 10:59 sda2
brw-rw----  1 root disk      8,   5 2010-06-04 10:59 sda5
brw-rw----  1 root disk      8,  16 2010-06-04 10:59 sdb
brw-rw----  1 root disk      8,  17 2010-06-04 10:59 sdb1
crw-rw----+ 1 root audio    14,   1 2010-06-04 10:59 sequencer
crw-rw----+ 1 root audio    14,   8 2010-06-04 10:59 sequencer2
crw-rw----  1 root disk     21,   0 2010-06-04 10:59 sg0
crw-rw----  1 root cdrom    21,   1 2010-06-04 10:59 sg1
crw-rw----  1 root disk     21,   2 2010-06-04 10:59 sg2
drwxrwxrwt  2 root root          40 2010-06-04 10:59 shm
crw-rw----  1 root root     10, 231 2010-06-04 10:59 snapshot
drwxr-xr-x  3 root root         200 2010-06-04 11:00 snd
lrwxrwxrwx  1 root root          24 2010-06-04 10:59 sndstat -> /proc/asound/oss/sndstat
brw-rw----+ 1 root cdrom    11,   0 2010-06-04 10:59 sr0
lrwxrwxrwx  1 root root          15 2010-06-04 10:59 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2010-06-04 10:59 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2010-06-04 10:59 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root tty       5,   0 2010-06-04 10:59 tty
crw--w----  1 root root      4,   0 2010-06-04 10:59 tty0
crw-------  1 root root      4,   1 2010-06-04 11:00 tty1
crw--w----  1 root tty       4,  10 2010-06-04 10:59 tty10
crw--w----  1 root tty       4,  11 2010-06-04 10:59 tty11
crw--w----  1 root tty       4,  12 2010-06-04 10:59 tty12
crw--w----  1 root tty       4,  13 2010-06-04 10:59 tty13
crw--w----  1 root tty       4,  14 2010-06-04 10:59 tty14
crw--w----  1 root tty       4,  15 2010-06-04 10:59 tty15
crw--w----  1 root tty       4,  16 2010-06-04 10:59 tty16
crw--w----  1 root tty       4,  17 2010-06-04 10:59 tty17
crw--w----  1 root tty       4,  18 2010-06-04 10:59 tty18
crw--w----  1 root tty       4,  19 2010-06-04 10:59 tty19
crw-------  1 root root      4,   2 2010-06-04 11:00 tty2
crw--w----  1 root tty       4,  20 2010-06-04 10:59 tty20
crw--w----  1 root tty       4,  21 2010-06-04 10:59 tty21
crw--w----  1 root tty       4,  22 2010-06-04 10:59 tty22
crw--w----  1 root tty       4,  23 2010-06-04 10:59 tty23
crw--w----  1 root tty       4,  24 2010-06-04 10:59 tty24
crw--w----  1 root tty       4,  25 2010-06-04 10:59 tty25
crw--w----  1 root tty       4,  26 2010-06-04 10:59 tty26
crw--w----  1 root tty       4,  27 2010-06-04 10:59 tty27
crw--w----  1 root tty       4,  28 2010-06-04 10:59 tty28
crw--w----  1 root tty       4,  29 2010-06-04 10:59 tty29
crw-------  1 root root      4,   3 2010-06-04 11:00 tty3
crw--w----  1 root tty       4,  30 2010-06-04 10:59 tty30
crw--w----  1 root tty       4,  31 2010-06-04 10:59 tty31
crw--w----  1 root tty       4,  32 2010-06-04 10:59 tty32
crw--w----  1 root tty       4,  33 2010-06-04 10:59 tty33
crw--w----  1 root tty       4,  34 2010-06-04 10:59 tty34
crw--w----  1 root tty       4,  35 2010-06-04 10:59 tty35
crw--w----  1 root tty       4,  36 2010-06-04 10:59 tty36
crw--w----  1 root tty       4,  37 2010-06-04 10:59 tty37
crw--w----  1 root tty       4,  38 2010-06-04 10:59 tty38
crw--w----  1 root tty       4,  39 2010-06-04 10:59 tty39
crw-------  1 root root      4,   4 2010-06-04 11:00 tty4
crw--w----  1 root tty       4,  40 2010-06-04 10:59 tty40
crw--w----  1 root tty       4,  41 2010-06-04 10:59 tty41
crw--w----  1 root tty       4,  42 2010-06-04 10:59 tty42
crw--w----  1 root tty       4,  43 2010-06-04 10:59 tty43
crw--w----  1 root tty       4,  44 2010-06-04 10:59 tty44
crw--w----  1 root tty       4,  45 2010-06-04 10:59 tty45
crw--w----  1 root tty       4,  46 2010-06-04 10:59 tty46
crw--w----  1 root tty       4,  47 2010-06-04 10:59 tty47
crw--w----  1 root tty       4,  48 2010-06-04 10:59 tty48
crw--w----  1 root tty       4,  49 2010-06-04 10:59 tty49
crw-------  1 root root      4,   5 2010-06-04 11:00 tty5
crw--w----  1 root tty       4,  50 2010-06-04 10:59 tty50
crw--w----  1 root tty       4,  51 2010-06-04 10:59 tty51
crw--w----  1 root tty       4,  52 2010-06-04 10:59 tty52
crw--w----  1 root tty       4,  53 2010-06-04 10:59 tty53
crw--w----  1 root tty       4,  54 2010-06-04 10:59 tty54
crw--w----  1 root tty       4,  55 2010-06-04 10:59 tty55
crw--w----  1 root tty       4,  56 2010-06-04 10:59 tty56
crw--w----  1 root tty       4,  57 2010-06-04 10:59 tty57
crw--w----  1 root tty       4,  58 2010-06-04 10:59 tty58
crw--w----  1 root tty       4,  59 2010-06-04 10:59 tty59
crw-------  1 root root      4,   6 2010-06-04 11:00 tty6
crw--w----  1 root tty       4,  60 2010-06-04 10:59 tty60
crw--w----  1 root tty       4,  61 2010-06-04 10:59 tty61
crw--w----  1 root tty       4,  62 2010-06-04 10:59 tty62
crw--w----  1 root tty       4,  63 2010-06-04 10:59 tty63
crw--w----  1 root root      4,   7 2010-06-04 10:59 tty7
crw--w----  1 root tty       4,   8 2010-06-04 10:59 tty8
crw--w----  1 root tty       4,   9 2010-06-04 10:59 tty9
crw-rw----  1 root dialout   4,  64 2010-06-04 10:59 ttyS0
crw-rw----  1 root dialout   4,  65 2010-06-04 10:59 ttyS1
crw-rw----  1 root dialout   4,  66 2010-06-04 10:59 ttyS2
crw-rw----  1 root dialout   4,  67 2010-06-04 10:59 ttyS3
crw-rw-rw-  1 root root      1,   9 2010-06-04 10:59 urandom
crw-rw----  1 root root    252,   0 2010-06-04 10:59 usbmon0
crw-rw----  1 root root    252,   1 2010-06-04 10:59 usbmon1
crw-rw----  1 root root    252,   2 2010-06-04 10:59 usbmon2
crw-rw----  1 root root    252,   3 2010-06-04 10:59 usbmon3
crw-rw----  1 root root    252,   4 2010-06-04 10:59 usbmon4
crw-rw----  1 root root    252,   5 2010-06-04 10:59 usbmon5
drwxr-xr-x  3 root root          60 2010-06-04 11:00 v4l
crw-rw----+ 1 root video    81,   2 2010-06-04 11:00 vbi0
crw-rw----+ 1 root video    81,   7 2010-06-04 11:00 vbi1
crw-rw----  1 root tty       7,   0 2010-06-04 10:59 vcs
crw-rw----  1 root tty       7,   1 2010-06-04 10:59 vcs1
crw-rw----  1 root tty       7,   2 2010-06-04 10:59 vcs2
crw-rw----  1 root tty       7,   3 2010-06-04 10:59 vcs3
crw-rw----  1 root tty       7,   4 2010-06-04 10:59 vcs4
crw-rw----  1 root tty       7,   5 2010-06-04 10:59 vcs5
crw-rw----  1 root tty       7,   6 2010-06-04 10:59 vcs6
crw-rw----  1 root tty       7,   7 2010-06-04 10:59 vcs7
crw-rw----  1 root tty       7, 128 2010-06-04 10:59 vcsa
crw-rw----  1 root tty       7, 129 2010-06-04 10:59 vcsa1
crw-rw----  1 root tty       7, 130 2010-06-04 10:59 vcsa2
crw-rw----  1 root tty       7, 131 2010-06-04 10:59 vcsa3
crw-rw----  1 root tty       7, 132 2010-06-04 10:59 vcsa4
crw-rw----  1 root tty       7, 133 2010-06-04 10:59 vcsa5
crw-rw----  1 root tty       7, 134 2010-06-04 10:59 vcsa6
crw-rw----  1 root tty       7, 135 2010-06-04 10:59 vcsa7
crw-rw----  1 root root     10,  63 2010-06-04 10:59 vga_arbiter
crw-rw----+ 1 root video    81,   0 2010-06-04 11:00 video0
crw-rw----+ 1 root video    81,   5 2010-06-04 11:00 video1
crw-rw----+ 1 root video    81,   3 2010-06-04 11:00 video24
crw-rw----+ 1 root video    81,   8 2010-06-04 11:00 video25
crw-rw----+ 1 root video    81,   1 2010-06-04 11:00 video32
crw-rw----+ 1 root video    81,   6 2010-06-04 11:00 video33
crw-rw-rw-  1 root root      1,   5 2010-06-04 10:59 zero
```

---

