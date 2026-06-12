---
title: "WMP600N Trouble with rt2800pci and wpa_supplicant"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by jasonlyle88 on 2012-05-05
I am running ubuntu 12.04 server edition and can connect just fine to unprotected wireless networks, but I am having trouble setting up my network to connect to protected networks (WPA and WPA2). below is my system information and a recorded screen (script utility) showing that without WPA_SUPPLICANT, just using iwlist scan, I get a list of networks.  However, when using WPA_SUPPLICANT, no networks are even detected, let alone trying to connect to them.  Any help would be appreciated!

cat lsb-release; uname -a:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux jserver 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0e5f40ec-d579-4eb3-ac61-a2232c3de58d ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffc0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffc0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000420000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M5A88-V EVO, BIOS 1202    03/16/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x420000 max_arch_pfn = 0x400000000
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
[    0.000000] TOM2: 0000000430000000 aka 17152M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff80000 page 4k
[    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000420000000
[    0.000000]  0100000000 - 0400000000 page 1G
[    0.000000]  0400000000 - 0420000000 page 2M
[    0.000000] kernel direct mapping tables up to 420000000 @ cff7e000-cff80000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 00000000000fbc30 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cff80100 00054 (v01 031612 XSDT1525 20120316 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 031612 FACP1525 20120316 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cff80460 0F14D (v01  A1867 A1867001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cff98000 00040
[    0.000000] ACPI: APIC 00000000cff80390 0008C (v01 031612 APIC1525 20120316 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cff80420 0003C (v01 031612 OEMMCFG  20120316 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 031612 OEMB1525 20120316 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cff8f8b0 00038 (v01 031612 OEMHPET  20120316 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cff8f8f0 00B9C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000420000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000420000000
[    0.000000]   NODE_DATA [000000041fffb000 - 000000041fffffff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040fa00000-ffff88041f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00420000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000]     0: 0x00100000 -> 0x00420000
[    0.000000] On node 0 totalpages: 4128526
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
[    0.000000]   Normal zone: 51200 pages used for memmap
[    0.000000]   Normal zone: 3225600 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x14] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 20, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
[    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffc0000
[    0.000000] PM: Registered nosave memory: 00000000cffc0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88041fc00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4060937
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0e5f40ec-d579-4eb3-ac61-a2232c3de58d ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 16093900k/17301504k available (6566k kernel code, 787400k absent, 420204k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 132120576 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 4139.641 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 8279.28 BogoMIPS (lpj=16558564)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004028] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004041] Yama: becoming mindful.
[    0.008247] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.012370] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014105] Mount-cache hash table entries: 256
[    0.014210] Initializing cgroup subsys cpuacct
[    0.014216] Initializing cgroup subsys memory
[    0.014224] Initializing cgroup subsys devices
[    0.014227] Initializing cgroup subsys freezer
[    0.014229] Initializing cgroup subsys blkio
[    0.014235] Initializing cgroup subsys perf_event
[    0.014256] tseg: 0000000000
[    0.014265] CPU: Physical Processor ID: 0
[    0.014267] CPU: Processor Core ID: 0
[    0.014270] mce: CPU supports 7 MCE banks
[    0.015483] ACPI: Core revision 20110623
[    0.020008] ftrace: allocating 27049 entries in 107 pages
[    0.024374] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.065895] CPU0: AMD FX(tm)-4100 Quad-Core Processor             stepping 02
[    0.068003] Performance Events: AMD Family 15h PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      6
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000003f
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.156030] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156121]  #2
[    0.156123] smpboot cpu 2: start_ip = 99000
[    0.248027] NMI watchdog enabled, takes one hw-pmu counter.
[    0.248086]  #3
[    0.248088] smpboot cpu 3: start_ip = 99000
[    0.340032] NMI watchdog enabled, takes one hw-pmu counter.
[    0.340051] Brought up 4 CPUs
[    0.340054] Total of 4 processors activated (33117.03 BogoMIPS).
[    0.344162] devtmpfs: initialized
[    0.345293] EVM: security.selinux
[    0.345296] EVM: security.SMACK64
[    0.345298] EVM: security.capability
[    0.345385] PM: Registering ACPI NVS region at cff98000 (163840 bytes)
[    0.348105] print_constraints: dummy: 
[    0.348134] RTC time: 21:46:22, date: 05/04/12
[    0.348163] NET: Registered protocol family 16
[    0.348257] Extended Config Space enabled on 1 nodes
[    0.348272] ACPI: bus type pci registered
[    0.348173] Trying to unpack rootfs image as initramfs...
[    0.348328] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.348334] PCI: not using MMCONFIG
[    0.348337] PCI: Using configuration type 1 for base access
[    0.348340] PCI: Using configuration type 1 for extended access
[    0.349240] bio: create slab <bio-0> at 0
[    0.349240] ACPI: Added _OSI(Module Device)
[    0.349240] ACPI: Added _OSI(Processor Device)
[    0.349240] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.349240] ACPI: Added _OSI(Processor Aggregator Device)
[    0.349493] ACPI: EC: Look up EC in DSDT
[    0.352445] ACPI: Executed 3 blocks of module-level executable AML code
[    0.532570] ACPI: Interpreter enabled
[    0.532577] ACPI: (supports S0 S1 S3 S4 S5)
[    0.532602] ACPI: Using IOAPIC for interrupt routing
[    0.532625] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.534356] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.548613] Freeing initrd memory: 13840k freed
[    0.650773] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.650900] ACPI: No dock devices found.
[    0.650903] HEST: Table not found.
[    0.650907] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.651093] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.651274] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.651278] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.651282] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.651287] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.651291] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.651296] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.651310] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.651357] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.651395] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
[    0.651426] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.651429] pci 0000:00:09.0: PME# disabled
[    0.651442] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.651472] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.651474] pci 0000:00:0a.0: PME# disabled
[    0.651497] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.651514] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
[    0.651522] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
[    0.651531] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
[    0.651539] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
[    0.651548] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
[    0.651556] pci 0000:00:11.0: reg 24: [mem 0xfe6ffc00-0xfe6fffff]
[    0.651574] pci 0000:00:11.0: set SATA to AHCI mode
[    0.651619] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.651631] pci 0000:00:12.0: reg 10: [mem 0xfe6fe000-0xfe6fefff]
[    0.651694] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.651711] pci 0000:00:12.2: reg 10: [mem 0xfe6ff800-0xfe6ff8ff]
[    0.651784] pci 0000:00:12.2: supports D1 D2
[    0.651785] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.651789] pci 0000:00:12.2: PME# disabled
[    0.651807] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.651819] pci 0000:00:13.0: reg 10: [mem 0xfe6fd000-0xfe6fdfff]
[    0.651882] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.651899] pci 0000:00:13.2: reg 10: [mem 0xfe6ff400-0xfe6ff4ff]
[    0.651972] pci 0000:00:13.2: supports D1 D2
[    0.651973] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.651977] pci 0000:00:13.2: PME# disabled
[    0.651996] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.652079] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.652092] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.652101] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.652109] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.652118] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.652126] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.652163] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.652181] pci 0000:00:14.2: reg 10: [mem 0xfe6f8000-0xfe6fbfff 64bit]
[    0.652240] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.652243] pci 0000:00:14.2: PME# disabled
[    0.652254] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.652321] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.652358] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.652370] pci 0000:00:14.5: reg 10: [mem 0xfe6fc000-0xfe6fcfff]
[    0.652434] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.652501] pci 0000:00:15.0: supports D1 D2
[    0.652524] pci 0000:00:15.1: [1002:43a1] type 1 class 0x000604
[    0.652591] pci 0000:00:15.1: supports D1 D2
[    0.652617] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.652629] pci 0000:00:16.0: reg 10: [mem 0xfe6f7000-0xfe6f7fff]
[    0.652692] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.652708] pci 0000:00:16.2: reg 10: [mem 0xfe6ff000-0xfe6ff0ff]
[    0.652781] pci 0000:00:16.2: supports D1 D2
[    0.652783] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.652786] pci 0000:00:16.2: PME# disabled
[    0.652804] pci 0000:00:18.0: [1022:1600] type 0 class 0x000600
[    0.652820] pci 0000:00:18.1: [1022:1601] type 0 class 0x000600
[    0.652833] pci 0000:00:18.2: [1022:1602] type 0 class 0x000600
[    0.652846] pci 0000:00:18.3: [1022:1603] type 0 class 0x000600
[    0.652862] pci 0000:00:18.4: [1022:1604] type 0 class 0x000600
[    0.652875] pci 0000:00:18.5: [1022:1605] type 0 class 0x000600
[    0.652917] pci 0000:01:05.0: [1002:9715] type 0 class 0x000300
[    0.652924] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.652928] pci 0000:01:05.0: reg 14: [io  0xb000-0xb0ff]
[    0.652932] pci 0000:01:05.0: reg 18: [mem 0xfe8f0000-0xfe8fffff]
[    0.652941] pci 0000:01:05.0: reg 24: [mem 0xfe700000-0xfe7fffff]
[    0.652957] pci 0000:01:05.0: supports D1 D2
[    0.652966] pci 0000:01:05.1: [1002:970f] type 0 class 0x000403
[    0.652973] pci 0000:01:05.1: reg 10: [mem 0xfe8e8000-0xfe8ebfff]
[    0.653001] pci 0000:01:05.1: supports D1 D2
[    0.653034] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.653039] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.653041] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.653045] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.653088] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
[    0.653116] pci 0000:02:00.0: reg 10: [mem 0xfe9ff800-0xfe9fffff 64bit]
[    0.653130] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
[    0.653251] pci 0000:02:00.0: supports D2
[    0.653252] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.653258] pci 0000:02:00.0: PME# disabled
[    0.653305] pci 0000:02:00.1: [1106:0415] type 0 class 0x000101
[    0.653325] pci 0000:02:00.1: reg 10: [io  0xcc00-0xcc07]
[    0.653340] pci 0000:02:00.1: reg 14: [io  0xc480-0xc483]
[    0.653354] pci 0000:02:00.1: reg 18: [io  0xc400-0xc407]
[    0.653369] pci 0000:02:00.1: reg 1c: [io  0xc080-0xc083]
[    0.653383] pci 0000:02:00.1: reg 20: [io  0xc000-0xc00f]
[    0.653411] pci 0000:02:00.1: reg 30: [mem 0xfe9e0000-0xfe9effff pref]
[    0.653482] pci 0000:02:00.1: supports D2
[    0.653483] pci 0000:02:00.1: PME# supported from D2 D3hot D3cold
[    0.653489] pci 0000:02:00.1: PME# disabled
[    0.660064] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.660069] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    0.660072] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.660112] pci 0000:03:00.0: [1b21:1042] type 0 class 0x000c03
[    0.660129] pci 0000:03:00.0: reg 10: [mem 0xfeaf8000-0xfeafffff 64bit]
[    0.660211] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.660215] pci 0000:03:00.0: PME# disabled
[    0.668051] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.668058] pci 0000:00:0a.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.668098] pci 0000:04:06.0: [1095:3124] type 0 class 0x000104
[    0.668128] pci 0000:04:06.0: reg 10: [mem 0xfebfbc00-0xfebfbc7f 64bit]
[    0.668145] pci 0000:04:06.0: reg 18: [mem 0xfebf0000-0xfebf7fff 64bit]
[    0.668157] pci 0000:04:06.0: reg 20: [io  0xdc00-0xdc0f]
[    0.668179] pci 0000:04:06.0: reg 30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.668234] pci 0000:04:06.0: supports D1 D2
[    0.668258] pci 0000:04:07.0: [1814:0601] type 0 class 0x000280
[    0.668277] pci 0000:04:07.0: reg 10: [mem 0xfebe0000-0xfebeffff]
[    0.668405] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.668411] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.668415] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.668419] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.668421] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.668422] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.668424] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.668426] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.668428] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.668472] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.668545] pci 0000:06:00.0: [10ec:8168] type 0 class 0x000200
[    0.668562] pci 0000:06:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.668590] pci 0000:06:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.668608] pci 0000:06:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    0.668685] pci 0000:06:00.0: supports D1 D2
[    0.668686] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668691] pci 0000:06:00.0: PME# disabled
[    0.676056] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.676064] pci 0000:00:15.1:   bridge window [io  0xe000-0xefff]
[    0.676071] pci 0000:00:15.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.676093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.676220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.676256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.676286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.676317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.676388] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE21._PRT]
[    0.676512]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.676665]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.681573] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[    0.681634] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.681695] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.681755] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *9 10 11 14 15)
[    0.681802] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.681840] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 14 15)
[    0.681877] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 14 15)
[    0.681914] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.681989] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.681989] vgaarb: loaded
[    0.681989] vgaarb: bridge control possible 0000:01:05.0
[    0.681989] i2c-core: driver [aat2870] using legacy suspend method
[    0.681989] i2c-core: driver [aat2870] using legacy resume method
[    0.681989] SCSI subsystem initialized
[    0.682075] libata version 3.00 loaded.
[    0.682075] usbcore: registered new interface driver usbfs
[    0.682075] usbcore: registered new interface driver hub
[    0.682075] usbcore: registered new device driver usb
[    0.682075] PCI: Using ACPI for IRQ routing
[    0.689868] PCI: pci_cache_line_size set to 64 bytes
[    0.689957] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.689959] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
[    0.690030] NetLabel: Initializing
[    0.690033] NetLabel:  domain hash size = 128
[    0.690036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.690048] NetLabel:  unlabeled traffic allowed by default
[    0.690065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.690065] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.692074] Switching to clocksource hpet
[    0.697582] AppArmor: AppArmor Filesystem Enabled
[    0.697599] pnp: PnP ACPI init
[    0.697610] ACPI: bus type pnp registered
[    0.697709] pnp 00:00: [bus 00-ff]
[    0.697711] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.697713] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.697714] pnp 00:00: [io  0x0d00-0xffff window]
[    0.697716] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.697718] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.697719] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.697721] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.697755] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.697825] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.697827] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.697862] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.698285] pnp 00:02: [dma 4]
[    0.698287] pnp 00:02: [io  0x0000-0x000f]
[    0.698288] pnp 00:02: [io  0x0081-0x0083]
[    0.698290] pnp 00:02: [io  0x0087]
[    0.698291] pnp 00:02: [io  0x0089-0x008b]
[    0.698293] pnp 00:02: [io  0x008f]
[    0.698294] pnp 00:02: [io  0x00c0-0x00df]
[    0.698321] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.698329] pnp 00:03: [io  0x0070-0x0071]
[    0.698336] pnp 00:03: [irq 8]
[    0.698363] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.698374] pnp 00:04: [io  0x0061]
[    0.698397] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.698403] pnp 00:05: [io  0x00f0-0x00ff]
[    0.698407] pnp 00:05: [irq 13]
[    0.698431] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.698469] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.698495] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.699018] pnp 00:07: [io  0x03f8-0x03ff]
[    0.699022] pnp 00:07: [irq 4]
[    0.699024] pnp 00:07: [dma 0 disabled]
[    0.699097] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.699170] pnp 00:08: [io  0x0060]
[    0.699172] pnp 00:08: [io  0x0064]
[    0.699173] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.699175] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.699218] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.699223] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.699227] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.699385] pnp 00:09: [io  0x0010-0x001f]
[    0.699387] pnp 00:09: [io  0x0022-0x003f]
[    0.699389] pnp 00:09: [io  0x0062-0x0063]
[    0.699390] pnp 00:09: [io  0x0065-0x006f]
[    0.699391] pnp 00:09: [io  0x0072-0x007f]
[    0.699393] pnp 00:09: [io  0x0080]
[    0.699394] pnp 00:09: [io  0x0084-0x0086]
[    0.699395] pnp 00:09: [io  0x0088]
[    0.699397] pnp 00:09: [io  0x008c-0x008e]
[    0.699398] pnp 00:09: [io  0x0090-0x009f]
[    0.699399] pnp 00:09: [io  0x00a2-0x00bf]
[    0.699401] pnp 00:09: [io  0x00b1]
[    0.699402] pnp 00:09: [io  0x00e0-0x00ef]
[    0.699403] pnp 00:09: [io  0x04d0-0x04d1]
[    0.699405] pnp 00:09: [io  0x040b]
[    0.699406] pnp 00:09: [io  0x04d6]
[    0.699407] pnp 00:09: [io  0x0c00-0x0c01]
[    0.699409] pnp 00:09: [io  0x0c14]
[    0.699410] pnp 00:09: [io  0x0c50-0x0c51]
[    0.699411] pnp 00:09: [io  0x0c52]
[    0.699413] pnp 00:09: [io  0x0c6c]
[    0.699414] pnp 00:09: [io  0x0c6f]
[    0.699415] pnp 00:09: [io  0x0cd0-0x0cd1]
[    0.699417] pnp 00:09: [io  0x0cd2-0x0cd3]
[    0.699418] pnp 00:09: [io  0x0cd4-0x0cd5]
[    0.699420] pnp 00:09: [io  0x0cd6-0x0cd7]
[    0.699421] pnp 00:09: [io  0x0cd8-0x0cdf]
[    0.699422] pnp 00:09: [io  0x0b00-0x0b3f]
[    0.699424] pnp 00:09: [io  0x0800-0x089f]
[    0.699425] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.699427] pnp 00:09: [io  0x0b00-0x0b1f]
[    0.699428] pnp 00:09: [io  0x0b20-0x0b3f]
[    0.699430] pnp 00:09: [io  0x0900-0x090f]
[    0.699431] pnp 00:09: [io  0x0910-0x091f]
[    0.699432] pnp 00:09: [io  0xfe00-0xfefe]
[    0.699434] pnp 00:09: [io  0x0060]
[    0.699435] pnp 00:09: [io  0x0064]
[    0.699438] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.699440] pnp 00:09: [mem 0xffb80000-0xffbfffff]
[    0.699441] pnp 00:09: [mem 0xfec10000-0xfec1001f]
[    0.699443] pnp 00:09: [mem 0xfed80000-0xfed80fff]
[    0.699444] pnp 00:09: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.699532] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.699536] system 00:09: [io  0x040b] has been reserved
[    0.699540] system 00:09: [io  0x04d6] has been reserved
[    0.699544] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.699547] system 00:09: [io  0x0c14] has been reserved
[    0.699551] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.699555] system 00:09: [io  0x0c52] has been reserved
[    0.699559] system 00:09: [io  0x0c6c] has been reserved
[    0.699562] system 00:09: [io  0x0c6f] has been reserved
[    0.699566] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.699570] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.699574] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.699577] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.699581] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.699585] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.699589] system 00:09: [io  0x0800-0x089f] has been reserved
[    0.699593] system 00:09: [io  0x0b00-0x0b1f] has been reserved
[    0.699597] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.699601] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.699605] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.699609] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.699615] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.699619] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.699623] system 00:09: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.699628] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.699802] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.699803] pnp 00:0a: [io  0x0230-0x023f]
[    0.699805] pnp 00:0a: [io  0x0290-0x029f]
[    0.699806] pnp 00:0a: [io  0x0300-0x030f]
[    0.699808] pnp 00:0a: [io  0x0a30-0x0a3f]
[    0.699851] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.699855] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.699859] system 00:0a: [io  0x0300-0x030f] has been reserved
[    0.699863] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.699867] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.699896] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.699938] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.699943] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.700050] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.700052] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.700053] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.700055] pnp 00:0c: [mem 0x00100000-0xcfffffff]
[    0.700056] pnp 00:0c: [mem 0xfec00000-0xffffffff]
[    0.700100] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.700104] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.700109] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.700113] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.700117] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.700122] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.700204] pnp: PnP ACPI: found 13 devices
[    0.700207] ACPI: ACPI bus type pnp unregistered
[    0.706892] PCI: max bus depth: 1 pci_try_num: 2
[    0.706919] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.706923] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.706928] pci 0000:00:01.0:   bridge window [mem 0xfe700000-0xfe8fffff]
[    0.706933] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.706939] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.706943] pci 0000:00:09.0:   bridge window [io  0xc000-0xcfff]
[    0.706947] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.706953] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.706958] pci 0000:00:0a.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.706964] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.706968] pci 0000:00:14.4:   bridge window [io  0xd000-0xdfff]
[    0.706974] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.706984] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.706994] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.706998] pci 0000:00:15.1:   bridge window [io  0xe000-0xefff]
[    0.707006] pci 0000:00:15.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.707024] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.707029] pci 0000:00:09.0: setting latency timer to 64
[    0.707035] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.707040] pci 0000:00:0a.0: setting latency timer to 64
[    0.707053] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.707059] pci 0000:00:15.0: setting latency timer to 64
[    0.707064] pci 0000:00:15.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.707069] pci 0000:00:15.1: setting latency timer to 64
[    0.707073] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.707074] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.707076] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.707078] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.707079] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.707081] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.707083] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.707084] pci_bus 0000:01: resource 1 [mem 0xfe700000-0xfe8fffff]
[    0.707086] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.707088] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.707090] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.707092] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.707094] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.707095] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.707097] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.707099] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.707100] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.707102] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.707104] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.707105] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.707107] pci_bus 0000:06: resource 0 [io  0xe000-0xefff]
[    0.707109] pci_bus 0000:06: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.707132] NET: Registered protocol family 2
[    0.707527] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.709124] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.710963] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.711182] TCP: Hash tables configured (established 524288 bind 65536)
[    0.711186] TCP reno registered
[    0.711212] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.711296] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.711419] NET: Registered protocol family 1
[    0.711429] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.711447] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.552028] pci 0000:00:12.0: PCI INT A disabled
[    1.552038] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.552068] pci 0000:00:12.2: PCI INT B disabled
[    1.552075] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.632031] pci 0000:00:13.0: PCI INT A disabled
[    1.632041] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.632070] pci 0000:00:13.2: PCI INT B disabled
[    1.632086] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.712024] pci 0000:00:14.5: PCI INT C disabled
[    1.712036] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.792032] pci 0000:00:16.0: PCI INT A disabled
[    1.792042] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.792071] pci 0000:00:16.2: PCI INT B disabled
[    1.792087] pci 0000:01:05.0: Boot video device
[    1.792100] pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.792130] pci 0000:03:00.0: PCI INT A disabled
[    1.792141] PCI: CLS 64 bytes, default 64
[    1.792695] PCI-DMA: Disabling AGP.
[    1.792777] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.792781] PCI-DMA: using GART IOMMU.
[    1.792785] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.796610] perf: AMD IBS detected (0x000000ff)
[    1.796769] audit: initializing netlink socket (disabled)
[    1.796786] type=2000 audit(1336167982.792:1): initialized
[    1.840245] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.897634] VFS: Disk quotas dquot_6.5.2
[    1.897682] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.898098] fuse init (API version 7.17)
[    1.898176] msgmni has been set to 31589
[    1.898560] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.898593] io scheduler noop registered
[    1.898597] io scheduler deadline registered
[    1.898622] io scheduler cfq registered (default)
[    1.898721] pcieport 0000:00:09.0: setting latency timer to 64
[    1.898746] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    1.898790] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.898809] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    1.898854] pcieport 0000:00:15.0: setting latency timer to 64
[    1.898894] pcieport 0000:00:15.0: irq 42 for MSI/MSI-X
[    1.898948] pcieport 0000:00:15.1: setting latency timer to 64
[    1.898989] pcieport 0000:00:15.1: irq 43 for MSI/MSI-X
[    1.899059] pcieport 0000:00:09.0: Signaling PME through PCIe PME interrupt
[    1.899064] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.899068] pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
[    1.899072] pcie_pme 0000:00:09.0:pcie01: service driver pcie_pme loaded
[    1.899082] pcieport 0000:00:0a.0: Signaling PME through PCIe PME interrupt
[    1.899086] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.899090] pcie_pme 0000:00:0a.0:pcie01: service driver pcie_pme loaded
[    1.899104] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
[    1.899109] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
[    1.899124] pcieport 0000:00:15.1: Signaling PME through PCIe PME interrupt
[    1.899128] pci 0000:06:00.0: Signaling PME through PCIe PME interrupt
[    1.899133] pcie_pme 0000:00:15.1:pcie01: service driver pcie_pme loaded
[    1.899146] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.899166] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.899263] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.899270] ACPI: Power Button [PWRB]
[    1.899303] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.899308] ACPI: Power Button [PWRF]
[    1.899625] ACPI: acpi_idle registered with cpuidle
[    2.100922] ERST: Table is not found!
[    2.100926] GHES: HEST is not enabled!
[    2.100997] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.121409] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.200586] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.232224] Linux agpgart interface v0.103
[    2.233368] brd: module loaded
[    2.233974] loop: module loaded
[    2.234072] ahci 0000:00:11.0: version 3.0
[    2.234084] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.234177] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    2.234183] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.234599] scsi0 : ahci
[    2.234672] scsi1 : ahci
[    2.234736] scsi2 : ahci
[    2.234802] scsi3 : ahci
[    2.234890] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 19
[    2.234896] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 19
[    2.234901] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 19
[    2.234906] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 19
[    2.234982] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.235007] pata_acpi 0000:00:14.1: setting latency timer to 64
[    2.235031] pata_acpi 0000:02:00.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.235052] pata_acpi 0000:02:00.1: setting latency timer to 64
[    2.235063] pata_acpi 0000:02:00.1: PCI INT A disabled
[    2.235288] Fixed MDIO Bus: probed
[    2.235304] tun: Universal TUN/TAP device driver, 1.6
[    2.235307] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.235349] PPP generic driver version 2.4.2
[    2.235428] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.235441] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.235454] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.235494] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.235504] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.235518] QUIRK: Enable AMD PLL fix
[    2.235527] ehci_hcd 0000:00:12.2: debug port 1
[    2.235545] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe6ff800
[    2.244029] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.244128] hub 1-0:1.0: USB hub found
[    2.244133] hub 1-0:1.0: 5 ports detected
[    2.244194] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.244210] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.244244] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.244253] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.244272] ehci_hcd 0000:00:13.2: debug port 1
[    2.244285] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe6ff400
[    2.256028] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.256125] hub 2-0:1.0: USB hub found
[    2.256129] hub 2-0:1.0: 5 ports detected
[    2.256189] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.256203] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    2.256238] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    2.256247] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.256265] ehci_hcd 0000:00:16.2: debug port 1
[    2.256277] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe6ff000
[    2.268029] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    2.268117] hub 3-0:1.0: USB hub found
[    2.268121] hub 3-0:1.0: 4 ports detected
[    2.268179] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.268191] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.268205] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.268241] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    2.268263] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe6fe000
[    2.328097] hub 4-0:1.0: USB hub found
[    2.328106] hub 4-0:1.0: 5 ports detected
[    2.328161] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.328176] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.328215] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.328229] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe6fd000
[    2.388114] hub 5-0:1.0: USB hub found
[    2.388121] hub 5-0:1.0: 5 ports detected
[    2.388171] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.388186] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.388231] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    2.388245] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe6fc000
[    2.448113] hub 6-0:1.0: USB hub found
[    2.448121] hub 6-0:1.0: 2 ports detected
[    2.448172] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.448188] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    2.448228] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    2.448245] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe6f7000
[    2.508136] hub 7-0:1.0: USB hub found
[    2.508143] hub 7-0:1.0: 4 ports detected
[    2.508194] uhci_hcd: USB Universal Host Controller Interface driver
[    2.508222] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.508240] xhci_hcd 0000:03:00.0: setting latency timer to 64
[    2.508243] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    2.508283] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    2.517892] xhci_hcd 0000:03:00.0: irq 18, io mem 0xfeaf8000
[    2.517927] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
[    2.517931] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[    2.517934] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    2.517937] xhci_hcd 0000:03:00.0: irq 47 for MSI/MSI-X
[    2.517940] xhci_hcd 0000:03:00.0: irq 48 for MSI/MSI-X
[    2.518059] xHCI xhci_add_endpoint called for root hub
[    2.518061] xHCI xhci_check_bandwidth called for root hub
[    2.518079] hub 8-0:1.0: USB hub found
[    2.518086] hub 8-0:1.0: 2 ports detected
[    2.518129] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    2.518165] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
[    2.518237] xHCI xhci_add_endpoint called for root hub
[    2.518238] xHCI xhci_check_bandwidth called for root hub
[    2.518256] hub 9-0:1.0: USB hub found
[    2.518262] hub 9-0:1.0: 2 ports detected
[    2.552054] ata4: SATA link down (SStatus 0 SControl 300)
[    2.552102] ata2: SATA link down (SStatus 0 SControl 300)
[    2.556083] usbcore: registered new interface driver libusual
[    2.556113] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.556452] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.556458] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.556566] mousedev: PS/2 mouse device common for all mice
[    2.556680] rtc_cmos 00:03: RTC can wake from S4
[    2.556764] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.556788] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.556845] device-mapper: uevent: version 1.0.3
[    2.556899] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.556963] cpuidle: using governor ladder
[    2.557068] cpuidle: using governor menu
[    2.557071] EFI Variables Facility v0.08 2004-May-17
[    2.557234] TCP cubic registered
[    2.557307] NET: Registered protocol family 10
[    2.557660] NET: Registered protocol family 17
[    2.557671] Registering the dns_resolver key type
[    2.557792] PM: Hibernation image not present or could not be loaded.
[    2.557799] registered taskstats version 1
[    2.590734]   Magic number: 12:756:802
[    2.590820] rtc_cmos 00:03: setting system clock to 2012-05-04 21:46:24 UTC (1336167984)
[    2.590845] powernow-k8: Found 1 AMD FX(tm)-4100 Quad-Core Processor             (4 cpu cores) (version 2.20.00)
[    2.590873] powernow-k8: Core Performance Boosting: on.
[    2.590923] powernow-k8:    0 : pstate 0 (3600 MHz)
[    2.590926] powernow-k8:    1 : pstate 1 (3300 MHz)
[    2.590929] powernow-k8:    2 : pstate 2 (2500 MHz)
[    2.590932] powernow-k8:    3 : pstate 3 (1700 MHz)
[    2.590935] powernow-k8:    4 : pstate 4 (1400 MHz)
[    2.591483] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.591487] EDD information not available.
[    2.724048] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.724075] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.724761] ata3.00: ATA-8: ST1500DL003-9VT16L, CC32, max UDMA/133
[    2.724766] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.724992] ata1.00: ATA-8: WDC WD2500AAKX-001CA0, 15.01H15, max UDMA/133
[    2.724997] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.725533] ata3.00: configured for UDMA/133
[    2.726959] ata1.00: configured for UDMA/133
[    2.727088] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKX-0 15.0 PQ: 0 ANSI: 5
[    2.727220] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.727236] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.727322] sd 0:0:0:0: [sda] Write Protect is off
[    2.727327] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.727366] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.727383] scsi 2:0:0:0: Direct-Access     ATA      ST1500DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    2.727492] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.727544] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.727560] sd 2:0:0:0: [sdb] Write Protect is off
[    2.727565] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.727584] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.755553]  sdb: unknown partition table
[    2.755782] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.769304]  sda: sda1 sda2 < sda5 >
[    2.769678] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.771644] Freeing unused kernel memory: 920k freed
[    2.771817] Write protecting the kernel read-only data: 12288k
[    2.777535] Freeing unused kernel memory: 1608k freed
[    2.781966] Freeing unused kernel memory: 1196k freed
[    2.794512] udevd[109]: starting version 175
[    2.796024] Refined TSC clocksource calibration: 4139.741 MHz.
[    2.796034] Switching to clocksource tsc
[    2.813494] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.813508] firewire_ohci 0000:02:00.0: setting latency timer to 64
[    2.825975] scsi4 : pata_atiixp
[    2.826285] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.826310] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.826351] r8169 0000:06:00.0: setting latency timer to 64
[    2.826425] r8169 0000:06:00.0: irq 49 for MSI/MSI-X
[    2.826862] scsi5 : pata_atiixp
[    2.826870] r8169 0000:06:00.0: eth0: RTL8168evl/8111evl at 0xffffc900125de000, 54:04:a6:f2:30:01, XID 0c900800 IRQ 49
[    2.826880] r8169 0000:06:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.827006] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.827013] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.830481] sata_sil24 0000:04:06.0: version 1.1
[    2.830496] sata_sil24 0000:04:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.832017] usb 5-1: new full-speed USB device number 2 using ohci_hcd
[    2.832664] scsi6 : sata_sil24
[    2.833817] scsi7 : sata_sil24
[    2.833932] scsi8 : sata_sil24
[    2.834000] scsi9 : sata_sil24
[    2.834046] ata7: SATA max UDMA/100 host m128@0xfebfbc00 port 0xfebf0000 irq 21
[    2.834054] ata8: SATA max UDMA/100 host m128@0xfebfbc00 port 0xfebf2000 irq 21
[    2.834061] ata9: SATA max UDMA/100 host m128@0xfebfbc00 port 0xfebf4000 irq 21
[    2.834068] ata10: SATA max UDMA/100 host m128@0xfebfbc00 port 0xfebf6000 irq 21
[    2.876063] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    2.876109] pata_via 0000:02:00.1: version 0.3.4
[    2.876123] pata_via 0000:02:00.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.876173] pata_via 0000:02:00.1: setting latency timer to 64
[    2.876471] scsi10 : pata_via
[    2.876546] scsi11 : pata_via
[    2.876697] ata11: PATA max UDMA/133 cmd 0xcc00 ctl 0xc480 bmdma 0xc000 irq 17
[    2.876704] ata12: PATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 17
[    3.002350] ata5.01: ATAPI: HL-DT-ST BDDVDRW UH12LS28, 1.00, max UDMA/133
[    3.002357] ata5.01: limited to UDMA/33 due to 40-wire cable
[    3.012784] usbcore: registered new interface driver usbhid
[    3.012790] usbhid: USB HID core driver
[    3.032448] ata5.01: configured for UDMA/33
[    3.041182] scsi 4:0:1:0: CD-ROM            HL-DT-ST BDDVDRW UH12LS28 1.00 PQ: 0 ANSI: 5
[    3.050186] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.050192] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.050303] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    3.050427] sr 4:0:1:0: Attached scsi generic sg2 type 5
[    3.053491] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.376077] firewire_core: created device fw0: GUID 001e8c0000346cbc, S400
[    4.912032] ata7: SATA link down (SStatus 0 SControl 0)
[    6.992034] ata8: SATA link down (SStatus 0 SControl 0)
[    9.072032] ata9: SATA link down (SStatus 0 SControl 0)
[   11.152030] ata10: SATA link down (SStatus 0 SControl 0)
[   15.313915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.341286] udevd[361]: starting version 175
[   15.360986] lp: driver loaded but no devices found
[   15.367254] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[   15.367259] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.367507] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   15.367570] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   15.370295] wmi: Mapper loaded
[   15.380961] Adding 8124412k swap on /dev/sda5.  Priority:-1 extents:1 across:8124412k 
[   15.388975] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.397691] ATK0110 ATK0110:00: EC enabled
[   15.405783] [drm] Initialized drm 1.1.0 20060810
[   15.411715] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.413934] [drm] radeon defaulting to kernel modesetting.
[   15.413936] [drm] radeon kernel modesetting enabled.
[   15.414001] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.414005] radeon 0000:01:05.0: setting latency timer to 64
[   15.414137] [drm] initializing kernel modesetting (RS880 0x1002:0x9715 0x1043:0x843E).
[   15.414158] [drm] register mmio base: 0xFE8F0000
[   15.414159] [drm] register mmio size: 65536
[   15.414859] ATOM BIOS: 113
[   15.414874] radeon 0000:01:05.0: VRAM: 368M 0x00000000C0000000 - 0x00000000D6FFFFFF (368M used)
[   15.414877] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[   15.420777] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-1/input2
[   15.420794] [drm] Detected VRAM RAM=368M, BAR=256M
[   15.420796] [drm] RAM width 32bits DDR
[   15.420949] [TTM] Zone  kernel: Available graphics memory: 8088708 kiB.
[   15.420952] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   15.420954] [TTM] Initializing pool allocator.
[   15.420974] [drm] radeon: 368M of VRAM memory ready
[   15.420976] [drm] radeon: 512M of GTT memory ready.
[   15.420989] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.420990] [drm] Driver supports precise vblank timestamp query.
[   15.421006] [drm] radeon: irq initialized.
[   15.421011] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.421749] [drm] Loading RS780 Microcode
[   15.426400] input: Logitech Unifying Device. Wireless PID:200a as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.2/0003:046D:C52B.0003/input/input2
[   15.426477] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:200a] on usb-0000:00:13.0-1:1
[   15.428751] cfg80211: Calling CRDA to update world regulatory domain
[   15.442863] MCE: In-kernel MCE decoding enabled.
[   15.444842] EDAC MC: Ver: 2.1.0
[   15.446936] rt2800pci 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.447078] AMD64 EDAC driver v3.4.0
[   15.456786] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.456790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456795] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.456797] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456800] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.456802] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456804] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.456807] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456809] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.456811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456814] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.456816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456818] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.456821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456823] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.456825] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456827] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.456830] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456832] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.456834] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456836] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.456839] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456840] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.456843] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.456845] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.456848] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.456850] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.456852] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.456854] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   15.456857] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456859] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   15.456861] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456863] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   15.456866] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456868] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   15.456871] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456873] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   15.456875] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456877] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   15.456880] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456881] cfg80211: Disabling freq 5260 MHz
[   15.456883] cfg80211: Disabling freq 5270 MHz
[   15.456884] cfg80211: Disabling freq 5280 MHz
[   15.456886] cfg80211: Disabling freq 5300 MHz
[   15.456887] cfg80211: Disabling freq 5310 MHz
[   15.456888] cfg80211: Disabling freq 5320 MHz
[   15.456890] cfg80211: Disabling freq 5500 MHz
[   15.456891] cfg80211: Disabling freq 5510 MHz
[   15.456892] cfg80211: Disabling freq 5520 MHz
[   15.456894] cfg80211: Disabling freq 5540 MHz
[   15.456895] cfg80211: Disabling freq 5550 MHz
[   15.456896] cfg80211: Disabling freq 5560 MHz
[   15.456898] cfg80211: Disabling freq 5580 MHz
[   15.456899] cfg80211: Disabling freq 5590 MHz
[   15.456900] cfg80211: Disabling freq 5600 MHz
[   15.456902] cfg80211: Disabling freq 5620 MHz
[   15.456903] cfg80211: Disabling freq 5630 MHz
[   15.456904] cfg80211: Disabling freq 5640 MHz
[   15.456906] cfg80211: Disabling freq 5660 MHz
[   15.456907] cfg80211: Disabling freq 5670 MHz
[   15.456909] cfg80211: Disabling freq 5680 MHz
[   15.456910] cfg80211: Disabling freq 5700 MHz
[   15.456912] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   15.456914] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456916] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   15.456919] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456921] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   15.456924] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456926] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   15.456928] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456930] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   15.456933] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456935] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   15.456937] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456939] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   15.456942] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.456943] cfg80211: Disabling freq 5835 MHz
[   15.456945] cfg80211: Disabling freq 5845 MHz
[   15.456946] cfg80211: Disabling freq 5855 MHz
[   15.456948] cfg80211: Disabling freq 5865 MHz
[   15.456949] cfg80211: Disabling freq 4920 MHz
[   15.456950] cfg80211: Disabling freq 4940 MHz
[   15.456952] cfg80211: Disabling freq 4960 MHz
[   15.456953] cfg80211: Disabling freq 4980 MHz
[   15.456954] cfg80211: Disabling freq 6040 MHz
[   15.456956] cfg80211: Disabling freq 6060 MHz
[   15.456957] cfg80211: Disabling freq 6080 MHz
[   15.474408] type=1400 audit(1336167997.377:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=486 comm="apparmor_parser"
[   15.474482] type=1400 audit(1336167997.377:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=520 comm="apparmor_parser"
[   15.474839] type=1400 audit(1336167997.377:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=486 comm="apparmor_parser"
[   15.474901] type=1400 audit(1336167997.377:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=520 comm="apparmor_parser"
[   15.475075] type=1400 audit(1336167997.377:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=486 comm="apparmor_parser"
[   15.475143] type=1400 audit(1336167997.377:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=520 comm="apparmor_parser"
[   15.482287] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.484843] Registered led device: rt2800pci-phy0::radio
[   15.484885] Registered led device: rt2800pci-phy0::assoc
[   15.484921] Registered led device: rt2800pci-phy0::quality
[   15.489414] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
[   15.489531] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[   15.489625] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   15.489718] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   15.490259] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   15.490366] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   15.491521] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   15.491957] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   15.498336] EDAC amd64: DRAM ECC disabled.
[   15.498343] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.498345]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.498346]  (Note that use of the override may cause unknown side effects.)
[   15.527602] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.527606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527609] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.527612] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527614] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.527616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527619] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.527621] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527623] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.527626] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527628] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.527631] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527633] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.527635] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527637] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.527640] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527642] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.527644] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527646] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.527649] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527651] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.527653] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527656] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.527658] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.527660] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.527663] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.527665] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.527667] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.527669] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   15.527672] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527674] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   15.527676] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527678] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   15.527681] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527683] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   15.527685] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527687] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   15.527690] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527692] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   15.527694] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527696] cfg80211: Disabling freq 5260 MHz
[   15.527698] cfg80211: Disabling freq 5270 MHz
[   15.527699] cfg80211: Disabling freq 5280 MHz
[   15.527701] cfg80211: Disabling freq 5300 MHz
[   15.527702] cfg80211: Disabling freq 5310 MHz
[   15.527704] cfg80211: Disabling freq 5320 MHz
[   15.527705] cfg80211: Disabling freq 5500 MHz
[   15.527706] cfg80211: Disabling freq 5510 MHz
[   15.527708] cfg80211: Disabling freq 5520 MHz
[   15.527709] cfg80211: Disabling freq 5540 MHz
[   15.527710] cfg80211: Disabling freq 5550 MHz
[   15.527712] cfg80211: Disabling freq 5560 MHz
[   15.527713] cfg80211: Disabling freq 5580 MHz
[   15.527714] cfg80211: Disabling freq 5590 MHz
[   15.527716] cfg80211: Disabling freq 5600 MHz
[   15.527717] cfg80211: Disabling freq 5620 MHz
[   15.527719] cfg80211: Disabling freq 5630 MHz
[   15.527720] cfg80211: Disabling freq 5640 MHz
[   15.527722] cfg80211: Disabling freq 5660 MHz
[   15.527723] cfg80211: Disabling freq 5670 MHz
[   15.527725] cfg80211: Disabling freq 5680 MHz
[   15.527726] cfg80211: Disabling freq 5700 MHz
[   15.527728] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   15.527731] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527733] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[   15.527735] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527737] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   15.527739] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527741] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   15.527744] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527746] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[   15.527749] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527751] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   15.527753] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527755] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   15.527758] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527759] cfg80211: Disabling freq 5835 MHz
[   15.527761] cfg80211: Disabling freq 5845 MHz
[   15.527763] cfg80211: Disabling freq 5855 MHz
[   15.527764] cfg80211: Disabling freq 5865 MHz
[   15.527765] cfg80211: Disabling freq 4920 MHz
[   15.527767] cfg80211: Disabling freq 4940 MHz
[   15.527768] cfg80211: Disabling freq 4960 MHz
[   15.527769] cfg80211: Disabling freq 4980 MHz
[   15.527771] cfg80211: Disabling freq 6040 MHz
[   15.527772] cfg80211: Disabling freq 6060 MHz
[   15.527773] cfg80211: Disabling freq 6080 MHz
[   15.527777] cfg80211: World regulatory domain updated:
[   15.527779] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.527782] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527784] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.527786] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.527788] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.527790] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.564053] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[   15.564129] radeon 0000:01:05.0: WB enabled
[   15.595947] [drm] ring test succeeded in 1 usecs
[   15.596078] [drm] radeon: ib pool ready.
[   15.596128] [drm] ib test succeeded in 0 usecs
[   15.596401] [drm] Radeon Display Connectors
[   15.596403] [drm] Connector 0:
[   15.596404] [drm]   VGA
[   15.596407] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.596409] [drm]   Encoders:
[   15.596410] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   15.596412] [drm] Connector 1:
[   15.596414] [drm]   DVI-D
[   15.596415] [drm]   HPD1
[   15.596416] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   15.596418] [drm]   Encoders:
[   15.596419] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[   15.596445] [drm] radeon: power management initialized
[   15.684947] [drm] fb mappable at 0xD0142000
[   15.684949] [drm] vram apper at 0xD0000000
[   15.684951] [drm] size 8294400
[   15.684952] [drm] fb depth is 24
[   15.684955] [drm]    pitch is 7680
[   15.685051] fbcon: radeondrmfb (fb0) is primary device
[   15.704235] Console: switching to colour frame buffer device 240x67
[   15.718807] fb0: radeondrmfb frame buffer device
[   15.718809] drm: registered panic notifier
[   15.718817] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   15.718854] snd_hda_intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   15.718884] snd_hda_intel 0000:01:05.1: setting latency timer to 64
[   15.744570] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.822134] init: failsafe main process (778) killed by TERM signal
[   15.981709] type=1400 audit(1336167997.885:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   15.981723] type=1400 audit(1336167997.885:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=850 comm="apparmor_parser"
[   15.982958] type=1400 audit(1336167997.885:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=852 comm="apparmor_parser"
[   15.983926] type=1400 audit(1336167997.885:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   44.657164] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.719906] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[   76.316174] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   76.353200] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  121.072221] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  121.118437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  308.580241] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  308.626481] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  590.992226] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  591.022480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  799.852144] rt2800pci 0000:04:07.0: PCI INT A disabled
[  804.430062] cfg80211: Calling CRDA to update world regulatory domain
[  804.438355] cfg80211: World regulatory domain updated:
[  804.438360] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  804.438366] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.438372] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  804.438377] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  804.438381] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.438386] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.441940] rt2800pci 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  804.450559] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  804.450562] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450564] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  804.450566] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450568] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  804.450570] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450572] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  804.450574] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450575] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  804.450577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450579] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  804.450581] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450583] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  804.450585] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450586] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  804.450588] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450590] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  804.450592] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450594] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  804.450596] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450597] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  804.450599] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450601] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  804.450603] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  804.450605] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  804.450607] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  804.450608] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  804.450610] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  804.450612] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  804.450614] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450616] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[  804.450618] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450620] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  804.450622] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450623] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  804.450625] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450627] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  804.450629] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450631] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  804.450633] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450634] cfg80211: Disabling freq 5260 MHz
[  804.450635] cfg80211: Disabling freq 5270 MHz
[  804.450636] cfg80211: Disabling freq 5280 MHz
[  804.450637] cfg80211: Disabling freq 5300 MHz
[  804.450639] cfg80211: Disabling freq 5310 MHz
[  804.450640] cfg80211: Disabling freq 5320 MHz
[  804.450641] cfg80211: Disabling freq 5500 MHz
[  804.450642] cfg80211: Disabling freq 5510 MHz
[  804.450643] cfg80211: Disabling freq 5520 MHz
[  804.450644] cfg80211: Disabling freq 5540 MHz
[  804.450645] cfg80211: Disabling freq 5550 MHz
[  804.450646] cfg80211: Disabling freq 5560 MHz
[  804.450647] cfg80211: Disabling freq 5580 MHz
[  804.450648] cfg80211: Disabling freq 5590 MHz
[  804.450650] cfg80211: Disabling freq 5600 MHz
[  804.450651] cfg80211: Disabling freq 5620 MHz
[  804.450652] cfg80211: Disabling freq 5630 MHz
[  804.450653] cfg80211: Disabling freq 5640 MHz
[  804.450654] cfg80211: Disabling freq 5660 MHz
[  804.450655] cfg80211: Disabling freq 5670 MHz
[  804.450656] cfg80211: Disabling freq 5680 MHz
[  804.450657] cfg80211: Disabling freq 5700 MHz
[  804.450659] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  804.450661] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450662] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[  804.450664] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450666] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  804.450668] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450670] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  804.450672] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450673] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[  804.450675] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450677] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  804.450679] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450681] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  804.450683] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  804.450684] cfg80211: Disabling freq 5835 MHz
[  804.450685] cfg80211: Disabling freq 5845 MHz
[  804.450686] cfg80211: Disabling freq 5855 MHz
[  804.450688] cfg80211: Disabling freq 5865 MHz
[  804.450689] cfg80211: Disabling freq 4920 MHz
[  804.450690] cfg80211: Disabling freq 4940 MHz
[  804.450691] cfg80211: Disabling freq 4960 MHz
[  804.450692] cfg80211: Disabling freq 4980 MHz
[  804.450693] cfg80211: Disabling freq 6040 MHz
[  804.450694] cfg80211: Disabling freq 6060 MHz
[  804.450695] cfg80211: Disabling freq 6080 MHz
[  804.450769] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  804.451252] Registered led device: rt2800pci-phy0::radio
[  804.451269] Registered led device: rt2800pci-phy0::assoc
[  804.451287] Registered led device: rt2800pci-phy0::quality
[  808.644551] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  808.694483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  817.389705] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[  847.300169] rt2800pci 0000:04:07.0: PCI INT A disabled
[  855.153755] cfg80211: Calling CRDA to update world regulatory domain
[  855.162191] cfg80211: World regulatory domain updated:
[  855.162196] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  855.162202] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.162207] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  855.162212] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  855.162217] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.162222] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.167336] rt2800pci 0000:04:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  855.177243] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  855.177249] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177254] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  855.177260] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177265] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  855.177270] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177274] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  855.177280] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177284] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  855.177289] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177293] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  855.177299] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177303] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  855.177308] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177312] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  855.177317] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177322] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  855.177327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177331] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  855.177336] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177340] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  855.177352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177353] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  855.177356] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  855.177357] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  855.177359] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  855.177361] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  855.177363] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  855.177365] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  855.177367] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177368] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[  855.177370] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177372] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  855.177374] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177376] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  855.177378] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177379] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  855.177382] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177383] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  855.177385] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177387] cfg80211: Disabling freq 5260 MHz
[  855.177388] cfg80211: Disabling freq 5270 MHz
[  855.177389] cfg80211: Disabling freq 5280 MHz
[  855.177390] cfg80211: Disabling freq 5300 MHz
[  855.177391] cfg80211: Disabling freq 5310 MHz
[  855.177392] cfg80211: Disabling freq 5320 MHz
[  855.177393] cfg80211: Disabling freq 5500 MHz
[  855.177395] cfg80211: Disabling freq 5510 MHz
[  855.177396] cfg80211: Disabling freq 5520 MHz
[  855.177397] cfg80211: Disabling freq 5540 MHz
[  855.177398] cfg80211: Disabling freq 5550 MHz
[  855.177399] cfg80211: Disabling freq 5560 MHz
[  855.177400] cfg80211: Disabling freq 5580 MHz
[  855.177401] cfg80211: Disabling freq 5590 MHz
[  855.177402] cfg80211: Disabling freq 5600 MHz
[  855.177403] cfg80211: Disabling freq 5620 MHz
[  855.177404] cfg80211: Disabling freq 5630 MHz
[  855.177405] cfg80211: Disabling freq 5640 MHz
[  855.177407] cfg80211: Disabling freq 5660 MHz
[  855.177408] cfg80211: Disabling freq 5670 MHz
[  855.177409] cfg80211: Disabling freq 5680 MHz
[  855.177410] cfg80211: Disabling freq 5700 MHz
[  855.177411] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  855.177413] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177415] cfg80211: Updating information on frequency 5755 MHz for a 20 MHz width channel with regulatory rule:
[  855.177417] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177419] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  855.177421] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177422] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  855.177424] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177426] cfg80211: Updating information on frequency 5795 MHz for a 20 MHz width channel with regulatory rule:
[  855.177428] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177429] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  855.177431] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177433] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  855.177435] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.177437] cfg80211: Disabling freq 5835 MHz
[  855.177438] cfg80211: Disabling freq 5845 MHz
[  855.177439] cfg80211: Disabling freq 5855 MHz
[  855.177440] cfg80211: Disabling freq 5865 MHz
[  855.177441] cfg80211: Disabling freq 4920 MHz
[  855.177442] cfg80211: Disabling freq 4940 MHz
[  855.177443] cfg80211: Disabling freq 4960 MHz
[  855.177445] cfg80211: Disabling freq 4980 MHz
[  855.177446] cfg80211: Disabling freq 6040 MHz
[  855.177447] cfg80211: Disabling freq 6060 MHz
[  855.177448] cfg80211: Disabling freq 6080 MHz
[  855.177525] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  855.177954] Registered led device: rt2800pci-phy0::radio
[  855.177968] Registered led device: rt2800pci-phy0::assoc
[  855.177983] Registered led device: rt2800pci-phy0::quality
[  894.388563] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  894.414488] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  906.785021] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
[  996.836304] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[  996.862469] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

lsmod:
```
Module                  Size  Used by
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
snd_hda_codec_hdmi     32474  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
psmouse                87692  0 
serio_raw              13211  0 
fam15h_power           13032  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
radeon                804372  1 
snd_hda_intel          33773  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hid_logitech_dj        18593  0 
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
snd_timer              29990  1 snd_pcm
snd                    78855  7 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
drm                   242038  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_atk0110           18078  0 
shpchp                 37277  0 
mac_hid                13253  0 
wmi                    19256  0 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
lp                     17799  0 
parport                46562  1 lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sata_sil24             18146  0 
r8169                  62099  0 
pata_atiixp            13204  0 
pata_via               13701  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```

lshw:
```
jserver
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=E00D001E-8C00-0034-6CBC-5404A6F23001
  *-core
       description: Motherboard
       product: M5A88-V EVO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MF70BCG00700124
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1202
          date: 03/16/2012
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-4100 Quad-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-4100 Quad-Core Processor
          serial: To Be Filled By O.E.M.
          slot: AM3R2
          size: 1400MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 192KiB
             capacity: 192KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 37
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM Synchronous 1600 MHz (0.6 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS880 PCI to PCI bridge (int gfx)
             vendor: ASUSTeK Computer Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:fe700000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4250]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:b000(size=256) memory:fe8f0000-fe8fffff memory:fe700000-fe7fffff
           *-multimedia
                description: Audio device
                product: RS880 HDMI Audio [Radeon HD 4200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fe8e8000-fe8ebfff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 4)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:fe900000-fe9fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:17 memory:fe9ff800-fe9fffff ioport:c800(size=256)
           *-ide
                description: IDE interface
                product: VT6415 PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a0
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom
                configuration: driver=pata_via latency=0
                resources: irq:17 ioport:cc00(size=8) ioport:c480(size=4) ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=16) memory:fe9e0000-fe9effff
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fea00000-feafffff
           *-usb
                description: USB controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:feaf8000-feafffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:19 ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=8) ioport:7000(size=4) ioport:6000(size=16) memory:fe6ffc00-fe6fffff
           *-disk:0
                description: ATA Disk
                product: WDC WD2500AAKX-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 15.0
                serial: WD-WCAYUF014209
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003ba04
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0e5f40ec-d579-4eb3-ac61-a2232c3de58d
                   size: 225GiB
                   capacity: 225GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-04-30 10:18:19 filesystem=ext4 lastmountpoint=/ modified=2012-04-30 10:37:30 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-05-02 01:24:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 7934MiB
                   capacity: 7934MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 7934MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST1500DL003-9VT1
                vendor: Seagate
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: CC32
                serial: 6YD0ZVJ1
                size: 1397GiB (1500GB)
                configuration: ansiversion=5
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fe000-fe6fefff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff800-fe6ff8ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fd000-fe6fdfff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff400-fe6ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: BDDVDRW UH12LS28
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fe6f8000-fe6fbfff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:d000(size=4096) memory:feb00000-febfffff
           *-storage
                description: RAID bus controller
                product: SiI 3124 PCI-X Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 02
                width: 64 bits
                clock: 66MHz
                capabilities: storage pm pcix msi bus_master cap_list rom
                configuration: driver=sata_sil24 latency=64
                resources: irq:21 memory:febfbc00-febfbc7f memory:febf0000-febf7fff ioport:dc00(size=16) memory:feb00000-feb7ffff
           *-network DISABLED
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: Ralink corp.
                physical id: 7
                bus info: pci@0000:04:07.0
                logical name: wlan0
                version: 00
                serial: 98:fc:11:e3:93:d3
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-24-generic firmware=0.34 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:22 memory:febe0000-febeffff
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6fc000-fe6fcfff
        *-pci:4
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-pci:5
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:e000(size=4096) ioport:fdf00000(size=1048576)
           *-network DISABLED
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 54:04:a6:f2:30:01
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:49 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe6f7000-fe6f7fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe6ff000-fe6ff0ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz

```

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

```

lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4250]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
02:00.1 IDE interface: VIA Technologies, Inc. VT6415 PATA IDE Host Controller (rev a0)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:06.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
04:07.0 Network controller: Ralink corp. RT2800 802.11n PCI
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

screen capture:
```
root@jserver:~# ifconfig wlan0 up
root@jserver:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:15:FF:0E:37:4E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Verizon MIFI4510L 374E Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001570ccd188
                    Extra: Last beacon: 2784ms ago
                    IE: Unknown: 001D566572697A6F6E204D494649343531304C203337344520536563757265
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 072455532001010D02010D03010D04010D05010D06010D07010D08010D09010D0A010D0B010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
          Cell 02 - Address: 2C:B0:5D:25:13:7D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Taco-Box"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 2796ms ago
                    IE: Unknown: 00085461636F2D426F78
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B00010310470010EF1BAF101C6D35CE47DFA11EEEB440F31021000D4E4554474541522C20496E632E10230008574E44523430303010240008574E4452343030301042000230311054000800060050F204000110110008574E445234303030100800020084103C000103
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 2E:B0:5D:25:13:7E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Taco-Box-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 2796ms ago
                    IE: Unknown: 000E5461636F2D426F782D4775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:22:2D:BB:E0:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"SMCWBR14S-03F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004030fc570a1
                    Extra: Last beacon: 2788ms ago
                    IE: Unknown: 000D534D435742523134532D303346
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000024127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336C0117FF000000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000100000000000000000000000000000000000000
          Cell 05 - Address: 00:1E:E5:4E:DB:FC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f20df6da7
                    Extra: Last beacon: 2476ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD710050F204104A0001101044000101103B00010310470010001EE54EDBFA001EE54EDBFA0400E8001021000C4C696E6B73797320496E632E102300075752543331304E1024000776312E302E3036104200033031361054000800060050F2040001101100075752543331304E100800020084
                    IE: Unknown: DD090010180200F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081100000000000000000000000000000000000000
          Cell 06 - Address: AC:81:12:80:5F:CD
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"buckeye2553"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018473214046
                    Extra: Last beacon: 2280ms ago
                    IE: Unknown: 000B6275636B65796532353533
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF00000001000000000000000000000000000000000000
                    IE: Unknown: 3D1609000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000E127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706313920010910
          Cell 07 - Address: 00:17:C5:5D:CA:F7
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DrBrix"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002e7555d4
                    Extra: Last beacon: 2224ms ago
                    IE: Unknown: 0006447242726978
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201010E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A0E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A071B00000000000000000000000000000000000000
                    IE: Unknown: 3D160A071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
          Cell 08 - Address: 00:21:7C:80:98:B1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE420"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004af627972bd
                    Extra: Last beacon: 2168ms ago
                    IE: Unknown: 00083257495245343230
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 09 - Address: 2C:B0:5D:25:13:7C
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Taco-Box -5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000531b22603a
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 000C5461636F2D426F78202D3547
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 050400020100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A7F081BFFFFFF0001000000000000000000000000000000000000
                    IE: Unknown: 3D16990F1600000000000000000000000000000000000000
                    IE: Unknown: DD270050F204104A000110104400010210470010EF1BAF101C6D35CE47DFA11EEEB440F3103C000103
                    IE: Unknown: DD090010180202F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

root@jserver:~# ifconfig wlan0 down
root@jserver:~# cat /etc/wpa_supplicant.conf
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
update_config=1
root@jserver:~# wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -ddd -B
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
update_config=1
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 98:fc:11:e3:93:d3
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=4 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_key: alg=0 key_idx=5 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
State: DISCONNECTED -> INACTIVE
WPS: UUID based on MAC address - hexdump(len=16): 69 a3 38 e2 16 8a 52 2f 88 00 66 57 68 dd 40 d8
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
Daemonize..
root@jserver:~# wpa_cli 
wpa_cli v0.7.3
Copyright (c) 2004-2010, Jouni Malinen <j@w1.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.


Selected interface 'wlan0'

Interactive mode

> scan
OK
> scan_results 
<2>CTRL-EVENT-SCAN-RESULTS 
> scan_results bssid / frequency / signal level / flags / ssid
> terminate
OK
> quit
root@jserver:~# exit

Script done on Fri 04 May 2012 06:03:39 PM EDT

```

---

### Post by chili555 on 2012-05-05
I'm not so sure it's wpa_supplicant; I think it may be the driver and firmware combination:> phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareYou might try a driver parameter:```
sudo modprobe -r t2800pci
sudo modprobe rt2800pci nohwcrypt=1
```Also, there is a different (newer? better??) firmware package available. You might try rt2860.bin from the package I've attached. You seem quite resourceful, but if you need assistance installing the newer firmware, don't hesitate to post back.

---

### Post by jasonlyle88 on 2012-05-05
I tried loading the driver with the parameter that you mentioned, but I am still receiving the MCU error when starting up the interface.  So if you could help me out with how to load the bin file you mentioned in your previous post, I would greatly appreciate it.  I am quite resourceful... but I am new to linux system administration, and mostly just a good googler.  And while I am sure I could find information on how to do it, determining which method i find as best may prove difficult!  So if you could tell me or point me to instructions, that would be great!

---

### Post by chili555 on 2012-05-05
Please run:```
dmesg
```Note the ending timestamp; we'll refer to it later. For example:> [88666.991152] wlan0: RX AssocResp from xx:13:10:62:8d:xx (capab=0x411 status=0 aid=2)
[88666.991160] wlan0: associated
[88666.993334] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[[COLOR="Red"]88677.568048[/COLOR]] wlan0: no IPv6 routers present

Download the file to your desktop so we can find it readily. Right-click it and select *Extract Here*. Now open a terminal and we back up the existing firmware:```
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bak
```By the way, a good practice is always back up. As you see, in Linux, it's fairly easy. Now we move over the new firmware:```
sudo cp Desktop/RT2860_Firmware_V26/rt2860.bin /lib/firmware
```Now unload the driver and reload so it grabs the new firmware:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci
```Now check dmesg; be aware of the timestamp; you want to see if the newest changes still cause the error:```
dmesg | grep rt2800pci
```

---

### Post by jasonlyle88 on 2012-05-05
Still having the same problem with the new bin file loaded.  I loaded the module once without parameters and once with the nohwcrypt=1 parameter, and both times i experienced the same issue as before and still received the MCU error upon starting the interface

---

### Post by chili555 on 2012-05-05
Googling, I found this: [http://www.spinics.net/lists/linux-wireless/msg85339.html](http://www.spinics.net/lists/linux-wireless/msg85339.html)  I have no idea when or how this patch may arrive. I also have no idea how to patch and recompile your kernel. 

You might try the linux-backports-modules-cw-3.3-precise-generic package available in Synaptic package manager. rt2800pci is different (new? better??) there; here is the standard version:> modinfo rt2800pci
filename:       /lib/modules/3.2.0-24-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[COLOR="Red"]srcversion:     88E705B35667EF897566E11[/COLOR]And here is backports-cw, also known as compat-wireless:>  modinfo rt2800pci
filename:       /lib/modules/3.2.0-24-generic-pae/[COLOR="Red"]updates/cw-3.3[/COLOR]/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[COLOR="Red"]srcversion:     B597DAC5FF6E682CF4224F6[/COLOR]I hope it will help.

---

### Post by jasonlyle88 on 2012-05-08
Wonderful, that linux_backports package worked for me!  Thank you very much for all your help!

---

### Post by chili555 on 2012-05-08
Glad it's working. So the searchers can learn from your experience, please use thread tools at the top to Mark Solved.

---

