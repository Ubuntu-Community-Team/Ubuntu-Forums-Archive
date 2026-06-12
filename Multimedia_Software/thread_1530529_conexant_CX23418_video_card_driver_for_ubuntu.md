---
title: "conexant CX23418 video card driver for ubuntu"
date: 2010-07-13
forum: Multimedia Software
---

### Post by abdulq8 on 2010-07-13
Hi guys. I am new here and I need help with my Toshiba Qosmio G-30 laptop. Two days ago I was using windows 7, but unfortunately it was messed up for unknown reason. I installed Ubuntu 10.04 desktop edition but I have a problem with the video card which conexant CX23418, and I got that from
 ```
sudo lshw
```
I need driver for that ASAP
thanks a lot
abdul

---

### Post by Yellow Pasque on 2010-07-13
It uses the cx18 kernel module, but it's still beta quality. For the latest: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

---

### Post by abdulq8 on 2010-07-14
Thanks a lot 
I will try it

---

### Post by saedelaere on 2010-07-16
And with [TV-Viewer]("http://tv-viewer.sourceforge.net/") you should be able to watch analog TV. 

Regards

---

### Post by abdulq8 on 2010-08-16
> **Temüjin said:**
> It uses the cx18 kernel module, but it's still beta quality. For the latest: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

it didn't work for me 
Anyone has another idea?

---

### Post by saedelaere on 2010-08-17
Sure tell us what does not work for you.

Post the output of

```
dmesg | grep cx18
```

---

### Post by abdulq8 on 2010-08-17
> **saedelaere said:**
> Sure tell us what does not work for you.

Post the output of

```
dmesg | grep cx18
```

I tried the code but it doesn't work
I have a problem with the display
this is the screen image for the problem
[http://www.flickr.com/photos/53083724@N04/4898127899/](http://www.flickr.com/photos/53083724@N04/4898127899/) 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff80000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec28000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF uncachable
[    0.000000]   D4000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FEDA0000 mask FFFFE0000 write-back
[    0.000000]   1 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  modified: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  modified: 000000007ff70000 - 000000007ff80000 (ACPI data)
[    0.000000]  modified: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec28000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef9bc
[    0.000000] Allocated new RAMDISK: 008e0000 - 010789bc
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef9bb to 008e0000 - 010789bb
[    0.000000] ACPI: RSDP 000f0180 00014 (v00 TOSHIB)
[    0.000000] ACPI: RSDT 7ff70000 0004C (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: FACP 7ff70074 00084 (v02 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: DSDT 7ff700f8 05179 (v01 TOSHIB A0037    20060706 MSFT 0100000E)
[    0.000000] ACPI: FACS 000eee00 00040
[    0.000000] ACPI: SSDT 7ff75271 00306 (v01 TOSHIB A0037    20050926 MSFT 0100000E)
[    0.000000] ACPI: DBGP 7ff75d88 00034 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: BOOT 7ff7004c 00028 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: APIC 7ff75ce4 00068 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: MCFG 7ff75d4c 0003C (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: HPET 7ff75f1c 00038 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: SSDT 7ff75f54 005E1 (v01 TOSHIB A0037    20050523 MSFT 0100000E)
[    0.000000] ACPI: SSDT 7ff75e6c 000B0 (v01 TOSHIB A0037    20051014 MSFT 0100000E)
[    0.000000] ACPI: SSDT 7ff77078 00076 (v01 TOSHIB A0037    20051021 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df21c]              BRK ==> [00008dc000 - 00008df21c]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 00010789bc]      NEW RAMDISK ==> [00008e0000 - 00010789bc]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007ff70
[    0.000000] On node 0 totalpages: 524042
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c107a000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2319 pages used for memmap
[    0.000000]   HighMem zone: 294499 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
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
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519947
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b09743c7-e1e5-4c10-92ad-371721a1a6ce ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10482880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ff70)
[    0.000000] Memory: 2051652k/2096576k available (4679k kernel code, 43448k reserved, 2116k data, 660k init, 1187272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.830 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.66 BogoMIPS (lpj=9311320)
[    0.004021] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004047] Mount-cache hash table entries: 512
[    0.004172] Initializing cgroup subsys ns
[    0.004176] Initializing cgroup subsys cpuacct
[    0.004180] Initializing cgroup subsys memory
[    0.004187] Initializing cgroup subsys devices
[    0.004190] Initializing cgroup subsys freezer
[    0.004192] Initializing cgroup subsys net_cls
[    0.004211] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004214] CPU: L2 cache: 4096K
[    0.004217] CPU: Physical Processor ID: 0
[    0.004219] CPU: Processor Core ID: 0
[    0.004222] mce: CPU supports 6 MCE banks
[    0.004230] CPU0: Thermal monitoring handled by SMI
[    0.004234] using mwait in idle threads.
[    0.004241] Performance Events: Core2 events, Intel PMU driver.
[    0.004249] ... version:                2
[    0.004251] ... bit width:              40
[    0.004252] ... generic registers:      2
[    0.004254] ... value mask:             000000ffffffffff
[    0.004256] ... max period:             000000007fffffff
[    0.004257] ... fixed-purpose events:   3
[    0.004259] ... event mask:             0000000700000003
[    0.004263] Checking 'hlt' instruction... OK.
[    0.022465] ACPI: Core revision 20090903
[    0.030278] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030284] ftrace: allocating 21780 entries in 43 pages
[    0.032054] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032366] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075373] CPU0: Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz stepping 06
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 4096K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.160054] CPU1: Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz stepping 06
[    0.160065] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164018] Brought up 2 CPUs
[    0.164021] Total of 2 processors activated (9310.75 BogoMIPS).
[    0.164626] CPU0 attaching sched-domain:
[    0.164629]  domain 0: span 0-1 level MC
[    0.164631]   groups: 0 1
[    0.164637] CPU1 attaching sched-domain:
[    0.164639]  domain 0: span 0-1 level MC
[    0.164641]   groups: 1 0
[    0.164738] devtmpfs: initialized
[    0.164738] regulator: core version 0.5
[    0.164738] Time: 15:53:05  Date: 08/17/10
[    0.164738] NET: Registered protocol family 16
[    0.164738] Trying to unpack rootfs image as initramfs...
[    0.164738] EISA bus registered
[    0.164738] ACPI: bus type pci registered
[    0.164738] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.164738] PCI: Not using MMCONFIG.
[    0.164738] PCI: PCI BIOS revision 2.10 entry at 0xfd5b9, last bus=8
[    0.164738] PCI: Using configuration type 1 for base access
[    0.168095] bio: create slab <bio-0> at 0
[    0.168813] ACPI: EC: Look up EC in DSDT
[    0.170346] ACPI Warning: Package List length (0xC) larger than NumElements count (0x5), truncated
[    0.170350]  (20090903/dsobject-515)
[    0.172455] ACPI: Interpreter enabled
[    0.172464] ACPI: (supports S0 S3 S4 S5)
[    0.172481] ACPI: Using IOAPIC for interrupt routing
[    0.172517] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.174596] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.174598] PCI: Using MMCONFIG for extended config space
[    0.177706] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.178805] ACPI: No dock devices found.
[    0.178868] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.178983] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.178986] pci 0000:00:01.0: PME# disabled
[    0.179053] pci 0000:00:1b.0: reg 10 64bit mmio: [0x000000-0x003fff]
[    0.179098] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.179101] pci 0000:00:1b.0: PME# disabled
[    0.179167] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.179171] pci 0000:00:1c.0: PME# disabled
[    0.179241] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.179244] pci 0000:00:1c.1: PME# disabled
[    0.179312] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.179316] pci 0000:00:1c.2: PME# disabled
[    0.179367] pci 0000:00:1d.0: reg 20 io port: [0x9fe0-0x9fff]
[    0.179417] pci 0000:00:1d.1: reg 20 io port: [0x9f80-0x9f9f]
[    0.179468] pci 0000:00:1d.2: reg 20 io port: [0x9f60-0x9f7f]
[    0.179519] pci 0000:00:1d.3: reg 20 io port: [0x9f40-0x9f5f]
[    0.179575] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffaffc00-0xffafffff]
[    0.179628] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.179633] pci 0000:00:1d.7: PME# disabled
[    0.179762] pci 0000:00:1f.0: quirk: region d800-d87f claimed by ICH6 ACPI/GPIO/TCO
[    0.179766] pci 0000:00:1f.0: quirk: region eec0-eeff claimed by ICH6 GPIO
[    0.179769] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.179776] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 01e0 (mask 000f)
[    0.179819] pci 0000:00:1f.1: reg 10 io port: [0x9f38-0x9f3f]
[    0.179826] pci 0000:00:1f.1: reg 14 io port: [0x9f34-0x9f37]
[    0.179833] pci 0000:00:1f.1: reg 18 io port: [0x9f28-0x9f2f]
[    0.179839] pci 0000:00:1f.1: reg 1c io port: [0x9f24-0x9f27]
[    0.179846] pci 0000:00:1f.1: reg 20 io port: [0x9f10-0x9f1f]
[    0.179894] pci 0000:00:1f.2: reg 10 io port: [0x9f08-0x9f0f]
[    0.179900] pci 0000:00:1f.2: reg 14 io port: [0x9f04-0x9f07]
[    0.179906] pci 0000:00:1f.2: reg 18 io port: [0x9ef8-0x9eff]
[    0.179912] pci 0000:00:1f.2: reg 1c io port: [0x9ef4-0x9ef7]
[    0.179917] pci 0000:00:1f.2: reg 20 io port: [0x9ee0-0x9eef]
[    0.179924] pci 0000:00:1f.2: reg 24 32bit mmio: [0xffaff800-0xffaffbff]
[    0.180016] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180020] pci 0000:00:1f.2: PME# disabled
[    0.180061] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.180071] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.180080] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.180085] pci 0000:01:00.0: reg 24 io port: [0xcf00-0xcf7f]
[    0.180091] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.180157] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.180161] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.180165] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.180233] pci 0000:02:00.0: reg 10 32bit mmio: [0xffde0000-0xffdfffff]
[    0.180254] pci 0000:02:00.0: reg 18 io port: [0xbfe0-0xbfff]
[    0.180344] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.180350] pci 0000:02:00.0: PME# disabled
[    0.180412] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.180416] pci 0000:00:1c.0: bridge 32bit mmio: [0xffd00000-0xffdfffff]
[    0.180463] pci 0000:00:1c.1: bridge io port: [0xa000-0xafff]
[    0.180467] pci 0000:00:1c.1: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.180603] pci 0000:05:00.0: reg 10 32bit mmio: [0xffcff000-0xffcfffff]
[    0.180825] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.180837] pci 0000:05:00.0: PME# disabled
[    0.180931] pci 0000:00:1c.2: bridge 32bit mmio: [0xffc00000-0xffcfffff]
[    0.180989] pci 0000:06:09.0: reg 10 32bit mmio: [0x000000-0x3ffffff]
[    0.181081] pci 0000:06:0b.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.181102] pci 0000:06:0b.0: supports D1 D2
[    0.181104] pci 0000:06:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.181108] pci 0000:06:0b.0: PME# disabled
[    0.181144] pci 0000:06:0b.1: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.181151] pci 0000:06:0b.1: reg 14 32bit mmio: [0x000000-0x003fff]
[    0.181197] pci 0000:06:0b.1: supports D1 D2
[    0.181199] pci 0000:06:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.181203] pci 0000:06:0b.1: PME# disabled
[    0.181239] pci 0000:06:0b.2: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.181289] pci 0000:06:0b.2: supports D1 D2
[    0.181291] pci 0000:06:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.181295] pci 0000:06:0b.2: PME# disabled
[    0.181332] pci 0000:06:0b.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.181382] pci 0000:06:0b.3: supports D1 D2
[    0.181384] pci 0000:06:0b.3: PME# supported from D0 D1 D2 D3hot
[    0.181388] pci 0000:06:0b.3: PME# disabled
[    0.181427] pci 0000:00:1e.0: transparent bridge
[    0.181473] pci_bus 0000:00: on NUMA node 0
[    0.181476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.181560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.181676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.181729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXCB._PRT]
[    0.181777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[    0.181830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.184583] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.184697] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.184814] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.184928] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.185042] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.185157] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.185270] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.185387] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.185500] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.185506] vgaarb: loaded
[    0.185620] SCSI subsystem initialized
[    0.185700] libata version 3.00 loaded.
[    0.185769] usbcore: registered new interface driver usbfs
[    0.185781] usbcore: registered new interface driver hub
[    0.185807] usbcore: registered new device driver usb
[    0.185992] ACPI: WMI: Mapper loaded
[    0.185994] PCI: Using ACPI for IRQ routing
[    0.186233] NetLabel: Initializing
[    0.186235] NetLabel:  domain hash size = 128
[    0.186236] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.186249] NetLabel:  unlabeled traffic allowed by default
[    0.186278] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.186283] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192072] Switching to clocksource tsc
[    0.194068] AppArmor: AppArmor Filesystem Enabled
[    0.194082] pnp: PnP ACPI init
[    0.194096] ACPI: bus type pnp registered
[    0.194995] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.194998] pnp 00:00: mem resource (0xe0000-0xfffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.195001] pnp 00:00: mem resource (0x100000-0x7ff6ffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.196836] pnp: PnP ACPI: found 11 devices
[    0.196838] ACPI: ACPI bus type pnp unregistered
[    0.196842] PnPBIOS: Disabled by ACPI PNP
[    0.196856] system 00:00: iomem range 0x7ff70000-0x7ff7ffff could not be reserved
[    0.196859] system 00:00: iomem range 0x7ff80000-0x7fffffff has been reserved
[    0.196862] system 00:00: iomem range 0xfec00000-0xfec27fff could not be reserved
[    0.196864] system 00:00: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.196867] system 00:00: iomem range 0xfed1c000-0xfed8ffff has been reserved
[    0.196869] system 00:00: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.196872] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.196875] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.196877] system 00:00: iomem range 0xffe00000-0xffffffff has been reserved
[    0.196882] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.196891] system 00:09: ioport range 0x1e0-0x1ef has been reserved
[    0.196893] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.196896] system 00:09: ioport range 0xe000-0xe07f has been reserved
[    0.196898] system 00:09: ioport range 0xe080-0xe0ff has been reserved
[    0.196901] system 00:09: ioport range 0xe400-0xe47f has been reserved
[    0.196903] system 00:09: ioport range 0xe480-0xe4ff has been reserved
[    0.196906] system 00:09: ioport range 0xe800-0xe87f has been reserved
[    0.196908] system 00:09: ioport range 0xe880-0xe8ff has been reserved
[    0.196911] system 00:09: ioport range 0xec00-0xec7f has been reserved
[    0.196913] system 00:09: ioport range 0xec80-0xecff has been reserved
[    0.196916] system 00:09: ioport range 0xd800-0xd87f has been reserved
[    0.196918] system 00:09: ioport range 0xd880-0xd89f has been reserved
[    0.196920] system 00:09: ioport range 0xeeb0-0xeebf has been reserved
[    0.196923] system 00:09: ioport range 0xeec0-0xeeff has been reserved
[    0.196925] system 00:09: ioport range 0x680-0x6ff has been reserved
[    0.196929] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.231677] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf0000000-0xefffffff]
[    0.231681] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.231684] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.231688] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.231692] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.231697] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.231700] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.231704] pci 0000:00:1c.0:   MEM window: 0xffd00000-0xffdfffff
[    0.231708] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.231714] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.231717] pci 0000:00:1c.1:   IO window: 0xa000-0xafff
[    0.231723] pci 0000:00:1c.1:   MEM window: 0xfa000000-0xfbffffff
[    0.231727] pci 0000:00:1c.1:   PREFETCH window: 0x0000008e000000-0x0000008e1fffff
[    0.231734] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.231735] pci 0000:00:1c.2:   IO window: disabled
[    0.231741] pci 0000:00:1c.2:   MEM window: 0xffc00000-0xffcfffff
[    0.231745] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.231770] pci 0000:06:0b.0: CardBus bridge, secondary bus 0000:07
[    0.231772] pci 0000:06:0b.0:   IO window: 0x001000-0x0010ff
[    0.231776] pci 0000:06:0b.0:   IO window: 0x001400-0x0014ff
[    0.231781] pci 0000:06:0b.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.231785] pci 0000:06:0b.0:   MEM window: 0x88000000-0x8bffffff
[    0.231790] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.231793] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.231798] pci 0000:00:1e.0:   MEM window: 0x84000000-0x8dffffff
[    0.231802] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.231822]   alloc irq_desc for 16 on node -1
[    0.231824]   alloc kstat_irqs on node -1
[    0.231832] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.231836] pci 0000:00:01.0: setting latency timer to 64
[    0.231845]   alloc irq_desc for 17 on node -1
[    0.231846]   alloc kstat_irqs on node -1
[    0.231850] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.231854] pci 0000:00:1c.0: setting latency timer to 64
[    0.231862] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.231866] pci 0000:00:1c.1: setting latency timer to 64
[    0.231874]   alloc irq_desc for 18 on node -1
[    0.231875]   alloc kstat_irqs on node -1
[    0.231879] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.231883] pci 0000:00:1c.2: setting latency timer to 64
[    0.231889] pci 0000:00:1e.0: setting latency timer to 64
[    0.231899] pci 0000:06:0b.0: enabling device (0000 -> 0003)
[    0.231903]   alloc irq_desc for 21 on node -1
[    0.231904]   alloc kstat_irqs on node -1
[    0.231907] pci 0000:06:0b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.231915] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.231917] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.231919] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.231921] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.231924] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.231926] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.231928] pci_bus 0000:02: resource 1 mem: [0xffd00000-0xffdfffff]
[    0.231930] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.231932] pci_bus 0000:03: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.231935] pci_bus 0000:03: resource 2 pref mem [0x8e000000-0x8e1fffff]
[    0.231937] pci_bus 0000:05: resource 1 mem: [0xffc00000-0xffcfffff]
[    0.231939] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.231942] pci_bus 0000:06: resource 1 mem: [0x84000000-0x8dffffff]
[    0.231944] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.231946] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.231948] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.231950] pci_bus 0000:07: resource 0 io:  [0x1000-0x10ff]
[    0.231952] pci_bus 0000:07: resource 1 io:  [0x1400-0x14ff]
[    0.231954] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.231957] pci_bus 0000:07: resource 3 mem: [0x88000000-0x8bffffff]
[    0.231996] NET: Registered protocol family 2
[    0.232105] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.232428] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.232977] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.233249] TCP: Hash tables configured (established 131072 bind 65536)
[    0.233252] TCP reno registered
[    0.233337] NET: Registered protocol family 1
[    0.233451] pci 0000:01:00.0: Boot video device
[    0.233486] Simple Boot Flag at 0x7c set to 0x1
[    0.233648] cpufreq-nforce2: No nForce2 chipset.
[    0.233673] Scanning for low memory corruption every 60 seconds
[    0.233785] audit: initializing netlink socket (disabled)
[    0.233798] type=2000 audit(1282060385.231:1): initialized
[    0.242479] highmem bounce pool size: 64 pages
[    0.242485] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.243898] VFS: Disk quotas dquot_6.5.2
[    0.243951] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.244482] fuse init (API version 7.13)
[    0.244562] msgmni has been set to 1690
[    0.244763] alg: No test for stdrng (krng)
[    0.244816] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.244819] io scheduler noop registered
[    0.244821] io scheduler anticipatory registered
[    0.244823] io scheduler deadline registered
[    0.244858] io scheduler cfq registered (default)
[    0.245001]   alloc irq_desc for 24 on node -1
[    0.245003]   alloc kstat_irqs on node -1
[    0.245011] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.245018] pcieport 0000:00:01.0: setting latency timer to 64
[    0.245116]   alloc irq_desc for 25 on node -1
[    0.245118]   alloc kstat_irqs on node -1
[    0.245124] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.245133] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.245236]   alloc irq_desc for 26 on node -1
[    0.245238]   alloc kstat_irqs on node -1
[    0.245245] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.245252] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.245368]   alloc irq_desc for 27 on node -1
[    0.245370]   alloc kstat_irqs on node -1
[    0.245376] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.245384] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.245460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.245515] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.245627] ACPI: AC Adapter [ADP1] (on-line)
[    0.245695] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.245731] ACPI: Lid Switch [LID]
[    0.245771] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.245776] ACPI: Power Button [PWRB]
[    0.245814] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.245816] ACPI: Power Button [PWRF]
[    0.246142] ACPI: SSDT 7ff75774 000F3 (v01 TOSHIB A0037    20050623 MSFT 0100000E)
[    0.246454] ACPI: SSDT 7ff758dd 0034E (v01 TOSHIB A0037    20050916 MSFT 0100000E)
[    0.246673] Marking TSC unstable due to TSC halts in idle
[    0.246725] processor LNXCPU:00: registered as cooling_device0
[    0.246830] ACPI: SSDT 7ff75867 00076 (v01 TOSHIB A0037    20050623 MSFT 0100000E)
[    0.247035] ACPI: SSDT 7ff75c2b 00079 (v01 TOSHIB A0037    20050916 MSFT 0100000E)
[    0.247287] processor LNXCPU:01: registered as cooling_device1
[    0.248651] thermal LNXTHERM:01: registered as thermal_zone0
[    0.248658] ACPI: Thermal Zone [THRM] (37 C)
[    0.250012] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.251271] brd: module loaded
[    0.251695] loop: module loaded
[    0.251771] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.251856] ata_piix 0000:00:1f.1: version 2.13
[    0.251868] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.251906] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.251986] scsi0 : ata_piix
[    0.252052] scsi1 : ata_piix
[    0.252314] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x9f10 irq 14
[    0.252317] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x9f18 irq 15
[    0.252629] Fixed MDIO Bus: probed
[    0.252660] PPP generic driver version 2.4.2
[    0.252695] tun: Universal TUN/TAP device driver, 1.6
[    0.252696] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.252772] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.252790]   alloc irq_desc for 23 on node -1
[    0.252792]   alloc kstat_irqs on node -1
[    0.252797] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.252809] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.252813] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.252841] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.252858] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.252870] ehci_hcd 0000:00:1d.7: debug port 1
[    0.256768] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.256809] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffaffc00
[    0.256940] Switching to clocksource hpet
[    0.256993] ACPI: Battery Slot [BAT1] (battery absent)
[    0.257004] isapnp: Scanning for PnP cards...
[    0.260865] ata2: port disabled. ignoring.
[    0.270816] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.270936] usb usb1: configuration #1 chosen from 1 choice
[    0.270965] hub 1-0:1.0: USB hub found
[    0.270974] hub 1-0:1.0: 8 ports detected
[    0.271039] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.271056] uhci_hcd: USB Universal Host Controller Interface driver
[    0.271093] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.271100] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.271103] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.271133] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.271157] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009fe0
[    0.271240] usb usb2: configuration #1 chosen from 1 choice
[    0.271262] hub 2-0:1.0: USB hub found
[    0.271268] hub 2-0:1.0: 2 ports detected
[    0.271309]   alloc irq_desc for 19 on node -1
[    0.271311]   alloc kstat_irqs on node -1
[    0.271316] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.271322] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.271324] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.271352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.271380] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009f80
[    0.271459] usb usb3: configuration #1 chosen from 1 choice
[    0.271481] hub 3-0:1.0: USB hub found
[    0.271487] hub 3-0:1.0: 2 ports detected
[    0.271525] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.271532] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.271535] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.271561] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.271588] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009f60
[    0.271671] usb usb4: configuration #1 chosen from 1 choice
[    0.271694] hub 4-0:1.0: USB hub found
[    0.271699] hub 4-0:1.0: 2 ports detected
[    0.271737] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.271742] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.271745] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.271777] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.271804] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00009f40
[    0.271884] usb usb5: configuration #1 chosen from 1 choice
[    0.271907] hub 5-0:1.0: USB hub found
[    0.271913] hub 5-0:1.0: 2 ports detected
[    0.272000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.276571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.276577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.282819] mice: PS/2 mouse device common for all mice
[    0.282944] rtc_cmos 00:08: RTC can wake from S4
[    0.282981] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.283005] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    0.283101] device-mapper: uevent: version 1.0.3
[    0.294115] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.306329] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.349170] Freeing initrd memory: 7778k freed
[    0.484104] device-mapper: multipath: version 1.1.0 loaded
[    0.484110] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484305] EISA: Probing bus 0 at eisa.0
[    0.484315] Cannot allocate resource for EISA slot 1
[    0.484349] EISA: Detected 0 cards.
[    0.484471] cpuidle: using governor ladder
[    0.484557] cpuidle: using governor menu
[    0.484983] TCP cubic registered
[    0.485143] NET: Registered protocol family 10
[    0.485173] ata1.00: ATAPI: TOSHIBA DVDW/HD TS-L802A, TF31, max UDMA/33
[    0.485594] lo: Disabled Privacy Extensions
[    0.485907] NET: Registered protocol family 17
[    0.486173] Using IPI No-Shortcut mode
[    0.486273] PM: Resume from disk failed.
[    0.486288] registered taskstats version 1
[    0.486754]   Magic number: 6:220:892
[    0.486817] bdi default: hash matches
[    0.486846] rtc_cmos 00:08: setting system clock to 2010-08-17 15:53:05 UTC (1282060385)
[    0.486849] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.486850] EDD information not available.
[    0.573405] ata1.00: configured for UDMA/33
[    0.615786] isapnp: No Plug & Play device found
[    0.624966] scsi 0:0:0:0: CD-ROM            TOSHIBA  DVDW/HD TS-L802A TF31 PQ: 0 ANSI: 5
[    0.668040] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.668046] Uniform CD-ROM driver Revision: 3.20
[    0.668213] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.668313] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.668364] Freeing unused kernel memory: 660k freed
[    0.668785] Write protecting the kernel text: 4680k
[    0.668827] Write protecting the kernel read-only data: 1840k
[    0.683521] udev: starting version 151
[    0.740142] ahci 0000:00:1f.2: version 3.0
[    0.740162] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.740201]   alloc irq_desc for 28 on node -1
[    0.740203]   alloc kstat_irqs on node -1
[    0.740212] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.740271] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    0.740274] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    0.740279] ahci 0000:00:1f.2: setting latency timer to 64
[    0.749318] scsi2 : ahci
[    0.749600] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.749602] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.749664] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.749704] e1000e 0000:02:00.0: setting latency timer to 64
[    0.750004]   alloc irq_desc for 29 on node -1
[    0.750006]   alloc kstat_irqs on node -1
[    0.750025] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.773204] scsi3 : ahci
[    0.780335] scsi4 : ahci
[    0.785787] scsi5 : ahci
[    0.786049] ata3: SATA max UDMA/133 abar m1024@0xffaff800 port 0xffaff900 irq 28
[    0.786051] ata4: DUMMY
[    0.786054] ata5: SATA max UDMA/133 abar m1024@0xffaff800 port 0xffaffa00 irq 28
[    0.786055] ata6: DUMMY
[    0.813165] e1000e 0000:02:00.0: Warning: detected ASPM enabled in EEPROM
[    0.872796] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:15:b7:e1:4a:53
[    0.872798] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    0.872868] 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    0.888042] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.057762] usb 4-2: configuration #1 chosen from 1 choice
[    1.104041] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.104632] ACPI Warning for \_SB_.PCI0.FNC2.PRT2._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.104647] ata5.00: _GTF unexpected object type 0x1
[    1.216040] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.216596] ACPI Warning for \_SB_.PCI0.FNC2.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.216610] ata3.00: _GTF unexpected object type 0x1
[    1.421301] ata5.00: ATA-7: TOSHIBA MK1637GSX, DL020M, max UDMA/100
[    1.421307] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.422229] ata5.00: _GTF unexpected object type 0x1
[    1.422507] ata5.00: configured for UDMA/100
[    1.554457] ata3.00: HPA unlocked: 302825250 -> 312581808, native 312581808
[    1.554522] ata3.00: ATA-7: TOSHIBA MK1637GSX, DL020M, max UDMA/100
[    1.554527] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.555448] ata3.00: _GTF unexpected object type 0x1
[    1.555729] ata3.00: configured for UDMA/100
[    1.568211] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL02 PQ: 0 ANSI: 5
[    1.568402] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.568473] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.568518] sd 2:0:0:0: [sda] Write Protect is off
[    1.568521] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.568537] scsi 4:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL02 PQ: 0 ANSI: 5
[    1.568545] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.568670] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.568685]  sda:
[    1.568856] sd 4:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.568897] sd 4:0:0:0: [sdb] Write Protect is off
[    1.568900] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.568922] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.569045]  sdb: sda1
[    1.610191] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.632769] 
[    1.633076] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.635525] ohci1394 0000:06:0b.1: enabling device (0000 -> 0002)
[    1.635533]   alloc irq_desc for 20 on node -1
[    1.635535]   alloc kstat_irqs on node -1
[    1.635541] ohci1394 0000:06:0b.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.692071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[8c006000-8c0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.865992] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.960236] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000a8ece0]
[   16.348382] udev: starting version 151
[   16.508053] type=1505 audit(1282060401.521:2):  operation="profile_load" pid=488 name="/sbin/dhclient3"
[   16.508762] type=1505 audit(1282060401.521:3):  operation="profile_load" pid=488 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.509496] type=1505 audit(1282060401.521:4):  operation="profile_load" pid=488 name="/usr/lib/connman/scripts/dhclient-script"
[   16.871868] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   16.871871] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   16.872364] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   16.872366] toshiba_acpi: ktoshkeyd will check 2 times per second
[   16.879204] toshiba_acpi: Dropped 0 keys from the queue on startup
[   17.031763] lp: driver loaded but no devices found
[   17.061190] Linux agpgart interface v0.103
[   17.061902] intel_rng: FWH not detected
[   17.101914] vga16fb: initializing
[   17.101918] vga16fb: mapped to 0xc00a0000
[   17.102065] fb0: VGA16 VGA frame buffer device
[   17.188676] type=1505 audit(1282060402.201:5):  operation="profile_load" pid=653 name="/usr/share/gdm/guest-session/Xsession"
[   17.190134] type=1505 audit(1282060402.201:6):  operation="profile_replace" pid=654 name="/sbin/dhclient3"
[   17.190737] type=1505 audit(1282060402.201:7):  operation="profile_replace" pid=654 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.191060] type=1505 audit(1282060402.201:8):  operation="profile_replace" pid=654 name="/usr/lib/connman/scripts/dhclient-script"
[   17.193949] type=1505 audit(1282060402.205:9):  operation="profile_load" pid=655 name="/usr/bin/evince"
[   17.203264] type=1505 audit(1282060402.213:10):  operation="profile_load" pid=655 name="/usr/bin/evince-previewer"
[   17.208073] type=1505 audit(1282060402.221:11):  operation="profile_load" pid=655 name="/usr/bin/evince-thumbnailer"
[   17.318852] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   17.319106] acpi device:20: registered as cooling_device2
[   17.319236] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1f/LNXVIDEO:00/input/input5
[   17.319293] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   17.319499] lirc_dev: IR Remote Control driver registered, major 61 
[   17.340431] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[   17.378889] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   17.378892] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   17.383526] sdhci: Secure Digital Host Controller Interface driver
[   17.383529] sdhci: Copyright(c) Pierre Ossman
[   17.396138] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[   17.396721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.398404] cfg80211: Calling CRDA to update world regulatory domain
[   17.403071] cfg80211: World regulatory domain updated:
[   17.403074] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.403077] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.403079] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.403081] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.403084] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.403086] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.416064] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   17.601140] usb 3-2: configuration #1 chosen from 1 choice
[   17.676046] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[   17.826629] lirc_dev: lirc_register_driver: sample_rate: 0
[   17.831622] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb4:2
[   17.831690] usbcore: registered new interface driver lirc_mceusb
[   17.851817] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   17.928969] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   18.283517] nvidia: module license 'NVIDIA' taints kernel.
[   18.283522] Disabling lock debugging due to kernel taint
[   18.989381] yenta_cardbus 0000:06:0b.0: CardBus bridge found [1179:0001]
[   18.989399] yenta_cardbus 0000:06:0b.0: Enabling burst memory read transactions
[   18.989404] yenta_cardbus 0000:06:0b.0: Using CSCINT to route CSC interrupts to PCI
[   18.989406] yenta_cardbus 0000:06:0b.0: Routing CardBus interrupts to PCI
[   18.989411] yenta_cardbus 0000:06:0b.0: TI: mfunc 0x01aa1022, devctl 0x64
[   19.056551] Bluetooth: Core ver 2.15
[   19.056602] NET: Registered protocol family 31
[   19.056604] Bluetooth: HCI device and connection manager initialized
[   19.056607] Bluetooth: HCI socket layer initialized
[   19.121293] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.122117] usbcore: registered new interface driver btusb
[   19.244493] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   19.244657] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   19.244674] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.244686] nvidia 0000:01:00.0: setting latency timer to 64
[   19.244693] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.244842] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   19.245832] yenta_cardbus 0000:06:0b.0: ISA IRQ mask 0x0cf8, PCI irq 21
[   19.245835] yenta_cardbus 0000:06:0b.0: Socket status: 30000006
[   19.245840] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   19.245843] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x1000-0x1fff: clean.
[   19.246018] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge Memory window: 0x84000000 - 0x8dffffff
[   19.246020] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   19.248410] sdhci-pci 0000:06:0b.3: SDHCI controller found [104c:803c] (rev 0)
[   19.248476] sdhci-pci 0000:06:0b.3: enabling device (0000 -> 0002)
[   19.248482] sdhci-pci 0000:06:0b.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   19.248578] Registered led device: mmc0::
[   19.248623] mmc0: SDHCI controller on PCI [0000:06:0b.3] using DMA
[   19.249167] tifm_7xx1 0000:06:0b.2: enabling device (0000 -> 0002)
[   19.249174] tifm_7xx1 0000:06:0b.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   19.291014] Bluetooth: L2CAP ver 2.14
[   19.291016] Bluetooth: L2CAP socket layer initialized
[   19.315816] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.315819] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.315911] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.315928] iwl3945 0000:05:00.0: setting latency timer to 64
[   19.384728] Console: switching to colour frame buffer device 80x30
[   19.387717] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.387719] Bluetooth: BNEP filters: protocol multicast
[   19.391164] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.391168] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.391273]   alloc irq_desc for 30 on node -1
[   19.391275]   alloc kstat_irqs on node -1
[   19.391305] iwl3945 0000:05:00.0: irq 30 for MSI/MSI-X
[   19.438514] Bridge firewalling registered
[   19.474082] Bluetooth: SCO (Voice Link) ver 0.6
[   19.474084] Bluetooth: SCO socket layer initialized
[   19.639236] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.649800] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   19.676599] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   19.704364] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.706403] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.707216] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.707933] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.710179] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.753461] Registered led device: iwl-phy0::radio
[   19.753481] Registered led device: iwl-phy0::assoc
[   19.753536] Registered led device: iwl-phy0::RX
[   19.753555] Registered led device: iwl-phy0::TX
[   19.763785] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.763818] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.763823] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   19.763830]   alloc irq_desc for 22 on node -1
[   19.763832]   alloc kstat_irqs on node -1
[   19.763838] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.763871] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.764891] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.789106] Bluetooth: RFCOMM TTY layer initialized
[   19.789111] Bluetooth: RFCOMM socket layer initialized
[   19.789112] Bluetooth: RFCOMM ver 1.11
[   20.299039] [drm] Initialized drm 1.1.0 20060810
[   30.324073] ppdev: user-space parallel port driver
[   81.874175] wlan0: deauthenticating from 00:1d:68:e9:02:33 by local choice (reason=3)
[   81.875451] wlan0: direct probe to AP 00:1d:68:e9:02:33 (try 1)
[   81.877559] wlan0: direct probe responded
[   81.877566] wlan0: authenticate with AP 00:1d:68:e9:02:33 (try 1)
[   81.879842] wlan0: authenticated
[   81.879870] wlan0: associate with AP 00:1d:68:e9:02:33 (try 1)
[   81.882553] wlan0: RX AssocResp from 00:1d:68:e9:02:33 (capab=0x411 status=0 aid=3)
[   81.882559] wlan0: associated
[   81.885199] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   92.425018] wlan0: no IPv6 routers present
```

---

### Post by saedelaere on 2010-08-17
> **abdulq8 said:**
> I tried the code but it doesn't work
I have a problem with the display
this is the screen image for the problem
[http://www.flickr.com/photos/53083724@N04/4898127899/](http://www.flickr.com/photos/53083724@N04/4898127899/) 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff80000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec28000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x7ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF uncachable
[    0.000000]   D4000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FEDA0000 mask FFFFE0000 write-back
[    0.000000]   1 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  modified: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff70000 (usable)
[    0.000000]  modified: 000000007ff70000 - 000000007ff80000 (ACPI data)
[    0.000000]  modified: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec28000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37857000 - 37fef9bc
[    0.000000] Allocated new RAMDISK: 008e0000 - 010789bc
[    0.000000] Move RAMDISK from 0000000037857000 - 0000000037fef9bb to 008e0000 - 010789bb
[    0.000000] ACPI: RSDP 000f0180 00014 (v00 TOSHIB)
[    0.000000] ACPI: RSDT 7ff70000 0004C (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: FACP 7ff70074 00084 (v02 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: DSDT 7ff700f8 05179 (v01 TOSHIB A0037    20060706 MSFT 0100000E)
[    0.000000] ACPI: FACS 000eee00 00040
[    0.000000] ACPI: SSDT 7ff75271 00306 (v01 TOSHIB A0037    20050926 MSFT 0100000E)
[    0.000000] ACPI: DBGP 7ff75d88 00034 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: BOOT 7ff7004c 00028 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: APIC 7ff75ce4 00068 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: MCFG 7ff75d4c 0003C (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: HPET 7ff75f1c 00038 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: SSDT 7ff75f54 005E1 (v01 TOSHIB A0037    20050523 MSFT 0100000E)
[    0.000000] ACPI: SSDT 7ff75e6c 000B0 (v01 TOSHIB A0037    20051014 MSFT 0100000E)
[    0.000000] ACPI: SSDT 7ff77078 00076 (v01 TOSHIB A0037    20051021 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df21c]              BRK ==> [00008dc000 - 00008df21c]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 00010789bc]      NEW RAMDISK ==> [00008e0000 - 00010789bc]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ff70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007ff70
[    0.000000] On node 0 totalpages: 524042
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c107a000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2319 pages used for memmap
[    0.000000]   HighMem zone: 294499 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
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
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519947
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b09743c7-e1e5-4c10-92ad-371721a1a6ce ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10482880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ff70)
[    0.000000] Memory: 2051652k/2096576k available (4679k kernel code, 43448k reserved, 2116k data, 660k init, 1187272k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2327.830 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4655.66 BogoMIPS (lpj=9311320)
[    0.004021] Security Framework initialized
[    0.004041] AppArmor: AppArmor initialized
[    0.004047] Mount-cache hash table entries: 512
[    0.004172] Initializing cgroup subsys ns
[    0.004176] Initializing cgroup subsys cpuacct
[    0.004180] Initializing cgroup subsys memory
[    0.004187] Initializing cgroup subsys devices
[    0.004190] Initializing cgroup subsys freezer
[    0.004192] Initializing cgroup subsys net_cls
[    0.004211] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004214] CPU: L2 cache: 4096K
[    0.004217] CPU: Physical Processor ID: 0
[    0.004219] CPU: Processor Core ID: 0
[    0.004222] mce: CPU supports 6 MCE banks
[    0.004230] CPU0: Thermal monitoring handled by SMI
[    0.004234] using mwait in idle threads.
[    0.004241] Performance Events: Core2 events, Intel PMU driver.
[    0.004249] ... version:                2
[    0.004251] ... bit width:              40
[    0.004252] ... generic registers:      2
[    0.004254] ... value mask:             000000ffffffffff
[    0.004256] ... max period:             000000007fffffff
[    0.004257] ... fixed-purpose events:   3
[    0.004259] ... event mask:             0000000700000003
[    0.004263] Checking 'hlt' instruction... OK.
[    0.022465] ACPI: Core revision 20090903
[    0.030278] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030284] ftrace: allocating 21780 entries in 43 pages
[    0.032054] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032366] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.075373] CPU0: Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz stepping 06
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 4096K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.160054] CPU1: Intel(R) Core(TM)2 CPU         T7600  @ 2.33GHz stepping 06
[    0.160065] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164018] Brought up 2 CPUs
[    0.164021] Total of 2 processors activated (9310.75 BogoMIPS).
[    0.164626] CPU0 attaching sched-domain:
[    0.164629]  domain 0: span 0-1 level MC
[    0.164631]   groups: 0 1
[    0.164637] CPU1 attaching sched-domain:
[    0.164639]  domain 0: span 0-1 level MC
[    0.164641]   groups: 1 0
[    0.164738] devtmpfs: initialized
[    0.164738] regulator: core version 0.5
[    0.164738] Time: 15:53:05  Date: 08/17/10
[    0.164738] NET: Registered protocol family 16
[    0.164738] Trying to unpack rootfs image as initramfs...
[    0.164738] EISA bus registered
[    0.164738] ACPI: bus type pci registered
[    0.164738] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.164738] PCI: Not using MMCONFIG.
[    0.164738] PCI: PCI BIOS revision 2.10 entry at 0xfd5b9, last bus=8
[    0.164738] PCI: Using configuration type 1 for base access
[    0.168095] bio: create slab <bio-0> at 0
[    0.168813] ACPI: EC: Look up EC in DSDT
[    0.170346] ACPI Warning: Package List length (0xC) larger than NumElements count (0x5), truncated
[    0.170350]  (20090903/dsobject-515)
[    0.172455] ACPI: Interpreter enabled
[    0.172464] ACPI: (supports S0 S3 S4 S5)
[    0.172481] ACPI: Using IOAPIC for interrupt routing
[    0.172517] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.174596] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.174598] PCI: Using MMCONFIG for extended config space
[    0.177706] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.178805] ACPI: No dock devices found.
[    0.178868] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.178983] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.178986] pci 0000:00:01.0: PME# disabled
[    0.179053] pci 0000:00:1b.0: reg 10 64bit mmio: [0x000000-0x003fff]
[    0.179098] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.179101] pci 0000:00:1b.0: PME# disabled
[    0.179167] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.179171] pci 0000:00:1c.0: PME# disabled
[    0.179241] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.179244] pci 0000:00:1c.1: PME# disabled
[    0.179312] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.179316] pci 0000:00:1c.2: PME# disabled
[    0.179367] pci 0000:00:1d.0: reg 20 io port: [0x9fe0-0x9fff]
[    0.179417] pci 0000:00:1d.1: reg 20 io port: [0x9f80-0x9f9f]
[    0.179468] pci 0000:00:1d.2: reg 20 io port: [0x9f60-0x9f7f]
[    0.179519] pci 0000:00:1d.3: reg 20 io port: [0x9f40-0x9f5f]
[    0.179575] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffaffc00-0xffafffff]
[    0.179628] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.179633] pci 0000:00:1d.7: PME# disabled
[    0.179762] pci 0000:00:1f.0: quirk: region d800-d87f claimed by ICH6 ACPI/GPIO/TCO
[    0.179766] pci 0000:00:1f.0: quirk: region eec0-eeff claimed by ICH6 GPIO
[    0.179769] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.179776] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 01e0 (mask 000f)
[    0.179819] pci 0000:00:1f.1: reg 10 io port: [0x9f38-0x9f3f]
[    0.179826] pci 0000:00:1f.1: reg 14 io port: [0x9f34-0x9f37]
[    0.179833] pci 0000:00:1f.1: reg 18 io port: [0x9f28-0x9f2f]
[    0.179839] pci 0000:00:1f.1: reg 1c io port: [0x9f24-0x9f27]
[    0.179846] pci 0000:00:1f.1: reg 20 io port: [0x9f10-0x9f1f]
[    0.179894] pci 0000:00:1f.2: reg 10 io port: [0x9f08-0x9f0f]
[    0.179900] pci 0000:00:1f.2: reg 14 io port: [0x9f04-0x9f07]
[    0.179906] pci 0000:00:1f.2: reg 18 io port: [0x9ef8-0x9eff]
[    0.179912] pci 0000:00:1f.2: reg 1c io port: [0x9ef4-0x9ef7]
[    0.179917] pci 0000:00:1f.2: reg 20 io port: [0x9ee0-0x9eef]
[    0.179924] pci 0000:00:1f.2: reg 24 32bit mmio: [0xffaff800-0xffaffbff]
[    0.180016] pci 0000:00:1f.2: PME# supported from D3hot
[    0.180020] pci 0000:00:1f.2: PME# disabled
[    0.180061] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.180071] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.180080] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.180085] pci 0000:01:00.0: reg 24 io port: [0xcf00-0xcf7f]
[    0.180091] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.180157] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.180161] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.180165] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.180233] pci 0000:02:00.0: reg 10 32bit mmio: [0xffde0000-0xffdfffff]
[    0.180254] pci 0000:02:00.0: reg 18 io port: [0xbfe0-0xbfff]
[    0.180344] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.180350] pci 0000:02:00.0: PME# disabled
[    0.180412] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.180416] pci 0000:00:1c.0: bridge 32bit mmio: [0xffd00000-0xffdfffff]
[    0.180463] pci 0000:00:1c.1: bridge io port: [0xa000-0xafff]
[    0.180467] pci 0000:00:1c.1: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.180603] pci 0000:05:00.0: reg 10 32bit mmio: [0xffcff000-0xffcfffff]
[    0.180825] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.180837] pci 0000:05:00.0: PME# disabled
[    0.180931] pci 0000:00:1c.2: bridge 32bit mmio: [0xffc00000-0xffcfffff]
[    0.180989] pci 0000:06:09.0: reg 10 32bit mmio: [0x000000-0x3ffffff]
[    0.181081] pci 0000:06:0b.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.181102] pci 0000:06:0b.0: supports D1 D2
[    0.181104] pci 0000:06:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.181108] pci 0000:06:0b.0: PME# disabled
[    0.181144] pci 0000:06:0b.1: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.181151] pci 0000:06:0b.1: reg 14 32bit mmio: [0x000000-0x003fff]
[    0.181197] pci 0000:06:0b.1: supports D1 D2
[    0.181199] pci 0000:06:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.181203] pci 0000:06:0b.1: PME# disabled
[    0.181239] pci 0000:06:0b.2: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.181289] pci 0000:06:0b.2: supports D1 D2
[    0.181291] pci 0000:06:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.181295] pci 0000:06:0b.2: PME# disabled
[    0.181332] pci 0000:06:0b.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.181382] pci 0000:06:0b.3: supports D1 D2
[    0.181384] pci 0000:06:0b.3: PME# supported from D0 D1 D2 D3hot
[    0.181388] pci 0000:06:0b.3: PME# disabled
[    0.181427] pci 0000:00:1e.0: transparent bridge
[    0.181473] pci_bus 0000:00: on NUMA node 0
[    0.181476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.181560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.181676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.181729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXCB._PRT]
[    0.181777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MPEX._PRT]
[    0.181830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.184583] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.184697] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.184814] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.184928] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.185042] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.185157] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.185270] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.185387] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.185500] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.185506] vgaarb: loaded
[    0.185620] SCSI subsystem initialized
[    0.185700] libata version 3.00 loaded.
[    0.185769] usbcore: registered new interface driver usbfs
[    0.185781] usbcore: registered new interface driver hub
[    0.185807] usbcore: registered new device driver usb
[    0.185992] ACPI: WMI: Mapper loaded
[    0.185994] PCI: Using ACPI for IRQ routing
[    0.186233] NetLabel: Initializing
[    0.186235] NetLabel:  domain hash size = 128
[    0.186236] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.186249] NetLabel:  unlabeled traffic allowed by default
[    0.186278] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.186283] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192072] Switching to clocksource tsc
[    0.194068] AppArmor: AppArmor Filesystem Enabled
[    0.194082] pnp: PnP ACPI init
[    0.194096] ACPI: bus type pnp registered
[    0.194995] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.194998] pnp 00:00: mem resource (0xe0000-0xfffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.195001] pnp 00:00: mem resource (0x100000-0x7ff6ffff) overlaps 0000:06:09.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.196836] pnp: PnP ACPI: found 11 devices
[    0.196838] ACPI: ACPI bus type pnp unregistered
[    0.196842] PnPBIOS: Disabled by ACPI PNP
[    0.196856] system 00:00: iomem range 0x7ff70000-0x7ff7ffff could not be reserved
[    0.196859] system 00:00: iomem range 0x7ff80000-0x7fffffff has been reserved
[    0.196862] system 00:00: iomem range 0xfec00000-0xfec27fff could not be reserved
[    0.196864] system 00:00: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.196867] system 00:00: iomem range 0xfed1c000-0xfed8ffff has been reserved
[    0.196869] system 00:00: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.196872] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.196875] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.196877] system 00:00: iomem range 0xffe00000-0xffffffff has been reserved
[    0.196882] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.196891] system 00:09: ioport range 0x1e0-0x1ef has been reserved
[    0.196893] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.196896] system 00:09: ioport range 0xe000-0xe07f has been reserved
[    0.196898] system 00:09: ioport range 0xe080-0xe0ff has been reserved
[    0.196901] system 00:09: ioport range 0xe400-0xe47f has been reserved
[    0.196903] system 00:09: ioport range 0xe480-0xe4ff has been reserved
[    0.196906] system 00:09: ioport range 0xe800-0xe87f has been reserved
[    0.196908] system 00:09: ioport range 0xe880-0xe8ff has been reserved
[    0.196911] system 00:09: ioport range 0xec00-0xec7f has been reserved
[    0.196913] system 00:09: ioport range 0xec80-0xecff has been reserved
[    0.196916] system 00:09: ioport range 0xd800-0xd87f has been reserved
[    0.196918] system 00:09: ioport range 0xd880-0xd89f has been reserved
[    0.196920] system 00:09: ioport range 0xeeb0-0xeebf has been reserved
[    0.196923] system 00:09: ioport range 0xeec0-0xeeff has been reserved
[    0.196925] system 00:09: ioport range 0x680-0x6ff has been reserved
[    0.196929] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.231677] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf0000000-0xefffffff]
[    0.231681] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.231684] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.231688] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.231692] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.231697] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.231700] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.231704] pci 0000:00:1c.0:   MEM window: 0xffd00000-0xffdfffff
[    0.231708] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.231714] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.231717] pci 0000:00:1c.1:   IO window: 0xa000-0xafff
[    0.231723] pci 0000:00:1c.1:   MEM window: 0xfa000000-0xfbffffff
[    0.231727] pci 0000:00:1c.1:   PREFETCH window: 0x0000008e000000-0x0000008e1fffff
[    0.231734] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.231735] pci 0000:00:1c.2:   IO window: disabled
[    0.231741] pci 0000:00:1c.2:   MEM window: 0xffc00000-0xffcfffff
[    0.231745] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.231770] pci 0000:06:0b.0: CardBus bridge, secondary bus 0000:07
[    0.231772] pci 0000:06:0b.0:   IO window: 0x001000-0x0010ff
[    0.231776] pci 0000:06:0b.0:   IO window: 0x001400-0x0014ff
[    0.231781] pci 0000:06:0b.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.231785] pci 0000:06:0b.0:   MEM window: 0x88000000-0x8bffffff
[    0.231790] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.231793] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.231798] pci 0000:00:1e.0:   MEM window: 0x84000000-0x8dffffff
[    0.231802] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.231822]   alloc irq_desc for 16 on node -1
[    0.231824]   alloc kstat_irqs on node -1
[    0.231832] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.231836] pci 0000:00:01.0: setting latency timer to 64
[    0.231845]   alloc irq_desc for 17 on node -1
[    0.231846]   alloc kstat_irqs on node -1
[    0.231850] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.231854] pci 0000:00:1c.0: setting latency timer to 64
[    0.231862] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.231866] pci 0000:00:1c.1: setting latency timer to 64
[    0.231874]   alloc irq_desc for 18 on node -1
[    0.231875]   alloc kstat_irqs on node -1
[    0.231879] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.231883] pci 0000:00:1c.2: setting latency timer to 64
[    0.231889] pci 0000:00:1e.0: setting latency timer to 64
[    0.231899] pci 0000:06:0b.0: enabling device (0000 -> 0003)
[    0.231903]   alloc irq_desc for 21 on node -1
[    0.231904]   alloc kstat_irqs on node -1
[    0.231907] pci 0000:06:0b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.231915] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.231917] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.231919] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.231921] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.231924] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.231926] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.231928] pci_bus 0000:02: resource 1 mem: [0xffd00000-0xffdfffff]
[    0.231930] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
[    0.231932] pci_bus 0000:03: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.231935] pci_bus 0000:03: resource 2 pref mem [0x8e000000-0x8e1fffff]
[    0.231937] pci_bus 0000:05: resource 1 mem: [0xffc00000-0xffcfffff]
[    0.231939] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.231942] pci_bus 0000:06: resource 1 mem: [0x84000000-0x8dffffff]
[    0.231944] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.231946] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.231948] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.231950] pci_bus 0000:07: resource 0 io:  [0x1000-0x10ff]
[    0.231952] pci_bus 0000:07: resource 1 io:  [0x1400-0x14ff]
[    0.231954] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.231957] pci_bus 0000:07: resource 3 mem: [0x88000000-0x8bffffff]
[    0.231996] NET: Registered protocol family 2
[    0.232105] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.232428] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.232977] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.233249] TCP: Hash tables configured (established 131072 bind 65536)
[    0.233252] TCP reno registered
[    0.233337] NET: Registered protocol family 1
[    0.233451] pci 0000:01:00.0: Boot video device
[    0.233486] Simple Boot Flag at 0x7c set to 0x1
[    0.233648] cpufreq-nforce2: No nForce2 chipset.
[    0.233673] Scanning for low memory corruption every 60 seconds
[    0.233785] audit: initializing netlink socket (disabled)
[    0.233798] type=2000 audit(1282060385.231:1): initialized
[    0.242479] highmem bounce pool size: 64 pages
[    0.242485] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.243898] VFS: Disk quotas dquot_6.5.2
[    0.243951] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.244482] fuse init (API version 7.13)
[    0.244562] msgmni has been set to 1690
[    0.244763] alg: No test for stdrng (krng)
[    0.244816] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.244819] io scheduler noop registered
[    0.244821] io scheduler anticipatory registered
[    0.244823] io scheduler deadline registered
[    0.244858] io scheduler cfq registered (default)
[    0.245001]   alloc irq_desc for 24 on node -1
[    0.245003]   alloc kstat_irqs on node -1
[    0.245011] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.245018] pcieport 0000:00:01.0: setting latency timer to 64
[    0.245116]   alloc irq_desc for 25 on node -1
[    0.245118]   alloc kstat_irqs on node -1
[    0.245124] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.245133] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.245236]   alloc irq_desc for 26 on node -1
[    0.245238]   alloc kstat_irqs on node -1
[    0.245245] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.245252] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.245368]   alloc irq_desc for 27 on node -1
[    0.245370]   alloc kstat_irqs on node -1
[    0.245376] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.245384] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.245460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.245515] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.245627] ACPI: AC Adapter [ADP1] (on-line)
[    0.245695] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.245731] ACPI: Lid Switch [LID]
[    0.245771] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.245776] ACPI: Power Button [PWRB]
[    0.245814] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.245816] ACPI: Power Button [PWRF]
[    0.246142] ACPI: SSDT 7ff75774 000F3 (v01 TOSHIB A0037    20050623 MSFT 0100000E)
[    0.246454] ACPI: SSDT 7ff758dd 0034E (v01 TOSHIB A0037    20050916 MSFT 0100000E)
[    0.246673] Marking TSC unstable due to TSC halts in idle
[    0.246725] processor LNXCPU:00: registered as cooling_device0
[    0.246830] ACPI: SSDT 7ff75867 00076 (v01 TOSHIB A0037    20050623 MSFT 0100000E)
[    0.247035] ACPI: SSDT 7ff75c2b 00079 (v01 TOSHIB A0037    20050916 MSFT 0100000E)
[    0.247287] processor LNXCPU:01: registered as cooling_device1
[    0.248651] thermal LNXTHERM:01: registered as thermal_zone0
[    0.248658] ACPI: Thermal Zone [THRM] (37 C)
[    0.250012] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.251271] brd: module loaded
[    0.251695] loop: module loaded
[    0.251771] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.251856] ata_piix 0000:00:1f.1: version 2.13
[    0.251868] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.251906] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.251986] scsi0 : ata_piix
[    0.252052] scsi1 : ata_piix
[    0.252314] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x9f10 irq 14
[    0.252317] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x9f18 irq 15
[    0.252629] Fixed MDIO Bus: probed
[    0.252660] PPP generic driver version 2.4.2
[    0.252695] tun: Universal TUN/TAP device driver, 1.6
[    0.252696] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.252772] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.252790]   alloc irq_desc for 23 on node -1
[    0.252792]   alloc kstat_irqs on node -1
[    0.252797] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.252809] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.252813] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.252841] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.252858] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.252870] ehci_hcd 0000:00:1d.7: debug port 1
[    0.256768] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.256809] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffaffc00
[    0.256940] Switching to clocksource hpet
[    0.256993] ACPI: Battery Slot [BAT1] (battery absent)
[    0.257004] isapnp: Scanning for PnP cards...
[    0.260865] ata2: port disabled. ignoring.
[    0.270816] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.270936] usb usb1: configuration #1 chosen from 1 choice
[    0.270965] hub 1-0:1.0: USB hub found
[    0.270974] hub 1-0:1.0: 8 ports detected
[    0.271039] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.271056] uhci_hcd: USB Universal Host Controller Interface driver
[    0.271093] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.271100] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.271103] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.271133] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.271157] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009fe0
[    0.271240] usb usb2: configuration #1 chosen from 1 choice
[    0.271262] hub 2-0:1.0: USB hub found
[    0.271268] hub 2-0:1.0: 2 ports detected
[    0.271309]   alloc irq_desc for 19 on node -1
[    0.271311]   alloc kstat_irqs on node -1
[    0.271316] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.271322] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.271324] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.271352] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.271380] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009f80
[    0.271459] usb usb3: configuration #1 chosen from 1 choice
[    0.271481] hub 3-0:1.0: USB hub found
[    0.271487] hub 3-0:1.0: 2 ports detected
[    0.271525] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.271532] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.271535] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.271561] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.271588] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009f60
[    0.271671] usb usb4: configuration #1 chosen from 1 choice
[    0.271694] hub 4-0:1.0: USB hub found
[    0.271699] hub 4-0:1.0: 2 ports detected
[    0.271737] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.271742] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.271745] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.271777] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.271804] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00009f40
[    0.271884] usb usb5: configuration #1 chosen from 1 choice
[    0.271907] hub 5-0:1.0: USB hub found
[    0.271913] hub 5-0:1.0: 2 ports detected
[    0.272000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.276571] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.276577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.282819] mice: PS/2 mouse device common for all mice
[    0.282944] rtc_cmos 00:08: RTC can wake from S4
[    0.282981] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.283005] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    0.283101] device-mapper: uevent: version 1.0.3
[    0.294115] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.306329] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.349170] Freeing initrd memory: 7778k freed
[    0.484104] device-mapper: multipath: version 1.1.0 loaded
[    0.484110] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484305] EISA: Probing bus 0 at eisa.0
[    0.484315] Cannot allocate resource for EISA slot 1
[    0.484349] EISA: Detected 0 cards.
[    0.484471] cpuidle: using governor ladder
[    0.484557] cpuidle: using governor menu
[    0.484983] TCP cubic registered
[    0.485143] NET: Registered protocol family 10
[    0.485173] ata1.00: ATAPI: TOSHIBA DVDW/HD TS-L802A, TF31, max UDMA/33
[    0.485594] lo: Disabled Privacy Extensions
[    0.485907] NET: Registered protocol family 17
[    0.486173] Using IPI No-Shortcut mode
[    0.486273] PM: Resume from disk failed.
[    0.486288] registered taskstats version 1
[    0.486754]   Magic number: 6:220:892
[    0.486817] bdi default: hash matches
[    0.486846] rtc_cmos 00:08: setting system clock to 2010-08-17 15:53:05 UTC (1282060385)
[    0.486849] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.486850] EDD information not available.
[    0.573405] ata1.00: configured for UDMA/33
[    0.615786] isapnp: No Plug & Play device found
[    0.624966] scsi 0:0:0:0: CD-ROM            TOSHIBA  DVDW/HD TS-L802A TF31 PQ: 0 ANSI: 5
[    0.668040] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.668046] Uniform CD-ROM driver Revision: 3.20
[    0.668213] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.668313] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.668364] Freeing unused kernel memory: 660k freed
[    0.668785] Write protecting the kernel text: 4680k
[    0.668827] Write protecting the kernel read-only data: 1840k
[    0.683521] udev: starting version 151
[    0.740142] ahci 0000:00:1f.2: version 3.0
[    0.740162] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.740201]   alloc irq_desc for 28 on node -1
[    0.740203]   alloc kstat_irqs on node -1
[    0.740212] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.740271] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    0.740274] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    0.740279] ahci 0000:00:1f.2: setting latency timer to 64
[    0.749318] scsi2 : ahci
[    0.749600] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.749602] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.749664] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.749704] e1000e 0000:02:00.0: setting latency timer to 64
[    0.750004]   alloc irq_desc for 29 on node -1
[    0.750006]   alloc kstat_irqs on node -1
[    0.750025] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.773204] scsi3 : ahci
[    0.780335] scsi4 : ahci
[    0.785787] scsi5 : ahci
[    0.786049] ata3: SATA max UDMA/133 abar m1024@0xffaff800 port 0xffaff900 irq 28
[    0.786051] ata4: DUMMY
[    0.786054] ata5: SATA max UDMA/133 abar m1024@0xffaff800 port 0xffaffa00 irq 28
[    0.786055] ata6: DUMMY
[    0.813165] e1000e 0000:02:00.0: Warning: detected ASPM enabled in EEPROM
[    0.872796] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:15:b7:e1:4a:53
[    0.872798] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    0.872868] 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    0.888042] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.057762] usb 4-2: configuration #1 chosen from 1 choice
[    1.104041] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.104632] ACPI Warning for \_SB_.PCI0.FNC2.PRT2._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.104647] ata5.00: _GTF unexpected object type 0x1
[    1.216040] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.216596] ACPI Warning for \_SB_.PCI0.FNC2.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    1.216610] ata3.00: _GTF unexpected object type 0x1
[    1.421301] ata5.00: ATA-7: TOSHIBA MK1637GSX, DL020M, max UDMA/100
[    1.421307] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.422229] ata5.00: _GTF unexpected object type 0x1
[    1.422507] ata5.00: configured for UDMA/100
[    1.554457] ata3.00: HPA unlocked: 302825250 -> 312581808, native 312581808
[    1.554522] ata3.00: ATA-7: TOSHIBA MK1637GSX, DL020M, max UDMA/100
[    1.554527] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.555448] ata3.00: _GTF unexpected object type 0x1
[    1.555729] ata3.00: configured for UDMA/100
[    1.568211] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL02 PQ: 0 ANSI: 5
[    1.568402] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.568473] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.568518] sd 2:0:0:0: [sda] Write Protect is off
[    1.568521] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.568537] scsi 4:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL02 PQ: 0 ANSI: 5
[    1.568545] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.568670] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    1.568685]  sda:
[    1.568856] sd 4:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.568897] sd 4:0:0:0: [sdb] Write Protect is off
[    1.568900] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.568922] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.569045]  sdb: sda1
[    1.610191] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.632769] 
[    1.633076] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.635525] ohci1394 0000:06:0b.1: enabling device (0000 -> 0002)
[    1.635533]   alloc irq_desc for 20 on node -1
[    1.635535]   alloc kstat_irqs on node -1
[    1.635541] ohci1394 0000:06:0b.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.692071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[8c006000-8c0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.865992] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.960236] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000a8ece0]
[   16.348382] udev: starting version 151
[   16.508053] type=1505 audit(1282060401.521:2):  operation="profile_load" pid=488 name="/sbin/dhclient3"
[   16.508762] type=1505 audit(1282060401.521:3):  operation="profile_load" pid=488 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.509496] type=1505 audit(1282060401.521:4):  operation="profile_load" pid=488 name="/usr/lib/connman/scripts/dhclient-script"
[   16.871868] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   16.871871] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   16.872364] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   16.872366] toshiba_acpi: ktoshkeyd will check 2 times per second
[   16.879204] toshiba_acpi: Dropped 0 keys from the queue on startup
[   17.031763] lp: driver loaded but no devices found
[   17.061190] Linux agpgart interface v0.103
[   17.061902] intel_rng: FWH not detected
[   17.101914] vga16fb: initializing
[   17.101918] vga16fb: mapped to 0xc00a0000
[   17.102065] fb0: VGA16 VGA frame buffer device
[   17.188676] type=1505 audit(1282060402.201:5):  operation="profile_load" pid=653 name="/usr/share/gdm/guest-session/Xsession"
[   17.190134] type=1505 audit(1282060402.201:6):  operation="profile_replace" pid=654 name="/sbin/dhclient3"
[   17.190737] type=1505 audit(1282060402.201:7):  operation="profile_replace" pid=654 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.191060] type=1505 audit(1282060402.201:8):  operation="profile_replace" pid=654 name="/usr/lib/connman/scripts/dhclient-script"
[   17.193949] type=1505 audit(1282060402.205:9):  operation="profile_load" pid=655 name="/usr/bin/evince"
[   17.203264] type=1505 audit(1282060402.213:10):  operation="profile_load" pid=655 name="/usr/bin/evince-previewer"
[   17.208073] type=1505 audit(1282060402.221:11):  operation="profile_load" pid=655 name="/usr/bin/evince-thumbnailer"
[   17.318852] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   17.319106] acpi device:20: registered as cooling_device2
[   17.319236] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1f/LNXVIDEO:00/input/input5
[   17.319293] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   17.319499] lirc_dev: IR Remote Control driver registered, major 61 
[   17.340431] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[   17.378889] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   17.378892] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   17.383526] sdhci: Secure Digital Host Controller Interface driver
[   17.383529] sdhci: Copyright(c) Pierre Ossman
[   17.396138] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[   17.396721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.398404] cfg80211: Calling CRDA to update world regulatory domain
[   17.403071] cfg80211: World regulatory domain updated:
[   17.403074] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.403077] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.403079] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.403081] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.403084] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.403086] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.416064] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   17.601140] usb 3-2: configuration #1 chosen from 1 choice
[   17.676046] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[   17.826629] lirc_dev: lirc_register_driver: sample_rate: 0
[   17.831622] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb4:2
[   17.831690] usbcore: registered new interface driver lirc_mceusb
[   17.851817] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   17.928969] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   18.283517] nvidia: module license 'NVIDIA' taints kernel.
[   18.283522] Disabling lock debugging due to kernel taint
[   18.989381] yenta_cardbus 0000:06:0b.0: CardBus bridge found [1179:0001]
[   18.989399] yenta_cardbus 0000:06:0b.0: Enabling burst memory read transactions
[   18.989404] yenta_cardbus 0000:06:0b.0: Using CSCINT to route CSC interrupts to PCI
[   18.989406] yenta_cardbus 0000:06:0b.0: Routing CardBus interrupts to PCI
[   18.989411] yenta_cardbus 0000:06:0b.0: TI: mfunc 0x01aa1022, devctl 0x64
[   19.056551] Bluetooth: Core ver 2.15
[   19.056602] NET: Registered protocol family 31
[   19.056604] Bluetooth: HCI device and connection manager initialized
[   19.056607] Bluetooth: HCI socket layer initialized
[   19.121293] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.122117] usbcore: registered new interface driver btusb
[   19.244493] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   19.244657] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   19.244674] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.244686] nvidia 0000:01:00.0: setting latency timer to 64
[   19.244693] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.244842] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   19.245832] yenta_cardbus 0000:06:0b.0: ISA IRQ mask 0x0cf8, PCI irq 21
[   19.245835] yenta_cardbus 0000:06:0b.0: Socket status: 30000006
[   19.245840] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   19.245843] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x1000-0x1fff: clean.
[   19.246018] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge Memory window: 0x84000000 - 0x8dffffff
[   19.246020] yenta_cardbus 0000:06:0b.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   19.248410] sdhci-pci 0000:06:0b.3: SDHCI controller found [104c:803c] (rev 0)
[   19.248476] sdhci-pci 0000:06:0b.3: enabling device (0000 -> 0002)
[   19.248482] sdhci-pci 0000:06:0b.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   19.248578] Registered led device: mmc0::
[   19.248623] mmc0: SDHCI controller on PCI [0000:06:0b.3] using DMA
[   19.249167] tifm_7xx1 0000:06:0b.2: enabling device (0000 -> 0002)
[   19.249174] tifm_7xx1 0000:06:0b.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   19.291014] Bluetooth: L2CAP ver 2.14
[   19.291016] Bluetooth: L2CAP socket layer initialized
[   19.315816] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   19.315819] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   19.315911] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.315928] iwl3945 0000:05:00.0: setting latency timer to 64
[   19.384728] Console: switching to colour frame buffer device 80x30
[   19.387717] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.387719] Bluetooth: BNEP filters: protocol multicast
[   19.391164] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   19.391168] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.391273]   alloc irq_desc for 30 on node -1
[   19.391275]   alloc kstat_irqs on node -1
[   19.391305] iwl3945 0000:05:00.0: irq 30 for MSI/MSI-X
[   19.438514] Bridge firewalling registered
[   19.474082] Bluetooth: SCO (Voice Link) ver 0.6
[   19.474084] Bluetooth: SCO socket layer initialized
[   19.639236] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   19.649800] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   19.676599] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   19.704364] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.706403] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.707216] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.707933] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.710179] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.753461] Registered led device: iwl-phy0::radio
[   19.753481] Registered led device: iwl-phy0::assoc
[   19.753536] Registered led device: iwl-phy0::RX
[   19.753555] Registered led device: iwl-phy0::TX
[   19.763785] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.763818] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   19.763823] HDA Intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   19.763830]   alloc irq_desc for 22 on node -1
[   19.763832]   alloc kstat_irqs on node -1
[   19.763838] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.763871] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.764891] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.789106] Bluetooth: RFCOMM TTY layer initialized
[   19.789111] Bluetooth: RFCOMM socket layer initialized
[   19.789112] Bluetooth: RFCOMM ver 1.11
[   20.299039] [drm] Initialized drm 1.1.0 20060810
[   30.324073] ppdev: user-space parallel port driver
[   81.874175] wlan0: deauthenticating from 00:1d:68:e9:02:33 by local choice (reason=3)
[   81.875451] wlan0: direct probe to AP 00:1d:68:e9:02:33 (try 1)
[   81.877559] wlan0: direct probe responded
[   81.877566] wlan0: authenticate with AP 00:1d:68:e9:02:33 (try 1)
[   81.879842] wlan0: authenticated
[   81.879870] wlan0: associate with AP 00:1d:68:e9:02:33 (try 1)
[   81.882553] wlan0: RX AssocResp from 00:1d:68:e9:02:33 (capab=0x411 status=0 aid=3)
[   81.882559] wlan0: associated
[   81.885199] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   92.425018] wlan0: no IPv6 routers present
```

This is a bit much to read but i could not find anything related to a TV-Device. 
Please post the output of
```
lspci
```
also please try
```
sudo modprobe cx18
```
then 
```
dmesg | grep cx18
```

---

### Post by saedelaere on 2010-08-17
By the way this is the cx18 driver homepage [http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)

---

### Post by abdulq8 on 2010-08-17
> **saedelaere said:**
> This is a bit much to read but i could not find anything related to a TV-Device. 
Please post the output of
```
lspci
```
also please try
```
sudo modprobe cx18
```
then 
```
dmesg | grep cx18
```


thanks for responding fast

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7600] (rev a1)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
06:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

```
adminq8@adminq8-laptop:~$ sudo modprobe cx18
FATAL: Module cx18 not found.
adminq8@adminq8-laptop:~$ dmesg | grep cx18
adminq8@adminq8-laptop:~$ 

```

---

### Post by Yellow Pasque on 2010-08-17
You need to build the driver..
[http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver](http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver)

---

### Post by saedelaere on 2010-08-17
> **Temüjin said:**
> You need to build the driver..
[http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver](http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver)

But shouldn't this driver already be in the kernel?

---

### Post by abdulq8 on 2010-08-17
> **saedelaere said:**
> But shouldn't this driver already be in the kernel?

I am new to this so could you please explain to me what do i have to do ?
step by step 
command by command

---

### Post by saedelaere on 2010-08-17
> **abdulq8 said:**
> I am new to this so could you please explain to me what do i have to do ?
step by step 
command by command

In fact Temüjin already gave you the important link [http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver](http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver)

first get the driver, extract the files and then compile it on your system.

---

### Post by abdulq8 on 2010-08-18
> **saedelaere said:**
> In fact Temüjin already gave you the important link [http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver](http://www.ivtvdriver.org/index.php/Cx18#Obtaining_the_driver)

first get the driver, extract the files and then compile it on your system.


Can you tell what commands I need to use please

---

### Post by abdulq8 on 2010-08-18
> **abdulq8 said:**
> I am new to this so could you please explain to me what do i have to do ?
step by step 
command by command



```
adminq8@adminq8-laptop:~$ modprobe cx18
FATAL: Module cx18 not found.

```

---

### Post by saedelaere on 2010-08-19
Did you read what is on the link we gave you?

I will copy and paste for you :p

> The easiest way to build it is to get the tar.bz2 archive:

[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

Unpack, 'make menuconfig', 'make', 'make install' (as root), 'make unload' (as root) and run 'modprobe cx18'. 

So unpack, cd in the created directory from within a terminal and run the commands from above. Might be you need some basics like make, gcc... therefor install the packages build-essential and linux-headers

---

### Post by abdulq8 on 2010-08-19
> **saedelaere said:**
> Did you read what is on the link we gave you?

I will copy and paste for you :p



So unpack, cd in the created directory from within a terminal and run the commands from above. Might be you need some basics like make, gcc... therefor install the packages build-essential and linux-headers
 

every thing works fine except that last command

---

### Post by saedelaere on 2010-08-20
Paste the output of each command here. Don't forget to use the quote or code tags :)

---

### Post by abdulq8 on 2010-08-21
> **saedelaere said:**
> Paste the output of each command here. Don't forget to use the quote or code tags :)


```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-eff98a88caf3$ make menuconfig
make -C /home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l menuconfig
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'
/lib/modules/2.6.32-24-generic/build/scripts/kconfig/mconf ./Kconfig
#
# configuration written to .config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

./scripts/fix_kconfig.pl
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'

```



```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-eff98a88caf3$ make
make -C /home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l 
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'
./scripts/make_myconfig.pl
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
make[2]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-24-generic/build
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/mt20xx.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tda827x.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tda8290.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tda9887.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tea5761.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tea5767.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tuner-simple.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tuner-types.mod': Permission denied
rm: cannot remove `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/.tmp_versions/tuner-xc2028.mod': Permission denied
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'
make: *** [all] Error 2

```


```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-eff98a88caf3$ sudo make install
[sudo] password for adminq8: 
make -C /home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l install
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.32-24-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.32-24-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.32-24-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/2.6.32-24-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.32-24-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.32-24-generic 
make -C firmware install
make[2]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l/firmware'
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'

```


```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-eff98a88caf3$ sudo make unload
make -C /home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l unload
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'
scripts/rmmod.pl unload
found 0 modules
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-eff98a88caf3/v4l'

```


```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-eff98a88caf3$ modprobe cx18
FATAL: Module cx18 not found.

```

---

### Post by Yellow Pasque on 2010-08-21
Permission denied, eh?
Try:
```
sudo make
```

---

### Post by abdulq8 on 2010-08-22
> **Temüjin said:**
> Permission denied, eh?
Try:
```
sudo make
```



```
adminq8@adminq8-laptop:~/Downloads/v4l-dvb-9295d36ab66e$ sudo make
make -C /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l 
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l'
make[1]: Entering directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.32-24-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firmware'
make[2]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-24-generic/build
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tuner-xc2028.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tuner-simple.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tuner-types.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/mt20xx.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tda8290.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tea5767.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tea5761.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tda9887.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/tda827x.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-dvb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au0828-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au8522_dig.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au8522_decoder.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-pci.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-usb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-fe-tuner.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-sram.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-eeprom.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-misc.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-hw-filter.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/flexcop-dma.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-driver.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-if.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-risc.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-gpio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-input.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/bttv-audio-hook.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cpia2_v4l.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cpia2_usb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cpia2_core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-alsa-main.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-alsa-pcm.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-driver.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-firmware.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-gpio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-queue.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-streams.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-fileops.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-ioctl.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-controls.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-mailbox.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-audio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-irq.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-av-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-av-audio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-av-firmware.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-av-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-scb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-dvb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx18-io.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-audio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-avcore.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx231xx-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-dvb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-417.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-ioctl.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-ir.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-input.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23888-ir.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/netup-init.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cimax2.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/netup-eeprom.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx23885-f300.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx25840-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx25840-audio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx25840-firmware.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx25840-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-mpeg.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-tvaudio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-dsp.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cx88-input.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvbdev.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dmxdev.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_demux.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_filter.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_ca_en50221.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_frontend.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_net.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_ringbuffer.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb_math.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_hw.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_v4l.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_av.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_ca.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_ipack.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/av7110_ir.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/a800.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/af9005-remote.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/af9005.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/af9005-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/af9015.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/anysee.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/au6610.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/az6027.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/ce6230.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cinergyT2-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cinergyT2-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/cxusb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dib0700_core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dib0700_devices.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dibusb-common.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dibusb-mb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dibusb-mc.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/digitv.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dtt200u.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dtt200u-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dtv5100.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dw2102.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/ec168.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/friio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/friio-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/gl861.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/gp8psk.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/gp8psk-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/m920x.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/nova-t-usb2.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/opera1.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/ttusb2.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/umt-010.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/vp702x.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/vp702x-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/vp7045.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/vp7045-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-firmware.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-init.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-urb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-dvb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/dvb-usb-remote.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/usb-urb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/pt1.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/va1j5jf8007s.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/va1j5jf8007t.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-audio.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-video.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-i2c.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-cards.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-input.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/em28xx-vbi.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/et61x251_core.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-avc.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-ci.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-dvb.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-fe.o
  CC [M]  /home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.o
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_of':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_lock':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_read':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_write':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'start_iso':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'stop_iso':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: At top level:
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'fcp_request':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_probe':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: At top level:
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'node_update':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: At top level:
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/adminq8/Downloads/v4l-dvb-9295d36ab66e/v4l'
make: *** [all] Error 2

```

---

### Post by Yellow Pasque on 2010-08-23
I run into the same issue trying to compile on my Lucid VM. Let me work on it a bit..

---

### Post by Yellow Pasque on 2010-08-23
I'm having a lot of trouble compiling on the standard Lucid kernel, even when I disable most of the modules in the configuration. abdul, you may want to try a newer kernel, such as: 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Installing%20Mainline%20Kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds#Installing%20Mainline%20Kernels)

---

