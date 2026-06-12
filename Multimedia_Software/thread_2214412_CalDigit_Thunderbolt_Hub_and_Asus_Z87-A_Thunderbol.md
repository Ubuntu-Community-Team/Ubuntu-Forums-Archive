---
title: "CalDigit Thunderbolt Hub and Asus Z87-A Thunderbolt add-on card"
date: 2014-04-01
forum: Multimedia Software
---

### Post by troy8 on 2014-04-01
Has anyone got the USB 3.0 Ports working on this setup?  The Video works perfectly, but for some reason I can not get the USB 3.0 ports working.

```

  0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-031300-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201401192235 SMP Mon Jan 20 03:36:48 UTC 2014
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-031300-generic root=UUID=8721ff2f-ce47-4dbd-b71c-295f066e0922 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000868a2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000868a3000-0x00000000868a9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000868aa000-0x0000000086cf9fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000086cfa000-0x0000000087157fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000087158000-0x0000000098400fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000098401000-0x000000009892afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009892b000-0x0000000098944fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000098945000-0x0000000098e82fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000098e83000-0x0000000099ffefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000099fff000-0x0000000099ffffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000003feffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUS All Series/Z87-A, BIOS 1802 01/28/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x3ff000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   2 base 00A0000000 mask 7FE0000000 uncachable
[    0.000000]   3 base 009C000000 mask 7FFC000000 uncachable
[    0.000000]   4 base 009B000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 03FF000000 mask 7FFF000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 3GB, range: 1GB, type UC
[    0.000000] reg 2, base: 2560MB, range: 512MB, type UC
[    0.000000] reg 3, base: 2496MB, range: 64MB, type UC
[    0.000000] reg 4, base: 2480MB, range: 16MB, type UC
[    0.000000] reg 5, base: 16368MB, range: 16MB, type UC
[    0.000000] total RAM covered: 14752M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 7  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2480MB, range: 16MB, type UC
[    0.000000] reg 3, base: 2496MB, range: 64MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16368MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0x9b000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x9a000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7b0-0x000fd7bf] mapped at [ffff8800000fd7b0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdc000, 0x01fdcfff] PGTABLE
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3fee00000-0x3feffffff]
[    0.000000]  [mem 0x3fee00000-0x3feffffff] page 2M
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3fc000000-0x3fedfffff]
[    0.000000]  [mem 0x3fc000000-0x3fedfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x380000000-0x3fbffffff]
[    0.000000]  [mem 0x380000000-0x3bfffffff] page 1G
[    0.000000]  [mem 0x3c0000000-0x3fbffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x868a2fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x867fffff] page 2M
[    0.000000]  [mem 0x86800000-0x868a2fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x868aa000-0x86cf9fff]
[    0.000000]  [mem 0x868aa000-0x869fffff] page 4k
[    0.000000]  [mem 0x86a00000-0x86bfffff] page 2M
[    0.000000]  [mem 0x86c00000-0x86cf9fff] page 4k
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x87158000-0x98400fff]
[    0.000000]  [mem 0x87158000-0x871fffff] page 4k
[    0.000000]  [mem 0x87200000-0x983fffff] page 2M
[    0.000000]  [mem 0x98400000-0x98400fff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x99fff000-0x99ffffff]
[    0.000000]  [mem 0x99fff000-0x99ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x37fffffff]
[    0.000000]  [mem 0x100000000-0x37fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35d64000-0x36ea9fff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0000000098930088 00008C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000009893eca8 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000989301b0 00EAF2 (v02 ALASKA    A M I 00000031 INTL 20091112)
[    0.000000] ACPI: FACS 0000000098e81080 000040
[    0.000000] ACPI: APIC 000000009893edb8 000092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000009893ee50 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: LPIT 000000009893ee98 00005C (v01 ALASKA    A M I 00000000 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000009893eef8 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
[    0.000000] ACPI: SSDT 000000009893f438 000AD8 (v01  PmRef    CpuPm 00003000 INTL 20091112)
[    0.000000] ACPI: MCFG 000000009893ff10 00003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 000000009893ff50 000038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000009893ff88 00036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000989402f8 0034E1 (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
[    0.000000] ACPI: BGRT 0000000098944318 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DMAR 0000000098943838 0000B8 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 00000000989438f0 000A26 (v01 Intel_ IsctTabl 00001000 INTL 20091112)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000003feffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x3feffffff]
[    0.000000]   NODE_DATA [mem 0x3feff7000-0x3feffbfff]
[    0.000000]  [ffffea0000000000-ffffea000fffffff] PMD -> [ffff8803efe00000-ffff8803fe5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x3feffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x868a2fff]
[    0.000000]   node   0: [mem 0x868aa000-0x86cf9fff]
[    0.000000]   node   0: [mem 0x87158000-0x98400fff]
[    0.000000]   node   0: [mem 0x99fff000-0x99ffffff]
[    0.000000]   node   0: [mem 0x100000000-0x3feffffff]
[    0.000000] On node 0 totalpages: 3764025
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9663 pages used for memmap
[    0.000000]   DMA32 zone: 618397 pages, LIFO batch:31
[    0.000000]   Normal zone: 49088 pages used for memmap
[    0.000000]   Normal zone: 3141632 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
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
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x868a3000-0x868a9fff]
[    0.000000] PM: Registered nosave memory: [mem 0x86cfa000-0x87157fff]
[    0.000000] PM: Registered nosave memory: [mem 0x98401000-0x9892afff]
[    0.000000] PM: Registered nosave memory: [mem 0x9892b000-0x98944fff]
[    0.000000] PM: Registered nosave memory: [mem 0x98945000-0x98e82fff]
[    0.000000] PM: Registered nosave memory: [mem 0x98e83000-0x99ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9a000000-0x9affffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f200000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x9f200000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff8803fec00000 s86400 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3705189
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-031300-generic root=UUID=8721ff2f-ce47-4dbd-b71c-295f066e0922 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 14717228K/15056100K available (7476K kernel code, 1128K rwdata, 3500K rodata, 1344K init, 1436K bss, 338872K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 60817408 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3398.053 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6796.10 BogoMIPS (lpj=13592212)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000017] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000028] Yama: becoming mindful.
[    0.000781] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.002771] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003574] Mount-cache hash table entries: 256
[    0.003686] Initializing cgroup subsys memory
[    0.003689] Initializing cgroup subsys devices
[    0.003690] Initializing cgroup subsys freezer
[    0.003691] Initializing cgroup subsys blkio
[    0.003692] Initializing cgroup subsys perf_event
[    0.003694] Initializing cgroup subsys hugetlb
[    0.003708] CPU: Physical Processor ID: 0
[    0.003709] CPU: Processor Core ID: 0
[    0.003712] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003712] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004453] mce: CPU supports 9 MCE banks
[    0.004463] CPU0: Thermal monitoring enabled (TM1)
[    0.004471] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.004471] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.004471] tlb_flushall_shift: 6
[    0.004541] Freeing SMP alternatives memory: 28K (ffffffff81e6c000 - ffffffff81e73000)
[    0.005190] ACPI: Core revision 20131115
[    0.010719] ACPI: All ACPI Tables successfully acquired
[    0.011879] ftrace: allocating 31023 entries in 122 pages
[    0.020370] dmar: Host address width 39
[    0.020371] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.020376] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    0.020377] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.020380] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    0.020381] dmar: RMRR base: 0x00000098631000 end: 0x0000009863dfff
[    0.020381] dmar: RMRR base: 0x0000009b000000 end: 0x0000009f1fffff
[    0.020445] IOAPIC id 8 under DRHD base  0xfed91000 IOMMU 1
[    0.020446] HPET id 0 under DRHD base 0xfed91000
[    0.020552] Enabled IRQ remapping in x2apic mode
[    0.020553] Enabling x2apic
[    0.020554] Enabled x2apic
[    0.020557] Switched APIC routing to cluster x2apic.
[    0.020947] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.060584] smpboot: CPU0: Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz (fam: 06, model: 3c, stepping: 03)
[    0.060589] TSC deadline timer enabled
[    0.061819] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.061824] ... version:                3
[    0.061824] ... bit width:              48
[    0.061825] ... generic registers:      4
[    0.061826] ... value mask:             0000ffffffffffff
[    0.061826] ... max period:             0000ffffffffffff
[    0.061827] ... fixed-purpose events:   3
[    0.061828] ... event mask:             000000070000000f
[    0.062915] x86: Booting SMP configuration:
[    0.076682] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.062916] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.159526] x86: Booted up 1 node, 8 CPUs
[    0.159529] smpboot: Total of 8 processors activated (54368.84 BogoMIPS)
[    0.166615] devtmpfs: initialized
[    0.169590] EVM: security.selinux
[    0.169591] EVM: security.SMACK64
[    0.169592] EVM: security.ima
[    0.169592] EVM: security.capability
[    0.169619] PM: Registering ACPI NVS region [mem 0x868a3000-0x868a9fff] (28672 bytes)
[    0.169620] PM: Registering ACPI NVS region [mem 0x98945000-0x98e82fff] (5496832 bytes)
[    0.170141] pinctrl core: initialized pinctrl subsystem
[    0.170176] regulator-dummy: no parameters
[    0.170201] RTC time:  7:58:45, date: 04/01/14
[    0.170221] NET: Registered protocol family 16
[    0.170279] cpuidle: using governor ladder
[    0.170280] cpuidle: using governor menu
[    0.170304] ACPI: bus type PCI registered
[    0.170305] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.170337] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.170339] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.178744] PCI: Using configuration type 1 for base access
[    0.179374] bio: create slab <bio-0> at 0
[    0.179478] ACPI: Added _OSI(Module Device)
[    0.179479] ACPI: Added _OSI(Processor Device)
[    0.179480] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.179481] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182740] ACPI: Executed 1 blocks of module-level executable AML code
[    0.184686] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.202514] ACPI: SSDT 0000000098920c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.202903] ACPI: Dynamic OEM Table Load:
[    0.202905] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    0.206590] ACPI: SSDT 0000000098920618 0005AA (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.207021] ACPI: Dynamic OEM Table Load:
[    0.207022] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20091112)
[    0.210500] ACPI: SSDT 000000009891fd98 000119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.210889] ACPI: Dynamic OEM Table Load:
[    0.210890] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    0.215233] ACPI: Interpreter enabled
[    0.215238] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.215241] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.215252] ACPI: (supports S0 S3 S4 S5)
[    0.215253] ACPI: Using IOAPIC for interrupt routing
[    0.215271] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.215400] ACPI: No dock devices found.
[    0.220679] ACPI: Power Resource [FN00] (off)
[    0.220727] ACPI: Power Resource [FN01] (off)
[    0.220772] ACPI: Power Resource [FN02] (off)
[    0.220817] ACPI: Power Resource [FN03] (off)
[    0.220860] ACPI: Power Resource [FN04] (off)
[    0.221459] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.221463] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.221957] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.222304] PCI host bridge to bus 0000:00
[    0.222306] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.222307] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.222308] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.222309] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.222310] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.222311] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.222312] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.222313] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.222314] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.222315] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.222316] pci_bus 0000:00: root bus resource [mem 0x9f200000-0xfeafffff]
[    0.222321] pci 0000:00:00.0: [8086:0c00] type 00 class 0x060000
[    0.222379] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.222403] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.222442] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.222464] pci 0000:00:02.0: [8086:0412] type 00 class 0x030000
[    0.222472] pci 0000:00:02.0: reg 0x10: [mem 0xee400000-0xee7fffff 64bit]
[    0.222476] pci 0000:00:02.0: reg 0x18: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.222480] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.222552] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.222568] pci 0000:00:14.0: reg 0x10: [mem 0xee900000-0xee90ffff 64bit]
[    0.222762] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.222791] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.222811] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.222828] pci 0000:00:16.0: reg 0x10: [mem 0xee916000-0xee91600f 64bit]
[    0.222882] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.222938] pci 0000:00:1a.0: [8086:8c2d] type 00 class 0x0c0320
[    0.222956] pci 0000:00:1a.0: reg 0x10: [mem 0xee914000-0xee9143ff]
[    0.223034] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.223073] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.223092] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.223147] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.223180] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.223198] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.223253] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.223285] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.223303] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    0.223359] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.223390] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.223415] pci 0000:00:1d.0: [8086:8c26] type 00 class 0x0c0320
[    0.223432] pci 0000:00:1d.0: reg 0x10: [mem 0xee913000-0xee9133ff]
[    0.223511] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.223550] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.223570] pci 0000:00:1f.0: [8086:8c44] type 00 class 0x060100
[    0.223844] pci 0000:00:1f.2: [8086:8c02] type 00 class 0x010601
[    0.223856] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.223862] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.223868] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.223874] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.223880] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.223885] pci 0000:00:1f.2: reg 0x24: [mem 0xee912000-0xee9127ff]
[    0.223916] pci 0000:00:1f.2: PME# supported from D3hot
[    0.223959] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.223970] pci 0000:00:1f.3: reg 0x10: [mem 0xee911000-0xee9110ff 64bit]
[    0.223987] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.224061] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.224112] acpiphp: Slot [1] registered
[    0.224115] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.224181] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.224196] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.224222] pci 0000:03:00.0: reg 0x18: [mem 0xee800000-0xee800fff 64bit]
[    0.224238] pci 0000:03:00.0: reg 0x20: [mem 0xd2100000-0xd2103fff 64bit pref]
[    0.224308] pci 0000:03:00.0: supports D1 D2
[    0.224309] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.224337] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.230447] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.230449] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.230452] pci 0000:00:1c.2:   bridge window [mem 0xee800000-0xee8fffff]
[    0.230456] pci 0000:00:1c.2:   bridge window [mem 0xd2100000-0xd21fffff 64bit pref]
[    0.230495] pci 0000:00:1c.4: PCI bridge to [bus 04-3c]
[    0.230499] pci 0000:00:1c.4:   bridge window [mem 0xd8000000-0xee0fffff]
[    0.230503] pci 0000:00:1c.4:   bridge window [mem 0xb0000000-0xd1ffffff 64bit pref]
[    0.231202] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.231234] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.231265] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.231296] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.231326] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.231355] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.231385] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.231415] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.231868] ACPI: Enabled 7 GPEs in block 00 to 3F
[    0.231873] ACPI: \_SB_.PCI0: notify handler is installed
[    0.231922] Found 1 acpi root devices
[    0.231978] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.231980] vgaarb: loaded
[    0.231980] vgaarb: bridge control possible 0000:00:02.0
[    0.232070] SCSI subsystem initialized
[    0.232097] libata version 3.00 loaded.
[    0.232106] ACPI: bus type USB registered
[    0.232115] usbcore: registered new interface driver usbfs
[    0.232119] usbcore: registered new interface driver hub
[    0.232139] usbcore: registered new device driver usb
[    0.232206] PCI: Using ACPI for IRQ routing
[    0.235200] PCI: pci_cache_line_size set to 64 bytes
[    0.235227] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.235228] e820: reserve RAM buffer [mem 0x868a3000-0x87ffffff]
[    0.235229] e820: reserve RAM buffer [mem 0x86cfa000-0x87ffffff]
[    0.235230] e820: reserve RAM buffer [mem 0x98401000-0x9bffffff]
[    0.235231] e820: reserve RAM buffer [mem 0x9a000000-0x9bffffff]
[    0.235232] e820: reserve RAM buffer [mem 0x3ff000000-0x3ffffffff]
[    0.235276] NetLabel: Initializing
[    0.235276] NetLabel:  domain hash size = 128
[    0.235277] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.235285] NetLabel:  unlabeled traffic allowed by default
[    0.235316] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.235320] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.237339] Switched to clocksource hpet
[    0.240789] AppArmor: AppArmor Filesystem Enabled
[    0.240799] pnp: PnP ACPI init
[    0.240804] ACPI: bus type PNP registered
[    0.240839] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.240841] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.240847] pnp 00:01: [dma 4]
[    0.240856] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.240866] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.240921] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.240949] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.241012] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.241013] system 00:05: [io  0xffff] has been reserved
[    0.241014] system 00:05: [io  0xffff] has been reserved
[    0.241016] system 00:05: [io  0xffff] has been reserved
[    0.241017] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.241018] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.241019] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.241020] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.241021] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.241022] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.241024] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241039] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.241065] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.241067] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.241113] system 00:08: [io  0x0290-0x029f] has been reserved
[    0.241114] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241139] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.241140] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241277] pnp 00:0a: [dma 0 disabled]
[    0.241302] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.241717] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.241718] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.241720] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.241721] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.241722] system 00:0b: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.241723] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.241724] system 00:0b: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.241725] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.241727] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.241728] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.241729] system 00:0b: [mem 0xeffee000-0xeffeefff] has been reserved
[    0.241730] system 00:0b: [mem 0xeffd0000-0xeffdffff] has been reserved
[    0.241732] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)



 0.241114] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241139] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.241140] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241277] pnp 00:0a: [dma 0 disabled]
[    0.241302] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.241717] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.241718] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.241720] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.241721] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.241722] system 00:0b: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.241723] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.241724] system 00:0b: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.241725] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.241727] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.241728] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.241729] system 00:0b: [mem 0xeffee000-0xeffeefff] has been reserved
[    0.241730] system 00:0b: [mem 0xeffd0000-0xeffdffff] has been reserved
[    0.241732] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241870] pnp: PnP ACPI: found 12 devices
[    0.241870] ACPI: bus type PNP unregistered
[    0.247726] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 04-3c] add_size 1000
[    0.247729] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.247731] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.247732] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.247737] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.247745] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.247747] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.247750] pci 0000:00:1c.2:   bridge window [mem 0xee800000-0xee8fffff]
[    0.247753] pci 0000:00:1c.2:   bridge window [mem 0xd2100000-0xd21fffff 64bit pref]
[    0.247757] pci 0000:00:1c.4: PCI bridge to [bus 04-3c]
[    0.247759] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.247762] pci 0000:00:1c.4:   bridge window [mem 0xd8000000-0xee0fffff]
[    0.247765] pci 0000:00:1c.4:   bridge window [mem 0xb0000000-0xd1ffffff 64bit pref]
[    0.247769] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.247770] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.247772] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.247773] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.247773] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.247774] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.247775] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.247776] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.247777] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.247778] pci_bus 0000:00: resource 13 [mem 0x9f200000-0xfeafffff]
[    0.247780] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.247781] pci_bus 0000:03: resource 1 [mem 0xee800000-0xee8fffff]
[    0.247782] pci_bus 0000:03: resource 2 [mem 0xd2100000-0xd21fffff 64bit pref]
[    0.247783] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.247784] pci_bus 0000:04: resource 1 [mem 0xd8000000-0xee0fffff]
[    0.247785] pci_bus 0000:04: resource 2 [mem 0xb0000000-0xd1ffffff 64bit pref]
[    0.247801] NET: Registered protocol family 2
[    0.247920] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.248057] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.248153] TCP: Hash tables configured (established 131072 bind 65536)
[    0.248164] TCP: reno registered
[    0.248176] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.248213] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.248266] NET: Registered protocol family 1
[    0.248273] pci 0000:00:02.0: Boot video device
[    0.269370] PCI: CLS mismatch (64 != 128), using 64 bytes
[    0.289370] Trying to unpack rootfs image as initramfs...
[    0.478901] Freeing initrd memory: 17688K (ffff880035d64000 - ffff880036eaa000)
[    0.478907] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.478909] software IO TLB [mem 0x94401000-0x98401000] (64MB) mapped at [ffff880094401000-ffff880098400fff]
[    0.479073] Scanning for low memory corruption every 60 seconds
[    0.479242] Initialise system trusted keyring
[    0.479268] audit: initializing netlink socket (disabled)
[    0.479274] type=2000 audit(1396339124.464:1): initialized
[    0.497616] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.498460] zbud: loaded
[    0.498540] VFS: Disk quotas dquot_6.5.2
[    0.498563] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.498788] fuse init (API version 7.22)
[    0.498826] msgmni has been set to 28779
[    0.498855] Key type big_key registered
[    0.499150] Key type asymmetric registered
[    0.499151] Asymmetric key parser 'x509' registered
[    0.499167] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.499201] io scheduler noop registered
[    0.499202] io scheduler deadline registered (default)
[    0.499214] io scheduler cfq registered
[    0.499329] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.499413] pcieport 0000:00:1c.0: irq 43 for MSI/MSI-X
[    0.499502] pcieport 0000:00:1c.2: irq 44 for MSI/MSI-X
[    0.499591] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.499645] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.499647] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.499658] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.499660] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.499669] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.499671] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.499673] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.499682] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.499684] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.499692] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.499717] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 8c18 ss_vid 1043 ss_did 8534
[    0.499743] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.499745] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.499861] simple-framebuffer simple-framebuffer.0: framebuffer at 0xa0000000, 0x12c000 bytes, mapped to 0xffffc90009b80000
[    0.499863] simple-framebuffer simple-framebuffer.0: format=a8r8g8b8, mode=640x480x32, linelength=2560
[    0.500303] Console: switching to colour frame buffer device 80x30
[    0.500703] simple-framebuffer simple-framebuffer.0: fb0: simplefb registered!
[    0.500707] intel_idle: MWAIT substates: 0x42120
[    0.500708] intel_idle: v0.4 model 0x3C
[    0.500708] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.500854] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.500857] ACPI: Power Button [PWRB]
[    0.500876] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.500878] ACPI: Power Button [PWRF]
[    0.500909] ACPI: Fan [FAN0] (off)
[    0.500923] ACPI: Fan [FAN1] (off)
[    0.500935] ACPI: Fan [FAN2] (off)
[    0.500948] ACPI: Fan [FAN3] (off)
[    0.500960] ACPI: Fan [FAN4] (off)
[    0.501233] thermal LNXTHERM:00: registered as thermal_zone0
[    0.501234] ACPI: Thermal Zone [TZ00] (28 C)
[    0.501364] thermal LNXTHERM:01: registered as thermal_zone1
[    0.501365] ACPI: Thermal Zone [TZ01] (30 C)
[    0.501380] GHES: HEST is not enabled!
[    0.501420] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.521761] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.522551] Linux agpgart interface v0.103
[    0.523214] brd: module loaded
[    0.523570] loop: module loaded
[    0.523764] libphy: Fixed MDIO Bus: probed
[    0.523807] tun: Universal TUN/TAP device driver, 1.6
[    0.523808] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.523833] PPP generic driver version 2.4.2
[    0.523855] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.523857] ehci-pci: EHCI PCI platform driver
[    0.523927] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.523931] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.523940] ehci-pci 0000:00:1a.0: debug port 2
[    0.527831] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.527840] ehci-pci 0000:00:1a.0: irq 20, io mem 0xee914000
[    0.537000] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.537025] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.537027] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.537028] usb usb1: Product: EHCI Host Controller
[    0.537029] usb usb1: Manufacturer: Linux 3.13.0-031300-generic ehci_hcd
[    0.537030] usb usb1: SerialNumber: 0000:00:1a.0
[    0.537089] hub 1-0:1.0: USB hub found
[    0.537094] hub 1-0:1.0: 2 ports detected
[    0.537212] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.537215] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.537224] ehci-pci 0000:00:1d.0: debug port 2
[    0.541121] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.541129] ehci-pci 0000:00:1d.0: irq 23, io mem 0xee913000
[    0.552979] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.552999] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.553000] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.553001] usb usb2: Product: EHCI Host Controller
[    0.553002] usb usb2: Manufacturer: Linux 3.13.0-031300-generic ehci_hcd
[    0.553003] usb usb2: SerialNumber: 0000:00:1d.0
[    0.553053] hub 2-0:1.0: USB hub found
[    0.553056] hub 2-0:1.0: 2 ports detected
[    0.553114] ehci-platform: EHCI generic platform driver
[    0.553118] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.553119] ohci-pci: OHCI PCI platform driver
[    0.553124] ohci-platform: OHCI generic platform driver
[    0.553128] uhci_hcd: USB Universal Host Controller Interface driver
[    0.553193] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.553197] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.553264] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.553278] xhci_hcd 0000:00:14.0: irq 46 for MSI/MSI-X
[    0.553316] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.553317] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.553318] usb usb3: Product: xHCI Host Controller
[    0.553319] usb usb3: Manufacturer: Linux 3.13.0-031300-generic xhci_hcd
[    0.553320] usb usb3: SerialNumber: 0000:00:14.0
[    0.553386] hub 3-0:1.0: USB hub found
[    0.553401] hub 3-0:1.0: 14 ports detected
[    0.555642] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.555644] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.555673] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.555674] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.555675] usb usb4: Product: xHCI Host Controller
[    0.555676] usb usb4: Manufacturer: Linux 3.13.0-031300-generic xhci_hcd
[    0.555677] usb usb4: SerialNumber: 0000:00:14.0
[    0.555744] hub 4-0:1.0: USB hub found
[    0.555754] hub 4-0:1.0: 6 ports detected
[    0.561026] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.563390] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.563396] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.563465] mousedev: PS/2 mouse device common for all mice
[    0.563618] rtc_cmos 00:06: RTC can wake from S4
[    0.563742] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.563768] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.563800] device-mapper: uevent: version 1.0.3
[    0.563864] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.563868] Intel P-state driver initializing.
[    0.563874] Intel pstate controlling: cpu 0
[    0.563882] Intel pstate controlling: cpu 1
[    0.563888] Intel pstate controlling: cpu 2
[    0.563895] Intel pstate controlling: cpu 3
[    0.563901] Intel pstate controlling: cpu 4
[    0.563909] Intel pstate controlling: cpu 5
[    0.563916] Intel pstate controlling: cpu 6
[    0.563922] Intel pstate controlling: cpu 7
[    0.563939] ledtrig-cpu: registered to indicate activity on CPUs
[    0.563992] TCP: cubic registered
[    0.564039] NET: Registered protocol family 10
[    0.564127] NET: Registered protocol family 17
[    0.564132] Key type dns_resolver registered
[    0.564328] Loading compiled-in X.509 certificates
[    0.564825] Loaded X.509 cert 'Magrathea: Glacier signing key: 35f135ec7fa376b562d3b56cf970db8321e8b4af'
[    0.564839] registered taskstats version 1
[    0.566838] Key type trusted registered
[    0.568638] Key type encrypted registered
[    0.570351] AppArmor: AppArmor sha1 policy hashing enabled
[    0.570353] IMA: No TPM chip found, activating TPM-bypass!
[    0.570778]   Magic number: 10:244:975
[    0.570905] rtc_cmos 00:06: setting system clock to 2014-04-01 07:58:45 UTC (1396339125)
[    0.571057] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.571058] EDD information not available.
[    0.571087] PM: Hibernation image not present or could not be loaded.
[    0.571829] Freeing unused kernel memory: 1344K (ffffffff81d1c000 - ffffffff81e6c000)
[    0.571830] Write protecting the kernel read-only data: 12288k
[    0.572837] Freeing unused kernel memory: 704K (ffff880001750000 - ffff880001800000)
[    0.573620] Freeing unused kernel memory: 596K (ffff880001b6b000 - ffff880001c00000)
[    0.582051] systemd-udevd[144]: starting version 204
[    0.593209] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x12
[    0.593248] microcode: CPU0 sig=0x306c3, pf=0x2, revision=0x12
[    0.594630] microcode: CPU0 updated to revision 0x16, date = 2013-08-07
[    0.594637] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x12
[    0.594670] microcode: CPU1 sig=0x306c3, pf=0x2, revision=0x12
[    0.595407] microcode: CPU1 updated to revision 0x16, date = 2013-08-07
[    0.595415] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x12
[    0.595439] microcode: CPU2 sig=0x306c3, pf=0x2, revision=0x12
[    0.596188] microcode: CPU2 updated to revision 0x16, date = 2013-08-07
[    0.596193] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x12
[    0.596214] microcode: CPU3 sig=0x306c3, pf=0x2, revision=0x12
[    0.596949] microcode: CPU3 updated to revision 0x16, date = 2013-08-07
[    0.596964] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x12
[    0.596988] microcode: CPU4 sig=0x306c3, pf=0x2, revision=0x12
[    0.597755] microcode: CPU4 updated to revision 0x16, date = 2013-08-07
[    0.597763] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x12
[    0.597786] microcode: CPU5 sig=0x306c3, pf=0x2, revision=0x12
[    0.598527] microcode: CPU5 updated to revision 0x16, date = 2013-08-07
[    0.598533] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x12
[    0.598557] microcode: CPU6 sig=0x306c3, pf=0x2, revision=0x12
[    0.599243] microcode: CPU6 updated to revision 0x16, date = 2013-08-07
[    0.599247] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x12
[    0.599265] microcode: CPU7 sig=0x306c3, pf=0x2, revision=0x12
[    0.600042] microcode: CPU7 updated to revision 0x16, date = 2013-08-07
[    0.600089] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.601805] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.603216] ahci 0000:00:1f.2: version 3.0
[    0.603296] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    0.603330] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0xd impl SATA mode
[    0.603332] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.609304] r8169 0000:03:00.0: irq 48 for MSI/MSI-X
[    0.609427] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90001840000, bc:ee:7b:8c:75:7a, XID 0c000800 IRQ 48
[    0.609428] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.617319] scsi0 : ahci
[    0.617402] scsi1 : ahci
[    0.617451] scsi2 : ahci
[    0.617503] scsi3 : ahci
[    0.617565] scsi4 : ahci
[    0.617613] scsi5 : ahci
[    0.617639] ata1: SATA max UDMA/133 abar m2048@0xee912000 port 0xee912100 irq 47
[    0.617640] ata2: DUMMY
[    0.617642] ata3: SATA max UDMA/133 abar m2048@0xee912000 port 0xee912200 irq 47
[    0.617643] ata4: SATA max UDMA/133 abar m2048@0xee912000 port 0xee912280 irq 47
[    0.617644] ata5: DUMMY
[    0.617644] ata6: DUMMY
[    0.852693] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.936577] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.936592] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.936606] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.937207] ata4.00: ATA-9: WDC WD30EZRX-00D8PB0, 80.00A80, max UDMA/133
[    0.937209] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.937559] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    0.937561] ata1.00: ATA-9: Samsung SSD 840 PRO Series, DXM05B0Q, max UDMA/133
[    0.937562] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.937868] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    0.937873] ata4.00: configured for UDMA/133
[    0.937925] ata1.00: configured for UDMA/133
[    0.938030] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXM0 PQ: 0 ANSI: 5
[    0.938159] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.938165] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    0.938347] sd 0:0:0:0: [sda] Write Protect is off
[    0.938348] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.938398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.938893]  sda: sda1 sda2 < sda5 >
[    0.939182] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.939938] ata3.00: ATAPI: PIONEER BD-RW   BDR-209D, 1.10, max UDMA/100
[    0.943482] ata3.00: configured for UDMA/100
[    0.954437] scsi 2:0:0:0: CD-ROM            PIONEER  BD-RW   BDR-209D 1.10 PQ: 0 ANSI: 5
[    0.975553] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[    0.975555] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.975644] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    0.975693] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    0.975815] scsi 3:0:0:0: Direct-Access     ATA      WDC WD30EZRX-00D 80.0 PQ: 0 ANSI: 5
[    0.975893] sd 3:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    0.975895] sd 3:0:0:0: [sdb] 4096-byte physical blocks
[    0.975908] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    0.975912] sd 3:0:0:0: [sdb] Write Protect is off
[    0.975913] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.975920] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.984876] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    0.984878] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.985130] hub 1-1:1.0: USB hub found
[    0.985248] hub 1-1:1.0: 6 ports detected
[    1.044851]  sdb:
[    1.044921] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.068489] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.068491] EXT4-fs (sda1): write access will be enabled during recovery
[    1.096376] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.110552] EXT4-fs (sda1): recovery complete
[    1.111929] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.163950] random: init urandom read with 86 bits of entropy available
[    1.196414] init: ureadahead main process (230) terminated with status 5
[    1.228564] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    1.228567] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.228697] hub 2-1:1.0: USB hub found
[    1.228814] hub 2-1:1.0: 8 ports detected
[    1.230481] Adding 16645116k swap on /dev/sda5.  Priority:-1 extents:1 across:16645116k SSFS
[    1.267405] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    1.270764] systemd-udevd[350]: starting version 204
[    1.285763] lp: driver loaded but no devices found
[    1.310575] wmi: Mapper loaded
[    1.317552] mei_me 0000:00:16.0: irq 49 for MSI/MSI-X
[    1.323568] [drm] Initialized drm 1.1.0 20060810
[    1.324485] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    1.324489] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324491] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    1.324493] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    1.324495] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324495] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    1.324497] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    1.324498] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324499] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    1.342754] random: nonblocking pool is initialized
[    1.343916] [drm] Memory usable by graphics device = 2048M
[    1.343919] checking generic (a0000000 12c000) vs hw (a0000000 10000000)
[    1.343920] fb: conflicting fb hw usage inteldrmfb vs simple - removing generic driver
[    1.343933] Console: switching to colour dummy device 80x25
[    1.375245] type=1400 audit(1396339126.301:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=529 comm="apparmor_parser"
[    1.375249] type=1400 audit(1396339126.301:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[    1.375250] type=1400 audit(1396339126.301:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    1.375583] type=1400 audit(1396339126.301:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[    1.375588] type=1400 audit(1396339126.301:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    1.375790] type=1400 audit(1396339126.301:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[    1.381124] asus_wmi: ASUS WMI generic driver loaded
[    1.383358] asus_wmi: Initialization: 0x0
[    1.383385] asus_wmi: BIOS WMI version: 0.9
[    1.383425] asus_wmi: SFUN value: 0x0
[    1.383721] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
[    1.388282] asus_wmi: Backlight controlled by ACPI video driver
[    1.388874] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[    1.388883] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.388884] [drm] Driver supports precise vblank timestamp query.
[    1.388962] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.396021] usb 3-10: new high-speed USB device number 2 using xhci_hcd
[    1.402496] Bluetooth: Core ver 2.17
[    1.402508] NET: Registered protocol family 31
[    1.402509] Bluetooth: HCI device and connection manager initialized
[    1.402515] Bluetooth: HCI socket layer initialized
[    1.402517] Bluetooth: L2CAP socket layer initialized
[    1.402520] Bluetooth: SCO socket layer initialized
[    1.406739] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    1.406742] Bluetooth: BNEP filters: protocol multicast
[    1.406751] Bluetooth: BNEP socket layer initialized
[    1.406864] Bluetooth: RFCOMM TTY layer initialized
[    1.406868] Bluetooth: RFCOMM socket layer initialized
[    1.406871] Bluetooth: RFCOMM ver 1.11
[    1.412207] usb 3-10: New USB device found, idVendor=1a40, idProduct=0101
[    1.412210] usb 3-10: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.412211] usb 3-10: Product: USB 2.0 Hub [MTT]
[    1.412505] hub 3-10:1.0: USB hub found
[    1.412528] hub 3-10:1.0: 4 ports detected
[    1.448773] ppdev: user-space parallel port driver
[    1.454917] init: avahi-cups-reload main process (645) terminated with status 1
[    1.473054] type=1400 audit(1396339126.401:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=664 comm="apparmor_parser"
[    1.473058] type=1400 audit(1396339126.401:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=664 comm="apparmor_parser"
[    1.473385] type=1400 audit(1396339126.401:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=664 comm="apparmor_parser"
[    1.475921] tsc: Refined TSC clocksource calibration: 3398.030 MHz
[    1.509221] init: failsafe main process (670) killed by TERM signal
[    1.609828] r8169 0000:03:00.0 eth0: link down
[    1.609845] r8169 0000:03:00.0 eth0: link down
[    1.609866] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.683679] usb 3-10.4: new high-speed USB device number 3 using xhci_hcd
[    1.699858] usb 3-10.4: New USB device found, idVendor=1a40, idProduct=0201
[    1.699860] usb 3-10.4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.699862] usb 3-10.4: Product: USB 2.0 Hub [MTT]
[    1.700149] hub 3-10.4:1.0: USB hub found
[    1.700204] hub 3-10.4:1.0: 7 ports detected
[    1.971340] usb 3-10.4.1: new high-speed USB device number 4 using xhci_hcd
[    1.995651] usb 3-10.4.1: New USB device found, idVendor=05ac, idProduct=1006
[    1.995654] usb 3-10.4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.995655] usb 3-10.4.1: Product: Keyboard Hub
[    1.995657] usb 3-10.4.1: Manufacturer: Apple, Inc.
[    1.995658] usb 3-10.4.1: SerialNumber: 000000000000
[    1.995971] hub 3-10.4.1:1.0: USB hub found
[    1.995993] hub 3-10.4.1:1.0: 3 ports detected
[    2.061008] fbcon: inteldrmfb (fb0) is primary device
[    2.067264] usb 3-10.4.2: new high-speed USB device number 5 using xhci_hcd
[    2.096460] usb 3-10.4.2: New USB device found, idVendor=0bda, idProduct=2838
[    2.096462] usb 3-10.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.096462] usb 3-10.4.2: Product: RTL2838UHIDIR
[    2.096463] usb 3-10.4.2: Manufacturer: Realtek
[    2.096463] usb 3-10.4.2: SerialNumber: 00000001
[    2.175107] usb 3-10.4.5: new full-speed USB device number 6 using xhci_hcd
[    2.206323] usb 3-10.4.5: New USB device found, idVendor=05a7, idProduct=1020
[    2.206324] usb 3-10.4.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.206325] usb 3-10.4.5: Product: Bose USB Audio
[    2.206326] usb 3-10.4.5: Manufacturer: Bose Corporation
[    2.279000] usb 3-10.4.7: new full-speed USB device number 7 using xhci_hcd
[    2.299097] Console: switching to colour frame buffer device 480x135
[    2.308530] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.308531] i915 0000:00:02.0: registered panic notifier
[    2.320008] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.320221] acpi device:56: registered as cooling_device14
[    2.320269] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.320322] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.329437] usb 3-10.4.7: New USB device found, idVendor=0a12, idProduct=0001
[    2.329439] usb 3-10.4.7: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.329441] usb 3-10.4.7: Product: CSR8510 A10
[    2.335134] usbcore: registered new interface driver btusb
[    2.339138] hidraw: raw HID events driver (C) Jiri Kosina
[    2.344806] usbcore: registered new interface driver usbhid
[    2.344807] usbhid: USB HID core driver
[    2.346685] usb 3-10.4.2: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[    2.349648] hid-generic 0003:05A7:1020.0001: hiddev0,hidraw0: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:14.0-10.4.5/input2
[    2.376441] 6:1:1: cannot get freq at ep 0x1
[    2.392917] usbcore: registered new interface driver snd-usb-audio
[    2.398856] usb 3-10.4.1.2: new low-speed USB device number 8 using xhci_hcd
[    2.407549] usb 3-10.4.2: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    2.407555] DVB: registering new adapter (Realtek RTL2832U reference design)
[    2.412972] usb 3-10.4.2: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[    2.415216] r820t 7-001a: creating new instance
[    2.421634] usb 3-10.4.1.2: New USB device found, idVendor=05ac, idProduct=024f
[    2.421636] usb 3-10.4.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.421638] usb 3-10.4.1.2: Product: Apple Keyboard
[    2.421639] usb 3-10.4.1.2: Manufacturer: Apple Inc.
[    2.421699] usb 3-10.4.1.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.421702] usb 3-10.4.1.2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.426446] r820t 7-001a: Rafael Micro r820t successfully identified
[    2.431987] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4.1/3-10.4.1.2/3-10.4.1.2:1.0/input/input7
[    2.432060] apple 0003:05AC:024F.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-10.4.1.2/input0
[    2.432737] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4.1/3-10.4.1.2/3-10.4.1.2:1.1/input/input8
[    2.432778] Registered IR keymap rc-empty
[    2.432800] apple 0003:05AC:024F.0003: input,hidraw2: USB HID v1.11 Device [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-10.4.1.2/input1
[    2.432839] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4.2/rc/rc0/input9
[    2.433457] rc0: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4.2/rc/rc0
[    2.435216] IR NEC protocol handler initialized
[    2.435398] IR RC5(x) protocol handler initialized
[    2.436079] usb 3-10.4.2: dvb_usb_v2: schedule remote query interval to 400 msecs
[    2.437453] IR Sony protocol handler initialized
[    2.437458] IR SANYO protocol handler initialized
[    2.437463] IR RC6 protocol handler initialized
[    2.437638] IR JVC protocol handler initialized
[    2.438110] input: MCE IR Keyboard/Mouse (dvb_usb_rtl28xxu) as /devices/virtual/input/input10
[    2.438179] IR MCE Keyboard/mouse protocol handler initialized
[    2.438397] lirc_dev: IR Remote Control driver registered, major 250 
[    2.439784] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[    2.439786] IR LIRC bridge handler initialized
[    2.447096] usb 3-10.4.2: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected
[    2.447134] usbcore: registered new interface driver dvb_usb_rtl28xxu
[    2.474821] Switched to clocksource tsc
[    2.826422] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    4.452922] 6:1:1: cannot get freq at ep 0x1
[    4.456006] 6:1:1: cannot get freq at ep 0x1
[    4.465484] 6:1:1: cannot get freq at ep 0x1
[    4.469002] 6:1:1: cannot get freq at ep 0x1
[    4.477373] 6:1:1: cannot get freq at ep 0x1
[    4.480309] 6:1:1: cannot get freq at ep 0x1
[    4.492357] 6:1:1: cannot get freq at ep 0x1
[    4.495294] 6:1:1: cannot get freq at ep 0x1
[    4.604645] r8169 0000:03:00.0 eth0: link up
[    4.604652] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   11.780386] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   11.780392] Bluetooth: HIDP socket layer initialized
[   11.780691] hid-generic 0005:046D:B009.0004: unknown main item tag 0x0
[   11.780727] input: Logitech Bluetooth Mouse M555b as /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.4/3-10.4.7/3-10.4.7:1.0/bluetooth/hci0/hci0:71/input11
[   11.780796] hid-generic 0005:046D:B009.0004: input,hidraw3: BLUETOOTH HID v4.19 Mouse [Logitech Bluetooth Mouse M555b] on 00:1b:dc:06:cd:b3

```

```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8000 
  bcdDevice            0.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-031300-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8008 
  bcdDevice            0.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood        0 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-031300-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-031300-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:00:14.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0
Hub Descriptor:
  bLength              12
  bDescriptorType      42
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  bHubDecLat          0.0 micro seconds
  wHubDelay             0 nano seconds
  DeviceRemovable    0x00
 Hub Port Status:
   Port 1: 0000.02a0 5Gbps power Rx.Detect
   Port 2: 0000.02a0 5Gbps power Rx.Detect
   Port 3: 0000.02a0 5Gbps power Rx.Detect
   Port 4: 0000.02a0 5Gbps power Rx.Detect
   Port 5: 0000.02a0 5Gbps power Rx.Detect
   Port 6: 0000.02a0 5Gbps power Rx.Detect
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           15
  bNumDeviceCaps          1
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x02
      Latency Tolerance Messages (LTM) Supported
    wSpeedsSupported   0x0008
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   3
      Lowest fully-functional device speed is SuperSpeed (5Gbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat         512 micro seconds
Device Status:     0x0001
  Self Powered


Bus 003 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a12 Cambridge Silicon Radio, Ltd
  idProduct          0x0001 Bluetooth Dongle (HCI mode)
  bcdDevice           88.91
  iManufacturer           0 
  iProduct                2 CSR8510 A10
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered


Bus 003 Device 006: ID 05a7:1020 Bose Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05a7 Bose Corp.
  idProduct          0x1020 
  bcdDevice            1.00
  iManufacturer           1 Bose Corporation
  iProduct                2 Bose USB Audio
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          146
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           44
        bInCollection           1
        baInterfaceNr( 0)       1
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             6
        wChannelConfig     0x003f
          Left Front (L)
          Right Front (R)
          Center Front (C)
          Low Freqency Enhancement (LFE)
          Left Surround (LS)
          Right Surround (RS)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 3
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x03
          Mute Control
          Volume Control
        bmaControls( 1)      0x00
        bmaControls( 2)      0x00
        bmaControls( 3)      0x00
        bmaControls( 4)      0x00
        bmaControls( 5)      0x00
        bmaControls( 6)      0x00
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             6
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x0240  1x 576 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      46
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered


Bus 003 Device 005: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x2838 RTL2838 DVB-T
  bcdDevice            1.00
  iManufacturer           1 Realtek
  iProduct                2 RTL2838UHIDIR
  iSerial                 3 00000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB2.0-Bulk&Iso
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 008: ID 05ac:024f Apple, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05ac Apple, Inc.
  idProduct          0x024f 
  bcdDevice            0.74
  iManufacturer           1 Apple Inc.
  iProduct                2 Apple Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               20mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode           33 US
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      75
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      47
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 004: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x05ac Apple, Inc.
  idProduct          0x1006 Hub in Aluminum Keyboard
  bcdDevice           96.15
  iManufacturer           1 Apple, Inc.
  iProduct                2 Keyboard Hub
  iSerial                 3 000000000000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x008d
    Per-port power switching
    Compound device
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    200 milli Ampere
  DeviceRemovable    0x04
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0303 lowspeed power enable connect
   Port 3: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


Bus 003 Device 003: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x1a40 Terminus Technology Inc.
  idProduct          0x0201 FE 2.1 7-port Hub
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB 2.0 Hub [MTT]
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             7
  wHubCharacteristic 0x0088
    Ganged power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0503 highspeed power enable connect
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0103 power enable connect
   Port 6: 0000.0100 power
   Port 7: 0000.0103 power enable connect
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 003 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         2 TT per port
  bMaxPacketSize0        64
  idVendor           0x1a40 Terminus Technology Inc.
  idProduct          0x0101 4-Port HUB
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB 2.0 Hub [MTT]
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      1 Single TT
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 TT per port
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0080
    Ganged power switching
    Ganged overcurrent protection
    TT think time 8 FS bits
    Port indicators
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent    100 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0503 highspeed power enable connect
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 Linux 3.13.0-031300-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:00:14.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            14
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0503 highspeed power enable connect
   Port 11: 0000.0100 power
   Port 12: 0000.0100 power
   Port 13: 0000.0100 power
   Port 14: 0000.0100 power
Device Status:     0x0001
  Self Powered

```

---

### Post by troy8 on 2014-04-02
Well I was hoping now that the 3.14 kernel is out it would fix the issue.  But, of course it didn't... :(  Nobody else using Asus's Thunderbolt?

---

### Post by troy8 on 2014-04-10
In case anyone else is having issues with thunderbolt the nightly build of Trusty yesterday fixed:

23568] [drm] Initialized drm 1.1.0 20060810
[    1.324485] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    1.324489] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324491] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    1.324493] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    1.324495] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324495] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    1.324497] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    1.324498] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.324499] lpc_ich: Resource conflict(s) found affecting gpio_ich


Fixing that I thought for sure it would get things working correctly, but it did not.

---

