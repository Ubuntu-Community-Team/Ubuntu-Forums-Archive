---
title: "Skype Video Problem"
date: 2010-04-20
forum: Multimedia Software
---

### Post by herbig on 2010-04-20
Hello!  I have a problem with Skype I'd like to get fixed super quick.  I'm pretty sure I messed up my graphics drivers somehow and would like to know how to revert them back to a working version.

First, I was trying to set up dual monitors and followed a bad tutorial on youtube, which told me to use envyng to download drivers.  Unbeknownst to me I installed nvidia drivers when I have an Intel video card.  The output of lspci | grep VGA is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

That messed up my video, but I was able to get to the recovery terminal and restore a backup copy of /etc/xorg.conf and things seem to be back to normal.

Since then though, my video in skype has not been working, whereas it was working perfectly before.  Is there anything I can do to get that back?

---

### Post by Linuxforall on 2010-04-20
> **herbig said:**
> Hello!  I have a problem with Skype I'd like to get fixed super quick.  I'm pretty sure I messed up my graphics drivers somehow and would like to know how to revert them back to a working version.

First, I was trying to set up dual monitors and followed a bad tutorial on youtube, which told me to use envyng to download drivers.  Unbeknownst to me I installed nvidia drivers when I have an Intel video card.  The output of lspci | grep VGA is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

That messed up my video, but I was able to get to the recovery terminal and restore a backup copy of /etc/xorg.conf and things seem to be back to normal.

Since then though, my video in skype has not been working, whereas it was working perfectly before.  Is there anything I can do to get that back?

Can you detect video with Cheese?

---

### Post by herbig on 2010-04-20
Nope, not working there either.  Thanks for your reply!

---

### Post by Linuxforall on 2010-04-20
Is your webcam detected in dmesg?

---

### Post by herbig on 2010-04-20
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000003f6d3400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3f6d3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f6d3400 (usable)
[    0.000000]  modified: 000000003f6d3400 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  modified: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378b4000 - 37fef53f
[    0.000000] Allocated new RAMDISK: 008b2000 - 00fed53f
[    0.000000] Move RAMDISK from 00000000378b4000 - 0000000037fef53e to 008b2000 - 00fed53e
[    0.000000] ACPI: RSDP 000fc1d0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 3f6d39cd 00040 (v01 DELL    M07     27D70402 ASL  00000061)
[    0.000000] ACPI: FACP 3f6d4800 00074 (v01 DELL    M07     27D70402 ASL  00000061)
[    0.000000] ACPI: DSDT 3f6d5400 0438C (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 3f6e3c00 00040
[    0.000000] ACPI: HPET 3f6d4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 3f6d5000 00068 (v01 DELL    M07     27D70402 ASL  00000047)
[    0.000000] ACPI: MCFG 3f6d4fc0 0003E (v16 DELL    M07     27D70402 ASL  00000061)
[    0.000000] ACPI: SLIC 3f6d509c 00176 (v01 DELL    M07     27D70402 ASL  00000061)
[    0.000000] ACPI: BOOT 3f6d4bc0 00028 (v01 DELL    M07     27D70402 ASL  00000061)
[    0.000000] ACPI: SSDT 3f6d3a0d 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1180]              BRK ==> [00008ae000 - 00008b1180]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b2000 - 0000fed53f]      NEW RAMDISK ==> [00008b2000 - 0000fed53f]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6d3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f6d3
[    0.000000] On node 0 totalpages: 259694
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32215 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:b0000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257664
[    0.000000] Kernel command line: root=UUID=24c9c066-3215-4627-b880-75976b523228 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5195900 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d3)
[    0.000000] Memory: 1008972k/1039180k available (4578k kernel code, 29440k reserved, 2146k data, 540k init, 129876k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1728.627 MHz processor.
[    0.002592] Console: colour VGA+ 80x25
[    0.002599] console [tty0] enabled
[    0.002886] hpet clockevent registered
[    0.002906] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002917] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.25 BogoMIPS (lpj=6914508)
[    0.002973] Security Framework initialized
[    0.003032] AppArmor: AppArmor initialized
[    0.003046] Mount-cache hash table entries: 512
[    0.003419] Initializing cgroup subsys ns
[    0.003429] Initializing cgroup subsys cpuacct
[    0.003449] Initializing cgroup subsys memory
[    0.003475] Initializing cgroup subsys freezer
[    0.003480] Initializing cgroup subsys net_cls
[    0.003517] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003524] CPU: L2 cache: 2048K
[    0.003541] CPU: Physical Processor ID: 0
[    0.003546] CPU: Processor Core ID: 0
[    0.003554] mce: CPU supports 6 MCE banks
[    0.003585] CPU0: Thermal monitoring enabled (TM2)
[    0.003602] using mwait in idle threads.
[    0.003613] Performance Counters: no PMU driver, software counters only.
[    0.003635] Checking 'hlt' instruction... OK.
[    0.020008] ACPI: Core revision 20090521
[    0.040713] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.082849] CPU0: Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3460.67 BogoMIPS (lpj=6921357)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.169142] CPU1: Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[    0.169197] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.172001] Measured 3242375383 cycles TSC warp between CPUs, turning off TSC clock.
[    0.172001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.172062] Brought up 2 CPUs
[    0.172070] Total of 2 processors activated (6917.93 BogoMIPS).
[    0.172175] CPU0 attaching sched-domain:
[    0.172193]  domain 0: span 0-1 level MC
[    0.172200]   groups: 0 1
[    0.172224] CPU1 attaching sched-domain:
[    0.172229]  domain 0: span 0-1 level MC
[    0.172236]   groups: 1 0
[    0.172495] Booting paravirtualized kernel on bare hardware
[    0.172797] regulator: core version 0.5
[    0.172797] Time:  1:18:41  Date: 04/21/10
[    0.172797] NET: Registered protocol family 16
[    0.172797] EISA bus registered
[    0.172797] ACPI: bus type pci registered
[    0.176154] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.176162] PCI: MCFG area at f0000000 reserved in E820
[    0.176178] PCI: Using MMCONFIG for extended config space
[    0.176184] PCI: Using configuration type 1 for base access
[    0.180122] bio: create slab <bio-0> at 0
[    0.182249] ACPI: EC: Look up EC in DSDT
[    0.223515] ACPI: Interpreter enabled
[    0.223539] ACPI: (supports S0 S3 S4 S5)
[    0.223609] ACPI: Using IOAPIC for interrupt routing
[    0.300418] ACPI: No dock devices found.
[    0.338699] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.338989] pci 0000:00:02.0: reg 10 32bit mmio: [0xeff00000-0xeff7ffff]
[    0.339013] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
[    0.339025] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.339048] pci 0000:00:02.0: reg 1c 32bit mmio: [0xefec0000-0xefefffff]
[    0.339174] pci 0000:00:02.1: reg 10 32bit mmio: [0xeff80000-0xefffffff]
[    0.339445] pci 0000:00:1b.0: reg 10 64bit mmio: [0xefebc000-0xefebffff]
[    0.339589] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.339599] pci 0000:00:1b.0: PME# disabled
[    0.339791] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.339801] pci 0000:00:1c.0: PME# disabled
[    0.340021] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.340031] pci 0000:00:1c.1: PME# disabled
[    0.340239] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.340249] pci 0000:00:1c.3: PME# disabled
[    0.340401] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.340541] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.340691] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.340830] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.340985] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80000-0xffa803ff]
[    0.341121] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.341142] pci 0000:00:1d.7: PME# disabled
[    0.341498] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.341509] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.341529] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.341542] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.341694] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.341709] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.341735] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.341760] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.341775] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.341861] pci 0000:00:1f.2: PME# supported from D3hot
[    0.341871] pci 0000:00:1f.2: PME# disabled
[    0.342002] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.342493] pci 0000:0c:00.0: reg 10 32bit mmio: [0xefdfc000-0xefdfffff]
[    0.342932] pci 0000:0c:00.0: supports D1 D2
[    0.343168] pci 0000:00:1c.1: bridge 32bit mmio: [0xefd00000-0xefdfffff]
[    0.343321] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.343332] pci 0000:00:1c.3: bridge 32bit mmio: [0xefa00000-0xefcfffff]
[    0.343358] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xe0000000-0xe01fffff]
[    0.343456] pci 0000:02:00.0: reg 10 32bit mmio: [0xef9fe000-0xef9fffff]
[    0.343582] pci 0000:02:00.0: supports D1 D2
[    0.343588] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.343599] pci 0000:02:00.0: PME# disabled
[    0.343695] pci 0000:02:01.0: reg 10 32bit mmio: [0xef9fd800-0xef9fdfff]
[    0.343824] pci 0000:02:01.0: supports D1 D2
[    0.343840] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.343850] pci 0000:02:01.0: PME# disabled
[    0.343947] pci 0000:02:01.1: reg 10 32bit mmio: [0xef9fd400-0xef9fd4ff]
[    0.344081] pci 0000:02:01.1: supports D1 D2
[    0.344098] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344108] pci 0000:02:01.1: PME# disabled
[    0.344204] pci 0000:02:01.2: reg 10 32bit mmio: [0xef9fd500-0xef9fd5ff]
[    0.344332] pci 0000:02:01.2: supports D1 D2
[    0.344338] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344359] pci 0000:02:01.2: PME# disabled
[    0.344456] pci 0000:02:01.3: reg 10 32bit mmio: [0xef9fd600-0xef9fd6ff]
[    0.344585] pci 0000:02:01.3: supports D1 D2
[    0.344591] pci 0000:02:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344601] pci 0000:02:01.3: PME# disabled
[    0.344698] pci 0000:02:01.4: reg 10 32bit mmio: [0xef9fd700-0xef9fd7ff]
[    0.344827] pci 0000:02:01.4: supports D1 D2
[    0.344833] pci 0000:02:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344853] pci 0000:02:01.4: PME# disabled
[    0.344992] pci 0000:00:1e.0: transparent bridge
[    0.345017] pci 0000:00:1e.0: bridge 32bit mmio: [0xef900000-0xef9fffff]
[    0.345089] pci_bus 0000:00: on NUMA node 0
[    0.345110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.346096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.346398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.346661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.346940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.379879] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.380298] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.380702] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.381093] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.381502] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.381904] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.382315] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.382728] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.383376] SCSI subsystem initialized
[    0.383457] libata version 3.00 loaded.
[    0.383457] usbcore: registered new interface driver usbfs
[    0.383457] usbcore: registered new interface driver hub
[    0.384040] usbcore: registered new device driver usb
[    0.384245] ACPI: WMI: Mapper loaded
[    0.384251] PCI: Using ACPI for IRQ routing
[    0.396030] Bluetooth: Core ver 2.15
[    0.396075] NET: Registered protocol family 31
[    0.396075] Bluetooth: HCI device and connection manager initialized
[    0.396075] Bluetooth: HCI socket layer initialized
[    0.396078] NetLabel: Initializing
[    0.396083] NetLabel:  domain hash size = 128
[    0.396087] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.396130] NetLabel:  unlabeled traffic allowed by default
[    0.396242] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.396256] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.404042] Switched to high resolution mode on CPU 0
[    0.405297] Switched to high resolution mode on CPU 1
[    0.416046] pnp: PnP ACPI init
[    0.416082] ACPI: bus type pnp registered
[    0.507641] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.507652] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.507954] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.507965] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.507985] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.507995] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.511649] pnp: PnP ACPI: found 12 devices
[    0.511665] ACPI: ACPI bus type pnp unregistered
[    0.511674] PnPBIOS: Disabled by ACPI PNP
[    0.511708] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.511727] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.511735] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.511744] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.511763] system 00:00: iomem range 0x100000-0x3f6d33ff could not be reserved
[    0.511771] system 00:00: iomem range 0x3f6d3400-0x3f6fffff has been reserved
[    0.511790] system 00:00: iomem range 0x3f700000-0x3f7fffff has been reserved
[    0.511799] system 00:00: iomem range 0x3f700000-0x3fefffff could not be reserved
[    0.511808] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.511827] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.511836] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.511854] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.511863] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.511872] system 00:00: iomem range 0xf4000000-0xf4003fff has been reserved
[    0.511891] system 00:00: iomem range 0xf4004000-0xf4004fff has been reserved
[    0.511899] system 00:00: iomem range 0xf4005000-0xf4005fff has been reserved
[    0.511918] system 00:00: iomem range 0xf4006000-0xf4006fff has been reserved
[    0.511927] system 00:00: iomem range 0xf4008000-0xf400bfff has been reserved
[    0.511935] system 00:00: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.511963] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.511989] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.511998] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.512032] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.512051] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.512081] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.512089] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.512097] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.512115] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.512123] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.512151] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.547266] AppArmor: AppArmor Filesystem Enabled
[    0.547426] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.547432] pci 0000:00:1c.0:   IO window: disabled
[    0.547443] pci 0000:00:1c.0:   MEM window: disabled
[    0.547463] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.547474] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.547490] pci 0000:00:1c.1:   IO window: disabled
[    0.547502] pci 0000:00:1c.1:   MEM window: 0xefd00000-0xefdfffff
[    0.547522] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.547532] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.547541] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.547564] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefcfffff
[    0.547585] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
[    0.547601] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.547617] pci 0000:00:1e.0:   IO window: disabled
[    0.547629] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.547649] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.547683]   alloc irq_desc for 16 on node -1
[    0.547689]   alloc kstat_irqs on node -1
[    0.547702] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.547724] pci 0000:00:1c.0: setting latency timer to 64
[    0.547751]   alloc irq_desc for 17 on node -1
[    0.547756]   alloc kstat_irqs on node -1
[    0.547765] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.547786] pci 0000:00:1c.1: setting latency timer to 64
[    0.547812]   alloc irq_desc for 19 on node -1
[    0.547817]   alloc kstat_irqs on node -1
[    0.547826] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.547847] pci 0000:00:1c.3: setting latency timer to 64
[    0.547862] pci 0000:00:1e.0: setting latency timer to 64
[    0.547883] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.547891] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.547909] pci_bus 0000:0c: resource 1 mem: [0xefd00000-0xefdfffff]
[    0.547917] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.547925] pci_bus 0000:0d: resource 1 mem: [0xefa00000-0xefcfffff]
[    0.547943] pci_bus 0000:0d: resource 2 pref mem [0xe0000000-0xe01fffff]
[    0.547951] pci_bus 0000:02: resource 1 mem: [0xef900000-0xef9fffff]
[    0.547958] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.547976] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.548111] NET: Registered protocol family 2
[    0.548452] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.549512] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.551827] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.553013] TCP: Hash tables configured (established 131072 bind 65536)
[    0.553020] TCP reno registered
[    0.553294] NET: Registered protocol family 1
[    0.553485] Trying to unpack rootfs image as initramfs...
[    1.001029] Clocksource tsc unstable (delta = 1875932955 ns)
[    1.290407] Freeing initrd memory: 7405k freed
[    1.299755] Simple Boot Flag at 0x79 set to 0x1
[    1.300446] cpufreq-nforce2: No nForce2 chipset.
[    1.300557] Scanning for low memory corruption every 60 seconds
[    1.300893] audit: initializing netlink socket (disabled)
[    1.300942] type=2000 audit(1271812722.300:1): initialized
[    1.333373] highmem bounce pool size: 64 pages
[    1.333385] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.339405] VFS: Disk quotas dquot_6.5.2
[    1.339633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.341821] fuse init (API version 7.12)
[    1.342144] msgmni has been set to 1732
[    1.342930] alg: No test for stdrng (krng)
[    1.342979] io scheduler noop registered
[    1.342986] io scheduler anticipatory registered
[    1.342991] io scheduler deadline registered
[    1.343151] io scheduler cfq registered (default)
[    1.343188] pci 0000:00:02.0: Boot video device
[    1.343829]   alloc irq_desc for 24 on node -1
[    1.343847]   alloc kstat_irqs on node -1
[    1.343878] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.343910] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.344330]   alloc irq_desc for 25 on node -1
[    1.344335]   alloc kstat_irqs on node -1
[    1.344362] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    1.344391] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.344788]   alloc irq_desc for 26 on node -1
[    1.344794]   alloc kstat_irqs on node -1
[    1.344820] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    1.344849] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.345165] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.345498] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.346657] ACPI: AC Adapter [AC] (on-line)
[    1.346943] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.347759] ACPI: Lid Switch [LID]
[    1.347929] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.347952] ACPI: Power Button [PBTN]
[    1.348212] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.348220] ACPI: Sleep Button [SBTN]
[    1.350399] ACPI: SSDT 3f6d4134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.351581] ACPI: SSDT 3f6d3ee9 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.353318] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.353414] processor LNXCPU:00: registered as cooling_device0
[    1.353425] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.354622] ACPI: SSDT 3f6d4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.355629] ACPI: SSDT 3f6d40af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.357100] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.357193] processor LNXCPU:01: registered as cooling_device1
[    1.357204] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.372789] thermal LNXTHERM:01: registered as thermal_zone0
[    1.372822] ACPI: Thermal Zone [THM] (34 C)
[    1.373118] isapnp: Scanning for PnP cards...
[    1.400221] ACPI: Battery Slot [BAT0] (battery absent)
[    1.738422] isapnp: No Plug & Play device found
[    1.742752] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.747737] brd: module loaded
[    1.749516] loop: module loaded
[    1.749786] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.750178] ata_piix 0000:00:1f.2: version 2.13
[    1.750219] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.750242] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.750365] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.750594] scsi0 : ata_piix
[    1.750892] scsi1 : ata_piix
[    1.753581] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.753600] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.757044] Fixed MDIO Bus: probed
[    1.757174] PPP generic driver version 2.4.2
[    1.757478] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.757552]   alloc irq_desc for 20 on node -1
[    1.757557]   alloc kstat_irqs on node -1
[    1.757582] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.757612] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.757621] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.757733] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.757744] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.761707] ehci_hcd 0000:00:1d.7: debug port 1
[    1.761720] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.761817] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    1.776044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.776316] usb usb1: configuration #1 chosen from 1 choice
[    1.776419] hub 1-0:1.0: USB hub found
[    1.776447] hub 1-0:1.0: 8 ports detected
[    1.776653] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.776716] uhci_hcd: USB Universal Host Controller Interface driver
[    1.776799] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.776813] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.776832] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.776938] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.777000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    1.777284] usb usb2: configuration #1 chosen from 1 choice
[    1.777382] hub 2-0:1.0: USB hub found
[    1.777408] hub 2-0:1.0: 2 ports detected
[    1.777559]   alloc irq_desc for 21 on node -1
[    1.777564]   alloc kstat_irqs on node -1
[    1.777575] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.777599] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.777607] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.777723] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.777798] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    1.778072] usb usb3: configuration #1 chosen from 1 choice
[    1.778169] hub 3-0:1.0: USB hub found
[    1.778184] hub 3-0:1.0: 2 ports detected
[    1.778343]   alloc irq_desc for 22 on node -1
[    1.778359]   alloc kstat_irqs on node -1
[    1.778370] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.778393] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.778401] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.778505] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.778589] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    1.778853] usb usb4: configuration #1 chosen from 1 choice
[    1.778952] hub 4-0:1.0: USB hub found
[    1.778977] hub 4-0:1.0: 2 ports detected
[    1.779130]   alloc irq_desc for 23 on node -1
[    1.779135]   alloc kstat_irqs on node -1
[    1.779146] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.779169] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.779177] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.779303] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.779391] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    1.779658] usb usb5: configuration #1 chosen from 1 choice
[    1.779756] hub 5-0:1.0: USB hub found
[    1.779781] hub 5-0:1.0: 2 ports detected
[    1.780112] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.783333] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.783358] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.783595] mice: PS/2 mouse device common for all mice
[    1.784038] rtc_cmos 00:06: RTC can wake from S4
[    1.784163] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.784257] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.784659] device-mapper: uevent: version 1.0.3
[    1.784973] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.785263] device-mapper: multipath: version 1.1.0 loaded
[    1.785270] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.785749] EISA: Probing bus 0 at eisa.0
[    1.785872] EISA: Mainboard QG_FFFF detected.
[    1.785930] Cannot allocate resource for EISA slot 1
[    1.786014] EISA: Detected 0 cards.
[    1.786669] cpuidle: using governor ladder
[    1.786927] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.787220] cpuidle: using governor menu
[    1.789085] TCP cubic registered
[    1.789712] NET: Registered protocol family 10
[    1.791384] lo: Disabled Privacy Extensions
[    1.792668] NET: Registered protocol family 17
[    1.792731] Bluetooth: L2CAP ver 2.13
[    1.792736] Bluetooth: L2CAP socket layer initialized
[    1.792754] Bluetooth: SCO (Voice Link) ver 0.6
[    1.792759] Bluetooth: SCO socket layer initialized
[    1.792889] Bluetooth: RFCOMM TTY layer initialized
[    1.792897] Bluetooth: RFCOMM socket layer initialized
[    1.792913] Bluetooth: RFCOMM ver 1.11
[    1.794221] Using IPI No-Shortcut mode
[    1.794334] PM: Resume from disk failed.
[    1.794347] registered taskstats version 1
[    1.794539]   Magic number: 6:937:306
[    1.794573] tty tty35: hash matches
[    1.794702] rtc_cmos 00:06: setting system clock to 2010-04-21 01:18:43 UTC (1271812723)
[    1.794716] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.794718] EDD information not available.
[    1.917349] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC74P, max UDMA/100
[    1.917368] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.924959] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A102, max UDMA/33
[    1.933216] ata1.00: configured for UDMA/100
[    1.933420] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    1.933613] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.933679] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.933757] sd 0:0:0:0: [sda] Write Protect is off
[    1.933771] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.933811] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.934033]  sda:
[    1.940510] ata2.00: configured for UDMA/33
[    1.949548] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A102 PQ: 0 ANSI: 5
[    1.961420] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.961424] Uniform CD-ROM driver Revision: 3.20
[    1.961559] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.961639] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.963974]  sda1 sda2 < sda5 >
[    1.999108] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.999162] Freeing unused kernel memory: 540k freed
[    1.999771] Write protecting the kernel text: 4580k
[    1.999872] Write protecting the kernel read-only data: 1840k
[    2.101061] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    2.195214] Linux agpgart interface v0.103
[    2.201330] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    2.202263] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.206756] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.252327] acpi device:24: registered as cooling_device2
[    2.252860] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/input/input5
[    2.252934] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.253026] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    2.253146] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/input/input6
[    2.253185] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    2.372392] [drm] Initialized drm 1.1.0 20060810
[    2.383002] usb 1-5: configuration #1 chosen from 1 choice
[    2.405276] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.405308] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    2.430731] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.430750] i915 0000:00:02.0: setting latency timer to 64
[    2.440537] ohci1394 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.522112] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.535287] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    2.541116] b44 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.608126] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    2.608166] b44.c:v2.0
[    2.629293] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:77:9a:41
[    3.048225] [drm] TV-14: set mode NTSC 480i 0
[    3.180987] [drm] fb0: inteldrmfb frame buffer device
[    3.181013] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.252759] [drm] DAC-6: set mode 1280x1024 26
[    3.313639] [drm] LVDS-8: set mode 1280x800 28
[    3.420608] Console: switching to colour frame buffer device 160x50
[    3.779120] PM: Starting manual resume from disk
[    3.779125] PM: Resume from partition 8:5
[    3.779128] PM: Checking hibernation image.
[    3.779397] PM: Resume from disk failed.
[    3.800289] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc0001ba1c561]
[    3.812256] kjournald starting.  Commit interval 5 seconds
[    3.812291] EXT3-fs: mounted filesystem with writeback data mode.
[    5.110135] type=1505 audit(1271812726.814:2): operation="profile_load" pid=391 name=/usr/share/gdm/guest-session/Xsession
[    5.186659] type=1505 audit(1271812726.891:3): operation="profile_load" pid=392 name=/sbin/dhclient3
[    5.187766] type=1505 audit(1271812726.891:4): operation="profile_load" pid=392 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.188395] type=1505 audit(1271812726.893:5): operation="profile_load" pid=392 name=/usr/lib/connman/scripts/dhclient-script
[    5.300239] type=1505 audit(1271812727.005:6): operation="profile_load" pid=393 name=/usr/bin/evince
[    5.318198] type=1505 audit(1271812727.021:7): operation="profile_load" pid=393 name=/usr/bin/evince-previewer
[    5.328896] type=1505 audit(1271812727.033:8): operation="profile_load" pid=393 name=/usr/bin/evince-thumbnailer
[    5.384193] type=1505 audit(1271812727.089:9): operation="profile_load" pid=395 name=/usr/lib/cups/backend/cups-pdf
[    5.385501] type=1505 audit(1271812727.089:10): operation="profile_load" pid=395 name=/usr/sbin/cupsd
[   42.254814] udev: starting version 147
[   42.289631] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[   42.403996] sdhci: Secure Digital Host Controller Interface driver
[   42.404001] sdhci: Copyright(c) Pierre Ossman
[   42.406708] sdhci-pci 0000:02:01.1: SDHCI controller found [1180:0822] (rev 19)
[   42.406742]   alloc irq_desc for 18 on node -1
[   42.406746]   alloc kstat_irqs on node -1
[   42.406766] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   42.408890] Registered led device: mmc0::
[   42.409969] mmc0: SDHCI controller on PCI [0000:02:01.1] using DMA
[   42.427093] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   42.427465] ricoh-mmc: Ricoh MMC Controller disabling driver
[   42.427468] ricoh-mmc: Copyright(c) Philip Langdale
[   42.427529] ricoh-mmc: Ricoh MMC controller found at 0000:02:01.2 [1180:0843] (rev 1)
[   42.427558] ricoh-mmc: Controller is now disabled.
[   42.491084] lp: driver loaded but no devices found
[   42.493577] intel_rng: FWH not detected
[   42.526437] Linux video capture interface: v2.00
[   42.582471] EXT3 FS on sda1, internal journal
[   42.621635] Disabling lock debugging due to kernel taint
[   42.630969] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   42.668462] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0804)
[   42.699105] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   42.724254] input: UVC Camera (046d:0804) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[   42.724350] usbcore: registered new interface driver uvcvideo
[   42.724354] USB Video Class driver (v0.1.0)
[   42.779963] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.828216] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   42.828281] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   42.952705] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   42.952857] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   43.033049] usbcore: registered new interface driver snd-usb-audio
[   43.033355] usbcore: registered new interface driver ndiswrapper
[   43.210566] nf_conntrack version 0.5.0 (16237 buckets, 64948 max)
[   43.210922] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   43.210942] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   43.210951] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   43.212029] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   43.271889] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   43.396332] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.601852] __ratelimit: 12 callbacks suppressed
[   43.601867] type=1505 audit(1271812765.305:15): operation="profile_replace" pid=1031 name=/usr/share/gdm/guest-session/Xsession
[   43.604615] type=1505 audit(1271812765.309:16): operation="profile_replace" pid=1032 name=/sbin/dhclient3
[   43.605745] type=1505 audit(1271812765.309:17): operation="profile_replace" pid=1032 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   43.606355] type=1505 audit(1271812765.309:18): operation="profile_replace" pid=1032 name=/usr/lib/connman/scripts/dhclient-script
[   43.612714] type=1505 audit(1271812765.317:19): operation="profile_replace" pid=1033 name=/usr/bin/evince
[   43.632265] type=1505 audit(1271812765.337:20): operation="profile_replace" pid=1033 name=/usr/bin/evince-previewer
[   43.642834] type=1505 audit(1271812765.345:21): operation="profile_replace" pid=1033 name=/usr/bin/evince-thumbnailer
[   43.658517] type=1505 audit(1271812765.362:22): operation="profile_replace" pid=1035 name=/usr/lib/cups/backend/cups-pdf
[   43.659828] type=1505 audit(1271812765.362:23): operation="profile_replace" pid=1035 name=/usr/sbin/cupsd
[   43.664387] type=1505 audit(1271812765.366:24): operation="profile_replace" pid=1036 name=/usr/sbin/mysqld
[   44.927388] [drm] DAC-6: set mode 1024x768 2a
[   45.217561] [drm] LVDS-8: set mode 1024x768 2b
[   50.824642] [drm] LVDS-8: set mode  29
[   51.285711] [drm] DAC-6: set mode  2f
[   66.802048] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   66.802052] vboxdrv: Successfully done.
[   66.802054] vboxdrv: Found 2 processor cores.
[   66.802195] vboxdrv: fAsync=1 offMin=0xc1425243 offMax=0xc1425243
[   66.802273] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   66.802276] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
[   67.161055] ppdev: user-space parallel port driver
[  113.099405] lib80211: common routines for IEEE802.11 drivers
[  113.099410] lib80211_crypt: registered algorithm 'NULL'
[  113.137363] b44: eth0: powering down PHY
[  113.177507] b44 0000:02:00.0: PCI INT A disabled
[  113.205463] b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[  113.236245] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  113.236282] wl 0000:0c:00.0: setting latency timer to 64
[  113.249763] lib80211_crypt: registered algorithm 'TKIP'
[  113.249948] eth0: Broadcom BCM4311 802.11 Wireless Controller 5.10.91.9
[  113.252887] udev: renamed network interface eth0 to eth1
[  124.300150] eth1: no IPv6 routers present
[  153.741156] CE: hpet increasing min_delta_ns to 15000 nsec
[  190.278016] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  235.705767] Inbound IN=eth1 OUT= MAC=00:19:7d:7a:2b:bf:00:17:3f:e7:32:17:08:00 SRC=24.18.254.109 DST=192.168.2.7 LEN=48 TOS=0x00 PREC=0x20 TTL=110 ID=7086 PROTO=UDP SPT=38063 DPT=61598 LEN=28 
[  242.311681] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  351.219279] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  351.220767] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  427.927780] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  427.929373] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  429.922773] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  548.625799] CE: hpet increasing min_delta_ns to 22500 nsec
[  596.476574] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  622.828999] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  642.614281] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  642.849965] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  659.641890] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  662.868146] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  682.885513] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  702.931845] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  706.384574] Inbound IN=eth1 OUT= MAC=00:19:7d:7a:2b:bf:00:17:3f:e7:32:17:08:00 SRC=72.45.204.82 DST=192.168.2.7 LEN=56 TOS=0x00 PREC=0x00 TTL=117 ID=18691 PROTO=UDP SPT=53796 DPT=61598 LEN=36 
[  722.946323] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  727.432080] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  730.125070] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  743.824308] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  743.869274] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  743.919314] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  743.969291] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.019306] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.069292] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.119287] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.169310] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.219732] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.269281] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.319260] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.370808] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.419455] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.469411] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.519431] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.569497] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.619291] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.669517] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.719324] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.769651] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.819351] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.869309] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.919333] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  744.969355] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.019396] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.069393] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.119354] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.169356] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.269373] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.319373] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.369346] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.420852] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.469341] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.519382] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.569420] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.619410] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.719482] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.769453] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.819419] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.869393] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.919442] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  745.969345] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.019458] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.069393] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.119438] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.169390] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.219406] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.269467] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.319447] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.369417] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.419475] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.469411] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.521254] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.569471] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.619472] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.669453] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.719448] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.769468] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.820143] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.869500] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.919568] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  746.969464] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.019478] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.069528] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.119492] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.169484] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.219517] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.269500] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.319457] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.369550] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.419521] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.469561] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.519541] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.571311] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.619564] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.669528] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.719535] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.769547] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.819541] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.869541] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.919557] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  747.969556] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.019572] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.069537] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.119535] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.169561] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.219525] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.269577] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.319534] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.369592] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.419665] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.469573] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.519557] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.569580] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.619584] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.669681] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.719593] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.769624] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.820098] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.869628] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.919638] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  748.970539] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.019622] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.069653] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.119642] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.169927] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.219675] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.269632] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.319643] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.419660] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.469660] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.519962] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.569623] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.619687] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.669695] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.721949] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.769663] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.819738] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.869695] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.919824] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  749.969667] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.019733] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.069695] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.119676] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.219726] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.269701] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.319713] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.369700] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.419829] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.470191] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.519796] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.569738] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.619777] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.669766] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.719757] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.769735] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.819761] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.869769] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.920121] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  750.970315] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.019786] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.069759] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.121078] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.169750] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.219751] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.269769] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.319763] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.369802] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.419814] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.470314] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.519749] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.569896] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.619802] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.669826] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.719813] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.770019] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.819802] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.872244] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.919838] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  751.969903] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.019858] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.069907] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.119852] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.169844] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.219834] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.269910] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.319939] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.369888] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.419888] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.469890] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.519854] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.569842] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.619844] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.719865] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.769938] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.819907] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.870127] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.919942] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  752.969912] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.019906] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.069934] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.170337] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.219943] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.269946] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.319930] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.369975] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.419974] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.469968] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.519967] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.569964] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.619975] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.670005] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.719980] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.769932] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.819975] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.869955] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.920180] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  753.969982] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.022793] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.070007] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.120082] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.169968] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.220044] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.270017] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.320060] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.369955] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.420107] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.469985] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.520019] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.570324] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.620060] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.670021] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.720055] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.770134] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.820083] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.870046] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.920075] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  754.970062] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.020632] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.070420] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.120132] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.170054] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.220161] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.270044] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.320148] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.370054] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.420136] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.470176] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.520103] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.570255] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.620144] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.670113] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.720127] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.770120] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.820136] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.870200] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  755.920148] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.020193] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.070687] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.120196] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.173153] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.220141] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.270241] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.320149] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.370207] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  756.420140] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  757.414485] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  757.530001] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  757.650386] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  757.700506] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  757.750652] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.092611] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.093558] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.170107] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.221161] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.270396] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.320808] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.831584] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  758.931434] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  759.219014] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  759.219925] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  759.575969] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  759.731011] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  759.802378] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  760.959851] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  761.267036] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  761.267986] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  761.369436] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  761.659688] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  762.117336] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  762.168282] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  762.225833] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  762.270624] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  762.874435] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  763.127745] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  763.417453] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  763.605616] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  763.650939] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  763.720440] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  764.197052] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  764.263650] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  764.300908] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  764.595082] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  765.197953] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  765.670300] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  765.671281] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  765.772702] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  765.977549] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.110113] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.150992] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.284754] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.331030] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.429102] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.493911] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.541167] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.592064] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.641133] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.691041] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.741409] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  766.791669] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.001469] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.206314] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.308698] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.615987] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.696894] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  767.878637] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  768.013651] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  768.061264] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  768.111271] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  768.211493] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  768.324466] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.049522] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.128183] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.171393] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.297646] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.561500] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.562418] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.609131] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.651386] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  769.710896] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.176002] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.176853] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.231475] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.269958] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.311649] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.447717] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.513511] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.695290] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.741527] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.981187] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  770.999008] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.041455] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.091523] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.141357] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.191626] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.328586] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.507178] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  771.814417] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.100931] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.151502] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.201451] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.251624] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.428723] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.429655] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.531139] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.538123] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.581528] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.631621] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.681632] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  772.895970] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.191874] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.205621] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.251575] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.301657] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.351823] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.452763] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.502209] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.551679] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.693395] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.741670] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.791617] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.843700] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  773.995765] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.041704] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.231650] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.351684] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.476781] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.579251] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.704242] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.810232] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  774.893998] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.006695] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.051795] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.603196] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.604152] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.638274] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.681903] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  775.731920] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.083037] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.131956] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.181932] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.755964] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.802005] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  776.871887] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.036789] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.139214] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.140186] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.202535] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.252000] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.302024] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.524417] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.572067] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  777.898752] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.163210] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.221884] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.270447] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.311933] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.399665] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.442048] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.492168] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.542020] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.642191] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.742082] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.817366] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  778.862587] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.061807] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.100368] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.142141] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.192221] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.699245] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.751987] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.765113] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  779.812234] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  780.211224] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  780.212168] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  780.221038] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  780.262622] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  780.825635] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  781.094015] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  781.324274] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  781.421916] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  781.472324] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  781.803503] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  782.212069] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  782.252371] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  782.663496] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  782.900071] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.019213] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.062519] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.229314] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.348177] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.530715] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.572511] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.622753] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.697458] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  783.804896] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.090142] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.132616] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.182630] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.512104] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.716879] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  784.717865] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.024133] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.126471] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.206744] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.255337] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.382984] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.740901] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.843336] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  785.844264] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  786.252898] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  786.346703] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  786.641526] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  787.481703] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  787.901971] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  788.608134] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  788.685454] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  788.815708] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  788.989919] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  789.033126] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  789.324996] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  790.144146] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=e8f76240
[  802.312677] CE: hpet increasing min_delta_ns to 33750 nsec
[ 1328.066084] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1348.087190] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1368.103137] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1408.141712] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1428.161366] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.067568] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.115032] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.164975] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.214996] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.264987] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.315012] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.365022] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.415060] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.465650] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.565008] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.615015] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.665110] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.715069] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.765025] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.815126] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1449.915123] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.015052] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.065065] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.165060] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.215044] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.265069] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.315587] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.365084] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.415115] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.465092] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.515113] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.565107] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.615154] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.665104] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.715511] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.815135] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.865126] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.915127] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1450.965152] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.015131] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.065129] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.115167] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.165485] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.215126] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.315149] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.365484] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.415172] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.465182] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.515159] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.565175] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.615131] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.665660] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.715154] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.765203] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.815429] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.865215] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.915186] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1451.965205] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.015177] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.065213] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.115201] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.165209] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.215171] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.315228] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.365221] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.415244] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.466036] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.515181] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.565272] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.615217] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.665239] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.715248] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.765257] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.815246] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.865736] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1452.965284] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.015304] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.065658] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.115336] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.165257] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.215292] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.265256] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.315281] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.365269] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.415296] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.465308] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.515301] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.565329] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.615289] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.665303] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.715295] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.765320] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.815333] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.865675] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.915337] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1453.965358] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.015342] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.065663] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.115351] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.165382] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.215663] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.265355] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.315420] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.365398] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.415781] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.515394] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.565368] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.616416] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.665419] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.715383] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.765342] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.815369] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.865427] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.915408] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1454.965386] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.015421] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.115400] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.165418] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.215420] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.265669] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.315398] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.365461] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.415431] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.515407] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.565570] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.615464] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.715412] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.765472] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.865679] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.915443] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1455.965542] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.015435] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.065667] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.115450] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.165485] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.215445] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.315441] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.365542] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.415492] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.515473] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.565624] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.615535] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.665566] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.715521] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.766886] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.815522] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.865718] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.915509] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1456.965689] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.015552] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.065663] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.115549] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.165607] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.215555] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.265537] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.315606] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.365536] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.415634] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.465710] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.515619] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.565692] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.615585] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.665673] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.715609] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.765959] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.815611] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.865718] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.915611] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1457.965583] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.015674] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.066834] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.115585] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.165725] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.215610] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.265651] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.315684] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.365698] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.415647] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.465811] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.515685] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.565719] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.615689] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.665710] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.715692] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.765686] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.815718] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.865743] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.917218] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1458.965769] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.015724] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.065661] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.115715] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.165707] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.215679] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.265782] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.315834] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.365768] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.415714] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.465765] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.565743] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.615711] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.665864] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.715688] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.765816] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.815732] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.915739] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1459.965788] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.015764] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.065863] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.115717] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.165887] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.215747] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.265807] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.365804] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.415777] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.465886] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.515831] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.565858] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.615792] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.665813] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.765841] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.816047] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.865910] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.915779] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1460.965912] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.015800] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.067611] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.115787] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.165847] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.215806] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.265906] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.315831] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.365930] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.416076] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.465941] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.515875] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.565873] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.615851] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1461.665945] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1466.479183] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1467.499343] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1467.546272] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1467.646711] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1467.696625] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1468.780893] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1468.826390] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1469.669329] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1470.386149] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1470.808801] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1470.856582] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1471.522026] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1471.566635] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1471.616676] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1471.666651] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1472.693514] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1474.835813] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1474.876970] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1476.027551] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1477.695325] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1478.827395] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1478.877422] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1480.791990] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1480.837582] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 1480.887557] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=dd06d0c0
[ 4223.575910] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4223.677941] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4396.225550] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4464.219862] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4486.336917] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4572.559109] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900
[ 4662.878221] TKIP: RX tkey->key_idx=2 frame keyidx=3 priv=ea852900



Sorry, not sure what to grep for...

---

### Post by herbig on 2010-04-20
The microphone works fine, also, when I do a video test, the light on the webcam turns on, it just doesn't show anything..

---

### Post by Linuxforall on 2010-04-20
If I am not mistaken, your cam is made by RICOH which is not natively supported by Linux yet but there is a driver for it which you can try at [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

---

### Post by herbig on 2010-04-20
It's a logitech c250, which was on the list for webcams that should just work with Ubuntu.  I've been messing around with it awhile, not sure what else to do.

---

### Post by Linuxforall on 2010-04-20
I don't see any mention of Logitech in your dmesg.

---

### Post by herbig on 2010-04-20
Ok, how would I get the drivers for that back to normal?  I wouldn't think that would have gotten messed up.  Are those part of xorg.conf?

---

### Post by Linuxforall on 2010-04-20
Are you sure you have a logitech webcam there?

---

### Post by herbig on 2010-04-20
So in messing around with Cheese, I can take picture/video and it will save the files and I'll appear, but it won't show it while it's happening.

---

### Post by herbig on 2010-04-20
Yeah I'm positive.  I bought it at Bestbuy a week ago specifically because I found it on a list of supported web cams.

---

### Post by herbig on 2010-04-20
I'm starting to feel like this is still a video card issue rather than a skype/webcam issue.  If I connect to someone on skype, they can see me fine, I just can't see them or me in the video window, all I see is gray.

---

### Post by herbig on 2010-04-20
SUCCESS!  Sorry for the quadruple post while I brainstorm, but I found a tutorial on how to roll back Intel drivers and got it working.  My intuition is that somehow it was still operating on nvidia drivers or settings or something, and that knocked it back?  In any case, it works, all's well.  Thank you kind sir.

---

### Post by Linuxforall on 2010-04-20
Hmm that sure looks like a video driver issue there, what did you do to xorg? Try sudo dpkg-reconfigure xserver-xorg

---

