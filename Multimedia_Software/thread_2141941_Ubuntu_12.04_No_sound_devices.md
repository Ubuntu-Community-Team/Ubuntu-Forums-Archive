---
title: "Ubuntu 12.04 No sound devices"
date: 2013-05-04
forum: Multimedia Software
---

### Post by Inperpetuammemoriam on 2013-05-04
Hey guys!

Recently when I started my computer no sound devices where detected. I therefore tried several suggestions found on the web (e.g. reinstalling alsa), but none of them worked for me. Today, when I started my computer, the sound devices were displayed once more, but after restarting it, they were lost again (beside the "Dummy Output" which appeared today).

Please consider the following logs:

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L
```

default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 2
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 3
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 1
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 2
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 3
    Hardware device with all software conversions

```

dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-28-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 (Ubuntu 3.5.0-28.48~precise1-generic 3.5.7.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-28-generic root=UUID=**** (Masked by the author) ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000de537fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de538000-0x00000000dec27fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dec28000-0x00000000dee8efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dee8f000-0x00000000dee9afff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000dee9b000-0x00000000deea7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deea8000-0x00000000deeacfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000deead000-0x00000000deeeffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000deef0000-0x00000000df7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI:                  /DZ77SL-50K, BIOS SLZ7710H.86A.0055.2012.0319.2140 03/19/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x41f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FF0000000 write-back
[    0.000000]   2 base 410000000 mask FF8000000 write-back
[    0.000000]   3 base 418000000 mask FFC000000 write-back
[    0.000000]   4 base 41C000000 mask FFE000000 write-back
[    0.000000]   5 base 41E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 256MB, type WB
[    0.000000] reg 2, base: 16640MB, range: 128MB, type WB
[    0.000000] reg 3, base: 16768MB, range: 64MB, type WB
[    0.000000] reg 4, base: 16832MB, range: 32MB, type WB
[    0.000000] reg 5, base: 16864MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 7      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16880MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcca0-0x000fccaf] mapped at [ffff8800000fcca0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdf7fffff]
[    0.000000]  [mem 0x00000000-0xdf7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdf7fffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x41effffff]
[    0.000000]  [mem 0x100000000-0x41effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x41effffff @ [mem 0xdf7f2000-0xdf7fffff]
[    0.000000] RAMDISK: [mem 0x35578000-0x36ab3fff]
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 00000000dee8f070 00064 (v01  INTEL   DZ75SL 00000037 AMI  00010013)
[    0.000000] ACPI: FACP 00000000dee98b30 000F4 (v04 INTEL  DZ75SL   00000037 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000dee8f168 099C4 (v02 INTEL  DZ75SL   00000037 INTL 20051117)
[    0.000000] ACPI: FACS 00000000deea6f80 00040
[    0.000000] ACPI: APIC 00000000dee98c28 00072 (v03  INTEL   DZ75SL 00000037 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000dee98ca0 0003C (v01 INTEL  DZ75SL   00000037 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000dee98ce0 00038 (v01 INTEL  DZ75SL   00000037 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000dee98d18 0036D (v01 INTEL  DZ75SL   00000037 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000dee99088 009AA (v01 INTEL  DZ75SL   00000037 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000dee99a38 00A92 (v01 INTEL  DZ75SL   00000037 INTL 20051117)
[    0.000000] ACPI: DMAR 00000000dee9a4d0 00080 (v01 INTEL  DZ75SL   00000037 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x41effffff]
[    0.000000]   NODE_DATA [mem 0x41effc000-0x41effffff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040e600000-ffff88041e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x41effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xde537fff]
[    0.000000]   node   0: [mem 0xdeef0000-0xdf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x41effffff]
[    0.000000] On node 0 totalpages: 4185557
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 892552 pages, LIFO batch:31
[    0.000000]   Normal zone: 51136 pages used for memmap
[    0.000000]   Normal zone: 3221568 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000de538000 - 00000000dec28000
[    0.000000] PM: Registered nosave memory: 00000000dec28000 - 00000000dee8f000
[    0.000000] PM: Registered nosave memory: 00000000dee8f000 - 00000000dee9b000
[    0.000000] PM: Registered nosave memory: 00000000dee9b000 - 00000000deea8000
[    0.000000] PM: Registered nosave memory: 00000000deea8000 - 00000000deead000
[    0.000000] PM: Registered nosave memory: 00000000deead000 - 00000000deef0000
[    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88041ec00000 s83584 r8192 d22912 u524288
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4118031
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-28-generic root=UUID=**** (Masked by the author) ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16375916k/17285120k available (6820k kernel code, 542892k absent, 366312k reserved, 6347k data, 948k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3392.353 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.70 BogoMIPS (lpj=13569412)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000017] Security Framework initialized
[    0.000026] AppArmor: AppArmor initialized
[    0.000026] Yama: becoming mindful.
[    0.000689] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.003557] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004826] Mount-cache hash table entries: 256
[    0.004938] Initializing cgroup subsys cpuacct
[    0.004940] Initializing cgroup subsys memory
[    0.004945] Initializing cgroup subsys devices
[    0.004946] Initializing cgroup subsys freezer
[    0.004947] Initializing cgroup subsys blkio
[    0.004948] Initializing cgroup subsys perf_event
[    0.004966] CPU: Physical Processor ID: 0
[    0.004967] CPU: Processor Core ID: 0
[    0.005246] mce: CPU supports 9 MCE banks
[    0.005255] CPU0: Thermal monitoring enabled (TM1)
[    0.005260] using mwait in idle threads.
[    0.006775] ACPI: Core revision 20120320
[    0.010366] ftrace: allocating 27621 entries in 108 pages
[    0.019652] DMAR: Host address width 36
[    0.019654] DMAR: DRHD base: 0x000000fed90000 flags: 0x1
[    0.019660] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.019661] DMAR: RMRR base: 0x000000deb9d000 end: 0x000000debbbfff
[    0.019730] IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.019731] HPET id 0 under DRHD base 0xfed90000
[    0.019789] Enabled IRQ remapping in x2apic mode
[    0.019790] Enabling x2apic
[    0.019790] Enabled x2apic
[    0.019795] Switched APIC routing to cluster x2apic.
[    0.020219] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059790] CPU0: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz stepping 09
[    0.164542] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.164546] ... version:                3
[    0.164547] ... bit width:              48
[    0.164548] ... generic registers:      8
[    0.164548] ... value mask:             0000ffffffffffff
[    0.164549] ... max period:             000000007fffffff
[    0.164550] ... fixed-purpose events:   3
[    0.164550] ... event mask:             00000007000000ff
[    0.164638] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.175595] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.175595] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.164689] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.204727] Brought up 4 CPUs
[    0.204730] Total of 4 processors activated (27138.82 BogoMIPS).
[    0.207336] devtmpfs: initialized
[    0.208389] EVM: security.selinux
[    0.208390] EVM: security.SMACK64
[    0.208391] EVM: security.capability
[    0.208418] PM: Registering ACPI NVS region [mem 0xdec28000-0xdee8efff] (2519040 bytes)
[    0.208442] PM: Registering ACPI NVS region [mem 0xdee9b000-0xdeea7fff] (53248 bytes)
[    0.208443] PM: Registering ACPI NVS region [mem 0xdeead000-0xdeeeffff] (274432 bytes)
[    0.208902] dummy: 
[    0.208930] RTC time:  8:16:07, date: 05/04/13
[    0.208952] NET: Registered protocol family 16
[    0.209009] Trying to unpack rootfs image as initramfs...
[    0.209049] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.209050] ACPI: bus type pci registered
[    0.209084] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.209085] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.213632] PCI: Using configuration type 1 for base access
[    0.214195] bio: create slab <bio-0> at 0
[    0.214237] ACPI: Added _OSI(Module Device)
[    0.214238] ACPI: Added _OSI(Processor Device)
[    0.214239] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.214240] ACPI: Added _OSI(Processor Aggregator Device)
[    0.215172] ACPI: EC: Look up EC in DSDT
[    0.216157] ACPI: Executed 1 blocks of module-level executable AML code
[    0.236591] ACPI: SSDT 00000000debd5018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.236826] ACPI: Dynamic OEM Table Load:
[    0.236827] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.272390] ACPI: SSDT 00000000debd6a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.272641] ACPI: Dynamic OEM Table Load:
[    0.272643] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.292238] ACPI: SSDT 00000000debd7c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.292467] ACPI: Dynamic OEM Table Load:
[    0.292469] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.320423] ACPI: Interpreter enabled
[    0.320426] ACPI: (supports S0 S3 S4 S5)
[    0.320440] ACPI: Using IOAPIC for interrupt routing
[    0.323677] ACPI: Power Resource [FN00] (off)
[    0.323720] ACPI: Power Resource [FN01] (off)
[    0.323762] ACPI: Power Resource [FN02] (off)
[    0.323802] ACPI: Power Resource [FN03] (off)
[    0.323842] ACPI: Power Resource [FN04] (off)
[    0.324113] ACPI: No dock devices found.
[    0.324116] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.324311] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.324569] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.324570] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.324572] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.324573] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.324574] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.324575] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.324576] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.324577] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.324578] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.324580] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff]
[    0.324599] PCI host bridge to bus 0000:00
[    0.324600] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.324601] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.324602] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.324603] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.324604] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.324606] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.324607] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.324608] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.324609] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.324610] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.324616] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.324643] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.324665] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.324704] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.324725] pci 0000:00:14.0: reg 10: [mem 0xf7120000-0xf712ffff 64bit]
[    0.324791] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.324812] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.324833] pci 0000:00:16.0: reg 10: [mem 0xf713b000-0xf713b00f 64bit]
[    0.324903] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.324931] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.324948] pci 0000:00:19.0: reg 10: [mem 0xf7100000-0xf711ffff]
[    0.324956] pci 0000:00:19.0: reg 14: [mem 0xf7139000-0xf7139fff]
[    0.324964] pci 0000:00:19.0: reg 18: [io  0xf040-0xf05f]
[    0.325022] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.325045] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.325064] pci 0000:00:1a.0: reg 10: [mem 0xf7138000-0xf71383ff]
[    0.325149] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.325172] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.325186] pci 0000:00:1b.0: reg 10: [mem 0xf7130000-0xf7133fff 64bit]
[    0.325249] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.325275] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.325404] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.325442] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.325515] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.325542] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.325561] pci 0000:00:1d.0: reg 10: [mem 0xf7137000-0xf71373ff]
[    0.325645] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.325670] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.325786] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.325803] pci 0000:00:1f.2: reg 10: [io  0xf090-0xf097]
[    0.325810] pci 0000:00:1f.2: reg 14: [io  0xf080-0xf083]
[    0.325817] pci 0000:00:1f.2: reg 18: [io  0xf070-0xf077]
[    0.325824] pci 0000:00:1f.2: reg 1c: [io  0xf060-0xf063]
[    0.325832] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
[    0.325839] pci 0000:00:1f.2: reg 24: [mem 0xf7136000-0xf71367ff]
[    0.325881] pci 0000:00:1f.2: PME# supported from D3hot
[    0.325897] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.325911] pci 0000:00:1f.3: reg 10: [mem 0xf7135000-0xf71350ff 64bit]
[    0.325930] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.325978] pci 0000:01:00.0: [10de:11c0] type 00 class 0x030000
[    0.325986] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.325995] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
[    0.326004] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.326010] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.326016] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
[    0.326064] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
[    0.326072] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff]
[    0.332073] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.332075] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.332077] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.332079] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.332150] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.332258] pci 0000:03:00.0: [1283:8892] type 01 class 0x060401
[    0.332642] pci 0000:03:00.0: supports D1 D2
[    0.332643] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.332704] pci 0000:00:1c.7: PCI bridge to [bus 03-04]
[    0.332898] pci 0000:03:00.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.332931] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.332933] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.332934] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.332935] pci 0000:03:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.332966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.333042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.333067] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.333087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08.BR21._PRT]
[    0.333115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.333195]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.333312]  pci0000:00: ACPI _OSC control (0x18) granted
[    0.335488] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.335518] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.335547] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.335575] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.335604] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.335633] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.335663] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.335691] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.335748] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.335749] vgaarb: loaded
[    0.335750] vgaarb: bridge control possible 0000:01:00.0
[    0.335842] SCSI subsystem initialized
[    0.335870] libata version 3.00 loaded.
[    0.335881] ACPI: bus type usb registered
[    0.335891] usbcore: registered new interface driver usbfs
[    0.335896] usbcore: registered new interface driver hub
[    0.335907] usbcore: registered new device driver usb
[    0.335946] PCI: Using ACPI for IRQ routing
[    0.337352] PCI: pci_cache_line_size set to 64 bytes
[    0.337408] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.337409] e820: reserve RAM buffer [mem 0xde538000-0xdfffffff]
[    0.337410] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
[    0.337411] e820: reserve RAM buffer [mem 0x41f000000-0x41fffffff]
[    0.337466] NetLabel: Initializing
[    0.337467] NetLabel:  domain hash size = 128
[    0.337467] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.337475] NetLabel:  unlabeled traffic allowed by default
[    0.337525] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.337530] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.339536] Switching to clocksource hpet
[    0.343115] AppArmor: AppArmor Filesystem Enabled
[    0.343127] pnp: PnP ACPI init
[    0.343134] ACPI: bus type pnp registered
[    0.343299] pnp 00:00: [bus 00-3e]
[    0.343301] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.343302] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.343303] pnp 00:00: [io  0x0d00-0xffff window]
[    0.343305] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.343306] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.343307] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.343308] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.343309] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.343310] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.343311] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.343312] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.343313] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.343314] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.343315] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.343316] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.343317] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.343318] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.343320] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
[    0.343321] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    0.343359] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.343375] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.343398] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.343399] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.343406] pnp 00:02: [io  0x0000-0x001f]
[    0.343407] pnp 00:02: [io  0x0081-0x0091]
[    0.343408] pnp 00:02: [io  0x0093-0x009f]
[    0.343409] pnp 00:02: [io  0x00c0-0x00df]
[    0.343411] pnp 00:02: [dma 4]
[    0.343423] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.343428] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.343437] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.343483] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.343494] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.343501] pnp 00:05: [io  0x002e-0x002f]
[    0.343502] pnp 00:05: [io  0x004e-0x004f]
[    0.343503] pnp 00:05: [io  0x0061]
[    0.343504] pnp 00:05: [io  0x0063]
[    0.343505] pnp 00:05: [io  0x0065]
[    0.343505] pnp 00:05: [io  0x0067]
[    0.343506] pnp 00:05: [io  0x0070]
[    0.343507] pnp 00:05: [io  0x0080]
[    0.343508] pnp 00:05: [io  0x0092]
[    0.343509] pnp 00:05: [io  0x00b2-0x00b3]
[    0.343510] pnp 00:05: [io  0x0680-0x069f]
[    0.343511] pnp 00:05: [io  0x0200-0x020f]
[    0.343512] pnp 00:05: [io  0xffff]
[    0.343514] pnp 00:05: [io  0xffff]
[    0.343515] pnp 00:05: [io  0x0400-0x0453]
[    0.343516] pnp 00:05: [io  0x0458-0x047f]
[    0.343517] pnp 00:05: [io  0x0500-0x057f]
[    0.343518] pnp 00:05: [io  0x164e-0x164f]
[    0.343536] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.343537] system 00:05: [io  0x0200-0x020f] has been reserved
[    0.343539] system 00:05: [io  0xffff] has been reserved
[    0.343540] system 00:05: [io  0xffff] has been reserved
[    0.343541] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.343549] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.343551] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.343552] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.343553] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.343558] pnp 00:06: [io  0x0070-0x0077]
[    0.343568] pnp 00:06: [irq 8]
[    0.343579] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.343594] pnp 00:07: [io  0x0454-0x0457]
[    0.343610] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.343612] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.343656] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.343657] pnp 00:08: [io  0x0a30-0x0a3f]
[    0.343658] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.343659] pnp 00:08: [io  0x0250-0x025f]
[    0.343675] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    0.343676] system 00:08: [io  0x0250-0x025f] has been reserved
[    0.343678] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.343703] pnp 00:09: [io  0x0010-0x001f]
[    0.343704] pnp 00:09: [io  0x0022-0x003f]
[    0.343705] pnp 00:09: [io  0x0044-0x005f]
[    0.343706] pnp 00:09: [io  0x0062-0x0063]
[    0.343707] pnp 00:09: [io  0x0065-0x006f]
[    0.343708] pnp 00:09: [io  0x0072-0x007f]
[    0.343709] pnp 00:09: [io  0x0080]
[    0.343710] pnp 00:09: [io  0x0084-0x0086]
[    0.343711] pnp 00:09: [io  0x0088]
[    0.343712] pnp 00:09: [io  0x008c-0x008e]
[    0.343713] pnp 00:09: [io  0x0090-0x009f]
[    0.343714] pnp 00:09: [io  0x00a2-0x00bf]
[    0.343714] pnp 00:09: [io  0x00e0-0x00ef]
[    0.343715] pnp 00:09: [io  0x04d0-0x04d1]
[    0.343733] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.343735] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.343739] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.343745] pnp 00:0a: [irq 13]
[    0.343755] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.343919] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    0.343920] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    0.343921] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    0.343922] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    0.343923] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    0.343924] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    0.343925] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    0.343926] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    0.343927] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    0.343928] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    0.343929] pnp 00:0b: [mem 0xe0000000-0xe0000fff]
[    0.343959] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.343960] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.343961] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.343963] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.343964] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.343965] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.343966] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.343967] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.343969] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.343970] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.343971] system 00:0b: [mem 0xe0000000-0xe0000fff] has been reserved
[    0.343973] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.344051] pnp: PnP ACPI: found 12 devices
[    0.344052] ACPI: ACPI bus type pnp unregistered
[    0.349790] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.349793] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.349795] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.349797] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.349799] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.349816] pci 0000:03:00.0: PCI bridge to [bus 04-04]
[    0.349845] pci 0000:00:1c.7: PCI bridge to [bus 03-04]
[    0.349890] pci 0000:03:00.0: setting latency timer to 64
[    0.349895] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.349897] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.349898] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.349899] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.349900] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.349901] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.349902] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.349904] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.349905] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.349906] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.349907] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.349908] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.349910] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
[    0.349929] NET: Registered protocol family 2
[    0.350105] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.350656] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.351585] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.351698] TCP: Hash tables configured (established 524288 bind 65536)
[    0.351699] TCP: reno registered
[    0.351714] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.351754] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.351817] NET: Registered protocol family 1
[    0.391447] pci 0000:01:00.0: Boot video device
[    0.391460] PCI: CLS 64 bytes, default 64
[    0.391464] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.391465] software IO TLB [mem 0xda538000-0xde537fff] (64MB) mapped at [ffff8800da538000-ffff8800de537fff]
[    0.391766] audit: initializing netlink socket (disabled)
[    0.391772] type=2000 audit(1367655367.284:1): initialized
[    0.407889] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.409324] VFS: Disk quotas dquot_6.5.2
[    0.409346] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.409600] fuse init (API version 7.19)
[    0.409641] msgmni has been set to 31984
[    0.409881] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.409901] io scheduler noop registered
[    0.409902] io scheduler deadline registered (default)
[    0.409915] io scheduler cfq registered
[    0.409977] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.410116] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.410124] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.410148] intel_idle: MWAIT substates: 0x1120
[    0.410149] intel_idle: v0.4 model 0x3A
[    0.410150] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.410200] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.410203] ACPI: Power Button [PWRB]
[    0.410224] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.410226] ACPI: Power Button [PWRF]
[    0.410273] ACPI: Fan [FAN0] (off)
[    0.410288] ACPI: Fan [FAN1] (off)
[    0.410303] ACPI: Fan [FAN2] (off)
[    0.410318] ACPI: Fan [FAN3] (off)
[    0.410332] ACPI: Fan [FAN4] (off)
[    0.410368] ACPI: Requesting acpi_cpufreq
[    0.451566] Freeing initrd memory: 21744k freed
[    0.455556] thermal LNXTHERM:00: registered as thermal_zone0
[    0.455558] ACPI: Thermal Zone [TZ00] (28 C)
[    0.455656] thermal LNXTHERM:01: registered as thermal_zone1
[    0.455657] ACPI: Thermal Zone [TZ01] (30 C)
[    0.455679] GHES: HEST is not enabled!
[    0.455729] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.456420] Linux agpgart interface v0.103
[    0.457077] brd: module loaded
[    0.457412] loop: module loaded
[    0.457588] Fixed MDIO Bus: probed
[    0.457608] tun: Universal TUN/TAP device driver, 1.6
[    0.457609] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.457630] PPP generic driver version 2.4.2
[    0.457654] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.457688] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.457691] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.457695] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.457716] ehci_hcd 0000:00:1a.0: debug port 2
[    0.461603] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.461615] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7138000
[    0.471195] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.471218] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.471220] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.471223] usb usb1: Product: EHCI Host Controller
[    0.471225] usb usb1: Manufacturer: Linux 3.5.0-28-generic ehci_hcd
[    0.471227] usb usb1: SerialNumber: 0000:00:1a.0
[    0.471315] hub 1-0:1.0: USB hub found
[    0.471317] hub 1-0:1.0: 2 ports detected
[    0.471362] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.471364] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.471367] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.471383] ehci_hcd 0000:00:1d.0: debug port 2
[    0.475266] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.475275] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7137000
[    0.487152] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.487166] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.487169] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487171] usb usb2: Product: EHCI Host Controller
[    0.487173] usb usb2: Manufacturer: Linux 3.5.0-28-generic ehci_hcd
[    0.487175] usb usb2: SerialNumber: 0000:00:1d.0
[    0.487255] hub 2-0:1.0: USB hub found
[    0.487257] hub 2-0:1.0: 2 ports detected
[    0.487288] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.487296] uhci_hcd: USB Universal Host Controller Interface driver
[    0.487324] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.487327] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.487329] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.487410] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.487449] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.487482] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.487483] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487484] usb usb3: Product: xHCI Host Controller
[    0.487485] usb usb3: Manufacturer: Linux 3.5.0-28-generic xhci_hcd
[    0.487486] usb usb3: SerialNumber: 0000:00:14.0
[    0.487529] xHCI xhci_add_endpoint called for root hub
[    0.487530] xHCI xhci_check_bandwidth called for root hub
[    0.487542] hub 3-0:1.0: USB hub found
[    0.487548] hub 3-0:1.0: 4 ports detected
[    0.487581] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.487583] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.487599] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.487600] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.487601] usb usb4: Product: xHCI Host Controller
[    0.487602] usb usb4: Manufacturer: Linux 3.5.0-28-generic xhci_hcd
[    0.487603] usb usb4: SerialNumber: 0000:00:14.0
[    0.487640] xHCI xhci_add_endpoint called for root hub
[    0.487641] xHCI xhci_check_bandwidth called for root hub
[    0.487650] hub 4-0:1.0: USB hub found
[    0.487656] hub 4-0:1.0: 4 ports detected
[    0.487731] usbcore: registered new interface driver libusual
[    0.487750] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.490918] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.490922] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.490976] mousedev: PS/2 mouse device common for all mice
[    0.491044] rtc_cmos 00:06: RTC can wake from S4
[    0.491167] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.491191] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.491229] device-mapper: uevent: version 1.0.3
[    0.491267] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.491303] cpuidle: using governor ladder
[    0.491349] cpuidle: using governor menu
[    0.491350] EFI Variables Facility v0.08 2004-May-17
[    0.491492] ashmem: initialized
[    0.491560] TCP: cubic registered
[    0.491612] NET: Registered protocol family 10
[    0.491713] NET: Registered protocol family 17
[    0.491719] Key type dns_resolver registered
[    0.491850] PM: Hibernation image not present or could not be loaded.
[    0.491860] registered taskstats version 1
[    0.493837] Key type trusted registered
[    0.495210] Key type encrypted registered
[    0.497234]   Magic number: 13:857:269
[    0.497362] rtc_cmos 00:06: setting system clock to 2013-05-04 08:16:08 UTC (1367655368)
[    0.497931] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.497932] EDD information not available.
[    0.498822] Freeing unused kernel memory: 948k freed
[    0.498894] Write protecting the kernel read-only data: 12288k
[    0.501093] Freeing unused kernel memory: 1360k freed
[    0.502932] Freeing unused kernel memory: 1064k freed
[    0.512759] udevd[101]: starting version 175
[    0.525691] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    0.525694] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.525790] e1000e 0000:00:19.0: setting latency timer to 64
[    0.525898] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.525928] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    0.782309] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    0.787572] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1e:8c:f4:60:82
[    0.787574] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    0.787611] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    0.787664] ahci 0000:00:1f.2: version 3.0
[    0.787753] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    0.787783] ahci: SSS flag set, parallel bus scan disabled
[    0.802292] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x2b impl SATA mode
[    0.802298] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    0.802305] ahci 0000:00:1f.2: setting latency timer to 64
[    0.826572] scsi0 : ahci
[    0.826731] scsi1 : ahci
[    0.826881] scsi2 : ahci
[    0.827039] scsi3 : ahci
[    0.827181] scsi4 : ahci
[    0.827317] scsi5 : ahci
[    0.827487] ata1: SATA max UDMA/133 abar m2048@0xf7136000 port 0xf7136100 irq 44
[    0.827489] ata2: SATA max UDMA/133 abar m2048@0xf7136000 port 0xf7136180 irq 44
[    0.827490] ata3: DUMMY
[    0.827492] ata4: SATA max UDMA/133 abar m2048@0xf7136000 port 0xf7136280 irq 44
[    0.827493] ata5: DUMMY
[    0.827495] ata6: SATA max UDMA/133 abar m2048@0xf7136000 port 0xf7136380 irq 44
[    0.914407] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    0.914412] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.914788] hub 1-1:1.0: USB hub found
[    0.914880] hub 1-1:1.0: 6 ports detected
[    1.025634] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.145295] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.156791] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.156797] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.156800] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.157571] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.157575] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.157854] hub 2-1:1.0: USB hub found
[    1.157944] hub 2-1:1.0: 8 ports detected
[    1.166804] ata1.00: ATA-8: KINGSTON SV300S37A120G, 505ABBF0, max UDMA/133
[    1.166809] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.176799] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.176805] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.176808] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.187183] ata1.00: configured for UDMA/133
[    1.187407] scsi 0:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 505A PQ: 0 ANSI: 5
[    1.187515] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.187536] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.187570] sd 0:0:0:0: [sda] Write Protect is off
[    1.187572] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.187606] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.187890]  sda: sda1 sda2
[    1.188149] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.229247] usb 1-1.6: new full-speed USB device number 3 using ehci_hcd
[    1.322985] usb 1-1.6: New USB device found, idVendor=09da, idProduct=9090
[    1.322990] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.322992] usb 1-1.6: Product: USB Device
[    1.322995] usb 1-1.6: Manufacturer: A4TECH
[    1.388589] Refined TSC clocksource calibration: 3392.293 MHz.
[    1.388595] Switching to clocksource tsc
[    1.428704] usb 2-1.7: new low-speed USB device number 3 using ehci_hcd
[    1.504260] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.515819] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.515825] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.515828] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.526164] ata2.00: ATA-8: KINGSTON SV300S37A120G, 505ABBF0, max UDMA/133
[    1.526168] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.535718] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.535724] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.535727] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.539983] usb 2-1.7: New USB device found, idVendor=04d9, idProduct=1702
[    1.539987] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.539990] usb 2-1.7: Product: USB Keyboard
[    1.539992] usb 2-1.7: Manufacturer:  
[    1.546111] ata2.00: configured for UDMA/133
[    1.546310] scsi 1:0:0:0: Direct-Access     ATA      KINGSTON SV300S3 505A PQ: 0 ANSI: 5
[    1.546479] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.546539] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.546612] sd 1:0:0:0: [sdb] Write Protect is off
[    1.546614] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.546621] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.547173]  sdb: sdb1 sdb2 < sdb5 >
[    1.547505] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.569736] usbcore: registered new interface driver usbhid
[    1.569740] usbhid: USB HID core driver
[    1.863233] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.863933] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.863938] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.863942] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.864527] ata4.00: ATA-8: ST3000DM001-1CH166, CC24, max UDMA/133
[    1.864532] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.865223] ata4.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.865229] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.865232] ata4.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.865825] ata4.00: configured for UDMA/133
[    1.865953] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC24 PQ: 0 ANSI: 5
[    1.866050] sd 3:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.866052] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    1.866054] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.866116] sd 3:0:0:0: [sdc] Write Protect is off
[    1.866117] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.866125] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.905693]  sdc: sdc1
[    1.905887] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.182319] ata6: SATA link down (SStatus 0 SControl 300)
[    2.185014] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input2
[    2.185151] hid-generic 0003:09DA:9090.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:1a.0-1.6/input0
[    2.185282] input: A4TECH USB Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input3
[    2.185394] hid-generic 0003:09DA:9090.0002: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:1a.0-1.6/input1
[    2.185534] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input4
[    2.185619] hid-generic 0003:04D9:1702.0003: input,hidraw2: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-1.7/input0
[    2.189023] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.1/input/input5
[    2.189144] hid-generic 0003:04D9:1702.0004: input,hidraw3: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-1.7/input1
[    3.310075] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    3.310077] vesafb: scrolling: redraw
[    3.310079] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.311864] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90006680000, using 1216k, total 1216k
[    3.311982] Console: switching to colour frame buffer device 80x30
[    3.311989] fb0: VESA VGA frame buffer device
[    8.382290] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    8.499936] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    8.517893] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.524147] udevd[460]: starting version 175
[    8.548825] lp: driver loaded but no devices found
[    8.553535] scsi6 : vhba
[    8.577254] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.577259] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.577260] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    8.577263] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.577264] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.577267] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    8.577269] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.577269] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.578835] mei 0000:00:16.0: setting latency timer to 64
[    8.579372] mei 0000:00:16.0: irq 45 for MSI/MSI-X
[    8.586192] mei 0000:00:16.0: wd: failed to find the client
[    8.597878] ppdev: user-space parallel port driver
[    8.607627] Bluetooth: Core ver 2.16
[    8.607637] NET: Registered protocol family 31
[    8.607638] Bluetooth: HCI device and connection manager initialized
[    8.607639] Bluetooth: HCI socket layer initialized
[    8.607640] Bluetooth: L2CAP socket layer initialized
[    8.607642] Bluetooth: SCO socket layer initialized
[    8.608253] type=1400 audit(1367655376.631:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
[    8.608493] type=1400 audit(1367655376.631:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=691 comm="apparmor_parser"
[    8.608624] type=1400 audit(1367655376.631:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=691 comm="apparmor_parser"
[    8.620033] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0xc
[    8.620192] Bluetooth: RFCOMM TTY layer initialized
[    8.620194] Bluetooth: RFCOMM socket layer initialized
[    8.620195] Bluetooth: RFCOMM ver 1.11
[    8.628710] type=1400 audit(1367655376.651:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=747 comm="apparmor_parser"
[    8.628988] type=1400 audit(1367655376.651:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=747 comm="apparmor_parser"
[    8.630442] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.630445] Bluetooth: BNEP filters: protocol multicast
[    8.667574] nvidia: module license 'NVIDIA' taints kernel.
[    8.667576] Disabling lock debugging due to kernel taint
[    8.677432] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.677497] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
[    8.690593] init: failsafe main process (896) killed by TERM signal
[    8.691208] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    8.711541] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0xc
[    8.712498] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0xc
[    8.713430] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0xc
[    8.714193] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.719651] hda-intel: no codecs found!
[    8.719754] hda_intel: Disabling MSI
[    8.719761] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[    8.740531] type=1400 audit(1367655376.763:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1060 comm="apparmor_parser"
[    8.740767] type=1400 audit(1367655376.763:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1060 comm="apparmor_parser"
[    8.740777] type=1400 audit(1367655376.763:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1059 comm="apparmor_parser"
[    8.740900] type=1400 audit(1367655376.763:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1060 comm="apparmor_parser"
[    8.742966] type=1400 audit(1367655376.763:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1064 comm="apparmor_parser"
[    8.794452] init: alsa-restore main process (1108) terminated with status 19
[    8.814191] init: gdm main process (1137) killed by TERM signal
[    8.829831] vboxdrv: Found 4 processor cores.
[    8.829939] vboxdrv: fAsync=0 offMin=0x1bd offMax=0x8d41
[    8.829982] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    8.829983] vboxdrv: Successfully loaded version 4.2.10 (interface 0x001a0004).
[    8.925298] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.026845] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    9.027602] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.027792] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.034906] vboxpci: IOMMU not found (not registered)
[    9.317966] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input6
[    9.318081] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input7
[    9.318221] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input8
[    9.318354] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input9
[    9.561277] NVRM: Your system is not currently configured to drive a VGA console
[    9.561280] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[    9.561281] NVRM: requires the use of a text-mode VGA console. Use of other console
[    9.561282] NVRM: drivers including, but not limited to, vesafb, may result in
[    9.561282] NVRM: corruption and stability problems, and is not supported.
[   10.549232] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   10.549236] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   10.549920] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.376594] audit_printk_skb: 36 callbacks suppressed
[   34.376597] type=1400 audit(1367655402.463:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2287 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
[  312.654451] type=1400 audit(1367655681.400:25): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=803 comm="cupsd" pid=803 comm="cupsd" capability=36  capname="block_suspend"
[  859.201703] type=1400 audit(1367656229.384:26): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=803 comm="cupsd" pid=803 comm="cupsd" capability=36  capname="block_suspend"
[ 1997.092816] type=1400 audit(1367657370.528:27): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=803 comm="cupsd" pid=803 comm="cupsd" capability=36  capname="block_suspend"

```

[I]lsmod
[/I]```

Module                  Size  Used by
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_crypt               23126  0 
pci_stub               12623  1 
vboxpci                23237  0 
vboxnetadp             25671  0 
vboxnetflt             23479  0 
snd_hda_codec_hdmi     32476  1 
vboxdrv               320186  3 vboxpci,vboxnetadp,vboxnetflt
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
snd_hda_intel          34063  1 
snd_hda_codec         135141  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia              11309216  41 
joydev                 17694  0 
snd_timer              29990  2 snd_seq,snd_pcm
psmouse               102075  0 
bnep                   18240  2 
serio_raw              13216  0 
snd                    83674  11 snd_rawmidi,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
rfcomm                 47562  0 
microcode              23030  0 
bluetooth             211812  10 bnep,rfcomm
parport_pc             32867  0 
ppdev                  17114  0 
mac_hid                13254  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mei                    41410  0 
lpc_ich                17145  0 
vhba                   17398  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
vesafb                 13846  1 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
video                  19653  0 
ghash_clmulni_intel    13221  0 
aesni_intel            51134  1 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
ahci                   25869  1 
libahci                27338  1 ahci
e1000e                198734  0 

```
[I]lspci
[/I]```

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 11c0 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e0b (rev a1)
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)

```
pactl list
```

Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "2.0"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "2.0"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "2.0"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "2.0"

Module #4
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "2.0"

Module #5
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "2.0"

Module #6
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "2.0"

Module #7
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "2.0"

Module #8
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
        module.version = "2.0"

Module #9
    Name: module-null-sink
    Argument: sink_name=auto_null sink_properties='device.description="Dummy Output"'
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Clocked NULL sink"
        module.version = "2.0"

Module #10
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "2.0"

Module #11
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based of intended roles of devices"
        module.version = "2.0"

Module #12
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "2.0"

Module #13
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "2.0"

Module #14
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "2.0"

Module #15
    Name: module-filter-heuristics
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "2.0"

Module #16
    Name: module-filter-apply
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "2.0"

Module #17
    Name: module-switch-on-port-available
    Argument: 
    Usage counter: n/a
    Properties:
        

Module #18
    Name: module-cli-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Command line interface protocol (UNIX sockets)"
        module.version = "2.0"

Sink #0
    State: SUSPENDED
    Name: auto_null
    Description: Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 9
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: auto_null.monitor
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"
    Formats:
        pcm

Source #0
    State: SUSPENDED
    Name: auto_null.monitor
    Description: Monitor of Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 9
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor of Sink: auto_null
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Dummy Output"
        device.class = "monitor"
        device.icon_name = "audio-input-microphone"
    Formats:
        pcm

Client #0
    Driver: module-console-kit.c
    Owner Module: 13
    Properties:
        application.name = "ConsoleKit Session /org/freedesktop/ConsoleKit/Session2"
        console-kit.session = "/org/freedesktop/ConsoleKit/Session2"

Client #1
    Driver: protocol-native.c
    Owner Module: 6
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "3.4.2"
        application.process.id = "1930"
        application.process.user = "***** (Masked by the author)"
        application.process.host = "***** (Masked by the author)"
        application.process.binary = "gnome-settings-daemon"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "***** (Masked by the author)"
        application.process.session_id = "***** (Masked by the author)"

Client #10
    Driver: protocol-native.c
    Owner Module: 6
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "26"
        application.process.id = "5327"
        application.process.user = "***** (Masked by the author)"
        application.process.host = "***** (Masked by the author)"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "***** (Masked by the author)"
        application.process.session_id = "***** (Masked by the author)"

Card #0
    Name: alsa_card.pci-0000_01_00.1
    Driver: module-alsa-card.c
    Owner Module: 4
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.string = "0"
        device.description = "HDA NVidia"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 300)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5200)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 100)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: off
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, not available)
            Part of profile(s): output:hdmi-stereo, output:hdmi-surround
        hdmi-output-1: HDMI / DisplayPort 2 (priority: 5800, not available)
            Part of profile(s): output:hdmi-stereo-extra1, output:hdmi-surround-extra1
        hdmi-output-2: HDMI / DisplayPort 3 (priority: 5700, not available)
            Part of profile(s): output:hdmi-stereo-extra2, output:hdmi-surround-extra2
        hdmi-output-3: HDMI / DisplayPort 4 (priority: 5600, not available)
            Part of profile(s): output:hdmi-stereo-extra3, output:hdmi-surround-extra3

```

pactl list sinks
```

Sink #0
    State: SUSPENDED
    Name: auto_null
    Description: Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 9
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    Base Volume: 100%
                 0.00 dB
    Monitor Source: auto_null.monitor
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"
    Formats:
        pcm

```

Obviously, my mainboard's sound hasn't been detected, in contrast to my graphic card's.

Additionally, my sound shortcut on the menu bar in the top right corner disappeared. I couldn't restore it either.

Many thanks in advance for your help!

---

