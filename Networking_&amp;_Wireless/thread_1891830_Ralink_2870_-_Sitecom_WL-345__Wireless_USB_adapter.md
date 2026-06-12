---
title: "Ralink 2870 - Sitecom WL-345  Wireless USB adapter 300N X3"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by flyshoppa on 2011-12-06
Hi everyone.. My first post here even tough I follow this forum almost daily...
that's the problem: 

I had a PCI network card: a D-Link DWL-G510 working via mrv8k51 driver in ndiswrapper.
Then I bought a Sitecom WL-345 Wireless USB adapter since my new graphic card exceeded its PCIE slot. 

I tried to install that evil piece of hardware without any result....

I first tried with ndiswrapper and downloaded USB(RT2870/RT2770/RT307X/RT2070 RT357X/RT3370/RT8070/RT537X) Windows driver (from [here]("http://www.ralinktech.com/en/04_support/license.php?sn=5007")) and it just not worked...
then I googled and I found in many sites instruction on how to complile the kernel module for that dongle. 
For example [this]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html") or [this one]("http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/") ... mmm I forgot [this]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html") as well.

The result is... 
Compiling was successful, rt2870sta module seems to be loaded by the kernel nonethless any 

```
iwconfig
```will return 
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```I even tried to blacklist ndiswrapper (and remove it from /etc/modules)
Please help me! Thanks in advantage
Davide
-------------------------------
```
uname -a 
Linux desktop 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux

``````

dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-35-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 (Ubuntu 2.6.32-35.78-generic 2.6.32.46+drm33.20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-35-generic root=UUID=cc570ec1-14c6-420a-ae7e-cab15f156f81 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffb0000 - 00000000bffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffb0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffb0000 (usable)
[    0.000000]  modified: 00000000bffb0000 - 00000000bffc0000 (ACPI data)
[    0.000000]  modified: 00000000bffc0000 - 00000000bfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffb0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffb0000 page 4k
[    0.000000] kernel direct mapping tables up to bffb0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 1G
[    0.000000] kernel direct mapping tables up to 140000000 @ 12000-13000
[    0.000000] RAMDISK: 377f3000 - 37fefa65
[    0.000000] ACPI: RSDP 00000000000fb0c0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bffb0000 0003C (v01 A_M_I  OEMRSDT  11000824 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffb0200 00084 (v02 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffb0450 049B4 (v01  ASR73 ASR73141 00000141 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bffc0000 00040
[    0.000000] ACPI: APIC 00000000bffb0390 00080 (v01 A_M_I  OEMAPIC  11000824 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffb0410 0003C (v01 A_M_I  OEMMCFG  11000824 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffc0040 00060 (v01 A_M_I  AMI_OEM  11000824 MSFT 00000097)
[    0.000000] ACPI: AAFT 00000000bffb4e10 00027 (v01 A_M_I  OEMAAFT  11000824 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffb4e40 00544 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  000000000003efff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a30ac4]    TEXT DATA BSS ==> [0001000000 - 0001a30ac4]
[    0.000000]   #3 [00377f3000 - 0037fefa65]          RAMDISK ==> [00377f3000 - 0037fefa65]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a31000 - 0001a31133]              BRK ==> [0001a31000 - 0001a31133]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffb0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048383
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3826 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767976 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bffb0000 - 00000000bffc0000
[    0.000000] PM: Registered nosave memory: 00000000bffc0000 - 00000000bfff0000
[    0.000000] PM: Registered nosave memory: 00000000bfff0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 00000000ff380000
[    0.000000] PM: Registered nosave memory: 00000000ff380000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u524288
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030362
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-35-generic root=UUID=cc570ec1-14c6-420a-ae7e-cab15f156f81 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 4051312k/5242880k available (5415k kernel code, 1049348k absent, 142220k reserved, 2978k data, 888k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2210.059 MHz processor.
[    0.020006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.11 BogoMIPS (lpj=22100560)
[    0.020033] Security Framework initialized
[    0.020053] AppArmor: AppArmor initialized
[    0.020550] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.031340] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.032189] Mount-cache hash table entries: 256
[    0.032331] Initializing cgroup subsys ns
[    0.032335] Initializing cgroup subsys cpuacct
[    0.032340] Initializing cgroup subsys memory
[    0.032348] Initializing cgroup subsys devices
[    0.032351] Initializing cgroup subsys freezer
[    0.032353] Initializing cgroup subsys net_cls
[    0.032374] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.032377] CPU: L2 Cache: 512K (64 bytes/line)
[    0.032380] CPU 0/0x0 -> Node 0
[    0.032384] tseg: 0000000000
[    0.032402] CPU: Physical Processor ID: 0
[    0.032404] CPU: Processor Core ID: 0
[    0.032407] mce: CPU supports 6 MCE banks
[    0.032418] using C1E aware idle routine
[    0.032420] Performance Events: AMD PMU driver.
[    0.032425] ... version:                0
[    0.032427] ... bit width:              48
[    0.032428] ... generic registers:      4
[    0.032430] ... value mask:             0000ffffffffffff
[    0.032432] ... max period:             00007fffffffffff
[    0.032434] ... fixed-purpose events:   0
[    0.032435] ... event mask:             000000000000000f
[    0.034110] ACPI: Core revision 20090903
[    0.042668] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.042673] ftrace: allocating 22484 entries in 89 pages
[    0.049549] Setting APIC routing to flat
[    0.050000] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.150297] CPU0: AMD Phenom(tm) 9550 Quad-Core Processor stepping 03
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.310114] CPU1: AMD Phenom(tm) 9550 Quad-Core Processor stepping 03
[    0.310123] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320077] Booting processor 2 APIC 0x2 ip 0x6000
[    0.030000] Initializing CPU#2
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 2/0x2 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 2
[    0.480092] CPU2: AMD Phenom(tm) 9550 Quad-Core Processor stepping 03
[    0.480100] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.490069] Booting processor 3 APIC 0x3 ip 0x6000
[    0.030000] Initializing CPU#3
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 3/0x3 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 3
[    0.650081] CPU3: AMD Phenom(tm) 9550 Quad-Core Processor stepping 03
[    0.650088] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.660012] Brought up 4 CPUs
[    0.660015] Total of 4 processors activated (17702.84 BogoMIPS).
[    0.661428] CPU0 attaching sched-domain:
[    0.661435]  domain 0: span 0-3 level MC
[    0.661437]   groups: 0 1 2 3
[    0.661445] CPU1 attaching sched-domain:
[    0.661446]  domain 0: span 0-3 level MC
[    0.661448]   groups: 1 2 3 0
[    0.661453] CPU2 attaching sched-domain:
[    0.661454]  domain 0: span 0-3 level MC
[    0.661456]   groups: 2 3 0 1
[    0.661460] CPU3 attaching sched-domain:
[    0.661461]  domain 0: span 0-3 level MC
[    0.661463]   groups: 3 0 1 2
[    0.661581] devtmpfs: initialized
[    0.661581] regulator: core version 0.5
[    0.661581] Time: 19:03:43  Date: 12/06/11
[    0.661581] NET: Registered protocol family 16
[    0.661581] node 0 link 0: io port [1000, ffffff]
[    0.661581] TOM: 00000000c0000000 aka 3072M
[    0.661581] Fam 10h mmconf [e0000000, e00fffff]
[    0.661581] node 0 link 0: mmio [e0000000, efffffff] ==> [e0100000, efffffff]
[    0.661581] node 0 link 0: mmio [a0000, bffff]
[    0.661581] node 0 link 0: mmio [c0000000, fe0bffff] ==> [c0000000, dfffffff] and [e0100000, fe0bffff]
[    0.661581] TOM2: 0000000140000000 aka 5120M
[    0.661581] bus: [00,07] on node 0 link 0
[    0.661581] Trying to unpack rootfs image as initramfs...
[    0.661581] bus: 00 index 0 io port: [0, ffff]
[    0.661581] bus: 00 index 1 mmio: [e0100000, ffffffff]
[    0.661581] bus: 00 index 2 mmio: [a0000, bffff]
[    0.661581] bus: 00 index 3 mmio: [c0000000, dfffffff]
[    0.661581] bus: 00 index 4 mmio: [140000000, fcffffffff]
[    0.661581] ACPI: bus type pci registered
[    0.661581] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.661581] PCI: Not using MMCONFIG.
[    0.661581] PCI: Using configuration type 1 for base access
[    0.661581] PCI: Using configuration type 1 for extended access
[    0.661581] bio: create slab <bio-0> at 0
[    0.661581] ACPI: EC: Look up EC in DSDT
[    0.663776] ACPI: Executed 1 blocks of module-level executable AML code
[    0.672480] ACPI: Interpreter enabled
[    0.672483] ACPI: (supports S0 S1 S4 S5)
[    0.672606] ACPI: Using IOAPIC for interrupt routing
[    0.672652] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.677244] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.684976] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.692695] ACPI Warning: Incorrect checksum in table [OEMB] - F3, should be E4 (20090903/tbutils-314)
[    0.692798] ACPI: No dock devices found.
[    0.692911] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.693129] pci 0000:00:01.1: reg 10 io port: [0xcc00-0xcc3f]
[    0.693140] pci 0000:00:01.1: reg 20 io port: [0x5000-0x503f]
[    0.693144] pci 0000:00:01.1: reg 24 io port: [0x6000-0x603f]
[    0.693163] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.693169] pci 0000:00:01.1: PME# disabled
[    0.693218] pci 0000:00:02.0: reg 10 32bit mmio: [0xdedff000-0xdedfffff]
[    0.693240] pci 0000:00:02.0: supports D1 D2
[    0.693243] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693246] pci 0000:00:02.0: PME# disabled
[    0.693268] pci 0000:00:02.1: reg 10 32bit mmio: [0xdedfec00-0xdedfecff]
[    0.693295] pci 0000:00:02.1: supports D1 D2
[    0.693297] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693300] pci 0000:00:02.1: PME# disabled
[    0.693366] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.693403] pci 0000:00:07.0: reg 10 32bit mmio: [0xdedfd000-0xdedfdfff]
[    0.693407] pci 0000:00:07.0: reg 14 io port: [0xc480-0xc487]
[    0.693429] pci 0000:00:07.0: supports D1 D2
[    0.693431] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693435] pci 0000:00:07.0: PME# disabled
[    0.693459] pci 0000:00:08.0: reg 10 io port: [0xc400-0xc407]
[    0.693462] pci 0000:00:08.0: reg 14 io port: [0xc080-0xc083]
[    0.693466] pci 0000:00:08.0: reg 18 io port: [0xc000-0xc007]
[    0.693469] pci 0000:00:08.0: reg 1c io port: [0xbc00-0xbc03]
[    0.693473] pci 0000:00:08.0: reg 20 io port: [0xb880-0xb88f]
[    0.693477] pci 0000:00:08.0: reg 24 32bit mmio: [0xdedfc000-0xdedfcfff]
[    0.693508] pci 0000:00:08.1: reg 10 io port: [0xb800-0xb807]
[    0.693512] pci 0000:00:08.1: reg 14 io port: [0xb480-0xb483]
[    0.693515] pci 0000:00:08.1: reg 18 io port: [0xb400-0xb407]
[    0.693519] pci 0000:00:08.1: reg 1c io port: [0xb080-0xb083]
[    0.693523] pci 0000:00:08.1: reg 20 io port: [0xb000-0xb00f]
[    0.693527] pci 0000:00:08.1: reg 24 32bit mmio: [0xdedfb000-0xdedfbfff]
[    0.693578] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693581] pci 0000:00:09.0: PME# disabled
[    0.693618] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693620] pci 0000:00:0b.0: PME# disabled
[    0.693656] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.693658] pci 0000:00:0c.0: PME# disabled
[    0.693778] pci 0000:01:08.0: reg 10 io port: [0xdc00-0xdc3f]
[    0.693810] pci 0000:01:08.0: supports D1 D2
[    0.693834] pci 0000:01:08.1: reg 10 io port: [0xd880-0xd887]
[    0.693866] pci 0000:01:08.1: supports D1 D2
[    0.693891] pci 0000:01:08.2: reg 10 32bit mmio: [0xdeeff800-0xdeefffff]
[    0.693897] pci 0000:01:08.2: reg 14 32bit mmio: [0xdeef8000-0xdeefbfff]
[    0.693929] pci 0000:01:08.2: supports D1 D2
[    0.693931] pci 0000:01:08.2: PME# supported from D0 D1 D2 D3hot
[    0.693934] pci 0000:01:08.2: PME# disabled
[    0.693964] pci 0000:00:04.0: transparent bridge
[    0.693967] pci 0000:00:04.0: bridge io port: [0xd000-0xdfff]
[    0.693971] pci 0000:00:04.0: bridge 32bit mmio: [0xdee00000-0xdeefffff]
[    0.693995] pci 0000:02:00.0: reg 10 32bit mmio: [0xdf000000-0xdfffffff]
[    0.694002] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.694009] pci 0000:02:00.0: reg 1c 64bit mmio pref: [0xdc000000-0xddffffff]
[    0.694014] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.694019] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xdef80000-0xdeffffff]
[    0.694063] pci 0000:02:00.1: reg 10 32bit mmio: [0xdef7c000-0xdef7ffff]
[    0.694131] pci 0000:00:09.0: bridge io port: [0xe000-0xefff]
[    0.694134] pci 0000:00:09.0: bridge 32bit mmio: [0xdef00000-0xdfffffff]
[    0.694138] pci 0000:00:09.0: bridge 64bit mmio pref: [0xc0000000-0xddffffff]
[    0.694217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.694380] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.694457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.694517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.701434] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *10
[    0.701614] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.701790] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.701964] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.702139] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *5
[    0.702313] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.702488] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.702662] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
[    0.702837] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.703014] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.703188] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *11
[    0.703364] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.703545] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.703723] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.703897] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.704072] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.704246] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.704421] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[    0.704627] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.704737] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.704740] vgaarb: loaded
[    0.704845] SCSI subsystem initialized
[    0.704871] libata version 3.00 loaded.
[    0.704871] usbcore: registered new interface driver usbfs
[    0.704871] usbcore: registered new interface driver hub
[    0.704871] usbcore: registered new device driver usb
[    0.704871] ACPI: WMI: Mapper loaded
[    0.704871] PCI: Using ACPI for IRQ routing
[    0.704871] NetLabel: Initializing
[    0.704871] NetLabel:  domain hash size = 128
[    0.704871] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.704871] NetLabel:  unlabeled traffic allowed by default
[    0.704871] Switching to clocksource tsc
[    0.705787] AppArmor: AppArmor Filesystem Enabled
[    0.705787] pnp: PnP ACPI init
[    0.705787] ACPI: bus type pnp registered
[    0.707095] pnp: PnP ACPI: found 16 devices
[    0.707097] ACPI: ACPI bus type pnp unregistered
[    0.707111] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.707114] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.707117] system 00:08: ioport range 0x4000-0x407f has been reserved
[    0.707120] system 00:08: ioport range 0x4080-0x40ff has been reserved
[    0.707122] system 00:08: ioport range 0x4400-0x447f has been reserved
[    0.707125] system 00:08: ioport range 0x4480-0x44ff has been reserved
[    0.707127] system 00:08: ioport range 0x4800-0x487f has been reserved
[    0.707130] system 00:08: ioport range 0x4880-0x48ff has been reserved
[    0.707132] system 00:08: ioport range 0x2000-0x207f has been reserved
[    0.707135] system 00:08: ioport range 0x2080-0x20ff has been reserved
[    0.707141] system 00:08: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.707144] system 00:08: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.707147] system 00:08: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.707152] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.707155] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.707160] system 00:0d: ioport range 0x290-0x29f has been reserved
[    0.707164] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.707169] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.707172] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    0.707175] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.707177] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
[    0.707180] system 00:0f: iomem range 0xff380000-0xffffffff has been reserved
[    0.711878] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.711882] pci 0000:00:04.0:   IO window: 0xd000-0xdfff
[    0.711885] pci 0000:00:04.0:   MEM window: 0xdee00000-0xdeefffff
[    0.711888] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.711892] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.711895] pci 0000:00:09.0:   IO window: 0xe000-0xefff
[    0.711898] pci 0000:00:09.0:   MEM window: 0xdef00000-0xdfffffff
[    0.711901] pci 0000:00:09.0:   PREFETCH window: 0x000000c0000000-0x000000ddffffff
[    0.711905] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.711907] pci 0000:00:0b.0:   IO window: disabled
[    0.711910] pci 0000:00:0b.0:   MEM window: disabled
[    0.711912] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.711916] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.711917] pci 0000:00:0c.0:   IO window: disabled
[    0.711920] pci 0000:00:0c.0:   MEM window: disabled
[    0.711922] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.711931] pci 0000:00:04.0: setting latency timer to 64
[    0.711937] pci 0000:00:09.0: setting latency timer to 64
[    0.711942] pci 0000:00:0b.0: setting latency timer to 64
[    0.711947] pci 0000:00:0c.0: setting latency timer to 64
[    0.711952] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.711954] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.711957] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.711960] pci_bus 0000:01: resource 1 mem: [0xdee00000-0xdeefffff]
[    0.711962] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.711965] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.711967] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.711970] pci_bus 0000:02: resource 1 mem: [0xdef00000-0xdfffffff]
[    0.711972] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xddffffff]
[    0.712008] NET: Registered protocol family 2
[    0.712169] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.713390] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.717097] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.717559] TCP: Hash tables configured (established 524288 bind 65536)
[    0.717562] TCP reno registered
[    0.717675] NET: Registered protocol family 1
[    0.804311] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804365] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804418] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804470] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804528] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804589] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804655] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.804678] pci 0000:02:00.0: Boot video device
[    0.805598] PCI-DMA: Disabling AGP.
[    0.805724] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.805726] PCI-DMA: using GART IOMMU.
[    0.805729] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.807672] Scanning for low memory corruption every 60 seconds
[    0.807803] audit: initializing netlink socket (disabled)
[    0.807823] type=2000 audit(1323198222.804:1): initialized
[    0.816045] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.817280] VFS: Disk quotas dquot_6.5.2
[    0.817327] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.817868] fuse init (API version 7.13)
[    0.817938] msgmni has been set to 7912
[    0.818189] alg: No test for stdrng (krng)
[    0.818240] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.818243] io scheduler noop registered
[    0.818246] io scheduler anticipatory registered
[    0.818248] io scheduler deadline registered
[    0.818277] io scheduler cfq registered (default)
[    0.818427]   alloc irq_desc for 24 on node 0
[    0.818430]   alloc kstat_irqs on node 0
[    0.818439] pcieport 0000:00:09.0: irq 24 for MSI/MSI-X
[    0.818444] pcieport 0000:00:09.0: setting latency timer to 64
[    0.818550]   alloc irq_desc for 25 on node 0
[    0.818552]   alloc kstat_irqs on node 0
[    0.818556] pcieport 0000:00:0b.0: irq 25 for MSI/MSI-X
[    0.818560] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.818655]   alloc irq_desc for 26 on node 0
[    0.818657]   alloc kstat_irqs on node 0
[    0.818662] pcieport 0000:00:0c.0: irq 26 for MSI/MSI-X
[    0.818666] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.818723] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.818748] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.818847] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.818851] ACPI: Power Button [PWRB]
[    0.818891] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.818893] ACPI: Power Button [PWRF]
[    0.819160] processor LNXCPU:00: registered as cooling_device0
[    0.819187] processor LNXCPU:01: registered as cooling_device1
[    0.819216] processor LNXCPU:02: registered as cooling_device2
[    0.819244] processor LNXCPU:03: registered as cooling_device3
[    0.823290] Linux agpgart interface v0.103
[    0.823323] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.823418] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.823511] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.823765] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.824591] brd: module loaded
[    0.824960] loop: module loaded
[    0.825037] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.825216] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.825534] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.825539]   alloc irq_desc for 23 on node 0
[    0.825540]   alloc kstat_irqs on node 0
[    0.825548] pata_acpi 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.825567] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.825573] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.825854] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.825857]   alloc irq_desc for 22 on node 0
[    0.825859]   alloc kstat_irqs on node 0
[    0.825866] pata_acpi 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.825879] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.825885] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.826214] Fixed MDIO Bus: probed
[    0.826241] PPP generic driver version 2.4.2
[    0.826269] tun: Universal TUN/TAP device driver, 1.6
[    0.826271] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.826333] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.826597] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.826600]   alloc irq_desc for 21 on node 0
[    0.826602]   alloc kstat_irqs on node 0
[    0.826609] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.826621] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.826624] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.826680] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.826714] ehci_hcd 0000:00:02.1: debug port 1
[    0.826722] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.826744] ehci_hcd 0000:00:02.1: irq 21, io mem 0xdedfec00
[    0.844240] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.844325] usb usb1: configuration #1 chosen from 1 choice
[    0.844354] hub 1-0:1.0: USB hub found
[    0.844362] hub 1-0:1.0: 10 ports detected
[    0.844424] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.844699] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.844702]   alloc irq_desc for 20 on node 0
[    0.844704]   alloc kstat_irqs on node 0
[    0.844711] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.844721] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.844723] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.844761] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.844783] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdedff000
[    0.857170] Freeing initrd memory: 8178k freed
[    0.906325] usb usb2: configuration #1 chosen from 1 choice
[    0.906346] hub 2-0:1.0: USB hub found
[    0.906354] hub 2-0:1.0: 10 ports detected
[    0.906410] uhci_hcd: USB Universal Host Controller Interface driver
[    0.906477] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.909239] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.909252] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.909390] mice: PS/2 mouse device common for all mice
[    0.909484] rtc_cmos 00:02: RTC can wake from S4
[    0.909522] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.909557] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.909696] device-mapper: uevent: version 1.0.3
[    0.909799] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.909925] device-mapper: multipath: version 1.1.0 loaded
[    0.909927] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.910182] cpuidle: using governor ladder
[    0.910184] cpuidle: using governor menu
[    0.910556] TCP cubic registered
[    0.910701] NET: Registered protocol family 10
[    0.911461] NET: Registered protocol family 17
[    0.911502] powernow-k8: Found 1 AMD Phenom(tm) 9550 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    0.911540] powernow-k8:    0 : pstate 0 (2200 MHz)
[    0.911542] powernow-k8:    1 : pstate 1 (1100 MHz)
[    0.911905] PM: Resume from disk failed.
[    0.911917] registered taskstats version 1
[    0.912224]   Magic number: 7:17:91
[    0.912317] rtc_cmos 00:02: setting system clock to 2011-12-06 19:03:43 UTC (1323198223)
[    0.912320] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.912322] EDD information not available.
[    0.912391] Freeing unused kernel memory: 888k freed
[    0.912746] Write protecting the kernel read-only data: 7692k
[    0.927639] udev: starting version 151
[    0.933685] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.956473] sata_nv 0000:00:08.0: version 3.5
[    0.956490] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.956557] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.956635] scsi0 : sata_nv
[    0.956817] scsi1 : sata_nv
[    0.957211] ata1: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 23
[    0.957214] ata2: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 23
[    0.958042] pata_amd 0000:00:06.0: version 0.4.1
[    0.958074] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.958138] scsi2 : pata_amd
[    0.958238] scsi3 : pata_amd
[    0.959330] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.959333] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.967633] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.967698] sata_nv 0000:00:08.1: setting latency timer to 64
[    0.969659] scsi4 : sata_nv
[    0.974721] scsi5 : sata_nv
[    0.974991] ata5: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb000 irq 22
[    0.974995] ata6: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xb008 irq 22
[    0.979476] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.979814] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    0.979820] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    0.979824] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.983118] Floppy drive(s): fd0 is 1.44M
[    0.996729] FDC 0 is a post-1991 82077
[    1.134893] ata3.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.02, max UDMA/66
[    1.134928] ata3: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    1.174713] ata3.00: configured for UDMA/66
[    1.224364] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.314832] ata5: SATA link down (SStatus 0 SControl 300)
[    1.391982] usb 1-4: configuration #1 chosen from 1 choice
[    1.444537] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.464898] ata1.00: ATA-8: ST500DM002-1BC142, JC4B, max UDMA/133
[    1.464902] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.504626] ata1.00: configured for UDMA/133
[    1.504756] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BC14 JC4B PQ: 0 ANSI: 5
[    1.504927] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.504932] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.504968] sd 0:0:0:0: [sda] Write Protect is off
[    1.504971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.505017] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.505139]  sda:
[    1.505463] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:66:a6:5c:51
[    1.505467] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.518408]  sda1
[    1.518614] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.723765] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    1.945324] usb 2-1: configuration #1 chosen from 1 choice
[    1.993795] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.014260] ata2.00: ATA-8: MAXTOR STM3500320AS, MX1A, max UDMA/133
[    2.014264] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.050536] ata2.00: configured for UDMA/133
[    2.050641] scsi 1:0:0:0: Direct-Access     ATA      MAXTOR STM350032 MX1A PQ: 0 ANSI: 5
[    2.050772] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.050792] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.050805] sd 1:0:0:0: [sdb] Write Protect is off
[    2.050808] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.050827] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.050939]  sdb:
[    2.051953] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.02 PQ: 0 ANSI: 5
[    2.053655] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.053658] Uniform CD-ROM driver Revision: 3.20
[    2.053735] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.053791] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    2.053880] ata4: port disabled. ignoring.
[    2.070512]  sdb1 sdb2 < sdb5 sdb6 > sdb3
[    2.108495] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.390399] ata6: SATA link down (SStatus 0 SControl 300)
[    2.393835] usbcore: registered new interface driver hiddev
[    2.396472] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[    2.396478]   alloc irq_desc for 19 on node 0
[    2.396480]   alloc kstat_irqs on node 0
[    2.396492] ohci1394 0000:01:08.2: PCI INT B -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    2.400521] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
[    2.400611] generic-usb 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:02.0-1/input0
[    2.400640] usbcore: registered new interface driver usbhid
[    2.400643] usbhid: v2.6:USB HID core driver
[    2.460058] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[deeff800-deefffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.836353] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[    3.773933] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510e5e72]
[   13.095791] udev: starting version 151
[   13.221723] type=1505 audit(1323194635.801:2):  operation="profile_load" pid=628 name="/sbin/dhclient3"
[   13.221756] type=1505 audit(1323194635.801:3):  operation="profile_replace" pid=631 name="/sbin/dhclient3"
[   13.221991] type=1505 audit(1323194635.801:4):  operation="profile_load" pid=628 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.222038] type=1505 audit(1323194635.801:5):  operation="profile_replace" pid=631 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.222145] type=1505 audit(1323194635.801:6):  operation="profile_load" pid=628 name="/usr/lib/connman/scripts/dhclient-script"
[   13.222199] type=1505 audit(1323194635.801:7):  operation="profile_replace" pid=631 name="/usr/lib/connman/scripts/dhclient-script"
[   13.277102] lp: driver loaded but no devices found
[   13.418610] parport_pc 00:07: reported by Plug and Play ACPI
[   13.418665] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.455836] ppdev: user-space parallel port driver
[   13.481321] rtusb init --->
[   13.481359] usbcore: registered new interface driver rt2870
[   13.500203] lp0: using parport0 (interrupt-driven).
[   13.639194] EDAC MC: Ver: 2.1.0 Oct 11 2011
[   13.641538] EDAC amd64_edac:  Ver: 3.2.0 Oct 11 2011
[   13.641612] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   13.641627] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   13.641628]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   13.641630]  (Note that use of the override may cause unknown side effects.)
[   13.641654] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   13.701423] i2c i2c-0: nForce2 SMBus adapter at 0x5000
[   13.701452] i2c i2c-1: nForce2 SMBus adapter at 0x6000
[   13.719292] gameport: EMU10K1 is pci0000:01:08.1/gameport0, io 0xd880, speed 1195kHz
[   13.929027] vga16fb: initializing
[   13.929034] vga16fb: mapped to 0xffff8800000a0000
[   13.929102] fb0: VGA16 VGA frame buffer device
[   14.112681] Adding 979924k swap on /dev/sdb6.  Priority:-1 extents:1 across:979924k 
[   14.116309] nvidia: module license 'NVIDIA' taints kernel.
[   14.116314] Disabling lock debugging due to kernel taint
[   14.762951] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   14.762957]   alloc irq_desc for 18 on node 0
[   14.762959]   alloc kstat_irqs on node 0
[   14.762970] HDA Intel 0000:02:00.1: PCI INT B -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   14.762974] hda_intel: Disable MSI for Nvidia chipset
[   14.763030] HDA Intel 0000:02:00.1: setting latency timer to 64
[   14.763317] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[   14.763319]   alloc irq_desc for 17 on node 0
[   14.763321]   alloc kstat_irqs on node 0
[   14.763328] EMU10K1_Audigy 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 17 (level, low) -> IRQ 17
[   14.766466] Installing spdif_bug patch: SB Audigy 2 ZS [SB0350]
[   14.781675] Console: switching to colour frame buffer device 80x30
[   15.373112] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.456858] EXT4-fs (sdb3): mounted filesystem with ordered data mode
[   16.620837] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 16
[   16.620844]   alloc irq_desc for 16 on node 0
[   16.620847]   alloc kstat_irqs on node 0
[   16.620858] nvidia 0000:02:00.0: PCI INT A -> Link[LNED] -> GSI 16 (level, low) -> IRQ 16
[   16.620867] nvidia 0000:02:00.0: setting latency timer to 64
[   16.620872] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.621085] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   16.958419] type=1505 audit(1323194639.541:8):  operation="profile_load" pid=976 name="/usr/share/gdm/guest-session/Xsession"
[   16.958657] type=1505 audit(1323194639.541:9):  operation="profile_replace" pid=977 name="/sbin/dhclient3"
[   16.958937] type=1505 audit(1323194639.541:10):  operation="profile_replace" pid=977 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.959094] type=1505 audit(1323194639.541:11):  operation="profile_replace" pid=977 name="/usr/lib/connman/scripts/dhclient-script"
[   17.060936]   alloc irq_desc for 27 on node 0
[   17.060941]   alloc kstat_irqs on node 0
[   17.060951] forcedeth 0000:00:07.0: irq 27 for MSI/MSI-X
[   17.340253] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   17.340257] vboxdrv: Successfully done.
[   17.340259] vboxdrv: Found 4 processor cores.
[   17.340338] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e5ba20
[   17.340409] vboxdrv: fAsync=0 offMin=0x2e8 offMax=0x2810
[   17.340795] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   17.340798] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   27.881266] eth0: no IPv6 routers present
[   86.106745] usb 1-4: USB disconnect, address 3
[   96.700260] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   96.871502] usb 1-4: configuration #1 chosen from 1 choice
``````

sudo modprobe rt2870sta
tail /var/log/kern.log

Dec  6 19:31:00 desktop kernel: [ 1637.434863] rtusb init --->
Dec  6 19:31:00 desktop kernel: [ 1637.434902] usbcore: registered new interface driver rt2870

``````
lsusb
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0df6:0042 Sitecom Europe B.V. WL-345 Wireless USB adapter 300N X3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
tail /etc/modprobe.d/blacklist.conf 
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist ndiswrapper

```

---

### Post by chili555 on 2011-12-07
Please let us see:```
lsusb
```Thanks.

---

### Post by flyshoppa on 2011-12-07
Hi chili555
I've already posted it ... 

Bus 001 Device 005: ID 0df6:0042 Sitecom Europe B.V. WL-345 Wireless USB adapter 300N 
Davide

---

### Post by praseodym on 2011-12-07
Hi,

you dont need ndiswrapper, so you should completely uninstall it:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
In 10.04 you need to add the device ID to the native module **rt2870sta**, it doesnt contain it:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0df6 0042" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf 
```
This is [COLOR="Red"]one[/COLOR] line, you better copy/paste it.

After that load the driver and replug the stick:

```
sudo modprobe -v rt2870sta
```

[COLOR="Red"]Edit:[/COLOR] Control:

```
iwconfig
lsmod
dmesg | grep rt2
sudo iwlist scan
rfkill list
grep rt2 /etc/modprobe.d/*
```

[COLOR="Red"]Edit 2:[/COLOR] ;-)
If it works, create an UDEV-rule to load the driver if the stick is plugged in:
```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Insert:
```
# UDEV-Rule for Sitecom USB Adapter 300N (WL-345UP) ID 0df6:0042
SUBSYSTEM=="usb", ATTR{idVendor}=="0df6", ATTR{idProduct}=="0042", RUN+="/sbin/modprobe rt2870sta"
```
save and close gedit and reload udev:
```
sudo service udev reload
```

---

