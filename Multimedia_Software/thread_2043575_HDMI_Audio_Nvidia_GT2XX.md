---
title: "HDMI Audio Nvidia GT2XX"
date: 2012-08-16
forum: Multimedia Software
---

### Post by LycanThroat70 on 2012-08-16
Having some issues with the GT218 (GT210) HDMI audio. Right now i have  the nvidia binary drivers installed (most recent version) and for some  reason aplay doesn't even find the audio device. (aplay:  device_list:252: no soundcards found...)  

I was using the nouveau driver for a while and the audio devices would show - since then nothing.. 

In both cases the audio never worked.

Please advise on the next steps as I'm completely lost.

```

Linux allan-pc 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

dmesg | grep 01:00.1
```

[    0.789610] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.789626] pci 0000:01:00.1: reg 10: [mem 0xfebf8000-0xfebfbfff]

```

lspci -v
```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device 1160
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at feb00000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nouveau, nvidiafb

01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 1160
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel modules: snd-hda-intel

```


```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic (buildd@allspice) (gcc  version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27  17:03:23 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.2.0-29-generic  root=UUID=b8cffa94-6590-4560-ae9e-6ce28da218e2 ro quiet splash  vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7e80000 (usable)
[    0.000000]  BIOS-e820: 00000000c7e80000 - 00000000c7e98000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7e98000 - 00000000c7ec0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7ec0000 - 00000000c7f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000137000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX V2, BIOS 0801    02/15/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x137000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000137000000 aka 4976M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7e80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7e80000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00c7e00000 page 2M
[    0.000000]  00c7e00000 - 00c7e80000 page 4k
[    0.000000] kernel direct mapping tables up to c7e80000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000137000000
[    0.000000]  0100000000 - 0137000000 page 2M
[    0.000000] kernel direct mapping tables up to 137000000 @ c7e7e000-c7e80000
[    0.000000] RAMDISK: 364d4000 - 37262000
[    0.000000] ACPI: RSDP 00000000000fb490 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000c7e80100 00054 (v01 021512 XSDT1624 20120215 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000c7e80290 000F4 (v03 021512 FACP1624 20120215 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero  address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000c7e80460 0D6DB (v01  A1974 A1974001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000c7e98000 00040
[    0.000000] ACPI: APIC 00000000c7e80390 0008C (v01 021512 APIC1624 20120215 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000c7e80420 0003C (v01 021512 OEMMCFG  20120215 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000c7e98040 00072 (v01 021512 OEMB1624 20120215 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000c7e8f460 00038 (v01 021512 OEMHPET  20120215 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c7e8f4a0 01158 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000137000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000137000000
[    0.000000]   NODE_DATA [0000000136ffb000 - 0000000136ffffff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880132600000-ffff8801365fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00137000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c7e80
[    0.000000]     0: 0x00100000 -> 0x00137000
[    0.000000] On node 0 totalpages: 1043983
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 798400 pages, LIFO batch:31
[    0.000000]   Normal zone: 3520 pages used for memmap
[    0.000000]   Normal zone: 221760 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x16] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 22, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c7e80000 - 00000000c7e98000
[    0.000000] PM: Registered nosave memory: 00000000c7e98000 - 00000000c7ec0000
[    0.000000] PM: Registered nosave memory: 00000000c7ec0000 - 00000000c7f00000
[    0.000000] PM: Registered nosave memory: 00000000c7f00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c7f00000 (gap: c7f00000:37f00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff880136c00000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1024074
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-29-generic  root=UUID=b8cffa94-6590-4560-ae9e-6ce28da218e2 ro quiet splash  vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ bc000000
[    0.000000] PM: Registered nosave memory: 00000000bc000000 - 00000000c0000000
[    0.000000] Memory: 3948204k/5095424k available (6555k kernel code, 919492k absent, 227728k reserved, 6645k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3314.750 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6629.50 BogoMIPS (lpj=13259000)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004029] Security Framework initialized
[    0.004040] AppArmor: AppArmor initialized
[    0.004041] Yama: becoming mindful.
[    0.004480] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005596] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.006051] Mount-cache hash table entries: 256
[    0.006167] Initializing cgroup subsys cpuacct
[    0.006171] Initializing cgroup subsys memory
[    0.006179] Initializing cgroup subsys devices
[    0.006181] Initializing cgroup subsys freezer
[    0.006182] Initializing cgroup subsys blkio
[    0.006187] Initializing cgroup subsys perf_event
[    0.006210] tseg: 0000000000
[    0.006220] CPU: Physical Processor ID: 0
[    0.006221] CPU: Processor Core ID: 0
[    0.006223] mce: CPU supports 7 MCE banks
[    0.008965] ACPI: Core revision 20110623
[    0.016017] ftrace: allocating 26998 entries in 106 pages
[    0.020400] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.062326] CPU0: AMD FX(tm)-6100 Six-Core Processor              stepping 02
[    0.064003] Performance Events: AMD Family 15h PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      6
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000003f
[    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 9a000
[    0.152030] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152131]  #2
[    0.152133] smpboot cpu 2: start_ip = 9a000
[    0.244028] NMI watchdog enabled, takes one hw-pmu counter.
[    0.244091]  #3
[    0.244092] smpboot cpu 3: start_ip = 9a000
[    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
[    0.336094]  #4
[    0.336095] smpboot cpu 4: start_ip = 9a000
[    0.428039] NMI watchdog enabled, takes one hw-pmu counter.
[    0.428122]  #5
[    0.428123] smpboot cpu 5: start_ip = 9a000
[    0.520043] NMI watchdog enabled, takes one hw-pmu counter.
[    0.520068] Brought up 6 CPUs
[    0.520070] Total of 6 processors activated (39777.27 BogoMIPS).
[    0.524217] devtmpfs: initialized
[    0.528307] EVM: security.selinux
[    0.528308] EVM: security.SMACK64
[    0.528310] EVM: security.capability
[    0.528335] PM: Registering ACPI NVS region at c7e98000 (163840 bytes)
[    0.528781] print_constraints: dummy: 
[    0.528808] RTC time:  1:25:55, date: 08/17/12
[    0.528840] NET: Registered protocol family 16
[    0.528958] Extended Config Space enabled on 1 nodes
[    0.528976] ACPI: bus type pci registered
[    0.529092] Trying to unpack rootfs image as initramfs...
[    0.529037] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.529040] PCI: not using MMCONFIG
[    0.529042] PCI: Using configuration type 1 for base access
[    0.529043] PCI: Using configuration type 1 for extended access
[    0.529951] bio: create slab <bio-0> at 0
[    0.529951] ACPI: Added _OSI(Module Device)
[    0.529951] ACPI: Added _OSI(Processor Device)
[    0.529951] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.529951] ACPI: Added _OSI(Processor Aggregator Device)
[    0.529951] ACPI: EC: Look up EC in DSDT
[    0.534481] ACPI: Executed 3 blocks of module-level executable AML code
[    0.604911] ACPI: Interpreter enabled
[    0.604916] ACPI: (supports S0 S1 S3 S4 S5)
[    0.604948] ACPI: Using IOAPIC for interrupt routing
[    0.604975] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.607055] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.763642] Freeing initrd memory: 13880k freed
[    0.786409] ACPI: No dock devices found.
[    0.786415] HEST: Table not found.
[    0.786422] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.786670] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.787174] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.787180] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.787185] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.787191] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.787196] pci_root PNP0A03:00: host bridge window [mem 0xc7f00000-0xdfffffff]
[    0.787201] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.787229] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.787325] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.787390] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.787397] pci 0000:00:02.0: PME# disabled
[    0.787424] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.787488] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.787493] pci 0000:00:04.0: PME# disabled
[    0.787545] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.787572] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.787587] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.787602] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.787616] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.787631] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.787645] pci 0000:00:11.0: reg 24: [mem 0xfcfffc00-0xfcffffff]
[    0.787674] pci 0000:00:11.0: set SATA to AHCI mode
[    0.787739] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.787760] pci 0000:00:12.0: reg 10: [mem 0xfcffe000-0xfcffefff]
[    0.787848] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.787868] pci 0000:00:12.1: reg 10: [mem 0xfcffd000-0xfcffdfff]
[    0.787964] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.787991] pci 0000:00:12.2: reg 10: [mem 0xfcfff800-0xfcfff8ff]
[    0.788129] pci 0000:00:12.2: supports D1 D2
[    0.788133] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.788140] pci 0000:00:12.2: PME# disabled
[    0.788183] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.788204] pci 0000:00:13.0: reg 10: [mem 0xfcffc000-0xfcffcfff]
[    0.788293] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.788313] pci 0000:00:13.1: reg 10: [mem 0xfcffb000-0xfcffbfff]
[    0.788408] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.788436] pci 0000:00:13.2: reg 10: [mem 0xfcfff400-0xfcfff4ff]
[    0.788545] pci 0000:00:13.2: supports D1 D2
[    0.788549] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.788556] pci 0000:00:13.2: PME# disabled
[    0.788592] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.788727] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.788751] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.788766] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.788780] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.788794] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.788808] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.788886] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.788989] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.789048] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.789068] pci 0000:00:14.5: reg 10: [mem 0xfcffa000-0xfcffafff]
[    0.789166] pci 0000:00:18.0: [1022:1600] type 0 class 0x000600
[    0.789210] pci 0000:00:18.1: [1022:1601] type 0 class 0x000600
[    0.789243] pci 0000:00:18.2: [1022:1602] type 0 class 0x000600
[    0.789278] pci 0000:00:18.3: [1022:1603] type 0 class 0x000600
[    0.789321] pci 0000:00:18.4: [1022:1604] type 0 class 0x000600
[    0.789354] pci 0000:00:18.5: [1022:1605] type 0 class 0x000600
[    0.789452] pci 0000:01:00.0: [10de:0a65] type 0 class 0x000300
[    0.789468] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.789485] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.789502] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.789515] pci 0000:01:00.0: reg 24: [io  0xdc00-0xdc7f]
[    0.789527] pci 0000:01:00.0: reg 30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.789610] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.789626] pci 0000:01:00.1: reg 10: [mem 0xfebf8000-0xfebfbfff]
[    0.796077] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.796086] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.796092] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.796100] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.796180] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.796204] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.796237] pci 0000:02:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit pref]
[    0.796262] pci 0000:02:00.0: reg 20: [mem 0xfbff8000-0xfbffbfff 64bit pref]
[    0.796341] pci 0000:02:00.0: supports D1 D2
[    0.796345] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.796357] pci 0000:02:00.0: PME# disabled
[    0.804078] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.804086] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.804096] pci 0000:00:04.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.804185] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.804200] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.804205] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.804211] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.804217] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.804223] pci 0000:00:14.4:   bridge window [mem 0xc7f00000-0xdfffffff] (subtractive decode)
[    0.804228] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.804251] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.804783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.804866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.805010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.805143]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.805150]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.805154] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.814473] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.814520] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.814565] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.814609] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.814652] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.814698] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.814747] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.814785] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.814873] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.814873] vgaarb: loaded
[    0.814873] vgaarb: bridge control possible 0000:01:00.0
[    0.814873] i2c-core: driver [aat2870] using legacy suspend method
[    0.814873] i2c-core: driver [aat2870] using legacy resume method
[    0.814873] SCSI subsystem initialized
[    0.814990] libata version 3.00 loaded.
[    0.814990] usbcore: registered new interface driver usbfs
[    0.814990] usbcore: registered new interface driver hub
[    0.814990] usbcore: registered new device driver usb
[    0.814990] PCI: Using ACPI for IRQ routing
[    0.824269] PCI: pci_cache_line_size set to 64 bytes
[    0.824340] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.824342] reserve RAM buffer: 00000000c7e80000 - 00000000c7ffffff 
[    0.824345] reserve RAM buffer: 0000000137000000 - 0000000137ffffff 
[    0.824426] NetLabel: Initializing
[    0.824427] NetLabel:  domain hash size = 128
[    0.824428] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.824438] NetLabel:  unlabeled traffic allowed by default
[    0.824457] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.824457] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.826113] Switching to clocksource hpet
[    0.830623] AppArmor: AppArmor Filesystem Enabled
[    0.830639] pnp: PnP ACPI init
[    0.830652] ACPI: bus type pnp registered
[    0.830768] pnp 00:00: [bus 00-ff]
[    0.830770] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.830772] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.830774] pnp 00:00: [io  0x0d00-0xffff window]
[    0.830776] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.830778] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.830781] pnp 00:00: [mem 0xc7f00000-0xdfffffff window]
[    0.830783] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.830822] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.830914] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.830916] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.830956] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.831000] pnp 00:02: [dma 4]
[    0.831002] pnp 00:02: [io  0x0000-0x000f]
[    0.831004] pnp 00:02: [io  0x0081-0x0083]
[    0.831005] pnp 00:02: [io  0x0087]
[    0.831007] pnp 00:02: [io  0x0089-0x008b]
[    0.831009] pnp 00:02: [io  0x008f]
[    0.831010] pnp 00:02: [io  0x00c0-0x00df]
[    0.831038] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.831050] pnp 00:03: [io  0x0070-0x0071]
[    0.831058] pnp 00:03: [irq 8]
[    0.831084] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.831092] pnp 00:04: [io  0x0061]
[    0.831119] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.831127] pnp 00:05: [io  0x00f0-0x00ff]
[    0.831131] pnp 00:05: [irq 13]
[    0.831160] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.832053] pnp 00:06: [io  0x0378-0x037f]
[    0.832057] pnp 00:06: [irq 7]
[    0.832061] pnp 00:06: [dma 0 disabled]
[    0.832366] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.832402] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    0.832432] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.833071] pnp 00:08: [io  0x03f8-0x03ff]
[    0.833076] pnp 00:08: [irq 4]
[    0.833078] pnp 00:08: [dma 0 disabled]
[    0.833158] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.833250] pnp 00:09: [io  0x0060]
[    0.833252] pnp 00:09: [io  0x0064]
[    0.833253] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.833255] pnp 00:09: [mem 0xfee00000-0xfee00fff]
[    0.833302] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.833305] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.833308] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.833525] pnp 00:0a: [io  0x0010-0x001f]
[    0.833527] pnp 00:0a: [io  0x0022-0x003f]
[    0.833528] pnp 00:0a: [io  0x0062-0x0063]
[    0.833530] pnp 00:0a: [io  0x0065-0x006f]
[    0.833532] pnp 00:0a: [io  0x0072-0x007f]
[    0.833533] pnp 00:0a: [io  0x0080]
[    0.833535] pnp 00:0a: [io  0x0084-0x0086]
[    0.833536] pnp 00:0a: [io  0x0088]
[    0.833538] pnp 00:0a: [io  0x008c-0x008e]
[    0.833540] pnp 00:0a: [io  0x0090-0x009f]
[    0.833541] pnp 00:0a: [io  0x00a2-0x00bf]
[    0.833543] pnp 00:0a: [io  0x00b1]
[    0.833545] pnp 00:0a: [io  0x00e0-0x00ef]
[    0.833546] pnp 00:0a: [io  0x04d0-0x04d1]
[    0.833548] pnp 00:0a: [io  0x040b]
[    0.833549] pnp 00:0a: [io  0x04d6]
[    0.833551] pnp 00:0a: [io  0x0c00-0x0c01]
[    0.833553] pnp 00:0a: [io  0x0c14]
[    0.833554] pnp 00:0a: [io  0x0c50-0x0c51]
[    0.833556] pnp 00:0a: [io  0x0c52]
[    0.833557] pnp 00:0a: [io  0x0c6c]
[    0.833559] pnp 00:0a: [io  0x0c6f]
[    0.833561] pnp 00:0a: [io  0x0cd0-0x0cd1]
[    0.833562] pnp 00:0a: [io  0x0cd2-0x0cd3]
[    0.833564] pnp 00:0a: [io  0x0cd4-0x0cd5]
[    0.833566] pnp 00:0a: [io  0x0cd6-0x0cd7]
[    0.833567] pnp 00:0a: [io  0x0cd8-0x0cdf]
[    0.833569] pnp 00:0a: [io  0x0b00-0x0b3f]
[    0.833571] pnp 00:0a: [io  0x0800-0x089f]
[    0.833573] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.833574] pnp 00:0a: [io  0x0b00-0x0b0f]
[    0.833576] pnp 00:0a: [io  0x0b20-0x0b3f]
[    0.833578] pnp 00:0a: [io  0x0900-0x090f]
[    0.833579] pnp 00:0a: [io  0x0910-0x091f]
[    0.833581] pnp 00:0a: [io  0xfe00-0xfefe]
[    0.833583] pnp 00:0a: [io  0x0060]
[    0.833584] pnp 00:0a: [io  0x0064]
[    0.833586] pnp 00:0a: [mem 0xc7f00000-0xc7ffffff]
[    0.833588] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
[    0.833592] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
[    0.833594] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.833668] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.833670] system 00:0a: [io  0x040b] has been reserved
[    0.833673] system 00:0a: [io  0x04d6] has been reserved
[    0.833675] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.833677] system 00:0a: [io  0x0c14] has been reserved
[    0.833679] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.833682] system 00:0a: [io  0x0c52] has been reserved
[    0.833684] system 00:0a: [io  0x0c6c] has been reserved
[    0.833686] system 00:0a: [io  0x0c6f] has been reserved
[    0.833688] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.833691] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.833693] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.833695] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.833698] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.833700] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
[    0.833702] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.833705] system 00:0a: [io  0x0b00-0x0b0f] has been reserved
[    0.833707] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
[    0.833709] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.833712] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.833714] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.833720] system 00:0a: [mem 0xc7f00000-0xc7ffffff] has been reserved
[    0.833725] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.833727] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.833730] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.833733] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.833945] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.833947] pnp 00:0b: [io  0x0230-0x023f]
[    0.833949] pnp 00:0b: [io  0x0290-0x029f]
[    0.833951] pnp 00:0b: [io  0x0300-0x030f]
[    0.833952] pnp 00:0b: [io  0x0a30-0x0a3f]
[    0.833998] system 00:0b: [io  0x0230-0x023f] has been reserved
[    0.834001] system 00:0b: [io  0x0290-0x029f] has been reserved
[    0.834003] system 00:0b: [io  0x0300-0x030f] has been reserved
[    0.834005] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
[    0.834008] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.834044] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.834088] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.834091] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.834718] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.834721] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.834723] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.834725] pnp 00:0d: [mem 0x00100000-0xc7efffff]
[    0.834727] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.834811] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.834814] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.834817] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.834819] system 00:0d: [mem 0x00100000-0xc7efffff] could not be reserved
[    0.834822] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.834826] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.834934] pnp: PnP ACPI: found 14 devices
[    0.834936] ACPI: ACPI bus type pnp unregistered
[    0.841927] PCI: max bus depth: 1 pci_try_num: 2
[    0.841942] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.841944] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.841948] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.841951] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.841955] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.841957] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.841961] pci 0000:00:04.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.841965] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.841985] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.841989] pci 0000:00:02.0: setting latency timer to 64
[    0.841997] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.842000] pci 0000:00:04.0: setting latency timer to 64
[    0.842007] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.842009] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.842011] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.842013] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.842015] pci_bus 0000:00: resource 8 [mem 0xc7f00000-0xdfffffff]
[    0.842017] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.842019] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.842021] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.842023] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.842026] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.842028] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.842030] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.842032] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.842034] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.842036] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.842038] pci_bus 0000:03: resource 8 [mem 0xc7f00000-0xdfffffff]
[    0.842040] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.842068] NET: Registered protocol family 2
[    0.842227] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.843373] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.845415] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.845641] TCP: Hash tables configured (established 524288 bind 65536)
[    0.845643] TCP reno registered
[    0.845654] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.845678] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.845761] NET: Registered protocol family 1
[    0.845784] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.948047] pci 0000:00:12.0: PCI INT A disabled
[    0.948064] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.028047] pci 0000:00:12.1: PCI INT A disabled
[    1.028077] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.028131] pci 0000:00:12.2: PCI INT B disabled
[    1.028145] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.108044] pci 0000:00:13.0: PCI INT A disabled
[    1.108061] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.188045] pci 0000:00:13.1: PCI INT A disabled
[    1.188071] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.188125] pci 0000:00:13.2: PCI INT B disabled
[    1.188152] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.268048] pci 0000:00:14.5: PCI INT C disabled
[    1.268096] pci 0000:01:00.0: Boot video device
[    1.268117] PCI: CLS 64 bytes, default 64
[    1.268944] PCI-DMA: Disabling AGP.
[    1.269123] PCI-DMA: aperture base @ bc000000 size 65536 KB
[    1.269127] PCI-DMA: using GART IOMMU.
[    1.269133] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.291052] perf: AMD IBS detected (0x000000ff)
[    1.291407] audit: initializing netlink socket (disabled)
[    1.291424] type=2000 audit(1345166756.284:1): initialized
[    1.320631] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.334728] VFS: Disk quotas dquot_6.5.2
[    1.334780] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.335283] fuse init (API version 7.17)
[    1.335371] msgmni has been set to 7867
[    1.335837] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.335874] io scheduler noop registered
[    1.335876] io scheduler deadline registered
[    1.335903] io scheduler cfq registered (default)
[    1.335992] pcieport 0000:00:02.0: setting latency timer to 64
[    1.336038] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.336076] pcieport 0000:00:04.0: setting latency timer to 64
[    1.336099] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.336158] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.336179] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.336290] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.336295] ACPI: Power Button [PWRB]
[    1.336332] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.336335] ACPI: Power Button [PWRF]
[    1.336620] ACPI: acpi_idle registered with cpuidle
[    1.513149] ERST: Table is not found!
[    1.513154] GHES: HEST is not enabled!
[    1.513302] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.533843] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.592784] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.628454] Linux agpgart interface v0.103
[    1.631459] brd: module loaded
[    1.633022] loop: module loaded
[    1.633268] ahci 0000:00:11.0: version 3.0
[    1.633298] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.633449] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.633457] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.634458] scsi0 : ahci
[    1.634622] scsi1 : ahci
[    1.634771] scsi2 : ahci
[    1.634915] scsi3 : ahci
[    1.635175] ata1: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd00 irq 22
[    1.635182] ata2: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd80 irq 22
[    1.635188] ata3: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe00 irq 22
[    1.635194] ata4: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe80 irq 22
[    1.635375] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.635420] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.636087] Fixed MDIO Bus: probed
[    1.636128] tun: Universal TUN/TAP device driver, 1.6
[    1.636132] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.636238] PPP generic driver version 2.4.2
[    1.636419] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.636443] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.636469] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.636556] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.636569] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.636609] ehci_hcd 0000:00:12.2: debug port 1
[    1.636639] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfcfff800
[    1.648048] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.648288] hub 1-0:1.0: USB hub found
[    1.648297] hub 1-0:1.0: 6 ports detected
[    1.648438] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.648465] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.648555] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.648567] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.648599] ehci_hcd 0000:00:13.2: debug port 1
[    1.648633] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfcfff400
[    1.660041] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.660271] hub 2-0:1.0: USB hub found
[    1.660279] hub 2-0:1.0: 6 ports detected
[    1.660428] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.660451] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.660475] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.660561] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.660601] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfcffe000
[    1.720248] hub 3-0:1.0: USB hub found
[    1.720260] hub 3-0:1.0: 3 ports detected
[    1.720373] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.720398] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.720487] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.720511] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfcffd000
[    1.780277] hub 4-0:1.0: USB hub found
[    1.780288] hub 4-0:1.0: 3 ports detected
[    1.780405] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.780431] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.780533] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.780574] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfcffc000
[    1.840257] hub 5-0:1.0: USB hub found
[    1.840268] hub 5-0:1.0: 3 ports detected
[    1.840383] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.840409] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.840497] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.840521] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.900258] hub 6-0:1.0: USB hub found
[    1.900269] hub 6-0:1.0: 3 ports detected
[    1.900388] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.900414] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.900508] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.900534] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfcffa000
[    1.952069] ata2: SATA link down (SStatus 0 SControl 300)
[    1.952155] ata4: SATA link down (SStatus 0 SControl 300)
[    1.960269] hub 7-0:1.0: USB hub found
[    1.960280] hub 7-0:1.0: 2 ports detected
[    1.960400] uhci_hcd: USB Universal Host Controller Interface driver
[    1.960570] usbcore: registered new interface driver libusual
[    1.960651] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.961063] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.961074] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.961332] mousedev: PS/2 mouse device common for all mice
[    1.961579] rtc_cmos 00:03: RTC can wake from S4
[    1.961750] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.961784] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.961936] device-mapper: uevent: version 1.0.3
[    1.962067] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.962315] cpuidle: using governor ladder
[    1.962734] cpuidle: using governor menu
[    1.962738] EFI Variables Facility v0.08 2004-May-17
[    1.963193] TCP cubic registered
[    1.963409] NET: Registered protocol family 10
[    1.964400] NET: Registered protocol family 17
[    1.964408] Registering the dns_resolver key type
[    1.964666] PM: Hibernation image not present or could not be loaded.
[    1.964683] registered taskstats version 1
[    1.988240]   Magic number: 8:765:407
[    1.988297] acpi PNP0800:00: hash matches
[    1.988379] rtc_cmos 00:03: setting system clock to 2012-08-17 01:25:57 UTC (1345166757)
[    1.988446] powernow-k8: Found 1 AMD FX(tm)-6100 Six-Core Processor              (6 cpu cores) (version 2.20.00)
[    1.988493] powernow-k8: Core Performance Boosting: on.
[    1.988594] powernow-k8:    0 : pstate 0 (3300 MHz)
[    1.988598] powernow-k8:    1 : pstate 1 (3000 MHz)
[    1.988602] powernow-k8:    2 : pstate 2 (2400 MHz)
[    1.988605] powernow-k8:    3 : pstate 3 (1800 MHz)
[    1.988609] powernow-k8:    4 : pstate 4 (1400 MHz)
[    1.990162] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.990168] EDD information not available.
[    2.124136] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.124162] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.124830] ata1.00: ATA-8: ST2000DM001-1CH164, CC43, max UDMA/133
[    2.124833] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.125645] ata1.00: configured for UDMA/133
[    2.125777] scsi 0:0:0:0: Direct-Access     ATA      ST2000DM001-1CH1 CC43 PQ: 0 ANSI: 5
[    2.125925] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.125928] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.125941] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.126036] sd 0:0:0:0: [sda] Write Protect is off
[    2.126038] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.126077] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.126131] ata3.00: ATAPI: TSSTcorp CDDVDW SH-222BB, SB00, max UDMA/100
[    2.127003] ata3.00: configured for UDMA/100
[    2.128149] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-222BB  SB00 PQ: 0 ANSI: 5
[    2.130991] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.130998] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.131241] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.131416] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.154557]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.155273] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.157496] Freeing unused kernel memory: 920k freed
[    2.157664] Write protecting the kernel read-only data: 12288k
[    2.164299] Freeing unused kernel memory: 1616k freed
[    2.169500] Freeing unused kernel memory: 1200k freed
[    2.185363] udevd[118]: starting version 175
[    2.204767] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.204789] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.204823] r8169 0000:02:00.0: setting latency timer to 64
[    2.204884] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.205518] r8169 0000:02:00.0: eth0: RTL8168evl/8111evl at 0xffffc9000065a000, c8:60:00:9c:40:7e, XID 0c900800 IRQ 42
[    2.205522] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.216357] scsi4 : pata_atiixp
[    2.216478] scsi5 : pata_atiixp
[    2.217491] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.217495] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.240151] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[    2.288169] Refined TSC clocksource calibration: 3314.882 MHz.
[    2.288180] Switching to clocksource tsc
[    2.415403] input: Rx504B  Ver:3.03 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
[    2.415560] generic-usb 0003:05AF:0630.0001: input,hidraw0: USB HID  v1.11 Keyboard [Rx504B  Ver:3.03] on usb-0000:00:12.0-3/input0
[    2.423621] input: Rx504B  Ver:3.03 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
[    2.423865] generic-usb 0003:05AF:0630.0002: input,hiddev0,hidraw1:  USB HID v1.11 Mouse [Rx504B  Ver:3.03] on usb-0000:00:12.0-3/input1
[    2.423881] usbcore: registered new interface driver usbhid
[    2.423883] usbhid: USB HID core driver
[    2.583595] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    2.672108] usb 4-1: new low-speed USB device number 2 using ohci_hcd
[    2.856247] input: 2.4GHZ Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input4
[    2.856340] generic-usb 0003:1EA7:0002.0003: input,hidraw2: USB HID  v1.10 Keyboard [2.4GHZ Mouse] on usb-0000:00:12.1-1/input0
[    2.864365] input: 2.4GHZ Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input5
[    2.864499] generic-usb 0003:1EA7:0002.0004: input,hiddev0,hidraw3:  USB HID v1.10 Mouse [2.4GHZ Mouse] on usb-0000:00:12.1-1/input1
[    7.479257] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.677966] udevd[379]: starting version 175
[    7.680689] Adding 7999484k swap on /dev/sda5.  Priority:-1 extents:1 across:7999484k 
[    7.693942] lp: driver loaded but no devices found
[    7.705205] wmi: Mapper loaded
[    7.736764] parport_pc 00:06: reported by Plug and Play ACPI
[    7.736819] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.743198] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[    7.743202] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.743569] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    7.743663] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    7.748559] type=1400 audit(1345166763.259:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=506  comm="apparmor_parser"
[    7.749099] type=1400 audit(1345166763.259:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506  comm="apparmor_parser"
[    7.749402] type=1400 audit(1345166763.259:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=506 comm="apparmor_parser"
[    7.755549] MCE: In-kernel MCE decoding enabled.
[    7.756147] EDAC MC: Ver: 2.1.0
[    7.759415] AMD64 EDAC driver v3.4.0
[    7.761471] EDAC amd64: DRAM ECC disabled.
[    7.761481] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    7.761483]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    7.761484]  (Note that use of the override may cause unknown side effects.)
[    7.811671] ppdev: user-space parallel port driver
[    7.836180] lp0: using parport0 (interrupt-driven).
[    7.887221] nvidia: module license 'NVIDIA' taints kernel.
[    7.887224] Disabling lock debugging due to kernel taint
[    7.941045] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.941053] nvidia 0000:01:00.0: setting latency timer to 64
[    7.941057] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    7.941167] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.37  Wed Aug  8 19:52:48 PDT 2012
[    8.491819] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    8.491822] vesafb: scrolling: redraw
[    8.491824] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    8.501967] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90011400000, using 1216k, total 1216k
[    8.502115] Console: switching to colour frame buffer device 80x30
[    8.502127] fb0: VESA VGA frame buffer device
[    8.709880] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[    9.056207] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    9.548819] init: failsafe main process (768) killed by TERM signal
[    9.597528] Bluetooth: Core ver 2.16
[    9.597548] NET: Registered protocol family 31
[    9.597551] Bluetooth: HCI device and connection manager initialized
[    9.597554] Bluetooth: HCI socket layer initialized
[    9.597556] Bluetooth: L2CAP socket layer initialized
[    9.597562] Bluetooth: SCO socket layer initialized
[    9.599518] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.599521] Bluetooth: BNEP filters: protocol multicast
[    9.607172] type=1400 audit(1345166765.115:5): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=833  comm="apparmor_parser"
[    9.607718] type=1400 audit(1345166765.115:6): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=833  comm="apparmor_parser"
[    9.622392] Bluetooth: RFCOMM TTY layer initialized
[    9.622399] Bluetooth: RFCOMM socket layer initialized
[    9.622401] Bluetooth: RFCOMM ver 1.11
[    9.622471] type=1400 audit(1345166765.131:7): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=870  comm="apparmor_parser"
[    9.623373] type=1400 audit(1345166765.131:8): apparmor="STATUS"  operation="profile_load" name="/usr/lib/telepathy/mission-control-5"  pid=876 comm="apparmor_parser"
[    9.623401] type=1400 audit(1345166765.131:9): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=872  comm="apparmor_parser"
[    9.623901] type=1400 audit(1345166765.131:10): apparmor="STATUS"  operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=876  comm="apparmor_parser"
[    9.623924] type=1400 audit(1345166765.131:11): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=872  comm="apparmor_parser"
[    9.789190] r8169 0000:02:00.0: eth0: link down
[    9.789260] r8169 0000:02:00.0: eth0: link down
[    9.789488] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.789762] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.876379] init: alsa-restore main process (919) terminated with status 19
[   11.480141] NVRM: GPU at 0000:01:00: GPU-7db5104e-0f0e-0dd8-7242-eb64cabc5b77
[   11.480149] NVRM: Your system is not currently configured to drive a VGA console
[   11.480152] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   11.480154] NVRM: requires the use of a text-mode VGA console. Use of other console
[   11.480156] NVRM: drivers including, but not limited to, vesafb, may result in
[   11.480157] NVRM: corruption and stability problems, and is not supported.
[   11.586138] r8169 0000:02:00.0: eth0: link up
[   11.586401] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.704075] eth0: no IPv6 routers present


```

---

### Post by BicyclerBoy on 2012-08-17
You have some odd warnings about console framebuffer not being available to NVM..

Post your /var/log/Xorg.0.log file

You might need to blacklist the "vesafb" module in /etc/modprobe.d/*.conf..

IIRC The nvidia installer should blacklist a couple of other modules..

Is your user a member of the audio group?

---

### Post by LycanThroat70 on 2012-08-19
Thanks for the reply. Yes the user is in the audio group.

This issue is now resolved. How I done this was:

1) First uninstalled the binary driver that was installed manually from the nvidia website. It was version 304.37. The .run script comes with an --uninstall parameter.
2) Installed the binary driver through apt. It was version 295.xx
3) Reboot
4) Messed around with the audio devices in pavucontrol, for some reason 4 hdmi devices appeared, it was one of them.

This is to confirm that HDMI audio does work on the GT210 ( 218 ) with the default Xorg configuration - besides setting the device in pavucontrol. I read somewhere that it was required to enable a pulse module - module-asla-sink. This is no longer the case and pulse worked with the default configuration. This was probably a workaround, at some point, pre 3.xx kernels.  This was using a 3.1 kernel.

As for the issue with the console frame buffer - I did notice a resolution change on tty sessions. I will look into this another time. I will blacklist the vesafb module.

Thanks!

---

