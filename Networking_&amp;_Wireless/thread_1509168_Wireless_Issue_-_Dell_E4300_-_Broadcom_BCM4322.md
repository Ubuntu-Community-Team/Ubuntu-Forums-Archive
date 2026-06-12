---
title: "Wireless Issue - Dell E4300 - Broadcom BCM4322"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by -lodogg- on 2010-06-13
I was praying a standard install of Ubuntu 10.04 would work out of the gate and I was wrong:-\  Looks like everything is working except for my wireless adapter, so any help would be greatly appreciated.

---

Dell E4300

@nix-laptop:~$ lspci | grep "Wireless"

0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

@nix-laptop:~$ lsusb | grep "Wireless"

@nix-laptop:~$ lspci -nn | grep "Wireless"
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

@nix-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

@nix-laptop:~$ lsmod | grep "wlan"

@nix-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:cd:ac:25
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.7-7 ip=10.35.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff

@nix-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS

@nix-laptop:~$ uname -mr
2.6.32-21-generic x86_64

@nix-laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=0e061b24-2845-472c-a4e5-50a491db18c9 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dd04d400 (usable)
[    0.000000]  BIOS-e820: 00000000dd04d400 - 00000000dd04f400 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dd04f400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe60000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 800000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 0DDC00000 mask FFFC00000 uncachable
[    0.000000]   3 base 0DE000000 mask FFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000ddc00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdd04d max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000dd04d400 (usable)
[    0.000000]  modified: 00000000dd04d400 - 00000000dd04f400 (ACPI NVS)
[    0.000000]  modified: 00000000dd04f400 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe60000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000dd04d000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00dd000000 page 2M
[    0.000000]  00dd000000 - 00dd04d000 page 4k
[    0.000000] kernel direct mapping tables up to dd04d000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
[    0.000000] RAMDISK: 37800000 - 37fef896
[    0.000000] ACPI: RSDP 00000000000fb9f0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000dd051e00 00074 (v01 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: FACP 00000000dd051c9c 000F4 (v04 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000dd052400 06566 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000dd060c00 00040
[    0.000000] ACPI: HPET 00000000dd051f00 00038 (v01 DELL    M09     00000001 ASL  00000061)
[    0.000000] ACPI: ____ 00000000dd060400 00030 (v01 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: APIC 00000000dd052000 00068 (v01 DELL    M09     27D90507 ASL  00000047)
[    0.000000] ACPI: ASF! 00000000dd051c00 0006A (v32 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: MCFG 00000000dd051fc0 0003E (v16 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: TCPA 00000000dd052300 00032 (v01                 00000000 ASL  00000000)
[    0.000000] ACPI: SLIC 00000000dd05209c 00176 (v01 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000dd051bc0 00028 (v01 DELL    M09     27D90507 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dd050331 0066C (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
[    0.000000]   bootmap [0000000000012000 -  0000000000035fff] pages 24
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [0037800000 - 0037fef896]          RAMDISK ==> [0037800000 - 0037fef896]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a1e0]              BRK ==> [0001a2a000 - 0001a2a1e0]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dd04d
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1036263
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 886917 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dd04d000 - 00000000dd04e000
[    0.000000] PM: Registered nosave memory: 00000000dd04e000 - 00000000dd04f000
[    0.000000] PM: Registered nosave memory: 00000000dd04f000 - 00000000dd050000
[    0.000000] PM: Registered nosave memory: 00000000dd050000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe60000
[    0.000000] PM: Registered nosave memory: 00000000ffe60000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1020030
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=0e061b24-2845-472c-a4e5-50a491db18c9 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4000676k/4718592k available (5409k kernel code, 573540k absent, 144376k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2392.132 MHz processor.
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.26 BogoMIPS (lpj=23921320)
[    0.010033] Security Framework initialized
[    0.010051] AppArmor: AppArmor initialized
[    0.010384] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012480] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013451] Mount-cache hash table entries: 256
[    0.013584] Initializing cgroup subsys ns
[    0.013588] Initializing cgroup subsys cpuacct
[    0.013591] Initializing cgroup subsys memory
[    0.013599] Initializing cgroup subsys devices
[    0.013601] Initializing cgroup subsys freezer
[    0.013603] Initializing cgroup subsys net_cls
[    0.013621] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.013623] CPU: L2 cache: 6144K
[    0.013626] CPU 0/0x0 -> Node 0
[    0.013628] CPU: Physical Processor ID: 0
[    0.013629] CPU: Processor Core ID: 0
[    0.013633] mce: CPU supports 6 MCE banks
[    0.013640] CPU0: Thermal monitoring enabled (TM2)
[    0.013644] using mwait in idle threads.
[    0.013645] Performance Events: Core2 events, Intel PMU driver.
[    0.013650] ... version:                2
[    0.013652] ... bit width:              40
[    0.013653] ... generic registers:      2
[    0.013654] ... value mask:             000000ffffffffff
[    0.013656] ... max period:             000000007fffffff
[    0.013657] ... fixed-purpose events:   3
[    0.013659] ... event mask:             0000000700000003
[    0.016738] ACPI: Core revision 20090903
[    0.030008] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030013] ftrace: allocating 22518 entries in 89 pages
[    0.040046] Setting APIC routing to flat
[    0.040390] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.147896] CPU0: Intel(R) Core(TM)2 Duo CPU     P9400  @ 2.40GHz stepping 0a
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 6144K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.300026] CPU1: Intel(R) Core(TM)2 Duo CPU     P9400  @ 2.40GHz stepping 0a
[    0.300033] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.310015] Brought up 2 CPUs
[    0.310017] Total of 2 processors activated (9568.78 BogoMIPS).
[    0.310908] CPU0 attaching sched-domain:
[    0.310910]  domain 0: span 0-1 level MC
[    0.310913]   groups: 0 1
[    0.310918] CPU1 attaching sched-domain:
[    0.310919]  domain 0: span 0-1 level MC
[    0.310921]   groups: 1 0
[    0.311001] devtmpfs: initialized
[    0.311001] regulator: core version 0.5
[    0.311001] Time: 19:00:29  Date: 06/11/10
[    0.311001] NET: Registered protocol family 16
[    0.311001] Trying to unpack rootfs image as initramfs...
[    0.311001] ACPI: bus type pci registered
[    0.311001] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.311001] PCI: MCFG area at f8000000 reserved in E820
[    0.312295] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.312297] PCI: Using configuration type 1 for base access
[    0.320087] bio: create slab <bio-0> at 0
[    0.320799] ACPI: EC: Look up EC in DSDT
[    0.321013] ACPI: BIOS _OSI(Linux) query ignored
[    0.382267] ACPI: Interpreter enabled
[    0.382267] ACPI: (supports S0 S3 S4 S5)
[    0.382267] ACPI: Using IOAPIC for interrupt routing
[    0.487375] ACPI: EC: GPE = 0x11, I/O: command/status = 0x934, data = 0x930
[    0.488908] ACPI: No dock devices found.
[    0.508484] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.508574] pci 0000:00:02.0: reg 10 64bit mmio: [0xf6c00000-0xf6ffffff]
[    0.508581] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.508585] pci 0000:00:02.0: reg 20 io port: [0xef98-0xef9f]
[    0.508618] pci 0000:00:02.1: reg 10 64bit mmio: [0xf6b00000-0xf6bfffff]
[    0.508729] pci 0000:00:19.0: reg 10 32bit mmio: [0xf6ae0000-0xf6afffff]
[    0.508736] pci 0000:00:19.0: reg 14 32bit mmio: [0xf6adb000-0xf6adbfff]
[    0.508744] pci 0000:00:19.0: reg 18 io port: [0xefe0-0xefff]
[    0.508797] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.508802] pci 0000:00:19.0: PME# disabled
[    0.508866] pci 0000:00:1a.0: reg 20 io port: [0x6f60-0x6f7f]
[    0.508957] pci 0000:00:1a.1: reg 20 io port: [0x6f80-0x6f9f]
[    0.509046] pci 0000:00:1a.2: reg 20 io port: [0x6fa0-0x6fbf]
[    0.509138] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.509203] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.509208] pci 0000:00:1a.7: PME# disabled
[    0.509264] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6adc000-0xf6adffff]
[    0.509323] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.509327] pci 0000:00:1b.0: PME# disabled
[    0.509416] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.509420] pci 0000:00:1c.0: PME# disabled
[    0.509512] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.509517] pci 0000:00:1c.1: PME# disabled
[    0.509610] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.509614] pci 0000:00:1c.3: PME# disabled
[    0.509690] pci 0000:00:1d.0: reg 20 io port: [0x6f00-0x6f1f]
[    0.509781] pci 0000:00:1d.1: reg 20 io port: [0x6f20-0x6f3f]
[    0.509870] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.509963] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.510034] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.510039] pci 0000:00:1d.7: PME# disabled
[    0.510281] pci 0000:00:1f.2: reg 10 io port: [0x6e70-0x6e77]
[    0.510288] pci 0000:00:1f.2: reg 14 io port: [0x6e78-0x6e7b]
[    0.510295] pci 0000:00:1f.2: reg 18 io port: [0x6e80-0x6e87]
[    0.510302] pci 0000:00:1f.2: reg 1c io port: [0x6e88-0x6e8b]
[    0.510309] pci 0000:00:1f.2: reg 20 io port: [0x6ea0-0x6eaf]
[    0.510317] pci 0000:00:1f.2: reg 24 io port: [0x6e90-0x6e9f]
[    0.510383] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf6adaf00-0xf6adafff]
[    0.510401] pci 0000:00:1f.3: reg 20 io port: [0x1100-0x111f]
[    0.510463] pci 0000:00:1f.5: reg 10 io port: [0x6eb0-0x6eb7]
[    0.510470] pci 0000:00:1f.5: reg 14 io port: [0x6eb8-0x6ebb]
[    0.510478] pci 0000:00:1f.5: reg 18 io port: [0x6ec0-0x6ec7]
[    0.510485] pci 0000:00:1f.5: reg 1c io port: [0x6ec8-0x6ecb]
[    0.510492] pci 0000:00:1f.5: reg 20 io port: [0x6ee0-0x6eef]
[    0.510499] pci 0000:00:1f.5: reg 24 io port: [0xefa0-0xefaf]
[    0.510856] pci 0000:0c:00.0: reg 10 64bit mmio: [0xf69fc000-0xf69fffff]
[    0.510968] pci 0000:0c:00.0: supports D1 D2
[    0.510970] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.510978] pci 0000:0c:00.0: PME# disabled
[    0.511068] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6900000-0xf69fffff]
[    0.511132] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.511137] pci 0000:00:1c.3: bridge 32bit mmio: [0xf6600000-0xf68fffff]
[    0.511144] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.511188] pci 0000:02:01.0: reg 10 32bit mmio: [0xf65ff800-0xf65fffff]
[    0.511245] pci 0000:02:01.0: supports D1 D2
[    0.511247] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511251] pci 0000:02:01.0: PME# disabled
[    0.511293] pci 0000:02:01.1: reg 10 32bit mmio: [0xf65ff700-0xf65ff7ff]
[    0.511349] pci 0000:02:01.1: supports D1 D2
[    0.511350] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.511355] pci 0000:02:01.1: PME# disabled
[    0.511426] pci 0000:00:1e.0: transparent bridge
[    0.511433] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6500000-0xf65fffff]
[    0.511468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511730] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.511850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.511915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.511981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.524956] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    0.525067] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[    0.525176] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.525285] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
[    0.525394] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.525505] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.525616] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.525715] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.525824] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.525836] vgaarb: loaded
[    0.525938] SCSI subsystem initialized
[    0.526022] libata version 3.00 loaded.
[    0.526086] usbcore: registered new interface driver usbfs
[    0.526096] usbcore: registered new interface driver hub
[    0.526118] usbcore: registered new device driver usb
[    0.526251] ACPI: WMI: Mapper loaded
[    0.526253] PCI: Using ACPI for IRQ routing
[    0.526574] NetLabel: Initializing
[    0.526575] NetLabel:  domain hash size = 128
[    0.526577] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.526589] NetLabel:  unlabeled traffic allowed by default
[    0.526619] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.526624] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.530050] Switching to clocksource tsc
[    0.531609] AppArmor: AppArmor Filesystem Enabled
[    0.531618] pnp: PnP ACPI init
[    0.531626] ACPI: bus type pnp registered
[    0.596679] pnp: PnP ACPI: found 13 devices
[    0.596681] ACPI: ACPI bus type pnp unregistered
[    0.596695] system 00:05: ioport range 0xc80-0xcaf has been reserved
[    0.596698] system 00:05: ioport range 0xcc0-0xcff could not be reserved
[    0.596705] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.596710] system 00:09: ioport range 0xcb0-0xcbb has been reserved
[    0.596713] system 00:09: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.596718] system 00:0a: ioport range 0x900-0x92f has been reserved
[    0.596721] system 00:0a: ioport range 0x931-0x933 has been reserved
[    0.596723] system 00:0a: ioport range 0x935-0x97f has been reserved
[    0.596725] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.596727] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    0.596729] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    0.596734] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.596737] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    0.596739] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    0.596741] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    0.596744] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.596746] system 00:0b: ioport range 0x1100-0x111f has been reserved
[    0.596748] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    0.596750] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.596755] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.596758] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.596760] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.596762] system 00:0c: iomem range 0xe0000-0xfffff has been reserved
[    0.596765] system 00:0c: iomem range 0x100000-0xdd04d3ff could not be reserved
[    0.596767] system 00:0c: iomem range 0xdd04d400-0xddafffff could not be reserved
[    0.596770] system 00:0c: iomem range 0xddb00000-0xddbfffff has been reserved
[    0.596772] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.596775] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.596778] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.596780] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.596782] system 00:0c: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.596785] system 00:0c: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.596787] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.596790] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.596792] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.596795] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.596797] system 00:0c: iomem range 0xfed1c800-0xfed1cfff has been reserved
[    0.596800] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.596802] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.601544] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.601548] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.601554] pci 0000:00:1c.0:   MEM window: 0xf0200000-0xf03fffff
[    0.601559] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
[    0.601566] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.601569] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.601575] pci 0000:00:1c.1:   MEM window: 0xf6900000-0xf69fffff
[    0.601580] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
[    0.601587] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.601590] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.601595] pci 0000:00:1c.3:   MEM window: 0xf6600000-0xf68fffff
[    0.601600] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.601607] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.601608] pci 0000:00:1e.0:   IO window: disabled
[    0.601614] pci 0000:00:1e.0:   MEM window: 0xf6500000-0xf65fffff
[    0.601618] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.601637]   alloc irq_desc for 16 on node -1
[    0.601638]   alloc kstat_irqs on node -1
[    0.601644] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.601650] pci 0000:00:1c.0: setting latency timer to 64
[    0.601659]   alloc irq_desc for 17 on node -1
[    0.601660]   alloc kstat_irqs on node -1
[    0.601663] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.601668] pci 0000:00:1c.1: setting latency timer to 64
[    0.601677]   alloc irq_desc for 19 on node -1
[    0.601678]   alloc kstat_irqs on node -1
[    0.601681] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.601685] pci 0000:00:1c.3: setting latency timer to 64
[    0.601693] pci 0000:00:1e.0: setting latency timer to 64
[    0.601698] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.601701] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.601703] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.601705] pci_bus 0000:0b: resource 1 mem: [0xf0200000-0xf03fffff]
[    0.601707] pci_bus 0000:0b: resource 2 pref mem [0xf0400000-0xf05fffff]
[    0.601709] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
[    0.601711] pci_bus 0000:0c: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.601713] pci_bus 0000:0c: resource 2 pref mem [0xf0600000-0xf07fffff]
[    0.601716] pci_bus 0000:0d: resource 0 io:  [0xd000-0xdfff]
[    0.601717] pci_bus 0000:0d: resource 1 mem: [0xf6600000-0xf68fffff]
[    0.601719] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.601722] pci_bus 0000:02: resource 1 mem: [0xf6500000-0xf65fffff]
[    0.601724] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.601726] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.601758] NET: Registered protocol family 2
[    0.601908] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.603004] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.606731] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.607252] TCP: Hash tables configured (established 524288 bind 65536)
[    0.607254] TCP reno registered
[    0.607356] NET: Registered protocol family 1
[    0.607375] pci 0000:00:02.0: Boot video device
[    0.607590] Simple Boot Flag at 0x79 set to 0x1
[    0.607754] Scanning for low memory corruption every 60 seconds
[    0.607889] audit: initializing netlink socket (disabled)
[    0.607901] type=2000 audit(1276282828.599:1): initialized
[    0.616170] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.617366] VFS: Disk quotas dquot_6.5.2
[    0.617414] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.617899] fuse init (API version 7.13)
[    0.617970] msgmni has been set to 7813
[    0.618142] alg: No test for stdrng (krng)
[    0.618186] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.618189] io scheduler noop registered
[    0.618190] io scheduler anticipatory registered
[    0.618192] io scheduler deadline registered
[    0.618223] io scheduler cfq registered (default)
[    0.618371]   alloc irq_desc for 24 on node -1
[    0.618373]   alloc kstat_irqs on node -1
[    0.618383] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.618394] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.618538]   alloc irq_desc for 25 on node -1
[    0.618540]   alloc kstat_irqs on node -1
[    0.618548] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.618558] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.618696]   alloc irq_desc for 26 on node -1
[    0.618698]   alloc kstat_irqs on node -1
[    0.618706] pcieport 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.618716] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.618805] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.618893] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.619025] ACPI: AC Adapter [AC] (on-line)
[    0.619090] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.621173] Freeing initrd memory: 8126k freed
[    0.621185] ACPI: Lid Switch [LID]
[    0.621227] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.621233] ACPI: Power Button [PBTN]
[    0.621272] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.621275] ACPI: Sleep Button [SBTN]
[    0.622023] ACPI: SSDT 00000000dd05099d 00281 (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.622485] ACPI: SSDT 00000000dd050df5 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.622839] Monitor-Mwait will be used to enter C-1 state
[    0.622881] Monitor-Mwait will be used to enter C-2 state
[    0.622908] Monitor-Mwait will be used to enter C-3 state
[    0.622914] Marking TSC unstable due to TSC halts in idle
[    0.623020] processor LNXCPU:00: registered as cooling_device0
[    0.623498] ACPI: SSDT 00000000dd050c1e 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.623853] ACPI: SSDT 00000000dd0513bb 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.624236] Switching to clocksource hpet
[    0.624442] processor LNXCPU:01: registered as cooling_device1
[    0.654176] thermal LNXTHERM:01: registered as thermal_zone0
[    0.654183] ACPI: Thermal Zone [THM] (66 C)
[    0.654413] ACPI: Battery Slot [BAT1] (battery absent)
[    0.655560] Linux agpgart interface v0.103
[    0.655589] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.656715] brd: module loaded
[    0.657113] loop: module loaded
[    0.657185] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.657273] ata_piix 0000:00:1f.2: version 2.13
[    0.657289] ata_piix 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.657294] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.657338] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.657399] scsi0 : ata_piix
[    0.657459] scsi1 : ata_piix
[    0.658929] ata1: SATA max UDMA/133 cmd 0x6e70 ctl 0x6e78 bmdma 0x6ea0 irq 19
[    0.658934] ata2: SATA max UDMA/133 cmd 0x6e80 ctl 0x6e88 bmdma 0x6ea8 irq 19
[    0.658957] ata_piix 0000:00:1f.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.658964] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.745274] ACPI: Battery Slot [BAT0] (battery present)
[    0.810032] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.810075] scsi2 : ata_piix
[    0.810125] scsi3 : ata_piix
[    0.810273] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 19
[    0.810277] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 19
[    0.810543] Fixed MDIO Bus: probed
[    0.810569] PPP generic driver version 2.4.2
[    0.810599] tun: Universal TUN/TAP device driver, 1.6
[    0.810601] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.810677] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.810695]   alloc irq_desc for 22 on node -1
[    0.810696]   alloc kstat_irqs on node -1
[    0.810702] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.810716] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.810720] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.810746] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.810777] ehci_hcd 0000:00:1a.7: debug port 1
[    0.814665] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.814678] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.830017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.830104] usb usb1: configuration #1 chosen from 1 choice
[    0.830128] hub 1-0:1.0: USB hub found
[    0.830134] hub 1-0:1.0: 6 ports detected
[    0.830190]   alloc irq_desc for 20 on node -1
[    0.830192]   alloc kstat_irqs on node -1
[    0.830195] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.830204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.830207] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.830235] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.830263] ehci_hcd 0000:00:1d.7: debug port 1
[    0.834135] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.834145] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.850014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.850069] usb usb2: configuration #1 chosen from 1 choice
[    0.850093] hub 2-0:1.0: USB hub found
[    0.850098] hub 2-0:1.0: 6 ports detected
[    0.850147] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.850158] uhci_hcd: USB Universal Host Controller Interface driver
[    0.850176] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.850181] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.850185] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.850213] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.850238] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    0.850312] usb usb3: configuration #1 chosen from 1 choice
[    0.850332] hub 3-0:1.0: USB hub found
[    0.850337] hub 3-0:1.0: 2 ports detected
[    0.850378]   alloc irq_desc for 21 on node -1
[    0.850380]   alloc kstat_irqs on node -1
[    0.850383] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.850391] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.850394] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.850418] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.850448] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    0.850521] usb usb4: configuration #1 chosen from 1 choice
[    0.850541] hub 4-0:1.0: USB hub found
[    0.850546] hub 4-0:1.0: 2 ports detected
[    0.850583] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.850589] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.850592] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.850618] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.850642] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    0.850715] usb usb5: configuration #1 chosen from 1 choice
[    0.850738] hub 5-0:1.0: USB hub found
[    0.850743] hub 5-0:1.0: 2 ports detected
[    0.850780] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.850786] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.850789] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.850817] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.850841] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    0.850920] usb usb6: configuration #1 chosen from 1 choice
[    0.850943] hub 6-0:1.0: USB hub found
[    0.850948] hub 6-0:1.0: 2 ports detected
[    0.850985] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.850991] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.850994] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.851024] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.851048] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    0.851124] usb usb7: configuration #1 chosen from 1 choice
[    0.851144] hub 7-0:1.0: USB hub found
[    0.851149] hub 7-0:1.0: 2 ports detected
[    0.851190] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.851196] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.851199] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.851222] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.851247] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.851324] usb usb8: configuration #1 chosen from 1 choice
[    0.851344] hub 8-0:1.0: USB hub found
[    0.851349] hub 8-0:1.0: 2 ports detected
[    0.851423] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.851984] i8042.c: Warning: Keylock active.
[    0.855188] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.855193] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.855286] mice: PS/2 mouse device common for all mice
[    0.855400] rtc_cmos 00:03: RTC can wake from S4
[    0.855433] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.855461] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.855558] device-mapper: uevent: version 1.0.3
[    0.855644] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.855718] device-mapper: multipath: version 1.1.0 loaded
[    0.855721] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.855944] cpuidle: using governor ladder
[    0.856036] cpuidle: using governor menu
[    0.856308] TCP cubic registered
[    0.856407] NET: Registered protocol family 10
[    0.856773] lo: Disabled Privacy Extensions
[    0.857002] NET: Registered protocol family 17
[    0.857612] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.857802] PM: Resume from disk failed.
[    0.857813] registered taskstats version 1
[    0.858418]   Magic number: 14:801:40
[    0.858423] bdi 7:5: hash matches
[    0.858434] system 00:0c: hash matches
[    0.858517] rtc_cmos 00:03: setting system clock to 2010-06-11 19:00:29 UTC (1276282829)
[    0.858520] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.858521] EDD information not available.
[    1.171256] ata3: SATA link down (SStatus 4 SControl 300)
[    1.171332] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.171509] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.182436] ata4: SATA link down (SStatus 4 SControl 300)
[    1.193119] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-U633A, DW10, max UDMA/100
[    1.193127] ata2.00: applying bridge limits
[    1.221802] ata1.00: ATA-8: ST980411ASG, DE17, max UDMA/133
[    1.221806] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.232905] ata2.00: configured for UDMA/100
[    1.299018] ata1.00: configured for UDMA/133
[    1.299132] scsi 0:0:0:0: Direct-Access     ATA      ST980411ASG      DE17 PQ: 0 ANSI: 5
[    1.299226] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.299371] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.299407] sd 0:0:0:0: [sda] Write Protect is off
[    1.299409] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.299429] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.299526]  sda:
[    1.303082] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-U633A DW10 PQ: 0 ANSI: 5
[    1.317758]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.318600] Uniform CD-ROM driver Revision: 3.20
[    1.318692] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.318744] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.344255]  sda5 >
[    1.344518] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.344531] Freeing unused kernel memory: 876k freed
[    1.344805] Write protecting the kernel read-only data: 7680k
[    1.357972] udev: starting version 151
[    1.443928] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.443940] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.444098] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.444100] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.444129] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.444136] e1000e 0000:00:19.0: setting latency timer to 64
[    1.444241]   alloc irq_desc for 27 on node -1
[    1.444243]   alloc kstat_irqs on node -1
[    1.444255] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    1.445854] ohci1394 0000:02:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.504620] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f65ff800-f65fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.520341] ssb: ERROR: PLL init unknown for device 4322
[    1.520344] ssb: ERROR: PMU resource config unknown for device 4322
[    1.560153] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    1.570078] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.582598] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:24:e8:cd:ac:25
[    1.582600] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.582626] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 3002ff-0ff
[    1.729573] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.764830] usb 5-1: configuration #0 chosen from 1 choice
[    1.764833] usb 5-1: config 0 descriptor??
[    2.820445] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc00037b96a21]
[    8.971710] udev: starting version 151
[    8.993141] lp: driver loaded but no devices found
[    8.994811] Adding 3227640k swap on /dev/sda5.  Priority:-1 extents:1 across:3227640k 
[    9.042897] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    9.044728] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    9.193184] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    9.201288] type=1505 audit(1276297237.834:2):  operation="profile_load" pid=630 name="/sbin/dhclient3"
[    9.201942] type=1505 audit(1276297237.834:3):  operation="profile_load" pid=630 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.202295] type=1505 audit(1276297237.834:4):  operation="profile_load" pid=630 name="/usr/lib/connman/scripts/dhclient-script"
[    9.222671] [drm] Initialized drm 1.1.0 20060810
[    9.230147] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.240084] cfg80211: Calling CRDA to update world regulatory domain
[    9.260786] sdhci: Secure Digital Host Controller Interface driver
[    9.260789] sdhci: Copyright(c) Pierre Ossman
[    9.273660] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.273665] i915 0000:00:02.0: setting latency timer to 64
[    9.276649] cfg80211: World regulatory domain updated:
[    9.276652] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.276655] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.276657] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.276659] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.276661] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.276663] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.292697] sdhci-pci 0000:02:01.1: SDHCI controller found [1180:0822] (rev 22)
[    9.292715]   alloc irq_desc for 18 on node -1
[    9.292717]   alloc kstat_irqs on node -1
[    9.292724] sdhci-pci 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    9.294815] Registered led device: mmc0::
[    9.295845] mmc0: SDHCI controller on PCI [0000:02:01.1] using DMA
[    9.296325] input: Dell WMI hotkeys as /devices/virtual/input/input5
[    9.300693] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[    9.303608] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    9.303611] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.306241]   alloc irq_desc for 28 on node -1
[    9.306243]   alloc kstat_irqs on node -1
[    9.306251] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    9.306256] [drm] set up 31M of stolen space
[    9.460199] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 8, Type 4, Revision 4)
[    9.476712] b43: probe of ssb0:0 failed with error -95
[    9.476749] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    9.562407] type=1505 audit(1276297238.194:5):  operation="profile_load" pid=858 name="/usr/share/gdm/guest-session/Xsession"
[    9.563677] type=1505 audit(1276297238.204:6):  operation="profile_replace" pid=859 name="/sbin/dhclient3"
[    9.564589] type=1505 audit(1276297238.204:7):  operation="profile_replace" pid=859 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.564907] type=1505 audit(1276297238.204:8):  operation="profile_replace" pid=859 name="/usr/lib/connman/scripts/dhclient-script"
[    9.567509] type=1505 audit(1276297238.204:9):  operation="profile_load" pid=860 name="/usr/bin/evince"
[    9.567850] dell-wmi: Unknown key ffd0 pressed
[    9.575028] type=1505 audit(1276297238.214:10):  operation="profile_load" pid=860 name="/usr/bin/evince-previewer"
[    9.579397] type=1505 audit(1276297238.214:11):  operation="profile_load" pid=860 name="/usr/bin/evince-thumbnailer"
[    9.802729] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    9.862553] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    9.863046] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.976103] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
[    9.993098] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.164193] fb0: inteldrmfb frame buffer device
[   10.164195] registered panic notifier
[   10.192560] acpi device:33: registered as cooling_device2
[   10.193557] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   10.193615] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   10.193663] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   10.193754] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   10.193829] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   10.193998] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.194041] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.194063] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.195777] vga16fb: initializing
[   10.195780] vga16fb: mapped to 0xffff8800000a0000
[   10.195783] vga16fb: not registering due to another framebuffer present
[   10.357377] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   10.382783] Console: switching to colour frame buffer device 160x50
[   10.391151] input: HDA Intel Mic at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.391229] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.391287] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.391336] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.718370] dell-wmi: Unknown key ffd1 pressed
[ 2845.665861] dell-wmi: Unknown key ffd0 pressed
[122051.775637] dell-wmi: Unknown key ffd1 pressed
[123861.672516] dell-wmi: Unknown key ffd0 pressed
[164261.347883] dell-wmi: Unknown key ffd1 pressed
[166233.671277] dell-wmi: Unknown key ffd0 pressed
[170944.370988] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[170944.370990] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[170944.371467] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[170946.752285] dell-wmi: Unknown key ffd1 pressed
[170954.660045] eth0: no IPv6 routers present
@nix-laptop:~$

---

### Post by -lodogg- on 2010-06-14
After applying every update in the world when I rebooted I received a prompt saying there was a driver available directly from the vendor!  I applied the new driver and I think all is well now.  Can someone send me a link on how to configure WPA2 from the CLI?

Does this look correct? eth1?

@nix-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:165
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by -lodogg- on 2010-06-14
I can see my wireless network called "test" but I don't have a clue on how to configure a basic WPA/AES setup.

@nix-laptop:/etc/network$ sudo iwlist eth1 scanning 

eth1      Scan completed :
          Cell 01 - Address: 00:1F:90:F4:54:54
                    ESSID:"5ULA3"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-77 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

          Cell 02 - Address: 00:18:01:F4:97:0B
                    ESSID:"TM0R3"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

          Cell 03 - Address: 90:84:0D:EA:1F:1F
                    ESSID:"mjr1"
                    Mode:Managed
                    Frequency=2.417 GHz (Channel 2)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


 	Cell 04 - Address: 00:14:F1:AE:4A:C0
                    ESSID:"test"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:4/5  Signal level:-59 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by -lodogg- on 2010-06-15
I was able to setup my WPA2 AES network through the GUI, however it would be nice to know how to do it through the CLI.

-lo

---

