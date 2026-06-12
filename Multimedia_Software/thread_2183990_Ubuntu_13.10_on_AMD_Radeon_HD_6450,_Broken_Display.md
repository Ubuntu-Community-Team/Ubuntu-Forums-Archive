---
title: "Ubuntu 13.10 on AMD Radeon HD 6450, Broken Display"
date: 2013-10-27
forum: Multimedia Software
---

### Post by ripthejacker_ on 2013-10-27
Hi everyone I installed Ubuntu 13.10 , two days ago and this time decided to keep open source drivers Instead of fglrx.
The display was totally broken, I could see just lines all over the screen like 'static' in TV.
I had to disable modesetting, to install and then I turned off.
I may be able to fix it by installing fglrx , but then I have to install it eveytime the kernel is updated.
The GPU card is codenamed CAICOS , 
The screen looks something like this,
[[IMG]http://s10.postimg.org/kuuwzefxh/new1.jpg[/IMG]]("http://postimg.org/image/kuuwzefxh/")
This is actually Ubuntu 13.04, but the effect is the same, It's just the salamander in place of ringtail.
And also
[[IMG]http://s10.postimg.org/cdveohb8l/new2.jpg[/IMG]]("http://postimg.org/image/cdveohb8l/")
and this
[[IMG]http://s10.postimg.org/q4zvqp06d/new3.jpg[/IMG]]("http://postimg.org/image/q4zvqp06d/")

In the third Image you can see the message as:
```
GPU lockup CP stall for more than 10000
```

I managed to open the terminal (without seeing anything on screen) using ctrl+alt+f1, and then login and extracted dmesg output to a file.
For some reason there was no output in glxinfo.
This is the output for the dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-12-generic (buildd@komainu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu7) ) #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 (Ubuntu 3.11.0-12.19-generic 3.11.3)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf533fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf534000-0x00000000bf58afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf58b000-0x00000000bf5aafff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf5ab000-0x00000000bf5bbfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf5bc000-0x00000000bf5d2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf5d3000-0x00000000bf5d4fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf5d5000-0x00000000bf5d5fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf5d6000-0x00000000bf5ddfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf5de000-0x00000000bf5e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf5e8000-0x00000000bf641fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf642000-0x00000000bf684fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf685000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013f7fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: System manufacturer System Product Name/P8H61-M LX, BIOS 0208 05/26/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x13f800 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 base 13F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 1GB, type UC
[    0.000000] reg 3, base: 5112MB, range: 8MB, type UC
[    0.000000] total RAM covered: 4088M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 1GB, type WB
[    0.000000] reg 3, base: 5112MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] found SMP MP-table at [mem 0x000fcd70-0x000fcd7f] mapped at [c00fcd70]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b39000, 0x01b39fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35fa4000-0x36fc9fff]
[    0.000000] ACPI: RSDP 000f0420 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT bf57e068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP bf5872c0 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT bf57e140 0917E (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS bf5dff80 00040
[    0.000000] ACPI: APIC bf5873b8 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT bf587430 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG bf587538 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET bf587578 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4220MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b3a000, 0x01b3afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f7fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbf533fff]
[    0.000000]   node   0: [mem 0xbf5d3000-0xbf5d4fff]
[    0.000000]   node   0: [mem 0xbf685000-0xbf7fffff]
[    0.000000]   node   0: [mem 0x00000000-0x3f7fffff]
[    0.000000] On node 0 totalpages: 1044045
[    0.000000] free_area_init_node: node 0, pgdat c1948bc0, node_mem_map f37b4020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8441 pages used for memmap
[    0.000000]   HighMem zone: 815795 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0xbf800000-0xfed1bfff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb4000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1042261
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=c14dc632-f3a7-4c20-9f0b-29782ac05ab7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 10469368 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0013f800)
[    0.000000] Memory: 4095848K/4176180K available (6351K kernel code, 607K rwdata, 2640K rodata, 880K init, 908K bss, 80332K reserved, 3263180K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1962000 - 0xc1a3e000   ( 880 kB)
[    0.000000]       .data : 0xc16341e4 - 0xc1961e00   (3255 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16341e4   (6352 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f3008000 soft=f300a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3092.880 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6185.76 BogoMIPS (lpj=12371520)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000022] Security Framework initialized
[    0.000034] AppArmor: AppArmor initialized
[    0.000035] Yama: becoming mindful.
[    0.000064] Mount-cache hash table entries: 512
[    0.000199] Initializing cgroup subsys memory
[    0.000204] Initializing cgroup subsys devices
[    0.000206] Initializing cgroup subsys freezer
[    0.000207] Initializing cgroup subsys blkio
[    0.000208] Initializing cgroup subsys perf_event
[    0.000210] Initializing cgroup subsys hugetlb
[    0.000228] CPU: Physical Processor ID: 0
[    0.000229] CPU: Processor Core ID: 0
[    0.000232] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000232] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000234] mce: CPU supports 9 MCE banks
[    0.000245] CPU0: Thermal monitoring enabled (TM1)
[    0.000256] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.000256] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.000256] tlb_flushall_shift: 5
[    0.000525] Freeing SMP alternatives memory: 28K (c1a3e000 - c1a45000)
[    0.002135] ACPI: Core revision 20130517
[    0.004788] ACPI: All ACPI Tables successfully acquired
[    0.004923] ftrace: allocating 27134 entries in 53 pages
[    0.014865] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.015249] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.054922] smpboot: CPU0: Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz (fam: 06, model: 2a, stepping: 07)
[    0.054928] TSC deadline timer enabled
[    0.054936] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.054941] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.054943] ... version:                3
[    0.054944] ... bit width:              48
[    0.054945] ... generic registers:      8
[    0.054946] ... value mask:             0000ffffffffffff
[    0.054946] ... max period:             0000ffffffffffff
[    0.054947] ... fixed-purpose events:   3
[    0.054948] ... event mask:             00000007000000ff
[    0.055997] CPU 1 irqstacks, hard=f30f6000 soft=f3100000
[    0.066202] Initializing CPU#1
[    0.069074] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.055998] smpboot: Booting Node   0, Processors  #1
[    0.069139] CPU 2 irqstacks, hard=f3184000 soft=f3186000
[    0.079377] Initializing CPU#2
[    0.069140]  #2
[    0.082340] CPU 3 irqstacks, hard=f31f0000 soft=f31f2000
[    0.082342]  #3 OK
[    0.092572] Initializing CPU#3
[    0.095488] Brought up 4 CPUs
[    0.095491] smpboot: Total of 4 processors activated (24743.04 BogoMIPS)
[    0.098093] devtmpfs: initialized
[    0.098234] EVM: security.selinux
[    0.098235] EVM: security.SMACK64
[    0.098236] EVM: security.capability
[    0.098310] PM: Registering ACPI NVS region [mem 0xbf534000-0xbf58afff] (356352 bytes)
[    0.098317] PM: Registering ACPI NVS region [mem 0xbf5ab000-0xbf5bbfff] (69632 bytes)
[    0.098319] PM: Registering ACPI NVS region [mem 0xbf5d5000-0xbf5d5fff] (4096 bytes)
[    0.098320] PM: Registering ACPI NVS region [mem 0xbf5de000-0xbf5e7fff] (40960 bytes)
[    0.098322] PM: Registering ACPI NVS region [mem 0xbf642000-0xbf684fff] (274432 bytes)
[    0.099035] regulator-dummy: no parameters
[    0.099063] RTC time:  1:26:38, date: 10/27/13
[    0.099093] NET: Registered protocol family 16
[    0.099192] EISA bus registered
[    0.099241] ACPI: bus type PCI registered
[    0.099243] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.099281] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.099283] PCI: not using MMCONFIG
[    0.111702] PCI: Using configuration type 1 for base access
[    0.112398] bio: create slab <bio-0> at 0
[    0.112500] ACPI: Added _OSI(Module Device)
[    0.112501] ACPI: Added _OSI(Processor Device)
[    0.112502] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.112503] ACPI: Added _OSI(Processor Aggregator Device)
[    0.113459] ACPI: EC: Look up EC in DSDT
[    0.114533] ACPI: Executed 1 blocks of module-level executable AML code
[    0.116266] ACPI: SSDT bf5dec18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.116542] ACPI: Dynamic OEM Table Load:
[    0.116543] ACPI: SSDT   (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.116561] ACPI: SSDT bf5dfe18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.116791] ACPI: Dynamic OEM Table Load:
[    0.116793] ACPI: SSDT   (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.117190] ACPI: Interpreter enabled
[    0.117203] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.117213] ACPI: (supports S0 S1 S3 S4 S5)
[    0.117214] ACPI: Using IOAPIC for interrupt routing
[    0.117229] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.117274] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.117275] PCI: Using MMCONFIG for extended config space
[    0.117285] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.117362] ACPI: No dock devices found.
[    0.117552] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.122611] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.122730] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.122892] acpi PNP0A08:00: ACPI _OSC control (0x1c) granted
[    0.123040] acpi PNP0A08:00: ignoring host bridge window [mem 0x000c8000-0x000dffff] (conflicts with Video ROM [mem 0x000c0000-0x000cffff])
[    0.123042] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.123122] PCI host bridge to bus 0000:00
[    0.123124] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.123125] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.123127] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.123128] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.123130] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.123136] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.123204] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.123231] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.123264] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.123318] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.123340] pci 0000:00:16.0: reg 0x10: [mem 0xfe708000-0xfe70800f 64bit]
[    0.123413] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.123485] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.123505] pci 0000:00:1a.0: reg 0x10: [mem 0xfe707000-0xfe7073ff]
[    0.123594] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.123632] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.123661] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.123675] pci 0000:00:1b.0: reg 0x10: [mem 0xfe700000-0xfe703fff 64bit]
[    0.123742] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.123802] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.123878] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.123918] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.123944] pci 0000:00:1c.1: [8086:1c12] type 01 class 0x060400
[    0.124020] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.124061] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.124086] pci 0000:00:1c.2: [8086:1c14] type 01 class 0x060400
[    0.124162] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.124203] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.124229] pci 0000:00:1c.3: [8086:1c16] type 01 class 0x060400
[    0.124305] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.124345] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.124372] pci 0000:00:1c.4: [8086:244e] type 01 class 0x060401
[    0.124448] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.124488] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.124513] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.124589] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.124629] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.124662] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.124682] pci 0000:00:1d.0: reg 0x10: [mem 0xfe706000-0xfe7063ff]
[    0.124770] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.124808] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.124839] pci 0000:00:1f.0: [8086:1c5c] type 00 class 0x060100
[    0.124995] pci 0000:00:1f.2: [8086:1c02] type 00 class 0x010601
[    0.125012] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.125019] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.125026] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.125033] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.125041] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.125048] pci 0000:00:1f.2: reg 0x24: [mem 0xfe705000-0xfe7057ff]
[    0.125091] pci 0000:00:1f.2: PME# supported from D3hot
[    0.125147] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.125161] pci 0000:00:1f.3: reg 0x10: [mem 0xfe704000-0xfe7040ff 64bit]
[    0.125181] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.125274] pci 0000:01:00.0: [1002:6779] type 00 class 0x030000
[    0.125286] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.125295] pci 0000:01:00.0: reg 0x18: [mem 0xfe620000-0xfe63ffff 64bit]
[    0.125301] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.125312] pci 0000:01:00.0: reg 0x30: [mem 0xfe600000-0xfe61ffff pref]
[    0.125339] pci 0000:01:00.0: supports D1 D2
[    0.125369] pci 0000:01:00.1: [1002:aa98] type 00 class 0x040300
[    0.125380] pci 0000:01:00.1: reg 0x10: [mem 0xfe640000-0xfe643fff 64bit]
[    0.125430] pci 0000:01:00.1: supports D1 D2
[    0.134299] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.134304] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.134308] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.134313] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.134386] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.134445] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.134526] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.134545] pci 0000:04:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.134578] pci 0000:04:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.134599] pci 0000:04:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.134690] pci 0000:04:00.0: supports D1 D2
[    0.134691] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.142305] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.142310] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.142321] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.142390] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.142450] pci 0000:00:1c.4: PCI bridge to [bus 06] (subtractive decode)
[    0.142460] pci 0000:00:1c.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.142461] pci 0000:00:1c.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.142463] pci 0000:00:1c.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.142464] pci 0000:00:1c.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.142515] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.142551] pci_bus 0000:00: on NUMA node 0
[    0.142993] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.143035] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.143075] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.143115] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.143154] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.143194] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.143234] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.143273] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.143375] ACPI: Enabled 2 GPEs in block 00 to 3F
[    0.143380] ACPI: \_SB_.PCI0: notify handler is installed
[    0.143414] Found 1 acpi root devices
[    0.143478] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.143480] vgaarb: loaded
[    0.143480] vgaarb: bridge control possible 0000:01:00.0
[    0.143609] SCSI subsystem initialized
[    0.143610] ACPI: bus type ATA registered
[    0.143636] libata version 3.00 loaded.
[    0.143647] ACPI: bus type USB registered
[    0.143658] usbcore: registered new interface driver usbfs
[    0.143664] usbcore: registered new interface driver hub
[    0.143676] usbcore: registered new device driver usb
[    0.143749] PCI: Using ACPI for IRQ routing
[    0.145174] PCI: pci_cache_line_size set to 64 bytes
[    0.145216] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.145217] e820: reserve RAM buffer [mem 0xbf534000-0xbfffffff]
[    0.145219] e820: reserve RAM buffer [mem 0xbf5d5000-0xbfffffff]
[    0.145221] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.145222] e820: reserve RAM buffer [mem 0x13f800000-0x13fffffff]
[    0.145281] NetLabel: Initializing
[    0.145282] NetLabel:  domain hash size = 128
[    0.145283] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.145289] NetLabel:  unlabeled traffic allowed by default
[    0.145356] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.145361] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.147378] Switched to clocksource hpet
[    0.151723] AppArmor: AppArmor Filesystem Enabled
[    0.151735] pnp: PnP ACPI init
[    0.151743] ACPI: bus type PNP registered
[    0.151819] system 00:00: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.151821] system 00:00: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.151823] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.151824] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.151826] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.151828] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.151888] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.151890] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.152094] pnp 00:02: [dma 0 disabled]
[    0.152166] pnp 00:02: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.152174] pnp 00:03: [dma 4]
[    0.152187] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.152206] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.152221] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.152252] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.152254] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.152272] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.152421] pnp 00:08: [dma 0 disabled]
[    0.152455] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.152486] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.152609] system 00:0a: [io  0x0400-0x0453] could not be reserved
[    0.152611] system 00:0a: [io  0x0458-0x047f] has been reserved
[    0.152612] system 00:0a: [io  0x0500-0x057f] has been reserved
[    0.152614] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.152616] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.152617] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.152619] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.152621] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.152663] system 00:0b: [io  0x0454-0x0457] has been reserved
[    0.152665] system 00:0b: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.152749] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.152846] pnp: PnP ACPI: found 13 devices
[    0.152847] ACPI: bus type PNP unregistered
[    0.152849] PnPBIOS: Disabled by ACPI PNP
[    0.188686] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.188688] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.188691] pci 0000:00:01.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.188693] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.188696] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.188706] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.188716] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.188719] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.188725] pci 0000:00:1c.2:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.188730] pci 0000:00:1c.3: PCI bridge to [bus 05]
[    0.188741] pci 0000:00:1c.4: PCI bridge to [bus 06]
[    0.188751] pci 0000:00:1c.5: PCI bridge to [bus 07]
[    0.189040] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.189042] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.189043] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.189045] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.189046] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.189047] pci_bus 0000:01: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.189049] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.189050] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.189052] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.189053] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.189055] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.189056] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.189057] pci_bus 0000:06: resource 7 [mem 0xc0000000-0xffffffff]
[    0.189077] NET: Registered protocol family 2
[    0.189180] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.189192] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.189203] TCP: Hash tables configured (established 8192 bind 8192)
[    0.189211] TCP: reno registered
[    0.189213] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.189217] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.189253] NET: Registered protocol family 1
[    0.443413] pci 0000:01:00.0: Boot video device
[    0.443419] PCI: CLS 64 bytes, default 64
[    0.443445] Trying to unpack rootfs image as initramfs...
[    0.668453] Freeing initrd memory: 16536K (f5fa4000 - f6fca000)
[    0.668658] Scanning for low memory corruption every 60 seconds
[    0.668852] Initialise module verification
[    0.668882] audit: initializing netlink socket (disabled)
[    0.668891] type=2000 audit(1382837198.668:1): initialized
[    0.684821] bounce pool size: 64 pages
[    0.684830] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.685849] zbud: loaded
[    0.685878] VFS: Disk quotas dquot_6.5.2
[    0.685911] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.686221] fuse init (API version 7.22)
[    0.686276] msgmni has been set to 1658
[    0.686587] Key type asymmetric registered
[    0.686588] Asymmetric key parser 'x509' registered
[    0.686611] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.686638] io scheduler noop registered
[    0.686639] io scheduler deadline registered (default)
[    0.686656] io scheduler cfq registered
[    0.686727] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.686778] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.686843] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.686909] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.686973] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.687039] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    0.687105] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.687106] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.687107] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    0.687110] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.687124] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.687127] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.687141] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.687145] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.687160] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    0.687161] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    0.687164] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    0.687180] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.687183] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.687197] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    0.687200] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    0.687209] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.687220] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.687284] intel_idle: MWAIT substates: 0x1120
[    0.687285] intel_idle: v0.4 model 0x2A
[    0.687286] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.687344] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.687348] ACPI: Power Button [PWRB]
[    0.687374] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.687376] ACPI: Power Button [PWRF]
[    0.687416] ACPI: Requesting acpi_cpufreq
[    0.688386] GHES: HEST is not enabled!
[    0.688399] isapnp: Scanning for PnP cards...
[    0.688438] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.708884] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.709810] Linux agpgart interface v0.103
[    0.710730] brd: module loaded
[    0.711203] loop: module loaded
[    0.711452] libphy: Fixed MDIO Bus: probed
[    0.711513] tun: Universal TUN/TAP device driver, 1.6
[    0.711514] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.711538] PPP generic driver version 2.4.2
[    0.711568] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.711569] ehci-pci: EHCI PCI platform driver
[    0.711631] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.711636] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.711640] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.711651] ehci-pci 0000:00:1a.0: debug port 2
[    0.715549] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.715561] ehci-pci 0000:00:1a.0: irq 23, io mem 0xfe707000
[    0.727264] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.727279] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.727280] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.727281] usb usb1: Product: EHCI Host Controller
[    0.727283] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.727284] usb usb1: SerialNumber: 0000:00:1a.0
[    0.727354] hub 1-0:1.0: USB hub found
[    0.727357] hub 1-0:1.0: 2 ports detected
[    0.727464] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.727469] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.727472] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.727482] ehci-pci 0000:00:1d.0: debug port 2
[    0.731384] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.731387] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfe706000
[    0.743255] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.743264] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.743265] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.743266] usb usb2: Product: EHCI Host Controller
[    0.743267] usb usb2: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.743269] usb usb2: SerialNumber: 0000:00:1d.0
[    0.743333] hub 2-0:1.0: USB hub found
[    0.743335] hub 2-0:1.0: 2 ports detected
[    0.743391] ehci-platform: EHCI generic platform driver
[    0.743396] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.743397] ohci-platform: OHCI generic platform driver
[    0.743401] uhci_hcd: USB Universal Host Controller Interface driver
[    0.743447] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.743448] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.744049] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.744107] mousedev: PS/2 mouse device common for all mice
[    0.744190] rtc_cmos 00:04: RTC can wake from S4
[    0.744296] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.744321] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.744362] device-mapper: uevent: version 1.0.3
[    0.744400] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.744411] platform eisa.0: Probing EISA bus 0
[    0.744428] platform eisa.0: EISA: Detected 0 cards
[    0.744432] cpufreq-nforce2: No nForce2 chipset.
[    0.744492] cpuidle: using governor ladder
[    0.744570] cpuidle: using governor menu
[    0.744576] ledtrig-cpu: registered to indicate activity on CPUs
[    0.744637] TCP: cubic registered
[    0.744702] NET: Registered protocol family 10
[    0.744825] NET: Registered protocol family 17
[    0.744830] Key type dns_resolver registered
[    0.744957] Using IPI No-Shortcut mode
[    0.745021] PM: Hibernation image not present or could not be loaded.
[    0.745023] Loading module verification certificates
[    0.747618] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 4b7c2664fb134f99aaf5e09f5b6d30d43b5eac95'
[    0.747624] registered taskstats version 1
[    0.749398] Key type trusted registered
[    0.750871] Key type encrypted registered
[    0.752310] AppArmor: AppArmor sha1 policy hashing enabled
[    0.752642]   Magic number: 1:531:408
[    0.752710] rtc_cmos 00:04: setting system clock to 2013-10-27 01:26:39 UTC (1382837199)
[    0.753198] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.753199] EDD information not available.
[    0.768464] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.039206] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.042206] isapnp: No Plug & Play device found
[    1.042460] Freeing unused kernel memory: 880K (c1962000 - c1a3e000)
[    1.042516] Write protecting the kernel text: 6356k
[    1.042592] Write protecting the kernel read-only data: 2644k
[    1.042592] NX-protecting the kernel data: 5932k
[    1.051544] systemd-udevd[108]: starting version 204
[    1.062057] mii: module verification failed: signature and/or required key missing - tainting kernel
[    1.062975] ahci 0000:00:1f.2: version 3.0
[    1.063074] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.066379] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.066582] r8169 0000:04:00.0: irq 47 for MSI/MSI-X
[    1.066722] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xf841a000, 14:da:e9:76:3c:e1, XID 0c900800 IRQ 47
[    1.066724] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.075205] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x22 impl SATA mode
[    1.075208] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.075212] ahci 0000:00:1f.2: setting latency timer to 64
[    1.083682] scsi0 : ahci
[    1.083770] scsi1 : ahci
[    1.083897] scsi2 : ahci
[    1.084040] scsi3 : ahci
[    1.084159] scsi4 : ahci
[    1.084251] scsi5 : ahci
[    1.084312] ata1: DUMMY
[    1.084314] ata2: SATA max UDMA/133 abar m2048@0xfe705000 port 0xfe705180 irq 46
[    1.084315] ata3: DUMMY
[    1.084316] ata4: DUMMY
[    1.084317] ata5: DUMMY
[    1.084319] ata6: SATA max UDMA/133 abar m2048@0xfe705000 port 0xfe705380 irq 46
[    1.171534] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.171539] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.171954] hub 1-1:1.0: USB hub found
[    1.171998] hub 1-1:1.0: 4 ports detected
[    1.283185] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.403134] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.403160] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.404464] ata6.00: ATA-8: ST31000524AS, JC4B, max UDMA/133
[    1.404470] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.406024] ata6.00: configured for UDMA/133
[    1.406393] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24NS70, GN00, max UDMA/100
[    1.410693] ata2.00: configured for UDMA/100
[    1.415478] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.415483] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.415731] hub 2-1:1.0: USB hub found
[    1.415847] hub 2-1:1.0: 6 ports detected
[    1.419017] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS70  GN00 PQ: 0 ANSI: 5
[    1.427537] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.427542] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.427695] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.427811] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.427980] scsi 5:0:0:0: Direct-Access     ATA      ST31000524AS     JC4B PQ: 0 ANSI: 5
[    1.428073] sd 5:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.428079] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.428194] sd 5:0:0:0: [sda] Write Protect is off
[    1.428197] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.428211] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.484999]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.485647] sd 5:0:0:0: [sda] Attached SCSI disk
[    1.667071] tsc: Refined TSC clocksource calibration: 3092.973 MHz
[    1.687139] usb 2-1.1: new low-speed USB device number 3 using ehci-pci
[    1.783237] usb 2-1.1: New USB device found, idVendor=046d, idProduct=c05a
[    1.783242] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.783245] usb 2-1.1: Product: USB Optical Mouse
[    1.783248] usb 2-1.1: Manufacturer: Logitech
[    1.788838] hidraw: raw HID events driver (C) Jiri Kosina
[    1.794356] usbcore: registered new interface driver usbhid
[    1.794365] usbhid: USB HID core driver
[    1.797363] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input3
[    1.797469] hid-generic 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.1/input0
[    1.855128] usb 2-1.4: new high-speed USB device number 4 using ehci-pci
[    1.963816] usb 2-1.4: New USB device found, idVendor=0cf3, idProduct=9271
[    1.963818] usb 2-1.4: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[    1.963820] usb 2-1.4: Product: USB2.0 WLAN
[    1.963821] usb 2-1.4: Manufacturer: ATHEROS
[    1.963822] usb 2-1.4: SerialNumber: 12345
[    2.667134] Switched to clocksource tsc
[    3.053623] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.053625] EXT4-fs (sda6): write access will be enabled during recovery
[    3.440763] EXT4-fs (sda6): orphan cleanup on readonly fs
[    3.440800] EXT4-fs (sda6): 1 orphan inode deleted
[    3.440801] EXT4-fs (sda6): recovery complete
[    3.506771] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    8.256911] Adding 1206268k swap on /dev/sda5.  Priority:-1 extents:1 across:1206268k FS
[    8.276123] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.327442] systemd-udevd[286]: starting version 204
[    8.415767] lp: driver loaded but no devices found
[    8.432839] wmi: Mapper loaded
[    8.436108] parport_pc 00:02: reported by Plug and Play ACPI
[    8.436156] parport0: PC-style at 0x378, irq 5 [PCSPP]
[    8.449045] mei_me 0000:00:16.0: setting latency timer to 64
[    8.449073] mei_me 0000:00:16.0: irq 48 for MSI/MSI-X
[    8.466888] [drm] Initialized drm 1.1.0 20060810
[    8.477450] cfg80211: Calling CRDA to update world regulatory domain
[    8.479008] type=1400 audit(1382817407.224:2): apparmor="STATUS" operation="profile_load" parent=320 profile="unconfined" name="/sbin/dhclient" pid=327 comm="apparmor_parser"
[    8.479014] type=1400 audit(1382817407.224:3): apparmor="STATUS" operation="profile_load" parent=320 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
[    8.479019] type=1400 audit(1382817407.224:4): apparmor="STATUS" operation="profile_load" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[    8.479463] type=1400 audit(1382817407.224:5): apparmor="STATUS" operation="profile_replace" parent=320 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
[    8.479467] type=1400 audit(1382817407.224:6): apparmor="STATUS" operation="profile_replace" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[    8.479703] type=1400 audit(1382817407.224:7): apparmor="STATUS" operation="profile_replace" parent=320 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[    8.486452] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x14
[    8.519386] [drm] radeon kernel modesetting enabled.
[    8.520777] usb 2-1.4: ath9k_htc: Firmware htc_9271.fw requested
[    8.520830] usbcore: registered new interface driver ath9k_htc
[    8.521948] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x1682:0x3202).
[    8.521963] [drm] register mmio base: 0xFE620000
[    8.521964] [drm] register mmio size: 131072
[    8.522006] ATOM BIOS: C26401
[    8.522145] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    8.522147] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    8.522148] [drm] Detected VRAM RAM=2048M, BAR=256M
[    8.522149] [drm] RAM width 64bits DDR
[    8.522182] [TTM] Zone  kernel: Available graphics memory: 425056 kiB
[    8.522184] [TTM] Zone highmem: Available graphics memory: 2056646 kiB
[    8.522185] [TTM] Initializing pool allocator
[    8.522188] [TTM] Initializing DMA pool allocator
[    8.522201] [drm] radeon: 2048M of VRAM memory ready
[    8.522203] [drm] radeon: 512M of GTT memory ready.
[    8.529583] lp0: using parport0 (interrupt-driven).
[    8.543178] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    8.543506] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    8.551222] ACPI Warning: 0x00000540-0x0000054f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20130517/utaddress-251)
[    8.551226] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.551228] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20130517/utaddress-251)
[    8.551230] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.551231] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20130517/utaddress-251)
[    8.551233] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \_GPE.GPIO 2 (20130517/utaddress-251)
[    8.551235] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.551236] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.551524] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[    8.553288] [drm] Loading CAICOS Microcode
[    8.564181] SKU: Nid=0x1d sku_cfg=0x4004c601
[    8.564183] SKU: port_connectivity=0x1
[    8.564184] SKU: enable_pcbeep=0x0
[    8.564185] SKU: check_sum=0x00000004
[    8.564186] SKU: customization=0x000000c6
[    8.564187] SKU: external_amp=0x0
[    8.564187] SKU: platform_type=0x0
[    8.564188] SKU: swap=0x0
[    8.564189] SKU: override=0x1
[    8.564472] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    8.564473]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    8.564474]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    8.564475]    mono: mono_out=0x0
[    8.564475]    dig-out=0x11/0x0
[    8.564476]    inputs:
[    8.564477]      Front Mic=0x19
[    8.564479]      Rear Mic=0x18
[    8.564479]      Line=0x1a
[    8.564480] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
[    8.564481] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
[    8.574397] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    8.574451] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    8.574490] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    8.574529] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    8.574567] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    8.602156] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[    8.602256] radeon 0000:01:00.0: WB enabled
[    8.602259] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffcf5c00
[    8.602260] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffcf5c0c
[    8.602658] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xf8bb2118
[    8.602660] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.602661] [drm] Driver supports precise vblank timestamp query.
[    8.602676] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
[    8.602684] radeon 0000:01:00.0: radeon: using MSI.
[    8.602702] [drm] radeon: irq initialized.
[    8.618861] [drm] ring test on 0 succeeded in 1 usecs
[    8.618918] [drm] ring test on 3 succeeded in 1 usecs
[    8.762137] ppdev: user-space parallel port driver
[    8.767083] asus_wmi: ASUS WMI generic driver loaded
[    8.770125] asus_wmi: Initialization: 0x0
[    8.770143] asus_wmi: BIOS WMI version: 0.9
[    8.770175] asus_wmi: SFUN value: 0x0
[    8.770405] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input9
[    8.771220] asus_wmi: Disabling ACPI video driver
[    8.772723] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x14
[    8.777159] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x14
[    8.777922] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x14
[    8.778307] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.783223] kvm: disabled by bios
[    8.814384] [drm] ring test on 5 succeeded in 1 usecs
[    8.814387] [drm] UVD initialized successfully.
[    8.814499] [drm] ib test on ring 0 succeeded in 0 usecs
[    8.814521] [drm] ib test on ring 3 succeeded in 0 usecs
[    8.820757] usb 2-1.4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[    8.933248] cfg80211: World regulatory domain updated:
[    8.933251] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.933252] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.933253] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.933254] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.933255] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.933256] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.984635] [drm] ib test on ring 5 succeeded
[    8.984864] [drm] Radeon Display Connectors
[    8.984866] [drm] Connector 0:
[    8.984867] [drm]   HDMI-A-1
[    8.984867] [drm]   HPD2
[    8.984869] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    8.984869] [drm]   Encoders:
[    8.984870] [drm]     DFP1: INTERNAL_UNIPHY1
[    8.984871] [drm] Connector 1:
[    8.984872] [drm]   DVI-I-1
[    8.984873] [drm]   HPD4
[    8.984874] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    8.984875] [drm]   Encoders:
[    8.984876] [drm]     DFP2: INTERNAL_UNIPHY
[    8.984876] [drm] Connector 2:
[    8.984877] [drm]   VGA-1
[    8.984878] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    8.984879] [drm]   Encoders:
[    8.984880] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.984923] [drm] Internal thermal controller without fan control
[    8.985715] [drm] radeon: power management initialized
[    9.019184] [drm] fb mappable at 0xC0375000
[    9.019186] [drm] vram apper at 0xC0000000
[    9.019187] [drm] size 8294400
[    9.019187] [drm] fb depth is 24
[    9.019188] [drm]    pitch is 7680
[    9.019266] fbcon: radeondrmfb (fb0) is primary device
[    9.056862] ath9k_htc 2-1.4:1.0: ath9k_htc: HTC initialized with 33 credits
[    9.226292] Console: switching to colour frame buffer device 240x67
[    9.231329] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    9.231330] radeon 0000:01:00.0: registered panic notifier
[    9.231334] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
[    9.231418] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    9.231420] hda-intel 0000:01:00.1: Using LPIB position fix
[    9.231453] snd_hda_intel 0000:01:00.1: irq 51 for MSI/MSI-X
[    9.233936] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[    9.238920] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    9.250534] ath9k_htc 2-1.4:1.0: ath9k_htc: FW Version: 1.3
[    9.250537] ath: EEPROM regdomain: 0x809c
[    9.250538] ath: EEPROM indicates we should expect a country code
[    9.250539] ath: doing EEPROM country->regdmn map search
[    9.250540] ath: country maps to regdmn code: 0x52
[    9.250541] ath: Country alpha2 being used: CN
[    9.250542] ath: Regpair used: 0x52
[    9.254954] ieee80211 phy0: Atheros AR9271 Rev:1
[    9.254962] cfg80211: Calling CRDA for country: CN
[    9.257025] cfg80211: Regulatory domain changed to country: CN
[    9.257027] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.257028] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    9.257029] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[    9.257031] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[    9.257032] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm)
[    9.257032] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm)
[   10.607915] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   12.727677] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   12.962959] init: failsafe main process (633) killed by TERM signal
[   13.155718] Bluetooth: Core ver 2.16
[   13.155730] NET: Registered protocol family 31
[   13.155731] Bluetooth: HCI device and connection manager initialized
[   13.155736] Bluetooth: HCI socket layer initialized
[   13.155738] Bluetooth: L2CAP socket layer initialized
[   13.155741] Bluetooth: SCO socket layer initialized
[   13.164675] Bluetooth: RFCOMM TTY layer initialized
[   13.164683] Bluetooth: RFCOMM socket layer initialized
[   13.164684] Bluetooth: RFCOMM ver 1.11
[   13.168326] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.168328] Bluetooth: BNEP filters: protocol multicast
[   13.168332] Bluetooth: BNEP socket layer initialized
[   13.290996] type=1400 audit(1382817412.036:8): apparmor="STATUS" operation="profile_replace" parent=781 profile="unconfined" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[   13.291003] type=1400 audit(1382817412.036:9): apparmor="STATUS" operation="profile_replace" parent=781 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   13.291006] type=1400 audit(1382817412.036:10): apparmor="STATUS" operation="profile_replace" parent=781 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   13.291211] type=1400 audit(1382817412.036:11): apparmor="STATUS" operation="profile_load" parent=781 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=787 comm="apparmor_parser"
[   13.322529] init: avahi-cups-reload main process (797) terminated with status 1
[   13.950433] r8169 0000:04:00.0 eth0: link down
[   13.950454] r8169 0000:04:00.0 eth0: link down
[   13.950487] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.950719] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.049839] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.050094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.455763] r8169 0000:04:00.0 eth0: link up
[   15.455769] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.454081] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
[   24.454087] radeon 0000:01:00.0: GPU lockup (waiting for 0x0000000000000004 last fence id 0x0000000000000001)
[   24.461064] radeon 0000:01:00.0: Saved 119 dwords of commands on ring 0.
[   24.461072] radeon 0000:01:00.0: GPU softreset: 0x00000008
[   24.461073] radeon 0000:01:00.0:   GRBM_STATUS               = 0xA0003828
[   24.461075] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   24.461076] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   24.461078] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   24.461079] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   24.461080] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   24.461082] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010100
[   24.461083] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020180
[   24.461085] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80038042
[   24.461086] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   24.472726] radeon 0000:01:00.0: GRBM_SOFT_RESET=0x00004001
[   24.472778] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
[   24.473922] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   24.473924] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   24.473925] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   24.473926] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   24.473928] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   24.473929] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   24.473930] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   24.473932] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   24.473933] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   24.473935] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   24.473940] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
[   24.491647] [drm] PCIE gen 2 link speeds already enabled
[   24.493423] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[   24.493504] radeon 0000:01:00.0: WB enabled
[   24.493506] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffcf5c00
[   24.493507] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffcf5c0c
[   24.493904] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xf8bb2118
[   24.509980] [drm] ring test on 0 succeeded in 1 usecs
[   24.510036] [drm] ring test on 3 succeeded in 1 usecs
[   24.705480] [drm] ring test on 5 succeeded in 1 usecs
[   24.705482] [drm] UVD initialized successfully.
[   24.710093] [drm] ib test on ring 0 succeeded in 0 usecs
[   24.710126] [drm] ib test on ring 3 succeeded in 1 usecs
[   24.880325] [drm] ib test on ring 5 succeeded
[   35.503607] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
[   35.503638] radeon 0000:01:00.0: GPU lockup (waiting for 0x0000000000000006 last fence id 0x0000000000000005)
[   35.510615] radeon 0000:01:00.0: Saved 55 dwords of commands on ring 0.
[   35.510622] radeon 0000:01:00.0: GPU softreset: 0x00000108
[   35.510624] radeon 0000:01:00.0:   GRBM_STATUS               = 0xA0003828
[   35.510626] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   35.510627] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   35.510628] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200200C0
[   35.510630] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   35.510631] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   35.510633] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010100
[   35.510634] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020180
[   35.510636] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80038042
[   35.510637] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   35.525668] radeon 0000:01:00.0: GRBM_SOFT_RESET=0x00004001
[   35.525719] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000500
[   35.526863] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   35.526865] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   35.526866] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   35.526868] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200200C0
[   35.526869] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   35.526871] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   35.526872] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   35.526873] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   35.526875] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   35.526876] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   35.526881] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
[   35.526886] radeon 0000:01:00.0: GPU softreset: 0x00000100
[   35.526888] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   35.526889] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   35.526890] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   35.526892] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200200C0
[   35.526893] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   35.526895] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   35.526896] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   35.526897] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   35.526899] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   35.526900] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   35.527055] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000400
[   35.528199] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   35.528200] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   35.528201] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   35.528203] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200200C0
[   35.528204] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   35.528205] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   35.528207] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   35.528208] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   35.528210] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   35.528211] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   35.544586] [drm] PCIE gen 2 link speeds already enabled
[   35.546355] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[   35.546437] radeon 0000:01:00.0: WB enabled
[   35.546439] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffcf5c00
[   35.546440] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffcf5c0c
[   35.546836] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xf8bb2118
[   35.562896] [drm] ring test on 0 succeeded in 1 usecs
[   35.562952] [drm] ring test on 3 succeeded in 1 usecs
[   35.758394] [drm] ring test on 5 succeeded in 1 usecs
[   35.758396] [drm] UVD initialized successfully.
[   35.758476] [drm] ib test on ring 0 succeeded in 0 usecs
[   35.758501] [drm] ib test on ring 3 succeeded in 1 usecs
[   35.928671] [drm] ib test on ring 5 succeeded
[   47.173030] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
[   47.173063] radeon 0000:01:00.0: GPU lockup (waiting for 0x0000000000000009 last fence id 0x0000000000000007)
[   47.180042] radeon 0000:01:00.0: Saved 55 dwords of commands on ring 0.
[   47.180050] radeon 0000:01:00.0: GPU softreset: 0x00000008
[   47.180052] radeon 0000:01:00.0:   GRBM_STATUS               = 0xA0003828
[   47.180053] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   47.180054] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   47.180056] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   47.180057] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   47.180059] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   47.180060] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
[   47.180062] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020184
[   47.180063] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80038647
[   47.180065] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   47.191749] radeon 0000:01:00.0: GRBM_SOFT_RESET=0x00004001
[   47.191800] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
[   47.192944] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   47.192946] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   47.192947] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   47.192949] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   47.192950] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   47.192951] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   47.192953] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   47.192954] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   47.192956] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   47.192957] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   47.192962] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
[   47.210687] [drm] PCIE gen 2 link speeds already enabled
[   47.212481] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[   47.212567] radeon 0000:01:00.0: WB enabled
[   47.212569] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffcf5c00
[   47.212570] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffcf5c0c
[   47.212969] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xf8bb2118
[   47.229056] [drm] ring test on 0 succeeded in 1 usecs
[   47.229112] [drm] ring test on 3 succeeded in 1 usecs
[   47.424556] [drm] ring test on 5 succeeded in 1 usecs
[   47.424558] [drm] UVD initialized successfully.
[   47.424749] [drm] ib test on ring 0 succeeded in 0 usecs
[   47.424782] [drm] ib test on ring 3 succeeded in 1 usecs
[   47.594903] [drm] ib test on ring 5 succeeded
[   58.226627] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
[   58.226692] radeon 0000:01:00.0: GPU lockup (waiting for 0x000000000000000d last fence id 0x000000000000000c)
[   58.233675] radeon 0000:01:00.0: Saved 23 dwords of commands on ring 0.
[   58.233683] radeon 0000:01:00.0: GPU softreset: 0x00000008
[   58.233685] radeon 0000:01:00.0:   GRBM_STATUS               = 0xA0003828
[   58.233686] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   58.233687] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   58.233689] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   58.233690] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   58.233692] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   58.233693] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00010002
[   58.233695] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00020180
[   58.233696] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x80038647
[   58.233698] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   58.240653] radeon 0000:01:00.0: GRBM_SOFT_RESET=0x00004001
[   58.240705] radeon 0000:01:00.0: SRBM_SOFT_RESET=0x00000100
[   58.241849] radeon 0000:01:00.0:   GRBM_STATUS               = 0x00003828
[   58.241850] radeon 0000:01:00.0:   GRBM_STATUS_SE0           = 0x00000007
[   58.241852] radeon 0000:01:00.0:   GRBM_STATUS_SE1           = 0x00000007
[   58.241853] radeon 0000:01:00.0:   SRBM_STATUS               = 0x200000C0
[   58.241855] radeon 0000:01:00.0:   SRBM_STATUS2              = 0x00000000
[   58.241856] radeon 0000:01:00.0:   R_008674_CP_STALLED_STAT1 = 0x00000000
[   58.241858] radeon 0000:01:00.0:   R_008678_CP_STALLED_STAT2 = 0x00000000
[   58.241859] radeon 0000:01:00.0:   R_00867C_CP_BUSY_STAT     = 0x00000000
[   58.241860] radeon 0000:01:00.0:   R_008680_CP_STAT          = 0x00000000
[   58.241862] radeon 0000:01:00.0:   R_00D034_DMA_STATUS_REG   = 0x44C83D57
[   58.241867] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
[   58.259589] [drm] PCIE gen 2 link speeds already enabled
[   58.261361] [drm] PCIE GART of 512M enabled (table at 0x0000000000273000).
[   58.261447] radeon 0000:01:00.0: WB enabled
[   58.261449] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffcf5c00
[   58.261450] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffcf5c0c
[   58.261847] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xf8bb2118
[   58.277906] [drm] ring test on 0 succeeded in 1 usecs
[   58.277962] [drm] ring test on 3 succeeded in 1 usecs
[   58.473404] [drm] ring test on 5 succeeded in 1 usecs
[   58.473407] [drm] UVD initialized successfully.
[   58.473430] [drm] ib test on ring 0 succeeded in 0 usecs
[   58.473452] [drm] ib test on ring 3 succeeded in 1 usecs
[   58.643572] [drm] ib test on ring 5 succeeded
[   85.449605] usb 2-1.1: USB disconnect, device number 3
[   86.928394] usb 2-1.1: new low-speed USB device number 5 using ehci-pci
[   87.024497] usb 2-1.1: New USB device found, idVendor=046d, idProduct=c05a
[   87.024499] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   87.024501] usb 2-1.1: Product: USB Optical Mouse
[   87.024502] usb 2-1.1: Manufacturer: Logitech
[   87.026979] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input11
[   87.027354] hid-generic 0003:046D:C05A.0002: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.1/input0
[  147.131578] usb 2-1.1: USB disconnect, device number 5
[  148.610868] usb 2-1.1: new low-speed USB device number 6 using ehci-pci
[  148.706844] usb 2-1.1: New USB device found, idVendor=046d, idProduct=c05a
[  148.706847] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  148.706848] usb 2-1.1: Product: USB Optical Mouse
[  148.706850] usb 2-1.1: Manufacturer: Logitech
[  148.708951] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input12
[  148.709151] hid-generic 0003:046D:C05A.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.1/input0


```

---

### Post by Yellow Pasque on 2013-10-27
> I may be able to fix it by installing fglrx , but then I have to install it eveytime the kernel is updated.
If you have to do that, then you're installing it incorrectly. Either use the package provided by Ubuntu, or make sure you have dkms installed: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by ripthejacker_ on 2013-10-27
So no help with the open source drivers?

---

### Post by ripthejacker_ on 2013-10-27
Fixed the problem.
I just added 'radeon.dpm=1' to the boot parameters before 'quiet splash'.
You can do this by editing /etc/default/grub and , then add 'radeon.dpm=1' in the line GRUB_CMDLINE_LINUX_DEFAULT, so it looks like this
```
GRUB_CMDLINE_LINUX_DEFAULT="radeon.dpm=1 quiet splash"
```.
Also remove the parameter 'nomodeset' if present.

---

