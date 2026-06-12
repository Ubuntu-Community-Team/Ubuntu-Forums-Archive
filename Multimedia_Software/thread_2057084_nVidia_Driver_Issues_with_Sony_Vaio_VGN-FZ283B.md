---
title: "nVidia Driver Issues with Sony Vaio VGN-FZ283B"
date: 2012-09-12
forum: Multimedia Software
---

### Post by HoneyGutClusters on 2012-09-12
I just wanted to share this information with you since I couldn't find anything about it on the Internet.

I have a Sony Vaio VGN-FZ283B laptop, on which I have installed Ubuntu 12.04 LTS. I'm having an issue where the nvidia driver reports that it will not support the GPU.

```
[   29.834610] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:0426) installed
[   29.834611] NVRM: in this system is not supported by the 304.43 NVIDIA Linux
[   29.834613] NVRM: graphics driver release.  Please see 'Appendix A -
[   29.834614] NVRM: Supported NVIDIA GPU Products' in this release's README,
[   29.834615] NVRM: available on the Linux graphics driver download page at
[   29.834617] NVRM: www.nvidia.com.

```

So far, I was able to resolve this issue by doing the following:

Blacklist the nouveau driver and add "pci=use_crs" kernel switch to GRUB. 
```
gksu gedit /etc/default/grub
```
Find the line that begins as "GRUB_CMDLINE_LINUX_DEFAULT=" and add the following before the end quote:
```
blacklist=nouveau pci=use_crs
```
Save and exit, then run this command to update GRUB configuration:
```
sudo update-grub
```

Next, blacklist the nouveau module from loading.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Go to the end of the file and add the following:
```
blacklist nouveau
```
Save and exit, then reboot the machine.

This is working for me thusfar. Let me know, if you're having a video driver issue with your Sony Vaio, if this works for you.

EDIT: Sorry, that didn't work. It is still reporting an error whereas it states it will not support the GPU. I'm at a loss here... I'll post some logs in a new reply.

---

### Post by HoneyGutClusters on 2012-09-12
Here's the dmesg from a time it successfully loaded the module.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-30-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 (Ubuntu 3.2.0-30.48-generic 3.2.27)
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
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Sony Corporation VGN-FZ283BN/VAIO, BIOS R1120J7 07/04/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 2  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00f8090] f8090
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 364f4000 - 37272000
[    0.000000] ACPI: RSDP 000f8060 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7fed7f39 00084 (v01   Sony     VAIO 20070704 PTL  00000000)
[    0.000000] ACPI: FACP 7fedfc04 000F4 (v03   Sony     VAIO 20070704 PTL  00000001)
[    0.000000] ACPI: DSDT 7fed9217 06979 (v02   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: APIC 7fedfcf8 00068 (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: SLIC 7fedfdd4 00176 (v01   Sony     VAIO 20070704 PTL  01000000)
[    0.000000] ACPI: TMOR 7fedff4a 00026 (v01   Sony     VAIO 20070704 PTL  00000003)
[    0.000000] ACPI: APIC 7fedff70 00068 (v01   Sony     VAIO 20070704 PTL  00000000)
[    0.000000] ACPI: BOOT 7fedffd8 00028 (v01   Sony     VAIO 20070704 PTL  00000001)
[    0.000000] ACPI: SSDT 7fed90fa 0011D (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed85a5 00287 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed84f1 000B4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed7fbd 00534 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c1822ec0, node_mem_map f54f4200
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
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519777
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic root=UUID=b0ea6cef-09a4-41f4-aea5-97263981433c ro blacklist=nouveau pci=use_crs
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8383488 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2046124k/2095936k available (5618k kernel code, 49360k reserved, 2762k data, 712k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157cac4 - 0xc182f5c0   (2762 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157cac4   (5618 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4808000 soft=f480a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.024 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.04 BogoMIPS (lpj=7980096)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004059] Yama: becoming mindful.
[    0.004118] Mount-cache hash table entries: 512
[    0.004260] Initializing cgroup subsys cpuacct
[    0.004268] Initializing cgroup subsys memory
[    0.004278] Initializing cgroup subsys devices
[    0.004282] Initializing cgroup subsys freezer
[    0.004286] Initializing cgroup subsys blkio
[    0.004295] Initializing cgroup subsys perf_event
[    0.004324] CPU: Physical Processor ID: 0
[    0.004328] CPU: Processor Core ID: 0
[    0.004334] mce: CPU supports 6 MCE banks
[    0.004344] CPU0: Thermal monitoring enabled (TM2)
[    0.004350] using mwait in idle threads.
[    0.009458] ACPI: Core revision 20110623
[    0.016031] ftrace: allocating 25901 entries in 51 pages
[    0.020052] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024272] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063970] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f48ea000 soft=f48ec000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.152038] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152087] Brought up 2 CPUs
[    0.152092] Total of 2 processors activated (7980.02 BogoMIPS).
[    0.153456] devtmpfs: initialized
[    0.153456] EVM: security.selinux
[    0.153456] EVM: security.SMACK64
[    0.153456] EVM: security.capability
[    0.153456] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
[    0.153456] print_constraints: dummy: 
[    0.153456] RTC time: 22:56:46, date: 09/12/12
[    0.153456] NET: Registered protocol family 16
[    0.153456] Trying to unpack rootfs image as initramfs...
[    0.153464] EISA bus registered
[    0.153500] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.153507] ACPI: bus type pci registered
[    0.153584] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153592] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.153597] PCI: Using MMCONFIG for extended config space
[    0.153602] PCI: Using configuration type 1 for base access
[    0.156837] bio: create slab <bio-0> at 0
[    0.156941] ACPI: Added _OSI(Module Device)
[    0.156946] ACPI: Added _OSI(Processor Device)
[    0.156951] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156956] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158734] ACPI: EC: Look up EC in DSDT
[    0.161841] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.163065] ACPI: SSDT 7fed8d75 002A1 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.163511] ACPI: Dynamic OEM Table Load:
[    0.163518] ACPI: SSDT   (null) 002A1 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.163663] ACPI: SSDT 7fed882c 004B7 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164094] ACPI: Dynamic OEM Table Load:
[    0.164100] ACPI: SSDT   (null) 004B7 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164463] ACPI: SSDT 7fed9016 000E4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164901] ACPI: Dynamic OEM Table Load:
[    0.164908] ACPI: SSDT   (null) 000E4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.165031] ACPI: SSDT 7fed8ce3 00092 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.165454] ACPI: Dynamic OEM Table Load:
[    0.165460] ACPI: SSDT   (null) 00092 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.167180] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.380135] ACPI: Interpreter enabled
[    0.380158] ACPI: (supports S0 S3 S4 S5)
[    0.380190] ACPI: Using IOAPIC for interrupt routing
[    0.428670] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.434150] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.434353] ACPI: No dock devices found.
[    0.434359] HEST: Table not found.
[    0.434366] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.434917] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.435682] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.435690] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.435696] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.435703] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.435709] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.435716] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.435723] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.435729] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.435750] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.435810] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.435866] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.435871] pci 0000:00:01.0: PME# disabled
[    0.435933] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.435996] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.436052] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.436115] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.436179] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.436206] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.436327] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.436333] pci 0000:00:1a.7: PME# disabled
[    0.436367] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.436392] pci 0000:00:1b.0: reg 10: [mem 0xfc400000-0xfc403fff 64bit]
[    0.436507] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.436513] pci 0000:00:1b.0: PME# disabled
[    0.436546] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.436669] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.436675] pci 0000:00:1c.0: PME# disabled
[    0.436712] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.436834] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.436840] pci 0000:00:1c.1: PME# disabled
[    0.436875] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.436998] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.437003] pci 0000:00:1c.2: PME# disabled
[    0.437040] pci 0000:00:1c.4: [8086:2847] type 1 class 0x000604
[    0.437163] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.437169] pci 0000:00:1c.4: PME# disabled
[    0.437204] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.437267] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.437314] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.437377] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.437428] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.437491] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.437553] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.437579] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.437698] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.437705] pci 0000:00:1d.7: PME# disabled
[    0.437730] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.437837] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.437960] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.437971] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.438044] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.438063] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.438077] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.438090] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.438104] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.438118] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.438178] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.438208] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.438221] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.438235] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.438248] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.438261] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.438275] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.438348] pci 0000:00:1f.2: PME# supported from D3hot
[    0.438353] pci 0000:00:1f.2: PME# disabled
[    0.438378] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.438398] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.438445] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.438582] pci 0000:01:00.0: [10de:0426] type 0 class 0x000300
[    0.438632] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    0.438687] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.438742] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    0.438778] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.438813] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.444061] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.444070] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.444074] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.444080] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.444150] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.444158] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.444164] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.444173] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.444241] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.444249] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.444256] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.444265] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.444401] pci 0000:06:00.0: [8086:4229] type 0 class 0x000280
[    0.444451] pci 0000:06:00.0: reg 10: [mem 0xfa000000-0xfa001fff 64bit]
[    0.444700] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.444718] pci 0000:06:00.0: PME# disabled
[    0.452079] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.452089] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.452095] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.452105] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.452207] pci 0000:08:00.0: [11ab:4351] type 0 class 0x000200
[    0.452242] pci 0000:08:00.0: reg 10: [mem 0xfc000000-0xfc003fff 64bit]
[    0.452261] pci 0000:08:00.0: reg 18: [io  0x6000-0x60ff]
[    0.452430] pci 0000:08:00.0: supports D1 D2
[    0.452433] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.452440] pci 0000:08:00.0: PME# disabled
[    0.460049] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.460059] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.460065] pci 0000:00:1c.4:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.460135] pci 0000:09:03.0: [104c:8039] type 2 class 0x000607
[    0.460163] pci 0000:09:03.0: reg 10: [mem 0xfc100000-0xfc100fff]
[    0.460212] pci 0000:09:03.0: supports D1 D2
[    0.460214] pci 0000:09:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460221] pci 0000:09:03.0: PME# disabled
[    0.460248] pci 0000:09:03.1: [104c:803a] type 0 class 0x000c00
[    0.460276] pci 0000:09:03.1: reg 10: [mem 0xfc102000-0xfc1027ff]
[    0.460293] pci 0000:09:03.1: reg 14: [mem 0xfc104000-0xfc107fff]
[    0.460408] pci 0000:09:03.1: supports D1 D2
[    0.460410] pci 0000:09:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.460417] pci 0000:09:03.1: PME# disabled
[    0.460444] pci 0000:09:03.2: [104c:803b] type 0 class 0x000180
[    0.460471] pci 0000:09:03.2: reg 10: [mem 0xfc101000-0xfc101fff]
[    0.460593] pci 0000:09:03.2: supports D1 D2
[    0.460596] pci 0000:09:03.2: PME# supported from D0 D1 D2 D3hot
[    0.460602] pci 0000:09:03.2: PME# disabled
[    0.460678] pci 0000:00:1e.0: PCI bridge to [bus 09-0a] (subtractive decode)
[    0.460690] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.460700] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.460703] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.460706] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.460709] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.460713] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.460716] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.460719] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.460723] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.460780] pci_bus 0000:0a: [bus 0a-0d] partially hidden behind transparent bridge 0000:09 [bus 09-0a]
[    0.460827] pci_bus 0000:00: on NUMA node 0
[    0.460835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.461085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.461266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.461375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.461482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.461590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.461882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.462189]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.462326]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x00
[    0.462333] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.476319] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.476391] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.476456] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.476521] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.476589] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.476655] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.476718] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.476782] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.476948] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.476959] vgaarb: loaded
[    0.476963] vgaarb: bridge control possible 0000:01:00.0
[    0.477105] i2c-core: driver [aat2870] using legacy suspend method
[    0.477110] i2c-core: driver [aat2870] using legacy resume method
[    0.477211] SCSI subsystem initialized
[    0.477289] libata version 3.00 loaded.
[    0.477345] usbcore: registered new interface driver usbfs
[    0.477363] usbcore: registered new interface driver hub
[    0.477398] usbcore: registered new device driver usb
[    0.477513] PCI: Using ACPI for IRQ routing
[    0.487650] Freeing initrd memory: 13816k freed
[    0.489467] PCI: pci_cache_line_size set to 64 bytes
[    0.489712] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.489717] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    0.490015] NetLabel: Initializing
[    0.490034] NetLabel:  domain hash size = 128
[    0.490038] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.490061] NetLabel:  unlabeled traffic allowed by default
[    0.490232] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.490247] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.490258] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.496185] Switching to clocksource hpet
[    0.506028] AppArmor: AppArmor Filesystem Enabled
[    0.506074] pnp: PnP ACPI init
[    0.506099] ACPI: bus type pnp registered
[    0.528444] pnp 00:00: [bus 00-ff]
[    0.528448] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.528451] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.528453] pnp 00:00: [io  0x0d00-0xffff window]
[    0.528456] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.528459] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.528462] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.528465] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.528468] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.528471] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.528474] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.528476] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.528479] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.528482] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.528485] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.528488] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.528491] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.528493] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.528496] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.528499] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.528502] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.528582] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.528675] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.528678] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.528681] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.528683] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.528686] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.528689] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.528691] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.528694] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.528772] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.528780] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.528786] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.528792] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.528798] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.528804] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.528810] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.528816] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.528822] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.529059] pnp 00:02: [io  0x0000-0x001f]
[    0.529062] pnp 00:02: [io  0x0081-0x0091]
[    0.529064] pnp 00:02: [io  0x0093-0x009f]
[    0.529066] pnp 00:02: [io  0x00c0-0x00df]
[    0.529069] pnp 00:02: [dma 4]
[    0.529122] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.529133] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.529185] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.529262] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.529347] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.529355] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.529369] pnp 00:05: [io  0x00f0]
[    0.529383] pnp 00:05: [irq 13]
[    0.529438] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.529452] pnp 00:06: [io  0x002e-0x002f]
[    0.529454] pnp 00:06: [io  0x004e-0x004f]
[    0.529457] pnp 00:06: [io  0x0061]
[    0.529459] pnp 00:06: [io  0x0063]
[    0.529461] pnp 00:06: [io  0x0065]
[    0.529464] pnp 00:06: [io  0x0067]
[    0.529466] pnp 00:06: [io  0x0080]
[    0.529468] pnp 00:06: [io  0x0092]
[    0.529470] pnp 00:06: [io  0x00b2-0x00b3]
[    0.529473] pnp 00:06: [io  0x0680-0x069f]
[    0.529476] pnp 00:06: [io  0x0800-0x080f]
[    0.529478] pnp 00:06: [io  0x1000-0x107f]
[    0.529480] pnp 00:06: [io  0x1180-0x11bf]
[    0.529483] pnp 00:06: [io  0x1640-0x164f]
[    0.529485] pnp 00:06: [io  0xfe00-0xfe7f]
[    0.529488] pnp 00:06: [io  0xfe80-0xfeff]
[    0.529585] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.529591] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.529597] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.529602] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.529608] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.529614] system 00:06: [io  0xfe00-0xfe7f] has been reserved
[    0.529619] system 00:06: [io  0xfe80-0xfeff] has been reserved
[    0.529626] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.529637] pnp 00:07: [io  0x0070-0x0077]
[    0.529644] pnp 00:07: [irq 8]
[    0.529699] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.529716] pnp 00:08: [io  0x0060]
[    0.529718] pnp 00:08: [io  0x0064]
[    0.529725] pnp 00:08: [irq 1]
[    0.529780] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.529795] pnp 00:09: [irq 12]
[    0.529854] pnp 00:09: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.529878] pnp: PnP ACPI: found 10 devices
[    0.529882] ACPI: ACPI bus type pnp unregistered
[    0.529889] PnPBIOS: Disabled by ACPI PNP
[    0.567558] PCI: max bus depth: 2 pci_try_num: 3
[    0.567626] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80000000-0x800000ff]
[    0.567637] pci 0000:00:1f.3: BAR 0: set to [mem 0x80000000-0x800000ff] (PCI address [0x80000000-0x800000ff])
[    0.567647] pci 0000:00:1e.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.567655] pci 0000:00:1e.0: BAR 13: assigned [io  0x7000-0x7fff]
[    0.567662] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80100000-0x802fffff 64bit pref]
[    0.567669] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.567675] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.567681] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.567689] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.567695] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.567705] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.567711] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.567721] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.567729] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.567742] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.567748] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.567758] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.567766] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.567779] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.567785] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.567795] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.567803] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.567816] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.567822] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.567832] pci 0000:00:1c.4:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.567840] pci 0000:00:1c.4:   bridge window [mem 0x80100000-0x802fffff 64bit pref]
[    0.567856] pci 0000:09:03.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.567862] pci 0000:09:03.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.567869] pci 0000:09:03.0: BAR 14: assigned [io  0x7000-0x70ff]
[    0.567874] pci 0000:09:03.0: BAR 13: assigned [io  0x7400-0x74ff]
[    0.567879] pci 0000:09:03.0: CardBus bridge to [bus 0a-0d]
[    0.567884] pci 0000:09:03.0:   bridge window [io  0x7400-0x74ff]
[    0.567893] pci 0000:09:03.0:   bridge window [io  0x7000-0x70ff]
[    0.567902] pci 0000:09:03.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.567911] pci 0000:09:03.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.567920] pci 0000:00:1e.0: PCI bridge to [bus 09-0a]
[    0.567926] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.567936] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.567945] pci 0000:00:1e.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.567969] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.567977] pci 0000:00:01.0: setting latency timer to 64
[    0.567989] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.568010] pci 0000:00:1c.0: setting latency timer to 64
[    0.568019] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.568027] pci 0000:00:1c.1: setting latency timer to 64
[    0.568040] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.568048] pci 0000:00:1c.2: setting latency timer to 64
[    0.568057] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.568066] pci 0000:00:1c.4: setting latency timer to 64
[    0.568075] pci 0000:00:1e.0: setting latency timer to 64
[    0.568086] pci 0000:09:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.568096] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.568099] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.568102] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.568105] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.568108] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.568111] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.568114] pci_bus 0000:00: resource 10 [mem 0x80000000-0xdfffffff]
[    0.568117] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.568120] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.568123] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.568126] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.568129] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.568132] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.568135] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.568139] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.568141] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.568144] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.568148] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.568150] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.568154] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.568157] pci_bus 0000:08: resource 0 [io  0x6000-0x6fff]
[    0.568160] pci_bus 0000:08: resource 1 [mem 0xfc000000-0xfc0fffff]
[    0.568163] pci_bus 0000:08: resource 2 [mem 0x80100000-0x802fffff 64bit pref]
[    0.568166] pci_bus 0000:09: resource 0 [io  0x7000-0x7fff]
[    0.568169] pci_bus 0000:09: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.568172] pci_bus 0000:09: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.568175] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.568178] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.568181] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.568183] pci_bus 0000:09: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.568186] pci_bus 0000:09: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.568189] pci_bus 0000:09: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.568192] pci_bus 0000:09: resource 10 [mem 0x80000000-0xdfffffff]
[    0.568195] pci_bus 0000:09: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.568198] pci_bus 0000:0a: resource 0 [io  0x7400-0x74ff]
[    0.568201] pci_bus 0000:0a: resource 1 [io  0x7000-0x70ff]
[    0.568204] pci_bus 0000:0a: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.568207] pci_bus 0000:0a: resource 3 [mem 0x88000000-0x8bffffff]
[    0.568254] NET: Registered protocol family 2
[    0.568337] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.568635] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.569094] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.569289] TCP: Hash tables configured (established 131072 bind 65536)
[    0.569295] TCP reno registered
[    0.569299] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.569311] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.569383] NET: Registered protocol family 1
[    0.569414] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.569439] pci 0000:00:1a.0: PCI INT A disabled
[    0.569458] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.569482] pci 0000:00:1a.1: PCI INT B disabled
[    0.569496] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.569532] pci 0000:00:1a.7: PCI INT C disabled
[    0.569563] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.569586] pci 0000:00:1d.0: PCI INT A disabled
[    0.569601] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.569625] pci 0000:00:1d.1: PCI INT B disabled
[    0.569636] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.569659] pci 0000:00:1d.2: PCI INT C disabled
[    0.569672] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.569694] pci 0000:00:1d.7: PCI INT A disabled
[    0.569758] pci 0000:01:00.0: Boot video device
[    0.569805] PCI: CLS 64 bytes, default 64
[    0.569812] Simple Boot Flag at 0x36 set to 0x1
[    0.570279] audit: initializing netlink socket (disabled)
[    0.570294] type=2000 audit(1347490606.564:1): initialized
[    0.593866] highmem bounce pool size: 64 pages
[    0.593875] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.596265] VFS: Disk quotas dquot_6.5.2
[    0.596342] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.597031] fuse init (API version 7.17)
[    0.597155] msgmni has been set to 1705
[    0.597616] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.597653] io scheduler noop registered
[    0.597659] io scheduler deadline registered
[    0.597670] io scheduler cfq registered (default)
[    0.597823] pcieport 0000:00:01.0: setting latency timer to 64
[    0.597864] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.597924] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.597984] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.598071] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.598131] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.598218] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.598277] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.598367] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.598426] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.598545] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.598580] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.598684] intel_idle: MWAIT substates: 0x22220
[    0.598686] intel_idle: does not run on family 6 model 15
[    0.612038] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.628044] ACPI: AC Adapter [ADP1] (on-line)
[    0.628133] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.644035] ACPI: Lid Switch [LID0]
[    0.644092] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.644102] ACPI: Power Button [PWRB]
[    0.678410] Monitor-Mwait will be used to enter C-1 state
[    0.678453] Monitor-Mwait will be used to enter C-2 state
[    0.678496] Monitor-Mwait will be used to enter C-3 state
[    0.678508] Marking TSC unstable due to TSC halts in idle
[    0.678528] ACPI: acpi_idle registered with cpuidle
[    0.732043] thermal LNXTHERM:00: registered as thermal_zone0
[    0.732049] ACPI: Thermal Zone [TZ00] (59 C)
[    0.748134] ACPI: Invalid active0 threshold
[    0.764049] thermal LNXTHERM:01: registered as thermal_zone1
[    0.764055] ACPI: Thermal Zone [TZ01] (59 C)
[    0.764077] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.764091] ACPI: Battery Slot [BAT0] (battery present)
[    0.764138] ERST: Table is not found!
[    0.764142] GHES: HEST is not enabled!
[    0.764196] isapnp: Scanning for PnP cards...
[    0.764237] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.060102] ACPI: Battery Slot [BAT0] (battery present)
[    1.119086] isapnp: No Plug & Play device found
[    1.168419] Linux agpgart interface v0.103
[    1.170558] brd: module loaded
[    1.171548] loop: module loaded
[    1.171677] ahci 0000:00:1f.2: version 3.0
[    1.171691] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.171746] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.171810] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    1.171819] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.171828] ahci 0000:00:1f.2: setting latency timer to 64
[    1.172283] scsi0 : ahci
[    1.172398] scsi1 : ahci
[    1.172501] scsi2 : ahci
[    1.172606] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 45
[    1.172613] ata2: DUMMY
[    1.172617] ata3: DUMMY
[    1.172715] ata_piix 0000:00:1f.1: version 2.13
[    1.172724] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.172766] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.173151] scsi3 : ata_piix
[    1.173248] scsi4 : ata_piix
[    1.173761] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    1.173768] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    1.174239] Fixed MDIO Bus: probed
[    1.174267] tun: Universal TUN/TAP device driver, 1.6
[    1.174272] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.174439] PPP generic driver version 2.4.2
[    1.174579] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.174602] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.174620] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.174625] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.174681] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.174715] ehci_hcd 0000:00:1a.7: debug port 1
[    1.178600] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.178618] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc404800
[    1.192022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.192185] hub 1-0:1.0: USB hub found
[    1.192193] hub 1-0:1.0: 4 ports detected
[    1.192287] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.192303] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.192308] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.192365] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.192399] ehci_hcd 0000:00:1d.7: debug port 1
[    1.196301] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.196318] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    1.212020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.212188] hub 2-0:1.0: USB hub found
[    1.212195] hub 2-0:1.0: 6 ports detected
[    1.212295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.212316] uhci_hcd: USB Universal Host Controller Interface driver
[    1.212339] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.212351] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.212355] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.212418] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.212464] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.212631] hub 3-0:1.0: USB hub found
[    1.212639] hub 3-0:1.0: 2 ports detected
[    1.212726] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.212739] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.212743] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.212803] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.212849] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.213004] hub 4-0:1.0: USB hub found
[    1.213011] hub 4-0:1.0: 2 ports detected
[    1.213099] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.213111] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.213115] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.213170] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.213204] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    1.213363] hub 5-0:1.0: USB hub found
[    1.213370] hub 5-0:1.0: 2 ports detected
[    1.213456] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.213468] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.213472] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.213528] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.213574] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    1.213735] hub 6-0:1.0: USB hub found
[    1.213742] hub 6-0:1.0: 2 ports detected
[    1.213826] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.213838] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.213842] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.213899] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.213932] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    1.214096] hub 7-0:1.0: USB hub found
[    1.214103] hub 7-0:1.0: 2 ports detected
[    1.214252] usbcore: registered new interface driver libusual
[    1.214309] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.218866] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.218875] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.219041] mousedev: PS/2 mouse device common for all mice
[    1.219449] rtc_cmos 00:07: RTC can wake from S4
[    1.219602] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.219639] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.219724] device-mapper: uevent: version 1.0.3
[    1.219830] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.219886] EISA: Probing bus 0 at eisa.0
[    1.219891] EISA: Cannot allocate resource for mainboard
[    1.219896] Cannot allocate resource for EISA slot 1
[    1.219900] Cannot allocate resource for EISA slot 2
[    1.219905] Cannot allocate resource for EISA slot 3
[    1.219909] Cannot allocate resource for EISA slot 4
[    1.219913] Cannot allocate resource for EISA slot 5
[    1.219918] Cannot allocate resource for EISA slot 6
[    1.219922] Cannot allocate resource for EISA slot 7
[    1.219926] Cannot allocate resource for EISA slot 8
[    1.219930] EISA: Detected 0 cards.
[    1.219944] cpufreq-nforce2: No nForce2 chipset.
[    1.220045] cpuidle: using governor ladder
[    1.220168] cpuidle: using governor menu
[    1.220173] EFI Variables Facility v0.08 2004-May-17
[    1.220511] TCP cubic registered
[    1.220657] NET: Registered protocol family 10
[    1.221410] NET: Registered protocol family 17
[    1.221418] Registering the dns_resolver key type
[    1.221448] Using IPI No-Shortcut mode
[    1.221649] PM: Hibernation image not present or could not be loaded.
[    1.221662] registered taskstats version 1
[    1.221930] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.232279]   Magic number: 12:146:957
[    1.232411] rtc_cmos 00:07: setting system clock to 2012-09-12 22:56:48 UTC (1347490608)
[    1.233020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.233026] EDD information not available.
[    1.344495] ata4.00: ATAPI: MATSHITABD-MLT UJ-220S, 1.01, max UDMA/33
[    1.360386] ata4.00: configured for UDMA/33
[    1.492097] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.492818] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.492822] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.493514] ata1.00: ATA-8: FUJITSU MHX2250BT, 0041000B, max UDMA/100
[    1.493521] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.494363] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.494368] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.495130] ata1.00: configured for UDMA/100
[    1.495327] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHX2250B 0041 PQ: 0 ANSI: 5
[    1.495489] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.495516] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.495549] sd 0:0:0:0: [sda] Write Protect is off
[    1.495555] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.495580] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.497756] scsi 3:0:0:0: CD-ROM            MATSHITA BD-MLT UJ-220S   1.01 PQ: 0 ANSI: 5
[    1.500905] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.500912] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.501084] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.501219] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.504049] usb 1-2: new high-speed USB device number 2 using ehci_hcd
[    1.567767]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.568590] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.568641] Freeing unused kernel memory: 712k freed
[    1.568975] Write protecting the kernel text: 5620k
[    1.569047] Write protecting the kernel read-only data: 2324k
[    1.587590] udevd[100]: starting version 175
[    1.671127] sky2: driver version 1.30
[    1.671178] sky2 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.671198] sky2 0000:08:00.0: setting latency timer to 64
[    1.671231] sky2 0000:08:00.0: Yukon-2 FE chip revision 1
[    1.671346] sky2 0000:08:00.0: irq 46 for MSI/MSI-X
[    1.672104] sky2 0000:08:00.0: eth0: addr 00:1a:80:48:da:94
[    1.696277] firewire_ohci 0000:09:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.752162] firewire_ohci: Added fw-ohci device 0000:09:03.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.088649] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.132066] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.252189] firewire_core: created device fw0: GUID 08004603028e99a6, S400
[    2.311040] hub 7-1:1.0: USB hub found
[    2.313004] hub 7-1:1.0: 3 ports detected
[    2.594011] usb 7-1.1: new full-speed USB device number 3 using uhci_hcd
[    2.806009] usb 7-1.2: new full-speed USB device number 4 using uhci_hcd
[    3.002007] usb 7-1.3: new full-speed USB device number 5 using uhci_hcd
[   26.992430] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.030450] udevd[294]: starting version 175
[   27.036787] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k 
[   27.095305] lp: driver loaded but no devices found
[   27.171219] sony_laptop: Sony Notebook Control Driver v0.6
[   27.252335] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY5001:00/input/input3
[   27.252521] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[   27.321823] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   27.393683] Linux video capture interface: v2.00
[   27.403163] cfg80211: Calling CRDA to update world regulatory domain
[   27.412684] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[   27.419050] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   27.420723] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   27.420734] uvcvideo: Failed to initialize the device (-5).
[   27.424830] usbcore: registered new interface driver uvcvideo
[   27.424834] USB Video Class driver (1.1.1)
[   27.452613] yenta_cardbus 0000:09:03.0: CardBus bridge found [104d:9005]
[   27.452638] yenta_cardbus 0000:09:03.0: Using CSCINT to route CSC interrupts to PCI
[   27.452642] yenta_cardbus 0000:09:03.0: Routing CardBus interrupts to PCI
[   27.452649] yenta_cardbus 0000:09:03.0: TI: mfunc 0x01121b22, devctl 0x64
[   27.456389] Bluetooth: Core ver 2.16
[   27.457447] NET: Registered protocol family 31
[   27.457451] Bluetooth: HCI device and connection manager initialized
[   27.457455] Bluetooth: HCI socket layer initialized
[   27.457457] Bluetooth: L2CAP socket layer initialized
[   27.457466] Bluetooth: SCO socket layer initialized
[   27.457999] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   27.464911] usbcore: registered new interface driver btusb
[   27.467866] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   27.467870] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   27.467958] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.468043] iwl4965 0000:06:00.0: setting latency timer to 64
[   27.468096] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   27.510703] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   27.558824] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.558963] iwl4965 0000:06:00.0: irq 47 for MSI/MSI-X
[   27.585248] input: HID 044e:3013 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.2/7-1.2:1.0/input/input5
[   27.585433] generic-usb 0003:044E:3013.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 044e:3013] on usb-0000:00:1d.2-1.2/input0
[   27.594982] usb 7-1.2: input irq status -75 received
[   27.599133] input: HID 044e:3012 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.3/7-1.3:1.0/input/input6
[   27.599365] generic-usb 0003:044E:3012.0002: input,hidraw1: USB HID v1.11 Mouse [HID 044e:3012] on usb-0000:00:1d.2-1.3/input0
[   27.599416] usbcore: registered new interface driver usbhid
[   27.599419] usbhid: USB HID core driver
[   27.610984] usb 7-1.2: input irq status -75 received
[   27.626982] usb 7-1.2: input irq status -75 received
[   27.634690] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.634754] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   27.634789] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   27.642982] usb 7-1.2: input irq status -75 received
[   27.658983] usb 7-1.2: input irq status -75 received
[   27.674983] usb 7-1.2: input irq status -75 received
[   27.684955] yenta_cardbus 0000:09:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   27.684960] yenta_cardbus 0000:09:03.0: Socket status: 30000006
[   27.684965] pci_bus 0000:09: Raising subordinate bus# of parent bus (#09) from #0a to #0d
[   27.684976] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   27.684980] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[   27.690985] usb 7-1.2: input irq status -75 received
[   27.704912] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.704916] Bluetooth: BNEP filters: protocol multicast
[   27.706978] usb 7-1.2: input irq status -75 received
[   27.709371] Bluetooth: RFCOMM TTY layer initialized
[   27.709378] Bluetooth: RFCOMM socket layer initialized
[   27.709380] Bluetooth: RFCOMM ver 1.11
[   27.722979] usb 7-1.2: input irq status -75 received
[   27.737499] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   27.737737] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   27.738983] usb 7-1.2: input irq status -75 received
[   27.742345] 
[   27.742353] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [mem 0xfc100000-0xfc1fffff]
[   27.742359] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc100000-0xfc1fffff: excluding 0xfc100000-0xfc10ffff
[   27.742375] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [mem 0x84000000-0x87ffffff pref]
[   27.742379] pcmcia_socket pcmcia_socket0: cs: memory probe 0x84000000-0x87ffffff: excluding 0x84000000-0x87ffffff
[   27.754577] cfg80211: World regulatory domain updated:
[   27.754581] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.754584] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.754588] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.754591] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.754594] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.754597] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.754980] usb 7-1.2: input irq status -75 received
[   27.763472] tifm_7xx1 0000:09:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   27.770980] usb 7-1.2: input irq status -75 received
[   27.786980] usb 7-1.2: input irq status -75 received
[   27.802979] usb 7-1.2: input irq status -75 received
[   27.818979] usb 7-1.2: input irq status -75 received
[   27.834983] usb 7-1.2: input irq status -75 received
[   27.848678] init: failsafe main process (610) killed by TERM signal
[   27.850983] usb 7-1.2: input irq status -75 received
[   27.866983] usb 7-1.2: input irq status -75 received
[   27.882984] usb 7-1.2: input irq status -75 received
[   27.898981] usb 7-1.2: input irq status -75 received
[   27.914979] usb 7-1.2: input irq status -75 received
[   27.925136] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   27.927550] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   27.928565] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   27.929389] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   27.930297] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xdc000-0xfffff
[   27.930333] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   27.930366] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   27.930400] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   27.930974] usb 7-1.2: input irq status -75 received
[   27.931333]  clean.
[   27.946974] usb 7-1.2: input irq status -75 received
[   27.962974] usb 7-1.2: input irq status -75 received
[   27.978976] usb 7-1.2: input irq status -75 received
[   27.994985] usb 7-1.2: input irq status -75 received
[   28.010985] usb 7-1.2: input irq status -75 received
[   28.026978] usb 7-1.2: input irq status -75 received
[   28.042975] usb 7-1.2: input irq status -75 received
[   28.058974] usb 7-1.2: input irq status -75 received
[   28.074973] usb 7-1.2: input irq status -75 received
[   28.145486] ppdev: user-space parallel port driver
[   28.181419] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   28.184869] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   28.185077] Registered led device: phy0-led
[   28.185114] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   28.199575] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   28.201188] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   28.531897] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.532329] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.537603] sky2 0000:08:00.0: eth0: enabling interface
[   28.538065] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.538925] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.385048] nvidia: module license 'NVIDIA' taints kernel.
[   29.385052] Disabling lock debugging due to kernel taint
[   29.739308] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.739326] nvidia 0000:01:00.0: setting latency timer to 64
[   29.739335] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   29.739576] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
[   30.033045] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   30.033048] vesafb: scrolling: redraw
[   30.033052] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   30.034730] vesafb: framebuffer at 0xcd000000, mapped to 0xf8600000, using 1216k, total 1216k
[   30.034883] Console: switching to colour frame buffer device 80x30
[   30.036399] fb0: VESA VGA frame buffer device
[   33.112556] wlan0: authenticate with 00:40:10:10:00:03 (try 1)
[   33.114421] wlan0: authenticated
[   33.114554] wlan0: associate with 00:40:10:10:00:03 (try 1)
[   33.117133] wlan0: RX AssocResp from 00:40:10:10:00:03 (capab=0x411 status=0 aid=4)
[   33.117137] wlan0: associated
[   33.146728] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.520040] wlan0: no IPv6 routers present
[   82.558494] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   82.559935] SGI XFS Quota Management subsystem
[   82.578491] JFS: nTxBlock = 8192, nTxLock = 65536
[   82.639983] NTFS driver 2.1.30 [Flags: R/O MODULE].
[   82.732703] QNX4 filesystem 0.2.3 registered.
[   82.857302] Btrfs loaded
```

---

### Post by HoneyGutClusters on 2012-09-12
And here's a dmesg, after I rebooted following successfully loading the module, where it subsequently failed to load the module.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-30-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48-Ubuntu SMP Fri Aug 24 16:54:40 UTC 2012 (Ubuntu 3.2.0-30.48-generic 3.2.27)
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
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Sony Corporation VGN-FZ283BN/VAIO, BIOS R1120J7 07/04/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 2  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00f8090] f8090
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 364f4000 - 37272000
[    0.000000] ACPI: RSDP 000f8060 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7fed7f39 00084 (v01   Sony     VAIO 20070704 PTL  00000000)
[    0.000000] ACPI: FACP 7fedfc04 000F4 (v03   Sony     VAIO 20070704 PTL  00000001)
[    0.000000] ACPI: DSDT 7fed9217 06979 (v02   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: APIC 7fedfcf8 00068 (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01   Sony     VAIO 20070704 PTL  0000005A)
[    0.000000] ACPI: SLIC 7fedfdd4 00176 (v01   Sony     VAIO 20070704 PTL  01000000)
[    0.000000] ACPI: TMOR 7fedff4a 00026 (v01   Sony     VAIO 20070704 PTL  00000003)
[    0.000000] ACPI: APIC 7fedff70 00068 (v01   Sony     VAIO 20070704 PTL  00000000)
[    0.000000] ACPI: BOOT 7fedffd8 00028 (v01   Sony     VAIO 20070704 PTL  00000001)
[    0.000000] ACPI: SSDT 7fed90fa 0011D (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed85a5 00287 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed84f1 000B4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: SSDT 7fed7fbd 00534 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c1822ec0, node_mem_map f54f4200
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
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519777
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic root=UUID=b0ea6cef-09a4-41f4-aea5-97263981433c ro blacklist=nouveau pci=use_crs
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8383488 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2046124k/2095936k available (5618k kernel code, 49360k reserved, 2762k data, 712k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157cac4 - 0xc182f5c0   (2762 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157cac4   (5618 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4808000 soft=f480a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.897 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.79 BogoMIPS (lpj=7979588)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004036] Security Framework initialized
[    0.004055] AppArmor: AppArmor initialized
[    0.004059] Yama: becoming mindful.
[    0.004118] Mount-cache hash table entries: 512
[    0.004259] Initializing cgroup subsys cpuacct
[    0.004268] Initializing cgroup subsys memory
[    0.004277] Initializing cgroup subsys devices
[    0.004281] Initializing cgroup subsys freezer
[    0.004286] Initializing cgroup subsys blkio
[    0.004294] Initializing cgroup subsys perf_event
[    0.004323] CPU: Physical Processor ID: 0
[    0.004327] CPU: Processor Core ID: 0
[    0.004333] mce: CPU supports 6 MCE banks
[    0.004343] CPU0: Thermal monitoring enabled (TM2)
[    0.004349] using mwait in idle threads.
[    0.009241] ACPI: Core revision 20110623
[    0.016031] ftrace: allocating 25901 entries in 51 pages
[    0.020053] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020499] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063689] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.064003] PEBS disabled due to CPU errata.
[    0.064003] ... version:                2
[    0.064003] ... bit width:              40
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             000000ffffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   3
[    0.064003] ... event mask:             0000000700000003
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] CPU 1 irqstacks, hard=f48ea000 soft=f48ec000
[    0.064003] Booting Node   0, Processors  #1 Ok.
[    0.064003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.152038] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152087] Brought up 2 CPUs
[    0.152092] Total of 2 processors activated (7979.76 BogoMIPS).
[    0.153457] devtmpfs: initialized
[    0.153457] EVM: security.selinux
[    0.153457] EVM: security.SMACK64
[    0.153457] EVM: security.capability
[    0.153457] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
[    0.153457] print_constraints: dummy: 
[    0.153457] RTC time: 23:19:26, date: 09/12/12
[    0.153457] NET: Registered protocol family 16
[    0.153457] Trying to unpack rootfs image as initramfs...
[    0.153464] EISA bus registered
[    0.153500] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.153507] ACPI: bus type pci registered
[    0.153584] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153592] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.153597] PCI: Using MMCONFIG for extended config space
[    0.153601] PCI: Using configuration type 1 for base access
[    0.156834] bio: create slab <bio-0> at 0
[    0.156938] ACPI: Added _OSI(Module Device)
[    0.156943] ACPI: Added _OSI(Processor Device)
[    0.156948] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.156953] ACPI: Added _OSI(Processor Aggregator Device)
[    0.158731] ACPI: EC: Look up EC in DSDT
[    0.161837] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.163065] ACPI: SSDT 7fed8d75 002A1 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.163511] ACPI: Dynamic OEM Table Load:
[    0.163518] ACPI: SSDT   (null) 002A1 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.163665] ACPI: SSDT 7fed882c 004B7 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164096] ACPI: Dynamic OEM Table Load:
[    0.164102] ACPI: SSDT   (null) 004B7 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164465] ACPI: SSDT 7fed9016 000E4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.164903] ACPI: Dynamic OEM Table Load:
[    0.164910] ACPI: SSDT   (null) 000E4 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.165033] ACPI: SSDT 7fed8ce3 00092 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.165456] ACPI: Dynamic OEM Table Load:
[    0.165463] ACPI: SSDT   (null) 00092 (v01   Sony     VAIO 20070704 PTL  20050624)
[    0.168038] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.384146] ACPI: Interpreter enabled
[    0.384169] ACPI: (supports S0 S3 S4 S5)
[    0.384200] ACPI: Using IOAPIC for interrupt routing
[    0.432672] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.438154] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.438354] ACPI: No dock devices found.
[    0.438360] HEST: Table not found.
[    0.438369] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.438915] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.439684] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.439691] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.439697] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.439704] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.439711] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.439717] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.439724] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.439731] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.439751] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.439811] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.439867] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.439872] pci 0000:00:01.0: PME# disabled
[    0.439932] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.439995] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.440050] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.440114] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.440177] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.440205] pci 0000:00:1a.7: reg 10: [mem 0xfc404800-0xfc404bff]
[    0.440323] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.440330] pci 0000:00:1a.7: PME# disabled
[    0.440364] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.440389] pci 0000:00:1b.0: reg 10: [mem 0xfc400000-0xfc403fff 64bit]
[    0.440506] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.440511] pci 0000:00:1b.0: PME# disabled
[    0.440545] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.440669] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.440675] pci 0000:00:1c.0: PME# disabled
[    0.440711] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.440835] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.440841] pci 0000:00:1c.1: PME# disabled
[    0.440877] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.441001] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.441007] pci 0000:00:1c.2: PME# disabled
[    0.441045] pci 0000:00:1c.4: [8086:2847] type 1 class 0x000604
[    0.441168] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.441174] pci 0000:00:1c.4: PME# disabled
[    0.441209] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.441272] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.441319] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.441382] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.441431] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.441494] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.441558] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.441585] pci 0000:00:1d.7: reg 10: [mem 0xfc404c00-0xfc404fff]
[    0.441704] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.441711] pci 0000:00:1d.7: PME# disabled
[    0.441738] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.441845] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.441969] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.441981] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.442054] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.442072] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.442086] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.442099] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.442113] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.442126] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.442187] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.442217] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.442231] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.442244] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.442258] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.442271] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.442285] pci 0000:00:1f.2: reg 24: [mem 0xfc404000-0xfc4047ff]
[    0.442358] pci 0000:00:1f.2: PME# supported from D3hot
[    0.442363] pci 0000:00:1f.2: PME# disabled
[    0.442388] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.442407] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.442453] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.442591] pci 0000:01:00.0: [10de:0426] type 0 class 0x000300
[    0.442641] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    0.442696] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.442751] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    0.442783] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.442819] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.472047] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.472060] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.472064] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.472070] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.472145] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.472153] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.472159] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.472168] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.472237] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.472245] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.472251] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.472260] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.472401] pci 0000:06:00.0: [8086:4229] type 0 class 0x000280
[    0.472459] pci 0000:06:00.0: reg 10: [mem 0xfa000000-0xfa001fff 64bit]
[    0.472705] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.472720] pci 0000:06:00.0: PME# disabled
[    0.480082] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.480091] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.480097] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.480107] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.480209] pci 0000:08:00.0: [11ab:4351] type 0 class 0x000200
[    0.480244] pci 0000:08:00.0: reg 10: [mem 0xfc000000-0xfc003fff 64bit]
[    0.480263] pci 0000:08:00.0: reg 18: [io  0x6000-0x60ff]
[    0.480430] pci 0000:08:00.0: supports D1 D2
[    0.480432] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.480440] pci 0000:08:00.0: PME# disabled
[    0.487616] Freeing initrd memory: 13816k freed
[    0.488069] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.488081] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.488087] pci 0000:00:1c.4:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.488170] pci 0000:09:03.0: [104c:8039] type 2 class 0x000607
[    0.488202] pci 0000:09:03.0: reg 10: [mem 0xfc100000-0xfc100fff]
[    0.488258] pci 0000:09:03.0: supports D1 D2
[    0.488261] pci 0000:09:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488269] pci 0000:09:03.0: PME# disabled
[    0.488299] pci 0000:09:03.1: [104c:803a] type 0 class 0x000c00
[    0.488329] pci 0000:09:03.1: reg 10: [mem 0xfc102000-0xfc1027ff]
[    0.488346] pci 0000:09:03.1: reg 14: [mem 0xfc104000-0xfc107fff]
[    0.488467] pci 0000:09:03.1: supports D1 D2
[    0.488470] pci 0000:09:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.488476] pci 0000:09:03.1: PME# disabled
[    0.488505] pci 0000:09:03.2: [104c:803b] type 0 class 0x000180
[    0.488534] pci 0000:09:03.2: reg 10: [mem 0xfc101000-0xfc101fff]
[    0.488663] pci 0000:09:03.2: supports D1 D2
[    0.488666] pci 0000:09:03.2: PME# supported from D0 D1 D2 D3hot
[    0.488672] pci 0000:09:03.2: PME# disabled
[    0.488753] pci 0000:00:1e.0: PCI bridge to [bus 09-0a] (subtractive decode)
[    0.488767] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.488778] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.488781] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.488785] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.488788] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.488792] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.488795] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.488799] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.488802] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.488865] pci_bus 0000:0a: [bus 0a-0d] partially hidden behind transparent bridge 0000:09 [bus 09-0a]
[    0.488919] pci_bus 0000:00: on NUMA node 0
[    0.488937] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.489280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.489496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.489612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.489724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.489838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.490155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.490508]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.490664]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x00
[    0.490672] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.505086] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.505158] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.505225] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.505289] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.505357] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.505423] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.505486] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.505550] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.505800] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.505800] vgaarb: loaded
[    0.505800] vgaarb: bridge control possible 0000:01:00.0
[    0.505800] i2c-core: driver [aat2870] using legacy suspend method
[    0.505800] i2c-core: driver [aat2870] using legacy resume method
[    0.505800] SCSI subsystem initialized
[    0.505800] libata version 3.00 loaded.
[    0.505800] usbcore: registered new interface driver usbfs
[    0.505800] usbcore: registered new interface driver hub
[    0.505800] usbcore: registered new device driver usb
[    0.505800] PCI: Using ACPI for IRQ routing
[    0.518195] PCI: pci_cache_line_size set to 64 bytes
[    0.518377] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.518380] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    0.518515] NetLabel: Initializing
[    0.518520] NetLabel:  domain hash size = 128
[    0.518524] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.518540] NetLabel:  unlabeled traffic allowed by default
[    0.518566] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.518566] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.518566] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.524180] Switching to clocksource hpet
[    0.533915] AppArmor: AppArmor Filesystem Enabled
[    0.533959] pnp: PnP ACPI init
[    0.533987] ACPI: bus type pnp registered
[    0.556444] pnp 00:00: [bus 00-ff]
[    0.556448] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.556451] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.556454] pnp 00:00: [io  0x0d00-0xffff window]
[    0.556457] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.556459] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.556462] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.556465] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.556468] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.556471] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.556473] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.556476] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.556479] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.556482] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.556485] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.556487] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.556490] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.556493] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.556496] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.556499] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.556502] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.556580] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.556673] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.556676] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.556678] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.556681] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.556684] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.556686] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.556689] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.556691] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.556766] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.556774] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.556780] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.556786] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.556792] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.556797] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.556803] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.556809] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.556816] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.557053] pnp 00:02: [io  0x0000-0x001f]
[    0.557055] pnp 00:02: [io  0x0081-0x0091]
[    0.557058] pnp 00:02: [io  0x0093-0x009f]
[    0.557060] pnp 00:02: [io  0x00c0-0x00df]
[    0.557063] pnp 00:02: [dma 4]
[    0.557119] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.557130] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.557183] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.557260] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.557340] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.557348] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.557361] pnp 00:05: [io  0x00f0]
[    0.557376] pnp 00:05: [irq 13]
[    0.557433] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.557447] pnp 00:06: [io  0x002e-0x002f]
[    0.557450] pnp 00:06: [io  0x004e-0x004f]
[    0.557452] pnp 00:06: [io  0x0061]
[    0.557454] pnp 00:06: [io  0x0063]
[    0.557457] pnp 00:06: [io  0x0065]
[    0.557459] pnp 00:06: [io  0x0067]
[    0.557461] pnp 00:06: [io  0x0080]
[    0.557464] pnp 00:06: [io  0x0092]
[    0.557466] pnp 00:06: [io  0x00b2-0x00b3]
[    0.557468] pnp 00:06: [io  0x0680-0x069f]
[    0.557471] pnp 00:06: [io  0x0800-0x080f]
[    0.557473] pnp 00:06: [io  0x1000-0x107f]
[    0.557476] pnp 00:06: [io  0x1180-0x11bf]
[    0.557478] pnp 00:06: [io  0x1640-0x164f]
[    0.557480] pnp 00:06: [io  0xfe00-0xfe7f]
[    0.557483] pnp 00:06: [io  0xfe80-0xfeff]
[    0.557577] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.557584] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.557589] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.557595] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.557600] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.557606] system 00:06: [io  0xfe00-0xfe7f] has been reserved
[    0.557612] system 00:06: [io  0xfe80-0xfeff] has been reserved
[    0.557618] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.557629] pnp 00:07: [io  0x0070-0x0077]
[    0.557636] pnp 00:07: [irq 8]
[    0.557693] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.557710] pnp 00:08: [io  0x0060]
[    0.557713] pnp 00:08: [io  0x0064]
[    0.557719] pnp 00:08: [irq 1]
[    0.557775] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.557789] pnp 00:09: [irq 12]
[    0.557846] pnp 00:09: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.557870] pnp: PnP ACPI: found 10 devices
[    0.557874] ACPI: ACPI bus type pnp unregistered
[    0.557881] PnPBIOS: Disabled by ACPI PNP
[    0.595542] PCI: max bus depth: 2 pci_try_num: 3
[    0.595610] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80000000-0x800000ff]
[    0.595621] pci 0000:00:1f.3: BAR 0: set to [mem 0x80000000-0x800000ff] (PCI address [0x80000000-0x800000ff])
[    0.595631] pci 0000:00:1e.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.595639] pci 0000:00:1e.0: BAR 13: assigned [io  0x7000-0x7fff]
[    0.595646] pci 0000:00:1c.4: BAR 15: assigned [mem 0x80100000-0x802fffff 64bit pref]
[    0.595654] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.595660] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.595665] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.595673] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.595680] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.595689] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.595695] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.595705] pci 0000:00:1c.0:   bridge window [mem 0xf6000000-0xf7ffffff]
[    0.595714] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.595726] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.595732] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.595742] pci 0000:00:1c.1:   bridge window [mem 0xf8000000-0xf9ffffff]
[    0.595751] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.595763] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.595770] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.595779] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.595788] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.595800] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    0.595807] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.595816] pci 0000:00:1c.4:   bridge window [mem 0xfc000000-0xfc0fffff]
[    0.595825] pci 0000:00:1c.4:   bridge window [mem 0x80100000-0x802fffff 64bit pref]
[    0.595840] pci 0000:09:03.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.595846] pci 0000:09:03.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.595853] pci 0000:09:03.0: BAR 14: assigned [io  0x7000-0x70ff]
[    0.595858] pci 0000:09:03.0: BAR 13: assigned [io  0x7400-0x74ff]
[    0.595864] pci 0000:09:03.0: CardBus bridge to [bus 0a-0d]
[    0.595868] pci 0000:09:03.0:   bridge window [io  0x7400-0x74ff]
[    0.595877] pci 0000:09:03.0:   bridge window [io  0x7000-0x70ff]
[    0.595885] pci 0000:09:03.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.595895] pci 0000:09:03.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.595904] pci 0000:00:1e.0: PCI bridge to [bus 09-0a]
[    0.595910] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.595920] pci 0000:00:1e.0:   bridge window [mem 0xfc100000-0xfc1fffff]
[    0.595928] pci 0000:00:1e.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.595953] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.595961] pci 0000:00:01.0: setting latency timer to 64
[    0.595973] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.595982] pci 0000:00:1c.0: setting latency timer to 64
[    0.595991] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.596011] pci 0000:00:1c.1: setting latency timer to 64
[    0.596023] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.596032] pci 0000:00:1c.2: setting latency timer to 64
[    0.596041] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.596049] pci 0000:00:1c.4: setting latency timer to 64
[    0.596059] pci 0000:00:1e.0: setting latency timer to 64
[    0.596069] pci 0000:09:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.596079] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.596082] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.596085] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.596088] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.596091] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.596094] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.596097] pci_bus 0000:00: resource 10 [mem 0x80000000-0xdfffffff]
[    0.596100] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.596103] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.596106] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.596109] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.596113] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.596116] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.596119] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.596122] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.596125] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.596128] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.596131] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.596134] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.596137] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.596140] pci_bus 0000:08: resource 0 [io  0x6000-0x6fff]
[    0.596143] pci_bus 0000:08: resource 1 [mem 0xfc000000-0xfc0fffff]
[    0.596146] pci_bus 0000:08: resource 2 [mem 0x80100000-0x802fffff 64bit pref]
[    0.596149] pci_bus 0000:09: resource 0 [io  0x7000-0x7fff]
[    0.596152] pci_bus 0000:09: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.596155] pci_bus 0000:09: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.596158] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.596161] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.596164] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.596167] pci_bus 0000:09: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.596170] pci_bus 0000:09: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.596173] pci_bus 0000:09: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.596176] pci_bus 0000:09: resource 10 [mem 0x80000000-0xdfffffff]
[    0.596179] pci_bus 0000:09: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.596182] pci_bus 0000:0a: resource 0 [io  0x7400-0x74ff]
[    0.596184] pci_bus 0000:0a: resource 1 [io  0x7000-0x70ff]
[    0.596187] pci_bus 0000:0a: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.596190] pci_bus 0000:0a: resource 3 [mem 0x88000000-0x8bffffff]
[    0.596235] NET: Registered protocol family 2
[    0.596315] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.596608] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.597069] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.597262] TCP: Hash tables configured (established 131072 bind 65536)
[    0.597267] TCP reno registered
[    0.597272] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.597284] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.597359] NET: Registered protocol family 1
[    0.597390] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.597416] pci 0000:00:1a.0: PCI INT A disabled
[    0.597435] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.597458] pci 0000:00:1a.1: PCI INT B disabled
[    0.597472] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.597508] pci 0000:00:1a.7: PCI INT C disabled
[    0.597538] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.597562] pci 0000:00:1d.0: PCI INT A disabled
[    0.597577] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.597601] pci 0000:00:1d.1: PCI INT B disabled
[    0.597612] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.597635] pci 0000:00:1d.2: PCI INT C disabled
[    0.597648] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.597670] pci 0000:00:1d.7: PCI INT A disabled
[    0.597748] PCI: CLS 64 bytes, default 64
[    0.597756] Simple Boot Flag at 0x36 set to 0x1
[    0.598228] audit: initializing netlink socket (disabled)
[    0.598243] type=2000 audit(1347491966.592:1): initialized
[    0.621813] highmem bounce pool size: 64 pages
[    0.621823] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.624223] VFS: Disk quotas dquot_6.5.2
[    0.624297] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.624986] fuse init (API version 7.17)
[    0.625112] msgmni has been set to 1705
[    0.625564] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.625601] io scheduler noop registered
[    0.625607] io scheduler deadline registered
[    0.625617] io scheduler cfq registered (default)
[    0.625768] pcieport 0000:00:01.0: setting latency timer to 64
[    0.625809] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.625873] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.625932] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.626020] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.626079] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.626166] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.626225] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.626317] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.626376] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.626493] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.626526] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.626633] intel_idle: MWAIT substates: 0x22220
[    0.626635] intel_idle: does not run on family 6 model 15
[    0.640039] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.656047] ACPI: AC Adapter [ADP1] (on-line)
[    0.656139] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.672035] ACPI: Lid Switch [LID0]
[    0.672093] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.672102] ACPI: Power Button [PWRB]
[    0.706408] Monitor-Mwait will be used to enter C-1 state
[    0.706452] Monitor-Mwait will be used to enter C-2 state
[    0.706494] Monitor-Mwait will be used to enter C-3 state
[    0.706506] Marking TSC unstable due to TSC halts in idle
[    0.706525] ACPI: acpi_idle registered with cpuidle
[    0.760044] thermal LNXTHERM:00: registered as thermal_zone0
[    0.760050] ACPI: Thermal Zone [TZ00] (54 C)
[    0.776135] ACPI: Invalid active0 threshold
[    0.792049] thermal LNXTHERM:01: registered as thermal_zone1
[    0.792055] ACPI: Thermal Zone [TZ01] (54 C)
[    0.792077] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.792091] ACPI: Battery Slot [BAT0] (battery present)
[    0.792136] ERST: Table is not found!
[    0.792140] GHES: HEST is not enabled!
[    0.792189] isapnp: Scanning for PnP cards...
[    0.792235] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.088102] ACPI: Battery Slot [BAT0] (battery present)
[    1.146291] isapnp: No Plug & Play device found
[    1.196421] Linux agpgart interface v0.103
[    1.198553] brd: module loaded
[    1.199551] loop: module loaded
[    1.199677] ahci 0000:00:1f.2: version 3.0
[    1.199691] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.199746] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.199810] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    1.199818] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.199828] ahci 0000:00:1f.2: setting latency timer to 64
[    1.200285] scsi0 : ahci
[    1.200398] scsi1 : ahci
[    1.200500] scsi2 : ahci
[    1.200605] ata1: SATA max UDMA/133 abar m2048@0xfc404000 port 0xfc404100 irq 45
[    1.200612] ata2: DUMMY
[    1.200616] ata3: DUMMY
[    1.200713] ata_piix 0000:00:1f.1: version 2.13
[    1.200723] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.200766] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.201145] scsi3 : ata_piix
[    1.201240] scsi4 : ata_piix
[    1.201748] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    1.201755] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    1.202233] Fixed MDIO Bus: probed
[    1.202261] tun: Universal TUN/TAP device driver, 1.6
[    1.202265] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.202433] PPP generic driver version 2.4.2
[    1.202564] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.202586] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.202604] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.202609] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.202666] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.202701] ehci_hcd 0000:00:1a.7: debug port 1
[    1.206585] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.206603] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc404800
[    1.220021] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.220196] hub 1-0:1.0: USB hub found
[    1.220204] hub 1-0:1.0: 4 ports detected
[    1.220300] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.220316] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.220320] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.220383] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.220418] ehci_hcd 0000:00:1d.7: debug port 1
[    1.224316] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.224333] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc404c00
[    1.240020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240167] hub 2-0:1.0: USB hub found
[    1.240174] hub 2-0:1.0: 6 ports detected
[    1.240273] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.240295] uhci_hcd: USB Universal Host Controller Interface driver
[    1.240318] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.240330] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.240334] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.240402] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.240447] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    1.240613] hub 3-0:1.0: USB hub found
[    1.240621] hub 3-0:1.0: 2 ports detected
[    1.240708] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.240720] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.240724] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.240779] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.240827] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    1.240986] hub 4-0:1.0: USB hub found
[    1.240993] hub 4-0:1.0: 2 ports detected
[    1.241081] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.241093] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.241097] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.241151] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.241185] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    1.241346] hub 5-0:1.0: USB hub found
[    1.241353] hub 5-0:1.0: 2 ports detected
[    1.241439] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.241451] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.241455] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.241509] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.241555] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    1.241712] hub 6-0:1.0: USB hub found
[    1.241719] hub 6-0:1.0: 2 ports detected
[    1.241807] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.241821] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.241825] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.241889] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.241923] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    1.242080] hub 7-0:1.0: USB hub found
[    1.242087] hub 7-0:1.0: 2 ports detected
[    1.242238] usbcore: registered new interface driver libusual
[    1.242298] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.245979] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.245989] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.246153] mousedev: PS/2 mouse device common for all mice
[    1.246399] rtc_cmos 00:07: RTC can wake from S4
[    1.246546] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.246585] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.246668] device-mapper: uevent: version 1.0.3
[    1.246785] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.246833] EISA: Probing bus 0 at eisa.0
[    1.246843] EISA: Cannot allocate resource for mainboard
[    1.246848] Cannot allocate resource for EISA slot 1
[    1.246852] Cannot allocate resource for EISA slot 2
[    1.246857] Cannot allocate resource for EISA slot 3
[    1.246861] Cannot allocate resource for EISA slot 4
[    1.246865] Cannot allocate resource for EISA slot 5
[    1.246869] Cannot allocate resource for EISA slot 6
[    1.246874] Cannot allocate resource for EISA slot 7
[    1.246878] Cannot allocate resource for EISA slot 8
[    1.246882] EISA: Detected 0 cards.
[    1.246895] cpufreq-nforce2: No nForce2 chipset.
[    1.246988] cpuidle: using governor ladder
[    1.247112] cpuidle: using governor menu
[    1.247117] EFI Variables Facility v0.08 2004-May-17
[    1.247448] TCP cubic registered
[    1.247593] NET: Registered protocol family 10
[    1.248350] NET: Registered protocol family 17
[    1.248357] Registering the dns_resolver key type
[    1.248381] Using IPI No-Shortcut mode
[    1.248580] PM: Hibernation image not present or could not be loaded.
[    1.248593] registered taskstats version 1
[    1.248869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.256890]   Magic number: 12:631:352
[    1.257007] rtc_cmos 00:07: setting system clock to 2012-09-12 23:19:27 UTC (1347491967)
[    1.257610] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.257616] EDD information not available.
[    1.372496] ata4.00: ATAPI: MATSHITABD-MLT UJ-220S, 1.01, max UDMA/33
[    1.388386] ata4.00: configured for UDMA/33
[    1.520098] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.520831] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.520835] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.521536] ata1.00: ATA-8: FUJITSU MHX2250BT, 0041000B, max UDMA/100
[    1.521543] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.522410] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.522414] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.523114] ata1.00: configured for UDMA/100
[    1.523309] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHX2250B 0041 PQ: 0 ANSI: 5
[    1.523471] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.523497] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.523531] sd 0:0:0:0: [sda] Write Protect is off
[    1.523537] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.523561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.525739] scsi 3:0:0:0: CD-ROM            MATSHITA BD-MLT UJ-220S   1.01 PQ: 0 ANSI: 5
[    1.528885] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.528893] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.529059] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.529195] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.532049] usb 1-2: new high-speed USB device number 2 using ehci_hcd
[    1.625193]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.626005] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.626056] Freeing unused kernel memory: 712k freed
[    1.626377] Write protecting the kernel text: 5620k
[    1.626450] Write protecting the kernel read-only data: 2324k
[    1.645126] udevd[100]: starting version 175
[    1.730146] sky2: driver version 1.30
[    1.730196] sky2 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.730215] sky2 0000:08:00.0: setting latency timer to 64
[    1.730246] sky2 0000:08:00.0: Yukon-2 FE chip revision 1
[    1.730360] sky2 0000:08:00.0: irq 46 for MSI/MSI-X
[    1.731068] sky2 0000:08:00.0: eth0: addr 00:1a:80:48:da:94
[    1.753687] firewire_ohci 0000:09:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.808146] firewire_ohci: Added fw-ohci device 0000:09:03.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.128080] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.146047] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.308160] firewire_core: created device fw0: GUID 08004603028e99a6, S400
[    2.309026] hub 7-1:1.0: USB hub found
[    2.310992] hub 7-1:1.0: 3 ports detected
[    2.589994] usb 7-1.1: new full-speed USB device number 3 using uhci_hcd
[    2.797998] usb 7-1.2: new full-speed USB device number 4 using uhci_hcd
[    2.993988] usb 7-1.3: new full-speed USB device number 5 using uhci_hcd
[   27.021284] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.047448] udevd[285]: starting version 175
[   27.124241] Adding 2094076k swap on /dev/sda5.  Priority:-1 extents:1 across:2094076k 
[   27.131163] lp: driver loaded but no devices found
[   27.212083] sony_laptop: Sony Notebook Control Driver v0.6
[   27.321850] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY5001:00/input/input3
[   27.322591] input: Sony Vaio Jogdial as /devices/virtual/input/input4
[   27.336057] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   27.388683] Bluetooth: Core ver 2.16
[   27.390777] NET: Registered protocol family 31
[   27.390782] Bluetooth: HCI device and connection manager initialized
[   27.390785] Bluetooth: HCI socket layer initialized
[   27.390788] Bluetooth: L2CAP socket layer initialized
[   27.390797] Bluetooth: SCO socket layer initialized
[   27.391653] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   27.394167] yenta_cardbus 0000:09:03.0: CardBus bridge found [104d:9005]
[   27.394193] yenta_cardbus 0000:09:03.0: Enabling burst memory read transactions
[   27.394200] yenta_cardbus 0000:09:03.0: Using CSCINT to route CSC interrupts to PCI
[   27.394203] yenta_cardbus 0000:09:03.0: Routing CardBus interrupts to PCI
[   27.394211] yenta_cardbus 0000:09:03.0: TI: mfunc 0x01121b22, devctl 0x64
[   27.394555] usbcore: registered new interface driver btusb
[   27.400702] cfg80211: Calling CRDA to update world regulatory domain
[   27.430910] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   27.430987] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   27.431021] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   27.444309] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   27.444312] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   27.444400] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.444430] iwl4965 0000:06:00.0: setting latency timer to 64
[   27.444483] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   27.486966] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   27.488553] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.488690] iwl4965 0000:06:00.0: irq 48 for MSI/MSI-X
[   27.504981] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   27.505156] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   27.612648] Linux video capture interface: v2.00
[   27.613332] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[   27.614010] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   27.614628] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   27.614638] uvcvideo: Failed to initialize the device (-5).
[   27.614694] usbcore: registered new interface driver uvcvideo
[   27.614696] USB Video Class driver (1.1.1)
[   27.620654] input: HID 044e:3013 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.2/7-1.2:1.0/input/input7
[   27.620943] generic-usb 0003:044E:3013.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 044e:3013] on usb-0000:00:1d.2-1.2/input0
[   27.624853] yenta_cardbus 0000:09:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   27.624858] yenta_cardbus 0000:09:03.0: Socket status: 30000006
[   27.624863] pci_bus 0000:09: Raising subordinate bus# of parent bus (#09) from #0a to #0d
[   27.624873] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   27.624877] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[   27.629037] input: HID 044e:3012 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1.3/7-1.3:1.0/input/input8
[   27.630969] usb 7-1.2: input irq status -75 received
[   27.632140] generic-usb 0003:044E:3012.0002: input,hidraw1: USB HID v1.11 Mouse [HID 044e:3012] on usb-0000:00:1d.2-1.3/input0
[   27.632163] usbcore: registered new interface driver usbhid
[   27.632165] usbhid: USB HID core driver
[   27.636319] 
[   27.636325] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [mem 0xfc100000-0xfc1fffff]
[   27.636329] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc100000-0xfc1fffff: excluding 0xfc100000-0xfc10ffff
[   27.636346] yenta_cardbus 0000:09:03.0: pcmcia: parent PCI bridge window: [mem 0x84000000-0x87ffffff pref]
[   27.636350] pcmcia_socket pcmcia_socket0: cs: memory probe 0x84000000-0x87ffffff: excluding 0x84000000-0x87ffffff
[   27.643289] tifm_7xx1 0000:09:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   27.646971] usb 7-1.2: input irq status -75 received
[   27.662973] usb 7-1.2: input irq status -75 received
[   27.678973] usb 7-1.2: input irq status -75 received
[   27.694972] usb 7-1.2: input irq status -75 received
[   27.710971] usb 7-1.2: input irq status -75 received
[   27.726975] usb 7-1.2: input irq status -75 received
[   27.727028] cfg80211: World regulatory domain updated:
[   27.727031] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.727034] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.727038] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.727041] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.727044] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.727047] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.742222] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   27.742444] Registered led device: phy0-led
[   27.742478] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   27.742975] usb 7-1.2: input irq status -75 received
[   27.749416] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   27.758970] usb 7-1.2: input irq status -75 received
[   27.774992] usb 7-1.2: input irq status -75 received
[   27.790990] usb 7-1.2: input irq status -75 received
[   27.806990] usb 7-1.2: input irq status -75 received
[   27.822986] usb 7-1.2: input irq status -75 received
[   27.838974] usb 7-1.2: input irq status -75 received
[   27.854992] usb 7-1.2: input irq status -75 received
[   27.870986] usb 7-1.2: input irq status -75 received
[   27.886986] usb 7-1.2: input irq status -75 received
[   27.902987] usb 7-1.2: input irq status -75 received
[   27.918988] usb 7-1.2: input irq status -75 received
[   27.934987] usb 7-1.2: input irq status -75 received
[   27.939739] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   27.941862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   27.942737] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   27.943454] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   27.944277] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xdc000-0xfffff
[   27.944310] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   27.944341] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   27.944371] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   27.950991] usb 7-1.2: input irq status -75 received
[   27.966990] usb 7-1.2: input irq status -75 received
[   27.982972] usb 7-1.2: input irq status -75 received
[   27.998970] usb 7-1.2: input irq status -75 received
[   28.011295] init: failsafe main process (588) killed by TERM signal
[   28.014980] usb 7-1.2: input irq status -75 received
[   28.030978] usb 7-1.2: input irq status -75 received
[   28.046980] usb 7-1.2: input irq status -75 received
[   28.062969] usb 7-1.2: input irq status -75 received
[   28.078992] usb 7-1.2: input irq status -75 received
[   28.080413] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   28.094994] usb 7-1.2: input irq status -75 received
[   28.097230] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   28.110974] usb 7-1.2: input irq status -75 received
[   28.300215] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.300219] Bluetooth: BNEP filters: protocol multicast
[   28.302157] ppdev: user-space parallel port driver
[   28.323986] Bluetooth: RFCOMM TTY layer initialized
[   28.323993] Bluetooth: RFCOMM socket layer initialized
[   28.323995] Bluetooth: RFCOMM ver 1.11
[   28.657120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.657675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.662915] sky2 0000:08:00.0: eth0: enabling interface
[   28.664376] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.665014] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.371025] nvidia: module license 'NVIDIA' taints kernel.
[   29.371029] Disabling lock debugging due to kernel taint
[   29.725505] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   29.725515] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.725528] nvidia 0000:01:00.0: setting latency timer to 64
[   29.725534] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   29.725574] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:0426) installed
[   29.725575] NVRM: in this system is not supported by the 295.40 NVIDIA Linux
[   29.725577] NVRM: graphics driver release.  Please see 'Appendix A -
[   29.725578] NVRM: Supported NVIDIA GPU Products' in this release's README,
[   29.725579] NVRM: available on the Linux graphics driver download page at
[   29.725581] NVRM: www.nvidia.com.
[   29.725590] nvidia 0000:01:00.0: PCI INT A disabled
[   29.725600] nvidia: probe of 0000:01:00.0 failed with error -1
[   29.726470] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   29.726474] NVRM: None of the NVIDIA graphics adapters were initialized!
[   29.818974] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   29.818977] vesafb: scrolling: redraw
[   29.818981] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   29.820135] vesafb: framebuffer at 0xcd000000, mapped to 0xf8380000, using 1216k, total 1216k
[   29.820294] Console: switching to colour frame buffer device 80x30
[   29.821634] fb0: VESA VGA frame buffer device
[   32.580744] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.580758] nvidia 0000:01:00.0: setting latency timer to 64
[   32.580763] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=io+mem
[   32.580796] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:0426) installed
[   32.580798] NVRM: in this system is not supported by the 295.40 NVIDIA Linux
[   32.580799] NVRM: graphics driver release.  Please see 'Appendix A -
[   32.580800] NVRM: Supported NVIDIA GPU Products' in this release's README,
[   32.580801] NVRM: available on the Linux graphics driver download page at
[   32.580802] NVRM: www.nvidia.com.
[   32.580811] nvidia 0000:01:00.0: PCI INT A disabled
[   32.580820] nvidia: probe of 0000:01:00.0 failed with error -1
[   32.580851] NVRM: The NVIDIA probe routine failed for 1 device(s).
[   32.580853] NVRM: None of the NVIDIA graphics adapters were initialized!
[   33.256801] wlan0: authenticate with 00:40:10:10:00:03 (try 1)
[   33.258625] wlan0: authenticated
[   33.258762] wlan0: associate with 00:40:10:10:00:03 (try 1)
[   33.261336] wlan0: RX AssocResp from 00:40:10:10:00:03 (capab=0x411 status=0 aid=4)
[   33.261340] wlan0: associated
[   33.291018] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.627563] iwl4965 0000:06:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   37.627568] iwl4965 0000:06:00.0: Loaded firmware version: 228.61.2.24
[   37.627588] iwl4965 0000:06:00.0: Start IWL Error Log Dump:
[   37.627591] iwl4965 0000:06:00.0: Status: 0x000213E4, count: 5
[   37.627767] iwl4965 0000:06:00.0: Desc                                  Time       data1      data2      line
[   37.627771] iwl4965 0000:06:00.0: FH_ERROR                     (0x000C) 3222507858 0x00000008 0x03130000 208
[   37.627774] iwl4965 0000:06:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
[   37.627777] iwl4965 0000:06:00.0: 0x0046C 0x04502 0x004C2 0x006DE 0x016BC 0x235001C
[   37.627780] iwl4965 0000:06:00.0: FH register values:
[   37.627798] iwl4965 0000:06:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0314cb00
[   37.627815] iwl4965 0000:06:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X003165a0
[   37.627832] iwl4965 0000:06:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000b8
[   37.627850] iwl4965 0000:06:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819000
[   37.627867] iwl4965 0000:06:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
[   37.627884] iwl4965 0000:06:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03130000
[   37.627902] iwl4965 0000:06:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   37.627919] iwl4965 0000:06:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0002
[   37.627936] iwl4965 0000:06:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   37.628273] ieee80211 phy0: Hardware restart was requested
[   45.088073] wlan0: no IPv6 routers present
```

---

### Post by HoneyGutClusters on 2012-09-12
One more thing to note: After the modifications I made in my first post, now it seems that the module will load properly on a cold boot, but will fail to load if I reboot from the OS. By shutting down first, then cold booting, the module will load successfully again.

Curiouser and curiouser...

Other notes:

Issue exists on the 295.40 driver in the repos as well as the 295.71 and 304.43 drivers from nVidia
Issue exists on kernels 3.2.0-23, 3.2.0-30, and 3.5.0-14 from the Quantal repositories.

---

### Post by BicyclerBoy on 2012-09-13
Your GPU is an old 8400m (10de:0426) certainly supported from away back..

One of your dmesg shows nVidia 304 & one shows 294 kernel module..
Are you using grub to boot a different kernel images that have different kernel modules ?

How did you install the nVidia driver ?

Isn't "pci=use"_crs default?

There is a launchpad bug report suggesting that only 64 bit kernel works on your h/w..

---

### Post by HoneyGutClusters on 2012-09-13
I've tried the drivers provided by the "nvidia-current" package (which I am currently running) and, during my troubleshooting, I've tried 295.71 and 304.43 from nVidia, all with similar results.

At the moment, the module provided by "nvidia-current" is working for me, but will fail to reload if I reboot the machine. However, if I cold boot, it loads properly.

Also, I tried the pci=use_crs" argument after seeing this pop up in dmesg:

```
[    0.391048] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug

```

This was my kernel parameters when this appeared:
```
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-30-generic root=UUID=b0ea6cef-09a4-41f4-aea5-97263981433c ro blacklist=nouveau

```

---

### Post by HoneyGutClusters on 2012-09-13
lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

verbose lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [88] Subsystem: Sony Corporation Device 9005
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4169
	Capabilities: [a0] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise-
			Slot #1, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Off, PwrInd On, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [140 v1] Root Complex Link
		Desc:	PortNumber=02 ComponentID=01 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=01 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed19000
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fc404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 41b1
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=1 ArbSelect=Fixed TC/VC=80
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c000
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #2, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4171
	Capabilities: [90] Subsystem: Sony Corporation Device 9005
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=01 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #3, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4179
	Capabilities: [90] Subsystem: Sony Corporation Device 9005
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=02 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #3, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #4, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4181
	Capabilities: [90] Subsystem: Sony Corporation Device 9005
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=03 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fc000000-fc0fffff
	Prefetchable memory behind bridge: 0000000080100000-00000000802fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #5, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #2, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4189
	Capabilities: [90] Subsystem: Sony Corporation Device 9005
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=05 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fc404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=09, subordinate=0d, sec-latency=56
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fc100000-fc1fffff
	Prefetchable memory behind bridge: 0000000084000000-0000000087ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: Sony Corporation Device 9005

00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 45
	Region 0: I/O ports at 18d8 [size=8]
	Region 1: I/O ports at 18cc [size=4]
	Region 2: I/O ports at 18d0 [size=8]
	Region 3: I/O ports at 18c8 [size=4]
	Region 4: I/O ports at 18e0 [size=32]
	Region 5: Memory at fc404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
		Address: fee0300c  Data: 4191
	Capabilities: [70] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a8] SATA HBA v1.0 BAR4 Offset=00000004
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Vaio VGN-FZ260E
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 10
	Region 0: Memory at 80000000 (32-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GT] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device 9005
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 2000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [128 v1] Power Budgeting <?>
	Capabilities: [600 v1] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 47
	Region 0: Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 41a1
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [140 v1] Device Serial Number 00-13-e8-ff-ff-7e-16-51
	Kernel driver in use: iwl4965
	Kernel modules: iwl4965

08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
	Subsystem: Sony Corporation Device 9005
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at 6000 [size=256]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
		Product Name: Marvell Yukon 88E8036 Fast Ethernet Controller
		Read-only fields:
			[PN] Part number: Yukon 88E8036
			[EC] Engineering changes: Rev. 1.6
			[MN] Manufacture ID: 4d 61 72 76 65 6c 6c
			[SN] Serial number: AbCdEfG48DA94
			[CP] Extended capability: 01 10 cc 03
			[RV] Reserved: checksum good, 12 byte(s) reserved
		Read/write fields:
			[RW] Read-write area: 121 byte(s) free
		End
	Capabilities: [5c] MSI: Enable+ Count=1/2 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4199
	Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <256ns, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		AERCap:	First Error Pointer: 1f, GenCap- CGenEn- ChkCap- ChkEn-
	Kernel driver in use: sky2
	Kernel modules: sky2

09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 9005
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
	Memory window 0: 84000000-87fff000 (prefetchable)
	Memory window 1: 88000000-8bfff000
	I/O window 0: 00007400-000074ff
	I/O window 1: 00007000-000070ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Device 9005
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (750ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fc102000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fc104000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 9005
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 57 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fc101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

```
cat /proc/interrupts
```

           CPU0       CPU1       
  0:      79482     112247   IO-APIC-edge      timer
  1:       2724       2575   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:         55         15   IO-APIC-fasteoi   acpi
 12:      70709        633   IO-APIC-edge      i8042
 14:       1204        895   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:        986       1084   IO-APIC-fasteoi   uhci_hcd:usb3, yenta, nvidia
 17:         20         14   IO-APIC-fasteoi   firewire_ohci
 18:        183        168   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, tifm_7xx1
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb6
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:          1          1   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 45:       8589       8376   PCI-MSI-edge      ahci
 46:          1          0   PCI-MSI-edge      eth0
 47:      47797        442   PCI-MSI-edge      iwl4965
 48:         94         91   PCI-MSI-edge      snd_hda_intel
NMI:         99         98   Non-maskable interrupts
LOC:      70218      75134   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:         99         98   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:     155133     187852   Rescheduling interrupts
CAL:        296        145   Function call interrupts
TLB:       7546       8863   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          7          7   Machine check polls
ERR:          0
MIS:          0

```

and, just to confirm I only have one version installed, ran updatedb, then "locate nvidia"
```

/etc/OpenCL/vendors/nvidia.icd
/etc/alternatives/i386-linux-gnu_libvdpau_nvidia.so
/etc/alternatives/i386-linux-gnu_libvdpau_nvidia.so.1
/etc/alternatives/i386-linux-gnu_man_nvidiaxconfig.gz
/etc/alternatives/i386-linux-gnu_nvidia-autostart.desktop
/etc/alternatives/i386-linux-gnu_nvidia-smi.1.gz
/etc/alternatives/i386-linux-gnu_nvidia.icd
/etc/alternatives/i386-linux-gnu_nvidia_bug_report
/etc/alternatives/i386-linux-gnu_nvidia_desktop
/etc/alternatives/i386-linux-gnu_nvidia_drv
/etc/alternatives/i386-linux-gnu_nvidia_modconf
/etc/alternatives/i386-linux-gnu_nvidia_smi
/etc/alternatives/i386-linux-gnu_nvidia_xconfig
/etc/alternatives/man_nvidiasettings.gz
/etc/alternatives/nvidia_settings
/etc/alternatives/nvidia_settings_conf
/etc/ld.so.conf.d/nvidia_settings.conf
/etc/modprobe.d/nvidia-graphics-drivers.conf
/etc/xdg/autostart/nvidia-autostart.desktop
/home/tbest/.nvidia-settings-rc
/home/tbest/nvidia-bug-report.log.gz
/lib/nvidia-current
/lib/modules/3.2.0-23-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-23-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
/lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-23-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.2.0-30-generic/kernel/drivers/char/drm/nvidia_current.ko
/lib/modules/3.2.0-30-generic/kernel/drivers/net/ethernet/nvidia
/lib/modules/3.2.0-30-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
/lib/modules/3.2.0-30-generic/kernel/drivers/video/nvidia
/lib/modules/3.2.0-30-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/nvidia-current/modprobe.conf
/root/.nvidia-settings-rc
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-settings
/usr/bin/nvidia-smi
/usr/bin/nvidia-xconfig
/usr/lib/libvdpau_nvidia.so
/usr/lib/nvidia-current
/usr/lib/nvidia-settings
/usr/lib/directfb-1.2-9/gfxdrivers/libdirectfb_nvidia.so
/usr/lib/nvidia-current/XvMCConfig
/usr/lib/nvidia-current/alt_ld.so.conf
/usr/lib/nvidia-current/bin
/usr/lib/nvidia-current/ld.so.conf
/usr/lib/nvidia-current/libGL.so
/usr/lib/nvidia-current/libGL.so.1
/usr/lib/nvidia-current/libGL.so.295.40
/usr/lib/nvidia-current/libOpenCL.so
/usr/lib/nvidia-current/libOpenCL.so.1
/usr/lib/nvidia-current/libOpenCL.so.1.0
/usr/lib/nvidia-current/libOpenCL.so.1.0.0
/usr/lib/nvidia-current/libXvMCNVIDIA.so
/usr/lib/nvidia-current/libXvMCNVIDIA.so.1
/usr/lib/nvidia-current/libXvMCNVIDIA.so.295.40
/usr/lib/nvidia-current/libXvMCNVIDIA_dynamic.so.1
/usr/lib/nvidia-current/libcuda.so
/usr/lib/nvidia-current/libcuda.so.1
/usr/lib/nvidia-current/libcuda.so.295.40
/usr/lib/nvidia-current/libnvcuvid.so
/usr/lib/nvidia-current/libnvcuvid.so.1
/usr/lib/nvidia-current/libnvcuvid.so.295.40
/usr/lib/nvidia-current/libnvidia-cfg.so
/usr/lib/nvidia-current/libnvidia-cfg.so.1
/usr/lib/nvidia-current/libnvidia-cfg.so.295.40
/usr/lib/nvidia-current/libnvidia-compiler.so
/usr/lib/nvidia-current/libnvidia-compiler.so.1
/usr/lib/nvidia-current/libnvidia-compiler.so.295.40
/usr/lib/nvidia-current/libnvidia-glcore.so.295.40
/usr/lib/nvidia-current/libnvidia-ml.so
/usr/lib/nvidia-current/libnvidia-ml.so.1
/usr/lib/nvidia-current/libnvidia-ml.so.295.40
/usr/lib/nvidia-current/libnvidia-tls.so.295.40
/usr/lib/nvidia-current/libnvidia-wfb.so.1
/usr/lib/nvidia-current/libnvidia-wfb.so.295.40
/usr/lib/nvidia-current/tls
/usr/lib/nvidia-current/vdpau
/usr/lib/nvidia-current/xorg
/usr/lib/nvidia-current/bin/nvidia-bug-report.sh
/usr/lib/nvidia-current/bin/nvidia-smi
/usr/lib/nvidia-current/bin/nvidia-xconfig
/usr/lib/nvidia-current/tls/libnvidia-tls.so.295.40
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1
/usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.295.40
/usr/lib/nvidia-current/xorg/libglx.so
/usr/lib/nvidia-current/xorg/libglx.so.295.40
/usr/lib/nvidia-current/xorg/nvidia_drv.so
/usr/lib/nvidia-settings/bin
/usr/lib/nvidia-settings/include
/usr/lib/nvidia-settings/ld.so.conf
/usr/lib/nvidia-settings/libXNVCtrl.a
/usr/lib/nvidia-settings/share
/usr/lib/nvidia-settings/bin/nvidia-settings
/usr/lib/nvidia-settings/include/NVCtrl
/usr/lib/nvidia-settings/include/NVCtrl/NVCtrl.h
/usr/lib/nvidia-settings/include/NVCtrl/NVCtrlLib.h
/usr/lib/nvidia-settings/share/man
/usr/lib/nvidia-settings/share/man/man1
/usr/lib/nvidia-settings/share/man/man1/alt-nvidia-settings.1.gz
/usr/lib/vdpau/libvdpau_nvidia.so.1
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib32/nvidia-current
/usr/share/nvidia-current
/usr/share/applications/ubuntu-nvidia-settings.desktop
/usr/share/doc/nvidia-current
/usr/share/doc/nvidia-settings
/usr/share/doc/nvidia-current/NVIDIA_Changelog.gz
/usr/share/doc/nvidia-current/README.Debian
/usr/share/doc/nvidia-current/README.txt.gz
/usr/share/doc/nvidia-current/changelog.Debian.gz
/usr/share/doc/nvidia-current/copyright
/usr/share/doc/nvidia-current/html
/usr/share/doc/nvidia-current/html/acknowledgements.html
/usr/share/doc/nvidia-current/html/addtlresources.html
/usr/share/doc/nvidia-current/html/appendices.html
/usr/share/doc/nvidia-current/html/audiosupport.html
/usr/share/doc/nvidia-current/html/commonproblems.html
/usr/share/doc/nvidia-current/html/configlaptop.html
/usr/share/doc/nvidia-current/html/configmultxscreens.html
/usr/share/doc/nvidia-current/html/configtvout.html
/usr/share/doc/nvidia-current/html/configtwinview.html
/usr/share/doc/nvidia-current/html/configuringagp.html
/usr/share/doc/nvidia-current/html/depth30.html
/usr/share/doc/nvidia-current/html/displaydevicenames.html
/usr/share/doc/nvidia-current/html/dma_issues.html
/usr/share/doc/nvidia-current/html/dpi.html
/usr/share/doc/nvidia-current/html/editxconfig.html
/usr/share/doc/nvidia-current/html/faq.html
/usr/share/doc/nvidia-current/html/flippingubb.html
/usr/share/doc/nvidia-current/html/framelock.html
/usr/share/doc/nvidia-current/html/glxsupport.html
/usr/share/doc/nvidia-current/html/i2c.html
/usr/share/doc/nvidia-current/html/index.html
/usr/share/doc/nvidia-current/html/installationandconfiguration.html
/usr/share/doc/nvidia-current/html/installdriver.html
/usr/share/doc/nvidia-current/html/installedcomponents.html
/usr/share/doc/nvidia-current/html/introduction.html
/usr/share/doc/nvidia-current/html/knownissues.html
/usr/share/doc/nvidia-current/html/minimumrequirements.html
/usr/share/doc/nvidia-current/html/newusertips.html
/usr/share/doc/nvidia-current/html/nvidia-debugdump.html
/usr/share/doc/nvidia-current/html/nvidia-ml.html
/usr/share/doc/nvidia-current/html/nvidia-smi.html
/usr/share/doc/nvidia-current/html/nvidiasettings.html
/usr/share/doc/nvidia-current/html/openglenvvariables.html
/usr/share/doc/nvidia-current/html/optimus.html
/usr/share/doc/nvidia-current/html/powermanagement.html
/usr/share/doc/nvidia-current/html/procinterface.html
/usr/share/doc/nvidia-current/html/programmingmodes.html
/usr/share/doc/nvidia-current/html/sdi.html
/usr/share/doc/nvidia-current/html/selectdriver.html
/usr/share/doc/nvidia-current/html/sli.html
/usr/share/doc/nvidia-current/html/supportedchips.html
/usr/share/doc/nvidia-current/html/vdpausupport.html
/usr/share/doc/nvidia-current/html/xcompositeextension.html
/usr/share/doc/nvidia-current/html/xconfigoptions.html
/usr/share/doc/nvidia-current/html/xineramaglx.html
/usr/share/doc/nvidia-current/html/xrandrextension.html
/usr/share/doc/nvidia-current/html/xvmcsupport.html
/usr/share/doc/nvidia-settings/FRAMELOCK.txt.gz
/usr/share/doc/nvidia-settings/NV-CONTROL-API.txt.gz
/usr/share/doc/nvidia-settings/changelog.Debian.gz
/usr/share/doc/nvidia-settings/copyright
/usr/share/doc/nvidia-settings/examples
/usr/share/doc/nvidia-settings/examples/samples
/usr/share/doc/nvidia-settings/examples/samples/Makefile
/usr/share/doc/nvidia-settings/examples/samples/README
/usr/share/doc/nvidia-settings/examples/samples/nv-control-3dvisionpro.c
/usr/share/doc/nvidia-settings/examples/samples/nv-control-dpy.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-dvc.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-events.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-framelock.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-gvi.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-info.c.gz
/usr/share/doc/nvidia-settings/examples/samples/nv-control-screen.h
/usr/share/doc/nvidia-settings/examples/samples/nv-control-targets.c.gz
/usr/share/doc/nvidia-settings/examples/samples/src.mk
/usr/share/hal/fdi/information/10freedesktop/21-video-quirk-nvidia.fdi
/usr/share/icons/Mint-X/apps/16/nvidia-current-settings.png
/usr/share/icons/Mint-X/apps/16/nvidia-settings.png
/usr/share/icons/Mint-X/apps/22/nvidia-current-settings.png
/usr/share/icons/Mint-X/apps/22/nvidia-settings.png
/usr/share/icons/Mint-X/apps/24/nvidia-current-settings.png
/usr/share/icons/Mint-X/apps/24/nvidia-settings.png
/usr/share/icons/Mint-X/apps/32/nvidia-current-settings.png
/usr/share/icons/Mint-X/apps/32/nvidia-settings.png
/usr/share/icons/Mint-X/apps/48/nvidia-current-settings.png
/usr/share/icons/Mint-X/apps/48/nvidia-settings.png
/usr/share/icons/Mint-X/apps/scalable/nvidia-current-settings.svg
/usr/share/icons/Mint-X/apps/scalable/nvidia-settings.svg
/usr/share/jockey/handlers/nvidia.py
/usr/share/jockey/modaliases/disable-upstream-nvidia
/usr/share/lintian/overrides/nvidia-current.override
/usr/share/man/man1/alt-nvidia-current-settings.1.gz
/usr/share/man/man1/alt-nvidia-current-smi.1.gz
/usr/share/man/man1/alt-nvidia-current-xconfig.1.gz
/usr/share/man/man1/nvidia-settings.1.gz
/usr/share/man/man1/nvidia-smi.1.gz
/usr/share/man/man1/nvidia-xconfig.1.gz
/usr/share/nvidia-current/nvidia-autostart.desktop
/usr/share/nvidia-current/nvidia-current.grub-gfxpayload
/usr/share/nvidia-current/nvidia.icd
/usr/share/nvidia-current/ubuntu-nvidia-settings.desktop
/usr/share/pixmaps/nvidia-current-settings.png
/usr/share/screen-resolution-extra/nvidia-polkit.py
/usr/share/screen-resolution-extra/nvidia-polkit.pyc
/usr/src/nvidia-current-295.40
/usr/src/linux-headers-3.2.0-23/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-23/drivers/net/ethernet/nvidia/Kconfig
/usr/src/linux-headers-3.2.0-23/drivers/net/ethernet/nvidia/Makefile
/usr/src/linux-headers-3.2.0-23/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-23/drivers/video/nvidia/Makefile
/usr/src/linux-headers-3.2.0-23-generic/include/config/agp/nvidia.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia/backlight.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/fb/nvidia/i2c.h
/usr/src/linux-headers-3.2.0-23-generic/include/config/net/vendor/nvidia.h
/usr/src/linux-headers-3.2.0-30/drivers/net/ethernet/nvidia
/usr/src/linux-headers-3.2.0-30/drivers/net/ethernet/nvidia/Kconfig
/usr/src/linux-headers-3.2.0-30/drivers/net/ethernet/nvidia/Makefile
/usr/src/linux-headers-3.2.0-30/drivers/video/nvidia
/usr/src/linux-headers-3.2.0-30/drivers/video/nvidia/Makefile
/usr/src/linux-headers-3.2.0-30-generic/include/config/agp/nvidia.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia/backlight.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/fb/nvidia/i2c.h
/usr/src/linux-headers-3.2.0-30-generic/include/config/net/vendor/nvidia.h
/usr/src/nvidia-current-295.40/Makefile
/usr/src/nvidia-current-295.40/Makefile.kbuild
/usr/src/nvidia-current-295.40/Makefile.nvidia
/usr/src/nvidia-current-295.40/conftest.sh
/usr/src/nvidia-current-295.40/cpuopsys.h
/usr/src/nvidia-current-295.40/dkms.conf
/usr/src/nvidia-current-295.40/g_nvreadme.h
/usr/src/nvidia-current-295.40/gcc-version-check.c
/usr/src/nvidia-current-295.40/makefile
/usr/src/nvidia-current-295.40/nv-acpi.c
/usr/src/nvidia-current-295.40/nv-chrdev.c
/usr/src/nvidia-current-295.40/nv-cray.c
/usr/src/nvidia-current-295.40/nv-gvi.c
/usr/src/nvidia-current-295.40/nv-i2c.c
/usr/src/nvidia-current-295.40/nv-kernel.o
/usr/src/nvidia-current-295.40/nv-linux.h
/usr/src/nvidia-current-295.40/nv-memdbg.h
/usr/src/nvidia-current-295.40/nv-mempool.c
/usr/src/nvidia-current-295.40/nv-misc.h
/usr/src/nvidia-current-295.40/nv-mlock.c
/usr/src/nvidia-current-295.40/nv-mmap.c
/usr/src/nvidia-current-295.40/nv-p2p.c
/usr/src/nvidia-current-295.40/nv-p2p.h
/usr/src/nvidia-current-295.40/nv-pat.c
/usr/src/nvidia-current-295.40/nv-procfs.c
/usr/src/nvidia-current-295.40/nv-proto.h
/usr/src/nvidia-current-295.40/nv-reg.h
/usr/src/nvidia-current-295.40/nv-usermap.c
/usr/src/nvidia-current-295.40/nv-vm.c
/usr/src/nvidia-current-295.40/nv-vtophys.c
/usr/src/nvidia-current-295.40/nv.c
/usr/src/nvidia-current-295.40/nv.h
/usr/src/nvidia-current-295.40/nverror.h
/usr/src/nvidia-current-295.40/nvtypes.h
/usr/src/nvidia-current-295.40/os-agp.c
/usr/src/nvidia-current-295.40/os-agp.h
/usr/src/nvidia-current-295.40/os-interface.c
/usr/src/nvidia-current-295.40/os-interface.h
/usr/src/nvidia-current-295.40/os-mtrr.c
/usr/src/nvidia-current-295.40/os-registry.c
/usr/src/nvidia-current-295.40/os-smp.c
/usr/src/nvidia-current-295.40/os-usermap.c
/usr/src/nvidia-current-295.40/patches
/usr/src/nvidia-current-295.40/rmil.h
/usr/src/nvidia-current-295.40/rmretval.h
/usr/src/nvidia-current-295.40/xapi-sdk.h
/usr/src/nvidia-current-295.40/patches/blacklist-vga-pmu-registers.patch
/usr/src/nvidia-current-295.40/patches/buildfix_kernel_3.0.patch
/var/cache/apt/archives/nvidia-current_295.40-0ubuntu1.1_i386.deb
/var/cache/apt/archives/nvidia-current_295.40-0ubuntu1_i386.deb
/var/cache/apt/archives/nvidia-settings_295.33-0ubuntu1_i386.deb
/var/cache/jockey/nvidia-current.noconf
/var/lib/dkms/nvidia-current
/var/lib/dkms/nvidia-current/295.40
/var/lib/dkms/nvidia-current/kernel-3.2.0-30-generic-i686
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic
/var/lib/dkms/nvidia-current/295.40/build
/var/lib/dkms/nvidia-current/295.40/source
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic/i686
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic/i686/log
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic/i686/module
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic/i686/log/make.log
/var/lib/dkms/nvidia-current/295.40/3.2.0-30-generic/i686/module/nvidia_current.ko
/var/lib/dkms/nvidia-current/295.40/build/.nv-acpi.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-chrdev.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-cray.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-gvi.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-i2c.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-mempool.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-mlock.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-mmap.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-p2p.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-pat.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-procfs.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-usermap.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-vm.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv-vtophys.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nv.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nvidia.mod.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.nvidia.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-agp.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-interface.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-mtrr.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-registry.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-smp.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/.os-usermap.o.cmd
/var/lib/dkms/nvidia-current/295.40/build/Makefile.kbuild
/var/lib/dkms/nvidia-current/295.40/build/Makefile.nvidia
/var/lib/dkms/nvidia-current/295.40/build/Module.symvers
/var/lib/dkms/nvidia-current/295.40/build/conftest.sh
/var/lib/dkms/nvidia-current/295.40/build/cpuopsys.h
/var/lib/dkms/nvidia-current/295.40/build/dkms.conf
/var/lib/dkms/nvidia-current/295.40/build/g_nvreadme.h
/var/lib/dkms/nvidia-current/295.40/build/gcc-version-check.c
/var/lib/dkms/nvidia-current/295.40/build/makefile
/var/lib/dkms/nvidia-current/295.40/build/modules.order
/var/lib/dkms/nvidia-current/295.40/build/nv-acpi.c
/var/lib/dkms/nvidia-current/295.40/build/nv-chrdev.c
/var/lib/dkms/nvidia-current/295.40/build/nv-cray.c
/var/lib/dkms/nvidia-current/295.40/build/nv-gvi.c
/var/lib/dkms/nvidia-current/295.40/build/nv-i2c.c
/var/lib/dkms/nvidia-current/295.40/build/nv-kernel.o
/var/lib/dkms/nvidia-current/295.40/build/nv-linux.h
/var/lib/dkms/nvidia-current/295.40/build/nv-memdbg.h
/var/lib/dkms/nvidia-current/295.40/build/nv-mempool.c
/var/lib/dkms/nvidia-current/295.40/build/nv-misc.h
/var/lib/dkms/nvidia-current/295.40/build/nv-mlock.c
/var/lib/dkms/nvidia-current/295.40/build/nv-mmap.c
/var/lib/dkms/nvidia-current/295.40/build/nv-p2p.c
/var/lib/dkms/nvidia-current/295.40/build/nv-p2p.h
/var/lib/dkms/nvidia-current/295.40/build/nv-pat.c
/var/lib/dkms/nvidia-current/295.40/build/nv-procfs.c
/var/lib/dkms/nvidia-current/295.40/build/nv-proto.h
/var/lib/dkms/nvidia-current/295.40/build/nv-reg.h
/var/lib/dkms/nvidia-current/295.40/build/nv-usermap.c
/var/lib/dkms/nvidia-current/295.40/build/nv-vm.c
/var/lib/dkms/nvidia-current/295.40/build/nv-vtophys.c
/var/lib/dkms/nvidia-current/295.40/build/nv.c
/var/lib/dkms/nvidia-current/295.40/build/nv.h
/var/lib/dkms/nvidia-current/295.40/build/nverror.h
/var/lib/dkms/nvidia-current/295.40/build/nvidia.ko
/var/lib/dkms/nvidia-current/295.40/build/nvidia.mod.c
/var/lib/dkms/nvidia-current/295.40/build/nvidia.o
/var/lib/dkms/nvidia-current/295.40/build/nvtypes.h
/var/lib/dkms/nvidia-current/295.40/build/os-agp.c
/var/lib/dkms/nvidia-current/295.40/build/os-agp.h
/var/lib/dkms/nvidia-current/295.40/build/os-interface.c
/var/lib/dkms/nvidia-current/295.40/build/os-interface.h
/var/lib/dkms/nvidia-current/295.40/build/os-mtrr.c
/var/lib/dkms/nvidia-current/295.40/build/os-registry.c
/var/lib/dkms/nvidia-current/295.40/build/os-smp.c
/var/lib/dkms/nvidia-current/295.40/build/os-usermap.c
/var/lib/dkms/nvidia-current/295.40/build/patches
/var/lib/dkms/nvidia-current/295.40/build/rmil.h
/var/lib/dkms/nvidia-current/295.40/build/rmretval.h
/var/lib/dkms/nvidia-current/295.40/build/xapi-sdk.h
/var/lib/dkms/nvidia-current/295.40/build/patches/blacklist-vga-pmu-registers.patch
/var/lib/dkms/nvidia-current/295.40/build/patches/buildfix_kernel_3.0.patch
/var/lib/dpkg/alternatives/nvidia_settings_conf
/var/lib/dpkg/info/nvidia-common.list
/var/lib/dpkg/info/nvidia-common.postrm
/var/lib/dpkg/info/nvidia-current.conffiles
/var/lib/dpkg/info/nvidia-current.list
/var/lib/dpkg/info/nvidia-current.md5sums
/var/lib/dpkg/info/nvidia-current.postinst
/var/lib/dpkg/info/nvidia-current.postrm
/var/lib/dpkg/info/nvidia-current.preinst
/var/lib/dpkg/info/nvidia-current.prerm
/var/lib/dpkg/info/nvidia-current.shlibs
/var/lib/dpkg/info/nvidia-settings.list
/var/lib/dpkg/info/nvidia-settings.md5sums
/var/lib/dpkg/info/nvidia-settings.postinst
/var/lib/dpkg/info/nvidia-settings.postrm
/var/lib/dpkg/info/nvidia-settings.prerm
/var/log/nvidia-installer.log

```

---

### Post by BicyclerBoy on 2012-09-13
A warm reboot bug is not so bad..my netbook would not warm boot (restart) for 3-4 months when 12.04 was released..
Does a file compare between your dmesg outputs (1 good & 1 bad) reveal any clues ?

---

### Post by HoneyGutClusters on 2012-09-13
I did find some more information involving this. This appears to be unique to 32 bit kernels and has existed as an issue since kernels after 2.6.32. It appears to stem from a PCI race condition involving certain nvidia products. (My personal thought would be "nvidia products with non-standard PCI ID's", but what do I know?)

Here's a bug report of a similar issues:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/661248](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/661248)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661394](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661394)

I'm going to try the pci=bios kernel switch suggested in the bug report and see what happens. I will report back.

Also, side note, the issue has cropped up again, can't get the module to insert itself no matter what I do...

EDIT: Replacing pci=use_crs with pci=bios seems to allow the nvidia kernel module to load again. I'll post back if any issues crop back up.

---

### Post by HoneyGutClusters on 2012-09-14
So far, the "pci=bios" kernel switch has been working as expected. With continued success over the next few days, I will mark this thread as solved.

---

### Post by HoneyGutClusters on 2012-09-17
The "pci=bios" kernel switch has been working consistently for me for about a week now.

---

### Post by BicyclerBoy on 2012-09-18
Well solved...

Chapter 8 of the driver readme (any version) has possible related info:
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/commonproblems.html)
this mentions use of "pci=biosirq"

I don't pretend to understand if this explains the symptoms you were getting..

---

