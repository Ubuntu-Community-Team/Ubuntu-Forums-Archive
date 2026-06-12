---
title: "Problems with post installation configuration"
date: 2016-06-24
forum: Mythbuntu
---

### Post by Espryon on 2016-06-24
So... this is the first time I've done something like this. I installed it and the driver for my dads network card was not included so I had to download and manually install the driver. I then tried to as the instructions from the website mentioned configure the backend + the frontend. I tried using defaults but, the backend database kept saying the default user was denied access, (I will post logs) and the frontend configuration window kept crashing. The network that I'm trying to put the mythbuntu box onto is a 192.168.2.0/24 network. Is there anything special I have to do? It also acted like since I swapped the network configuration manually that parts of the OS didn't update (I don't know if this is the case but, this is my guess).

Thanks,

Espryon

---

### Post by QIII on 2016-06-24
Hello!

What is "it" in "installed it"?  What is the hardware?

You haven't given us anything to go on here.

---

### Post by Espryon on 2016-06-24
sec, I'll post a dmesg.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-21-generic (buildd@lgw01-21) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 (Ubuntu 4.4.0-21.37-generic 4.4.6)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.4.0-21-generic root=/dev/mapper/mythbuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] tseg: 00bf800000
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000be864fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000be865000-0x00000000bea3cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bea3d000-0x00000000bea46fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bea47000-0x00000000bee34fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bee35000-0x00000000bf15bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf15c000-0x00000000bf15cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf15d000-0x00000000bf362fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf363000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000023effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./990FXA-UD3, BIOS F2 07/15/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x23f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000BF800000 mask FFFFFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000023f000000 aka 9200M
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] total RAM covered: 3064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3064MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xbf800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd850-0x000fd85f] mapped at [ffff8800000fd850]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x021fe000, 0x021fefff] PGTABLE
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x336b8000-0x35b53fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000BEA3F068 000054 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000BEA44D18 0000F4 (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20150930/tbfadt-654)
[    0.000000] ACPI: DSDT 0x00000000BEA3F150 005BC1 (v02 ALASKA A M I    00000000 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000BEE2FF80 000040
[    0.000000] ACPI: APIC 0x00000000BEA44E10 00008E (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000BEA44EA0 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000BEA44EE8 00003C (v01 ALASKA A M I    01072009 MSFT 00010013)
[    0.000000] ACPI: HPET 0x00000000BEA44F28 000038 (v01 ALASKA A M I    01072009 AMI  00000005)
[    0.000000] ACPI: SSDT 0x00000000BEA44F60 001158 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x23eff7000-0x23effbfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000023effffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000be864fff]
[    0.000000]   node   0: [mem 0x00000000bf15c000-0x00000000bf15cfff]
[    0.000000]   node   0: [mem 0x00000000bf363000-0x00000000bf7fffff]
[    0.000000]   node   0: [mem 0x0000000100001000-0x000000023effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023effffff]
[    0.000000] On node 0 totalpages: 2088095
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12149 pages used for memmap
[    0.000000]   DMA32 zone: 777475 pages, LIFO batch:31
[    0.000000]   Normal zone: 20416 pages used for memmap
[    0.000000]   Normal zone: 1306623 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 7, version 33, address 0xfec00000, GSI 0-23
[    0.000000] IOAPIC[1]: apic_id 8, version 33, address 0xfec20000, GSI 24-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 6 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbe865000-0xbea3cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbea3d000-0xbea46fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbea47000-0xbee34fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbee35000-0xbf15bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf15d000-0xbf362fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
[    0.000000] e820: [mem 0xbf800000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88023ec00000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2055445
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.4.0-21-generic root=/dev/mapper/mythbuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0xf8000000-0xfbffffff] (64MB)
[    0.000000] Memory: 8098156K/8352380K available (8356K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 254224K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=6.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=6
[    0.000000] NR_IRQS:16640 nr_irqs:1016 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484873504 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3515.758 MHz processor
[    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 7031.51 BogoMIPS (lpj=14063032)
[    0.000025] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20150930
[    0.002683] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.002701] Security Framework initialized
[    0.002703] Yama: becoming mindful.
[    0.002716] AppArmor: AppArmor initialized
[    0.003203] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005245] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.006121] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.006130] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.006343] Initializing cgroup subsys io
[    0.006346] Initializing cgroup subsys memory
[    0.006353] Initializing cgroup subsys devices
[    0.006357] Initializing cgroup subsys freezer
[    0.006359] Initializing cgroup subsys net_cls
[    0.006361] Initializing cgroup subsys perf_event
[    0.006363] Initializing cgroup subsys net_prio
[    0.006365] Initializing cgroup subsys hugetlb
[    0.006368] Initializing cgroup subsys pids
[    0.006386] CPU: Physical Processor ID: 0
[    0.006387] CPU: Processor Core ID: 0
[    0.006389] mce: CPU supports 7 MCE banks
[    0.006395] LVT offset 1 assigned for vector 0xf9
[    0.006400] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.006401] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512, 1GB 0
[    0.006638] Freeing SMP alternatives memory: 28K (ffffffff820b2000 - ffffffff820b9000)
[    0.010850] ftrace: allocating 31878 entries in 125 pages
[    0.020692] smpboot: Max logical packages: 2
[    0.020694] smpboot: APIC(10) Converting physical 1 to logical package 0
[    0.021032] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.167680] smpboot: CPU0: AMD FX(tm)-6300 Six-Core Processor (family: 0x15, model: 0x2, stepping: 0x0)
[    0.167693] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.167697] ... version:                0
[    0.167698] ... bit width:              48
[    0.167699] ... generic registers:      6
[    0.167700] ... value mask:             0000ffffffffffff
[    0.167701] ... max period:             00007fffffffffff
[    0.167701] ... fixed-purpose events:   0
[    0.167702] ... event mask:             000000000000003f
[    0.168388] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.168449] x86: Booting SMP configuration:
[    0.168450] .... node  #0, CPUs:      #1 #2 #3 #4 #5
[    0.182349] x86: Booted up 1 node, 6 CPUs
[    0.182352] smpboot: Total of 6 processors activated (42189.09 BogoMIPS)
[    0.190119] devtmpfs: initialized
[    0.193045] evm: security.selinux
[    0.193046] evm: security.SMACK64
[    0.193047] evm: security.SMACK64EXEC
[    0.193048] evm: security.SMACK64TRANSMUTE
[    0.193049] evm: security.SMACK64MMAP
[    0.193050] evm: security.ima
[    0.193051] evm: security.capability
[    0.193118] PM: Registering ACPI NVS region [mem 0xbea47000-0xbee34fff] (4120576 bytes)
[    0.193168] PM: Registering ACPI NVS region [mem 0xbf15d000-0xbf362fff] (2121728 bytes)
[    0.193270] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.193349] pinctrl core: initialized pinctrl subsystem
[    0.193445] RTC time:  4:36:04, date: 06/24/16
[    0.193543] NET: Registered protocol family 16
[    0.203685] cpuidle: using governor ladder
[    0.215684] cpuidle: using governor menu
[    0.215688] PCCT header not found.
[    0.215757] ACPI: bus type PCI registered
[    0.215759] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.215823] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.215825] PCI: not using MMCONFIG
[    0.215826] PCI: Using configuration type 1 for base access
[    0.215827] PCI: Using configuration type 1 for extended access
[    0.228081] ACPI: Added _OSI(Module Device)
[    0.228082] ACPI: Added _OSI(Processor Device)
[    0.228084] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.228085] ACPI: Added _OSI(Processor Aggregator Device)
[    0.229495] ACPI: Executed 3 blocks of module-level executable AML code
[    0.231631] ACPI: Interpreter enabled
[    0.231636] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.231640] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.231651] ACPI: (supports S0 S3 S4 S5)
[    0.231652] ACPI: Using IOAPIC for interrupt routing
[    0.231772] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.231804] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.231814] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.236500] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.236504] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.236508] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.236768] PCI host bridge to bus 0000:00
[    0.236771] pci_bus 0000:00: root bus resource [io  0x0000-0x03af window]
[    0.236773] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7 window]
[    0.236774] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df window]
[    0.236776] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.236778] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.236779] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.236781] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff window]
[    0.236783] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.236817] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
[    0.236927] pci 0000:00:04.0: [1002:5a18] type 01 class 0x060400
[    0.236958] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.236997] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.237034] pci 0000:00:09.0: [1002:5a1c] type 01 class 0x060400
[    0.237064] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.237102] pci 0000:00:09.0: System wakeup disabled by ACPI
[    0.237136] pci 0000:00:0a.0: [1002:5a1d] type 01 class 0x060400
[    0.237165] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.237205] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.237247] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.237267] pci 0000:00:11.0: reg 0x10: [io  0xf090-0xf097]
[    0.237274] pci 0000:00:11.0: reg 0x14: [io  0xf080-0xf083]
[    0.237281] pci 0000:00:11.0: reg 0x18: [io  0xf070-0xf077]
[    0.237288] pci 0000:00:11.0: reg 0x1c: [io  0xf060-0xf063]
[    0.237295] pci 0000:00:11.0: reg 0x20: [io  0xf050-0xf05f]
[    0.237302] pci 0000:00:11.0: reg 0x24: [mem 0xfeb0b000-0xfeb0b3ff]
[    0.237388] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.237400] pci 0000:00:12.0: reg 0x10: [mem 0xfeb0a000-0xfeb0afff]
[    0.237475] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.237513] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.237532] pci 0000:00:12.2: reg 0x10: [mem 0xfeb09000-0xfeb090ff]
[    0.237584] pci 0000:00:12.2: supports D1 D2
[    0.237585] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.237624] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.237662] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.237674] pci 0000:00:13.0: reg 0x10: [mem 0xfeb08000-0xfeb08fff]
[    0.237750] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.237788] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.237807] pci 0000:00:13.2: reg 0x10: [mem 0xfeb07000-0xfeb070ff]
[    0.237859] pci 0000:00:13.2: supports D1 D2
[    0.237861] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.237899] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.237937] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.238048] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.238060] pci 0000:00:14.1: reg 0x10: [io  0xf040-0xf047]
[    0.238067] pci 0000:00:14.1: reg 0x14: [io  0xf030-0xf033]
[    0.238074] pci 0000:00:14.1: reg 0x18: [io  0xf020-0xf027]
[    0.238081] pci 0000:00:14.1: reg 0x1c: [io  0xf010-0xf013]
[    0.238088] pci 0000:00:14.1: reg 0x20: [io  0xf000-0xf00f]
[    0.238103] pci 0000:00:14.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.238104] pci 0000:00:14.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.238106] pci 0000:00:14.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.238107] pci 0000:00:14.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.238175] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.238195] pci 0000:00:14.2: reg 0x10: [mem 0xfeb00000-0xfeb03fff 64bit]
[    0.238239] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.238277] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.238311] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.238424] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.238486] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.238521] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.238533] pci 0000:00:14.5: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
[    0.238609] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.238647] pci 0000:00:15.0: [1002:43a0] type 01 class 0x060400
[    0.238698] pci 0000:00:15.0: supports D1 D2
[    0.238739] pci 0000:00:15.0: System wakeup disabled by ACPI
[    0.238777] pci 0000:00:15.2: [1002:43a2] type 01 class 0x060400
[    0.238828] pci 0000:00:15.2: supports D1 D2
[    0.238868] pci 0000:00:15.2: System wakeup disabled by ACPI
[    0.238908] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.238920] pci 0000:00:16.0: reg 0x10: [mem 0xfeb05000-0xfeb05fff]
[    0.238996] pci 0000:00:16.0: System wakeup disabled by ACPI
[    0.239034] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.239053] pci 0000:00:16.2: reg 0x10: [mem 0xfeb04000-0xfeb040ff]
[    0.239105] pci 0000:00:16.2: supports D1 D2
[    0.239106] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.239145] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.239183] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.239252] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.239320] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.239387] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.239454] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.239519] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.239628] pci 0000:01:00.0: [1002:6758] type 00 class 0x030000
[    0.239653] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.239663] pci 0000:01:00.0: reg 0x18: [mem 0xfea20000-0xfea3ffff 64bit]
[    0.239670] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.239685] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.239713] pci 0000:01:00.0: supports D1 D2
[    0.239761] pci 0000:01:00.1: [1002:aa90] type 00 class 0x040300
[    0.239786] pci 0000:01:00.1: reg 0x10: [mem 0xfea40000-0xfea43fff 64bit]
[    0.239840] pci 0000:01:00.1: supports D1 D2
[    0.247693] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.247697] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.247699] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.247702] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.247769] pci 0000:02:00.0: [1106:3483] type 00 class 0x0c0330
[    0.247789] pci 0000:02:00.0: reg 0x10: [mem 0xfe900000-0xfe900fff 64bit]
[    0.247835] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.255690] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.255694] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.255735] pci 0000:03:00.0: [1b4b:9172] type 00 class 0x010601
[    0.255753] pci 0000:03:00.0: reg 0x10: [io  0xd040-0xd047]
[    0.255759] pci 0000:03:00.0: reg 0x14: [io  0xd030-0xd033]
[    0.255765] pci 0000:03:00.0: reg 0x18: [io  0xd020-0xd027]
[    0.255771] pci 0000:03:00.0: reg 0x1c: [io  0xd010-0xd013]
[    0.255777] pci 0000:03:00.0: reg 0x20: [io  0xd000-0xd00f]
[    0.255783] pci 0000:03:00.0: reg 0x24: [mem 0xfe810000-0xfe8101ff]
[    0.255789] pci 0000:03:00.0: reg 0x30: [mem 0xfe800000-0xfe80ffff pref]
[    0.255813] pci 0000:03:00.0: PME# supported from D3hot
[    0.263689] pci 0000:00:0a.0: PCI bridge to [bus 03]
[    0.263693] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.263695] pci 0000:00:0a.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.263748] pci 0000:04:0e.0: [1106:3044] type 00 class 0x0c0010
[    0.263773] pci 0000:04:0e.0: reg 0x10: [mem 0xfe700000-0xfe7007ff]
[    0.263783] pci 0000:04:0e.0: reg 0x14: [io  0xc000-0xc07f]
[    0.263853] pci 0000:04:0e.0: supports D2
[    0.263855] pci 0000:04:0e.0: PME# supported from D2 D3hot D3cold
[    0.263914] pci 0000:00:14.4: PCI bridge to [bus 04] (subtractive decode)
[    0.263917] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.263921] pci 0000:00:14.4:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.263924] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af window] (subtractive decode)
[    0.263925] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7 window] (subtractive decode)
[    0.263927] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df window] (subtractive decode)
[    0.263928] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.263930] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.263932] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.263933] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff window] (subtractive decode)
[    0.263995] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    0.264030] pci 0000:05:00.0: reg 0x10: [io  0xb000-0xb0ff]
[    0.264055] pci 0000:05:00.0: reg 0x18: [mem 0xfe600000-0xfe600fff 64bit]
[    0.264071] pci 0000:05:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.264134] pci 0000:05:00.0: supports D1 D2
[    0.264136] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264171] pci 0000:05:00.0: System wakeup disabled by ACPI
[    0.271695] pci 0000:00:15.0: PCI bridge to [bus 05]
[    0.271699] pci 0000:00:15.0:   bridge window [io  0xb000-0xbfff]
[    0.271702] pci 0000:00:15.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.271706] pci 0000:00:15.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.271765] pci 0000:06:00.0: [14f1:8880] type 00 class 0x040000
[    0.271818] pci 0000:06:00.0: reg 0x10: [mem 0xfe400000-0xfe5fffff 64bit]
[    0.271944] pci 0000:06:00.0: supports D1 D2
[    0.271946] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.279694] pci 0000:00:15.2: PCI bridge to [bus 06]
[    0.279701] pci 0000:00:15.2:   bridge window [mem 0xfe400000-0xfe5fffff]
[    0.280093] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.280146] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.280201] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.280254] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
[    0.280298] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 10 11 14 15) *0
[    0.280332] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 10 11 14 15) *0
[    0.280366] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 11 14 15) *0
[    0.280400] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 10 11 14 15) *0
[    0.280595] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.280597] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.280599] vgaarb: loaded
[    0.280600] vgaarb: bridge control possible 0000:01:00.0
[    0.280823] SCSI subsystem initialized
[    0.280873] libata version 3.00 loaded.
[    0.280895] ACPI: bus type USB registered
[    0.280911] usbcore: registered new interface driver usbfs
[    0.280920] usbcore: registered new interface driver hub
[    0.280942] usbcore: registered new device driver usb
[    0.281093] PCI: Using ACPI for IRQ routing
[    0.287357] PCI: pci_cache_line_size set to 64 bytes
[    0.287415] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.287416] e820: reserve RAM buffer [mem 0xbe865000-0xbfffffff]
[    0.287418] e820: reserve RAM buffer [mem 0xbf15d000-0xbfffffff]
[    0.287419] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.287420] e820: reserve RAM buffer [mem 0x23f000000-0x23fffffff]
[    0.287520] NetLabel: Initializing
[    0.287521] NetLabel:  domain hash size = 128
[    0.287522] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.287531] NetLabel:  unlabeled traffic allowed by default
[    0.287596] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.287599] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.289649] clocksource: Switched to clocksource hpet
[    0.295856] AppArmor: AppArmor Filesystem Enabled
[    0.295903] pnp: PnP ACPI init
[    0.295994] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.295997] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.296217] system 00:01: [io  0x040b] has been reserved
[    0.296219] system 00:01: [io  0x04d6] has been reserved
[    0.296221] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.296223] system 00:01: [io  0x0c14] has been reserved
[    0.296224] system 00:01: [io  0x0c50-0x0c51] has been reserved
[    0.296226] system 00:01: [io  0x0c52] has been reserved
[    0.296228] system 00:01: [io  0x0c6c] has been reserved
[    0.296229] system 00:01: [io  0x0c6f] has been reserved
[    0.296231] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.296232] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.296234] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
[    0.296235] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
[    0.296237] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
[    0.296238] system 00:01: [io  0x0800-0x089f] could not be reserved
[    0.296240] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.296242] system 00:01: [io  0x0900-0x090f] has been reserved
[    0.296243] system 00:01: [io  0x0910-0x091f] has been reserved
[    0.296245] system 00:01: [io  0xfe00-0xfefe] has been reserved
[    0.296247] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.296249] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.296251] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.296253] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.296255] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.296257] system 00:01: [mem 0xfed00000-0xfed00fff] could not be reserved
[    0.296259] system 00:01: [mem 0xffc00000-0xffffffff] has been reserved
[    0.296261] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296387] system 00:02: [io  0x0220-0x0227] has been reserved
[    0.296389] system 00:02: [io  0x0228-0x0237] has been reserved
[    0.296391] system 00:02: [io  0x0a20-0x0a2f] has been reserved
[    0.296393] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296595] pnp 00:03: [dma 0 disabled]
[    0.296632] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.296656] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.296709] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.296712] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296751] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296862] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.296956] system 00:08: [mem 0xfec20000-0xfec200ff] could not be reserved
[    0.296958] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.297044] pnp: PnP ACPI: found 9 devices
[    0.303574] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.303602] pci 0000:00:04.0: PCI bridge to [bus 01]
[    0.303604] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.303607] pci 0000:00:04.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.303610] pci 0000:00:04.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.303613] pci 0000:00:09.0: PCI bridge to [bus 02]
[    0.303615] pci 0000:00:09.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.303619] pci 0000:00:0a.0: PCI bridge to [bus 03]
[    0.303620] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.303623] pci 0000:00:0a.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.303627] pci 0000:00:14.4: PCI bridge to [bus 04]
[    0.303629] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.303633] pci 0000:00:14.4:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.303639] pci 0000:00:15.0: PCI bridge to [bus 05]
[    0.303641] pci 0000:00:15.0:   bridge window [io  0xb000-0xbfff]
[    0.303644] pci 0000:00:15.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.303647] pci 0000:00:15.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.303651] pci 0000:00:15.2: PCI bridge to [bus 06]
[    0.303654] pci 0000:00:15.2:   bridge window [mem 0xfe400000-0xfe5fffff]
[    0.303660] pci_bus 0000:00: resource 4 [io  0x0000-0x03af window]
[    0.303662] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7 window]
[    0.303663] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df window]
[    0.303665] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
[    0.303666] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.303668] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.303669] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff window]
[    0.303671] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.303672] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.303674] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.303675] pci_bus 0000:02: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.303677] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.303678] pci_bus 0000:03: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.303680] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.303681] pci_bus 0000:04: resource 1 [mem 0xfe700000-0xfe7fffff]
[    0.303683] pci_bus 0000:04: resource 4 [io  0x0000-0x03af window]
[    0.303684] pci_bus 0000:04: resource 5 [io  0x03e0-0x0cf7 window]
[    0.303685] pci_bus 0000:04: resource 6 [io  0x03b0-0x03df window]
[    0.303687] pci_bus 0000:04: resource 7 [io  0x0d00-0xffff window]
[    0.303688] pci_bus 0000:04: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.303690] pci_bus 0000:04: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.303691] pci_bus 0000:04: resource 10 [mem 0xc0000000-0xffffffff window]
[    0.303693] pci_bus 0000:05: resource 0 [io  0xb000-0xbfff]
[    0.303694] pci_bus 0000:05: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.303695] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.303697] pci_bus 0000:06: resource 1 [mem 0xfe400000-0xfe5fffff]
[    0.303722] NET: Registered protocol family 2
[    0.303881] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.304050] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.304254] TCP: Hash tables configured (established 65536 bind 65536)
[    0.304298] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.304333] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.304395] NET: Registered protocol family 1
[    0.629724] pci 0000:01:00.0: Video device with shadowed ROM
[    0.629752] PCI: CLS 64 bytes, default 64
[    0.629798] Trying to unpack rootfs image as initramfs...
[    1.131355] Freeing initrd memory: 37488K (ffff8800336b8000 - ffff880035b54000)
[    1.132966] PCI-DMA: Disabling AGP.
[    1.133035] PCI-DMA: aperture base @ f8000000 size 65536 KB
[    1.133043] PCI-DMA: using GART IOMMU.
[    1.133045] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.136817] perf: AMD NB counters detected
[    1.136856] LVT offset 0 assigned for vector 0x400
[    1.136871] perf: AMD IBS detected (0x000000ff)
[    1.136943] Scanning for low memory corruption every 60 seconds
[    1.137312] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.137345] audit: initializing netlink subsys (disabled)
[    1.137358] audit: type=2000 audit(1466742965.024:1): initialized
[    1.137643] Initialise system trusted keyring
[    1.137778] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    1.137779] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.139350] zbud: loaded
[    1.139528] VFS: Disk quotas dquot_6.6.0
[    1.139561] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.140050] fuse init (API version 7.23)
[    1.140170] Key type big_key registered
[    1.140627] Key type asymmetric registered
[    1.140629] Asymmetric key parser 'x509' registered
[    1.140663] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.140701] io scheduler noop registered
[    1.140703] io scheduler deadline registered (default)
[    1.140732] io scheduler cfq registered
[    1.141164] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.141170] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.141198] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
[    1.141199] vesafb: scrolling: redraw
[    1.141201] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.141211] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 5824k, total 5824k
[    1.141310] Console: switching to colour frame buffer device 175x65
[    1.141328] fb0: VESA VGA frame buffer device
[    1.141403] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.141407] ACPI: Power Button [PWRB]
[    1.141444] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.141445] ACPI: Power Button [PWRF]
[    1.141475] ACPI: acpi_idle registered with cpuidle
[    1.142055] GHES: HEST is not enabled!
[    1.142167] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.162513] 00:03: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.164039] Linux agpgart interface v0.103
[    1.167195] brd: module loaded
[    1.168474] loop: module loaded
[    1.168778] libphy: Fixed MDIO Bus: probed
[    1.168781] tun: Universal TUN/TAP device driver, 1.6
[    1.168782] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.168820] PPP generic driver version 2.4.2
[    1.168876] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.168880] ehci-pci: EHCI PCI platform driver
[    1.168939] QUIRK: Enable AMD PLL fix
[    1.168955] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.168960] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.168963] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.168970] ehci-pci 0000:00:12.2: debug port 1
[    1.168998] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb09000
[    1.181725] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.181778] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.181780] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.181781] usb usb1: Product: EHCI Host Controller
[    1.181783] usb usb1: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    1.181784] usb usb1: SerialNumber: 0000:00:12.2
[    1.181893] hub 1-0:1.0: USB hub found
[    1.181898] hub 1-0:1.0: 5 ports detected
[    1.182100] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.182104] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.182107] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.182114] ehci-pci 0000:00:13.2: debug port 1
[    1.182135] ehci-pci 0000:00:13.2: irq 17, io mem 0xfeb07000
[    1.193721] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.193749] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.193751] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.193752] usb usb2: Product: EHCI Host Controller
[    1.193754] usb usb2: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    1.193755] usb usb2: SerialNumber: 0000:00:13.2
[    1.193853] hub 2-0:1.0: USB hub found
[    1.193857] hub 2-0:1.0: 5 ports detected
[    1.194029] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.194034] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.194037] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.194044] ehci-pci 0000:00:16.2: debug port 1
[    1.194065] ehci-pci 0000:00:16.2: irq 17, io mem 0xfeb04000
[    1.205724] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.205758] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.205759] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.205761] usb usb3: Product: EHCI Host Controller
[    1.205762] usb usb3: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    1.205763] usb usb3: SerialNumber: 0000:00:16.2
[    1.205853] hub 3-0:1.0: USB hub found
[    1.205857] hub 3-0:1.0: 4 ports detected
[    1.205954] ehci-platform: EHCI generic platform driver
[    1.205964] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.205968] ohci-pci: OHCI PCI platform driver
[    1.206034] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.206041] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.206058] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb0a000
[    1.265738] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.265739] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.265741] usb usb4: Product: OHCI PCI host controller
[    1.265742] usb usb4: Manufacturer: Linux 4.4.0-21-generic ohci_hcd
[    1.265743] usb usb4: SerialNumber: 0000:00:12.0
[    1.265847] hub 4-0:1.0: USB hub found
[    1.265854] hub 4-0:1.0: 5 ports detected
[    1.266004] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.266008] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.266021] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb08000
[    1.325791] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.325793] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.325795] usb usb5: Product: OHCI PCI host controller
[    1.325796] usb usb5: Manufacturer: Linux 4.4.0-21-generic ohci_hcd
[    1.325798] usb usb5: SerialNumber: 0000:00:13.0
[    1.325903] hub 5-0:1.0: USB hub found
[    1.325909] hub 5-0:1.0: 5 ports detected
[    1.326064] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.326068] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.326082] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb06000
[    1.385793] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.385796] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.385797] usb usb6: Product: OHCI PCI host controller
[    1.385799] usb usb6: Manufacturer: Linux 4.4.0-21-generic ohci_hcd
[    1.385800] usb usb6: SerialNumber: 0000:00:14.5
[    1.385897] hub 6-0:1.0: USB hub found
[    1.385904] hub 6-0:1.0: 2 ports detected
[    1.386026] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    1.386030] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.386048] ohci-pci 0000:00:16.0: irq 18, io mem 0xfeb05000
[    1.445784] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.445786] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.445788] usb usb7: Product: OHCI PCI host controller
[    1.445789] usb usb7: Manufacturer: Linux 4.4.0-21-generic ohci_hcd
[    1.445791] usb usb7: SerialNumber: 0000:00:16.0
[    1.445893] hub 7-0:1.0: USB hub found
[    1.445899] hub 7-0:1.0: 4 ports detected
[    1.445993] ohci-platform: OHCI generic platform driver
[    1.446003] uhci_hcd: USB Universal Host Controller Interface driver
[    1.446073] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.446077] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.446149] xhci_hcd 0000:02:00.0: hcc params 0x002841eb hci version 0x100 quirks 0x00000090
[    1.446223] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.446225] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.446226] usb usb8: Product: xHCI Host Controller
[    1.446228] usb usb8: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    1.446229] usb usb8: SerialNumber: 0000:02:00.0
[    1.446315] hub 8-0:1.0: USB hub found
[    1.446320] hub 8-0:1.0: 1 port detected
[    1.446375] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.446379] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.446398] usb usb9: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.446411] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.446412] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.446414] usb usb9: Product: xHCI Host Controller
[    1.446415] usb usb9: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    1.446416] usb usb9: SerialNumber: 0000:02:00.0
[    1.446513] hub 9-0:1.0: USB hub found
[    1.446522] hub 9-0:1.0: 4 ports detected
[    1.446651] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.446992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.446995] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.447123] mousedev: PS/2 mouse device common for all mice
[    1.447256] rtc_cmos 00:04: RTC can wake from S4
[    1.447353] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.447370] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.447377] i2c /dev entries driver
[    1.447424] device-mapper: uevent: version 1.0.3
[    1.447502] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.447513] ledtrig-cpu: registered to indicate activity on CPUs
[    1.447853] NET: Registered protocol family 10
[    1.448039] NET: Registered protocol family 17
[    1.448055] Key type dns_resolver registered
[    1.448467] microcode: CPU0: patch_level=0x06000822
[    1.448475] microcode: CPU1: patch_level=0x06000822
[    1.448483] microcode: CPU2: patch_level=0x06000822
[    1.448492] microcode: CPU3: patch_level=0x06000822
[    1.448499] microcode: CPU4: patch_level=0x06000822
[    1.448507] microcode: CPU5: patch_level=0x06000822
[    1.448540] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.448680] registered taskstats version 1
[    1.448692] Loading compiled-in X.509 certificates
[    1.449442] Loaded X.509 cert 'Build time autogenerated kernel key: fc7c0e9f152f32eca50ea2d9722926e5127af244'
[    1.449457] zswap: loaded using pool lzo/zbud
[    1.451281] Key type trusted registered
[    1.454209] Key type encrypted registered
[    1.454215] AppArmor: AppArmor sha1 policy hashing enabled
[    1.454218] ima: No TPM chip found, activating TPM-bypass!
[    1.454233] evm: HMAC attrs: 0x1
[    1.454559]   Magic number: 4:805:616
[    1.454576]  clockevents: hash matches
[    1.454640] rtc_cmos 00:04: setting system clock to 2016-06-24 04:36:06 UTC (1466742966)
[    1.454776] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.454982] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.454983] EDD information not available.
[    1.455051] PM: Hibernation image not present or could not be loaded.
[    1.456183] Freeing unused kernel memory: 1476K (ffffffff81f41000 - ffffffff820b2000)
[    1.456185] Write protecting the kernel read-only data: 14336k
[    1.456818] Freeing unused kernel memory: 1872K (ffff88000182c000 - ffff880001a00000)
[    1.457190] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    1.467722] random: systemd-udevd urandom read with 7 bits of entropy available
[    1.493668] wmi: Mapper loaded
[    1.493669] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.493721] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.503296] scsi host0: pata_atiixp
[    1.503418] scsi host1: pata_atiixp
[    1.503464] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.503466] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.503577] ahci 0000:00:11.0: version 3.0
[    1.503660] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.503663] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.504053] [drm] Initialized drm 1.1.0 20060810
[    1.504242] r8168: module verification failed: signature and/or required key missing - tainting kernel
[    1.504607] r8168 Gigabit Ethernet driver 8.042.00-NAPI loaded
[    1.505157] scsi host2: ahci
[    1.505449] scsi host3: ahci
[    1.505553] scsi host4: ahci
[    1.505655] scsi host5: ahci
[    1.505726] ata3: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b100 irq 19
[    1.505729] ata4: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
[    1.505732] ata5: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b200 irq 19
[    1.505734] ata6: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b280 irq 19
[    1.505894] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.505898] ahci 0000:03:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    1.506320] scsi host6: ahci
[    1.506433] scsi host7: ahci
[    1.506498] ata7: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810100 irq 30
[    1.506500] ata8: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810180 irq 30
[    1.517727] usb 3-4: new high-speed USB device number 2 using ehci-pci
[    1.523042] AVX version of gcm_enc/dec engaged.
[    1.523044] AES CTR mode by8 optimization enabled
[    1.525623] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.525628] r8168  Copyright (C) 2016  Realtek NIC software team <nicfae@realtek.com> 
                This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
                This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    1.535807] [drm] radeon kernel modesetting enabled.
[    1.537807] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.537809] AMD IOMMUv2 functionality not available on this system
[    1.540479] CRAT table not found
[    1.540481] Finished initializing topology ret=0
[    1.540529] kfd kfd: Initialized module
[    1.540764] checking generic (c0000000 5b0000) vs hw (c0000000 10000000)
[    1.540766] fb: switching to radeondrmfb from VESA VGA
[    1.540792] Console: switching to colour dummy device 80x25
[    1.541027] [drm] initializing kernel modesetting (TURKS 0x1002:0x6758 0x174B:0xE194).
[    1.541037] [drm] register mmio base: 0xFEA20000
[    1.541038] [drm] register mmio size: 131072
[    1.541127] ATOM BIOS: TURKS
[    1.541304] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    1.541306] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    1.541308] [drm] Detected VRAM RAM=1024M, BAR=256M
[    1.541309] [drm] RAM width 128bits DDR
[    1.541400] [TTM] Zone  kernel: Available graphics memory: 4102574 kiB
[    1.541402] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.541403] [TTM] Initializing pool allocator
[    1.541411] [TTM] Initializing DMA pool allocator
[    1.541428] [drm] radeon: 1024M of VRAM memory ready
[    1.541429] [drm] radeon: 1024M of GTT memory ready.
[    1.541444] [drm] Loading TURKS Microcode
[    1.541519] [drm] Internal thermal controller without fan control
[    1.546031] r8168 0000:05:00.0 enp5s0: renamed from eth0
[    1.546467] [drm] radeon: dpm initialized
[    1.546557] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.547562] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    1.557294] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    1.557395] radeon 0000:01:00.0: WB enabled
[    1.557397] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8800bde38c00
[    1.557399] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8800bde38c0c
[    1.560530] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90001032118
[    1.560532] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.560533] [drm] Driver supports precise vblank timestamp query.
[    1.560534] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.560589] radeon 0000:01:00.0: radeon: using MSI.
[    1.560624] [drm] radeon: irq initialized.
[    1.573811] firewire_ohci 0000:04:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    1.576886] [drm] ring test on 0 succeeded in 2 usecs
[    1.576897] [drm] ring test on 3 succeeded in 7 usecs
[    1.605773] usb 1-1: device descriptor read/64, error -32
[    1.752678] [drm] ring test on 5 succeeded in 2 usecs
[    1.752687] [drm] UVD initialized successfully.
[    1.752818] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.752873] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.761816] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[    1.829788] ata8: SATA link down (SStatus 0 SControl 300)
[    1.829821] ata7: SATA link down (SStatus 0 SControl 300)
[    1.836265] usb 3-4: New USB device found, idVendor=058f, idProduct=6364
[    1.836267] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.836270] usb 3-4: Product: Mass Storage Device
[    1.836272] usb 3-4: Manufacturer: Generic
[    1.836273] usb 3-4: SerialNumber: 058F63646476
[    1.839833] usb-storage 3-4:1.0: USB Mass Storage device detected
[    1.839924] scsi host8: usb-storage 3-4:1.0
[    1.839997] usbcore: registered new interface driver usb-storage
[    1.840202] hidraw: raw HID events driver (C) Jiri Kosina
[    1.841332] usbcore: registered new interface driver uas
[    1.843454] usb 1-1: New USB device found, idVendor=1b1c, idProduct=1a09
[    1.843457] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.843458] usb 1-1: Product: Voyager GT 3.0
[    1.843460] usb 1-1: Manufacturer: Corsair
[    1.843461] usb 1-1: SerialNumber: 0708569591943F96
[    1.843675] usb-storage 1-1:1.0: USB Mass Storage device detected
[    1.843756] scsi host9: usb-storage 1-1:1.0
[    1.845267] usbhid 3-4:1.1: can't add hid device: -32
[    1.845273] usbhid: probe of 3-4:1.1 failed with error -32
[    1.845288] usbcore: registered new interface driver usbhid
[    1.845289] usbhid: USB HID core driver
[    1.890895] usb 8-1: New USB device found, idVendor=2109, idProduct=3431
[    1.890898] usb 8-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.890899] usb 8-1: Product: USB2.0 Hub
[    1.891280] hub 8-1:1.0: USB hub found
[    1.891413] hub 8-1:1.0: 4 ports detected
[    1.953736] usb 1-3: new high-speed USB device number 3 using ehci-pci
[    1.997747] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.997806] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.997828] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.998529] ata5.00: ATA-8: WDC WD1001FALS-00E8B0, 05.00K05, max UDMA/133
[    1.998531] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.998634] ata6.00: ATA-8: WDC WD1001FALS-00E8B0, 05.00K05, max UDMA/133
[    1.998637] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.999448] ata5.00: configured for UDMA/133
[    1.999541] ata6.00: configured for UDMA/133
[    2.001743] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.009288] ata3.00: ATAPI: ASUS    BW-12B1ST, 1.03, max UDMA/100
[    2.009857] ata4.00: ATA-8: KINGSTON SH103S3120G, 507KC4, max UDMA/133
[    2.009859] ata4.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.011055] ata3.00: configured for UDMA/100
[    2.015044] scsi 2:0:0:0: CD-ROM            ASUS     BW-12B1ST        1.03 PQ: 0 ANSI: 5
[    2.019690] ata4.00: configured for UDMA/133
[    2.044593] sr 2:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.044599] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.044911] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.044997] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    2.045205] scsi 3:0:0:0: Direct-Access     ATA      KINGSTON SH103S3 C4   PQ: 0 ANSI: 5
[    2.045395] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    2.045417] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.045510] sd 3:0:0:0: [sda] Write Protect is off
[    2.045513] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.045544] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.045598] scsi 4:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 0K05 PQ: 0 ANSI: 5
[    2.045794] sd 4:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    2.045829] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.045863] sd 4:0:0:0: [sdb] Write Protect is off
[    2.045865] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.045896] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.045994] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 0K05 PQ: 0 ANSI: 5
[    2.046067]  sda: sda1 sda2 < sda5 >
[    2.046200] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    2.046238] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.046265] sd 5:0:0:0: [sdc] Write Protect is off
[    2.046268] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.046295] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.046517] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.060677]  sdc:
[    2.060895] sd 5:0:0:0: [sdc] Attached SCSI disk
[    2.073869] firewire_core 0000:04:0e.0: created device fw0: GUID 0049e550179f0c00, S400
[    2.085956]  sdb: sdb1 sdb2 sdb3
[    2.086335] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.087017] usb 1-3: New USB device found, idVendor=0781, idProduct=5575
[    2.087019] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.087021] usb 1-3: Product: Cruzer Glide
[    2.087022] usb 1-3: Manufacturer: SanDisk
[    2.087024] usb 1-3: SerialNumber: 4C531001501017121111
[    2.088276] usb-storage 1-3:1.0: USB Mass Storage device detected
[    2.089318] scsi host10: usb-storage 1-3:1.0
[    2.133812] tsc: Refined TSC clocksource calibration: 3515.865 MHz
[    2.133821] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x32addc43862, max_idle_ns: 440795314332 ns
[    2.173721] usb 8-1.1: new low-speed USB device number 3 using xhci_hcd
[    2.269627] usb 8-1.1: New USB device found, idVendor=046d, idProduct=c018
[    2.269634] usb 8-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.269639] usb 8-1.1: Product: USB Optical Mouse
[    2.269642] usb 8-1.1: Manufacturer: Logitech
[    2.269929] usb 8-1.1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.279170] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:09.0/0000:02:00.0/usb8/8-1/8-1.1/8-1.1:1.0/0003:046D:C018.0001/input/input5
[    2.279290] hid-generic 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:02:00.0-1.1/input0
[    2.349814] usb 8-1.2: new low-speed USB device number 4 using xhci_hcd
[    2.401908] [drm] ib test on ring 5 succeeded
[    2.403011] [drm] Radeon Display Connectors
[    2.403012] [drm] Connector 0:
[    2.403013] [drm]   DP-1
[    2.403014] [drm]   HPD5
[    2.403015] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.403016] [drm]   Encoders:
[    2.403017] [drm]     DFP1: INTERNAL_UNIPHY1
[    2.403018] [drm] Connector 1:
[    2.403019] [drm]   HDMI-A-1
[    2.403019] [drm]   HPD1
[    2.403021] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[    2.403021] [drm]   Encoders:
[    2.403022] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.403023] [drm] Connector 2:
[    2.403023] [drm]   DVI-I-1
[    2.403024] [drm]   HPD4
[    2.403025] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    2.403026] [drm]   Encoders:
[    2.403026] [drm]     DFP3: INTERNAL_UNIPHY
[    2.403027] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.454838] usb 8-1.2: New USB device found, idVendor=03f0, idProduct=0024
[    2.454845] usb 8-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.454850] usb 8-1.2: Product: HP Basic USB Keyboard
[    2.454853] usb 8-1.2: Manufacturer: CHICONY
[    2.454984] usb 8-1.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.465707] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:09.0/0000:02:00.0/usb8/8-1/8-1.2/8-1.2:1.0/0003:03F0:0024.0002/input/input6
[    2.495710] [drm] fb mappable at 0xC0475000
[    2.495712] [drm] vram apper at 0xC0000000
[    2.495713] [drm] size 8294400
[    2.495714] [drm] fb depth is 24
[    2.495714] [drm]    pitch is 7680
[    2.495841] fbcon: radeondrmfb (fb0) is primary device
[    2.495916] Console: switching to colour frame buffer device 240x67
[    2.495942] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.505863] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    2.522142] hid-generic 0003:03F0:0024.0002: input,hidraw1: USB HID v1.11 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:02:00.0-1.2/input0
[    2.838612] scsi 8:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    2.839225] scsi 8:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.839811] scsi 8:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    2.840619] scsi 8:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    2.840927] sd 8:0:0:0: Attached scsi generic sg4 type 0
[    2.841074] sd 8:0:0:1: Attached scsi generic sg5 type 0
[    2.841215] sd 8:0:0:2: Attached scsi generic sg6 type 0
[    2.841357] sd 8:0:0:3: Attached scsi generic sg7 type 0
[    2.842303] scsi 9:0:0:0: Direct-Access     Corsair  Voyager GT 3.0   000A PQ: 0 ANSI: 6
[    2.843590] sd 9:0:0:0: Attached scsi generic sg8 type 0
[    2.844608] sd 9:0:0:0: [sdh] 61800448 512-byte logical blocks: (31.6 GB/29.5 GiB)
[    2.845358] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[    2.845607] sd 9:0:0:0: [sdh] Write Protect is off
[    2.845610] sd 9:0:0:0: [sdh] Mode Sense: 2b 00 00 08
[    2.846684] sd 9:0:0:0: [sdh] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.846756] sd 8:0:0:2: [sdf] Attached SCSI removable disk
[    2.871673] sd 8:0:0:1: [sde] Attached SCSI removable disk
[    2.873047] sd 8:0:0:3: [sdg] Attached SCSI removable disk
[    3.038188]  sdh: sdh1 sdh2
[    3.042349] sd 9:0:0:0: [sdh] Attached SCSI removable disk
[    3.086462] scsi 10:0:0:0: Direct-Access     SanDisk  Cruzer Glide     1.27 PQ: 0 ANSI: 6
[    3.086762] sd 10:0:0:0: Attached scsi generic sg9 type 0
[    3.087714] sd 10:0:0:0: [sdi] 122606848 512-byte logical blocks: (62.8 GB/58.5 GiB)
[    3.089081] sd 10:0:0:0: [sdi] Write Protect is off
[    3.089083] sd 10:0:0:0: [sdi] Mode Sense: 43 00 00 00
[    3.090083] sd 10:0:0:0: [sdi] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.095337]  sdi: sdi1
[    3.098837] sd 10:0:0:0: [sdi] Attached SCSI removable disk
[    3.133999] clocksource: Switched to clocksource tsc
[    4.147543] random: nonblocking pool is initialized
[   11.597654] NET: Registered protocol family 38
[   17.227863] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   17.311025] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   17.311176] systemd[1]: Detected architecture x86-64.
[   17.311417] systemd[1]: Set hostname to <Enterprise>.
[   17.389801] systemd[1]: Listening on fsck to fsckd communication Socket.
[   17.389862] systemd[1]: Listening on udev Control Socket.
[   17.389892] systemd[1]: Listening on Journal Socket (/dev/log).
[   17.389980] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   17.390007] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   17.390014] systemd[1]: Reached target Remote File Systems (Pre).
[   17.390105] systemd[1]: Created slice System Slice.
[   17.390131] systemd[1]: Listening on LVM2 poll daemon socket.
[   17.390147] systemd[1]: Listening on udev Kernel Socket.
[   17.390206] systemd[1]: Listening on Journal Audit Socket.
[   17.390235] systemd[1]: Listening on Syslog Socket.
[   17.390318] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[   17.390351] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   17.390359] systemd[1]: Reached target User and Group Name Lookups.
[   17.390375] systemd[1]: Listening on LVM2 metadata daemon socket.
[   17.390448] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   17.390477] systemd[1]: Listening on Journal Socket.
[   17.410381] systemd[1]: Mounting POSIX Message Queue File System...
[   17.410960] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   17.411463] systemd[1]: Starting Nameserver information manager...
[   17.411975] systemd[1]: Starting Uncomplicated firewall...
[   17.412540] systemd[1]: Mounting Debug File System...
[   17.413776] systemd[1]: Started Read required files in advance.
[   17.415885] systemd[1]: Starting Load Kernel Modules...
[   17.416413] systemd[1]: Mounting Huge Pages File System...
[   17.416917] systemd[1]: Starting Journal Service...
[   17.420153] systemd[1]: Starting LSB: controls configuration of serial ports...
[   17.420294] systemd[1]: Created slice User and Session Slice.
[   17.420314] systemd[1]: Reached target Slices.
[   17.420339] systemd[1]: Reached target Remote File Systems.
[   17.420873] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[   17.420952] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   17.422549] systemd[1]: Mounted POSIX Message Queue File System.
[   17.422620] systemd[1]: Mounted Debug File System.
[   17.422661] systemd[1]: Mounted Huge Pages File System.
[   17.423295] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   17.424026] systemd[1]: Started Uncomplicated firewall.
[   17.427466] systemd[1]: Started Nameserver information manager.
[   17.434906] lp: driver loaded but no devices found
[   17.438535] ppdev: user-space parallel port driver
[   17.444060] systemd[1]: Started Load Kernel Modules.
[   17.468794] systemd[1]: Started LVM2 metadata daemon.
[   17.469501] systemd[1]: Mounting FUSE Control File System...
[   17.470055] systemd[1]: Starting Apply Kernel Variables...
[   17.470897] systemd[1]: Starting Create Static Device Nodes in /dev...
[   17.471522] systemd[1]: Started Journal Service.
[   17.507139] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   17.518455] systemd-journald[484]: Received request to flush runtime journal from PID 1
[   17.630382] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.676102] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   17.676535] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[   17.707476] EDAC MC: Ver: 3.0.0
[   17.712119] MCE: In-kernel MCE decoding enabled.
[   17.713631] AMD64 EDAC driver v3.4.0
[   17.713657] EDAC amd64: DRAM ECC disabled.
[   17.713663] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[   17.735888] media: Linux media interface: v0.10
[   17.742255] Linux video capture interface: v2.00
[   17.759811] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   17.775048] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   17.775728] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:04.0/0000:01:00.1/sound/card1/input7
[   17.780782] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC889: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   17.780786] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.780788] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   17.780790] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   17.780792] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   17.780793] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   17.780795] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   17.780797] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   17.780798] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   17.816438] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   17.816532] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   17.816606] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   17.816669] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   17.818851] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   17.819018] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[   17.819118] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input14
[   17.819341] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input15
[   17.827987] kvm: Nested Virtualization enabled
[   17.827992] kvm: Nested Paging enabled
[   17.838930] cx23885 driver version 0.0.4 loaded
[   17.839029] cx23885[0]: Your board isn't known (yet) to the driver.
               cx23885[0]: Try to pick one of the existing card configs via
               cx23885[0]: card=<n> insmod option.  Updating to the latest
               cx23885[0]: version might help as well.
[   17.839030] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   17.839030] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   17.839031] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   17.839032] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   17.839032] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   17.839033] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   17.839033] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   17.839034] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   17.839034] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   17.839035] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   17.839035] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   17.839036] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   17.839037] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   17.839037] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   17.839038] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   17.839039] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   17.839039] cx23885[0]:    card=15 -> TeVii S470
[   17.839040] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   17.839041] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   17.839042] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[   17.839042] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[   17.839043] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[   17.839043] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[   17.839044] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[   17.839045] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   17.839045] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   17.839046] cx23885[0]:    card=25 -> Compro VideoMate E800
[   17.839047] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
[   17.839047] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
[   17.839048] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200
[   17.839048] cx23885[0]:    card=29 -> GoTView X5 3D Hybrid
[   17.839049] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[   17.839050] cx23885[0]:    card=31 -> Leadtek Winfast PxDVR3200 H XC4000
[   17.839050] cx23885[0]:    card=32 -> MPX-885
[   17.839051] cx23885[0]:    card=33 -> Mygica X8502/X8507 ISDB-T
[   17.839051] cx23885[0]:    card=34 -> TerraTec Cinergy T PCIe Dual
[   17.839052] cx23885[0]:    card=35 -> TeVii S471
[   17.839053] cx23885[0]:    card=36 -> Hauppauge WinTV-HVR1255
[   17.839053] cx23885[0]:    card=37 -> Prof Revolution DVB-S2 8000
[   17.839054] cx23885[0]:    card=38 -> Hauppauge WinTV-HVR4400/HVR5500
[   17.839055] cx23885[0]:    card=39 -> AVerTV Hybrid Express Slim HC81R
[   17.839055] cx23885[0]:    card=40 -> TurboSight TBS 6981
[   17.839056] cx23885[0]:    card=41 -> TurboSight TBS 6980
[   17.839056] cx23885[0]:    card=42 -> Leadtek Winfast PxPVR2200
[   17.839057] cx23885[0]:    card=43 -> Hauppauge ImpactVCB-e
[   17.839058] cx23885[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Express2
[   17.839059] cx23885[0]:    card=45 -> DVBSky T9580
[   17.839059] cx23885[0]:    card=46 -> DVBSky T980C
[   17.839060] cx23885[0]:    card=47 -> DVBSky S950C
[   17.839060] cx23885[0]:    card=48 -> Technotrend TT-budget CT2-4500 CI
[   17.839061] cx23885[0]:    card=49 -> DVBSky S950
[   17.839061] cx23885[0]:    card=50 -> DVBSky S952
[   17.839062] cx23885[0]:    card=51 -> DVBSky T982
[   17.839063] cx23885[0]:    card=52 -> Hauppauge WinTV-HVR5525
[   17.839063] cx23885[0]:    card=53 -> Hauppauge WinTV Starburst
[   17.839078] CORE cx23885[0]: subsystem: 0070:2a18, board: UNKNOWN/GENERIC [card=0,autodetected]
[   17.878362] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   17.966038] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   17.966043] cx23885[0]/0: found at 0000:06:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfe400000
[   18.062711] Adding 8347132k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:8347132k SSFS
[   18.120526] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   18.121633] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   18.165139] audit: type=1400 audit(1466742983.203:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=907 comm="apparmor_parser"
[   18.165166] audit: type=1400 audit(1466742983.203:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=905 comm="apparmor_parser"
[   18.166043] audit: type=1400 audit(1466742983.203:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=903 comm="apparmor_parser"
[   18.166050] audit: type=1400 audit(1466742983.203:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=903 comm="apparmor_parser"
[   18.166056] audit: type=1400 audit(1466742983.203:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=903 comm="apparmor_parser"
[   18.166061] audit: type=1400 audit(1466742983.203:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=903 comm="apparmor_parser"
[   18.166441] audit: type=1400 audit(1466742983.207:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=906 comm="apparmor_parser"
[   18.166449] audit: type=1400 audit(1466742983.207:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=906 comm="apparmor_parser"
[   18.166455] audit: type=1400 audit(1466742983.207:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=906 comm="apparmor_parser"
[   18.166791] audit: type=1400 audit(1466742983.207:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=908 comm="apparmor_parser"
[   18.178307] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   18.419016] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[   18.419341] enp5s0: 0xffffc90000c64000, 74:d4:35:04:7d:c9, IRQ 27
[   18.478230] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   18.490191] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[   21.500639] r8168: enp5s0: link up
[   21.500682] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
[  493.637842] audit_printk_skb: 12 callbacks suppressed
[  493.637845] audit: type=1400 audit(1466757857.708:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=24110 comm="apparmor_parser"
[  493.807092] audit: type=1400 audit(1466757857.876:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/mysqld" pid=24148 comm="apparmor_parser"
[  526.066613] audit: type=1400 audit(1466757890.136:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=30931 comm="apparmor_parser"
[ 2975.956780] [drm:radeon_dvi_detect [radeon]] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID
```

---

### Post by Espryon on 2016-06-24
(Edit, doublepost)

I don't know the videocard because I didn't purchase it but, the Motherboard is --> [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128859&cm_re=gigabyte_990FXA-UD3-_-13-128-859-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128859&cm_re=gigabyte_990FXA-UD3-_-13-128-859-_-Product) i.e. "GIGABYTE GA-990FXA-UD3 R5 (rev. 1.0) AM3+/AM3 AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard"

the TV Tuner Card is a Hauppauge 1250 HVR.

[IMG]http://pre01.deviantart.net/e855/th/pre/f/2016/176/1/9/screenshot_from_2016_06_24_14_11_51_by_espry0n-da7lho3.png[/IMG]

I haven't worked with databases enough to understand how to remedy this. Any suggestions?

The version of Mythbuntu is 16.04. I tried 14.04 and I couldn't get the network card to work at all with the Realtek driver I used i.e. [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2) To Clarify <-- I fixed the issue of Ubuntu not having my RealTek driver with the aforementioned driver i.e. replacing 8169 with 8168.

^ If others are having problems with an embedded NIC similar to mine.

lspci -vvvn on Realtek with correct driver loaded.

```
05:00.0 0200: 10ec:8168 (rev 06)
        Subsystem: 1458:e000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 27
        Region 0: I/O ports at b000 [size=256]
        Region 2: Memory at fe600000 (64-bit, non-prefetchable) [size=4K]
        Region 4: Memory at d0000000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee1000c  Data: 41b3
        Capabilities: [70] Express (v2) Endpoint, MSI 01
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s unlimited, L1 <64us
                        ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
 LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
                Vector table: BAR=4 offset=00000000
                PBA: BAR=4 offset=00000800
        Capabilities: [d0] Vital Product Data
                Unknown small resource type 00, will not decode more.
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [140 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=01
                        Status: NegoPending- InProgress-
        Capabilities: [160 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
        Kernel driver in use: r8168
        Kernel modules: r8168

```

---

### Post by QDR06VV9 on 2016-06-24
Espryon Please use code tags when posting long Out Puts your Join Date 2008 I would have thought you knew this by now.

You can do that by:

1. Clicking the # symbol in the toolbar above the text entry box, placing your cursor between the tags and pasting your text.
Thanks

2. Highlighting text already present and clicking the # symbol in the toolbar.

---

### Post by Espryon on 2016-06-24
ok, sorry It's been a while since I've posted on the Ubuntu Forums.

MythTV-Setup Log:

```
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbparams.cpp:39 (IsValid) DBHostName is not set in config.xml
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcontext.cpp:809 (UPnPautoconf) UPNP Search 2 secs
Jun 24 04:52:02 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcontext.cpp:824 (UPnPautoconf) UPNP Search 1 secs
Jun 24 04:52:03 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcontext.cpp:824 (UPnPautoconf) UPNP Search 1 secs
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythcontext.cpp:834 (UPnPautoconf) No UPnP backends found
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:52:04 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:52:05 Enterprise mythtv-setup.real: mythtv-setup[6626]: W CoreContext mythdownloadmanager.cpp:1655 (load) MythCookieJar::load() failed to open file for reading: /home/espryon/.mythtv/MythBrowser/cookiejar.txt
Jun 24 04:52:05 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:52:05 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:52:05 Enterprise mythtv-setup.real: mythtv-setup[6626]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:52:05 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:52:08 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:35 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:53:38 Enterprise mythtv-setup.real: mythtv-setup[6626]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:39 Enterprise mythtv-setup.real: mythtv-setup[6626]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 04:53:39 Enterprise mythtv-setup.real: mythtv-setup[6626]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)
Jun 24 04:54:18 Enterprise mythtv-setup.real: mythtv-setup[6806]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:19 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:54:21 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'Espryon'@'localhost' (using password: YES)
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:39 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:54:41 Enterprise mythtv-setup.real: mythtv-setup[6806]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:43 Enterprise mythtv-setup.real: mythtv-setup[6806]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 04:54:43 Enterprise mythtv-setup.real: mythtv-setup[6806]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'Espryon'@'localhost' (using password: YES)
Jun 24 04:57:37 Enterprise mythtv-setup.real: mythtv-setup[8422]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:57:38 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:57:40 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mytht'@'localhost' (using password: YES)
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:57:57 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:57:58 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:57:58 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:57:58 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:57:58 Enterprise mythtv-setup.real: mythtv-setup[8422]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:57:58 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:57:59 Enterprise mythtv-setup.real: mythtv-setup[8422]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:58:00 Enterprise mythtv-setup.real: mythtv-setup[8422]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 04:58:00 Enterprise mythtv-setup.real: mythtv-setup[8422]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:58:33 Enterprise mythtv-setup.real: mythtv-setup[8513]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mytht'@'localhost' (using password: YES)
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:58:34 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:58:37 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip6
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to 'Enterprise.local'
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager2] Unable to connect to database!
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:58:48 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 04:58:49 Enterprise mythtv-setup.real: mythtv-setup[8513]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:58:50 Enterprise mythtv-setup.real: mythtv-setup[8513]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 04:58:50 Enterprise mythtv-setup.real: mythtv-setup[8513]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 05:03:06 Enterprise mythtv-setup.real: mythtv-setup[9230]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to 'Enterprise.local'
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 05:03:07 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 05:03:10 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager2] Unable to connect to database!
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager2] Unable to connect to database!
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip6
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to 'Enterprise.local'
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager3] Unable to connect to database!
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 05:03:18 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 05:03:19 Enterprise mythtv-setup.real: mythtv-setup[9230]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 05:03:19 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 05:03:20 Enterprise mythtv-setup.real: mythtv-setup[9230]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 05:03:21 Enterprise mythtv-setup.real: mythtv-setup[9230]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 05:03:21 Enterprise mythtv-setup.real: mythtv-setup[9230]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythtv-setup version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/espryon/.mythtv
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:20 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to 'Enterprise.local'
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager1] Unable to connect to database!
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x800 59.910 Hz
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 14:05:21 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 14:05:24 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager2] Unable to connect to database!
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager2] Unable to connect to database!
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdb.cpp:631 (GetSettingOnHost) Database not open while trying to load setting: backendserverip6
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to 'Enterprise.local'
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager3] Unable to connect to database!
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to MySQL server on 'Enterprise.local' (111)
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: A CoreContext mythcontext.cpp:428 (FindDatabase) Cannot login to database
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/var/run/lirc/lircd'#012#011#011#011eno: No such file or directory (2)
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext cecadapter.cpp:125 (Open) CECAdapter: Failed to load libcec.
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:0
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.52:0
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:0
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::6901:7fdd:5622:ba11%enp5s0]:0
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.2.255:0
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1052 (Init) Using Full Screen Window
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1280 x 800
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 14:05:37 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext langsettings.cpp:117 (Load) System Locale (en_US), Country (US), Language (en_US)
Jun 24 14:05:38 Enterprise mythtv-setup.real: mythtv-setup[20850]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 14:05:40 Enterprise mythtv-setup.real: mythtv-setup[20850]: A CoreContext mythcontext.cpp:589 (PromptForDatabaseParams) User cancelled database configuration
Jun 24 14:05:40 Enterprise mythtv-setup.real: mythtv-setup[20850]: E CoreContext main.cpp:354 (main) Failed to init MythContext, exiting.
```

---

### Post by Espryon on 2016-06-24
Mythbuntu Backend Log:

```
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('Country') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('FreqTable') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('ISO639Language0') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('ISO639Language1') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('Language') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('TVFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('VbiFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('DateFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('MythArchiveDateFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('MythArchiveTimeFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('MythArchiveVideoFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('ShortDateFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdb.cpp:286 (SaveSettingOnHost) SaveSettingOnHost('TimeFormat') - No database yet
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdbcon.cpp:864 (prepare) Error preparing query: SELECT data FROM settings WHERE value = :VALUE AND hostname = :HOSTNAME
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdbcon.cpp:866 (prepare) Driver error was [2/1146]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table 'mythconverg.settings' doesn't exist
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdbcon.cpp:864 (prepare) Error preparing query: SELECT data FROM settings WHERE value = :VALUE AND hostname = :HOSTNAME
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythdbcon.cpp:866 (prepare) Driver error was [2/1146]:#012QMYSQL3: Unable to prepare statement#012Database error was:#012Table 'mythconverg.settings' doesn't exist
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext schemawizard.cpp:109 (Compare) No current database version?
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext schemawizard.cpp:113 (Compare) Database appears to be empty/new!
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: W CoreContext dbcheck.cpp:498 (UpgradeTVDatabaseSchema) Not allowed to upgrade the database.
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: N CoreContext dbcheck.cpp:3342 (InitializeMythSchema) Inserting MythTV initial database information.
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1307
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1308
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1309
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1310
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1311
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1312
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1313
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1314
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1315
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1316
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1317
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1318
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1319
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1320
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1321
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1322
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1323
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1324
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1325
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1326
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1327
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1328
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1329
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1330
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:2846 (doUpgradeTVDatabaseSchema) Upgrading to MythTV schema version 1332
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1333
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1334
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1335
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1336
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1337
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1338
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1339
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1341
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1342
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:3224 (doUpgradeTVDatabaseSchema) Upgrading to MythTV schema version 1343
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1344
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext dbcheck.cpp:523 (UpgradeTVDatabaseSchema) Database schema upgrade complete.
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ed5700:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:44 Enterprise mythbackend: mythbackend[1085]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:13): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(147aff0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:46 Enterprise mythbackend: mythbackend[1239]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1810070:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:47 Enterprise mythbackend: mythbackend[1366]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(92e590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:49 Enterprise mythbackend: mythbackend[1382]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(276a580:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:50 Enterprise mythbackend: mythbackend[1391]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(2231130:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:52 Enterprise mythbackend: mythbackend[1505]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(14c5300:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:53 Enterprise mythbackend: mythbackend[1653]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1f07d40:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:55 Enterprise mythbackend: mythbackend[1670]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(21d05b0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:56 Enterprise mythbackend: mythbackend[1681]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(27d1350:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:10:58 Enterprise mythbackend: mythbackend[1691]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:11): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:23 Enterprise mythbackend: mythbackend[1150]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1e7f590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:25 Enterprise mythbackend: mythbackend[1276]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ced0a0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:26 Enterprise mythbackend: mythbackend[1285]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(cf1590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:27 Enterprise mythbackend: mythbackend[1414]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1573350:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:29 Enterprise mythbackend: mythbackend[1428]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1dc8d40:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:30 Enterprise mythbackend: mythbackend[1442]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(141a350:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:32 Enterprise mythbackend: mythbackend[1683]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1159080:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:33 Enterprise mythbackend: mythbackend[1699]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1377590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:34 Enterprise mythbackend: mythbackend[1711]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(9f0ca0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: E CoreContext mmulticastsocketdevice.cpp:60 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:12): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Jun 24 00:36:36 Enterprise mythbackend: mythbackend[1720]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(12c1080:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:51 Enterprise mythbackend: mythbackend[6679]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(27f1ca0:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:52 Enterprise mythbackend: mythbackend[6693]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ed4d70:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:54 Enterprise mythbackend: mythbackend[6708]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ee8590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:55 Enterprise mythbackend: mythbackend[6717]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(2312590:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:57 Enterprise mythbackend: mythbackend[6726]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ee2d40:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:53:58 Enterprise mythbackend: mythbackend[6735]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1423580:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:54:00 Enterprise mythbackend: mythbackend[6744]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(1c8c080:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:54:01 Enterprise mythbackend: mythbackend[6753]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(19b0320:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:54:02 Enterprise mythbackend: mythbackend[6762]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: localhost
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(163ed50:-1): Failed to connect to (127.0.0.1:6543) Connection refused
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: E CoreContext mythcorecontext.cpp:979 (GetBackendServerIP) MythCoreContext::GetBackendServerIP(): No address defined for host: Enterprise
Jun 24 04:54:04 Enterprise mythbackend: mythbackend[6771]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:47 Enterprise mythbackend: mythbackend[20990]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:49 Enterprise mythbackend: mythbackend[21017]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:50 Enterprise mythbackend: mythbackend[21027]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:52 Enterprise mythbackend: mythbackend[21039]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:53 Enterprise mythbackend: mythbackend[21049]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:54 Enterprise mythbackend: mythbackend[21062]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:56 Enterprise mythbackend: mythbackend[21072]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:57 Enterprise mythbackend: mythbackend[21082]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:05:59 Enterprise mythbackend: mythbackend[21094]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I Logger logging.cpp:313 (run) Added logging to the console
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of Enterprise
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: E CoreContext mythdbcon.cpp:229 (OpenDatabase) [DBManager0] Unable to connect to database!
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: E CoreContext mythdbcon.cpp:230 (OpenDatabase) Driver error was [1/2002]:#012QMYSQL: Unable to connect#012Database error was:#012Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: C CoreContext main.cpp:132 (main) Failed to init MythContext.
Jun 24 14:06:00 Enterprise mythbackend: mythbackend[21104]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
```

---

### Post by Espryon on 2016-06-25
I reinstalled (on a portable harddrive confirming my suspicions of problems with a regular HDD that is getting up there in age) and I got up to the point of the tv tuner card being recognized and me manually loading the driver but, not recognized by the Mythbuntu setup i.e.

<MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: cx23885
	Kernel modules: cx23885

[https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](https://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)

full lspci -vvvn: 

```

00:00.0 0600: 1002:5a14 (rev 02)
	Subsystem: 1002:5a14
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Capabilities: [f0] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=20 MastHost- DefDir- DUL-
		Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b+
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 3.00
		Link Frequency 0: [e]
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [9c] HyperTransport: #1a
	Capabilities: [70] MSI: Enable- Count=1/4 Maskable- 64bit-
		Address: 00000000  Data: 0000

00:04.0 0604: 1002:5a18 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 24
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag+ RBE+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
			ClockPM- Surprise- LLActRep+ BwNot+ ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #4, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible+
		RootCap: CRSVisible+
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
		DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [b0] Subsystem: 1002:5a14
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190 v1] Access Control Services
		ACSCap:	SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
		ACSCtl:	SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 0604: 1002:5a1c (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 25
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag+ RBE+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #1, Speed 5GT/s, Width x2, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
			ClockPM- Surprise- LLActRep+ BwNot+ ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #9, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible+
		RootCap: CRSVisible+
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
		DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [b0] Subsystem: 1002:5a14
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190 v1] Access Control Services
		ACSCap:	SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
		ACSCtl:	SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0a.0 0604: 1002:5a1d (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 26
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag+ RBE+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 5GT/s, Width x2, ASPM L0s L1, Exit Latency L0s <1us, L1 <8us
			ClockPM- Surprise- LLActRep+ BwNot+ ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt+
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
			Slot #10, PowerLimit 75.000W; Interlock- NoCompl+
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible+
		RootCap: CRSVisible+
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd+
		DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [b0] Subsystem: 1002:5a14
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [190 v1] Access Control Services
		ACSCap:	SrcValid+ TransBlk+ ReqRedir+ CmpltRedir+ UpstreamFwd+ EgressCtrl- DirectTrans+
		ACSCtl:	SrcValid- TransBlk- ReqRedir- CmpltRedir- UpstreamFwd- EgressCtrl- DirectTrans-
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 0106: 1002:4391 (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: 1458:b002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at f090 [size=8]
	Region 1: I/O ports at f080 [size=4]
	Region 2: I/O ports at f070 [size=8]
	Region 3: I/O ports at f060 [size=4]
	Region 4: I/O ports at f050 [size=16]
	Region 5: Memory at feb0b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [70] SATA HBA v1.0 InCfgSpace
	Capabilities: [a4] PCI Advanced Features
		AFCap: TP+ FLR+
		AFCtrl: FLR-
		AFStatus: TP-
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 0c03: 1002:4397 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at feb0a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:12.2 0c03: 1002:4396 (prog-if 20 [EHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at feb09000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci-pci

00:13.0 0c03: 1002:4397 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at feb08000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:13.2 0c03: 1002:4396 (prog-if 20 [EHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at feb07000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci-pci

00:14.0 0c05: 1002:4385 (rev 42)
	Subsystem: 1002:4385
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c_piix4, sp5100_tco

00:14.1 0101: 1002:439c (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: 1458:5002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374
	Region 4: I/O ports at f000 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp, pata_acpi

00:14.2 0403: 1002:4383 (rev 40)
	Subsystem: 1458:a132
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

00:14.3 0601: 1002:439d (rev 40)
	Subsystem: 1002:439d
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 0604: 1002:4384 (rev 40) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe700000-fe7fffff
	Prefetchable memory behind bridge: fff00000-000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 0c03: 1002:4399 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at feb06000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:15.0 0604: 1002:43a0 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe600000-fe6fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot-), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag+ RBE+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep+ BwNot+ ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible+
		RootCap: CRSVisible+
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd-
		DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [b0] Subsystem: 1002:0000
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.2 0604: 1002:43a2 (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fe400000-fe5fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Root Port (Slot-), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0
			ExtTag+ RBE+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #2, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep+ BwNot+ ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible+
		RootCap: CRSVisible+
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported ARIFwd-
		DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-, LTR-, OBFF Disabled ARIFwd-
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [b0] Subsystem: 1002:0000
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 0c03: 1002:4397 (prog-if 10 [OHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:16.2 0c03: 1002:4396 (prog-if 20 [EHCI])
	Subsystem: 1458:5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at feb04000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
		Bridge: PM- B3+
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci-pci

00:18.0 0600: 1022:1600
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b+
		Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Revision ID: 3.00
		Link Frequency: [e]
		Link Error: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE-

00:18.1 0600: 1022:1601
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 0600: 1022:1602
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel modules: amd64_edac_mod

00:18.3 0600: 1022:1603
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 0600: 1022:1604
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: fam15h_power
	Kernel modules: fam15h_power

00:18.5 0600: 1022:1605
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:00.0 0300: 1002:6758 (prog-if 00 [VGA controller])
	Subsystem: 174b:e194
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 31
	Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
	Region 4: I/O ports at e000 [size=256]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0200c  Data: 4154
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Kernel driver in use: radeon
	Kernel modules: radeon

01:00.1 0403: 1002:aa90
	Subsystem: 174b:aa90
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 32
	Region 0: Memory at fea40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis-, LTR-, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee3e00c  Data: 4174
	Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

02:00.0 0c03: 1106:3483 (rev 01) (prog-if 30 [XHCI])
	Subsystem: 1458:5007
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at fe900000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] MSI: Enable+ Count=1/4 Maskable- 64bit+
		Address: 00000000fee3000c  Data: 41a3
	Capabilities: [c4] Express (v2) Endpoint, MSI 00
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <2us, L1 <16us
			ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range B, TimeoutDis+, LTR-, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis+
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Kernel driver in use: xhci_hcd

03:00.0 0106: 1b4b:9172 (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: 1458:b000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 30
	Region 0: I/O ports at d040 [size=8]
	Region 1: I/O ports at d030 [size=4]
	Region 2: I/O ports at d020 [size=8]
	Region 3: I/O ports at d010 [size=4]
	Region 4: I/O ports at d000 [size=16]
	Region 5: Memory at fe810000 (32-bit, non-prefetchable) [size=512]
	Expansion ROM at fe800000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee3f00c  Data: 41e3
	Capabilities: [70] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 512 bytes, PhantFunc 0, Latency L0s <1us, L1 <8us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+, LTR-, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Kernel driver in use: ahci
	Kernel modules: ahci

04:0e.0 0c00: 1106:3044 (rev c0) (prog-if 10 [OHCI])
	Subsystem: 1458:1000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fe700000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at c000 [size=128]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire_ohci

05:00.0 0200: 10ec:8168 (rev 06)
	Subsystem: 1458:e000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 27
	Region 0: I/O ports at b000 [size=256]
	Region 2: Memory at fe600000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at d0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee1000c  Data: 41b3
	Capabilities: [70] Express (v2) Endpoint, MSI 01
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s unlimited, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
			 EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
		Vector table: BAR=4 offset=00000000
		PBA: BAR=4 offset=00000800
	Capabilities: [d0] Vital Product Data
		Unknown small resource type 00, will not decode more.
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
	Kernel driver in use: r8168
	Kernel modules: r8168

06:00.0 0400: 14f1:8880 (rev 04)
	Subsystem: 0070:2a18
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe400000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <2us, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data
		Unknown small resource type 01, will not decode more.
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [200 v1] Virtual Channel
		Caps:	LPEVC=1 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32+ WRR64+ WRR128-
		Ctrl:	ArbSelect=WRR64
		Status:	InProgress-
		Port Arbitration Table [240] <?>
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=1 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Kernel driver in use: cx23885
	Kernel modules: cx23885


```

Any advice leading up to my ability to use this card and/or suggestions of cards that actually work with Mythbuntu would be much appreciated. I don't mind returning this card and getting one that is easy(ier) to configure.

---

### Post by Espryon on 2016-06-25
I went into the kernel and its showing this. It wants me to select the card somehow. I'm going to try researching selecting it and/or using the command it mentioned to help the OS. Any help would be much appreciated.

```
Jun 24 22:56:42 USSEnterprise kernel: [   15.227699] cx23885[0]: Your board isn't known (yet) to the driver.
Jun 24 22:56:42 USSEnterprise kernel: [   15.227699] cx23885[0]: Try to pick one of the existing card configs via
Jun 24 22:56:42 USSEnterprise kernel: [   15.227699] cx23885[0]: card=<n> insmod option.  Updating to the latest
Jun 24 22:56:42 USSEnterprise kernel: [   15.227699] cx23885[0]: version might help as well.
Jun 24 22:56:42 USSEnterprise kernel: [   15.227702] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
Jun 24 22:56:42 USSEnterprise kernel: [   15.227703] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
Jun 24 22:56:42 USSEnterprise kernel: [   15.227704] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
Jun 24 22:56:42 USSEnterprise kernel: [   15.227705] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
Jun 24 22:56:42 USSEnterprise kernel: [   15.227706] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
Jun 24 22:56:42 USSEnterprise kernel: [   15.227707] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
Jun 24 22:56:42 USSEnterprise kernel: [   15.227708] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
Jun 24 22:56:42 USSEnterprise kernel: [   15.227709] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
Jun 24 22:56:42 USSEnterprise kernel: [   15.227710] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
Jun 24 22:56:42 USSEnterprise kernel: [   15.227711] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
Jun 24 22:56:42 USSEnterprise kernel: [   15.227711] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
Jun 24 22:56:42 USSEnterprise kernel: [   15.227712] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
Jun 24 22:56:42 USSEnterprise kernel: [   15.227713] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
Jun 24 22:56:42 USSEnterprise kernel: [   15.227714] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
Jun 24 22:56:42 USSEnterprise kernel: [   15.227715] cx23885[0]:    card=13 -> Compro VideoMate E650F
Jun 24 22:56:42 USSEnterprise kernel: [   15.227716] cx23885[0]:    card=14 -> TurboSight TBS 6920
Jun 24 22:56:42 USSEnterprise kernel: [   15.227717] cx23885[0]:    card=15 -> TeVii S470
Jun 24 22:56:42 USSEnterprise kernel: [   15.227718] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
Jun 24 22:56:42 USSEnterprise kernel: [   15.227719] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
Jun 24 22:56:42 USSEnterprise kernel: [   15.227720] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
Jun 24 22:56:42 USSEnterprise kernel: [   15.227721] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
Jun 24 22:56:42 USSEnterprise kernel: [   15.227722] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
Jun 24 22:56:42 USSEnterprise kernel: [   15.227722] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
Jun 24 22:56:42 USSEnterprise kernel: [   15.227723] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
Jun 24 22:56:42 USSEnterprise kernel: [   15.227724] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
Jun 24 22:56:42 USSEnterprise kernel: [   15.227725] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
Jun 24 22:56:42 USSEnterprise kernel: [   15.227726] cx23885[0]:    card=25 -> Compro VideoMate E800
Jun 24 22:56:42 USSEnterprise kernel: [   15.227727] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
Jun 24 22:56:42 USSEnterprise kernel: [   15.227728] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
Jun 24 22:56:42 USSEnterprise kernel: [   15.227729] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200

```

---

### Post by Espryon on 2016-06-26
Followed these instructions [http://www.gossamer-threads.com/lists/mythtv/users/452987](http://www.gossamer-threads.com/lists/mythtv/users/452987) i.e. creating a file named hvr1250.conf in /etc/modprobe.d/ and putting in that file "options cx23885 card=3". I started an RMA on the card just in case I can't get it working but, I'm hopeful that I can possibly get it working so I don't have to return it (Although Haupapauge isn't doing their company any favors with the exclusivity of support for windows and/or Mac OS).

Going to test it and see whether I can get the card to receive channels from my antenna. I will report back on here what I find. 

```

Jun 26 22:30:24 USSEnterprise kernel: [160811.567872] CORE cx23885[0]: subsystem: 0070:2a18, board: Hauppauge WinTV-HVR1250 [card=3,insmod option]
Jun 26 22:30:24 USSEnterprise kernel: [160811.696592] tveeprom 11-0050: Hauppauge model 161111, rev A1I6, serial# 4035813293
Jun 26 22:30:24 USSEnterprise kernel: [160811.696599] tveeprom 11-0050: MAC address is 00:0d:fe:8d:9f:ad
Jun 26 22:30:24 USSEnterprise kernel: [160811.696603] tveeprom 11-0050: tuner model is SiLabs Si2157 (idx 186, type 4)
Jun 26 22:30:24 USSEnterprise kernel: [160811.696608] tveeprom 11-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
Jun 26 22:30:24 USSEnterprise kernel: [160811.696612] tveeprom 11-0050: audio processor is CX23888 (idx 40)
Jun 26 22:30:24 USSEnterprise kernel: [160811.696615] tveeprom 11-0050: decoder processor is CX23888 (idx 34)
Jun 26 22:30:24 USSEnterprise kernel: [160811.696618] tveeprom 11-0050: has no radio, has IR receiver, has no IR transmitter
Jun 26 22:30:24 USSEnterprise kernel: [160811.696621] cx23885[0]: warning: unknown hauppauge model #161111
Jun 26 22:30:24 USSEnterprise kernel: [160811.696623] cx23885[0]: hauppauge eeprom: model=161111
Jun 26 22:30:24 USSEnterprise kernel: [160811.741825] cx25840 13-0044: cx23888 A/V decoder found @ 0x88 (cx23885[0])
Jun 26 22:30:25 USSEnterprise kernel: [160812.361599] cx25840 13-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
Jun 26 22:30:25 USSEnterprise kernel: [160812.539968] cx23885[0]: registered device video0 [v4l2]
Jun 26 22:30:25 USSEnterprise kernel: [160812.540014] cx23885[0]: registered device vbi0
Jun 26 22:30:25 USSEnterprise kernel: [160812.540175] cx23885[0]: registered ALSA audio device
Jun 26 22:30:25 USSEnterprise kernel: [160812.540178] cx23885_dvb_register() allocating 1 frontend(s)
Jun 26 22:30:25 USSEnterprise kernel: [160812.540181] cx23885[0]: cx23885 based dvb card
Jun 26 22:30:25 USSEnterprise kernel: [160812.579511] cx23885[0]: frontend initialization failed
Jun 26 22:30:25 USSEnterprise kernel: [160812.579521] cx23885_dvb_register() dvb_register failed err = -22
Jun 26 22:30:25 USSEnterprise kernel: [160812.579525] cx23885_dev_setup() Failed to register dvb on VID_C
Jun 26 22:30:25 USSEnterprise kernel: [160812.579531] cx23885_dev_checkrevision() Hardware revision = 0xd0
Jun 26 22:30:25 USSEnterprise kernel: [160812.579540] cx23885[0]/0: found at 0000:06:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfe400000

```

So.. I updated the OS before getting the card to be semi-recognized and now my NIC card has been swapped to the previous driver somehow.. Great! I guess I'll just refix that now before I test the aforementioned card. 

(EDIT #2). Seems like the driver 8168 was actually removed from the update to the OS frustratingly i.e. the new version of 14.04.21 updated to 14.04.??.

(EDIT #3). Seems like the OS recognizes the card now but, is still unable to associate subsystems of the card. With little to go on here, I'm doing an RMA and probably getting this to test [http://www.newegg.com/Product/Product.aspx?Item=N82E16815345015](http://www.newegg.com/Product/Product.aspx?Item=N82E16815345015) , hopefully the refurbished one will become available within the week because of cheaper prices. These are pro ported to work and hopefully they do with Linux.

[https://www.linuxtv.org/wiki/index.php/Silicondust_HDHomeRun](https://www.linuxtv.org/wiki/index.php/Silicondust_HDHomeRun)

---

### Post by Rocko262c on 2017-04-26
Dear Espryon and Community,

I am building a new mythbuntu box and would like to use the Hauppauge WinTV-Starburst DVB-S2 PCIe card (PCIe 1x interface). Has anyone been able to get this card to work?

Thanks for your kind help.

Cheers,
Rocko262

---

