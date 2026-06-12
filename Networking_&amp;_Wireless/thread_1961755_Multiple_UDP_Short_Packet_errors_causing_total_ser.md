---
title: "Multiple UDP Short Packet errors causing total server lockup"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by abyrne on 2012-04-19
Hi all,

I'm running a low-traffic headless home server with Ubuntu Server 11.10 installed. The server mainly just hosts my website as well as a Transmission WebUI. I very recently replaced my old dying onboard NIC with a [brand new one]("http://www.bestbuy.com/site/Dynex%26%23153%3B+-+Gigabit+PCI+Desktop+Adapter/8858569.p?id=1209774346613&skuId=8858569&st=dynex%20gigabit&cp=1&lp=1"), but now the new NIC is giving me a bit of a stability issue. The system would totally lock up without any response from Ctrl-Alt-Del or any kernel magic keys, forcing a hard reset. A look into the kernel logs reveal this final error before the system went under:
```

Apr 17 10:31:07 LXDE kernel: [56711.217785] UDP: short packet: From 184.75.122.186:51413 16642/38 to 192.168.1.5:51413
Apr 17 11:06:18 LXDE kernel: [58822.256692] UDP: short packet: From 184.75.122.186:51413 16642/38 to 192.168.1.5:51413
Apr 17 11:41:34 LXDE kernel: [60938.505825] UDP: short packet: From 184.75.122.186:51413 16642/38 to 192.168.1.5:51413

```
A little research lead me to believe that this was being caused by bittorrent, and lo and behold disabling transmission-daemon stopped the lockups. 

I hope it's not a hardware issue, but it might just come to that. However, totally disabling services that use UDP is not an option. Anyone have any ideas to get the NIC working?

For the sake of completeness:
Section of kern.log
```
Apr 17 14:14:07 LXDE kernel: Kernel logging (proc) stopped.
Apr 17 14:14:46 LXDE kernel: imklog 5.8.1, log source = /proc/kmsg started.
Apr 17 14:14:46 LXDE kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 17 14:14:46 LXDE kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 17 14:14:46 LXDE kernel: [    0.000000] Linux version 3.0.0-17-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
Apr 17 14:14:46 LXDE kernel: [    0.000000] KERNEL supported cpus:
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Intel GenuineIntel
Apr 17 14:14:46 LXDE kernel: [    0.000000]   AMD AuthenticAMD
Apr 17 14:14:46 LXDE kernel: [    0.000000]   NSC Geode by NSC
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Cyrix CyrixInstead
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Centaur CentaurHauls
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 17 14:14:46 LXDE kernel: [    0.000000]   UMC UMC UMC UMC
Apr 17 14:14:46 LXDE kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002dff0000 (usable)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 000000002dff0000 - 000000002dff3000 (ACPI NVS)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 000000002dff3000 - 000000002e000000 (ACPI data)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 17 14:14:46 LXDE kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Apr 17 14:14:46 LXDE kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Apr 17 14:14:46 LXDE kernel: [    0.000000] DMI 2.3 present.
Apr 17 14:14:46 LXDE kernel: [    0.000000] DMI: Compaq Presario 06 DA235A-ABA 6410nx NA910/KM266-8235, BIOS AM37320 08/01/2003
Apr 17 14:14:46 LXDE kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr 17 14:14:46 LXDE kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Apr 17 14:14:46 LXDE kernel: [    0.000000] last_pfn = 0x2dff0 max_arch_pfn = 0x100000
Apr 17 14:14:46 LXDE kernel: [    0.000000] MTRR default type: uncachable
Apr 17 14:14:46 LXDE kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 17 14:14:46 LXDE kernel: [    0.000000]   00000-9FFFF write-back
Apr 17 14:14:46 LXDE kernel: [    0.000000]   A0000-BFFFF uncachable
Apr 17 14:14:46 LXDE kernel: [    0.000000]   C0000-C7FFF write-protect
Apr 17 14:14:46 LXDE kernel: [    0.000000]   C8000-FFFFF uncachable
Apr 17 14:14:46 LXDE kernel: [    0.000000] MTRR variable ranges enabled:
Apr 17 14:14:46 LXDE kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Apr 17 14:14:46 LXDE kernel: [    0.000000]   1 base 02E000000 mask FFE000000 uncachable
Apr 17 14:14:46 LXDE kernel: [    0.000000]   2 base 030000000 mask FF0000000 uncachable
Apr 17 14:14:46 LXDE kernel: [    0.000000]   3 base 0E8000000 mask FFC000000 write-combining
Apr 17 14:14:46 LXDE kernel: [    0.000000]   4 base 0E8000000 mask FFC000000 write-combining
Apr 17 14:14:46 LXDE kernel: [    0.000000]   5 disabled
Apr 17 14:14:46 LXDE kernel: [    0.000000]   6 disabled
Apr 17 14:14:46 LXDE kernel: [    0.000000]   7 disabled
Apr 17 14:14:46 LXDE kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 17 14:14:46 LXDE kernel: [    0.000000] found SMP MP-table at [c00f61a0] f61a0
Apr 17 14:14:46 LXDE kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Apr 17 14:14:46 LXDE kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Apr 17 14:14:46 LXDE kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000002dff0000
Apr 17 14:14:46 LXDE kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr 17 14:14:46 LXDE kernel: [    0.000000]  0000400000 - 002dc00000 page 2M
Apr 17 14:14:46 LXDE kernel: [    0.000000]  002dc00000 - 002dff0000 page 4k
Apr 17 14:14:46 LXDE kernel: [    0.000000] kernel direct mapping tables up to 2dff0000 @ 1bfb000-1c00000
Apr 17 14:14:46 LXDE kernel: [    0.000000] RAMDISK: 2cb93000 - 2d895000
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: RSDP 000f7c50 00014 (v00 KM266 )
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: RSDT 2dff3000 0002C (v01 KM266  AWRDACPI 42302E31 AWRD 00000000)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: FACP 2dff3040 00074 (v01 KM266  AWRDACPI 42302E31 AWRD 00000000)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: DSDT 2dff30c0 04329 (v01 KM266  AWRDACPI 00001000 MSFT 0100000E)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: FACS 2dff0000 00040
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: APIC 2dff7400 0005A (v01 KM266  AWRDACPI 42302E31 AWRD 00000000)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 17 14:14:46 LXDE kernel: [    0.000000] 0MB HIGHMEM available.
Apr 17 14:14:46 LXDE kernel: [    0.000000] 735MB LOWMEM available.
Apr 17 14:14:46 LXDE kernel: [    0.000000]   mapped low ram: 0 - 2dff0000
Apr 17 14:14:46 LXDE kernel: [    0.000000]   low ram: 0 - 2dff0000
Apr 17 14:14:46 LXDE kernel: [    0.000000] Zone PFN ranges:
Apr 17 14:14:46 LXDE kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Normal   0x00001000 -> 0x0002dff0
Apr 17 14:14:46 LXDE kernel: [    0.000000]   HighMem  empty
Apr 17 14:14:46 LXDE kernel: [    0.000000] Movable zone start PFN for each node
Apr 17 14:14:46 LXDE kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 17 14:14:46 LXDE kernel: [    0.000000]     0: 0x00000010 -> 0x000000a0
Apr 17 14:14:46 LXDE kernel: [    0.000000]     0: 0x00000100 -> 0x0002dff0
Apr 17 14:14:46 LXDE kernel: [    0.000000] On node 0 totalpages: 188288
Apr 17 14:14:46 LXDE kernel: [    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map eda2f200
Apr 17 14:14:46 LXDE kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 17 14:14:46 LXDE kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 17 14:14:46 LXDE kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Normal zone: 1440 pages used for memmap
Apr 17 14:14:46 LXDE kernel: [    0.000000]   Normal zone: 182864 pages, LIFO batch:31
Apr 17 14:14:46 LXDE kernel: [    0.000000] Using APIC driver default
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 17 14:14:46 LXDE kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 17 14:14:46 LXDE kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 17 14:14:46 LXDE kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 17 14:14:46 LXDE kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Apr 17 14:14:46 LXDE kernel: [    0.000000] nr_irqs_gsi: 40
Apr 17 14:14:46 LXDE kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr 17 14:14:46 LXDE kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr 17 14:14:46 LXDE kernel: [    0.000000] Allocating PCI resources starting at 2e000000 (gap: 2e000000:d0c00000)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 17 14:14:46 LXDE kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Apr 17 14:14:46 LXDE kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @ec400000 s26240 r0 d22912 u4194304
Apr 17 14:14:46 LXDE kernel: [    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
Apr 17 14:14:46 LXDE kernel: [    0.000000] pcpu-alloc: [0] 0 
Apr 17 14:14:46 LXDE kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 186816
Apr 17 14:14:46 LXDE kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=3c1af128-84d2-4b9a-a7b6-c3558bc28173 ro splash quiet vt.handoff=7
Apr 17 14:14:46 LXDE kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Initializing CPU#0
Apr 17 14:14:46 LXDE kernel: [    0.000000] allocated 3014144 bytes of page_cgroup
Apr 17 14:14:46 LXDE kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 17 14:14:46 LXDE kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Memory: 720568k/753600k available (5340k kernel code, 32584k reserved, 2595k data, 696k init, 0k highmem)
Apr 17 14:14:46 LXDE kernel: [    0.000000] virtual kernel memory layout:
Apr 17 14:14:46 LXDE kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]     vmalloc : 0xee7f0000 - 0xff7fe000   ( 272 MB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xedff0000   ( 735 MB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]       .data : 0xc15371c4 - 0xc17c0140   (2595 kB)
Apr 17 14:14:46 LXDE kernel: [    0.000000]       .text : 0xc1000000 - 0xc15371c4   (5340 kB)
Apr 17 14:14:46 LXDE kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 17 14:14:46 LXDE kernel: [    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Apr 17 14:14:46 LXDE kernel: [    0.000000] Hierarchical RCU implementation.
Apr 17 14:14:46 LXDE kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Apr 17 14:14:46 LXDE kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Apr 17 14:14:46 LXDE kernel: [    0.000000] CPU 0 irqstacks, hard=ec008000 soft=ec00a000
Apr 17 14:14:46 LXDE kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr 17 14:14:46 LXDE kernel: [    0.000000] Console: colour dummy device 80x25
Apr 17 14:14:46 LXDE kernel: [    0.000000] console [tty0] enabled
Apr 17 14:14:46 LXDE kernel: [    0.000000] Fast TSC calibration using PIT
Apr 17 14:14:46 LXDE kernel: [    0.000000] Detected 1665.543 MHz processor.
Apr 17 14:14:46 LXDE kernel: [    0.008006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3331.08 BogoMIPS (lpj=6662172)
Apr 17 14:14:46 LXDE kernel: [    0.008016] pid_max: default: 32768 minimum: 301
Apr 17 14:14:46 LXDE kernel: [    0.008064] Security Framework initialized
Apr 17 14:14:46 LXDE kernel: [    0.008115] AppArmor: AppArmor initialized
Apr 17 14:14:46 LXDE kernel: [    0.008119] Yama: becoming mindful.
Apr 17 14:14:46 LXDE kernel: [    0.008232] Mount-cache hash table entries: 512
Apr 17 14:14:46 LXDE kernel: [    0.008510] Initializing cgroup subsys cpuacct
Apr 17 14:14:46 LXDE kernel: [    0.008522] Initializing cgroup subsys memory
Apr 17 14:14:46 LXDE kernel: [    0.008541] Initializing cgroup subsys devices
Apr 17 14:14:46 LXDE kernel: [    0.008547] Initializing cgroup subsys freezer
Apr 17 14:14:46 LXDE kernel: [    0.008551] Initializing cgroup subsys net_cls
Apr 17 14:14:46 LXDE kernel: [    0.008557] Initializing cgroup subsys blkio
Apr 17 14:14:46 LXDE kernel: [    0.008571] Initializing cgroup subsys perf_event
Apr 17 14:14:46 LXDE kernel: [    0.008631] mce: CPU supports 4 MCE banks
Apr 17 14:14:46 LXDE kernel: [    0.008737] SMP alternatives: switching to UP code
Apr 17 14:14:46 LXDE kernel: [    0.019481] Freeing SMP alternatives: 24k freed
Apr 17 14:14:46 LXDE kernel: [    0.019552] ACPI: Core revision 20110413
Apr 17 14:14:46 LXDE kernel: [    0.026044] ftrace: allocating 24903 entries in 49 pages
Apr 17 14:14:46 LXDE kernel: [    0.028252] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 17 14:14:46 LXDE kernel: [    0.029586] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 17 14:14:46 LXDE kernel: [    0.071071] CPU0: AMD Athlon(tm) XP 2000+ stepping 02
Apr 17 14:14:46 LXDE kernel: [    0.072003] Performance Events: AMD PMU driver.
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... version:                0
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... bit width:              48
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... generic registers:      4
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... value mask:             0000ffffffffffff
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... max period:             00007fffffffffff
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... fixed-purpose events:   0
Apr 17 14:14:46 LXDE kernel: [    0.072003] ... event mask:             000000000000000f
Apr 17 14:14:46 LXDE kernel: [    0.072003] Brought up 1 CPUs
Apr 17 14:14:46 LXDE kernel: [    0.072003] Total of 1 processors activated (3331.08 BogoMIPS).
Apr 17 14:14:46 LXDE kernel: [    0.072003] devtmpfs: initialized
Apr 17 14:14:46 LXDE kernel: [    0.072003] PM: Registering ACPI NVS region at 2dff0000 (12288 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.073572] print_constraints: dummy: 
Apr 17 14:14:46 LXDE kernel: [    0.073616] Time: 18:14:35  Date: 04/17/12
Apr 17 14:14:46 LXDE kernel: [    0.073702] NET: Registered protocol family 16
Apr 17 14:14:46 LXDE kernel: [    0.073939] EISA bus registered
Apr 17 14:14:46 LXDE kernel: [    0.073963] ACPI: bus type pci registered
Apr 17 14:14:46 LXDE kernel: [    0.080061] PCI: PCI BIOS revision 2.10 entry at 0xfba00, last bus=1
Apr 17 14:14:46 LXDE kernel: [    0.080066] PCI: Using configuration type 1 for base access
Apr 17 14:14:46 LXDE kernel: [    0.081944] bio: create slab <bio-0> at 0
Apr 17 14:14:46 LXDE kernel: [    0.083039] ACPI: EC: Look up EC in DSDT
Apr 17 14:14:46 LXDE kernel: [    0.087494] ACPI: Interpreter enabled
Apr 17 14:14:46 LXDE kernel: [    0.087504] ACPI: (supports S0 S1 S3 S4 S5)
Apr 17 14:14:46 LXDE kernel: [    0.087543] ACPI: Using IOAPIC for interrupt routing
Apr 17 14:14:46 LXDE kernel: [    0.093236] ACPI: No dock devices found.
Apr 17 14:14:46 LXDE kernel: [    0.093241] HEST: Table not found.
Apr 17 14:14:46 LXDE kernel: [    0.093249] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Apr 17 14:14:46 LXDE kernel: [    0.093360] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr 17 14:14:46 LXDE kernel: [    0.093551] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Apr 17 14:14:46 LXDE kernel: [    0.093556] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Apr 17 14:14:46 LXDE kernel: [    0.093561] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Apr 17 14:14:46 LXDE kernel: [    0.093565] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Apr 17 14:14:46 LXDE kernel: [    0.093569] pci_root PNP0A03:00: host bridge window [mem 0x2e000000-0xfebfffff] (ignored)
Apr 17 14:14:46 LXDE kernel: [    0.093599] pci 0000:00:00.0: [1106:3116] type 0 class 0x000600
Apr 17 14:14:46 LXDE kernel: [    0.093615] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xebffffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.093699] pci 0000:00:01.0: [1106:b091] type 1 class 0x000604
Apr 17 14:14:46 LXDE kernel: [    0.093748] pci 0000:00:01.0: supports D1
Apr 17 14:14:46 LXDE kernel: [    0.093777] pci 0000:00:08.0: [10ec:8169] type 0 class 0x000200
Apr 17 14:14:46 LXDE kernel: [    0.093795] pci 0000:00:08.0: reg 10: [io  0xc000-0xc0ff]
Apr 17 14:14:46 LXDE kernel: [    0.093806] pci 0000:00:08.0: reg 14: [mem 0xef000000-0xef0000ff]
Apr 17 14:14:46 LXDE kernel: [    0.093844] pci 0000:00:08.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.093871] pci 0000:00:08.0: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.093875] pci 0000:00:08.0: PME# supported from D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.093881] pci 0000:00:08.0: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.093903] pci 0000:00:09.0: [1106:3038] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.093947] pci 0000:00:09.0: reg 20: [io  0xc400-0xc41f]
Apr 17 14:14:46 LXDE kernel: [    0.093986] pci 0000:00:09.0: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.093990] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.093995] pci 0000:00:09.0: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094021] pci 0000:00:09.1: [1106:3038] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094064] pci 0000:00:09.1: reg 20: [io  0xc800-0xc81f]
Apr 17 14:14:46 LXDE kernel: [    0.094104] pci 0000:00:09.1: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094108] pci 0000:00:09.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094113] pci 0000:00:09.1: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094135] pci 0000:00:09.2: [1106:3104] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094152] pci 0000:00:09.2: reg 10: [mem 0xef001000-0xef0010ff]
Apr 17 14:14:46 LXDE kernel: [    0.094219] pci 0000:00:09.2: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094222] pci 0000:00:09.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094227] pci 0000:00:09.2: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094255] pci 0000:00:0a.0: [11c1:044e] type 0 class 0x000780
Apr 17 14:14:46 LXDE kernel: [    0.094272] pci 0000:00:0a.0: reg 10: [mem 0xef002000-0xef0020ff]
Apr 17 14:14:46 LXDE kernel: [    0.094283] pci 0000:00:0a.0: reg 14: [io  0xcc00-0xcc07]
Apr 17 14:14:46 LXDE kernel: [    0.094294] pci 0000:00:0a.0: reg 18: [io  0xd000-0xd0ff]
Apr 17 14:14:46 LXDE kernel: [    0.094348] pci 0000:00:0a.0: supports D2
Apr 17 14:14:46 LXDE kernel: [    0.094352] pci 0000:00:0a.0: PME# supported from D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094357] pci 0000:00:0a.0: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094380] pci 0000:00:0b.0: [10ec:8139] type 0 class 0x000200
Apr 17 14:14:46 LXDE kernel: [    0.094397] pci 0000:00:0b.0: reg 10: [io  0xd400-0xd4ff]
Apr 17 14:14:46 LXDE kernel: [    0.094408] pci 0000:00:0b.0: reg 14: [mem 0xef003000-0xef0030ff]
Apr 17 14:14:46 LXDE kernel: [    0.094446] pci 0000:00:0b.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.094473] pci 0000:00:0b.0: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094476] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094482] pci 0000:00:0b.0: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094509] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094553] pci 0000:00:10.0: reg 20: [io  0xd800-0xd81f]
Apr 17 14:14:46 LXDE kernel: [    0.094592] pci 0000:00:10.0: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094596] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094601] pci 0000:00:10.0: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094623] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094666] pci 0000:00:10.1: reg 20: [io  0xdc00-0xdc1f]
Apr 17 14:14:46 LXDE kernel: [    0.094706] pci 0000:00:10.1: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094709] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094714] pci 0000:00:10.1: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094736] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094780] pci 0000:00:10.2: reg 20: [io  0xe000-0xe01f]
Apr 17 14:14:46 LXDE kernel: [    0.094820] pci 0000:00:10.2: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094823] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094828] pci 0000:00:10.2: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094851] pci 0000:00:10.3: [1106:3104] type 0 class 0x000c03
Apr 17 14:14:46 LXDE kernel: [    0.094868] pci 0000:00:10.3: reg 10: [mem 0xef004000-0xef0040ff]
Apr 17 14:14:46 LXDE kernel: [    0.094934] pci 0000:00:10.3: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.094938] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr 17 14:14:46 LXDE kernel: [    0.094943] pci 0000:00:10.3: PME# disabled
Apr 17 14:14:46 LXDE kernel: [    0.094972] pci 0000:00:11.0: [1106:3177] type 0 class 0x000601
Apr 17 14:14:46 LXDE kernel: [    0.095033] HPET not enabled in BIOS. You might try hpet=force boot option
Apr 17 14:14:46 LXDE kernel: [    0.095046] pci 0000:00:11.0: quirk: [io  0x4000-0x407f] claimed by vt8235 PM
Apr 17 14:14:46 LXDE kernel: [    0.095051] pci 0000:00:11.0: quirk: [io  0x5000-0x500f] claimed by vt8235 SMB
Apr 17 14:14:46 LXDE kernel: [    0.095096] pci 0000:00:11.1: [1106:0571] type 0 class 0x000101
Apr 17 14:14:46 LXDE kernel: [    0.095143] pci 0000:00:11.1: reg 20: [io  0xe400-0xe40f]
Apr 17 14:14:46 LXDE kernel: [    0.095209] pci 0000:00:11.5: [1106:3059] type 0 class 0x000401
Apr 17 14:14:46 LXDE kernel: [    0.095227] pci 0000:00:11.5: reg 10: [io  0xe800-0xe8ff]
Apr 17 14:14:46 LXDE kernel: [    0.095297] pci 0000:00:11.5: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.095364] pci 0000:01:00.0: [5333:8d04] type 0 class 0x000300
Apr 17 14:14:46 LXDE kernel: [    0.095381] pci 0000:01:00.0: reg 10: [mem 0xed000000-0xed07ffff]
Apr 17 14:14:46 LXDE kernel: [    0.095391] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xe7ffffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.095423] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.095452] pci 0000:01:00.0: supports D1 D2
Apr 17 14:14:46 LXDE kernel: [    0.095488] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr 17 14:14:46 LXDE kernel: [    0.095495] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
Apr 17 14:14:46 LXDE kernel: [    0.095500] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
Apr 17 14:14:46 LXDE kernel: [    0.095506] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.095516] pci_bus 0000:00: on NUMA node 0
Apr 17 14:14:46 LXDE kernel: [    0.095521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 17 14:14:46 LXDE kernel: [    0.095840]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Apr 17 14:14:46 LXDE kernel: [    0.118329] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
Apr 17 14:14:46 LXDE kernel: [    0.118471] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
Apr 17 14:14:46 LXDE kernel: [    0.118613] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
Apr 17 14:14:46 LXDE kernel: [    0.118754] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 *12)
Apr 17 14:14:46 LXDE kernel: [    0.118862] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 17 14:14:46 LXDE kernel: [    0.118965] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 17 14:14:46 LXDE kernel: [    0.119068] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 17 14:14:46 LXDE kernel: [    0.119172] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Apr 17 14:14:46 LXDE kernel: [    0.119323] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
Apr 17 14:14:46 LXDE kernel: [    0.119475] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
Apr 17 14:14:46 LXDE kernel: [    0.119651] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
Apr 17 14:14:46 LXDE kernel: [    0.119801] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
Apr 17 14:14:46 LXDE kernel: [    0.120034] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 17 14:14:46 LXDE kernel: [    0.120038] vgaarb: loaded
Apr 17 14:14:46 LXDE kernel: [    0.120041] vgaarb: bridge control possible 0000:01:00.0
Apr 17 14:14:46 LXDE kernel: [    0.120500] SCSI subsystem initialized
Apr 17 14:14:46 LXDE kernel: [    0.120688] libata version 3.00 loaded.
Apr 17 14:14:46 LXDE kernel: [    0.120797] usbcore: registered new interface driver usbfs
Apr 17 14:14:46 LXDE kernel: [    0.120831] usbcore: registered new interface driver hub
Apr 17 14:14:46 LXDE kernel: [    0.120898] usbcore: registered new device driver usb
Apr 17 14:14:46 LXDE kernel: [    0.121078] PCI: Using ACPI for IRQ routing
Apr 17 14:14:46 LXDE kernel: [    0.121088] PCI: pci_cache_line_size set to 32 bytes
Apr 17 14:14:46 LXDE kernel: [    0.121174] reserve RAM buffer: 000000002dff0000 - 000000002fffffff 
Apr 17 14:14:46 LXDE kernel: [    0.121396] NetLabel: Initializing
Apr 17 14:14:46 LXDE kernel: [    0.121400] NetLabel:  domain hash size = 128
Apr 17 14:14:46 LXDE kernel: [    0.121402] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 17 14:14:46 LXDE kernel: [    0.121428] NetLabel:  unlabeled traffic allowed by default
Apr 17 14:14:46 LXDE kernel: [    0.138535] AppArmor: AppArmor Filesystem Enabled
Apr 17 14:14:46 LXDE kernel: [    0.138630] pnp: PnP ACPI init
Apr 17 14:14:46 LXDE kernel: [    0.138675] ACPI: bus type pnp registered
Apr 17 14:14:46 LXDE kernel: [    0.139052] pnp 00:00: [mem 0x000d6000-0x000d7fff]
Apr 17 14:14:46 LXDE kernel: [    0.139057] pnp 00:00: [mem 0x000f0000-0x000f7fff]
Apr 17 14:14:46 LXDE kernel: [    0.139061] pnp 00:00: [mem 0x000f8000-0x000fbfff]
Apr 17 14:14:46 LXDE kernel: [    0.139065] pnp 00:00: [mem 0x000fc000-0x000fffff]
Apr 17 14:14:46 LXDE kernel: [    0.139068] pnp 00:00: [mem 0x2dff0000-0x2dffffff]
Apr 17 14:14:46 LXDE kernel: [    0.139072] pnp 00:00: [mem 0xffff0000-0xffffffff]
Apr 17 14:14:46 LXDE kernel: [    0.139076] pnp 00:00: [mem 0x00000000-0x0009ffff]
Apr 17 14:14:46 LXDE kernel: [    0.139079] pnp 00:00: [mem 0x00100000-0x2dfeffff]
Apr 17 14:14:46 LXDE kernel: [    0.139083] pnp 00:00: [mem 0xfec00000-0xfec00fff]
Apr 17 14:14:46 LXDE kernel: [    0.139086] pnp 00:00: [mem 0xfee00000-0xfee00fff]
Apr 17 14:14:46 LXDE kernel: [    0.139090] pnp 00:00: [mem 0xfff80000-0xfffeffff]
Apr 17 14:14:46 LXDE kernel: [    0.139206] system 00:00: [mem 0x000d6000-0x000d7fff] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139212] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139217] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139221] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139225] system 00:00: [mem 0x2dff0000-0x2dffffff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139230] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139235] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139239] system 00:00: [mem 0x00100000-0x2dfeffff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139244] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr 17 14:14:46 LXDE kernel: [    0.139248] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139253] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139260] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr 17 14:14:46 LXDE kernel: [    0.139361] pnp 00:01: [bus 00-ff]
Apr 17 14:14:46 LXDE kernel: [    0.139367] pnp 00:01: [io  0x0cf8-0x0cff]
Apr 17 14:14:46 LXDE kernel: [    0.139371] pnp 00:01: [io  0x0000-0x0cf7 window]
Apr 17 14:14:46 LXDE kernel: [    0.139376] pnp 00:01: [io  0x0d00-0xffff window]
Apr 17 14:14:46 LXDE kernel: [    0.139380] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Apr 17 14:14:46 LXDE kernel: [    0.139384] pnp 00:01: [mem 0x000c0000-0x000dffff window]
Apr 17 14:14:46 LXDE kernel: [    0.139388] pnp 00:01: [mem 0x2e000000-0xfebfffff window]
Apr 17 14:14:46 LXDE kernel: [    0.139473] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Apr 17 14:14:46 LXDE kernel: [    0.139507] pnp 00:02: [io  0x4000-0x407f]
Apr 17 14:14:46 LXDE kernel: [    0.139511] pnp 00:02: [io  0x5000-0x500f]
Apr 17 14:14:46 LXDE kernel: [    0.139567] system 00:02: [io  0x4000-0x407f] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139572] system 00:02: [io  0x5000-0x500f] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.139578] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140079] pnp 00:03: [io  0x0010-0x001f]
Apr 17 14:14:46 LXDE kernel: [    0.140083] pnp 00:03: [io  0x0022-0x003f]
Apr 17 14:14:46 LXDE kernel: [    0.140099] pnp 00:03: [io  0x0044-0x005f]
Apr 17 14:14:46 LXDE kernel: [    0.140103] pnp 00:03: [io  0x0062-0x0063]
Apr 17 14:14:46 LXDE kernel: [    0.140106] pnp 00:03: [io  0x0065-0x006f]
Apr 17 14:14:46 LXDE kernel: [    0.140110] pnp 00:03: [io  0x0074-0x007f]
Apr 17 14:14:46 LXDE kernel: [    0.140113] pnp 00:03: [io  0x0091-0x0093]
Apr 17 14:14:46 LXDE kernel: [    0.140116] pnp 00:03: [io  0x00a2-0x00bf]
Apr 17 14:14:46 LXDE kernel: [    0.140119] pnp 00:03: [io  0x00e0-0x00ef]
Apr 17 14:14:46 LXDE kernel: [    0.140123] pnp 00:03: [io  0x04d0-0x04d1]
Apr 17 14:14:46 LXDE kernel: [    0.140126] pnp 00:03: [io  0x0800-0x0805]
Apr 17 14:14:46 LXDE kernel: [    0.140129] pnp 00:03: [io  0x0290-0x0297]
Apr 17 14:14:46 LXDE kernel: [    0.140203] system 00:03: [io  0x04d0-0x04d1] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.140208] system 00:03: [io  0x0800-0x0805] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.140212] system 00:03: [io  0x0290-0x0297] has been reserved
Apr 17 14:14:46 LXDE kernel: [    0.140217] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140240] pnp 00:04: [dma 4]
Apr 17 14:14:46 LXDE kernel: [    0.140244] pnp 00:04: [io  0x0000-0x000f]
Apr 17 14:14:46 LXDE kernel: [    0.140247] pnp 00:04: [io  0x0080-0x0090]
Apr 17 14:14:46 LXDE kernel: [    0.140251] pnp 00:04: [io  0x0094-0x009f]
Apr 17 14:14:46 LXDE kernel: [    0.140254] pnp 00:04: [io  0x00c0-0x00df]
Apr 17 14:14:46 LXDE kernel: [    0.140300] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140320] pnp 00:05: [io  0x0070-0x0073]
Apr 17 14:14:46 LXDE kernel: [    0.140346] pnp 00:05: [irq 8]
Apr 17 14:14:46 LXDE kernel: [    0.140402] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140419] pnp 00:06: [io  0x0061]
Apr 17 14:14:46 LXDE kernel: [    0.140464] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140481] pnp 00:07: [io  0x00f0-0x00ff]
Apr 17 14:14:46 LXDE kernel: [    0.140491] pnp 00:07: [irq 13]
Apr 17 14:14:46 LXDE kernel: [    0.140537] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr 17 14:14:46 LXDE kernel: [    0.140760] pnp 00:08: [io  0x03f0-0x03f5]
Apr 17 14:14:46 LXDE kernel: [    0.140764] pnp 00:08: [io  0x03f7]
Apr 17 14:14:46 LXDE kernel: [    0.140773] pnp 00:08: [irq 6]
Apr 17 14:14:46 LXDE kernel: [    0.140776] pnp 00:08: [dma 2]
Apr 17 14:14:46 LXDE kernel: [    0.140850] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
Apr 17 14:14:46 LXDE kernel: [    0.141142] pnp 00:09: [io  0x03f8-0x03ff]
Apr 17 14:14:46 LXDE kernel: [    0.141151] pnp 00:09: [irq 4]
Apr 17 14:14:46 LXDE kernel: [    0.141254] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Apr 17 14:14:46 LXDE kernel: [    0.141761] pnp 00:0a: [io  0x0378-0x037f]
Apr 17 14:14:46 LXDE kernel: [    0.141765] pnp 00:0a: [io  0x0778-0x077b]
Apr 17 14:14:46 LXDE kernel: [    0.141773] pnp 00:0a: [irq 7]
Apr 17 14:14:46 LXDE kernel: [    0.141777] pnp 00:0a: [dma 3]
Apr 17 14:14:46 LXDE kernel: [    0.141878] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
Apr 17 14:14:46 LXDE kernel: [    0.141941] pnp 00:0b: [io  0x0060]
Apr 17 14:14:46 LXDE kernel: [    0.141945] pnp 00:0b: [io  0x0064]
Apr 17 14:14:46 LXDE kernel: [    0.141953] pnp 00:0b: [irq 1]
Apr 17 14:14:46 LXDE kernel: [    0.142004] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Apr 17 14:14:46 LXDE kernel: [    0.142045] pnp: PnP ACPI: found 12 devices
Apr 17 14:14:46 LXDE kernel: [    0.142048] ACPI: ACPI bus type pnp unregistered
Apr 17 14:14:46 LXDE kernel: [    0.142055] PnPBIOS: Disabled by ACPI PNP
Apr 17 14:14:46 LXDE kernel: [    0.179635] Switching to clocksource acpi_pm
Apr 17 14:14:46 LXDE kernel: [    0.179687] PCI: max bus depth: 1 pci_try_num: 2
Apr 17 14:14:46 LXDE kernel: [    0.179737] pci 0000:00:08.0: BAR 6: assigned [mem 0x30000000-0x3001ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.179746] pci 0000:00:0b.0: BAR 6: assigned [mem 0x30020000-0x3002ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.179752] pci 0000:01:00.0: BAR 6: assigned [mem 0xec000000-0xec00ffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.179757] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr 17 14:14:46 LXDE kernel: [    0.179761] pci 0000:00:01.0:   bridge window [io  disabled]
Apr 17 14:14:46 LXDE kernel: [    0.179769] pci 0000:00:01.0:   bridge window [mem 0xec000000-0xedffffff]
Apr 17 14:14:46 LXDE kernel: [    0.179775] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe7ffffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.179797] pci 0000:00:01.0: setting latency timer to 64
Apr 17 14:14:46 LXDE kernel: [    0.179804] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Apr 17 14:14:46 LXDE kernel: [    0.179808] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Apr 17 14:14:46 LXDE kernel: [    0.179812] pci_bus 0000:01: resource 1 [mem 0xec000000-0xedffffff]
Apr 17 14:14:46 LXDE kernel: [    0.179816] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xe7ffffff pref]
Apr 17 14:14:46 LXDE kernel: [    0.179939] NET: Registered protocol family 2
Apr 17 14:14:46 LXDE kernel: [    0.179939] Switched to NOHz mode on CPU #0
Apr 17 14:14:46 LXDE kernel: [    0.179939] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.179939] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.180570] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.182199] TCP: Hash tables configured (established 131072 bind 65536)
Apr 17 14:14:46 LXDE kernel: [    0.182206] TCP reno registered
Apr 17 14:14:46 LXDE kernel: [    0.182216] UDP hash table entries: 512 (order: 2, 16384 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.182271] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.182563] NET: Registered protocol family 1
Apr 17 14:14:46 LXDE kernel: [    0.182606] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Apr 17 14:14:46 LXDE kernel: [    0.182769] pci 0000:01:00.0: Boot video device
Apr 17 14:14:46 LXDE kernel: [    0.182775] PCI: CLS 32 bytes, default 32
Apr 17 14:14:46 LXDE kernel: [    0.183631] audit: initializing netlink socket (disabled)
Apr 17 14:14:46 LXDE kernel: [    0.183655] type=2000 audit(1334686475.176:1): initialized
Apr 17 14:14:46 LXDE kernel: [    0.213139] Trying to unpack rootfs image as initramfs...
Apr 17 14:14:46 LXDE kernel: [    0.260487] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 17 14:14:46 LXDE kernel: [    0.296737] VFS: Disk quotas dquot_6.5.2
Apr 17 14:14:46 LXDE kernel: [    0.296856] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 17 14:14:46 LXDE kernel: [    0.298222] fuse init (API version 7.16)
Apr 17 14:14:46 LXDE kernel: [    0.298395] msgmni has been set to 1407
Apr 17 14:14:46 LXDE kernel: [    0.312468] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 17 14:14:46 LXDE kernel: [    0.312618] io scheduler noop registered
Apr 17 14:14:46 LXDE kernel: [    0.312621] io scheduler deadline registered
Apr 17 14:14:46 LXDE kernel: [    0.312646] io scheduler cfq registered (default)
Apr 17 14:14:46 LXDE kernel: [    0.312931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 17 14:14:46 LXDE kernel: [    0.312990] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 17 14:14:46 LXDE kernel: [    0.313253] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr 17 14:14:46 LXDE kernel: [    0.313266] ACPI: Power Button [PWRB]
Apr 17 14:14:46 LXDE kernel: [    0.313372] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr 17 14:14:46 LXDE kernel: [    0.313377] ACPI: Power Button [PWRF]
Apr 17 14:14:46 LXDE kernel: [    0.313462] ACPI: Fan [FAN] (on)
Apr 17 14:14:46 LXDE kernel: [    0.313475] ACPI: acpi_idle registered with cpuidle
Apr 17 14:14:46 LXDE kernel: [    0.313534] Marking TSC unstable due to TSC halts in idle
Apr 17 14:14:46 LXDE kernel: [    0.316402] thermal LNXTHERM:00: registered as thermal_zone0
Apr 17 14:14:46 LXDE kernel: [    0.316407] ACPI: Thermal Zone [THRM] (40 C)
Apr 17 14:14:46 LXDE kernel: [    0.316448] ERST: Table is not found!
Apr 17 14:14:46 LXDE kernel: [    0.316785] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr 17 14:14:46 LXDE kernel: [    0.337168] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 17 14:14:46 LXDE kernel: [    0.340220] isapnp: Scanning for PnP cards...
Apr 17 14:14:46 LXDE kernel: [    0.474731] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 17 14:14:46 LXDE kernel: [    0.496751] Linux agpgart interface v0.103
Apr 17 14:14:46 LXDE kernel: [    0.496878] agpgart: Detected VIA PM266/KM266 chipset
Apr 17 14:14:46 LXDE kernel: [    0.512446] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
Apr 17 14:14:46 LXDE kernel: [    0.514769] brd: module loaded
Apr 17 14:14:46 LXDE kernel: [    0.515852] loop: module loaded
Apr 17 14:14:46 LXDE kernel: [    0.516834] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Apr 17 14:14:46 LXDE kernel: [    0.516838] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Apr 17 14:14:46 LXDE kernel: [    0.516881] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Apr 17 14:14:46 LXDE kernel: [    0.517026] pata_acpi 0000:00:11.1: PCI INT A disabled
Apr 17 14:14:46 LXDE kernel: [    0.517652] Fixed MDIO Bus: probed
Apr 17 14:14:46 LXDE kernel: [    0.517698] PPP generic driver version 2.4.2
Apr 17 14:14:46 LXDE kernel: [    0.517841] tun: Universal TUN/TAP device driver, 1.6
Apr 17 14:14:46 LXDE kernel: [    0.517844] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 17 14:14:46 LXDE kernel: [    0.518030] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 17 14:14:46 LXDE kernel: [    0.518067] ehci_hcd 0000:00:09.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Apr 17 14:14:46 LXDE kernel: [    0.518103] ehci_hcd 0000:00:09.2: EHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.518171] ehci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 1
Apr 17 14:14:46 LXDE kernel: [    0.518292] ehci_hcd 0000:00:09.2: irq 19, io mem 0xef001000
Apr 17 14:14:46 LXDE kernel: [    0.528477] ehci_hcd 0000:00:09.2: USB 2.0 started, EHCI 1.00
Apr 17 14:14:46 LXDE kernel: [    0.528860] hub 1-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.528870] hub 1-0:1.0: 4 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.529415] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.529419] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.529459] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.529517] ehci_hcd 0000:00:10.3: EHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.529619] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 2
Apr 17 14:14:46 LXDE kernel: [    0.529745] ehci_hcd 0000:00:10.3: irq 21, io mem 0xef004000
Apr 17 14:14:46 LXDE kernel: [    0.573311] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
Apr 17 14:14:46 LXDE kernel: [    0.573534] hub 2-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.573544] hub 2-0:1.0: 6 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.573683] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 17 14:14:46 LXDE kernel: [    0.573720] uhci_hcd: USB Universal Host Controller Interface driver
Apr 17 14:14:46 LXDE kernel: [    0.573853] uhci_hcd 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 17 14:14:46 LXDE kernel: [    0.573870] uhci_hcd 0000:00:09.0: UHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.573953] uhci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
Apr 17 14:14:46 LXDE kernel: [    0.574017] uhci_hcd 0000:00:09.0: irq 17, io base 0x0000c400
Apr 17 14:14:46 LXDE kernel: [    0.574264] hub 3-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.574272] hub 3-0:1.0: 2 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.574388] uhci_hcd 0000:00:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Apr 17 14:14:46 LXDE kernel: [    0.574399] uhci_hcd 0000:00:09.1: UHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.574461] uhci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
Apr 17 14:14:46 LXDE kernel: [    0.574523] uhci_hcd 0000:00:09.1: irq 18, io base 0x0000c800
Apr 17 14:14:46 LXDE kernel: [    0.574761] hub 4-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.574769] hub 4-0:1.0: 2 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.574871] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.574883] uhci_hcd 0000:00:10.0: UHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.574948] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
Apr 17 14:14:46 LXDE kernel: [    0.574978] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
Apr 17 14:14:46 LXDE kernel: [    0.575200] hub 5-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.575208] hub 5-0:1.0: 2 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.575292] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.575303] uhci_hcd 0000:00:10.1: UHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.575376] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
Apr 17 14:14:46 LXDE kernel: [    0.575406] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
Apr 17 14:14:46 LXDE kernel: [    0.575647] hub 6-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.575655] hub 6-0:1.0: 2 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.575756] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Apr 17 14:14:46 LXDE kernel: [    0.575767] uhci_hcd 0000:00:10.2: UHCI Host Controller
Apr 17 14:14:46 LXDE kernel: [    0.575826] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 7
Apr 17 14:14:46 LXDE kernel: [    0.575853] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
Apr 17 14:14:46 LXDE kernel: [    0.656454] hub 7-0:1.0: USB hub found
Apr 17 14:14:46 LXDE kernel: [    0.656471] hub 7-0:1.0: 2 ports detected
Apr 17 14:14:46 LXDE kernel: [    0.656725] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Apr 17 14:14:46 LXDE kernel: [    0.656729] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Apr 17 14:14:46 LXDE kernel: [    0.656958] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 17 14:14:46 LXDE kernel: [    0.657278] mousedev: PS/2 mouse device common for all mice
Apr 17 14:14:46 LXDE kernel: [    0.657512] rtc_cmos 00:05: RTC can wake from S4
Apr 17 14:14:46 LXDE kernel: [    0.657706] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 17 14:14:46 LXDE kernel: [    0.657760] rtc0: alarms up to one year, y3k, 242 bytes nvram
Apr 17 14:14:46 LXDE kernel: [    0.658016] device-mapper: uevent: version 1.0.3
Apr 17 14:14:46 LXDE kernel: [    0.658161] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Apr 17 14:14:46 LXDE kernel: [    0.658221] EISA: Probing bus 0 at eisa.0
Apr 17 14:14:46 LXDE kernel: [    0.658248] Cannot allocate resource for EISA slot 4
Apr 17 14:14:46 LXDE kernel: [    0.658252] Cannot allocate resource for EISA slot 5
Apr 17 14:14:46 LXDE kernel: [    0.658268] EISA: Detected 0 cards.
Apr 17 14:14:46 LXDE kernel: [    0.658289] cpufreq-nforce2: No nForce2 chipset.
Apr 17 14:14:46 LXDE kernel: [    0.658349] cpuidle: using governor ladder
Apr 17 14:14:46 LXDE kernel: [    0.658424] cpuidle: using governor menu
Apr 17 14:14:46 LXDE kernel: [    0.658427] EFI Variables Facility v0.08 2004-May-17
Apr 17 14:14:46 LXDE kernel: [    0.658834] TCP cubic registered
Apr 17 14:14:46 LXDE kernel: [    0.659125] NET: Registered protocol family 10
Apr 17 14:14:46 LXDE kernel: [    0.659995] NET: Registered protocol family 17
Apr 17 14:14:46 LXDE kernel: [    0.662124] Registering the dns_resolver key type
Apr 17 14:14:46 LXDE kernel: [    0.662186] Using IPI No-Shortcut mode
Apr 17 14:14:46 LXDE kernel: [    0.662455] PM: Hibernation image not present or could not be loaded.
Apr 17 14:14:46 LXDE kernel: [    0.662483] registered taskstats version 1
Apr 17 14:14:46 LXDE kernel: [    0.808638] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Apr 17 14:14:46 LXDE kernel: [    0.951702] isapnp: No Plug & Play device found
Apr 17 14:14:46 LXDE kernel: [    1.181835] Freeing initrd memory: 13320k freed
Apr 17 14:14:46 LXDE kernel: [    1.234606]   Magic number: 8:342:241
Apr 17 14:14:46 LXDE kernel: [    1.234851] rtc_cmos 00:05: setting system clock to 2012-04-17 18:14:36 UTC (1334686476)
Apr 17 14:14:46 LXDE kernel: [    1.234859] powernow-k8: Processor cpuid 662 not supported
Apr 17 14:14:46 LXDE kernel: [    1.234899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 17 14:14:46 LXDE kernel: [    1.234903] EDD information not available.
Apr 17 14:14:46 LXDE kernel: [    1.235143] Freeing unused kernel memory: 696k freed
Apr 17 14:14:46 LXDE kernel: [    1.236990] Write protecting the kernel text: 5344k
Apr 17 14:14:46 LXDE kernel: [    1.237045] Write protecting the kernel read-only data: 2192k
Apr 17 14:14:46 LXDE kernel: [    1.544232] Floppy drive(s): fd0 is 1.44M
Apr 17 14:14:46 LXDE kernel: [    1.564098] FDC 0 is a post-1991 82077
Apr 17 14:14:46 LXDE kernel: [    1.603022] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr 17 14:14:46 LXDE kernel: [    1.603088] r8169 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 17 14:14:46 LXDE kernel: [    1.603138] r8169 0000:00:08.0: (unregistered net_device): no PCI Express capability
Apr 17 14:14:46 LXDE kernel: [    1.603918] r8169 0000:00:08.0: eth0: RTL8169sb/8110sb at 0xee802000, 6c:fd:b9:4d:12:5e, XID 10000000 IRQ 16
Apr 17 14:14:46 LXDE kernel: [    1.635142] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Apr 17 14:14:46 LXDE kernel: [    1.656798] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Apr 17 14:14:46 LXDE kernel: [    1.657940] 8139too: 8139too Fast Ethernet driver 0.9.28
Apr 17 14:14:46 LXDE kernel: [    1.658030] 8139too 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 17 14:14:46 LXDE kernel: [    1.659147] 8139too 0000:00:0b.0: eth1: RealTek RTL8139 at 0xd400, 00:40:ca:4a:63:e2, IRQ 18
Apr 17 14:14:46 LXDE kernel: [    1.684997] pata_via 0000:00:11.1: version 0.3.4
Apr 17 14:14:46 LXDE kernel: [    1.685039] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Apr 17 14:14:46 LXDE kernel: [    1.700132] scsi0 : pata_via
Apr 17 14:14:46 LXDE kernel: [    1.703737] scsi1 : pata_via
Apr 17 14:14:46 LXDE kernel: [    1.706812] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
Apr 17 14:14:46 LXDE kernel: [    1.706818] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
Apr 17 14:14:46 LXDE kernel: [    1.888877] ata1.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
Apr 17 14:14:46 LXDE kernel: [    1.888887] ata1.00: 976773168 sectors, multi 16: LBA48 
Apr 17 14:14:46 LXDE kernel: [    1.904868] ata1.00: configured for UDMA/133
Apr 17 14:14:46 LXDE kernel: [    1.905159] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
Apr 17 14:14:46 LXDE kernel: [    1.905554] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 17 14:14:46 LXDE kernel: [    1.906203] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr 17 14:14:46 LXDE kernel: [    1.906300] sd 0:0:0:0: [sda] Write Protect is off
Apr 17 14:14:46 LXDE kernel: [    1.906306] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 17 14:14:46 LXDE kernel: [    1.906345] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 17 14:14:46 LXDE kernel: [    1.947279]  sda: sda1 sda2
Apr 17 14:14:46 LXDE kernel: [    1.948133] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 17 14:14:46 LXDE kernel: [    2.319111] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
Apr 17 14:14:46 LXDE kernel: [    2.319123] EXT4-fs (sda2): write access will be enabled during recovery
Apr 17 14:14:46 LXDE kernel: [    4.030017] EXT4-fs (sda2): recovery complete
Apr 17 14:14:46 LXDE kernel: [    4.030931] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Apr 17 14:14:46 LXDE kernel: [   10.844281] Adding 4192960k swap on /dev/sda1.  Priority:-1 extents:1 across:4192960k 
Apr 17 14:14:46 LXDE kernel: [   10.887493] lp: driver loaded but no devices found
Apr 17 14:14:46 LXDE kernel: [   11.080126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 17 14:14:46 LXDE kernel: [   11.140871] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Apr 17 14:14:46 LXDE kernel: [   11.442191] parport_pc 00:0a: reported by Plug and Play ACPI
Apr 17 14:14:46 LXDE kernel: [   11.442292] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 17 14:14:46 LXDE kernel: [   11.632128] lp0: using parport0 (interrupt-driven).
Apr 17 14:14:47 LXDE kernel: [   12.003381] type=1400 audit(1334686487.263:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=422 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.004143] type=1400 audit(1334686487.267:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=418 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.007587] type=1400 audit(1334686487.267:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=418 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.008093] type=1400 audit(1334686487.271:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=418 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.022151] type=1400 audit(1334686487.283:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=422 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.022601] type=1400 audit(1334686487.283:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=422 comm="apparmor_parser"
Apr 17 14:14:47 LXDE kernel: [   12.180284] r8169 0000:00:08.0: eth1: link down
Apr 17 14:14:47 LXDE kernel: [   12.182435] irda_init()
Apr 17 14:14:47 LXDE kernel: [   12.182485] NET: Registered protocol family 23
Apr 17 14:14:47 LXDE kernel: [   12.192558] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 17 14:14:47 LXDE kernel: [   12.275189] 8139too 0000:00:0b.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 17 14:14:47 LXDE kernel: [   12.389137] input: PC Speaker as /devices/platform/pcspkr/input/input3
Apr 17 14:14:47 LXDE kernel: [   12.395506] init: ssh main process (369) terminated with status 255
Apr 17 14:14:48 LXDE kernel: [   12.808755] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Apr 17 14:14:48 LXDE kernel: [   12.808764] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Apr 17 14:14:48 LXDE kernel: [   12.808801] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Apr 17 14:14:48 LXDE kernel: [   12.808987] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
Apr 17 14:14:48 LXDE kernel: [   13.114709] init: smbd main process (508) killed by HUP signal
Apr 17 14:14:48 LXDE kernel: [   13.114791] init: smbd main process ended, respawning
Apr 17 14:14:48 LXDE kernel: [   13.327163] init: ssh main process (482) terminated with status 255
Apr 17 14:14:49 LXDE kernel: [   13.796637] init: failsafe main process (636) killed by TERM signal
Apr 17 14:14:49 LXDE kernel: [   13.944338] type=1400 audit(1334686489.207:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
Apr 17 14:14:49 LXDE kernel: [   13.948807] type=1400 audit(1334686489.211:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=691 comm="apparmor_parser"
Apr 17 14:14:49 LXDE kernel: [   13.949284] type=1400 audit(1334686489.211:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=691 comm="apparmor_parser"
Apr 17 14:14:49 LXDE kernel: [   13.958379] type=1400 audit(1334686489.219:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=694 comm="apparmor_parser"
Apr 17 14:14:49 LXDE kernel: [   14.036709] r8169 0000:00:08.0: eth1: link up
Apr 17 14:14:49 LXDE kernel: [   14.037122] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 17 14:14:49 LXDE kernel: [   14.214041] ppdev: user-space parallel port driver
Apr 17 14:14:49 LXDE kernel: [   14.347586] init: apport pre-start process (733) terminated with status 1
Apr 17 14:14:49 LXDE kernel: [   14.396188] init: apport post-stop process (764) terminated with status 1
Apr 17 14:14:50 LXDE kernel: [   14.770858] vesafb: mode is 640x480x32, linelength=2560, pages=0
Apr 17 14:14:50 LXDE kernel: [   14.770867] vesafb: scrolling: redraw
Apr 17 14:14:50 LXDE kernel: [   14.770872] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Apr 17 14:14:50 LXDE kernel: [   14.771308] vesafb: framebuffer at 0xe0000000, mapped to 0xeeb00000, using 1216k, total 1216k
Apr 17 14:14:50 LXDE kernel: [   14.771782] Console: switching to colour frame buffer device 80x30
Apr 17 14:14:50 LXDE kernel: [   14.771812] fb0: VESA VGA frame buffer device
Apr 17 14:14:53 LXDE kernel: [   17.832733] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 17 14:14:57 LXDE kernel: [   22.720028] eth0: no IPv6 routers present
Apr 17 14:15:00 LXDE kernel: [   24.768028] eth1: no IPv6 routers present
Apr 17 14:35:00 LXDE kernel: [  975.940066] usb 1-2: new high speed USB device number 2 using ehci_hcd
Apr 17 14:35:09 LXDE kernel: [  985.116332] usb 1-2: USB disconnect, device number 2
Apr 17 14:35:14 LXDE kernel: [  989.931765] usbcore: registered new interface driver uas
Apr 17 14:35:14 LXDE kernel: [  989.945127] Initializing USB Mass Storage driver...
Apr 17 14:35:14 LXDE kernel: [  989.946856] usbcore: registered new interface driver usb-storage
Apr 17 14:35:14 LXDE kernel: [  989.946867] USB Mass Storage support registered.
Apr 17 14:43:55 LXDE kernel: [ 1510.744075] usb 1-2: new high speed USB device number 3 using ehci_hcd
Apr 17 14:43:55 LXDE kernel: [ 1510.888203] scsi2 : usb-storage 1-2:1.0
Apr 17 14:43:56 LXDE kernel: [ 1511.903957] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.2  PQ: 0 ANSI: 2
Apr 17 14:43:56 LXDE kernel: [ 1511.905947] sd 2:0:0:0: Attached scsi generic sg1 type 0
Apr 17 14:43:56 LXDE kernel: [ 1511.906159] sd 2:0:0:0: [sdb] 501759 512-byte logical blocks: (256 MB/244 MiB)
Apr 17 14:43:56 LXDE kernel: [ 1511.906874] sd 2:0:0:0: [sdb] Write Protect is off
Apr 17 14:43:56 LXDE kernel: [ 1511.906880] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
Apr 17 14:43:56 LXDE kernel: [ 1511.907623] sd 2:0:0:0: [sdb] No Caching mode page present
Apr 17 14:43:56 LXDE kernel: [ 1511.907882] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Apr 17 14:43:56 LXDE kernel: [ 1511.913633] sd 2:0:0:0: [sdb] No Caching mode page present
Apr 17 14:43:56 LXDE kernel: [ 1511.913840] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Apr 17 14:43:56 LXDE kernel: [ 1511.916650]  sdb: sdb1
Apr 17 14:43:56 LXDE kernel: [ 1511.926139] sd 2:0:0:0: [sdb] No Caching mode page present
Apr 17 14:43:56 LXDE kernel: [ 1511.926382] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Apr 17 14:43:56 LXDE kernel: [ 1511.926622] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Apr 17 14:43:59 LXDE kernel: [ 1515.217867] usb 1-2: USB disconnect, device number 3
```
ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 6c:fd:b9:4d:12:5e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6efd:b9ff:fe4d:125e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:879220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:787270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101164449 (101.1 MB)  TX bytes:129208453 (129.2 MB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3112793 (3.1 MB)  TX bytes:3112793 (3.1 MB)
```
lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
brkfre55@LXDE:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```

Thank you in advanced.

---

