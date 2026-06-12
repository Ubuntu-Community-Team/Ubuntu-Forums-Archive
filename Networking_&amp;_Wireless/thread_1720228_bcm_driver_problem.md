---
title: "bcm driver problem"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by cyclone731 on 2011-04-03
hey all i'm attempting to get injection working on my bcm4322 i followed all the steps and rechecked that i did everything correctly here "http://www.aircrack-ng.org/doku.php?id=b43". i first install the drivers with compat-wireless then the firmware with b43-fwcutter. 

the interface deosn't load on boot do to errors that i found with dmesg and when i try to activate it gives me this

 ```
cyclone@ubuntu-lt:~$ sudo ifconfig wlan1 up
SIOCSIFFLAGS: No such file or directory

```

here is what i think is needed to troubleshoot this issue if you need more let me know.

system specs
-dell studio 15
-model pp31l
-core 2 duo t6400 2Ghz
-4gigs ram

uname -r
```
2.6.32-30-generic

```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-30-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 (Ubuntu 2.6.32-30.59-generic 2.6.32.29+drm33.13)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bd4a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bd4a1000 - 00000000bd4a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bd4a7000 - 00000000bd5c2000 (usable)
[    0.000000]  BIOS-e820: 00000000bd5c2000 - 00000000bd60f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bd60f000 - 00000000bd709000 (usable)
[    0.000000]  BIOS-e820: 00000000bd709000 - 00000000bd90f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bd90f000 - 00000000bd919000 (usable)
[    0.000000]  BIOS-e820: 00000000bd919000 - 00000000bd91f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bd91f000 - 00000000bd963000 (usable)
[    0.000000]  BIOS-e820: 00000000bd963000 - 00000000bd99f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bd99f000 - 00000000bd9e4000 (usable)
[    0.000000]  BIOS-e820: 00000000bd9e4000 - 00000000bd9ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bd9ff000 - 00000000bda00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbda00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BE000000 mask FFE000000 uncachable
[    0.000000]   4 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   5 base 0BDE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bd4a1000 (usable)
[    0.000000]  modified: 00000000bd4a1000 - 00000000bd4a7000 (reserved)
[    0.000000]  modified: 00000000bd4a7000 - 00000000bd5c2000 (usable)
[    0.000000]  modified: 00000000bd5c2000 - 00000000bd60f000 (reserved)
[    0.000000]  modified: 00000000bd60f000 - 00000000bd709000 (usable)
[    0.000000]  modified: 00000000bd709000 - 00000000bd90f000 (reserved)
[    0.000000]  modified: 00000000bd90f000 - 00000000bd919000 (usable)
[    0.000000]  modified: 00000000bd919000 - 00000000bd91f000 (reserved)
[    0.000000]  modified: 00000000bd91f000 - 00000000bd963000 (usable)
[    0.000000]  modified: 00000000bd963000 - 00000000bd99f000 (ACPI NVS)
[    0.000000]  modified: 00000000bd99f000 - 00000000bd9e4000 (usable)
[    0.000000]  modified: 00000000bd9e4000 - 00000000bd9ff000 (ACPI data)
[    0.000000]  modified: 00000000bd9ff000 - 00000000bda00000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37852000 - 37fef6f2
[    0.000000] Allocated new RAMDISK: 008e6000 - 010836f2
[    0.000000] Move RAMDISK from 0000000037852000 - 0000000037fef6f1 to 008e6000 - 010836f1
[    0.000000] ACPI: RSDP 000f7900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bd9f7e43 0007C (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: FACP bd9e8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bd9e9000 06C8E (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS bd99efc0 00040
[    0.000000] ACPI: HPET bd9fed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bd9fed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bd9fed8a 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bd9fedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bd9fee1a 00176 (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bd9fef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bd9f7ee7 00039 (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bd9e7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bd9e6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bd9e5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2146MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00008e2000 - 00008e5168]              BRK ==> [00008e2000 - 00008e5168]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e6000 - 00010836f2]      NEW RAMDISK ==> [00008e6000 - 00010836f2]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f79b0] f79b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bda00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bd4a1
[    0.000000]     0: 0x000bd4a7 -> 0x000bd5c2
[    0.000000]     0: 0x000bd60f -> 0x000bd709
[    0.000000]     0: 0x000bd90f -> 0x000bd919
[    0.000000]     0: 0x000bd91f -> 0x000bd963
[    0.000000]     0: 0x000bd99f -> 0x000bd9e4
[    0.000000]     0: 0x000bd9ff -> 0x000bda00
[    0.000000] On node 0 totalpages: 775906
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1085000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3960 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4293 pages used for memmap
[    0.000000]   HighMem zone: 544391 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bda00000 (gap: bda00000:42600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 769837
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=a2c67228-7e6a-4e01-a504-41d8c4ee9a1c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15534080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bda00)
[    0.000000] Memory: 3046344k/3106816k available (4689k kernel code, 56356k reserved, 2122k data, 664k init, 2194736k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc0594467 - 0xc07a6f08   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0594467   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.791 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.58 BogoMIPS (lpj=7979164)
[    0.004020] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004045] Mount-cache hash table entries: 512
[    0.004161] Initializing cgroup subsys ns
[    0.004165] Initializing cgroup subsys cpuacct
[    0.004170] Initializing cgroup subsys memory
[    0.004176] Initializing cgroup subsys devices
[    0.004178] Initializing cgroup subsys freezer
[    0.004180] Initializing cgroup subsys net_cls
[    0.004200] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004203] CPU: L2 cache: 2048K
[    0.004206] CPU: Physical Processor ID: 0
[    0.004207] CPU: Processor Core ID: 0
[    0.004211] mce: CPU supports 6 MCE banks
[    0.004219] CPU0: Thermal monitoring enabled (TM2)
[    0.004222] using mwait in idle threads.
[    0.004229] Performance Events: Core2 events, Intel PMU driver.
[    0.004237] ... version:                2
[    0.004239] ... bit width:              40
[    0.004240] ... generic registers:      2
[    0.004242] ... value mask:             000000ffffffffff
[    0.004244] ... max period:             000000007fffffff
[    0.004246] ... fixed-purpose events:   3
[    0.004247] ... event mask:             0000000700000003
[    0.004253] Checking 'hlt' instruction... OK.
[    0.022885] ACPI: Core revision 20090903
[    0.036010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036015] ftrace: allocating 21799 entries in 43 pages
[    0.040056] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040422] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.081280] CPU0: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.168085] CPU1: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.168093] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172026] Brought up 2 CPUs
[    0.172029] Total of 2 processors activated (7979.54 BogoMIPS).
[    0.172556] CPU0 attaching sched-domain:
[    0.172560]  domain 0: span 0-1 level MC
[    0.172563]   groups: 0 1
[    0.172568] CPU1 attaching sched-domain:
[    0.172570]  domain 0: span 0-1 level MC
[    0.172572]   groups: 1 0
[    0.172631] devtmpfs: initialized
[    0.172631] regulator: core version 0.5
[    0.172631] Time: 20:58:52  Date: 04/02/11
[    0.172631] NET: Registered protocol family 16
[    0.172631] Trying to unpack rootfs image as initramfs...
[    0.172631] EISA bus registered
[    0.172631] ACPI: bus type pci registered
[    0.172631] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172631] PCI: Not using MMCONFIG.
[    0.172679] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=9
[    0.172681] PCI: Using configuration type 1 for base access
[    0.180087] bio: create slab <bio-0> at 0
[    0.181317] ACPI: EC: Look up EC in DSDT
[    0.182519] ACPI: BIOS _OSI(Linux) query ignored
[    0.184008] ACPI: Interpreter enabled
[    0.184008] ACPI: (supports S0 S3 S4 S5)
[    0.184008] ACPI: Using IOAPIC for interrupt routing
[    0.184008] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.188608] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.188608] PCI: Using MMCONFIG for extended config space
[    0.199719] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.199719] ACPI: No dock devices found.
[    0.199719] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.199719] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc3fffff]
[    0.199719] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.199719] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.199719] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc400000-0xfc4fffff]
[    0.199719] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.199719] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.199719] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.199719] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc904800-0xfc904bff]
[    0.199719] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1a.7: PME# disabled
[    0.199719] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc700000-0xfc703fff]
[    0.199719] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1b.0: PME# disabled
[    0.199719] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1c.0: PME# disabled
[    0.199719] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1c.1: PME# disabled
[    0.199719] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1c.3: PME# disabled
[    0.199719] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.199719] pci 0000:00:1c.5: PME# disabled
[    0.199719] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.200041] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.200145] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.200247] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc904c00-0xfc904fff]
[    0.200320] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.200325] pci 0000:00:1d.7: PME# disabled
[    0.200593] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.200601] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.200609] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.200618] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.200626] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.200635] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc904000-0xfc9047ff]
[    0.200687] pci 0000:00:1f.2: PME# supported from D3hot
[    0.200692] pci 0000:00:1f.2: PME# disabled
[    0.200736] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.200757] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.200847] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.200852] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.200861] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.201114] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8003fff]
[    0.201238] pci 0000:04:00.0: supports D1 D2
[    0.201240] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.201249] pci 0000:04:00.0: PME# disabled
[    0.201345] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.201350] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.201359] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.201421] pci 0000:00:1c.3: bridge io port: [0x4000-0x4fff]
[    0.201427] pci 0000:00:1c.3: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.201435] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.201701] pci 0000:08:00.0: reg 10 64bit mmio: [0xfc500000-0xfc50ffff]
[    0.201842] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.201850] pci 0000:08:00.0: PME# disabled
[    0.201937] pci 0000:00:1c.5: bridge 32bit mmio: [0xfc500000-0xfc5fffff]
[    0.201993] pci 0000:09:01.0: reg 10 32bit mmio: [0xfc600000-0xfc6007ff]
[    0.202061] pci 0000:09:01.0: supports D1 D2
[    0.202063] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202069] pci 0000:09:01.0: PME# disabled
[    0.202117] pci 0000:09:01.1: reg 10 32bit mmio: [0xfc600800-0xfc6008ff]
[    0.202185] pci 0000:09:01.1: supports D1 D2
[    0.202187] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202193] pci 0000:09:01.1: PME# disabled
[    0.202241] pci 0000:09:01.2: reg 10 32bit mmio: [0xfc600c00-0xfc600cff]
[    0.202308] pci 0000:09:01.2: supports D1 D2
[    0.202310] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202316] pci 0000:09:01.2: PME# disabled
[    0.202364] pci 0000:09:01.3: reg 10 32bit mmio: [0xfc601000-0xfc6010ff]
[    0.202433] pci 0000:09:01.3: supports D1 D2
[    0.202435] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202440] pci 0000:09:01.3: PME# disabled
[    0.202512] pci 0000:00:1e.0: transparent bridge
[    0.202521] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc600000-0xfc6fffff]
[    0.202561] pci_bus 0000:00: on NUMA node 0
[    0.202568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.202718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.202822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.202897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.202970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.203031] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.216457] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.216566] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.216672] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.216775] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.216879] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.216984] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.217087] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.217194] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.217308] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217325] vgaarb: loaded
[    0.217449] SCSI subsystem initialized
[    0.219970] libata version 3.00 loaded.
[    0.220011] usbcore: registered new interface driver usbfs
[    0.220011] usbcore: registered new interface driver hub
[    0.220011] usbcore: registered new device driver usb
[    0.220011] ACPI: WMI: Mapper loaded
[    0.220011] PCI: Using ACPI for IRQ routing
[    0.220011] NetLabel: Initializing
[    0.220011] NetLabel:  domain hash size = 128
[    0.220011] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.220011] NetLabel:  unlabeled traffic allowed by default
[    0.220011] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.220011] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.224183] Switching to clocksource tsc
[    0.226788] AppArmor: AppArmor Filesystem Enabled
[    0.226788] pnp: PnP ACPI init
[    0.226788] ACPI: bus type pnp registered
[    0.228757] pnp: PnP ACPI: found 10 devices
[    0.228760] ACPI: ACPI bus type pnp unregistered
[    0.228764] PnPBIOS: Disabled by ACPI PNP
[    0.228777] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.228784] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.228787] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.228790] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.228792] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.228795] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.228798] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.228801] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.228803] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.228806] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.228809] system 00:04: ioport range 0x900-0x97f has been reserved
[    0.228816] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.228819] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.228822] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.228825] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.228828] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.228831] system 00:09: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.228834] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.228837] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.228840] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.263616] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.263621] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.263628] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.263633] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.263642] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.263646] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.263652] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.263658] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.263666] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.263669] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.263676] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfbffffff
[    0.263689] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.263697] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.263701] pci 0000:00:1c.5:   IO window: 0x5000-0x5fff
[    0.263707] pci 0000:00:1c.5:   MEM window: 0xfc500000-0xfc5fffff
[    0.263713] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0000000-0x000000c01fffff
[    0.263722] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.263724] pci 0000:00:1e.0:   IO window: disabled
[    0.263730] pci 0000:00:1e.0:   MEM window: 0xfc600000-0xfc6fffff
[    0.263735] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.263758]   alloc irq_desc for 17 on node -1
[    0.263761]   alloc kstat_irqs on node -1
[    0.263768] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.263774] pci 0000:00:1c.0: setting latency timer to 64
[    0.263785]   alloc irq_desc for 16 on node -1
[    0.263786]   alloc kstat_irqs on node -1
[    0.263790] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.263795] pci 0000:00:1c.1: setting latency timer to 64
[    0.263806]   alloc irq_desc for 19 on node -1
[    0.263808]   alloc kstat_irqs on node -1
[    0.263811] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.263816] pci 0000:00:1c.3: setting latency timer to 64
[    0.263827] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.263832] pci 0000:00:1c.5: setting latency timer to 64
[    0.263840] pci 0000:00:1e.0: setting latency timer to 64
[    0.263845] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.263848] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.263851] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.263853] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.263856] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.263858] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.263860] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.263863] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.263866] pci_bus 0000:06: resource 0 io:  [0x4000-0x4fff]
[    0.263868] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.263870] pci_bus 0000:06: resource 2 pref mem [0xf4000000-0xf5ffffff]
[    0.263873] pci_bus 0000:08: resource 0 io:  [0x5000-0x5fff]
[    0.263875] pci_bus 0000:08: resource 1 mem: [0xfc500000-0xfc5fffff]
[    0.263878] pci_bus 0000:08: resource 2 pref mem [0xc0000000-0xc01fffff]
[    0.263880] pci_bus 0000:09: resource 1 mem: [0xfc600000-0xfc6fffff]
[    0.263883] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.263885] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.263929] NET: Registered protocol family 2
[    0.264029] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264353] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.264821] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.265039] TCP: Hash tables configured (established 131072 bind 65536)
[    0.265042] TCP reno registered
[    0.265138] NET: Registered protocol family 1
[    0.265162] pci 0000:00:02.0: Boot video device
[    0.265350] Simple Boot Flag at 0x36 set to 0x1
[    0.265521] cpufreq-nforce2: No nForce2 chipset.
[    0.265550] Scanning for low memory corruption every 60 seconds
[    0.265667] audit: initializing netlink socket (disabled)
[    0.265676] type=2000 audit(1301777931.265:1): initialized
[    0.275764] highmem bounce pool size: 64 pages
[    0.275769] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.277328] VFS: Disk quotas dquot_6.5.2
[    0.277389] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.277970] fuse init (API version 7.13)
[    0.278055] msgmni has been set to 1665
[    0.278260] alg: No test for stdrng (krng)
[    0.278313] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.278316] io scheduler noop registered
[    0.278318] io scheduler anticipatory registered
[    0.278320] io scheduler deadline registered
[    0.278362] io scheduler cfq registered (default)
[    0.278538]   alloc irq_desc for 24 on node -1
[    0.278540]   alloc kstat_irqs on node -1
[    0.278552] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.278564] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.278728]   alloc irq_desc for 25 on node -1
[    0.278730]   alloc kstat_irqs on node -1
[    0.278739] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.278750] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.278907]   alloc irq_desc for 26 on node -1
[    0.278909]   alloc kstat_irqs on node -1
[    0.278917] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.278929] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.279088]   alloc irq_desc for 27 on node -1
[    0.279090]   alloc kstat_irqs on node -1
[    0.279099] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.279110] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.279214] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.279360] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.372658] Freeing initrd memory: 7797k freed
[    0.383798] ACPI: AC Adapter [ADP1] (off-line)
[    0.383890] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.383894] ACPI: Power Button [PWRB]
[    0.383938] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.383940] ACPI: Sleep Button [SLPB]
[    0.383981] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.384762] ACPI: Lid Switch [LID0]
[    0.384810] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.384812] ACPI: Power Button [PWRF]
[    0.385642] ACPI: SSDT bd91aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.386175] ACPI: SSDT bd919620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.388445] Monitor-Mwait will be used to enter C-1 state
[    0.388476] Monitor-Mwait will be used to enter C-2 state
[    0.388498] Monitor-Mwait will be used to enter C-3 state
[    0.388504] Marking TSC unstable due to TSC halts in idle
[    0.388555] processor LNXCPU:00: registered as cooling_device0
[    0.388997] ACPI: SSDT bd91aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.389413] ACPI: SSDT bd91af20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.390413] Switching to clocksource hpet
[    0.390483] processor LNXCPU:01: registered as cooling_device1
[    0.395062] thermal LNXTHERM:01: registered as thermal_zone0
[    0.395070] ACPI: Thermal Zone [TZ00] (53 C)
[    0.401192] thermal LNXTHERM:02: registered as thermal_zone1
[    0.401202] ACPI: Thermal Zone [TZ01] (42 C)
[    0.402841] thermal LNXTHERM:03: registered as thermal_zone2
[    0.402849] ACPI: Thermal Zone [TZ02] (0 C)
[    0.402954] isapnp: Scanning for PnP cards...
[    0.411002] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.412380] brd: module loaded
[    0.412954] loop: module loaded
[    0.413054] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.413556] Fixed MDIO Bus: probed
[    0.413639] PPP generic driver version 2.4.2
[    0.413667] tun: Universal TUN/TAP device driver, 1.6
[    0.413669] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.413793] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.413825] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.413855] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.413859] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.413890] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.413928] ehci_hcd 0000:00:1a.7: debug port 1
[    0.417809] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.417857] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc904800
[    0.433074] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.433152] usb usb1: configuration #1 chosen from 1 choice
[    0.433182] hub 1-0:1.0: USB hub found
[    0.433189] hub 1-0:1.0: 6 ports detected
[    0.433378]   alloc irq_desc for 23 on node -1
[    0.433380]   alloc kstat_irqs on node -1
[    0.433386] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.433396] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.433400] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.433431] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.433465] ehci_hcd 0000:00:1d.7: debug port 1
[    0.437341] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.437367] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc904c00
[    0.445266] ACPI: Battery Slot [BAT0] (battery present)
[    0.453021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.453090] usb usb2: configuration #1 chosen from 1 choice
[    0.453153] hub 2-0:1.0: USB hub found
[    0.453160] hub 2-0:1.0: 6 ports detected
[    0.453218] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.453233] uhci_hcd: USB Universal Host Controller Interface driver
[    0.453253] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.453260] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.453263] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.453294] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.453327] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.453414] usb usb3: configuration #1 chosen from 1 choice
[    0.453439] hub 3-0:1.0: USB hub found
[    0.453445] hub 3-0:1.0: 2 ports detected
[    0.453491]   alloc irq_desc for 21 on node -1
[    0.453493]   alloc kstat_irqs on node -1
[    0.453497] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.453503] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.453507] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.453536] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.453615] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.453707] usb usb4: configuration #1 chosen from 1 choice
[    0.453732] hub 4-0:1.0: USB hub found
[    0.453738] hub 4-0:1.0: 2 ports detected
[    0.453783] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.453790] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.453793] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.453824] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.453851] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.453984] usb usb5: configuration #1 chosen from 1 choice
[    0.454021] hub 5-0:1.0: USB hub found
[    0.454027] hub 5-0:1.0: 2 ports detected
[    0.454073] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.454080] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.454083] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.454115] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.454182] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.454320] usb usb6: configuration #1 chosen from 1 choice
[    0.454349] hub 6-0:1.0: USB hub found
[    0.454355] hub 6-0:1.0: 2 ports detected
[    0.454410] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.454416] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.454420] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.454455] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.454483] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.454625] usb usb7: configuration #1 chosen from 1 choice
[    0.454650] hub 7-0:1.0: USB hub found
[    0.454657] hub 7-0:1.0: 2 ports detected
[    0.454704]   alloc irq_desc for 18 on node -1
[    0.454706]   alloc kstat_irqs on node -1
[    0.454710] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.454721] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.454726] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.454796] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.454835] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.454921] usb usb8: configuration #1 chosen from 1 choice
[    0.454946] hub 8-0:1.0: USB hub found
[    0.454952] hub 8-0:1.0: 2 ports detected
[    0.455046] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.467112] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.467128] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.467243] mice: PS/2 mouse device common for all mice
[    0.467398] rtc_cmos 00:06: RTC can wake from S4
[    0.467433] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.467464] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.467557] device-mapper: uevent: version 1.0.3
[    0.467655] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.467720] device-mapper: multipath: version 1.1.0 loaded
[    0.467722] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.467863] EISA: Probing bus 0 at eisa.0
[    0.467869] Cannot allocate resource for EISA slot 1
[    0.467871] Cannot allocate resource for EISA slot 2
[    0.467873] Cannot allocate resource for EISA slot 3
[    0.467875] Cannot allocate resource for EISA slot 4
[    0.467877] Cannot allocate resource for EISA slot 5
[    0.467892] EISA: Detected 0 cards.
[    0.468026] cpuidle: using governor ladder
[    0.468139] cpuidle: using governor menu
[    0.468552] TCP cubic registered
[    0.468702] NET: Registered protocol family 10
[    0.469215] lo: Disabled Privacy Extensions
[    0.469555] NET: Registered protocol family 17
[    0.470202] Using IPI No-Shortcut mode
[    0.470268] PM: Resume from disk failed.
[    0.470279] registered taskstats version 1
[    0.471233]   Magic number: 7:700:1002
[    0.471257] system 00:04: hash matches
[    0.471306] rtc_cmos 00:06: setting system clock to 2011-04-02 20:58:52 UTC (1301777932)
[    0.471309] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.471311] EDD information not available.
[    0.478523] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.749031] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    0.757940] isapnp: No Plug & Play device found
[    0.757983] Freeing unused kernel memory: 664k freed
[    0.758356] Write protecting the kernel text: 4692k
[    0.758407] Write protecting the kernel read-only data: 1844k
[    0.774550] udev: starting version 151
[    0.882220] tg3.c:v3.102 (September 1, 2009)
[    0.882348] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.882361] tg3 0000:08:00.0: setting latency timer to 64
[    0.888354] ahci 0000:00:1f.2: version 3.0
[    0.888368] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.888413]   alloc irq_desc for 28 on node -1
[    0.888415]   alloc kstat_irqs on node -1
[    0.888426] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.888510] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.888514] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ccc sxs 
[    0.888519] ahci 0000:00:1f.2: setting latency timer to 64
[    0.888787] scsi0 : ahci
[    0.888966] scsi1 : ahci
[    0.889589] scsi2 : ahci
[    0.889692] scsi3 : ahci
[    0.889789] scsi4 : ahci
[    0.889890] scsi5 : ahci
[    0.889940] ata1: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904100 irq 28
[    0.889944] ata2: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904180 irq 28
[    0.889946] ata3: DUMMY
[    0.889948] ata4: DUMMY
[    0.889951] ata5: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904300 irq 28
[    0.889954] ata6: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904380 irq 28
[    0.891006] usb 1-6: configuration #1 chosen from 1 choice
[    1.209139] ata5: SATA link down (SStatus 0 SControl 300)
[    1.212127] ata6: SATA link down (SStatus 0 SControl 300)
[    1.372109] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.373233] ata1.00: ATA-8: Hitachi HTS543232L9A300, FB4OC40C, max UDMA/133
[    1.373239] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.374600] ata1.00: configured for UDMA/133
[    1.376046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.388385] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4O PQ: 0 ANSI: 5
[    1.388531] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.388611] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.388657] sd 0:0:0:0: [sda] Write Protect is off
[    1.388660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.388684] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.388812]  sda:
[    1.390099] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, DW20, max UDMA/100
[    1.390125] ata2.00: applying bridge limits
[    1.403950] ata2.00: configured for UDMA/100
[    1.409644]  sda1 sda2 sda3 <
[    1.414459] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:21:70:8f:93:f0
[    1.414463] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.414465] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.414468] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.420980]  sda5
[    1.422396] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A DW20 PQ: 0 ANSI: 5
[    1.426784] sr0: scsi3-mmc drive: 20x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.426789] Uniform CD-ROM driver Revision: 3.20
[    1.426927] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.426995] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.440231]  sda6 sda7 > sda4
[    1.461351] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.463810] Compat-wireless backport release: compat-wireless-2011-03-30-1-g7b4debf
[    1.463813] Backport based on linux-next.git next-20110331
[    1.476253] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.476267] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[    1.478894] ohci1394 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.496219] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x17, vendor 0x4243)
[    1.496232] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x10, vendor 0x4243)
[    1.496244] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x0B, vendor 0x4243)
[    1.496255] ssb: Core 3 found: PCI (cc 0x804, rev 0x0E, vendor 0x4243)
[    1.496267] ssb: Core 4 found: USB 2.0 Device (cc 0x81A, rev 0x05, vendor 0x4243)
[    1.496278] ssb: Core 5 found: UNKNOWN (cc 0x8FF, rev 0x00, vendor 0x4243)
[    1.496290] ssb: Core 6 found: Internal Memory (cc 0x80E, rev 0x03, vendor 0x4243)
[    1.535071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc600000-fc6007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.544300] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[    2.162352] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.809378] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[   12.600767] udev: starting version 151
[   12.602463] Adding 2039800k swap on /dev/sda7.  Priority:-1 extents:1 across:2039800k 
[   12.639110] lp: driver loaded but no devices found
[   12.839189] sdhci: Secure Digital Host Controller Interface driver
[   12.839191] sdhci: Copyright(c) Pierre Ossman
[   12.841252] Linux agpgart interface v0.103
[   12.842228] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.848996] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   12.849037] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   12.854788] Registered led device: mmc0::
[   12.872937] type=1505 audit(1301795944.896:2):  operation="profile_load" pid=572 name="/sbin/dhclient3"
[   12.873678] type=1505 audit(1301795944.901:3):  operation="profile_load" pid=572 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.874074] type=1505 audit(1301795944.901:4):  operation="profile_load" pid=572 name="/usr/lib/connman/scripts/dhclient-script"
[   12.874213] Linux video capture interface: v2.00
[   12.876914] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   12.877686] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   12.877915] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:18a0)
[   12.896895] input: Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
[   12.896952] usbcore: registered new interface driver uvcvideo
[   12.896954] USB Video Class driver (v0.1.0)
[   12.911084] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   12.947287] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   13.017504] cfg80211: Calling CRDA to update world regulatory domain
[   13.023711] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   13.024431] [drm] Initialized drm 1.1.0 20060810
[   13.056961] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.056966] i915 0000:00:02.0: setting latency timer to 64
[   13.063957]   alloc irq_desc for 29 on node -1
[   13.063960]   alloc kstat_irqs on node -1
[   13.063969] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[   13.063977] [drm] set up 31M of stolen space
[   13.272910] b43-phy0: f3c65db0
[   13.343662] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.343666] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343668] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.343671] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343673] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.343676] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343678] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.343681] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343683] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.343686] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343688] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.343691] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343693] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.343696] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343698] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.343701] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343703] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.343706] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343708] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.343710] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343713] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.343715] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343718] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.343720] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343722] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.343725] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.343727] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.343730] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   13.447174] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   13.471178] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   13.654239] fb0: inteldrmfb frame buffer device
[   13.654242] registered panic notifier
[   13.656095] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[   13.656167] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.656220] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.656264]   alloc irq_desc for 22 on node -1
[   13.656266]   alloc kstat_irqs on node -1
[   13.656272] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.656312] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.658516] vga16fb: initializing
[   13.658521] vga16fb: mapped to 0xc00a0000
[   13.658524] vga16fb: not registering due to another framebuffer present
[   13.708196] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.708938] Registered led device: b43-phy0::tx
[   13.708956] Registered led device: b43-phy0::rx
[   13.708972] Registered led device: b43-phy0::radio
[   13.708990] Broadcom 43xx driver loaded [ Features: PMNLS, Firmware-ID: FW13 ]
[   13.715121] udev: renamed network interface wlan0 to wlan1
[   13.730047] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.730051] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730053] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.730055] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730057] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.730059] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730061] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.730064] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730066] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.730068] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730070] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.730072] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730074] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.730077] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730078] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.730081] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730083] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.730085] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730087] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.730089] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730091] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.730093] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730095] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.730097] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730099] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.730102] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730104] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.730106] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   13.730108] cfg80211: World regulatory domain updated:
[   13.730110] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.730112] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.730115] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.730117] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.730119] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.730121] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.772367] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   13.793289] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.793378] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.793436] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   13.909129] Console: switching to colour frame buffer device 180x56
[   14.195224] type=1505 audit(1301795946.221:5):  operation="profile_replace" pid=907 name="/sbin/dhclient3"
[   14.195951] type=1505 audit(1301795946.221:6):  operation="profile_replace" pid=907 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.196375] type=1505 audit(1301795946.221:7):  operation="profile_replace" pid=907 name="/usr/lib/connman/scripts/dhclient-script"
[   14.198050] type=1505 audit(1301795946.225:8):  operation="profile_load" pid=906 name="/usr/share/gdm/guest-session/Xsession"
[   14.202644] type=1505 audit(1301795946.229:9):  operation="profile_load" pid=911 name="/usr/lib/cups/backend/cups-pdf"
[   14.203506] type=1505 audit(1301795946.229:10):  operation="profile_load" pid=911 name="/usr/sbin/cupsd"
[   14.206787] type=1505 audit(1301795946.233:11):  operation="profile_load" pid=912 name="/usr/sbin/tcpdump"
[   15.170782] ppdev: user-space parallel port driver
[   15.198257] b43-phy0 ERROR: f3c85ad0
[   15.198261] b43-phy0 ERROR: f3c85ad0
[   15.198263] b43-phy0 ERROR: f3c859e8
[   15.200093]   alloc irq_desc for 30 on node -1
[   15.200097]   alloc kstat_irqs on node -1
[   15.200120] tg3 0000:08:00.0: irq 30 for MSI/MSI-X
[   15.317494] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.668743] b43-phy0 ERROR: f2c53da8
[   15.668747] b43-phy0 ERROR: f2c53da8
[   15.668750] b43-phy0 ERROR: f2c53cc0
[   16.081042] b43-phy0 ERROR: f3c7dda8
[   16.081047] b43-phy0 ERROR: f3c7dda8
[   16.081049] b43-phy0 ERROR: f3c7dcc0
[   16.903372] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   16.903376] tg3: eth0: Flow control is off for TX and off for RX.
[   16.903560] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.517801] ISO 9660 Extensions: Microsoft Joliet Level 3
[   23.530447] ISOFS: changing to secondary root
[   27.220088] eth0: no IPv6 routers present
[  107.101157] lo: Disabled Privacy Extensions
[  184.301134] CE: hpet increasing min_delta_ns to 15000 nsec
[  198.301063] CE: hpet increasing min_delta_ns to 22500 nsec
[  202.551151] b43-phy0 ERROR: f20a5da8
[  202.551158] b43-phy0 ERROR: f20a5da8
[  202.551162] b43-phy0 ERROR: f20a5cc0
[  655.378171] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  655.379438] SGI XFS Quota Management subsystem
[  655.387843] JFS: nTxBlock = 8192, nTxLock = 65536
[  655.410934] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  655.434926] QNX4 filesystem 0.2.3 registered.
[  655.488616] Btrfs loaded
[  691.311021] b43-phy0 ERROR: f2143da8
[  691.311026] b43-phy0 ERROR: f2143da8
[  691.311029] b43-phy0 ERROR: f2143cc0
[  703.329869] b43-phy0 ERROR: f2145da8
[  703.329875] b43-phy0 ERROR: f2145da8
[  703.329881] b43-phy0 ERROR: f2145cc0
[ 1007.691494] b43-phy0 ERROR: f435bda8
[ 1007.691501] b43-phy0 ERROR: f435bda8
[ 1007.691505] b43-phy0 ERROR: f435bcc0
[ 1187.673661] b43-pci-bridge 0000:04:00.0: PCI INT A disabled
[ 1207.681217] Compat-wireless backport release: compat-wireless-2011-03-30-1-g7b4debf
[ 1207.681222] Backport based on linux-next.git next-20110331
[ 1207.697990] cfg80211: Calling CRDA to update world regulatory domain
[ 1207.709380] cfg80211: World regulatory domain updated:
[ 1207.709384] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1207.709387] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1207.709390] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1207.709392] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1207.709395] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1207.709398] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1207.730794] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1207.730811] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[ 1207.748538] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x17, vendor 0x4243)
[ 1207.748555] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x10, vendor 0x4243)
[ 1207.748570] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x0B, vendor 0x4243)
[ 1207.748583] ssb: Core 3 found: PCI (cc 0x804, rev 0x0E, vendor 0x4243)
[ 1207.748597] ssb: Core 4 found: USB 2.0 Device (cc 0x81A, rev 0x05, vendor 0x4243)
[ 1207.748611] ssb: Core 5 found: UNKNOWN (cc 0x8FF, rev 0x00, vendor 0x4243)
[ 1207.748625] ssb: Core 6 found: Internal Memory (cc 0x80E, rev 0x03, vendor 0x4243)
[ 1207.796496] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
[ 1207.811650] b43-phy0: f4a29db0
[ 1207.876473] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876479] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876484] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876488] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876492] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876497] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876501] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876506] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876509] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876514] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876518] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876522] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876526] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876531] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876535] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876539] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876543] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876548] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876552] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876556] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876560] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876565] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876569] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876573] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876577] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876582] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876586] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1207.876590] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 1207.876852] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 1207.880654] Registered led device: b43-phy0::tx
[ 1207.880687] Registered led device: b43-phy0::rx
[ 1207.880716] Registered led device: b43-phy0::radio
[ 1207.880744] Broadcom 43xx driver loaded [ Features: PMNLS, Firmware-ID: FW13 ]
[ 1207.891268] udev: renamed network interface wlan0 to wlan1
[ 1207.947235] b43-phy0 ERROR: f3c85ad0
[ 1207.947241] b43-phy0 ERROR: f3c85ad0
[ 1207.947244] b43-phy0 ERROR: f3c859e8
[ 1207.982477] b43-phy0 ERROR: f2c53da8
[ 1207.982483] b43-phy0 ERROR: f2c53da8
[ 1207.982487] b43-phy0 ERROR: f2c53cc0


```


lspci -vnn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at fc000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, fast devsel, latency 0
	Memory at fc400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fc904800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fc500000-fc5fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc904c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: fc600000-fc6fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fc904000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Dell Device [1028:02a0]
	Flags: medium devsel, IRQ 10
	Memory at c0200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Dell Device [1028:000d]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at fc500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

09:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fc600000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

09:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fc600800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at fc600c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Dell Device [1028:02a0]
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at fc601000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:21:70:8f:93:f0  
          inet addr:192.168.1.44  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe8f:93f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2482999 (2.4 MB)  TX bytes:452176 (452.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7437 (7.4 KB)  TX bytes:7437 (7.4 KB)


```

---

### Post by bkratz on 2011-04-03
Have you ever had wireless with the b43 driver you are trying?  According to the table on this page

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Your card is not supported by that driver and needs the STA driver (which will not work with aircrack)

---

### Post by cyclone731 on 2011-04-03
this is my first attempt to use the b43 driver. i was using the STA driver and everything worked fine with it. i switched for the rfmon monitor mode/injection capability.

i also reviewed that table beforehand and my card *is* supported (my PCI-ID: 14e4:432b) but now i noticed as i look closer.. "partially in 2.6.39+" whereas my kernel is 2.6.32-30-generic. could this be the issue?

---

### Post by vlaar on 2011-04-03
> **cyclone731 said:**
> i also reviewed that table beforehand and my card *is* supported (my PCI-ID: 14e4:432b) but now i noticed as i look closer.. "partially in 2.6.39+" whereas my kernel is 2.6.32-30-generic. could this be the issue?

That's highly unlikely. You could check if the b43 is properly loading, cause "SIOCSIFFLAGS: No such file or directory" usually means the firmware isn't found. Looking at your dmesg log, it looks like somethings wrong with the firmware.

I advice you to reinstall the firmware using link below as a reference
[http://wireless.kernel.org/en/users/Drivers/b43#Supported_chip_types](http://wireless.kernel.org/en/users/Drivers/b43#Supported_chip_types)

---

### Post by bkratz on 2011-04-03
Even in the link supplied by the last poster it says


BCM4322 (experimental in 2.6.38, kernel 2.6.39 suggested)


So if you are back at kernel 32, I would not expect much.

---

### Post by cyclone731 on 2011-04-10
i tried reinstalling the firmware with b43-fwcutter and bbroadcom-wl-4.150.10.5.tar.bz2 and wl_apsta-3.130.20.0.o ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)), again without any luck i'm going to try updrading the kernel to 2.6.39 rc2 but im at a loss at how to do it. i searched ubuntu docs but havne't found anything. i found some compiling from source tuts and installing headers with another one, just not sure which one to do.

here is also my lsmod output.  i was wondering if any other modules where conflicting, like ssb?

```
cyclone@ubuntu-lt:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
arc4                    1153  2 
b43                   308320  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      52010  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
mac80211              252009  1 b43
snd_hda_intel          22037  1 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
joydev                  8740  0 
cfg80211              151706  2 b43,mac80211
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
i915                  287458  3 
drm_kms_helper         29329  1 i915
ses                     5875  0 
enclosure               6624  1 ses
snd                    54180  15 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop             6888  0 
compat_firmware_class     6200  1 b43
uvcvideo               57310  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162345  4 i915,drm_kms_helper
dcdbas                  5422  1 dell_laptop
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
ssb                    45829  1 b43
ohci1394               26950  0 
pcmcia                 30784  2 b43,ssb
usb_storage            39841  2 
compat                  8257  4 b43,mac80211,cfg80211,ssb
ieee1394               81181  1 ohci1394
ahci                   32200  2 
tg3                   109324  0 
led_class               2864  3 b43,sdhci,compat
pcmcia_core            32964  2 pcmcia,compat


```


UPDATE:
i found this newer driver from broadcom, hybrid-portsrc_x86_32-v5_100_82_38.tar ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) i haven't tried it but could that work?

---

### Post by bkratz on 2011-04-10
Quote

i'm going to try updrading the kernel to 2.6.39 rc2 but im at a loss at how to do it. i searched ubuntu docs but havne't found anything. i found some compiling from source tuts and installing headers with another one, just not sure which one to do.

UPDATE:
i found this newer driver from broadcom, hybrid-portsrc_x86_32-v5_100_82_38.tar ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) i haven't tried it but could that work?







The driver you found is the standard STA driver from Broadcom which does not work with aircrack.  Here is a thread where the user updated his kernel. Please note that this was for an old kernel but I suspect you could transfer this knowledge to the correct kernel (the method would be the same). [COLOR="Red"]Make sure that you back up everything important you are "messing" with the most important parts.[/COLOR]

The instructions
[http://ubuntuforums.org/showpost.php?p=8912349&postcount=15](http://ubuntuforums.org/showpost.php?p=8912349&postcount=15)

the kernels
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

release candidate 2 doesn't seem to have all the required deb files in the location above, but release candidate 1 does.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/)


I used the same methodology once before and had no problems--but backup everything first. Look at the documentation and if you feel overwhelmed think twice!

---

### Post by AnotherPenguin on 2011-09-21
If your internet still isn't working use this page: [http://ubuntuforums.org/showthread.php?t=1846959&highlight=broadcom&page=3](http://ubuntuforums.org/showthread.php?t=1846959&highlight=broadcom&page=3)
Then scroll down to garvinrick4's message. Once you download the driver activate the STA in your additional drivers application. After that just restart.

---

