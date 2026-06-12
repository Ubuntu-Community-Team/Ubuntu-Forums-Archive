---
title: "b43 mac suspend failed"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by yaami on 2010-08-09
Hi all,
I'm using linux Mint 9, (broadcom wireless), because Ubuntu and Mint are very similar, I'm asking this question here.
```
lspci | grep -i network
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
```
```
uname -r
2.6.32-24-generic

```
I had this problem and was not able to connect to the internet twice. I tried rebooting and it worked the third time. The dmesg had this line **_*b43 mac suspend failed*_**. 
I'm posting my complete dmesg here,
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
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf50000 (usable)
[    0.000000]  BIOS-e820: 000000003bf50000 - 000000003bf65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf65000 - 000000003bf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf66000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3bf50 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
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
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bf50000 (usable)
[    0.000000]  modified: 000000003bf50000 - 000000003bf65000 (ACPI data)
[    0.000000]  modified: 000000003bf65000 - 000000003bf66000 (ACPI NVS)
[    0.000000]  modified: 000000003bf66000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2c2a8000 - 2cfbb0fd
[    0.000000] ACPI: RSDP 000f8250 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 3bf5c0ce 0006C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3bf649ba 000F4 (v03 NVIDIA MCP67-M  06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 3bf5c13a 0880C (v01 NVIDIA    MCP67 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 3bf65fc0 00040
[    0.000000] ACPI: TCPA 3bf64aae 00032 (v01 Phoeni  x       06040000  TL  00000000)
[    0.000000] ACPI: SRAT 3bf64ae0 000A0 (v01 AMD    HAMMER   06040000 AMD  00000001)
[    0.000000] ACPI: SSDT 3bf64b80 00206 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 3bf64d86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 3bf64dc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 3bf64dfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3bf64e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 3bf64e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 71MB HIGHMEM available.
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
[    0.000000]   #4 [002c2a8000 - 002cfbb0fd]          RAMDISK ==> [002c2a8000 - 002cfbb0fd]
[    0.000000]   #5 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #6 [00008dc000 - 00008df150]              BRK ==> [00008dc000 - 00008df150]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f8220] f8220
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bf50
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0003bf50
[    0.000000] On node 0 totalpages: 245482
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 143 pages used for memmap
[    0.000000]   HighMem zone: 18115 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243563
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-24-generic root=UUID=23414442-650e-4943-ba51-3731a247ef90 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4911680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bf50)
[    0.000000] Memory: 946644k/982336k available (4679k kernel code, 34892k reserved, 2116k data, 660k init, 73032k highmem)
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
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1900.292 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3800.58 BogoMIPS (lpj=7601168)
[    0.004023] Security Framework initialized
[    0.004044] AppArmor: AppArmor initialized
[    0.004052] Mount-cache hash table entries: 512
[    0.004179] Initializing cgroup subsys ns
[    0.004183] Initializing cgroup subsys cpuacct
[    0.004187] Initializing cgroup subsys memory
[    0.004194] Initializing cgroup subsys devices
[    0.004197] Initializing cgroup subsys freezer
[    0.004200] Initializing cgroup subsys net_cls
[    0.004219] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004222] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004225] CPU: Physical Processor ID: 0
[    0.004227] CPU: Processor Core ID: 0
[    0.004231] mce: CPU supports 5 MCE banks
[    0.004241] using C1E aware idle routine
[    0.004249] Performance Events: AMD PMU driver.
[    0.004255] ... version:                0
[    0.004258] ... bit width:              48
[    0.004260] ... generic registers:      4
[    0.004262] ... value mask:             0000ffffffffffff
[    0.004265] ... max period:             00007fffffffffff
[    0.004267] ... fixed-purpose events:   0
[    0.004269] ... event mask:             000000000000000f
[    0.004273] Checking 'hlt' instruction... OK.
[    0.022326] ACPI: Core revision 20090903
[    0.036010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036016] ftrace: allocating 21780 entries in 43 pages
[    0.040088] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040560] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083197] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.168106] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.168136] Brought up 2 CPUs
[    0.168139] Total of 2 processors activated (7600.95 BogoMIPS).
[    0.168135] System has AMD C1E enabled
[    0.168135] Switch to broadcast mode on CPU1
[    0.168373] CPU0 attaching sched-domain:
[    0.168377]  domain 0: span 0-1 level MC
[    0.168380]   groups: 0 1
[    0.168385] CPU1 attaching sched-domain:
[    0.168388]  domain 0: span 0-1 level MC
[    0.168391]   groups: 1 0
[    0.168476] Switch to broadcast mode on CPU0
[    0.168476] devtmpfs: initialized
[    0.168476] regulator: core version 0.5
[    0.168476] Time:  0:10:18  Date: 08/10/10
[    0.168476] NET: Registered protocol family 16
[    0.168476] Trying to unpack rootfs image as initramfs...
[    0.168476] EISA bus registered
[    0.168476] ACPI: bus type pci registered
[    0.168476] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.168476] PCI: MCFG area at e0000000 reserved in E820
[    0.168476] PCI: Using MMCONFIG for extended config space
[    0.168476] PCI: Using configuration type 1 for base access
[    0.172117] bio: create slab <bio-0> at 0
[    0.172938] ACPI: EC: Look up EC in DSDT
[    0.175666] ACPI: BIOS _OSI(Linux) query ignored
[    0.176496] ACPI: Interpreter enabled
[    0.176508] ACPI: (supports S0 S3 S4 S5)
[    0.176529] ACPI: Using IOAPIC for interrupt routing
[    0.183721] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.184095] ACPI: No dock devices found.
[    0.184316] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.184537] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.184550] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.184555] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.184576] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.184582] pci 0000:00:01.1: PME# disabled
[    0.184640] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.184722] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.184747] pci 0000:00:02.0: supports D1 D2
[    0.184749] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184754] pci 0000:00:02.0: PME# disabled
[    0.184778] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.184807] pci 0000:00:02.1: supports D1 D2
[    0.184810] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184815] pci 0000:00:02.1: PME# disabled
[    0.184843] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.184868] pci 0000:00:04.0: supports D1 D2
[    0.184870] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184875] pci 0000:00:04.0: PME# disabled
[    0.184899] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.184929] pci 0000:00:04.1: supports D1 D2
[    0.184931] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.184936] pci 0000:00:04.1: PME# disabled
[    0.184972] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.185012] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.185041] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.185045] pci 0000:00:07.0: PME# disabled
[    0.185113] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.185118] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.185123] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.185128] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.185133] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.185138] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.185190] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.185195] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.185200] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.185206] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.185229] pci 0000:00:0a.0: supports D1 D2
[    0.185232] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185237] pci 0000:00:0a.0: PME# disabled
[    0.185280] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185284] pci 0000:00:0c.0: PME# disabled
[    0.185324] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185328] pci 0000:00:0d.0: PME# disabled
[    0.185352] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.185359] pci 0000:00:12.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.185366] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.185372] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.185495] pci 0000:02:05.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.185530] pci 0000:02:05.0: supports D1 D2
[    0.185533] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185537] pci 0000:02:05.0: PME# disabled
[    0.185563] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.185598] pci 0000:02:05.1: supports D1 D2
[    0.185601] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185606] pci 0000:02:05.1: PME# disabled
[    0.185632] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.185666] pci 0000:02:05.2: supports D1 D2
[    0.185669] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185674] pci 0000:02:05.2: PME# disabled
[    0.185700] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.185734] pci 0000:02:05.3: supports D1 D2
[    0.185737] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185742] pci 0000:02:05.3: PME# disabled
[    0.185768] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.185802] pci 0000:02:05.4: supports D1 D2
[    0.185805] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.185810] pci 0000:02:05.4: PME# disabled
[    0.185843] pci 0000:00:08.0: transparent bridge
[    0.185848] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.185887] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.185891] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.185896] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.185937] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf6003fff]
[    0.185984] pci 0000:03:00.0: supports D1 D2
[    0.186035] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.186045] pci_bus 0000:00: on NUMA node 0
[    0.186050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.186148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.186173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.186210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.220168] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.220365] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.220557] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.220747] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.220938] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.221129] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.221321] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.221512] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.221703] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.221894] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.222085] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.222277] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.222471] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.222661] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.222851] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.223044] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.223236] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.223427] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.223618] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.223742] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
[    0.223750] vgaarb: loaded
[    0.223874] SCSI subsystem initialized
[    0.223978] libata version 3.00 loaded.
[    0.224071] usbcore: registered new interface driver usbfs
[    0.224085] usbcore: registered new interface driver hub
[    0.224112] usbcore: registered new device driver usb
[    0.224281] ACPI: WMI: Mapper loaded
[    0.224283] PCI: Using ACPI for IRQ routing
[    0.224460] NetLabel: Initializing
[    0.224462] NetLabel:  domain hash size = 128
[    0.224464] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224479] NetLabel:  unlabeled traffic allowed by default
[    0.224515] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.224521] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.232040] Switching to clocksource hpet
[    0.233985] AppArmor: AppArmor Filesystem Enabled
[    0.234006] pnp: PnP ACPI init
[    0.234024] ACPI: bus type pnp registered
[    0.237089] pnp: PnP ACPI: found 12 devices
[    0.237091] ACPI: ACPI bus type pnp unregistered
[    0.237095] PnPBIOS: Disabled by ACPI PNP
[    0.237109] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.237116] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.237119] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.237122] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.237126] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.237129] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.237132] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.237139] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.237142] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.237151] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.237155] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.237158] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.237162] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.237165] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.271885] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.271888] pci 0000:00:08.0:   IO window: disabled
[    0.271893] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.271897] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.271902] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.271906] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.271910] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.271914] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.271920] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.271922] pci 0000:00:0d.0:   IO window: disabled
[    0.271926] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.271930] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.271940] pci 0000:00:08.0: setting latency timer to 64
[    0.271947] pci 0000:00:0c.0: setting latency timer to 64
[    0.271953] pci 0000:00:0d.0: setting latency timer to 64
[    0.271958] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.271962] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.271966] pci_bus 0000:02: resource 1 mem: [0xf6100000-0xf61fffff]
[    0.271969] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.271972] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.271976] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.271979] pci_bus 0000:04: resource 1 mem: [0xf2000000-0xf3ffffff]
[    0.271983] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.271987] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf60fffff]
[    0.272041] NET: Registered protocol family 2
[    0.272143] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.272514] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.273182] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.273504] TCP: Hash tables configured (established 131072 bind 65536)
[    0.273507] TCP reno registered
[    0.273605] NET: Registered protocol family 1
[    0.273766] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.273820] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.273879] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.273945] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.274015] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.274090] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.274097] pci 0000:00:12.0: Boot video device
[    0.274136] Simple Boot Flag at 0x36 set to 0x1
[    0.274320] cpufreq-nforce2: No nForce2 chipset.
[    0.274348] Scanning for low memory corruption every 60 seconds
[    0.274484] audit: initializing netlink socket (disabled)
[    0.274495] type=2000 audit(1281399018.273:1): initialized
[    0.285251] highmem bounce pool size: 64 pages
[    0.285257] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.286879] VFS: Disk quotas dquot_6.5.2
[    0.286939] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.287532] fuse init (API version 7.13)
[    0.287623] msgmni has been set to 1707
[    0.287854] alg: No test for stdrng (krng)
[    0.287913] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.287916] io scheduler noop registered
[    0.287919] io scheduler anticipatory registered
[    0.287921] io scheduler deadline registered
[    0.287966] io scheduler cfq registered (default)
[    0.288130]   alloc irq_desc for 24 on node -1
[    0.288133]   alloc kstat_irqs on node -1
[    0.288142] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.288148] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.288225]   alloc irq_desc for 25 on node -1
[    0.288227]   alloc kstat_irqs on node -1
[    0.288232] pcieport 0000:00:0d.0: irq 25 for MSI/MSI-X
[    0.288236] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.288300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.288325] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.288868] ACPI: AC Adapter [ACAD] (on-line)
[    0.288965] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.288970] ACPI: Sleep Button [SLPB]
[    0.289016] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.289285] ACPI: Lid Switch [LID]
[    0.289350] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.289354] ACPI: Power Button [PWRB]
[    0.289402] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.289406] ACPI: Power Button [PWRF]
[    0.289736] ACPI: processor limited to max C-state 1
[    0.289760] processor LNXCPU:00: registered as cooling_device0
[    0.289866] processor LNXCPU:01: registered as cooling_device1
[    0.293151] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)
[    0.294818] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.296176] brd: module loaded
[    0.296679] loop: module loaded
[    0.296778] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.296962] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.297374] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    0.297380]   alloc irq_desc for 23 on node -1
[    0.297383]   alloc kstat_irqs on node -1
[    0.297394] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    0.297413] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.297421] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.297741] Fixed MDIO Bus: probed
[    0.297779] PPP generic driver version 2.4.2
[    0.297820] tun: Universal TUN/TAP device driver, 1.6
[    0.297822] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.297910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.298215] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.298219]   alloc irq_desc for 22 on node -1
[    0.298221]   alloc kstat_irqs on node -1
[    0.298229] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.298246] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.298250] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.298287] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.298313] ehci_hcd 0000:00:02.1: debug port 1
[    0.298322] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.298344] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    0.298747] isapnp: Scanning for PnP cards...
[    0.347669] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.347789] usb usb1: configuration #1 chosen from 1 choice
[    0.347823] hub 1-0:1.0: USB hub found
[    0.347832] hub 1-0:1.0: 7 ports detected
[    0.348224] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    0.348228] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    0.348238] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.348241] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.348276] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.348297] ehci_hcd 0000:00:04.1: debug port 1
[    0.348305] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.348311] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    0.391773] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.391861] usb usb2: configuration #1 chosen from 1 choice
[    0.391888] hub 2-0:1.0: USB hub found
[    0.391896] hub 2-0:1.0: 2 ports detected
[    0.391944] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.392250] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.392254]   alloc irq_desc for 18 on node -1
[    0.392257]   alloc kstat_irqs on node -1
[    0.392265] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.392275] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.392279] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.392315] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.392347] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    0.481251] usb usb3: configuration #1 chosen from 1 choice
[    0.481279] hub 3-0:1.0: USB hub found
[    0.481289] hub 3-0:1.0: 7 ports detected
[    0.481618] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    0.481623] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    0.481632] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.481635] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.481669] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.481682] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    0.550524] usb usb4: configuration #1 chosen from 1 choice
[    0.550558] hub 4-0:1.0: USB hub found
[    0.550570] hub 4-0:1.0: 2 ports detected
[    0.550633] uhci_hcd: USB Universal Host Controller Interface driver
[    0.550731] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.579011] Freeing initrd memory: 13388k freed
[    0.589980] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.589994] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.590176] mice: PS/2 mouse device common for all mice
[    0.591455] rtc_cmos 00:07: RTC can wake from S4
[    0.591509] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.591549] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.591677] device-mapper: uevent: version 1.0.3
[    0.591798] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.591872] device-mapper: multipath: version 1.1.0 loaded
[    0.591876] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.592022] EISA: Probing bus 0 at eisa.0
[    0.592028] Cannot allocate resource for EISA slot 1
[    0.592034] Cannot allocate resource for EISA slot 3
[    0.592037] Cannot allocate resource for EISA slot 4
[    0.592050] EISA: Detected 0 cards.
[    0.592137] cpuidle: using governor ladder
[    0.592139] cpuidle: using governor menu
[    0.592609] TCP cubic registered
[    0.592778] NET: Registered protocol family 10
[    0.593257] lo: Disabled Privacy Extensions
[    0.593598] NET: Registered protocol family 17
[    0.593630] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[    0.593675] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[    0.593678] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[    0.593680] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[    0.593683] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    0.593724] Using IPI No-Shortcut mode
[    0.593810] PM: Resume from disk failed.
[    0.593823] registered taskstats version 1
[    0.594178]   Magic number: 6:375:152
[    0.594198] bdi 1:4: hash matches
[    0.594291] rtc_cmos 00:07: setting system clock to 2010-08-10 00:10:19 UTC (1281399019)
[    0.594295] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.594298] EDD information not available.
[    0.610926] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.623316] ACPI: Battery Slot [BAT0] (battery present)
[    0.655878] isapnp: No Plug & Play device found
[    0.908388] Freeing unused kernel memory: 660k freed
[    0.908878] Write protecting the kernel text: 4680k
[    0.908919] Write protecting the kernel read-only data: 1840k
[    0.930443] udev: starting version 151
[    0.968060] usb 3-4: new low speed USB device using ohci_hcd and address 2
[    1.048514] pata_amd 0000:00:06.0: version 0.4.1
[    1.048569] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.058771] acpi device:23: registered as cooling_device2
[    1.058922] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.058978] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[    1.059479] scsi0 : pata_amd
[    1.065839] scsi1 : pata_amd
[    1.066305] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    1.066309] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    1.076951] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.077328] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.077335]   alloc irq_desc for 20 on node -1
[    1.077338]   alloc kstat_irqs on node -1
[    1.077349] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.077355] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.080365] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[    1.080372]   alloc irq_desc for 19 on node -1
[    1.080374]   alloc kstat_irqs on node -1
[    1.080385] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[    1.080394] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    1.140085] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.177299] usb 3-4: configuration #1 chosen from 1 choice
[    1.252310] ata1.00: ATAPI: Slimtype DVD A  DS8A1P, CH71, max MWDMA2
[    1.252340] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.292294] ata1.00: configured for MWDMA2
[    1.296107] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CH71 PQ: 0 ANSI: 5
[    1.306796] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.306799] Uniform CD-ROM driver Revision: 3.20
[    1.306918] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.306984] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.307076] ata2: port disabled. ignoring.
[    1.308569] vga16fb: initializing
[    1.308574] vga16fb: mapped to 0xc00a0000
[    1.308640] fb0: VGA16 VGA frame buffer device
[    1.312225] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    1.312573] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.312587] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.317622] usbcore: registered new interface driver hiddev
[    1.332524] input: HID 04d9:0499 as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input7
[    1.332632] generic-usb 0003:04D9:0499.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:0499] on usb-0000:00:02.0-4/input0
[    1.332661] usbcore: registered new interface driver usbhid
[    1.332694] usbhid: v2.6:USB HID core driver
[    1.370067] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.516649] Console: switching to colour frame buffer device 80x30
[    1.597130] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:74:c6:1c
[    1.597136] forcedeth 0000:00:0a.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.597165] ahci 0000:00:09.0: version 3.0
[    1.597181] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.597228]   alloc irq_desc for 26 on node -1
[    1.597231]   alloc kstat_irqs on node -1
[    1.597240] ahci 0000:00:09.0: irq 26 for MSI/MSI-X
[    1.597246] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    1.597315] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.597320] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    1.597325] ahci 0000:00:09.0: setting latency timer to 64
[    1.597789] scsi2 : ahci
[    1.597889] scsi3 : ahci
[    1.597972] scsi4 : ahci
[    1.598042] scsi5 : ahci
[    1.598184] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 26
[    1.598189] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 26
[    1.598193] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 26
[    1.598197] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 26
[    1.620034] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.850508] usb 4-1: configuration #1 chosen from 1 choice
[    1.916035] ata6: SATA link down (SStatus 0 SControl 300)
[    1.916066] ata5: SATA link down (SStatus 0 SControl 300)
[    1.916080] ata4: SATA link down (SStatus 0 SControl 300)
[    2.080027] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.080639] ata3.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
[    2.080643] ata3.00: 312581808 sectors, multi 16: LBA48 
[    2.081352] ata3.00: configured for UDMA/100
[    2.081467] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
[    2.081650] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.081768] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.081814] sd 2:0:0:0: [sda] Write Protect is off
[    2.081818] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.081842] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.081999]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.134410] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.640181] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0095334000]
[    2.727205] xor: automatically using best checksumming function: pIII_sse
[    2.744010]    pIII_sse  :  5768.000 MB/sec
[    2.744013] xor: using function: pIII_sse (5768.000 MB/sec)
[    2.747231] device-mapper: dm-raid45: initialized v0.2594b
[    2.902481] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   18.004763] udev: starting version 151
[   18.048854] Adding 2047992k swap on /dev/sda5.  Priority:-1 extents:1 across:2047992k 
[   18.141886] lp: driver loaded but no devices found
[   18.319909] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   18.319934] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   18.429655] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.434731] Linux agpgart interface v0.103
[   18.501304] nvidia: module license 'NVIDIA' taints kernel.
[   18.501309] Disabling lock debugging due to kernel taint
[   19.398225] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   19.476997] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   19.675165] ricoh-mmc: Ricoh MMC Controller disabling driver
[   19.675169] ricoh-mmc: Copyright(c) Philip Langdale
[   19.675199] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   19.675214] ricoh-mmc: Controller is now disabled.
[   19.695406] sdhci: Secure Digital Host Controller Interface driver
[   19.695411] sdhci: Copyright(c) Pierre Ossman
[   19.697403] cfg80211: Calling CRDA to update world regulatory domain
[   19.726629] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   19.745066] cfg80211: World regulatory domain updated:
[   19.745070] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.745074] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.745078] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.745081] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.745084] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.745087] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.850871] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   19.850878]   alloc irq_desc for 21 on node -1
[   19.850880]   alloc kstat_irqs on node -1
[   19.850892] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   19.850895] hda_intel: Disable MSI for Nvidia chipset
[   19.850942] HDA Intel 0000:00:07.0: setting latency timer to 64
[   19.857720] phy0: Selected rate control algorithm 'minstrel'
[   19.858491] Registered led device: b43-phy0::tx
[   19.858509] Registered led device: b43-phy0::rx
[   19.858529] Registered led device: b43-phy0::radio
[   19.858603] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   19.874005] Bluetooth: Core ver 2.15
[   19.874139] NET: Registered protocol family 31
[   19.874142] Bluetooth: HCI device and connection manager initialized
[   19.874146] Bluetooth: HCI socket layer initialized
[   19.876177] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.876297] usbcore: registered new interface driver btusb
[   19.879786] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   19.880130] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   19.880145] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   19.887963] Registered led device: mmc0::
[   19.889101] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   19.952676] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   20.260660] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   20.260668]   alloc irq_desc for 16 on node -1
[   20.260671]   alloc kstat_irqs on node -1
[   20.260682] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   20.260689] nvidia 0000:00:12.0: setting latency timer to 64
[   20.260695] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.260972] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   20.848529] kjournald starting.  Commit interval 5 seconds
[   20.848779] EXT3 FS on sda1, internal journal
[   20.848785] EXT3-fs: mounted filesystem with ordered data mode.
[   21.259296]   alloc irq_desc for 27 on node -1
[   21.259300]   alloc kstat_irqs on node -1
[   21.259311] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   21.259512] eth0: no link during initialization.
[   21.260124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.320034] b43 ssb0:0: firmware: requesting b43/ucode13.fw
[   21.338220] b43 ssb0:0: firmware: requesting b43/b0g0initvals13.fw
[   21.480041] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   21.717542] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.229768] Bluetooth: L2CAP ver 2.14
[   22.229772] Bluetooth: L2CAP socket layer initialized
[   22.236550] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.236555] Bluetooth: BNEP filters: protocol multicast
[   22.245362] Bridge firewalling registered
[   22.252838] Bluetooth: SCO (Voice Link) ver 0.6
[   22.252842] Bluetooth: SCO socket layer initialized
[   22.270196] ppdev: user-space parallel port driver
[   23.729266] Bluetooth: RFCOMM TTY layer initialized
[   23.729272] Bluetooth: RFCOMM socket layer initialized
[   23.729275] Bluetooth: RFCOMM ver 1.11
[   31.152147] wlan0: deauthenticating from 00:23:69:b8:92:52 by local choice (reason=3)
[   31.152242] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 1)
[   31.352050] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 2)
[   31.552071] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 3)
[   31.752029] wlan0: direct probe to AP 00:23:69:b8:92:52 timed out
[b][   41.676029] b43-phy0 ERROR: MAC suspend failed
[   42.064027] b43-phy0 ERROR: MAC suspend failed
[   42.452029] b43-phy0 ERROR: MAC suspend failed
[   42.840029] b43-phy0 ERROR: MAC suspend failed
[   43.228028] b43-phy0 ERROR: MAC suspend failed
[   43.616027] b43-phy0 ERROR: MAC suspend failed
[   44.004033] b43-phy0 ERROR: MAC suspend failed
[   44.392029] b43-phy0 ERROR: MAC suspend failed
[   44.780029] b43-phy0 ERROR: MAC suspend failed
[   45.168027] b43-phy0 ERROR: MAC suspend failed
[   46.924031] __ratelimit: 3 callbacks suppressed
[   46.924035] b43-phy0 ERROR: MAC suspend failed
[   47.256027] b43-phy0 ERROR: MAC suspend failed
[   51.928030] b43-phy0 ERROR: MAC suspend failed
[   52.248027] b43-phy0 ERROR: MAC suspend failed
[   52.668029] b43-phy0 ERROR: MAC suspend failed
[   53.056028] b43-phy0 ERROR: MAC suspend failed
[   53.444028] b43-phy0 ERROR: MAC suspend failed
[   53.832028] b43-phy0 ERROR: MAC suspend failed
[   54.220028] b43-phy0 ERROR: MAC suspend failed
[   54.608029] b43-phy0 ERROR: MAC suspend failed
[   54.996032] b43-phy0 ERROR: MAC suspend failed
[   55.384031] b43-phy0 ERROR: MAC suspend failed
[   55.772028] b43-phy0 ERROR: MAC suspend failed
[   56.160030] b43-phy0 ERROR: MAC suspend failed
[   58.304032] __ratelimit: 4 callbacks suppressed
[   58.304036] b43-phy0 ERROR: MAC suspend failed
[   58.636027] b43-phy0 ERROR: MAC suspend failed
[   63.308030] b43-phy0 ERROR: MAC suspend failed
[   63.756028] b43-phy0 ERROR: MAC suspend failed
[   64.144030] b43-phy0 ERROR: MAC suspend failed
[   64.532027] b43-phy0 ERROR: MAC suspend failed
[   64.920027] b43-phy0 ERROR: MAC suspend failed
[   65.308028] b43-phy0 ERROR: MAC suspend failed
[   65.696027] b43-phy0 ERROR: MAC suspend failed
[   66.084027] b43-phy0 ERROR: MAC suspend failed
[   66.668029] b43-phy0 ERROR: MAC suspend failed
[   67.056027] b43-phy0 ERROR: MAC suspend failed
[   67.444028] b43-phy0 ERROR: MAC suspend failed
[   69.396031] __ratelimit: 4 callbacks suppressed
[   69.396035] b43-phy0 ERROR: MAC suspend failed
[   69.728028] b43-phy0 ERROR: MAC suspend failed
[   74.400029] b43-phy0 ERROR: MAC suspend failed
[   74.848027] b43-phy0 ERROR: MAC suspend failed
[   75.236027] b43-phy0 ERROR: MAC suspend failed
[   75.624027] b43-phy0 ERROR: MAC suspend failed
[   76.300028] b43-phy0 ERROR: MAC suspend failed
[   76.688028] b43-phy0 ERROR: MAC suspend failed
[   77.076027] b43-phy0 ERROR: MAC suspend failed
[   77.464027] b43-phy0 ERROR: MAC suspend failed
[   77.852029] b43-phy0 ERROR: MAC suspend failed
[   78.240027] b43-phy0 ERROR: MAC suspend failed
[   78.628027] b43-phy0 ERROR: MAC suspend failed
[   80.328031] __ratelimit: 3 callbacks suppressed
[   80.328035] b43-phy0 ERROR: MAC suspend failed
[   84.504042] Clocksource tsc unstable (delta = -217712880 ns)
[   85.196043] b43-phy0 ERROR: MAC suspend failed
[   85.584042] b43-phy0 ERROR: MAC suspend failed
[   85.972043] b43-phy0 ERROR: MAC suspend failed
[   86.360044] b43-phy0 ERROR: MAC suspend failed
[   86.748045] b43-phy0 ERROR: MAC suspend failed
[   87.136044] b43-phy0 ERROR: MAC suspend failed
[   87.600041] b43-phy0 ERROR: MAC suspend failed
[   87.988046] b43-phy0 ERROR: MAC suspend failed
[   88.380060] b43-phy0 ERROR: MAC suspend failed
[   90.472034] __ratelimit: 4 callbacks suppressed[/b]
[   90.472044] b43-phy0 ERROR: MAC suspend failed
[   95.664024] b43-phy0 ERROR: MAC suspend failed
[   96.048048] b43-phy0 ERROR: MAC suspend failed
[   96.608048] b43-phy0 ERROR: MAC suspend failed
[   96.996050] b43-phy0 ERROR: MAC suspend failed
[   97.385050] b43-phy0 ERROR: MAC suspend failed
[   97.772053] b43-phy0 ERROR: MAC suspend failed
[   98.164125] b43-phy0 ERROR: MAC suspend failed
[   98.556055] b43-phy0 ERROR: MAC suspend failed
[   98.944052] b43-phy0 ERROR: MAC suspend failed
[  100.992043] __ratelimit: 4 callbacks suppressed
[  100.992052] b43-phy0 ERROR: MAC suspend failed
[  101.324052] b43-phy0 ERROR: MAC suspend failed
[  106.396058] b43-phy0 ERROR: MAC suspend failed
[  106.784278] b43-phy0 ERROR: MAC suspend failed
[  107.176046] b43-phy0 ERROR: MAC suspend failed
[  107.564076] b43-phy0 ERROR: MAC suspend failed
[  107.952049] b43-phy0 ERROR: MAC suspend failed
[  108.340048] b43-phy0 ERROR: MAC suspend failed
[  108.728049] b43-phy0 ERROR: MAC suspend failed
[  109.116043] b43-phy0 ERROR: MAC suspend failed
[  109.572051] b43-phy0 ERROR: MAC suspend failed
[  110.029031] b43-phy0 ERROR: MAC suspend failed
[  115.700021] __ratelimit: 2 callbacks suppressed
[  115.700024] b43-phy0 ERROR: MAC suspend failed
[  116.088061] b43-phy0 ERROR: MAC suspend failed
[  116.476071] b43-phy0 ERROR: MAC suspend failed
[  116.865058] b43-phy0 ERROR: MAC suspend failed
[  117.252046] b43-phy0 ERROR: MAC suspend failed
[  117.640043] b43-phy0 ERROR: MAC suspend failed
[  118.272034] b43-phy0 ERROR: MAC suspend failed
[  118.660049] b43-phy0 ERROR: MAC suspend failed
[  119.048048] b43-phy0 ERROR: MAC suspend failed
[  119.436039] b43-phy0 ERROR: MAC suspend failed
[  121.140037] __ratelimit: 3 callbacks suppressed
[  121.140041] b43-phy0 ERROR: MAC suspend failed
[  126.232051] b43-phy0 ERROR: MAC suspend failed
[  126.620047] b43-phy0 ERROR: MAC suspend failed
[  127.008071] b43-phy0 ERROR: MAC suspend failed
[  127.396050] b43-phy0 ERROR: MAC suspend failed
[  127.784053] b43-phy0 ERROR: MAC suspend failed
[  128.172049] b43-phy0 ERROR: MAC suspend failed
[  128.560063] b43-phy0 ERROR: MAC suspend failed
[  128.948071] b43-phy0 ERROR: MAC suspend failed
[  134.876046] b43-phy0 ERROR: MAC suspend failed
[  135.268044] b43-phy0 ERROR: MAC suspend failed
[  135.656054] b43-phy0 ERROR: MAC suspend failed
[  136.044051] b43-phy0 ERROR: MAC suspend failed
[  136.432051] b43-phy0 ERROR: MAC suspend failed
[  136.820042] b43-phy0 ERROR: MAC suspend failed
[  137.476052] b43-phy0 ERROR: MAC suspend failed
[  137.864051] b43-phy0 ERROR: MAC suspend failed
[  138.252063] b43-phy0 ERROR: MAC suspend failed
[  138.640047] b43-phy0 ERROR: MAC suspend failed
[  140.340052] __ratelimit: 3 callbacks suppressed
[  140.340061] b43-phy0 ERROR: MAC suspend failed
[  145.348052] b43-phy0 ERROR: MAC suspend failed
[  145.736048] b43-phy0 ERROR: MAC suspend failed
[  146.124047] b43-phy0 ERROR: MAC suspend failed
[  146.512050] b43-phy0 ERROR: MAC suspend failed
[  147.048053] b43-phy0 ERROR: MAC suspend failed

```

This is part of the above message which shows the problem with b43. 
```
[   31.152147] wlan0: deauthenticating from 00:23:69:b8:92:52 by local choice (reason=3)
[   31.152242] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 1)
[   31.352050] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 2)
[   31.552071] wlan0: direct probe to AP 00:23:69:b8:92:52 (try 3)
[   31.752029] wlan0: direct probe to AP 00:23:69:b8:92:52 timed out
[   41.676029] b43-phy0 ERROR: MAC suspend failed
[   42.064027] b43-phy0 ERROR: MAC suspend failed
[   42.452029] b43-phy0 ERROR: MAC suspend failed
[   42.840029] b43-phy0 ERROR: MAC suspend failed
[   43.228028] b43-phy0 ERROR: MAC suspend failed
[   43.616027] b43-phy0 ERROR: MAC suspend failed
[   44.004033] b43-phy0 ERROR: MAC suspend failed
[   44.392029] b43-phy0 ERROR: MAC suspend failed
[   44.780029] b43-phy0 ERROR: MAC suspend failed
[   45.168027] b43-phy0 ERROR: MAC suspend failed
[   46.924031] __ratelimit: 3 callbacks suppressed
[   46.924035] b43-phy0 ERROR: MAC suspend failed
[   47.256027] b43-phy0 ERROR: MAC suspend failed
[   51.928030] b43-phy0 ERROR: MAC suspend failed
[   52.248027] b43-phy0 ERROR: MAC suspend failed
[   52.668029] b43-phy0 ERROR: MAC suspend failed
[   53.056028] b43-phy0 ERROR: MAC suspend failed
[   53.444028] b43-phy0 ERROR: MAC suspend failed
[   53.832028] b43-phy0 ERROR: MAC suspend failed
[   54.220028] b43-phy0 ERROR: MAC suspend failed
[   54.608029] b43-phy0 ERROR: MAC suspend failed
[   54.996032] b43-phy0 ERROR: MAC suspend failed
[   55.384031] b43-phy0 ERROR: MAC suspend failed
[   55.772028] b43-phy0 ERROR: MAC suspend failed
[   56.160030] b43-phy0 ERROR: MAC suspend failed
[   58.304032] __ratelimit: 4 callbacks suppressed
[   58.304036] b43-phy0 ERROR: MAC suspend failed
[   58.636027] b43-phy0 ERROR: MAC suspend failed
[   63.308030] b43-phy0 ERROR: MAC suspend failed
[   63.756028] b43-phy0 ERROR: MAC suspend failed
[   64.144030] b43-phy0 ERROR: MAC suspend failed
[   64.532027] b43-phy0 ERROR: MAC suspend failed
[   64.920027] b43-phy0 ERROR: MAC suspend failed
[   65.308028] b43-phy0 ERROR: MAC suspend failed
[   65.696027] b43-phy0 ERROR: MAC suspend failed
[   66.084027] b43-phy0 ERROR: MAC suspend failed
[   66.668029] b43-phy0 ERROR: MAC suspend failed
[   67.056027] b43-phy0 ERROR: MAC suspend failed
[   67.444028] b43-phy0 ERROR: MAC suspend failed
[   69.396031] __ratelimit: 4 callbacks suppressed
[   69.396035] b43-phy0 ERROR: MAC suspend failed
[   69.728028] b43-phy0 ERROR: MAC suspend failed
[   74.400029] b43-phy0 ERROR: MAC suspend failed
[   74.848027] b43-phy0 ERROR: MAC suspend failed
[   75.236027] b43-phy0 ERROR: MAC suspend failed
[   75.624027] b43-phy0 ERROR: MAC suspend failed
[   76.300028] b43-phy0 ERROR: MAC suspend failed
[   76.688028] b43-phy0 ERROR: MAC suspend failed
[   77.076027] b43-phy0 ERROR: MAC suspend failed
[   77.464027] b43-phy0 ERROR: MAC suspend failed
[   77.852029] b43-phy0 ERROR: MAC suspend failed
[   78.240027] b43-phy0 ERROR: MAC suspend failed
[   78.628027] b43-phy0 ERROR: MAC suspend failed
[   80.328031] __ratelimit: 3 callbacks suppressed
[   80.328035] b43-phy0 ERROR: MAC suspend failed
[   84.504042] Clocksource tsc unstable (delta = -217712880 ns)
[   85.196043] b43-phy0 ERROR: MAC suspend failed
[   85.584042] b43-phy0 ERROR: MAC suspend failed
[   85.972043] b43-phy0 ERROR: MAC suspend failed
[   86.360044] b43-phy0 ERROR: MAC suspend failed
[   86.748045] b43-phy0 ERROR: MAC suspend failed
[   87.136044] b43-phy0 ERROR: MAC suspend failed
[   87.600041] b43-phy0 ERROR: MAC suspend failed
[   87.988046] b43-phy0 ERROR: MAC suspend failed
[   88.380060] b43-phy0 ERROR: MAC suspend failed
[   90.472034] __ratelimit: 4 callbacks suppressed
[   90.472044] b43-phy0 ERROR: MAC suspend failed
[   95.664024] b43-phy0 ERROR: MAC suspend failed
[   96.048048] b43-phy0 ERROR: MAC suspend failed
[   96.608048] b43-phy0 ERROR: MAC suspend failed
[   96.996050] b43-phy0 ERROR: MAC suspend failed
[   97.385050] b43-phy0 ERROR: MAC suspend failed
[   97.772053] b43-phy0 ERROR: MAC suspend failed
[   98.164125] b43-phy0 ERROR: MAC suspend failed
[   98.556055] b43-phy0 ERROR: MAC suspend failed
[   98.944052] b43-phy0 ERROR: MAC suspend failed
[  100.992043] __ratelimit: 4 callbacks suppressed
[  100.992052] b43-phy0 ERROR: MAC suspend failed
[  101.324052] b43-phy0 ERROR: MAC suspend failed
[  106.396058] b43-phy0 ERROR: MAC suspend failed
[  106.784278] b43-phy0 ERROR: MAC suspend failed
[  107.176046] b43-phy0 ERROR: MAC suspend failed
[  107.564076] b43-phy0 ERROR: MAC suspend failed
[  107.952049] b43-phy0 ERROR: MAC suspend failed
[  108.340048] b43-phy0 ERROR: MAC suspend failed
[  108.728049] b43-phy0 ERROR: MAC suspend failed
[  109.116043] b43-phy0 ERROR: MAC suspend failed
[  109.572051] b43-phy0 ERROR: MAC suspend failed
[  110.029031] b43-phy0 ERROR: MAC suspend failed
[  115.700021] __ratelimit: 2 callbacks suppressed
[  115.700024] b43-phy0 ERROR: MAC suspend failed
[  116.088061] b43-phy0 ERROR: MAC suspend failed
[  116.476071] b43-phy0 ERROR: MAC suspend failed
[  116.865058] b43-phy0 ERROR: MAC suspend failed
[  117.252046] b43-phy0 ERROR: MAC suspend failed
[  117.640043] b43-phy0 ERROR: MAC suspend failed
[  118.272034] b43-phy0 ERROR: MAC suspend failed
[  118.660049] b43-phy0 ERROR: MAC suspend failed
[  119.048048] b43-phy0 ERROR: MAC suspend failed
[  119.436039] b43-phy0 ERROR: MAC suspend failed
[  121.140037] __ratelimit: 3 callbacks suppressed
[  121.140041] b43-phy0 ERROR: MAC suspend failed
[  126.232051] b43-phy0 ERROR: MAC suspend failed
[  126.620047] b43-phy0 ERROR: MAC suspend failed
[  127.008071] b43-phy0 ERROR: MAC suspend failed
[  127.396050] b43-phy0 ERROR: MAC suspend failed
[  127.784053] b43-phy0 ERROR: MAC suspend failed
[  128.172049] b43-phy0 ERROR: MAC suspend failed
[  128.560063] b43-phy0 ERROR: MAC suspend failed
[  128.948071] b43-phy0 ERROR: MAC suspend failed
[  134.876046] b43-phy0 ERROR: MAC suspend failed
[  135.268044] b43-phy0 ERROR: MAC suspend failed
[  135.656054] b43-phy0 ERROR: MAC suspend failed
[  136.044051] b43-phy0 ERROR: MAC suspend failed
[  136.432051] b43-phy0 ERROR: MAC suspend failed
[  136.820042] b43-phy0 ERROR: MAC suspend failed
[  137.476052] b43-phy0 ERROR: MAC suspend failed
[  137.864051] b43-phy0 ERROR: MAC suspend failed
[  138.252063] b43-phy0 ERROR: MAC suspend failed
[  138.640047] b43-phy0 ERROR: MAC suspend failed
[  140.340052] __ratelimit: 3 callbacks suppressed
[  140.340061] b43-phy0 ERROR: MAC suspend failed
[  145.348052] b43-phy0 ERROR: MAC suspend failed
[  145.736048] b43-phy0 ERROR: MAC suspend failed
[  146.124047] b43-phy0 ERROR: MAC suspend failed
[  146.512050] b43-phy0 ERROR: MAC suspend failed
[  147.048053] b43-phy0 ERROR: MAC suspend failed

```
Has anyone experienced this problem before and how to fix this if it should show up again. 
Hope this info helps someone to help me resolve this issue. 

Thanks.

---

