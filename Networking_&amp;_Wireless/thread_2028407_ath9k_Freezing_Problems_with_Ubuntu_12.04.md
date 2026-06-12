---
title: "ath9k Freezing Problems with Ubuntu 12.04"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by sjb300 on 2012-07-18
I am currently running Ubuntu 12.04 64-bit with a TP-Link TL-WN851ND wireless card. Every time I start up, anywhere between 0 and 60 seconds after the login screen appears, the computer freezes permanently and I am forced to power off. I managed to isolate the problem to the ath9k module, so I blacklisted ath9k and everything is running smoothly... Except now I can't use my wifi card.

Is there a way to fix ath9k? Or are there alternative drivers I can install?
Thanks.

---

### Post by wnelson on 2012-07-18
When you have the ath9k loaded what is the output from dmesg?

---

### Post by sjb300 on 2012-07-18
dmesg output shortly before the freeze with ath9k loaded:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-26-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 (Ubuntu 3.2.0-26.41-generic 3.2.19)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.2.0-26-generic root=UUID=f4ca5a0e-7418-45e5-b575-8d74c9acca9f ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
[    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
[    0.000000]  BIOS-e820: 0000000040005000 - 00000000d98d7000 (usable)
[    0.000000]  BIOS-e820: 00000000d98d7000 - 00000000da031000 (reserved)
[    0.000000]  BIOS-e820: 00000000da031000 - 00000000da2b1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da2b1000 - 00000000da2b6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000da2b6000 - 00000000da2f9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000da2f9000 - 00000000dac6d000 (usable)
[    0.000000]  BIOS-e820: 00000000dac6d000 - 00000000dafd9000 (reserved)
[    0.000000]  BIOS-e820: 00000000dafd9000 - 00000000db000000 (usable)
[    0.000000]  BIOS-e820: 00000000db800000 - 00000000dfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000021f600000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./Z77-D3H, BIOS F8 02/21/2012
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x21f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   5 base 21F800000 mask FFF800000 uncachable
[    0.000000]   6 base 21F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 5, base: 8696MB, range: 8MB, type UC
[    0.000000] reg 6, base: 8694MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8110M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 9  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8694MB, range: 2MB, type UC
[    0.000000] reg 8, base: 8696MB, range: 8MB, type UC
[    0.000000] e820 update range: 00000000db800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcb50] fcb50
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000db000000
[    0.000000]  0000000000 - 00db000000 page 2M
[    0.000000] kernel direct mapping tables up to db000000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000021f600000
[    0.000000]  0100000000 - 021f600000 page 2M
[    0.000000] kernel direct mapping tables up to 21f600000 @ daff6000-db000000
[    0.000000] RAMDISK: 364da000 - 37265000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000da298078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000da2a1b00 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000da298178 09985 (v02 ALASKA    A M I 00000012 INTL 20051117)
[    0.000000] ACPI: FACS 00000000da2aff80 00040
[    0.000000] ACPI: APIC 00000000da2a1bf8 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000da2a1c90 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000da2a1cd0 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000da2a1d08 00460 (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000da2a2168 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000da2a2b18 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 00000000da2a35b0 000B8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: BGRT 00000000da2a3668 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000021f600000
[    0.000000] Initmem setup node 0 0000000000000000-000000021f600000
[    0.000000]   NODE_DATA [000000021f5fb000 - 000000021f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216c00000-ffff88021ebfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0021f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040004
[    0.000000]     0: 0x00040005 -> 0x000d98d7
[    0.000000]     0: 0x000da2f9 -> 0x000dac6d
[    0.000000]     0: 0x000dafd9 -> 0x000db000
[    0.000000]     0: 0x00100000 -> 0x0021f600
[    0.000000] On node 0 totalpages: 2070015
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 872625 pages, LIFO batch:31
[    0.000000]   Normal zone: 18392 pages used for memmap
[    0.000000]   Normal zone: 1158696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
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
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000d98d7000 - 00000000da031000
[    0.000000] PM: Registered nosave memory: 00000000da031000 - 00000000da2b1000
[    0.000000] PM: Registered nosave memory: 00000000da2b1000 - 00000000da2b6000
[    0.000000] PM: Registered nosave memory: 00000000da2b6000 - 00000000da2f9000
[    0.000000] PM: Registered nosave memory: 00000000dac6d000 - 00000000dafd9000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
[    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
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
[    0.000000] Allocating PCI resources starting at dfa00000 (gap: dfa00000:18600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f200000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2035234
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-26-generic root=UUID=f4ca5a0e-7418-45e5-b575-8d74c9acca9f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8052320k/8902656k available (6555k kernel code, 622596k absent, 227740k reserved, 6645k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3430.297 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6860.59 BogoMIPS (lpj=13721188)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000028] AppArmor: AppArmor initialized
[    0.000029] Yama: becoming mindful.
[    0.000500] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001971] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002594] Mount-cache hash table entries: 256
[    0.002665] Initializing cgroup subsys cpuacct
[    0.002667] Initializing cgroup subsys memory
[    0.002672] Initializing cgroup subsys devices
[    0.002674] Initializing cgroup subsys freezer
[    0.002675] Initializing cgroup subsys blkio
[    0.002678] Initializing cgroup subsys perf_event
[    0.002697] CPU: Physical Processor ID: 0
[    0.002697] CPU: Processor Core ID: 0
[    0.002701] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002701] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002961] mce: CPU supports 9 MCE banks
[    0.002971] CPU0: Thermal monitoring enabled (TM1)
[    0.002977] using mwait in idle threads.
[    0.004382] ACPI: Core revision 20110623
[    0.012088] ftrace: allocating 26991 entries in 106 pages
[    0.018084] DMAR: Host address width 36
[    0.018085] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.018091] IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.018092] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.018096] IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.018097] DMAR: RMRR base: 0x000000d9fa8000 end: 0x000000d9fc4fff
[    0.018098] DMAR: RMRR base: 0x000000db800000 end: 0x000000df9fffff
[    0.018168] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.018169] HPET id 0 under DRHD base 0xfed91000
[    0.018284] Enabled IRQ remapping in x2apic mode
[    0.018285] Enabling x2apic
[    0.018285] Enabled x2apic
[    0.018289] Switched APIC routing to cluster x2apic.
[    0.018685] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058300] CPU0: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz stepping 09
[    0.164508] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
[    0.164512] ... version:                3
[    0.164513] ... bit width:              48
[    0.164513] ... generic registers:      4
[    0.164514] ... value mask:             0000ffffffffffff
[    0.164515] ... max period:             000000007fffffff
[    0.164516] ... fixed-purpose events:   3
[    0.164517] ... event mask:             000000070000000f
[    0.164617] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164669] Booting Node   0, Processors  #1
[    0.164671] smpboot cpu 1: start_ip = 99000
[    0.272709] NMI watchdog enabled, takes one hw-pmu counter.
[    0.272766]  #2
[    0.272767] smpboot cpu 2: start_ip = 99000
[    0.380502] NMI watchdog enabled, takes one hw-pmu counter.
[    0.380557]  #3
[    0.380557] smpboot cpu 3: start_ip = 99000
[    0.488292] NMI watchdog enabled, takes one hw-pmu counter.
[    0.488347]  #4
[    0.488348] smpboot cpu 4: start_ip = 99000
[    0.596082] NMI watchdog enabled, takes one hw-pmu counter.
[    0.596146]  #5
[    0.596147] smpboot cpu 5: start_ip = 99000
[    0.703884] NMI watchdog enabled, takes one hw-pmu counter.
[    0.703941]  #6
[    0.703942] smpboot cpu 6: start_ip = 99000
[    0.811677] NMI watchdog enabled, takes one hw-pmu counter.
[    0.811731]  #7 Ok.
[    0.811732] smpboot cpu 7: start_ip = 99000
[    0.919567] NMI watchdog enabled, takes one hw-pmu counter.
[    0.919589] Brought up 8 CPUs
[    0.919590] Total of 8 processors activated (54881.68 BogoMIPS).
[    0.926483] devtmpfs: initialized
[    0.927011] EVM: security.selinux
[    0.927012] EVM: security.SMACK64
[    0.927013] EVM: security.capability
[    0.927028] PM: Registering ACPI NVS region at da031000 (2621440 bytes)
[    0.927052] PM: Registering ACPI NVS region at da2b6000 (274432 bytes)
[    0.927532] print_constraints: dummy: 
[    0.927558] RTC time: 23:09:26, date: 07/18/12
[    0.927577] NET: Registered protocol family 16
[    0.927640] Trying to unpack rootfs image as initramfs...
[    0.927642] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.927644] ACPI: bus type pci registered
[    0.927680] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.927682] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.937095] PCI: Using configuration type 1 for base access
[    0.937627] bio: create slab <bio-0> at 0
[    0.937672] ACPI: Added _OSI(Module Device)
[    0.937674] ACPI: Added _OSI(Processor Device)
[    0.937675] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.937676] ACPI: Added _OSI(Processor Aggregator Device)
[    0.938648] ACPI: EC: Look up EC in DSDT
[    0.939759] ACPI: Executed 1 blocks of module-level executable AML code
[    0.983302] ACPI: SSDT 00000000d9fd9018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.983547] ACPI: Dynamic OEM Table Load:
[    0.983549] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.007131] ACPI: SSDT 00000000d9fdaa98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.007391] ACPI: Dynamic OEM Table Load:
[    1.007393] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.031005] ACPI: SSDT 00000000d9fd8d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.031247] ACPI: Dynamic OEM Table Load:
[    1.031249] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.055652] ACPI: Interpreter enabled
[    1.055655] ACPI: (supports S0 S3 S4 S5)
[    1.055669] ACPI: Using IOAPIC for interrupt routing
[    1.059120] ACPI: Power Resource [FN00] (off)
[    1.059164] ACPI: Power Resource [FN01] (off)
[    1.059207] ACPI: Power Resource [FN02] (off)
[    1.059251] ACPI: Power Resource [FN03] (off)
[    1.059293] ACPI: Power Resource [FN04] (off)
[    1.059574] ACPI: No dock devices found.
[    1.059575] HEST: Table not found.
[    1.059577] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.059768] \_SB_.PCI0:_OSC invalid UUID
[    1.059769] _OSC request data:1 8 1f 
[    1.059772] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.060066] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.060068] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.060069] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.060070] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.060072] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.060073] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.060074] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.060075] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.060077] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.060078] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
[    1.060079] pci_root PNP0A08:00: host bridge window [mem 0x21f600000-0xfffffffff]
[    1.060088] pci 0000:00:00.0: [8086:0150] type 0 class 0x000600
[    1.060114] pci 0000:00:02.0: [8086:0162] type 0 class 0x000300
[    1.060122] pci 0000:00:02.0: reg 10: [mem 0xf7800000-0xf7bfffff 64bit]
[    1.060127] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.060131] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    1.060172] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
[    1.060192] pci 0000:00:14.0: reg 10: [mem 0xf7f00000-0xf7f0ffff 64bit]
[    1.060257] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.060260] pci 0000:00:14.0: PME# disabled
[    1.060278] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
[    1.060298] pci 0000:00:16.0: reg 10: [mem 0xf7f19000-0xf7f1900f 64bit]
[    1.060366] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.060369] pci 0000:00:16.0: PME# disabled
[    1.060396] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
[    1.060415] pci 0000:00:1a.0: reg 10: [mem 0xf7f17000-0xf7f173ff]
[    1.060498] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.060501] pci 0000:00:1a.0: PME# disabled
[    1.060521] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
[    1.060534] pci 0000:00:1b.0: reg 10: [mem 0xf7f10000-0xf7f13fff 64bit]
[    1.060595] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.060597] pci 0000:00:1b.0: PME# disabled
[    1.060615] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
[    1.060686] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.060689] pci 0000:00:1c.0: PME# disabled
[    1.060713] pci 0000:00:1c.5: [8086:244e] type 1 class 0x000604
[    1.060784] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.060787] pci 0000:00:1c.5: PME# disabled
[    1.060806] pci 0000:00:1c.6: [8086:1e1c] type 1 class 0x000604
[    1.060877] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    1.060880] pci 0000:00:1c.6: PME# disabled
[    1.060900] pci 0000:00:1c.7: [8086:1e1e] type 1 class 0x000604
[    1.060971] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    1.060974] pci 0000:00:1c.7: PME# disabled
[    1.060997] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
[    1.061015] pci 0000:00:1d.0: reg 10: [mem 0xf7f16000-0xf7f163ff]
[    1.061097] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.061101] pci 0000:00:1d.0: PME# disabled
[    1.061120] pci 0000:00:1f.0: [8086:1e44] type 0 class 0x000601
[    1.061231] pci 0000:00:1f.2: [8086:1e00] type 0 class 0x000101
[    1.061244] pci 0000:00:1f.2: reg 10: [io  0xf110-0xf117]
[    1.061250] pci 0000:00:1f.2: reg 14: [io  0xf100-0xf103]
[    1.061257] pci 0000:00:1f.2: reg 18: [io  0xf0f0-0xf0f7]
[    1.061263] pci 0000:00:1f.2: reg 1c: [io  0xf0e0-0xf0e3]
[    1.061270] pci 0000:00:1f.2: reg 20: [io  0xf0d0-0xf0df]
[    1.061276] pci 0000:00:1f.2: reg 24: [io  0xf0c0-0xf0cf]
[    1.061315] pci 0000:00:1f.3: [8086:1e22] type 0 class 0x000c05
[    1.061328] pci 0000:00:1f.3: reg 10: [mem 0xf7f15000-0xf7f150ff 64bit]
[    1.061347] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    1.061375] pci 0000:00:1f.5: [8086:1e08] type 0 class 0x000101
[    1.061388] pci 0000:00:1f.5: reg 10: [io  0xf0b0-0xf0b7]
[    1.061394] pci 0000:00:1f.5: reg 14: [io  0xf0a0-0xf0a3]
[    1.061401] pci 0000:00:1f.5: reg 18: [io  0xf090-0xf097]
[    1.061407] pci 0000:00:1f.5: reg 1c: [io  0xf080-0xf083]
[    1.061414] pci 0000:00:1f.5: reg 20: [io  0xf070-0xf07f]
[    1.061420] pci 0000:00:1f.5: reg 24: [io  0xf060-0xf06f]
[    1.061494] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.061563] pci 0000:02:00.0: [1283:8892] type 1 class 0x000604
[    1.061716] pci 0000:02:00.0: supports D1 D2
[    1.061717] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.061723] pci 0000:02:00.0: PME# disabled
[    1.061746] pci 0000:00:1c.5: PCI bridge to [bus 02-03] (subtractive decode)
[    1.061751] pci 0000:00:1c.5:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.061756] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.061757] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.061759] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.061760] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.061761] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.061763] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.061764] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.061765] pci 0000:00:1c.5:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.061767] pci 0000:00:1c.5:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.061768] pci 0000:00:1c.5:   bridge window [mem 0xdfa00000-0xfeafffff] (subtractive decode)
[    1.061770] pci 0000:00:1c.5:   bridge window [mem 0x21f600000-0xfffffffff] (subtractive decode)
[    1.061854] pci 0000:03:00.0: [168c:002d] type 0 class 0x000280
[    1.061889] pci 0000:03:00.0: reg 10: [mem 0xf7e00000-0xf7e0ffff]
[    1.062057] pci 0000:03:00.0: PME# supported from D0 D3hot
[    1.062063] pci 0000:03:00.0: PME# disabled
[    1.062155] pci 0000:02:00.0: PCI bridge to [bus 03-03] (subtractive decode)
[    1.062171] pci 0000:02:00.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.062181] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.062183] pci 0000:02:00.0:   bridge window [mem 0xf7e00000-0xf7efffff] (subtractive decode)
[    1.062185] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.062187] pci 0000:02:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    1.062188] pci 0000:02:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.062189] pci 0000:02:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.062191] pci 0000:02:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.062192] pci 0000:02:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    1.062193] pci 0000:02:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    1.062195] pci 0000:02:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    1.062196] pci 0000:02:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    1.062197] pci 0000:02:00.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    1.062199] pci 0000:02:00.0:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    1.062200] pci 0000:02:00.0:   bridge window [mem 0xdfa00000-0xfeafffff] (subtractive decode)
[    1.062202] pci 0000:02:00.0:   bridge window [mem 0x21f600000-0xfffffffff] (subtractive decode)
[    1.062274] pci 0000:04:00.0: [1969:1083] type 0 class 0x000200
[    1.062300] pci 0000:04:00.0: reg 10: [mem 0xf7d00000-0xf7d3ffff 64bit]
[    1.062314] pci 0000:04:00.0: reg 18: [io  0xe000-0xe07f]
[    1.062435] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.062439] pci 0000:04:00.0: PME# disabled
[    1.066897] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    1.066900] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    1.066903] pci 0000:00:1c.6:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.066967] pci 0000:05:00.0: [1b6f:7023] type 0 class 0x000c03
[    1.066991] pci 0000:05:00.0: reg 10: [mem 0xf7c00000-0xf7c07fff 64bit]
[    1.067111] pci 0000:05:00.0: supports D1 D2
[    1.067112] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.067116] pci 0000:05:00.0: PME# disabled
[    1.074880] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
[    1.074885] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.074907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.074982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.075005] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.075024] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.075044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    1.075109] \_SB_.PCI0:_OSC invalid UUID
[    1.075110] _OSC request data:1 1f 1f 
[    1.075113]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.075138] \_SB_.PCI0:_OSC invalid UUID
[    1.075139] _OSC request data:1 0 1d 
[    1.075141]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.075142] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.077767] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.077795] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.077822] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.077849] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.077876] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.077903] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.077931] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.077958] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.078019] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.078024] vgaarb: loaded
[    1.078024] vgaarb: bridge control possible 0000:00:02.0
[    1.078076] i2c-core: driver [aat2870] using legacy suspend method
[    1.078077] i2c-core: driver [aat2870] using legacy resume method
[    1.078110] SCSI subsystem initialized
[    1.078139] libata version 3.00 loaded.
[    1.078163] usbcore: registered new interface driver usbfs
[    1.078169] usbcore: registered new interface driver hub
[    1.078181] usbcore: registered new device driver usb
[    1.078227] PCI: Using ACPI for IRQ routing
[    1.079595] PCI: pci_cache_line_size set to 64 bytes
[    1.079655] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    1.079656] reserve RAM buffer: 0000000040004000 - 0000000043ffffff 
[    1.079658] reserve RAM buffer: 00000000d98d7000 - 00000000dbffffff 
[    1.079659] reserve RAM buffer: 00000000dac6d000 - 00000000dbffffff 
[    1.079661] reserve RAM buffer: 00000000db000000 - 00000000dbffffff 
[    1.079662] reserve RAM buffer: 000000021f600000 - 000000021fffffff 
[    1.079716] NetLabel: Initializing
[    1.079717] NetLabel:  domain hash size = 128
[    1.079718] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.079724] NetLabel:  unlabeled traffic allowed by default
[    1.079753] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.079756] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.081763] Switching to clocksource hpet
[    1.081874] Freeing initrd memory: 13868k freed
[    1.085332] AppArmor: AppArmor Filesystem Enabled
[    1.085344] pnp: PnP ACPI init
[    1.085351] ACPI: bus type pnp registered
[    1.085513] pnp 00:00: [bus 00-3e]
[    1.085515] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.085516] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.085517] pnp 00:00: [io  0x0d00-0xffff window]
[    1.085519] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.085520] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.085521] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.085522] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.085523] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.085524] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.085525] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.085526] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.085527] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.085529] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.085530] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.085532] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.085533] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.085534] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.085535] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    1.085537] pnp 00:00: [mem 0x21f600000-0xfffffffff window]
[    1.085574] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.085585] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    1.085608] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    1.085610] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.085616] pnp 00:02: [io  0x0000-0x001f]
[    1.085617] pnp 00:02: [io  0x0081-0x0091]
[    1.085618] pnp 00:02: [io  0x0093-0x009f]
[    1.085619] pnp 00:02: [io  0x00c0-0x00df]
[    1.085620] pnp 00:02: [dma 4]
[    1.085631] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.085635] pnp 00:03: [mem 0xff000000-0xffffffff]
[    1.085646] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    1.085689] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    1.085701] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.085708] pnp 00:05: [io  0x002e-0x002f]
[    1.085709] pnp 00:05: [io  0x004e-0x004f]
[    1.085710] pnp 00:05: [io  0x0061]
[    1.085711] pnp 00:05: [io  0x0063]
[    1.085712] pnp 00:05: [io  0x0065]
[    1.085712] pnp 00:05: [io  0x0067]
[    1.085713] pnp 00:05: [io  0x0070]
[    1.085714] pnp 00:05: [io  0x0080]
[    1.085715] pnp 00:05: [io  0x0092]
[    1.085716] pnp 00:05: [io  0x00b2-0x00b3]
[    1.085717] pnp 00:05: [io  0x0680-0x069f]
[    1.085718] pnp 00:05: [io  0x0200-0x020f]
[    1.085719] pnp 00:05: [io  0xffff]
[    1.085720] pnp 00:05: [io  0xffff]
[    1.085721] pnp 00:05: [io  0x0400-0x0453]
[    1.085722] pnp 00:05: [io  0x0458-0x047f]
[    1.085723] pnp 00:05: [io  0x0500-0x057f]
[    1.085724] pnp 00:05: [io  0x164e-0x164f]
[    1.085746] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.085747] system 00:05: [io  0x0200-0x020f] has been reserved
[    1.085748] system 00:05: [io  0xffff] has been reserved
[    1.085750] system 00:05: [io  0xffff] has been reserved
[    1.085751] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.085752] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.085754] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.085761] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.085763] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.085767] pnp 00:06: [io  0x0070-0x0077]
[    1.085776] pnp 00:06: [irq 8]
[    1.085789] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.085803] pnp 00:07: [io  0x0454-0x0457]
[    1.085824] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.085825] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.085883] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    1.085884] pnp 00:08: [io  0x0a00-0x0a0f]
[    1.085885] pnp 00:08: [io  0x0a30-0x0a3f]
[    1.085886] pnp 00:08: [io  0x0a20-0x0a2f]
[    1.085905] system 00:08: [io  0x0a00-0x0a0f] has been reserved
[    1.085907] system 00:08: [io  0x0a30-0x0a3f] has been reserved
[    1.085908] system 00:08: [io  0x0a20-0x0a2f] has been reserved
[    1.085910] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.085922] pnp 00:09: [io  0x0060]
[    1.085923] pnp 00:09: [io  0x0064]
[    1.085927] pnp 00:09: [irq 1]
[    1.085943] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    1.085963] pnp 00:0a: [irq 12]
[    1.085981] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    1.086074] pnp 00:0b: [io  0x03f8-0x03ff]
[    1.086078] pnp 00:0b: [irq 4]
[    1.086079] pnp 00:0b: [dma 0 disabled]
[    1.086110] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.086121] pnp 00:0c: [io  0x0010-0x001f]
[    1.086123] pnp 00:0c: [io  0x0022-0x003f]
[    1.086123] pnp 00:0c: [io  0x0044-0x005f]
[    1.086124] pnp 00:0c: [io  0x0062-0x0063]
[    1.086125] pnp 00:0c: [io  0x0065-0x006f]
[    1.086126] pnp 00:0c: [io  0x0072-0x007f]
[    1.086127] pnp 00:0c: [io  0x0080]
[    1.086128] pnp 00:0c: [io  0x0084-0x0086]
[    1.086129] pnp 00:0c: [io  0x0088]
[    1.086130] pnp 00:0c: [io  0x008c-0x008e]
[    1.086131] pnp 00:0c: [io  0x0090-0x009f]
[    1.086132] pnp 00:0c: [io  0x00a2-0x00bf]
[    1.086133] pnp 00:0c: [io  0x00e0-0x00ef]
[    1.086134] pnp 00:0c: [io  0x04d0-0x04d1]
[    1.086156] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    1.086158] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.086162] pnp 00:0d: [io  0x00f0-0x00ff]
[    1.086166] pnp 00:0d: [irq 13]
[    1.086179] pnp 00:0d: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.086312] pnp 00:0e: [mem 0xfed1c000-0xfed1ffff]
[    1.086314] pnp 00:0e: [mem 0xfed10000-0xfed17fff]
[    1.086315] pnp 00:0e: [mem 0xfed18000-0xfed18fff]
[    1.086316] pnp 00:0e: [mem 0xfed19000-0xfed19fff]
[    1.086317] pnp 00:0e: [mem 0xf8000000-0xfbffffff]
[    1.086318] pnp 00:0e: [mem 0xfed20000-0xfed3ffff]
[    1.086319] pnp 00:0e: [mem 0xfed90000-0xfed93fff]
[    1.086320] pnp 00:0e: [mem 0xfed45000-0xfed8ffff]
[    1.086322] pnp 00:0e: [mem 0xff000000-0xffffffff]
[    1.086323] pnp 00:0e: [mem 0xfee00000-0xfeefffff]
[    1.086324] pnp 00:0e: [mem 0xdfa00000-0xdfa00fff]
[    1.086355] system 00:0e: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.086357] system 00:0e: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.086358] system 00:0e: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.086360] system 00:0e: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.086361] system 00:0e: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.086363] system 00:0e: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.086364] system 00:0e: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.086365] system 00:0e: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.086367] system 00:0e: [mem 0xff000000-0xffffffff] has been reserved
[    1.086368] system 00:0e: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.086370] system 00:0e: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    1.086371] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.086454] pnp 00:0f: [mem 0x20000000-0x201fffff]
[    1.086455] pnp 00:0f: [mem 0x40004000-0x40004fff]
[    1.086488] system 00:0f: [mem 0x20000000-0x201fffff] has been reserved
[    1.086489] system 00:0f: [mem 0x40004000-0x40004fff] has been reserved
[    1.086491] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.086504] pnp: PnP ACPI: found 16 devices
[    1.086505] ACPI: ACPI bus type pnp unregistered
[    1.092204] PCI: max bus depth: 2 pci_try_num: 3
[    1.092248] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.092258] pci 0000:02:00.0: PCI bridge to [bus 03-03]
[    1.092266] pci 0000:02:00.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.092281] pci 0000:00:1c.5: PCI bridge to [bus 02-03]
[    1.092285] pci 0000:00:1c.5:   bridge window [mem 0xf7e00000-0xf7efffff]
[    1.092292] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
[    1.092294] pci 0000:00:1c.6:   bridge window [io  0xe000-0xefff]
[    1.092298] pci 0000:00:1c.6:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.092304] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
[    1.092308] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.092324] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.092327] pci 0000:00:1c.0: setting latency timer to 64
[    1.092335] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.092338] pci 0000:00:1c.5: setting latency timer to 64
[    1.092346] pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.092352] pci 0000:02:00.0: setting latency timer to 64
[    1.092360] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.092363] pci 0000:00:1c.6: setting latency timer to 64
[    1.092371] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.092374] pci 0000:00:1c.7: setting latency timer to 64
[    1.092377] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.092378] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.092380] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.092381] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.092382] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.092383] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.092384] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.092386] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.092387] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.092388] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    1.092389] pci_bus 0000:00: resource 14 [mem 0x21f600000-0xfffffffff]
[    1.092391] pci_bus 0000:02: resource 1 [mem 0xf7e00000-0xf7efffff]
[    1.092392] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    1.092393] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    1.092394] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    1.092396] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.092397] pci_bus 0000:02: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.092398] pci_bus 0000:02: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.092399] pci_bus 0000:02: resource 10 [mem 0x000dc000-0x000dffff]
[    1.092401] pci_bus 0000:02: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.092402] pci_bus 0000:02: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.092403] pci_bus 0000:02: resource 13 [mem 0xdfa00000-0xfeafffff]
[    1.092404] pci_bus 0000:02: resource 14 [mem 0x21f600000-0xfffffffff]
[    1.092406] pci_bus 0000:03: resource 1 [mem 0xf7e00000-0xf7efffff]
[    1.092407] pci_bus 0000:03: resource 5 [mem 0xf7e00000-0xf7efffff]
[    1.092408] pci_bus 0000:03: resource 8 [io  0x0000-0x0cf7]
[    1.092409] pci_bus 0000:03: resource 9 [io  0x0d00-0xffff]
[    1.092410] pci_bus 0000:03: resource 10 [mem 0x000a0000-0x000bffff]
[    1.092412] pci_bus 0000:03: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.092413] pci_bus 0000:03: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.092414] pci_bus 0000:03: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.092415] pci_bus 0000:03: resource 14 [mem 0x000dc000-0x000dffff]
[    1.092416] pci_bus 0000:03: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.092418] pci_bus 0000:03: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.092419] pci_bus 0000:03: resource 17 [mem 0xdfa00000-0xfeafffff]
[    1.092420] pci_bus 0000:03: resource 18 [mem 0x21f600000-0xfffffffff]
[    1.092422] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    1.092423] pci_bus 0000:04: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    1.092424] pci_bus 0000:05: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    1.092441] NET: Registered protocol family 2
[    1.092578] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.093171] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.094111] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.094224] TCP: Hash tables configured (established 524288 bind 65536)
[    1.094225] TCP reno registered
[    1.094235] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.094258] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.094313] NET: Registered protocol family 1
[    1.094321] pci 0000:00:02.0: Boot video device
[    1.094326] pci 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.094370] pci 0000:00:14.0: PCI INT A disabled
[    1.094378] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.113726] pci 0000:00:1a.0: PCI INT A disabled
[    1.113754] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.133689] pci 0000:00:1d.0: PCI INT A disabled
[    1.133719] pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.133778] pci 0000:05:00.0: PCI INT A disabled
[    1.133781] PCI: CLS 64 bytes, default 64
[    1.133784] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.133786] Placing 64MB software IO TLB between ffff8800d58d7000 - ffff8800d98d7000
[    1.133787] software IO TLB at phys 0xd58d7000 - 0xd98d7000
[    1.134176] audit: initializing netlink socket (disabled)
[    1.134185] type=2000 audit(1342652965.912:1): initialized
[    1.156511] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.173539] VFS: Disk quotas dquot_6.5.2
[    1.173569] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.173852] fuse init (API version 7.17)
[    1.173901] msgmni has been set to 15754
[    1.174107] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.174124] io scheduler noop registered
[    1.174125] io scheduler deadline registered
[    1.174141] io scheduler cfq registered (default)
[    1.174318] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.174330] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.174358] intel_idle: MWAIT substates: 0x1120
[    1.174359] intel_idle: does not run on family 6 model 58
[    1.174410] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.174414] ACPI: Power Button [PWRB]
[    1.174438] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.174440] ACPI: Power Button [PWRF]
[    1.174493] ACPI: Fan [FAN0] (off)
[    1.174510] ACPI: Fan [FAN1] (off)
[    1.174527] ACPI: Fan [FAN2] (off)
[    1.174543] ACPI: Fan [FAN3] (off)
[    1.174558] ACPI: Fan [FAN4] (off)
[    1.245707] Monitor-Mwait will be used to enter C-1 state
[    1.245724] Monitor-Mwait will be used to enter C-3 state
[    1.245734] ACPI: acpi_idle registered with cpuidle
[    1.261653] thermal LNXTHERM:00: registered as thermal_zone0
[    1.261655] ACPI: Thermal Zone [TZ00] (28 C)
[    1.261766] thermal LNXTHERM:01: registered as thermal_zone1
[    1.261767] ACPI: Thermal Zone [TZ01] (30 C)
[    1.261791] ERST: Table is not found!
[    1.261792] GHES: HEST is not enabled!
[    1.261831] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.282184] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.353902] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.389410] Linux agpgart interface v0.103
[    1.389460] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
[    1.389558] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.390689] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.390778] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.391520] brd: module loaded
[    1.391896] loop: module loaded
[    1.391984] ata_piix 0000:00:1f.2: version 2.13
[    1.391993] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.391997] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.392021] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.392168] scsi0 : ata_piix
[    1.392208] scsi1 : ata_piix
[    1.392307] ata1: SATA max UDMA/133 cmd 0xf110 ctl 0xf100 bmdma 0xf0d0 irq 19
[    1.392311] ata2: SATA max UDMA/133 cmd 0xf0f0 ctl 0xf0e0 bmdma 0xf0d8 irq 19
[    1.392322] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.392325] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.392352] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.392451] scsi2 : ata_piix
[    1.392488] scsi3 : ata_piix
[    1.392533] ata3: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf070 irq 19
[    1.392536] ata4: SATA max UDMA/133 cmd 0xf090 ctl 0xf080 bmdma 0xf078 irq 19
[    1.392691] Fixed MDIO Bus: probed
[    1.392699] tun: Universal TUN/TAP device driver, 1.6
[    1.392700] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.392726] PPP generic driver version 2.4.2
[    1.392781] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.392789] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.392803] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.392805] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.392828] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.392847] ehci_hcd 0000:00:1a.0: debug port 2
[    1.396712] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.396721] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7f17000
[    1.409200] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.409303] hub 1-0:1.0: USB hub found
[    1.409306] hub 1-0:1.0: 2 ports detected
[    1.409339] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.409348] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.409350] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.409373] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.409389] ehci_hcd 0000:00:1d.0: debug port 2
[    1.413253] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.413260] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7f16000
[    1.425172] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.425266] hub 2-0:1.0: USB hub found
[    1.425268] hub 2-0:1.0: 2 ports detected
[    1.425298] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.425304] uhci_hcd: USB Universal Host Controller Interface driver
[    1.425318] xhci_hcd 0000:00:14.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.425337] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.425339] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.425363] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.425432] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.425435] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7f00000
[    1.425473] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    1.425535] xHCI xhci_add_endpoint called for root hub
[    1.425536] xHCI xhci_check_bandwidth called for root hub
[    1.425549] hub 3-0:1.0: USB hub found
[    1.425554] hub 3-0:1.0: 4 ports detected
[    1.425587] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.425610] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.425651] xHCI xhci_add_endpoint called for root hub
[    1.425651] xHCI xhci_check_bandwidth called for root hub
[    1.425663] hub 4-0:1.0: USB hub found
[    1.425669] hub 4-0:1.0: 4 ports detected
[    1.473094] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.473122] xhci_hcd 0000:05:00.0: setting latency timer to 64
[    1.473126] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.473174] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 5
[    1.473276] xhci_hcd 0000:05:00.0: irq 19, io mem 0xf7c00000
[    1.473339] xhci_hcd 0000:05:00.0: irq 43 for MSI/MSI-X
[    1.473414] xHCI xhci_add_endpoint called for root hub
[    1.473415] xHCI xhci_check_bandwidth called for root hub
[    1.473427] hub 5-0:1.0: USB hub found
[    1.473432] hub 5-0:1.0: 2 ports detected
[    1.473462] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.473486] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 6
[    1.473527] xHCI xhci_add_endpoint called for root hub
[    1.473528] xHCI xhci_check_bandwidth called for root hub
[    1.473539] hub 6-0:1.0: USB hub found
[    1.473544] hub 6-0:1.0: 2 ports detected
[    1.537017] usbcore: registered new interface driver libusual
[    1.537059] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.537427] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.537431] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.537498] mousedev: PS/2 mouse device common for all mice
[    1.537575] rtc_cmos 00:06: RTC can wake from S4
[    1.537654] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.537676] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.537717] device-mapper: uevent: version 1.0.3
[    1.537751] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.537825] cpuidle: using governor ladder
[    1.537938] cpuidle: using governor menu
[    1.537939] EFI Variables Facility v0.08 2004-May-17
[    1.538034] TCP cubic registered
[    1.538084] NET: Registered protocol family 10
[    1.538297] NET: Registered protocol family 17
[    1.538300] Registering the dns_resolver key type
[    1.538373] PM: Hibernation image not present or could not be loaded.
[    1.538380] registered taskstats version 1
[    1.550981]   Magic number: 4:416:201
[    1.551082] rtc_cmos 00:06: setting system clock to 2012-07-18 23:09:27 UTC (1342652967)
[    1.551947] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.551948] EDD information not available.
[    1.719397] ata3: SATA link down (SStatus 0 SControl 330)
[    1.720667] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.853300] hub 1-1:1.0: USB hub found
[    1.853383] hub 1-1:1.0: 6 ports detected
[    1.872432] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    1.880684] ata4.00: ATA-8: SAMSUNG HM641JI, 2AJ10001, max UDMA/133
[    1.880689] ata4.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.888696] ata4.00: configured for UDMA/133
[    1.964237] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.038856] ata1.00: SATA link down (SStatus 0 SControl 330)
[    2.038868] ata1.01: SATA link down (SStatus 0 SControl 330)
[    2.049611] ata2.00: SATA link down (SStatus 0 SControl 330)
[    2.049651] ata2.01: SATA link down (SStatus 0 SControl 330)
[    2.049907] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HM641JI  2AJ1 PQ: 0 ANSI: 5
[    2.050069] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    2.050122] sd 3:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.050342] sd 3:0:0:0: [sda] Write Protect is off
[    2.050344] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.050460] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.096734] hub 2-1:1.0: USB hub found
[    2.096944] hub 2-1:1.0: 8 ports detected
[    2.131929] Refined TSC clocksource calibration: 3430.171 MHz.
[    2.131935] Switching to clocksource tsc
[    2.137764]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    2.138947] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.139849] Freeing unused kernel memory: 920k freed
[    2.139922] Write protecting the kernel read-only data: 12288k
[    2.142765] Freeing unused kernel memory: 1616k freed
[    2.144889] Freeing unused kernel memory: 1200k freed
[    2.153949] udevd[139]: starting version 175
[    2.167914] usb 1-1.1: new low-speed USB device number 3 using ehci_hcd
[    2.168749] atl1c 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.168759] atl1c 0000:04:00.0: setting latency timer to 64
[    2.269439] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
[    2.269531] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1a.0-1.1/input0
[    2.274893] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1/input/input3
[    2.275004] generic-usb 0003:0603:00F2.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1a.0-1.1/input1
[    2.275011] usbcore: registered new interface driver usbhid
[    2.275011] usbhid: USB HID core driver
[    2.296048] atl1c 0000:04:00.0: version 1.0.1.0-NAPI
[    2.335616] usb 1-1.2: new low-speed USB device number 4 using ehci_hcd
[    2.434167] input: Logitech Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input4
[    2.434327] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0
[    2.503319] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[    2.598325] Initializing USB Mass Storage driver...
[    2.598350] usbcore: registered new interface driver uas
[    2.598394] scsi4 : usb-storage 2-1.5:1.0
[    2.598437] usbcore: registered new interface driver usb-storage
[    2.598438] USB Mass Storage support registered.
[    2.789075] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.789077] EXT4-fs (sda6): write access will be enabled during recovery
[    2.878952] EXT4-fs (sda6): orphan cleanup on readonly fs
[    2.878956] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396131
[    2.878983] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396130
[    2.879007] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396129
[    2.879013] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396128
[    2.879018] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396127
[    2.879023] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396126
[    2.879029] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396125
[    2.879034] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396124
[    2.879039] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396123
[    2.879044] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396122
[    2.879049] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 396121
[    2.879055] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 262795
[    2.879060] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 262792
[    2.879067] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 262785
[    2.879072] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 262784
[    2.879077] EXT4-fs (sda6): 15 orphan inodes deleted
[    2.879078] EXT4-fs (sda6): recovery complete
[    3.594564] scsi 4:0:0:0: Direct-Access     USB      Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[    3.594880] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    3.595866] sd 4:0:0:0: [sdb] 7928832 512-byte logical blocks: (4.05 GB/3.78 GiB)
[    3.596977] sd 4:0:0:0: [sdb] Write Protect is off
[    3.596979] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    3.597986] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.597988] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.601018] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.601023] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.601854]  sdb: sdb1
[    3.607383] sd 4:0:0:0: [sdb] No Caching mode page present
[    3.607388] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.607391] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.715501] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.415515] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.427690] udevd[379]: starting version 175
[   13.446762] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   13.447040] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.447045] mei 0000:00:16.0: setting latency timer to 64
[   13.447098] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   13.449480] lp: driver loaded but no devices found
[   13.450219] [drm] Initialized drm 1.1.0 20060810
[   13.453379] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.453383] i915 0000:00:02.0: setting latency timer to 64
[   13.468471] type=1400 audit(1342649379.435:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=432 comm="apparmor_parser"
[   13.468729] type=1400 audit(1342649379.435:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=432 comm="apparmor_parser"
[   13.468876] type=1400 audit(1342649379.435:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=432 comm="apparmor_parser"
[   13.507194] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   13.507199] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.507200] [drm] Driver supports precise vblank timestamp query.
[   13.507727] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.547096] Adding 3905532k swap on /dev/sda8.  Priority:-1 extents:1 across:3905532k 
[   13.890994] fbcon: inteldrmfb (fb0) is primary device
[   13.891050] Console: switching to colour frame buffer device 160x64
[   13.891064] fb0: inteldrmfb frame buffer device
[   13.891065] drm: registered panic notifier
[   13.967363] acpi device:4d: registered as cooling_device13
[   13.967481] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   13.967520] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.967545] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.967584] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.967655] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   13.967671] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   14.527048] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   14.527095] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   14.527153] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
[   14.527201] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.527336] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.527458] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.527504] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.527535] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.527567] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.527598] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.527628] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.527657] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   14.527688] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   14.705368] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.046864] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   21.300122] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   21.640487] init: failsafe main process (862) killed by TERM signal
[   21.920610] Bluetooth: Core ver 2.16
[   21.920622] NET: Registered protocol family 31
[   21.920624] Bluetooth: HCI device and connection manager initialized
[   21.920625] Bluetooth: HCI socket layer initialized
[   21.920626] Bluetooth: L2CAP socket layer initialized
[   21.920630] Bluetooth: SCO socket layer initialized
[   21.921534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.921535] Bluetooth: BNEP filters: protocol multicast
[   21.957193] ppdev: user-space parallel port driver
[   21.975527] Bluetooth: RFCOMM TTY layer initialized
[   21.975530] Bluetooth: RFCOMM socket layer initialized
[   21.975531] Bluetooth: RFCOMM ver 1.11
[   21.985401] type=1400 audit(1342649387.967:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=937 comm="apparmor_parser"
[   21.985657] type=1400 audit(1342649387.967:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=937 comm="apparmor_parser"
[   21.994068] type=1400 audit(1342649387.975:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=971 comm="apparmor_parser"
[   21.994079] type=1400 audit(1342649387.975:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=978 comm="apparmor_parser"
[   21.994276] type=1400 audit(1342649387.975:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=972 comm="apparmor_parser"
[   21.994552] type=1400 audit(1342649387.975:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=972 comm="apparmor_parser"
[   21.994635] type=1400 audit(1342649387.975:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=976 comm="apparmor_parser"
[   21.994707] type=1400 audit(1342649387.975:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=972 comm="apparmor_parser"
[   21.994882] type=1400 audit(1342649387.975:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=976 comm="apparmor_parser"
[   21.997739] type=1400 audit(1342649387.979:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=973 comm="apparmor_parser"
[   22.121878] atl1c 0000:04:00.0: irq 47 for MSI/MSI-X
[   22.205100] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.206613] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.602905] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  238.919122] cfg80211: Calling CRDA to update world regulatory domain
[  239.018619] cfg80211: World regulatory domain updated:
[  239.018622] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  239.018624] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.018625] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  239.018627] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  239.018628] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.018630] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.077747] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  239.383763] ath: EEPROM regdomain: 0x809c
[  239.383765] ath: EEPROM indicates we should expect a country code
[  239.383767] ath: doing EEPROM country->regdmn map search
[  239.383769] ath: country maps to regdmn code: 0x52
[  239.383771] ath: Country alpha2 being used: CN
[  239.383773] ath: Regpair used: 0x52
[  239.383776] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  239.383779] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383782] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  239.383785] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383787] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  239.383790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383793] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  239.383796] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383798] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  239.383801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383803] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  239.383806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383809] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  239.383812] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383814] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  239.383817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383819] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  239.383822] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383825] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  239.383828] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383830] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  239.383833] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.383835] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  239.383838] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  239.383841] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  239.385365] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  239.385368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385371] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  239.385374] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385376] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  239.385379] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385381] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  239.385384] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385387] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  239.385390] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385392] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  239.385395] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385398] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  239.385401] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385403] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  239.385406] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385408] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  239.385411] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385414] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  239.385417] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385419] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  239.385422] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  239.385425] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  239.385428] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  239.385430] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  239.385433] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  239.385436] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  239.385439] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  239.428932] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  239.429480] Registered led device: ath9k-phy0
[  239.429485] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90006040000, irq=17
[  239.429673] cfg80211: Calling CRDA for country: CN
[  239.432825] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  239.432828] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432829] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  239.432830] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432831] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  239.432833] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432834] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  239.432835] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432836] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  239.432837] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432838] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  239.432840] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432841] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  239.432842] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432843] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  239.432844] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432845] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  239.432847] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432848] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  239.432849] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432850] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  239.432851] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432852] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  239.432853] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432855] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  239.432856] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  239.432857] cfg80211: Disabling freq 2484 MHz
[  239.432859] cfg80211: Regulatory domain changed to country: CN
[  239.432860] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  239.432861] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  239.432862] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[  239.489984] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.494161] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  262.242611] wlan0: authenticate with 00:14:7f:d0:df:84 (try 1)
[  262.244623] wlan0: authenticated
[  262.272387] wlan0: associate with 00:14:7f:d0:df:84 (try 1)
[  262.275092] wlan0: RX AssocResp from 00:14:7f:d0:df:84 (capab=0x411 status=0 aid=4)
[  262.275097] wlan0: associated
[  262.275657] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

