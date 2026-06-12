---
title: "Unable to burn DVD's.."
date: 2013-11-18
forum: Multimedia Software
---

### Post by killabee44 on 2013-11-18
Hi guys,

I have a Optiarc DVD AD-7170S DVD writer on my pc for a long time but have not tried to burn a DVD since I last installed 13.04. Well, Im finding out that the drive handles CD's just fine, but not DVD's. When I put in a disc, it is not recognized at all. 

K3B gives me this error:

```
Devices
-----------------------
Optiarc DVD RW AD-7170S 1.00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 538239 with sector size 2048. Length: 538240 sectors, 1102315520 bytes.

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.8.5 (4.8.5)
QT Version:  4.8.1
Kernel:      3.2.0-56-generic

```


sudo lshw -sanitize -C disk:

```
*-disk:0                
       description: ATA Disk
       product: ST3000DM001-9YN1
       vendor: Seagate
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: CC4B
       serial: [REMOVED]
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=47c843c7-1f10-4c35-b5c7-3e7e1cc7dacf
  *-disk:1
       description: ATA Disk
       product: WDC WD2001FASS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: 01.0
       serial: [REMOVED]
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0008a108
  *-disk:2
       description: ATA Disk
       product: ST3250823AS
       vendor: Seagate
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 3.02
       serial: [REMOVED]
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4c5d0935
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7170S
       vendor: Optiarc
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.00
       serial: [REMOVED]
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: ST3250823AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdd
       version: 3.03
       serial: [REMOVED]
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=127589c5

```

dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-56-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013 (Ubuntu 3.2.0-56.86-generic 3.2.51)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-56-generic root=UUID=177d552f-a53d-4410-b997-976d4d5f9216 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: System manufacturer System Product Name/P5B-Deluxe, BIOS 1238    09/30/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x180000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask F80000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 2, base: 0GB, range: 4GB, type WB
[    0.000000] reg 3, base: 4GB, range: 2GB, type WB
[    0.000000] total RAM covered: 5376M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64K 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 2GB, type WB
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbff90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff90000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff90000 page 4k
[    0.000000] kernel direct mapping tables up to bff90000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000180000000
[    0.000000]  0100000000 - 0180000000 page 2M
[    0.000000] kernel direct mapping tables up to 180000000 @ bff8d000-bff90000
[    0.000000] RAMDISK: 35894000 - 36c42000
[    0.000000] ACPI: RSDP 00000000000fae70 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bff90000 00038 (v01 MSTEST TESTONLY 09000830 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bff90200 00084 (v02 MSTEST OEMFACP  09000830 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bff905c0 0918E (v01  A0483 A0483035 00000035 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bff9e000 00040
[    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 MSTEST OEMAPIC  09000830 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 MSTEST OEMMCFG  09000830 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bff9e040 0007B (v01 MSTEST AMI_OEM  09000830 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bff99750 00038 (v01 MSTEST OEMHPET  09000830 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000180000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000180000000
[    0.000000]   NODE_DATA [000000017fffb000 - 000000017fffffff]
[    0.000000]  [ffffea0000000000-ffffea0005ffffff] PMD -> [ffff88017a600000-ffff88017f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00180000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x00180000
[    0.000000] On node 0 totalpages: 1310495
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 765904 pages, LIFO batch:31
[    0.000000]   Normal zone: 8192 pages used for memmap
[    0.000000]   Normal zone: 516096 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
[    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
[    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
[    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88017fc00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1285914
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-56-generic root=UUID=177d552f-a53d-4410-b997-976d4d5f9216 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 5057568k/6291456k available (6585k kernel code, 1049476k absent, 184412k reserved, 6620k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2133.439 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4266.87 BogoMIPS (lpj=8533756)
[    0.008009] pid_max: default: 32768 minimum: 301
[    0.008038] Security Framework initialized
[    0.008056] AppArmor: AppArmor initialized
[    0.008058] Yama: becoming mindful.
[    0.008848] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.013843] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.016213] Mount-cache hash table entries: 256
[    0.016389] Initializing cgroup subsys cpuacct
[    0.016395] Initializing cgroup subsys memory
[    0.016405] Initializing cgroup subsys devices
[    0.016407] Initializing cgroup subsys freezer
[    0.016409] Initializing cgroup subsys blkio
[    0.016417] Initializing cgroup subsys perf_event
[    0.016452] CPU: Physical Processor ID: 0
[    0.016454] CPU: Processor Core ID: 0
[    0.016456] mce: CPU supports 6 MCE banks
[    0.016465] CPU0: Thermal monitoring enabled (TM2)
[    0.016469] using mwait in idle threads.
[    0.019146] ACPI: Core revision 20110623
[    0.024033] ftrace: allocating 26595 entries in 105 pages
[    0.028413] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068495] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06
[    0.072003] APIC calibration not consistent with PM-Timer: 115ms instead of 100ms
[    0.072003] APIC delta adjusted to PM-Timer: 1666667 (1933308)
[    0.072003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.072003] PEBS disabled due to CPU errata.
[    0.072003] ... version:                2
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Booting Node   0, Processors  #1
[    0.072003] smpboot cpu 1: start_ip = 9a000
[    0.160039] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160081] Brought up 2 CPUs
[    0.160084] Total of 2 processors activated (8533.57 BogoMIPS).
[    0.161370] devtmpfs: initialized
[    0.161370] EVM: security.selinux
[    0.161370] EVM: security.SMACK64
[    0.161370] EVM: security.capability
[    0.161370] PM: Registering ACPI NVS region at bff9e000 (270336 bytes)
[    0.161370] print_constraints: dummy: 
[    0.161370] RTC time: 20:17:11, date: 11/14/13
[    0.161370] NET: Registered protocol family 16
[    0.161370] Trying to unpack rootfs image as initramfs...
[    0.161370] ACPI: bus type pci registered
[    0.161370] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.161370] PCI: not using MMCONFIG
[    0.161370] PCI: Using configuration type 1 for base access
[    0.165015] bio: create slab <bio-0> at 0
[    0.165105] ACPI: Added _OSI(Module Device)
[    0.165108] ACPI: Added _OSI(Processor Device)
[    0.165110] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.165112] ACPI: Added _OSI(Processor Aggregator Device)
[    0.166457] ACPI: EC: Look up EC in DSDT
[    0.167874] ACPI: Executed 1 blocks of module-level executable AML code
[    0.172544] ACPI: SSDT 00000000bff9e0c0 001C6 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.172883] ACPI: Dynamic OEM Table Load:
[    0.172887] ACPI: SSDT           (null) 001C6 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.173051] ACPI: SSDT 00000000bff9e290 0013A (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.173388] ACPI: Dynamic OEM Table Load:
[    0.173392] ACPI: SSDT           (null) 0013A (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.173557] ACPI: Interpreter enabled
[    0.173562] ACPI: (supports S0 S1 S3 S4 S5)
[    0.173582] ACPI: Using IOAPIC for interrupt routing
[    0.173609] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.174053] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.227459] ACPI: No dock devices found.
[    0.227463] HEST: Table not found.
[    0.227466] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.227535] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.227670] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.227674] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.227676] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.227679] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.227682] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xffffffff]
[    0.227699] pci 0000:00:00.0: [8086:29a0] type 0 class 0x000600
[    0.227751] pci 0000:00:01.0: [8086:29a1] type 1 class 0x000604
[    0.227792] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.227796] pci 0000:00:01.0: PME# disabled
[    0.227833] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.227872] pci 0000:00:1a.0: reg 20: [io  0xa880-0xa89f]
[    0.227904] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.227943] pci 0000:00:1a.1: reg 20: [io  0xac00-0xac1f]
[    0.227986] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.228018] pci 0000:00:1a.7: reg 10: [mem 0xf7fffc00-0xf7ffffff]
[    0.228102] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.228107] pci 0000:00:1a.7: PME# disabled
[    0.228126] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.228193] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.228198] pci 0000:00:1c.0: PME# disabled
[    0.228222] pci 0000:00:1c.4: [8086:2847] type 1 class 0x000604
[    0.228289] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.228293] pci 0000:00:1c.4: PME# disabled
[    0.228318] pci 0000:00:1c.5: [8086:2849] type 1 class 0x000604
[    0.228385] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.228390] pci 0000:00:1c.5: PME# disabled
[    0.228410] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.228448] pci 0000:00:1d.0: reg 20: [io  0xa400-0xa41f]
[    0.228480] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.228518] pci 0000:00:1d.1: reg 20: [io  0xa480-0xa49f]
[    0.228549] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.228590] pci 0000:00:1d.2: reg 20: [io  0xa800-0xa81f]
[    0.228631] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.228649] pci 0000:00:1d.7: reg 10: [mem 0xf7fff800-0xf7fffbff]
[    0.228729] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.228733] pci 0000:00:1d.7: PME# disabled
[    0.228752] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.228814] pci 0000:00:1f.0: [8086:2810] type 0 class 0x000601
[    0.228895] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.228941] pci 0000:00:1f.2: [8086:2820] type 0 class 0x000101
[    0.228955] pci 0000:00:1f.2: reg 10: [io  0x9400-0x9407]
[    0.228963] pci 0000:00:1f.2: reg 14: [io  0x9080-0x9083]
[    0.228971] pci 0000:00:1f.2: reg 18: [io  0x9000-0x9007]
[    0.228979] pci 0000:00:1f.2: reg 1c: [io  0x8c00-0x8c03]
[    0.228987] pci 0000:00:1f.2: reg 20: [io  0x8880-0x888f]
[    0.228995] pci 0000:00:1f.2: reg 24: [io  0x8800-0x880f]
[    0.229023] pci 0000:00:1f.2: PME# supported from D3hot
[    0.229027] pci 0000:00:1f.2: PME# disabled
[    0.229039] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.229050] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.229077] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.229109] pci 0000:00:1f.5: [8086:2825] type 0 class 0x000101
[    0.229122] pci 0000:00:1f.5: reg 10: [io  0xa080-0xa087]
[    0.229130] pci 0000:00:1f.5: reg 14: [io  0xa000-0xa003]
[    0.229138] pci 0000:00:1f.5: reg 18: [io  0x9c00-0x9c07]
[    0.229146] pci 0000:00:1f.5: reg 1c: [io  0x9880-0x9883]
[    0.229155] pci 0000:00:1f.5: reg 20: [io  0x9800-0x980f]
[    0.229164] pci 0000:00:1f.5: reg 24: [io  0x9480-0x948f]
[    0.229192] pci 0000:00:1f.5: PME# supported from D3hot
[    0.229196] pci 0000:00:1f.5: PME# disabled
[    0.229239] pci 0000:01:00.0: [10de:0193] type 0 class 0x000300
[    0.229249] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.229259] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.229270] pci 0000:01:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit]
[    0.229277] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
[    0.229285] pci 0000:01:00.0: reg 30: [mem 0xfbce0000-0xfbcfffff pref]
[    0.229326] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.229334] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.229337] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.229341] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    0.229345] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.229384] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.229393] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.229451] pci 0000:03:00.0: [197b:2363] type 0 class 0x000101
[    0.229539] pci 0000:03:00.0: reg 24: [mem 0xfbefe000-0xfbefffff]
[    0.229553] pci 0000:03:00.0: reg 30: [mem 0xfbee0000-0xfbeeffff pref]
[    0.229605] pci 0000:03:00.0: PME# supported from D3hot
[    0.229611] pci 0000:03:00.0: PME# disabled
[    0.229641] pci 0000:03:00.1: [197b:2363] type 0 class 0x000101
[    0.229666] pci 0000:03:00.1: reg 10: [io  0xdc00-0xdc07]
[    0.229680] pci 0000:03:00.1: reg 14: [io  0xd880-0xd883]
[    0.229694] pci 0000:03:00.1: reg 18: [io  0xd800-0xd807]
[    0.229708] pci 0000:03:00.1: reg 1c: [io  0xd480-0xd483]
[    0.229721] pci 0000:03:00.1: reg 20: [io  0xd400-0xd40f]
[    0.229806] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.229820] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.229824] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.229828] pci 0000:00:1c.4:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.229893] pci 0000:02:00.0: [11ab:4364] type 0 class 0x000200
[    0.229916] pci 0000:02:00.0: reg 10: [mem 0xfbdfc000-0xfbdfffff 64bit]
[    0.229928] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
[    0.229971] pci 0000:02:00.0: reg 30: [mem 0xfbdc0000-0xfbddffff pref]
[    0.230038] pci 0000:02:00.0: supports D1 D2
[    0.230040] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.230045] pci 0000:02:00.0: PME# disabled
[    0.236037] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.236042] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.236047] pci 0000:00:1c.5:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.236089] pci 0000:05:01.0: [13f6:8788] type 0 class 0x000401
[    0.236106] pci 0000:05:01.0: reg 10: [io  0xe800-0xe8ff]
[    0.236181] pci 0000:05:01.0: supports D1 D2
[    0.236200] pci 0000:05:03.0: [104c:8023] type 0 class 0x000c00
[    0.236218] pci 0000:05:03.0: reg 10: [mem 0xfbfff800-0xfbffffff]
[    0.236228] pci 0000:05:03.0: reg 14: [mem 0xfbff8000-0xfbffbfff]
[    0.236297] pci 0000:05:03.0: supports D1 D2
[    0.236299] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.236304] pci 0000:05:03.0: PME# disabled
[    0.236323] pci 0000:05:04.0: [11ab:4320] type 0 class 0x000200
[    0.236343] pci 0000:05:04.0: reg 10: [mem 0xfbff4000-0xfbff7fff]
[    0.236353] pci 0000:05:04.0: reg 14: [io  0xe400-0xe4ff]
[    0.236397] pci 0000:05:04.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.236434] pci 0000:05:04.0: supports D1 D2
[    0.236436] pci 0000:05:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.236441] pci 0000:05:04.0: PME# disabled
[    0.236482] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.236486] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.236490] pci 0000:00:1e.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.236496] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.236499] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.236502] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.236505] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.236508] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.236532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.236645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.236674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.236753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.236787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.236826] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.236870]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.236874]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.236876] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.243512] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.243567] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.243616] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.243664] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.243711] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.243766] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.243814] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.243861] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.244006] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.244023] vgaarb: loaded
[    0.244025] vgaarb: bridge control possible 0000:01:00.0
[    0.244148] i2c-core: driver [aat2870] using legacy suspend method
[    0.244150] i2c-core: driver [aat2870] using legacy resume method
[    0.244225] SCSI subsystem initialized
[    0.244291] libata version 3.00 loaded.
[    0.244348] usbcore: registered new interface driver usbfs
[    0.244362] usbcore: registered new interface driver hub
[    0.244392] usbcore: registered new device driver usb
[    0.244492] PCI: Using ACPI for IRQ routing
[    0.250316] PCI: pci_cache_line_size set to 64 bytes
[    0.250421] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.250429] reserve RAM buffer: 00000000bff90000 - 00000000bfffffff 
[    0.250556] NetLabel: Initializing
[    0.250558] NetLabel:  domain hash size = 128
[    0.250559] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.250572] NetLabel:  unlabeled traffic allowed by default
[    0.250637] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.250642] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.250647] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.256084] Switching to clocksource hpet
[    0.265231] AppArmor: AppArmor Filesystem Enabled
[    0.265267] pnp: PnP ACPI init
[    0.265293] ACPI: bus type pnp registered
[    0.265394] pnp 00:00: [bus 00-ff]
[    0.265397] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.265400] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.265402] pnp 00:00: [io  0x0d00-0xffff window]
[    0.265405] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.265407] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.265410] pnp 00:00: [mem 0xc0000000-0xffffffff window]
[    0.265487] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.265498] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.265564] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.265568] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.265603] pnp 00:02: [dma 4]
[    0.265605] pnp 00:02: [io  0x0000-0x000f]
[    0.265608] pnp 00:02: [io  0x0081-0x0083]
[    0.265610] pnp 00:02: [io  0x0087]
[    0.265612] pnp 00:02: [io  0x0089-0x008b]
[    0.265614] pnp 00:02: [io  0x008f]
[    0.265616] pnp 00:02: [io  0x00c0-0x00df]
[    0.265646] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.265658] pnp 00:03: [io  0x0070-0x0071]
[    0.265670] pnp 00:03: [irq 8]
[    0.265701] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.265711] pnp 00:04: [io  0x0061]
[    0.265738] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.265748] pnp 00:05: [io  0x00f0-0x00ff]
[    0.265754] pnp 00:05: [irq 13]
[    0.265784] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.266014] pnp 00:06: [irq 4]
[    0.266017] pnp 00:06: [dma 0 disabled]
[    0.266023] pnp 00:06: [io  0x03f8-0x03ff]
[    0.266104] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.266234] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.266237] pnp 00:07: [io  0x0000-0xffffffffffffffff disabled]
[    0.266239] pnp 00:07: [io  0x0290-0x0297]
[    0.266296] system 00:07: [io  0x0290-0x0297] has been reserved
[    0.266300] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266396] pnp 00:08: [io  0x0010-0x001f]
[    0.266398] pnp 00:08: [io  0x0022-0x003f]
[    0.266400] pnp 00:08: [io  0x0044-0x005f]
[    0.266402] pnp 00:08: [io  0x0062-0x0063]
[    0.266404] pnp 00:08: [io  0x0065-0x006f]
[    0.266406] pnp 00:08: [io  0x0072-0x007f]
[    0.266409] pnp 00:08: [io  0x0080]
[    0.266411] pnp 00:08: [io  0x0084-0x0086]
[    0.266413] pnp 00:08: [io  0x0088]
[    0.266415] pnp 00:08: [io  0x008c-0x008e]
[    0.266417] pnp 00:08: [io  0x0090-0x009f]
[    0.266419] pnp 00:08: [io  0x00a2-0x00bf]
[    0.266421] pnp 00:08: [io  0x00e0-0x00ef]
[    0.266423] pnp 00:08: [io  0x04d0-0x04d1]
[    0.266425] pnp 00:08: [io  0x0800-0x087f]
[    0.266427] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.266429] pnp 00:08: [io  0x0480-0x04bf]
[    0.266432] pnp 00:08: [mem 0xffafe000-0xffb0cbff]
[    0.266434] pnp 00:08: [mem 0xffb00000-0xffbfffff]
[    0.266436] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.266438] pnp 00:08: [mem 0xfed20000-0xfed8ffff]
[    0.266440] pnp 00:08: [mem 0xfff00000-0xfffffffe]
[    0.266443] pnp 00:08: [mem 0xfebfe000-0xfebfec00]
[    0.266522] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.266526] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.266528] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.266532] system 00:08: [mem 0xffafe000-0xffb0cbff] could not be reserved
[    0.266535] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.266538] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.266541] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.266543] system 00:08: [mem 0xfff00000-0xfffffffe] has been reserved
[    0.266546] system 00:08: [mem 0xfebfe000-0xfebfec00] has been reserved
[    0.266550] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266620] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.266654] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.266698] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.266701] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.266761] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.266764] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.266768] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.266832] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.266886] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.266890] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.267059] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.267061] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.267064] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.267066] pnp 00:0c: [mem 0x00100000-0xbfffffff]
[    0.267068] pnp 00:0c: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.267137] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.267141] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.267144] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.267147] system 00:0c: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.267150] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.267274] pnp: PnP ACPI: found 13 devices
[    0.267276] ACPI: ACPI bus type pnp unregistered
[    0.273899] PCI: max bus depth: 1 pci_try_num: 2
[    0.273946] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0000000-0xc00000ff]
[    0.273952] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0000000-0xc00000ff] (PCI address [0xc0000000-0xc00000ff])
[    0.273956] pci 0000:00:1c.5: BAR 15: assigned [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.273961] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.273964] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0500000-0xc08fffff]
[    0.273969] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.273973] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.273976] pci 0000:00:01.0:   bridge window [io  0xb000-0xbfff]
[    0.273980] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    0.273984] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.273988] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.273991] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.273996] pci 0000:00:1c.0:   bridge window [mem 0xc0500000-0xc08fffff]
[    0.274001] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.274007] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.274010] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.274015] pci 0000:00:1c.4:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.274019] pci 0000:00:1c.4:   bridge window [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.274025] pci 0000:00:1c.5: PCI bridge to [bus 02-02]
[    0.274028] pci 0000:00:1c.5:   bridge window [io  0xc000-0xcfff]
[    0.274033] pci 0000:00:1c.5:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.274037] pci 0000:00:1c.5:   bridge window [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.274043] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.274046] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.274051] pci 0000:00:1e.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.274076] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.274081] pci 0000:00:01.0: setting latency timer to 64
[    0.274087] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.274092] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.274096] pci 0000:00:1c.0: setting latency timer to 64
[    0.274102] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.274106] pci 0000:00:1c.4: setting latency timer to 64
[    0.274117] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.274121] pci 0000:00:1c.5: setting latency timer to 64
[    0.274128] pci 0000:00:1e.0: setting latency timer to 64
[    0.274132] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.274134] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.274137] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.274139] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.274142] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xffffffff]
[    0.274145] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.274148] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbcfffff]
[    0.274151] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.274155] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.274159] pci_bus 0000:04: resource 1 [mem 0xc0500000-0xc08fffff]
[    0.274162] pci_bus 0000:04: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    0.274166] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.274169] pci_bus 0000:03: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.274173] pci_bus 0000:03: resource 2 [mem 0xc0300000-0xc04fffff 64bit pref]
[    0.274176] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.274180] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.274183] pci_bus 0000:02: resource 2 [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.274187] pci_bus 0000:05: resource 0 [io  0xe000-0xefff]
[    0.274190] pci_bus 0000:05: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.274194] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.274197] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.274200] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.274204] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.274207] pci_bus 0000:05: resource 8 [mem 0xc0000000-0xffffffff]
[    0.274254] NET: Registered protocol family 2
[    0.274516] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.276819] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.281864] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.282480] TCP: Hash tables configured (established 524288 bind 65536)
[    0.282483] TCP reno registered
[    0.282500] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.282588] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.282780] NET: Registered protocol family 1
[    0.282815] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.282832] pci 0000:00:1a.0: PCI INT A disabled
[    0.282840] pci 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.282856] pci 0000:00:1a.1: PCI INT B disabled
[    0.282875] pci 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.578332] Freeing initrd memory: 20152k freed
[    1.880039] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    1.880163] pci 0000:00:1a.7: PCI INT C disabled
[    1.880208] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.880225] pci 0000:00:1d.0: PCI INT A disabled
[    1.880240] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.880257] pci 0000:00:1d.1: PCI INT B disabled
[    1.880276] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.880291] pci 0000:00:1d.2: PCI INT C disabled
[    1.880300] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.880333] pci 0000:00:1d.7: PCI INT A disabled
[    1.880357] pci 0000:01:00.0: Boot video device
[    1.880375] PCI: CLS 32 bytes, default 64
[    1.880379] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.880381] Placing 64MB software IO TLB between ffff8800bbf8d000 - ffff8800bff8d000
[    1.880384] software IO TLB at phys 0xbbf8d000 - 0xbff8d000
[    1.880812] audit: initializing netlink socket (disabled)
[    1.880826] type=2000 audit(1384460232.876:1): initialized
[    1.903847] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.906379] VFS: Disk quotas dquot_6.5.2
[    1.906440] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.907003] fuse init (API version 7.17)
[    1.907108] msgmni has been set to 9917
[    1.907478] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.907509] io scheduler noop registered
[    1.907511] io scheduler deadline registered
[    1.907550] io scheduler cfq registered (default)
[    1.907668] pcieport 0000:00:01.0: setting latency timer to 64
[    1.907701] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.907750] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.907785] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.907842] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.907878] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    1.907936] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.907973] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    1.908075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.908096] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.908158] intel_idle: MWAIT substates: 0x20
[    1.908160] intel_idle: does not run on family 6 model 15
[    1.908255] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.908261] ACPI: Power Button [PWRB]
[    1.908314] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.908318] ACPI: Power Button [PWRF]
[    1.909745] ERST: Table is not found!
[    1.909748] GHES: HEST is not enabled!
[    1.909832] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.930177] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.056494] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.056789] Linux agpgart interface v0.103
[    2.058567] brd: module loaded
[    2.059424] loop: module loaded
[    2.059579] ahci 0000:03:00.0: version 3.0
[    2.059594] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.072060] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.072065] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.072073] ahci 0000:03:00.0: setting latency timer to 64
[    2.072467] scsi0 : ahci
[    2.072566] scsi1 : ahci
[    2.072659] ata1: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 16
[    2.072663] ata2: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 16
[    2.072745] ata_piix 0000:00:1f.2: version 2.13
[    2.072754] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.072759] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.072799] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.073108] scsi2 : ata_piix
[    2.073191] scsi3 : ata_piix
[    2.074619] ata3: SATA max UDMA/133 cmd 0x9400 ctl 0x9080 bmdma 0x8880 irq 19
[    2.074625] ata4: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8888 irq 19
[    2.074665] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.074699] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.074736] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.074974] scsi4 : ata_piix
[    2.075054] scsi5 : ata_piix
[    2.075905] ata5: SATA max UDMA/133 cmd 0xa080 ctl 0xa000 bmdma 0x9800 irq 19
[    2.075909] ata6: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9808 irq 19
[    2.075983] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    2.075990] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.076035] pata_acpi 0000:03:00.1: setting latency timer to 64
[    2.076049] pata_acpi 0000:03:00.1: PCI INT B disabled
[    2.076382] Fixed MDIO Bus: probed
[    2.076405] tun: Universal TUN/TAP device driver, 1.6
[    2.076407] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.076473] PPP generic driver version 2.4.2
[    2.076586] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.076602] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.076620] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.076624] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.076682] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.076708] ehci_hcd 0000:00:1a.7: debug port 1
[    2.080602] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.080618] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf7fffc00
[    2.096047] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.096227] hub 1-0:1.0: USB hub found
[    2.096233] hub 1-0:1.0: 4 ports detected
[    2.096331] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.096344] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.096347] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.096395] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.096420] ehci_hcd 0000:00:1d.7: debug port 1
[    2.100317] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.100331] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7fff800
[    2.116047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.116216] hub 2-0:1.0: USB hub found
[    2.116222] hub 2-0:1.0: 6 ports detected
[    2.116323] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.116338] uhci_hcd: USB Universal Host Controller Interface driver
[    2.116358] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.116364] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.116367] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.116412] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.116435] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a880
[    2.116571] hub 3-0:1.0: USB hub found
[    2.116576] hub 3-0:1.0: 2 ports detected
[    2.116647] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.116654] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.116657] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.116702] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.116732] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ac00
[    2.116874] hub 4-0:1.0: USB hub found
[    2.116878] hub 4-0:1.0: 2 ports detected
[    2.116953] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.116960] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.116963] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.117007] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.117031] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a400
[    2.117165] hub 5-0:1.0: USB hub found
[    2.117170] hub 5-0:1.0: 2 ports detected
[    2.117237] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.117244] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.117247] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.117293] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.117319] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a480
[    2.117450] hub 6-0:1.0: USB hub found
[    2.117454] hub 6-0:1.0: 2 ports detected
[    2.117527] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.117533] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.117536] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.117582] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.117604] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a800
[    2.117735] hub 7-0:1.0: USB hub found
[    2.117739] hub 7-0:1.0: 2 ports detected
[    2.117861] usbcore: registered new interface driver libusual
[    2.117906] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.120454] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.120460] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.120601] mousedev: PS/2 mouse device common for all mice
[    2.120757] rtc_cmos 00:03: RTC can wake from S4
[    2.120864] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.120887] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.120974] device-mapper: uevent: version 1.0.3
[    2.121052] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    2.121060] cpuidle: using governor ladder
[    2.121062] cpuidle: using governor menu
[    2.121064] EFI Variables Facility v0.08 2004-May-17
[    2.121325] TCP cubic registered
[    2.121441] NET: Registered protocol family 10
[    2.121961] NET: Registered protocol family 17
[    2.121965] Registering the dns_resolver key type
[    2.122098] PM: Hibernation image not present or could not be loaded.
[    2.122112] registered taskstats version 1
[    2.129376]   Magic number: 5:923:295
[    2.129433] tty tty28: hash matches
[    2.129495] rtc_cmos 00:03: setting system clock to 2013-11-14 20:17:13 UTC (1384460233)
[    2.129766] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.129768] EDD information not available.
[    2.392119] ata2: SATA link down (SStatus 0 SControl 300)
[    2.402717] ata6: SATA link down (SStatus 0 SControl 300)
[    2.402756] ata1: SATA link down (SStatus 0 SControl 300)
[    2.540035] usb 2-2: new high-speed USB device number 3 using ehci_hcd
[    2.548070] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.556276] ata5.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[    2.556279] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.564250] ata5.00: configured for UDMA/133
[    2.672680] hub 2-2:1.0: USB hub found
[    2.672761] hub 2-2:1.0: 4 ports detected
[    2.876101] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.876115] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.880091] Refined TSC clocksource calibration: 2133.333 MHz.
[    2.880097] Switching to clocksource tsc
[    2.892279] ata4.00: ATA-7: ST3250823AS, 3.02, max UDMA/133
[    2.892283] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.892289] ata4.01: ATAPI: Optiarc DVD RW AD-7170S, 1.00, max UDMA/66
[    2.900267] ata4.00: configured for UDMA/133
[    2.916140] ata4.01: configured for UDMA/66
[    2.932060] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.932074] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.995787] ata3.00: ATA-8: ST3000DM001-9YN166, CC4B, max UDMA/133
[    2.995791] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.995929] ata3.01: ATA-8: WDC WD2001FASS-00W2B0, 01.00101, max UDMA/133
[    2.995933] ata3.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.012297] ata3.00: configured for UDMA/133
[    3.021069] ata3.01: configured for UDMA/133
[    3.021205] scsi 2:0:0:0: Direct-Access     ATA      ST3000DM001-9YN1 CC4B PQ: 0 ANSI: 5
[    3.021359] sd 2:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    3.021363] sd 2:0:0:0: [sda] 4096-byte physical blocks
[    3.021394] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    3.021419] sd 2:0:0:0: [sda] Write Protect is off
[    3.021423] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.021447] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.021495] scsi 2:0:1:0: Direct-Access     ATA      WDC WD2001FASS-0 01.0 PQ: 0 ANSI: 5
[    3.021606] sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    3.021629] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    3.021658] sd 2:0:1:0: [sdb] Write Protect is off
[    3.021662] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.021689] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.021730] scsi 3:0:0:0: Direct-Access     ATA      ST3250823AS      3.02 PQ: 0 ANSI: 5
[    3.021877] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    3.022450] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.022861] scsi 3:0:1:0: CD-ROM            Optiarc  DVD RW AD-7170S  1.00 PQ: 0 ANSI: 5
[    3.022910] sd 3:0:0:0: [sdc] Write Protect is off
[    3.022914] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.022947] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.024103] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[    3.026705] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.026710] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.026866] sr 3:0:1:0: Attached scsi CD-ROM sr0
[    3.026949] sr 3:0:1:0: Attached scsi generic sg3 type 5
[    3.027062] scsi 4:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    3.027167] sd 4:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.027203] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    3.027236] sd 4:0:0:0: [sdd] Write Protect is off
[    3.027240] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.027278] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.044773]  sdc: sdc1
[    3.045271] sd 3:0:0:0: [sdc] Attached SCSI disk
[    3.059238]  sdd: sdd1
[    3.059526] sd 4:0:0:0: [sdd] Attached SCSI disk
[    3.456032] usb 6-1: new full-speed USB device number 2 using uhci_hcd
[    3.610892]  sdb: sdb1
[    3.641243] sd 2:0:1:0: [sdb] Attached SCSI disk
[    3.712139] usb 2-2.1: new full-speed USB device number 5 using ehci_hcd
[    3.717011]  sda: sda1 sda2 sda3 sda4
[    3.717436] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.719138] Freeing unused kernel memory: 924k freed
[    3.719381] Write protecting the kernel read-only data: 12288k
[    3.725134] Freeing unused kernel memory: 1588k freed
[    3.729854] Freeing unused kernel memory: 1188k freed
[    3.748732] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    3.748974] zram: num_devices not specified. Using default: 1
[    3.748976] zram: Creating 1 devices ...
[    3.752790] udevd[106]: starting version 175
[    3.825503] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.825540] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    3.829008] scsi6 : pata_jmicron
[    3.829502] scsi7 : pata_jmicron
[    3.830041] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    3.830045] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    3.862148] sky2: driver version 1.30
[    3.862185] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.862199] sky2 0000:02:00.0: setting latency timer to 64
[    3.862228] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
[    3.862311] sky2 0000:02:00.0: irq 44 for MSI/MSI-X
[    3.862840] sky2 0000:02:00.0: eth0: addr 00:18:f3:75:79:55
[    3.873008] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input2
[    3.873128] generic-usb 0003:046D:C526.0004: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    3.879001] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input3
[    3.879545] generic-usb 0003:046D:C526.0005: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    3.879601] usbcore: registered new interface driver usbhid
[    3.879603] usbhid: USB HID core driver
[    3.884629] skge 0000:05:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.884674] skge: 1.14 addr 0xfbff4000 irq 19 chip Yukon-Lite rev 9
[    3.885203] skge 0000:05:04.0: eth1: addr 00:18:f3:75:5b:0b
[    3.894305] Adding 2540708k swap on /dev/zram0.  Priority:100 extents:1 across:2540708k SS
[    3.924221] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input2
[    4.154860] firewire_ohci 0000:05:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.208097] firewire_ohci: Added fw-ohci device 0000:05:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    4.708149] firewire_core: created device fw0: GUID 0011d80000e7de2f, S400
[    6.004120] Btrfs loaded
[    6.009938] xor: automatically using best checksumming function: generic_sse
[    6.028005]    generic_sse:  7797.000 MB/sec
[    6.028007] xor: using function: generic_sse (7797.000 MB/sec)
[    6.028609] device-mapper: dm-raid45: initialized v0.2594b
[    7.415199] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.240671] Adding 4882808k swap on /dev/sda3.  Priority:-1 extents:1 across:4882808k 
[   10.811957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.811965] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.868731] udevd[448]: starting version 175
[   11.977910] lp: driver loaded but no devices found
[   12.414398] Buffer I/O error on device zram0, logical block 635177
[   12.414434] Buffer I/O error on device zram0, logical block 635177
[   12.414526] Buffer I/O error on device zram0, logical block 635177
[   12.414560] Buffer I/O error on device zram0, logical block 635177
[   12.414593] Buffer I/O error on device zram0, logical block 635177
[   12.414626] Buffer I/O error on device zram0, logical block 635177
[   12.414661] Buffer I/O error on device zram0, logical block 635177
[   12.414718] Buffer I/O error on device zram0, logical block 635177
[   12.414751] Buffer I/O error on device zram0, logical block 635177
[   12.414790] Buffer I/O error on device zram0, logical block 635177
[   12.510274] nvidia: module license 'NVIDIA' taints kernel.
[   12.510279] Disabling lock debugging due to kernel taint
[   12.550382] device-mapper: multipath: version 1.3.1 loaded
[   12.756990] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.756999] nvidia 0000:01:00.0: setting latency timer to 64
[   12.757004] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.757248] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
[   12.796629] udevd[628]: renamed network interface eth0 to rename2
[   12.816564] udevd[643]: renamed network interface eth1 to eth2
[   12.856580] udevd[628]: renamed network interface rename2 to eth1
[   13.993520] Bluetooth: Core ver 2.16
[   13.993593] NET: Registered protocol family 31
[   13.993596] Bluetooth: HCI device and connection manager initialized
[   13.993599] Bluetooth: HCI socket layer initialized
[   13.993601] Bluetooth: L2CAP socket layer initialized
[   13.993607] Bluetooth: SCO socket layer initialized
[   14.087089] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.087409] usbcore: registered new interface driver btusb
[   14.317502] Bluetooth: can't load firmware, may not work correctly
[   14.431952] snd_oxygen 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.748762] init: udev-fallback-graphics main process (1016) terminated with status 1
[   16.202959] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.036129] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   17.434807] init: failsafe main process (1063) killed by TERM signal
[   18.365309] audit_printk_skb: 27 callbacks suppressed
[   18.365313] type=1400 audit(1384460249.733:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1125 comm="apparmor_parser"
[   18.365756] type=1400 audit(1384460249.733:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1125 comm="apparmor_parser"
[   18.366006] type=1400 audit(1384460249.733:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1125 comm="apparmor_parser"
[   18.425284] type=1400 audit(1384460249.793:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1124 comm="apparmor_parser"
[   18.425689] type=1400 audit(1384460249.793:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1124 comm="apparmor_parser"
[   18.477467] type=1400 audit(1384460249.845:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1128 comm="apparmor_parser"
[   18.477996] type=1400 audit(1384460249.845:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1128 comm="apparmor_parser"
[   18.638595] type=1400 audit(1384460250.005:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1126 comm="apparmor_parser"
[   18.643858] type=1400 audit(1384460250.009:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1126 comm="apparmor_parser"
[   18.645913] type=1400 audit(1384460250.013:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1126 comm="apparmor_parser"
[   18.936580] ppdev: user-space parallel port driver
[   19.362575] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.362579] Bluetooth: BNEP filters: protocol multicast
[   19.543498] Bluetooth: RFCOMM TTY layer initialized
[   19.543504] Bluetooth: RFCOMM socket layer initialized
[   19.543506] Bluetooth: RFCOMM ver 1.11
[   19.867500] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   21.105300] sky2 0000:02:00.0: eth1: enabling interface
[   21.106185] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.106905] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.109179] skge 0000:05:04.0: eth2: enabling interface
[   23.551910] sky2 0000:02:00.0: eth1: Link is up at 1000 Mbps, full duplex, flow control both
[   23.552771] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   33.363722] input: Logitech Unifying Device. Wireless PID:200a as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.2/0003:046D:C52B.0003/input/input4
[   33.363839] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:200a] on usb-0000:00:1d.0-1:1
[   34.992044] eth1: no IPv6 routers present
[31563.035045] sky2 0000:02:00.0: eth1: disabling interface
[31563.040585] skge 0000:05:04.0: eth2: disabling interface
[31564.817118] init: anacron main process (5641) killed by TERM signal
[31566.153204] PM: Syncing filesystems ... done.
[31566.195150] PM: Preparing system for mem sleep
[31566.195165] Freezing user space processes ... (elapsed 0.01 seconds) done.
[31566.208102] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[31566.224077] PM: Entering mem sleep
[31566.224112] Suspending console(s) (use no_console_suspend to debug)
[31566.224737] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[31566.224855] sd 4:0:0:0: [sdd] Stopping disk
[31566.224979] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[31566.225070] sd 3:0:0:0: [sdc] Stopping disk
[31566.225189] sd 2:0:1:0: [sdb] Synchronizing SCSI cache
[31566.225308] sd 2:0:1:0: [sdb] Stopping disk
[31566.227668] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[31566.228377] serial 00:06: disabled
[31566.228383] serial 00:06: wake-up capability disabled by ACPI
[31566.229127] ACPI handle has no context!
[31566.229137] snd_oxygen 0000:05:01.0: PCI INT A disabled
[31566.229173] ACPI handle has no context!
[31566.229238] pata_jmicron 0000:03:00.1: PCI INT B disabled
[31566.229338] ahci 0000:03:00.0: PCI INT A disabled
[31566.232176] ata_piix 0000:00:1f.5: PCI INT B disabled
[31566.240079] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[31566.240091] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[31566.264078] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[31566.264084] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[31566.264129] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[31566.268037] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[31566.272035] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[31566.702299] PM: suspend of drv:sd dev:2:0:1:0 complete after 477.110 msecs
[31566.702323] PM: suspend of drv:scsi dev:target2:0:1 complete after 474.699 msecs
[31566.877159] sd 2:0:0:0: [sda] Stopping disk
[31567.883529] PM: suspend of drv:sd dev:2:0:0:0 complete after 1655.863 msecs
[31567.883544] PM: suspend of drv:scsi dev:target2:0:0 complete after 1655.845 msecs
[31567.883557] PM: suspend of drv:scsi dev:host2 complete after 1655.590 msecs
[31567.883658] ata_piix 0000:00:1f.2: PCI INT B disabled
[31567.896037] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 1663.826 msecs
[31567.896058] PM: suspend of drv: dev:pci0000:00 complete after 1663.595 msecs
[31567.896070] PM: suspend of devices complete after 1671.609 msecs
[31567.896074] PM: suspend devices took 1.672 seconds
[31567.896363] skge 0000:05:04.0: PME# enabled
[31567.896375] pci 0000:00:1e.0: wake-up capability enabled by ACPI
[31568.068078] PM: late suspend of drv:sky2 dev:0000:02:00.0 complete after 156.049 msecs
[31568.068204] ehci_hcd 0000:00:1d.7: PME# enabled
[31568.068213] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[31568.084090] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[31568.084132] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[31568.084172] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[31568.084208] ehci_hcd 0000:00:1a.7: PME# enabled
[31568.084214] ehci_hcd 0000:00:1a.7: wake-up capability enabled by ACPI
[31568.100072] uhci_hcd 0000:00:1a.1: wake-up capability enabled by ACPI
[31568.100112] uhci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[31568.100174] PM: late suspend of devices complete after 204.096 msecs
[31568.100439] ACPI: Preparing to enter system sleep state S3
[31568.100646] PM: Saving platform NVS memory
[31568.101105] Disabling non-boot CPUs ...
[31568.204022] CPU 1 is now offline
[31568.204554] ACPI: Low-level resume complete
[31568.204554] PM: Restoring platform NVS memory
[31568.204554] Enabling non-boot CPUs ...
[31568.204554] Booting Node 0 Processor 1 APIC 0x1
[31568.204554] smpboot cpu 1: start_ip = 9a000
[31568.102391] Calibrating delay loop (skipped) already calibrated this CPU
[31568.236106] NMI watchdog enabled, takes one hw-pmu counter.
[31568.240056] CPU1 is up
[31568.241412] ACPI: Waking up from system sleep state S3
[31568.241960] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0xa0100, writing 0xa010b)
[31568.241971] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[31568.242004] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[31568.242026] uhci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[31568.242046] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[31568.242065] uhci_hcd 0000:00:1a.1: wake-up capability disabled by ACPI
[31568.242092] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[31568.242106] ehci_hcd 0000:00:1a.7: wake-up capability disabled by ACPI
[31568.242111] ehci_hcd 0000:00:1a.7: PME# disabled
[31568.242123] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[31568.242132] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xc080c050)
[31568.242136] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x1010)
[31568.242145] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
[31568.242177] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[31568.242185] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc041c031)
[31568.242195] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[31568.242227] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x20200, writing 0x2020a)
[31568.242235] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc021c011)
[31568.242246] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[31568.242284] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[31568.242303] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[31568.242323] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[31568.242342] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[31568.242361] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[31568.242380] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[31568.242407] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[31568.242421] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[31568.242426] ehci_hcd 0000:00:1d.7: PME# disabled
[31568.242434] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x20000, writing 0x200ff)
[31568.242517] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xc0000000)
[31568.242559] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfbce0000, writing 0x0)
[31568.242568] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x8, writing 0x0)
[31568.242604] ahci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[31568.242613] ahci 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbee0000)
[31568.242622] ahci 0000:03:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xfbefe000)
[31568.242628] ahci 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x0)
[31568.242633] ahci 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x0)
[31568.242639] ahci 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x0)
[31568.242645] ahci 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x0)
[31568.242650] ahci 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x0)
[31568.242656] ahci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x800008)
[31568.242662] ahci 0000:03:00.0: restoring config space at offset 0x2 (was 0x1018502, writing 0x1060102)
[31568.242668] ahci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[31568.242716] pata_jmicron 0000:03:00.1: restoring config space at offset 0x8 (was 0x1, writing 0xd401)
[31568.242722] pata_jmicron 0000:03:00.1: restoring config space at offset 0x7 (was 0x1, writing 0xd481)
[31568.242727] pata_jmicron 0000:03:00.1: restoring config space at offset 0x6 (was 0x1, writing 0xd801)
[31568.242733] pata_jmicron 0000:03:00.1: restoring config space at offset 0x5 (was 0x1, writing 0xd881)
[31568.242739] pata_jmicron 0000:03:00.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[31568.242748] pata_jmicron 0000:03:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100005)
[31568.242782] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[31568.242790] sky2 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbdc0000)
[31568.242803] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xc801)
[31568.242809] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfbdfc004)
[31568.242815] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[31568.242821] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[31568.242876] snd_oxygen 0000:05:01.0: restoring config space at offset 0x4 (was 0x7fffe801, writing 0xe801)
[31568.242883] snd_oxygen 0000:05:01.0: restoring config space at offset 0x1 (was 0x2100005, writing 0x2100001)
[31568.242901] firewire_ohci 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010e)
[31568.242916] firewire_ohci 0000:05:03.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbff8000)
[31568.242921] firewire_ohci 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbfff800)
[31568.242925] firewire_ohci 0000:05:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[31568.242931] firewire_ohci 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[31568.242951] skge 0000:05:04.0: restoring config space at offset 0xf (was 0x1f170100, writing 0x1f17010f)
[31568.242957] skge 0000:05:04.0: restoring config space at offset 0xc (was 0x0, writing 0xfbfc0000)
[31568.242969] skge 0000:05:04.0: restoring config space at offset 0x5 (was 0x1, writing 0xe401)
[31568.242973] skge 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbff4000)
[31568.242978] skge 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[31568.242984] skge 0000:05:04.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00017)
[31568.243197] PM: early resume of devices complete after 1.304 msecs
[31568.243263] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[31568.243269] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[31568.243289] usb usb3: root hub lost power or was reset
[31568.243301] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[31568.243306] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[31568.243325] usb usb4: root hub lost power or was reset
[31568.243337] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[31568.243342] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[31568.243372] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[31568.243378] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[31568.243397] usb usb5: root hub lost power or was reset
[31568.243403] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[31568.243413] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[31568.243409] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[31568.243418] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[31568.243435] usb usb6: root hub lost power or was reset
[31568.243444] usb usb7: root hub lost power or was reset
[31568.243467] pci 0000:00:1e.0: setting latency timer to 64
[31568.243473] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[31568.243479] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[31568.243527] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[31568.243531] ata_piix 0000:00:1f.2: setting latency timer to 64
[31568.243559] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[31568.243574] ata_piix 0000:00:1f.5: setting latency timer to 64
[31568.243802] snd_oxygen 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[31568.244212] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[31568.244265] ahci 0000:03:00.0: setting latency timer to 64
[31568.244391] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[31568.244443] pata_jmicron 0000:03:00.1: setting latency timer to 64
[31568.249265] serial 00:06: activated
[31568.251490] pci 0000:00:1e.0: wake-up capability disabled by ACPI
[31568.251496] skge 0000:05:04.0: PME# disabled
[31568.256293] sd 2:0:0:0: [sda] Starting disk
[31568.256361] sd 2:0:1:0: [sdb] Starting disk
[31568.256416] sd 3:0:0:0: [sdc] Starting disk
[31568.256476] sd 4:0:0:0: [sdd] Starting disk
[31568.372056] PM: resume of drv:hub dev:3-0:1.0 complete after 120.005 msecs
[31568.372064] PM: resume of drv: dev:ep_00 complete after 120.005 msecs
[31568.372069] PM: resume of drv:hub dev:4-0:1.0 complete after 119.993 msecs
[31568.372076] PM: resume of drv: dev:ep_00 complete after 119.987 msecs
[31568.372081] PM: resume of drv: dev:ep_81 complete after 120.025 msecs
[31568.372086] PM: resume of drv: dev:ep_81 complete after 120.004 msecs
[31568.376077] PM: resume of drv:hub dev:7-0:1.0 complete after 119.957 msecs
[31568.376084] PM: resume of drv: dev:ep_00 complete after 119.898 msecs
[31568.376089] PM: resume of drv: dev:ep_81 complete after 119.925 msecs
[31568.396353] PM: resume of drv:btusb dev:2-2.1:1.0 complete after 139.520 msecs
[31568.396362] PM: resume of drv:btusb dev:2-2.1:1.1 complete after 139.449 msecs
[31568.396370] PM: resume of drv:usb dev:2-2.1:1.2 complete after 139.396 msecs
[31568.396378] PM: resume of drv:usb dev:2-2.1:1.3 complete after 139.341 msecs
[31568.396383] PM: resume of drv: dev:ep_00 complete after 139.326 msecs
[31568.396388] PM: resume of drv: dev:ep_81 complete after 139.536 msecs
[31568.396393] PM: resume of drv: dev:ep_82 complete after 139.520 msecs
[31568.396398] PM: resume of drv: dev:ep_02 complete after 139.505 msecs
[31568.396403] PM: resume of drv: dev:ep_83 complete after 139.470 msecs
[31568.396408] PM: resume of drv: dev:ep_03 complete after 139.455 msecs
[31568.396413] PM: resume of drv: dev:ep_84 complete after 139.420 msecs
[31568.396418] PM: resume of drv: dev:ep_04 complete after 139.403 msecs
[31568.480030] PM: resume of drv:hub dev:5-0:1.0 complete after 223.971 msecs
[31568.480038] PM: resume of drv: dev:ep_00 complete after 223.965 msecs
[31568.480057] PM: resume of drv:hub dev:6-0:1.0 complete after 223.968 msecs
[31568.480065] PM: resume of drv: dev:ep_00 complete after 223.962 msecs
[31568.480078] PM: resume of drv: dev:ep_81 complete after 224.013 msecs
[31568.480084] PM: resume of drv: dev:ep_81 complete after 223.988 msecs
[31568.492200] PM: resume of drv:snd_oxygen dev:0000:05:01.0 complete after 248.412 msecs
[31568.579376] ata6: SATA link down (SStatus 0 SControl 300)
[31568.579434] ata1: SATA link down (SStatus 0 SControl 300)
[31568.580040] ata2: SATA link down (SStatus 0 SControl 300)
[31568.592021] usb 5-1: reset full-speed USB device number 2 using uhci_hcd
[31568.707071] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 463.600 msecs
[31568.707082] firewire_core: skipped bus generations, destroying all nodes
[31568.753073] PM: resume of drv:usbhid dev:5-1:1.0 complete after 496.523 msecs
[31568.753080] PM: resume of drv: dev:ep_00 complete after 496.403 msecs
[31568.753085] PM: resume of drv:usbhid dev:5-1:1.1 complete after 496.497 msecs
[31568.753103] PM: resume of drv: dev:ep_81 complete after 496.534 msecs
[31568.753108] PM: resume of drv:usbhid dev:5-1:1.2 complete after 496.476 msecs
[31568.753119] PM: resume of drv: dev:ep_82 complete after 496.511 msecs
[31568.753124] PM: resume of drv: dev:ep_83 complete after 496.473 msecs
[31568.840044] usb 6-1: reset full-speed USB device number 2 using uhci_hcd
[31568.994109] PM: resume of drv:usbhid dev:6-1:1.0 complete after 737.395 msecs
[31568.994118] PM: resume of drv: dev:ep_00 complete after 737.323 msecs
[31568.994124] PM: resume of drv:usbhid dev:6-1:1.1 complete after 737.367 msecs
[31568.994135] PM: resume of drv: dev:ep_81 complete after 737.402 msecs
[31568.994140] PM: resume of drv: dev:ep_82 complete after 737.363 msecs
[31569.204277] firewire_core: rediscovered device fw0
[31573.772031] ata5: link is slow to respond, please be patient (ready=0)
[31574.084279] ata3.00: link is slow to respond, please be patient (ready=0)
[31574.092031] ata4.00: link is slow to respond, please be patient (ready=0)
[31574.372079] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[31574.372093] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[31574.380150] ata4.01: ACPI cmd ef/03:44:00:00:00:b0 (SET FEATURES) filtered out
[31574.380155] ata4.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[31574.388154] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[31574.388159] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[31574.388275] ata4.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[31574.412284] ata4.00: configured for UDMA/133
[31574.428153] ata4.01: configured for UDMA/66
[31574.446197] PM: resume of drv:sd dev:3:0:0:0 complete after 6189.780 msecs
[31574.446209] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 6189.760 msecs
[31574.556063] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[31574.564146] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[31574.564151] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[31574.564247] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[31574.588290] ata5.00: configured for UDMA/133
[31574.604551] PM: resume of drv:sd dev:4:0:0:0 complete after 6348.072 msecs
[31574.604562] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 6348.054 msecs
[31578.284031] ata3.00: SRST failed (errno=-16)
[31584.120031] ata3.00: link is slow to respond, please be patient (ready=0)
[31588.096073] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[31588.096087] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[31588.104153] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 (SET FEATURES) filtered out
[31588.104158] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[31588.104590] ata3.01: ACPI cmd c6/00:10:00:00:00:b0 (SET MULTIPLE MODE) succeeded
[31588.144203] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[31588.144207] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[31588.177124] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[31588.200300] ata3.00: configured for UDMA/133
[31588.208733] ata3.01: configured for UDMA/133
[31588.218521] PM: resume of drv:sd dev:2:0:1:0 complete after 19962.159 msecs
[31588.218533] PM: resume of drv:scsi_device dev:2:0:1:0 complete after 19962.138 msecs
[31588.224338] PM: resume of drv:sd dev:2:0:0:0 complete after 19968.045 msecs
[31588.224352] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 19968.016 msecs
[31588.224361] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 19961.043 msecs
[31588.224597] PM: resume of devices complete after 19981.362 msecs
[31588.224839] PM: resume devices took 19.984 seconds
[31588.224841] ------------[ cut here ]------------
[31588.224847] WARNING: at /build/buildd/linux-3.2.0/kernel/power/suspend_test.c:53 suspend_test_finish+0x86/0x90()
[31588.224849] Hardware name: System Product Name
[31588.224850] Component: resume devices, time: 19984
[31588.224852] Modules linked in: rfcomm bnep parport_pc ppdev binfmt_misc snd_oxygen snd_oxygen_lib snd_pcm snd_page_alloc snd_mpu401_uart btusb bluetooth snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) dm_multipath psmouse serio_raw mac_hid asus_atk0110 lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c firewire_ohci firewire_core hid_logitech_dj skge crc_itu_t usbhid hid sky2 pata_jmicron zram(C)
[31588.224884] Pid: 5553, comm: pm-suspend Tainted: P         C O 3.2.0-56-generic #86-Ubuntu
[31588.224886] Call Trace:
[31588.224891]  [<ffffffff810681df>] warn_slowpath_common+0x7f/0xc0
[31588.224895]  [<ffffffff810682d6>] warn_slowpath_fmt+0x46/0x50
[31588.224898]  [<ffffffff810acbb6>] suspend_test_finish+0x86/0x90
[31588.224901]  [<ffffffff810ac8ab>] suspend_devices_and_enter+0x10b/0x200
[31588.224904]  [<ffffffff810aca71>] enter_state+0xd1/0x110
[31588.224906]  [<ffffffff810ab427>] state_store+0xb7/0x130
[31588.224910]  [<ffffffff813104af>] kobj_attr_store+0xf/0x30
[31588.224914]  [<ffffffff811eea1f>] sysfs_write_file+0xef/0x170
[31588.224917]  [<ffffffff8117a543>] vfs_write+0xb3/0x180
[31588.224920]  [<ffffffff8117a86a>] sys_write+0x4a/0x90
[31588.224924]  [<ffffffff81669802>] system_call_fastpath+0x16/0x1b
[31588.224926] ---[ end trace 9e4141bbdeb5724d ]---
[31588.224982] PM: Finishing wakeup.
[31588.224983] Restarting tasks ... done.
[31589.201303] sky2 0000:02:00.0: eth1: enabling interface
[31589.202460] ADDRCONF(NETDEV_UP): eth1: link is not ready
[31589.205919] skge 0000:05:04.0: eth2: enabling interface
[31589.210215] ADDRCONF(NETDEV_UP): eth2: link is not ready
[31591.667651] sky2 0000:02:00.0: eth1: Link is up at 1000 Mbps, full duplex, flow control both
[31591.668724] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[31602.096028] eth1: no IPv6 routers present
[75920.576506] sky2 0000:02:00.0: eth1: disabling interface
[75920.586346] skge 0000:05:04.0: eth2: disabling interface
[75923.129853] PM: Syncing filesystems ... done.
[75923.173189] PM: Preparing system for mem sleep
[75923.173204] Freezing user space processes ... (elapsed 0.01 seconds) done.
[75923.188094] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[75923.204081] PM: Entering mem sleep
[75923.204119] Suspending console(s) (use no_console_suspend to debug)
[75923.207557] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[75923.207652] sd 4:0:0:0: [sdd] Stopping disk
[75923.207735] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[75923.207802] sd 2:0:1:0: [sdb] Synchronizing SCSI cache
[75923.207859] sd 3:0:0:0: [sdc] Stopping disk
[75923.207926] sd 2:0:1:0: [sdb] Stopping disk
[75923.207990] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[75923.208315] serial 00:06: disabled
[75923.208321] serial 00:06: wake-up capability disabled by ACPI
[75923.209064] ACPI handle has no context!
[75923.209074] snd_oxygen 0000:05:01.0: PCI INT A disabled
[75923.209111] ACPI handle has no context!
[75923.209179] pata_jmicron 0000:03:00.1: PCI INT B disabled
[75923.209276] ahci 0000:03:00.0: PCI INT A disabled
[75923.212184] ata_piix 0000:00:1f.5: PCI INT B disabled
[75923.220168] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[75923.220179] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[75923.248098] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[75923.248132] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[75923.248165] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[75923.252039] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[75923.252045] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[75923.631575] PM: suspend of drv:sd dev:2:0:1:0 complete after 423.773 msecs
[75923.631599] PM: suspend of drv:scsi dev:target2:0:1 complete after 423.614 msecs
[75923.829367] sd 2:0:0:0: [sda] Stopping disk
[75924.836104] PM: suspend of drv:sd dev:2:0:0:0 complete after 1628.116 msecs
[75924.836120] PM: suspend of drv:scsi dev:target2:0:0 complete after 1628.101 msecs
[75924.836134] PM: suspend of drv:scsi dev:host2 complete after 1627.876 msecs
[75924.836227] ata_piix 0000:00:1f.2: PCI INT B disabled
[75924.852035] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 1639.905 msecs
[75924.852050] PM: suspend of drv: dev:pci0000:00 complete after 1639.522 msecs
[75924.852057] PM: suspend of devices complete after 1647.593 msecs
[75924.852061] PM: suspend devices took 1.648 seconds
[75924.852352] skge 0000:05:04.0: PME# enabled
[75924.852363] pci 0000:00:1e.0: wake-up capability enabled by ACPI
[75925.024071] PM: late suspend of drv:sky2 dev:0000:02:00.0 complete after 156.036 msecs
[75925.024196] ehci_hcd 0000:00:1d.7: PME# enabled
[75925.024205] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[75925.040087] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[75925.040130] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[75925.040170] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[75925.040302] ehci_hcd 0000:00:1a.7: PME# enabled
[75925.040307] ehci_hcd 0000:00:1a.7: wake-up capability enabled by ACPI
[75925.056061] uhci_hcd 0000:00:1a.1: wake-up capability enabled by ACPI
[75925.056102] uhci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[75925.056181] PM: late suspend of devices complete after 204.117 msecs
[75925.056447] ACPI: Preparing to enter system sleep state S3
[75925.056652] PM: Saving platform NVS memory
[75925.057120] Disabling non-boot CPUs ...
[75925.160021] CPU 1 is now offline
[75925.160519] ACPI: Low-level resume complete
[75925.160519] PM: Restoring platform NVS memory
[75925.160519] Enabling non-boot CPUs ...
[75925.160519] Booting Node 0 Processor 1 APIC 0x1
[75925.160519] smpboot cpu 1: start_ip = 9a000
[75925.058407] Calibrating delay loop (skipped) already calibrated this CPU
[75925.192082] NMI watchdog enabled, takes one hw-pmu counter.
[75925.196062] CPU1 is up
[75925.197421] ACPI: Waking up from system sleep state S3
[75925.197968] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0xa0100, writing 0xa010b)
[75925.197978] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[75925.198011] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[75925.198034] uhci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[75925.198053] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[75925.198073] uhci_hcd 0000:00:1a.1: wake-up capability disabled by ACPI
[75925.198100] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[75925.198114] ehci_hcd 0000:00:1a.7: wake-up capability disabled by ACPI
[75925.198119] ehci_hcd 0000:00:1a.7: PME# disabled
[75925.198131] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[75925.198140] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xc080c050)
[75925.198145] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x20001010)
[75925.198153] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
[75925.198185] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[75925.198193] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc041c031)
[75925.198203] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[75925.198235] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x20200, writing 0x2020a)
[75925.198243] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc021c011)
[75925.198253] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[75925.198292] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[75925.198311] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[75925.198330] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[75925.198349] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[75925.198369] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[75925.198387] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[75925.198414] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[75925.198428] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[75925.198432] ehci_hcd 0000:00:1d.7: PME# disabled
[75925.198441] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x20000, writing 0x200ff)
[75925.198524] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xc0000000)
[75925.198565] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfbce0000, writing 0x0)
[75925.198575] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x8, writing 0x0)
[75925.198611] ahci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[75925.198620] ahci 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbee0000)
[75925.198629] ahci 0000:03:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xfbefe000)
[75925.198634] ahci 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x0)
[75925.198640] ahci 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x0)
[75925.198646] ahci 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x0)
[75925.198651] ahci 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x0)
[75925.198657] ahci 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x0)
[75925.198662] ahci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x800008)
[75925.198668] ahci 0000:03:00.0: restoring config space at offset 0x2 (was 0x1018502, writing 0x1060102)
[75925.198674] ahci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[75925.198722] pata_jmicron 0000:03:00.1: restoring config space at offset 0x8 (was 0x1, writing 0xd401)
[75925.198728] pata_jmicron 0000:03:00.1: restoring config space at offset 0x7 (was 0x1, writing 0xd481)
[75925.198734] pata_jmicron 0000:03:00.1: restoring config space at offset 0x6 (was 0x1, writing 0xd801)
[75925.198739] pata_jmicron 0000:03:00.1: restoring config space at offset 0x5 (was 0x1, writing 0xd881)
[75925.198745] pata_jmicron 0000:03:00.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[75925.198754] pata_jmicron 0000:03:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100005)
[75925.198788] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[75925.198796] sky2 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbdc0000)
[75925.198809] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xc801)
[75925.198815] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfbdfc004)
[75925.198821] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[75925.198827] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[75925.198882] snd_oxygen 0000:05:01.0: restoring config space at offset 0x4 (was 0x7fffe801, writing 0xe801)
[75925.198889] snd_oxygen 0000:05:01.0: restoring config space at offset 0x1 (was 0x2100005, writing 0x2100001)
[75925.198907] firewire_ohci 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010e)
[75925.198922] firewire_ohci 0000:05:03.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbff8000)
[75925.198926] firewire_ohci 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbfff800)
[75925.198931] firewire_ohci 0000:05:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[75925.198937] firewire_ohci 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[75925.198956] skge 0000:05:04.0: restoring config space at offset 0xf (was 0x1f170100, writing 0x1f17010f)
[75925.198963] skge 0000:05:04.0: restoring config space at offset 0xc (was 0x0, writing 0xfbfc0000)
[75925.198974] skge 0000:05:04.0: restoring config space at offset 0x5 (was 0x1, writing 0xe401)
[75925.198979] skge 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbff4000)
[75925.198984] skge 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[75925.198989] skge 0000:05:04.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00017)
[75925.199204] PM: early resume of devices complete after 1.303 msecs
[75925.199272] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[75925.199279] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[75925.199299] usb usb3: root hub lost power or was reset
[75925.199311] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[75925.199316] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[75925.199335] usb usb4: root hub lost power or was reset
[75925.199347] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[75925.199353] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[75925.199383] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[75925.199389] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[75925.199408] usb usb5: root hub lost power or was reset
[75925.199419] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[75925.199424] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[75925.199424] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[75925.199430] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[75925.199446] usb usb6: root hub lost power or was reset
[75925.199460] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[75925.199456] usb usb7: root hub lost power or was reset
[75925.199467] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[75925.199468] pci 0000:00:1e.0: setting latency timer to 64
[75925.199482] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[75925.199495] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[75925.199491] ata_piix 0000:00:1f.2: setting latency timer to 64
[75925.199500] ata_piix 0000:00:1f.5: setting latency timer to 64
[75925.199519] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[75925.199525] ahci 0000:03:00.0: setting latency timer to 64
[75925.202867] serial 00:06: activated
[75925.206459] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[75925.206466] pata_jmicron 0000:03:00.1: setting latency timer to 64
[75925.206516] snd_oxygen 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[75925.206893] pci 0000:00:1e.0: wake-up capability disabled by ACPI
[75925.206900] skge 0000:05:04.0: PME# disabled
[75925.207182] sd 2:0:0:0: [sda] Starting disk
[75925.207235] sd 2:0:1:0: [sdb] Starting disk
[75925.207281] sd 3:0:0:0: [sdc] Starting disk
[75925.207334] sd 4:0:0:0: [sdd] Starting disk
[75925.324124] PM: resume of drv:hub dev:3-0:1.0 complete after 117.122 msecs
[75925.324132] PM: resume of drv: dev:ep_00 complete after 117.127 msecs
[75925.324137] PM: resume of drv:hub dev:4-0:1.0 complete after 117.123 msecs
[75925.324144] PM: resume of drv: dev:ep_00 complete after 117.125 msecs
[75925.324149] PM: resume of drv:hub dev:7-0:1.0 complete after 117.093 msecs
[75925.324156] PM: resume of drv: dev:ep_00 complete after 117.048 msecs
[75925.324161] PM: resume of drv: dev:ep_81 complete after 117.160 msecs
[75925.324166] PM: resume of drv: dev:ep_81 complete after 117.150 msecs
[75925.324171] PM: resume of drv: dev:ep_81 complete after 117.080 msecs
[75925.352359] PM: resume of drv:btusb dev:2-2.1:1.0 complete after 144.754 msecs
[75925.352369] PM: resume of drv:btusb dev:2-2.1:1.1 complete after 144.704 msecs
[75925.352377] PM: resume of drv:usb dev:2-2.1:1.2 complete after 144.666 msecs
[75925.352385] PM: resume of drv:usb dev:2-2.1:1.3 complete after 144.632 msecs
[75925.352390] PM: resume of drv: dev:ep_00 complete after 144.621 msecs
[75925.352395] PM: resume of drv: dev:ep_81 complete after 144.775 msecs
[75925.352400] PM: resume of drv: dev:ep_82 complete after 144.765 msecs
[75925.352405] PM: resume of drv: dev:ep_02 complete after 144.755 msecs
[75925.352410] PM: resume of drv: dev:ep_83 complete after 144.730 msecs
[75925.352415] PM: resume of drv: dev:ep_03 complete after 144.719 msecs
[75925.352420] PM: resume of drv: dev:ep_84 complete after 144.695 msecs
[75925.352425] PM: resume of drv: dev:ep_04 complete after 144.686 msecs
[75925.428031] PM: resume of drv:hub dev:5-0:1.0 complete after 221.002 msecs
[75925.428039] PM: resume of drv: dev:ep_00 complete after 221.006 msecs
[75925.428059] PM: resume of drv:hub dev:6-0:1.0 complete after 221.017 msecs
[75925.428066] PM: resume of drv: dev:ep_00 complete after 221.019 msecs
[75925.428079] PM: resume of drv: dev:ep_81 complete after 221.049 msecs
[75925.428085] PM: resume of drv: dev:ep_81 complete after 221.040 msecs
[75925.472204] PM: resume of drv:snd_oxygen dev:0000:05:01.0 complete after 265.688 msecs
[75925.531452] ata6: SATA link down (SStatus 0 SControl 300)
[75925.531492] ata1: SATA link down (SStatus 0 SControl 300)
[75925.532029] ata2: SATA link down (SStatus 0 SControl 300)
[75925.540020] usb 5-1: reset full-speed USB device number 2 using uhci_hcd
[75925.663932] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 464.427 msecs
[75925.663943] firewire_core: skipped bus generations, destroying all nodes
[75925.705049] PM: resume of drv:usbhid dev:5-1:1.0 complete after 497.651 msecs
[75925.705055] PM: resume of drv: dev:ep_00 complete after 497.564 msecs
[75925.705061] PM: resume of drv:usbhid dev:5-1:1.1 complete after 497.635 msecs
[75925.705078] PM: resume of drv: dev:ep_81 complete after 497.666 msecs
[75925.705083] PM: resume of drv:usbhid dev:5-1:1.2 complete after 497.624 msecs
[75925.705095] PM: resume of drv: dev:ep_82 complete after 497.654 msecs
[75925.705100] PM: resume of drv: dev:ep_83 complete after 497.627 msecs
[75925.792042] usb 6-1: reset full-speed USB device number 2 using uhci_hcd
[75925.946065] PM: resume of drv:usbhid dev:6-1:1.0 complete after 738.550 msecs
[75925.946074] PM: resume of drv: dev:ep_00 complete after 738.497 msecs
[75925.946080] PM: resume of drv:usbhid dev:6-1:1.1 complete after 738.531 msecs
[75925.946092] PM: resume of drv: dev:ep_81 complete after 738.563 msecs
[75925.946097] PM: resume of drv: dev:ep_82 complete after 738.535 msecs
[75926.160718] firewire_core: rediscovered device fw0
[75930.716031] ata5: link is slow to respond, please be patient (ready=0)
[75931.044031] ata3.00: link is slow to respond, please be patient (ready=0)
[75931.048288] ata4.00: link is slow to respond, please be patient (ready=0)
[75931.328358] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[75931.328372] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[75931.336149] ata4.01: ACPI cmd ef/03:44:00:00:00:b0 (SET FEATURES) filtered out
[75931.336154] ata4.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[75931.344153] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[75931.344158] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[75931.344263] ata4.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[75931.368262] ata4.00: configured for UDMA/133
[75931.384151] ata4.01: configured for UDMA/66
[75931.408589] PM: resume of drv:sd dev:3:0:0:0 complete after 6201.300 msecs
[75931.408610] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 6201.297 msecs
[75931.500064] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[75931.524148] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[75931.524153] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[75931.524239] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[75931.540261] ata5.00: configured for UDMA/133
[75931.556743] PM: resume of drv:sd dev:4:0:0:0 complete after 6349.402 msecs
[75931.556755] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 6349.389 msecs
[75935.244031] ata3.00: SRST failed (errno=-16)
[75941.080030] ata3.00: link is slow to respond, please be patient (ready=0)
[75944.944096] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[75944.944110] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[75944.952151] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 (SET FEATURES) filtered out
[75944.952157] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[75944.952849] ata3.01: ACPI cmd c6/00:10:00:00:00:b0 (SET MULTIPLE MODE) succeeded
[75945.060202] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[75945.060206] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[75946.487821] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[75946.544304] ata3.00: configured for UDMA/133
[75946.576614] ata3.01: configured for UDMA/133
[75946.587423] PM: resume of drv:sd dev:2:0:1:0 complete after 21380.180 msecs
[75946.587434] PM: resume of drv:scsi_device dev:2:0:1:0 complete after 21380.165 msecs
[75946.603804] PM: resume of drv:sd dev:2:0:0:0 complete after 21396.616 msecs
[75946.603818] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 21396.592 msecs
[75946.603826] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 21388.570 msecs
[75946.604066] PM: resume of devices complete after 21404.823 msecs
[75946.604307] PM: resume devices took 21.408 seconds
[75946.604308] ------------[ cut here ]------------
[75946.604314] WARNING: at /build/buildd/linux-3.2.0/kernel/power/suspend_test.c:53 suspend_test_finish+0x86/0x90()
[75946.604316] Hardware name: System Product Name
[75946.604318] Component: resume devices, time: 21408
[75946.604320] Modules linked in: rfcomm bnep parport_pc ppdev binfmt_misc snd_oxygen snd_oxygen_lib snd_pcm snd_page_alloc snd_mpu401_uart btusb bluetooth snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) dm_multipath psmouse serio_raw mac_hid asus_atk0110 lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c firewire_ohci firewire_core hid_logitech_dj skge crc_itu_t usbhid hid sky2 pata_jmicron zram(C)
[75946.604351] Pid: 8039, comm: pm-suspend Tainted: P        WC O 3.2.0-56-generic #86-Ubuntu
[75946.604353] Call Trace:
[75946.604358]  [<ffffffff810681df>] warn_slowpath_common+0x7f/0xc0
[75946.604362]  [<ffffffff810682d6>] warn_slowpath_fmt+0x46/0x50
[75946.604365]  [<ffffffff810acbb6>] suspend_test_finish+0x86/0x90
[75946.604368]  [<ffffffff810ac8ab>] suspend_devices_and_enter+0x10b/0x200
[75946.604371]  [<ffffffff810aca71>] enter_state+0xd1/0x110
[75946.604374]  [<ffffffff810ab427>] state_store+0xb7/0x130
[75946.604378]  [<ffffffff813104af>] kobj_attr_store+0xf/0x30
[75946.604382]  [<ffffffff811eea1f>] sysfs_write_file+0xef/0x170
[75946.604385]  [<ffffffff8117a543>] vfs_write+0xb3/0x180
[75946.604388]  [<ffffffff8117a86a>] sys_write+0x4a/0x90
[75946.604392]  [<ffffffff81669802>] system_call_fastpath+0x16/0x1b
[75946.604394] ---[ end trace 9e4141bbdeb5724e ]---
[75946.604451] PM: Finishing wakeup.
[75946.604452] Restarting tasks ... done.
[75947.895426] sky2 0000:02:00.0: eth1: enabling interface
[75947.896809] ADDRCONF(NETDEV_UP): eth1: link is not ready
[75947.900676] skge 0000:05:04.0: eth2: enabling interface
[75947.905300] ADDRCONF(NETDEV_UP): eth2: link is not ready
[75950.488742] sky2 0000:02:00.0: eth1: Link is up at 1000 Mbps, full duplex, flow control both
[75950.489793] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[75960.600013] eth1: no IPv6 routers present
[80789.408161] usb 2-2.4: new high-speed USB device number 6 using ehci_hcd
[80789.650547] Initializing USB Mass Storage driver...
[80789.650725] scsi8 : usb-storage 2-2.4:1.0
[80789.650820] usbcore: registered new interface driver usb-storage
[80789.650822] USB Mass Storage support registered.
[80790.649045] scsi 8:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[80790.649910] sd 8:0:0:0: Attached scsi generic sg5 type 0
[80790.654885] sd 8:0:0:0: [sde] Attached SCSI removable disk
[80831.192900] usb 2-2.4: USB disconnect, device number 6
[80834.464167] usb 2-2.4: new high-speed USB device number 7 using ehci_hcd
[80834.560181] scsi9 : usb-storage 2-2.4:1.0
[80835.561171] scsi 9:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[80835.562043] sd 9:0:0:0: Attached scsi generic sg5 type 0
[80835.566539] sd 9:0:0:0: [sde] Attached SCSI removable disk
[80892.889032] usb 2-2.4: USB disconnect, device number 7
[80904.608172] usb 2-2.4: new high-speed USB device number 8 using ehci_hcd
[80904.704563] scsi10 : usb-storage 2-2.4:1.1
[80904.920909] usb 2-2.4: USB disconnect, device number 8
[80905.632172] usb 2-2.4: new high-speed USB device number 9 using ehci_hcd
[80906.477915] usb 2-2.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71
[80906.485914] usb 2-2.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71
[80906.493911] usb 2-2.4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -71
[80906.712907] usb 2-2.4: USB disconnect, device number 9
[80906.912165] usb 2-2.4: new high-speed USB device number 10 using ehci_hcd
[80907.008818] scsi11 : usb-storage 2-2.4:1.2
[80907.224909] usb 2-2.4: USB disconnect, device number 10
[80907.936176] usb 2-2.4: new high-speed USB device number 11 using ehci_hcd
[81329.209680] usb 2-2.4: usbfs: process 10006 (go-mtpfs) did not claim interface 0 before use
[81329.284111] usb 2-2.4: reset high-speed USB device number 11 using ehci_hcd
[81329.377633] usb 2-2.4: usbfs: process 10006 (go-mtpfs) did not claim interface 0 before use
[81350.432332] usb 2-2.4: usbfs: process 9910 (go-mtpfs) did not claim interface 0 before use
[88005.849932] usb 2-2.4: USB disconnect, device number 11
[96180.875900] sky2 0000:02:00.0: eth1: disabling interface
[96180.886005] skge 0000:05:04.0: eth2: disabling interface
[96185.893389] PM: Syncing filesystems ... done.
[96185.946874] PM: Preparing system for mem sleep
[96185.946887] Freezing user space processes ... (elapsed 0.01 seconds) done.
[96185.960096] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[96185.976084] PM: Entering mem sleep
[96185.976130] Suspending console(s) (use no_console_suspend to debug)
[96185.976764] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[96185.976906] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[96185.977016] sd 2:0:1:0: [sdb] Synchronizing SCSI cache
[96185.977127] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[96185.979492] sd 2:0:1:0: [sdb] Stopping disk
[96185.979529] sd 3:0:0:0: [sdc] Stopping disk
[96185.979576] sd 4:0:0:0: [sdd] Stopping disk
[96185.980293] serial 00:06: disabled
[96185.980299] serial 00:06: wake-up capability disabled by ACPI
[96185.980368] ACPI handle has no context!
[96185.981073] snd_oxygen 0000:05:01.0: PCI INT A disabled
[96185.981104] ACPI handle has no context!
[96185.981240] ahci 0000:03:00.0: PCI INT A disabled
[96185.981289] pata_jmicron 0000:03:00.1: PCI INT B disabled
[96185.981388] ata_piix 0000:00:1f.5: PCI INT B disabled
[96185.992070] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[96185.992197] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[96186.000565] sd 2:0:0:0: [sda] Stopping disk
[96186.016097] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[96186.016103] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[96186.016156] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[96186.020036] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[96186.024035] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[96186.424903] PM: suspend of drv:sd dev:2:0:1:0 complete after 447.887 msecs
[96186.424926] PM: suspend of drv:scsi dev:target2:0:1 complete after 447.830 msecs
[96187.431271] PM: suspend of drv:sd dev:2:0:0:0 complete after 1454.145 msecs
[96187.431286] PM: suspend of drv:scsi dev:target2:0:0 complete after 1454.118 msecs
[96187.431299] PM: suspend of drv:scsi dev:host2 complete after 1451.476 msecs
[96187.431392] ata_piix 0000:00:1f.2: PCI INT B disabled
[96187.444057] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 1462.629 msecs
[96187.444072] PM: suspend of drv: dev:pci0000:00 complete after 1462.303 msecs
[96187.444080] PM: suspend of devices complete after 1467.606 msecs
[96187.444083] PM: suspend devices took 1.468 seconds
[96187.444374] skge 0000:05:04.0: PME# enabled
[96187.444385] pci 0000:00:1e.0: wake-up capability enabled by ACPI
[96187.616080] PM: late suspend of drv:sky2 dev:0000:02:00.0 complete after 156.052 msecs
[96187.616204] ehci_hcd 0000:00:1d.7: PME# enabled
[96187.616211] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[96187.632088] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[96187.632131] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[96187.632171] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[96187.632302] ehci_hcd 0000:00:1a.7: PME# enabled
[96187.632306] ehci_hcd 0000:00:1a.7: wake-up capability enabled by ACPI
[96187.648063] uhci_hcd 0000:00:1a.1: wake-up capability enabled by ACPI
[96187.648103] uhci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[96187.648183] PM: late suspend of devices complete after 204.096 msecs
[96187.648449] ACPI: Preparing to enter system sleep state S3
[96187.648654] PM: Saving platform NVS memory
[96187.649133] Disabling non-boot CPUs ...
[96187.752032] CPU 1 is now offline
[96187.752523] ACPI: Low-level resume complete
[96187.752523] PM: Restoring platform NVS memory
[96187.752523] Enabling non-boot CPUs ...
[96187.752523] Booting Node 0 Processor 1 APIC 0x1
[96187.752523] smpboot cpu 1: start_ip = 9a000
[96187.650431] Calibrating delay loop (skipped) already calibrated this CPU
[96187.784057] NMI watchdog enabled, takes one hw-pmu counter.
[96187.788052] CPU1 is up
[96187.789412] ACPI: Waking up from system sleep state S3
[96187.789956] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0xa0100, writing 0xa010b)
[96187.789966] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[96187.789999] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[96187.790022] uhci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[96187.790041] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[96187.790061] uhci_hcd 0000:00:1a.1: wake-up capability disabled by ACPI
[96187.790088] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[96187.790102] ehci_hcd 0000:00:1a.7: wake-up capability disabled by ACPI
[96187.790107] ehci_hcd 0000:00:1a.7: PME# disabled
[96187.790119] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[96187.790128] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xc080c050)
[96187.790132] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x1010)
[96187.790141] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
[96187.790172] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[96187.790181] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc041c031)
[96187.790191] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[96187.790222] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x20200, writing 0x2020a)
[96187.790231] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc021c011)
[96187.790241] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[96187.790279] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[96187.790298] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[96187.790318] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[96187.790337] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[96187.790356] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[96187.790374] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[96187.790401] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[96187.790415] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[96187.790419] ehci_hcd 0000:00:1d.7: PME# disabled
[96187.790428] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x20000, writing 0x200ff)
[96187.790511] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xc0000000)
[96187.790552] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfbce0000, writing 0x0)
[96187.790561] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x8, writing 0x0)
[96187.790598] ahci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[96187.790607] ahci 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbee0000)
[96187.790616] ahci 0000:03:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xfbefe000)
[96187.790621] ahci 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x0)
[96187.790627] ahci 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x0)
[96187.790633] ahci 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x0)
[96187.790638] ahci 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x0)
[96187.790644] ahci 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x0)
[96187.790649] ahci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x800008)
[96187.790655] ahci 0000:03:00.0: restoring config space at offset 0x2 (was 0x1018502, writing 0x1060102)
[96187.790661] ahci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[96187.790709] pata_jmicron 0000:03:00.1: restoring config space at offset 0x8 (was 0x1, writing 0xd401)
[96187.790715] pata_jmicron 0000:03:00.1: restoring config space at offset 0x7 (was 0x1, writing 0xd481)
[96187.790720] pata_jmicron 0000:03:00.1: restoring config space at offset 0x6 (was 0x1, writing 0xd801)
[96187.790726] pata_jmicron 0000:03:00.1: restoring config space at offset 0x5 (was 0x1, writing 0xd881)
[96187.790732] pata_jmicron 0000:03:00.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[96187.790741] pata_jmicron 0000:03:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100005)
[96187.790775] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[96187.790784] sky2 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbdc0000)
[96187.790796] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xc801)
[96187.790803] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfbdfc004)
[96187.790808] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[96187.790815] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[96187.790869] snd_oxygen 0000:05:01.0: restoring config space at offset 0x4 (was 0x7fffe801, writing 0xe801)
[96187.790876] snd_oxygen 0000:05:01.0: restoring config space at offset 0x1 (was 0x2100005, writing 0x2100001)
[96187.790893] firewire_ohci 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010e)
[96187.790908] firewire_ohci 0000:05:03.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbff8000)
[96187.790913] firewire_ohci 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbfff800)
[96187.790918] firewire_ohci 0000:05:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[96187.790924] firewire_ohci 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[96187.790943] skge 0000:05:04.0: restoring config space at offset 0xf (was 0x1f170100, writing 0x1f17010f)
[96187.790950] skge 0000:05:04.0: restoring config space at offset 0xc (was 0x0, writing 0xfbfc0000)
[96187.790961] skge 0000:05:04.0: restoring config space at offset 0x5 (was 0x1, writing 0xe401)
[96187.790966] skge 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbff4000)
[96187.790971] skge 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[96187.790976] skge 0000:05:04.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00017)
[96187.791190] PM: early resume of devices complete after 1.301 msecs
[96187.791255] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[96187.791261] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[96187.791282] usb usb3: root hub lost power or was reset
[96187.791294] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[96187.791299] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[96187.791318] usb usb4: root hub lost power or was reset
[96187.791326] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[96187.791337] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[96187.791333] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[96187.791344] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[96187.791365] usb usb5: root hub lost power or was reset
[96187.791361] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[96187.791366] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[96187.791376] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[96187.791382] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[96187.791387] usb usb6: root hub lost power or was reset
[96187.791407] usb usb7: root hub lost power or was reset
[96187.791403] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[96187.791408] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[96187.791420] pci 0000:00:1e.0: setting latency timer to 64
[96187.791430] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[96187.791436] ata_piix 0000:00:1f.2: setting latency timer to 64
[96187.791436] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[96187.791441] ata_piix 0000:00:1f.5: setting latency timer to 64
[96187.791461] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[96187.791468] ahci 0000:03:00.0: setting latency timer to 64
[96187.793863] serial 00:06: activated
[96187.798568] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[96187.798575] pata_jmicron 0000:03:00.1: setting latency timer to 64
[96187.798623] snd_oxygen 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[96187.799219] pci 0000:00:1e.0: wake-up capability disabled by ACPI
[96187.799226] skge 0000:05:04.0: PME# disabled
[96187.808105] sd 2:0:0:0: [sda] Starting disk
[96187.808172] sd 2:0:1:0: [sdb] Starting disk
[96187.808228] sd 3:0:0:0: [sdc] Starting disk
[96187.808291] sd 4:0:0:0: [sdd] Starting disk
[96187.916035] PM: resume of drv:hub dev:3-0:1.0 complete after 116.671 msecs
[96187.916043] PM: resume of drv: dev:ep_00 complete after 116.003 msecs
[96187.916048] PM: resume of drv: dev:ep_81 complete after 116.011 msecs
[96187.920078] PM: resume of drv:hub dev:4-0:1.0 complete after 120.020 msecs
[96187.920086] PM: resume of drv: dev:ep_00 complete after 120.014 msecs
[96187.920091] PM: resume of drv: dev:ep_81 complete after 120.026 msecs
[96187.924031] PM: resume of drv:hub dev:7-0:1.0 complete after 119.947 msecs
[96187.924038] PM: resume of drv: dev:ep_00 complete after 119.948 msecs
[96187.924043] PM: resume of drv: dev:ep_81 complete after 119.955 msecs
[96187.944331] PM: resume of drv:btusb dev:2-2.1:1.0 complete after 135.678 msecs
[96187.944341] PM: resume of drv:btusb dev:2-2.1:1.1 complete after 135.604 msecs
[96187.944349] PM: resume of drv:usb dev:2-2.1:1.2 complete after 135.552 msecs
[96187.944356] PM: resume of drv:usb dev:2-2.1:1.3 complete after 135.497 msecs
[96187.944362] PM: resume of drv: dev:ep_00 complete after 135.482 msecs
[96187.944367] PM: resume of drv: dev:ep_81 complete after 135.695 msecs
[96187.944372] PM: resume of drv: dev:ep_82 complete after 135.679 msecs
[96187.944377] PM: resume of drv: dev:ep_02 complete after 135.660 msecs
[96187.944382] PM: resume of drv: dev:ep_83 complete after 135.625 msecs
[96187.944387] PM: resume of drv: dev:ep_03 complete after 135.610 msecs
[96187.944392] PM: resume of drv: dev:ep_84 complete after 135.573 msecs
[96187.944397] PM: resume of drv: dev:ep_04 complete after 135.558 msecs
[96188.024030] PM: resume of drv:hub dev:6-0:1.0 complete after 223.910 msecs
[96188.024038] PM: resume of drv: dev:ep_00 complete after 219.964 msecs
[96188.024058] PM: resume of drv:hub dev:5-0:1.0 complete after 223.969 msecs
[96188.024065] PM: resume of drv: dev:ep_00 complete after 223.963 msecs
[96188.024078] PM: resume of drv: dev:ep_81 complete after 223.952 msecs
[96188.024084] PM: resume of drv: dev:ep_81 complete after 223.988 msecs
[96188.056192] PM: resume of drv:snd_oxygen dev:0000:05:01.0 complete after 257.568 msecs
[96188.123267] ata6: SATA link down (SStatus 0 SControl 300)
[96188.123324] ata2: SATA link down (SStatus 0 SControl 300)
[96188.123440] ata1: SATA link down (SStatus 0 SControl 300)
[96188.136021] usb 6-1: reset full-speed USB device number 2 using uhci_hcd
[96188.254204] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 462.758 msecs
[96188.254219] firewire_core: skipped bus generations, destroying all nodes
[96188.290141] PM: resume of drv:usbhid dev:6-1:1.0 complete after 481.610 msecs
[96188.290155] PM: resume of drv: dev:ep_00 complete after 481.541 msecs
[96188.290161] PM: resume of drv:usbhid dev:6-1:1.1 complete after 481.586 msecs
[96188.290172] PM: resume of drv: dev:ep_81 complete after 481.622 msecs
[96188.290178] PM: resume of drv: dev:ep_82 complete after 481.584 msecs
[96188.388062] usb 5-1: reset full-speed USB device number 2 using uhci_hcd
[96188.549106] PM: resume of drv:usbhid dev:5-1:1.0 complete after 740.740 msecs
[96188.549114] PM: resume of drv: dev:ep_00 complete after 740.626 msecs
[96188.549120] PM: resume of drv:usbhid dev:5-1:1.2 complete after 740.670 msecs
[96188.549124] PM: resume of drv:usbhid dev:5-1:1.1 complete after 740.718 msecs
[96188.549130] PM: resume of drv: dev:ep_81 complete after 740.746 msecs
[96188.549141] PM: resume of drv: dev:ep_83 complete after 740.673 msecs
[96188.549147] PM: resume of drv: dev:ep_82 complete after 740.717 msecs
[96188.752257] firewire_core: rediscovered device fw0
[96193.316089] ata5: link is slow to respond, please be patient (ready=0)
[96193.636032] ata4.00: link is slow to respond, please be patient (ready=0)
[96193.636210] ata3.00: link is slow to respond, please be patient (ready=0)
[96193.972357] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[96193.972371] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[96193.980148] ata4.01: ACPI cmd ef/03:44:00:00:00:b0 (SET FEATURES) filtered out
[96193.980152] ata4.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[96193.988149] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[96193.988154] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[96193.988258] ata4.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[96194.004289] ata4.00: configured for UDMA/133
[96194.020150] ata4.01: configured for UDMA/66
[96194.032111] PM: resume of drv:sd dev:3:0:0:0 complete after 6223.881 msecs
[96194.032132] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 6223.871 msecs
[96194.100064] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[96194.108152] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[96194.108157] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[96194.108259] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[96194.124286] ata5.00: configured for UDMA/133
[96194.150572] PM: resume of drv:sd dev:4:0:0:0 complete after 6342.280 msecs
[96194.150584] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 6342.258 msecs
[96197.836051] ata3.00: SRST failed (errno=-16)
[96203.672030] ata3.00: link is slow to respond, please be patient (ready=0)
[96207.592072] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[96207.592086] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[96207.600151] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 (SET FEATURES) filtered out
[96207.600157] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[96207.600286] ata3.01: ACPI cmd c6/00:10:00:00:00:b0 (SET MULTIPLE MODE) succeeded
[96207.624163] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[96207.624168] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[96207.662611] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[96207.684300] ata3.00: configured for UDMA/133
[96207.692386] ata3.01: configured for UDMA/133
[96207.694833] PM: resume of drv:sd dev:2:0:1:0 complete after 19886.660 msecs
[96207.694845] PM: resume of drv:scsi_device dev:2:0:1:0 complete after 19886.639 msecs
[96207.704999] PM: resume of drv:sd dev:2:0:0:0 complete after 19896.895 msecs
[96207.705015] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 19897.777 msecs
[96207.705258] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 19897.110 msecs
[96207.705267] PM: resume of devices complete after 19914.039 msecs
[96207.705510] PM: resume devices took 19.916 seconds
[96207.705512] ------------[ cut here ]------------
[96207.705518] WARNING: at /build/buildd/linux-3.2.0/kernel/power/suspend_test.c:53 suspend_test_finish+0x86/0x90()
[96207.705520] Hardware name: System Product Name
[96207.705522] Component: resume devices, time: 19916
[96207.705523] Modules linked in: usb_storage rfcomm bnep parport_pc ppdev binfmt_misc snd_oxygen snd_oxygen_lib snd_pcm snd_page_alloc snd_mpu401_uart btusb bluetooth snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) dm_multipath psmouse serio_raw mac_hid asus_atk0110 lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c firewire_ohci firewire_core hid_logitech_dj skge crc_itu_t usbhid hid sky2 pata_jmicron zram(C)
[96207.705556] Pid: 12161, comm: pm-suspend Tainted: P        WC O 3.2.0-56-generic #86-Ubuntu
[96207.705558] Call Trace:
[96207.705563]  [<ffffffff810681df>] warn_slowpath_common+0x7f/0xc0
[96207.705567]  [<ffffffff810682d6>] warn_slowpath_fmt+0x46/0x50
[96207.705570]  [<ffffffff810acbb6>] suspend_test_finish+0x86/0x90
[96207.705573]  [<ffffffff810ac8ab>] suspend_devices_and_enter+0x10b/0x200
[96207.705576]  [<ffffffff810aca71>] enter_state+0xd1/0x110
[96207.705579]  [<ffffffff810ab427>] state_store+0xb7/0x130
[96207.705582]  [<ffffffff813104af>] kobj_attr_store+0xf/0x30
[96207.705586]  [<ffffffff811eea1f>] sysfs_write_file+0xef/0x170
[96207.705590]  [<ffffffff8117a543>] vfs_write+0xb3/0x180
[96207.705592]  [<ffffffff8117a86a>] sys_write+0x4a/0x90
[96207.705596]  [<ffffffff81669802>] system_call_fastpath+0x16/0x1b
[96207.705598] ---[ end trace 9e4141bbdeb5724f ]---
[96207.705653] PM: Finishing wakeup.
[96207.705654] Restarting tasks ... done.
[96209.366745] sky2 0000:02:00.0: eth1: enabling interface
[96209.367663] ADDRCONF(NETDEV_UP): eth1: link is not ready
[96209.371453] skge 0000:05:04.0: eth2: enabling interface
[96209.375460] ADDRCONF(NETDEV_UP): eth2: link is not ready
[96211.799973] sky2 0000:02:00.0: eth1: Link is up at 1000 Mbps, full duplex, flow control both
[96211.800843] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[96222.728010] eth1: no IPv6 routers present
[142853.198888] sky2 0000:02:00.0: eth1: disabling interface
[142853.204440] skge 0000:05:04.0: eth2: disabling interface
[142856.961989] PM: Syncing filesystems ... done.
[142857.000425] PM: Preparing system for mem sleep
[142857.000439] Freezing user space processes ... (elapsed 0.01 seconds) done.
[142857.016097] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[142857.032082] PM: Entering mem sleep
[142857.032114] Suspending console(s) (use no_console_suspend to debug)
[142857.035580] sd 4:0:0:0: [sdd] Synchronizing SCSI cache
[142857.035687] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[142857.035749] sd 4:0:0:0: [sdd] Stopping disk
[142857.035806] sd 3:0:0:0: [sdc] Stopping disk
[142857.035872] sd 2:0:1:0: [sdb] Synchronizing SCSI cache
[142857.035942] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[142857.036100] sd 2:0:1:0: [sdb] Stopping disk
[142857.036261] serial 00:06: disabled
[142857.036267] serial 00:06: wake-up capability disabled by ACPI
[142857.036272] sd 2:0:0:0: [sda] Stopping disk
[142857.037099] ACPI handle has no context!
[142857.037137] snd_oxygen 0000:05:01.0: PCI INT A disabled
[142857.037165] ACPI handle has no context!
[142857.037329] pata_jmicron 0000:03:00.1: PCI INT B disabled
[142857.037369] ahci 0000:03:00.0: PCI INT A disabled
[142857.040153] ata_piix 0000:00:1f.5: PCI INT B disabled
[142857.048155] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[142857.052067] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[142857.076076] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[142857.076141] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[142857.076147] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[142857.080038] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[142857.080043] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[142857.459777] PM: suspend of drv:sd dev:2:0:1:0 complete after 423.905 msecs
[142857.459793] PM: suspend of drv:scsi dev:target2:0:1 complete after 423.855 msecs
[142858.466300] PM: suspend of drv:sd dev:2:0:0:0 complete after 1430.358 msecs
[142858.466322] PM: suspend of drv:scsi dev:target2:0:0 complete after 1430.353 msecs
[142858.466338] PM: suspend of drv:scsi dev:host2 complete after 1429.974 msecs
[142858.466429] ata_piix 0000:00:1f.2: PCI INT B disabled
[142858.480034] PM: suspend of drv:ata_piix dev:0000:00:1f.2 complete after 1439.925 msecs
[142858.480057] PM: suspend of drv: dev:pci0000:00 complete after 1439.515 msecs
[142858.480069] PM: suspend of devices complete after 1447.607 msecs
[142858.480073] PM: suspend devices took 1.448 seconds
[142858.480363] skge 0000:05:04.0: PME# enabled
[142858.480374] pci 0000:00:1e.0: wake-up capability enabled by ACPI
[142858.652035] PM: late suspend of drv:sky2 dev:0000:02:00.0 complete after 156.008 msecs
[142858.652159] ehci_hcd 0000:00:1d.7: PME# enabled
[142858.652166] ehci_hcd 0000:00:1d.7: wake-up capability enabled by ACPI
[142858.668088] uhci_hcd 0000:00:1d.2: wake-up capability enabled by ACPI
[142858.668130] uhci_hcd 0000:00:1d.1: wake-up capability enabled by ACPI
[142858.668171] uhci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
[142858.668302] ehci_hcd 0000:00:1a.7: PME# enabled
[142858.668306] ehci_hcd 0000:00:1a.7: wake-up capability enabled by ACPI
[142858.684063] uhci_hcd 0000:00:1a.1: wake-up capability enabled by ACPI
[142858.684103] uhci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
[142858.684184] PM: late suspend of devices complete after 204.108 msecs
[142858.684450] ACPI: Preparing to enter system sleep state S3
[142858.684653] PM: Saving platform NVS memory
[142858.685122] Disabling non-boot CPUs ...
[142858.788041] CPU 1 is now offline
[142858.788537] ACPI: Low-level resume complete
[142858.788537] PM: Restoring platform NVS memory
[142858.788537] Enabling non-boot CPUs ...
[142858.788537] Booting Node 0 Processor 1 APIC 0x1
[142858.788537] smpboot cpu 1: start_ip = 9a000
[142858.686409] Calibrating delay loop (skipped) already calibrated this CPU
[142858.820070] NMI watchdog enabled, takes one hw-pmu counter.
[142858.824067] CPU1 is up
[142858.825428] ACPI: Waking up from system sleep state S3
[142858.825976] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0xa0100, writing 0xa010b)
[142858.825986] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[142858.826019] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[142858.826042] uhci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
[142858.826062] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[142858.826081] uhci_hcd 0000:00:1a.1: wake-up capability disabled by ACPI
[142858.826108] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[142858.826122] ehci_hcd 0000:00:1a.7: wake-up capability disabled by ACPI
[142858.826127] ehci_hcd 0000:00:1a.7: PME# disabled
[142858.826139] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[142858.826148] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xc080c050)
[142858.826153] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0x20001010)
[142858.826161] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
[142858.826193] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x20100, writing 0x2010b)
[142858.826202] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc041c031)
[142858.826212] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[142858.826243] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x20200, writing 0x2020a)
[142858.826252] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc021c011)
[142858.826262] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
[142858.826301] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[142858.826320] uhci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
[142858.826339] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[142858.826358] uhci_hcd 0000:00:1d.1: wake-up capability disabled by ACPI
[142858.826377] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[142858.826396] uhci_hcd 0000:00:1d.2: wake-up capability disabled by ACPI
[142858.826423] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900002)
[142858.826437] ehci_hcd 0000:00:1d.7: wake-up capability disabled by ACPI
[142858.826442] ehci_hcd 0000:00:1d.7: PME# disabled
[142858.826450] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x20000, writing 0x200ff)
[142858.826533] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xc0000000)
[142858.826575] nvidia 0000:01:00.0: restoring config space at offset 0xc (was 0xfbce0000, writing 0x0)
[142858.826584] nvidia 0000:01:00.0: restoring config space at offset 0x3 (was 0x8, writing 0x0)
[142858.826620] ahci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[142858.826630] ahci 0000:03:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbee0000)
[142858.826639] ahci 0000:03:00.0: restoring config space at offset 0x9 (was 0x0, writing 0xfbefe000)
[142858.826644] ahci 0000:03:00.0: restoring config space at offset 0x8 (was 0x1, writing 0x0)
[142858.826650] ahci 0000:03:00.0: restoring config space at offset 0x7 (was 0x1, writing 0x0)
[142858.826656] ahci 0000:03:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x0)
[142858.826661] ahci 0000:03:00.0: restoring config space at offset 0x5 (was 0x1, writing 0x0)
[142858.826667] ahci 0000:03:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x0)
[142858.826673] ahci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x800008)
[142858.826678] ahci 0000:03:00.0: restoring config space at offset 0x2 (was 0x1018502, writing 0x1060102)
[142858.826684] ahci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[142858.826732] pata_jmicron 0000:03:00.1: restoring config space at offset 0x8 (was 0x1, writing 0xd401)
[142858.826738] pata_jmicron 0000:03:00.1: restoring config space at offset 0x7 (was 0x1, writing 0xd481)
[142858.826744] pata_jmicron 0000:03:00.1: restoring config space at offset 0x6 (was 0x1, writing 0xd801)
[142858.826750] pata_jmicron 0000:03:00.1: restoring config space at offset 0x5 (was 0x1, writing 0xd881)
[142858.826755] pata_jmicron 0000:03:00.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[142858.826765] pata_jmicron 0000:03:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100005)
[142858.826799] sky2 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[142858.826807] sky2 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfbdc0000)
[142858.826819] sky2 0000:02:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xc801)
[142858.826826] sky2 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfbdfc004)
[142858.826831] sky2 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[142858.826838] sky2 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[142858.826893] snd_oxygen 0000:05:01.0: restoring config space at offset 0x4 (was 0x7fffe801, writing 0xe801)
[142858.826900] snd_oxygen 0000:05:01.0: restoring config space at offset 0x1 (was 0x2100005, writing 0x2100001)
[142858.826917] firewire_ohci 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010e)
[142858.826933] firewire_ohci 0000:05:03.0: restoring config space at offset 0x5 (was 0x0, writing 0xfbff8000)
[142858.826938] firewire_ohci 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbfff800)
[142858.826942] firewire_ohci 0000:05:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[142858.826948] firewire_ohci 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[142858.826968] skge 0000:05:04.0: restoring config space at offset 0xf (was 0x1f170100, writing 0x1f17010f)
[142858.826975] skge 0000:05:04.0: restoring config space at offset 0xc (was 0x0, writing 0xfbfc0000)
[142858.826986] skge 0000:05:04.0: restoring config space at offset 0x5 (was 0x1, writing 0xe401)
[142858.826991] skge 0000:05:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbff4000)
[142858.826996] skge 0000:05:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[142858.827001] skge 0000:05:04.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00017)
[142858.827216] PM: early resume of devices complete after 1.307 msecs
[142858.827285] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[142858.827291] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[142858.827312] usb usb3: root hub lost power or was reset
[142858.827323] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[142858.827328] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[142858.827348] usb usb4: root hub lost power or was reset
[142858.827360] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[142858.827365] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[142858.827396] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[142858.827401] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[142858.827421] usb usb5: root hub lost power or was reset
[142858.827431] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[142858.827437] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[142858.827435] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[142858.827440] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[142858.827458] usb usb6: root hub lost power or was reset
[142858.827472] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[142858.827468] usb usb7: root hub lost power or was reset
[142858.827478] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[142858.827480] pci 0000:00:1e.0: setting latency timer to 64
[142858.827494] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[142858.827506] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[142858.827502] ata_piix 0000:00:1f.2: setting latency timer to 64
[142858.827511] ata_piix 0000:00:1f.5: setting latency timer to 64
[142858.827531] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[142858.827537] ahci 0000:03:00.0: setting latency timer to 64
[142858.830861] serial 00:06: activated
[142858.834454] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[142858.834462] pata_jmicron 0000:03:00.1: setting latency timer to 64
[142858.834510] snd_oxygen 0000:05:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[142858.835099] pci 0000:00:1e.0: wake-up capability disabled by ACPI
[142858.835106] skge 0000:05:04.0: PME# disabled
[142858.835456] sd 2:0:0:0: [sda] Starting disk
[142858.835520] sd 2:0:1:0: [sdb] Starting disk
[142858.835573] sd 3:0:0:0: [sdc] Starting disk
[142858.835632] sd 4:0:0:0: [sdd] Starting disk
[142858.952122] PM: resume of drv:hub dev:3-0:1.0 complete after 116.882 msecs
[142858.952130] PM: resume of drv: dev:ep_00 complete after 116.883 msecs
[142858.952135] PM: resume of drv:hub dev:4-0:1.0 complete after 116.879 msecs
[142858.952142] PM: resume of drv: dev:ep_00 complete after 116.880 msecs
[142858.952147] PM: resume of drv:hub dev:7-0:1.0 complete after 116.850 msecs
[142858.952154] PM: resume of drv: dev:ep_00 complete after 116.798 msecs
[142858.952159] PM: resume of drv: dev:ep_81 complete after 116.920 msecs
[142858.952163] PM: resume of drv: dev:ep_81 complete after 116.905 msecs
[142858.952168] PM: resume of drv: dev:ep_81 complete after 116.835 msecs
[142858.980336] PM: resume of drv:btusb dev:2-2.1:1.0 complete after 144.335 msecs
[142858.980347] PM: resume of drv:btusb dev:2-2.1:1.1 complete after 144.190 msecs
[142858.980355] PM: resume of drv:usb dev:2-2.1:1.2 complete after 144.137 msecs
[142858.980363] PM: resume of drv:usb dev:2-2.1:1.3 complete after 144.083 msecs
[142858.980368] PM: resume of drv: dev:ep_00 complete after 144.069 msecs
[142858.980373] PM: resume of drv: dev:ep_81 complete after 144.279 msecs
[142858.980379] PM: resume of drv: dev:ep_82 complete after 144.263 msecs
[142858.980383] PM: resume of drv: dev:ep_02 complete after 144.247 msecs
[142858.980389] PM: resume of drv: dev:ep_83 complete after 144.212 msecs
[142858.980393] PM: resume of drv: dev:ep_03 complete after 144.196 msecs
[142858.980399] PM: resume of drv: dev:ep_84 complete after 144.161 msecs
[142858.980403] PM: resume of drv: dev:ep_04 complete after 144.146 msecs
[142859.056031] PM: resume of drv:hub dev:5-0:1.0 complete after 220.761 msecs
[142859.056039] PM: resume of drv: dev:ep_00 complete after 220.764 msecs
[142859.056059] PM: resume of drv:hub dev:6-0:1.0 complete after 220.775 msecs
[142859.056067] PM: resume of drv: dev:ep_00 complete after 220.777 msecs
[142859.056080] PM: resume of drv: dev:ep_81 complete after 220.808 msecs
[142859.056086] PM: resume of drv: dev:ep_81 complete after 220.799 msecs
[142859.092199] PM: resume of drv:snd_oxygen dev:0000:05:01.0 complete after 257.689 msecs
[142859.159348] ata6: SATA link down (SStatus 0 SControl 300)
[142859.160032] ata1: SATA link down (SStatus 0 SControl 300)
[142859.160067] ata2: SATA link down (SStatus 0 SControl 300)
[142859.168020] usb 5-1: reset full-speed USB device number 2 using uhci_hcd
[142859.291433] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 463.916 msecs
[142859.291444] firewire_core: skipped bus generations, destroying all nodes
[142859.328291] PM: resume of drv:usbhid dev:5-1:1.0 complete after 492.576 msecs
[142859.328298] PM: resume of drv: dev:ep_00 complete after 492.456 msecs
[142859.328303] PM: resume of drv:usbhid dev:5-1:1.1 complete after 492.547 msecs
[142859.328321] PM: resume of drv: dev:ep_81 complete after 492.585 msecs
[142859.328337] PM: resume of drv:usbhid dev:5-1:1.2 complete after 492.527 msecs
[142859.328345] PM: resume of drv: dev:ep_82 complete after 492.570 msecs
[142859.328350] PM: resume of drv: dev:ep_83 complete after 492.532 msecs
[142859.416044] usb 6-1: reset full-speed USB device number 2 using uhci_hcd
[142859.569308] PM: resume of drv:usbhid dev:6-1:1.0 complete after 733.431 msecs
[142859.569318] PM: resume of drv: dev:ep_00 complete after 733.357 msecs
[142859.569324] PM: resume of drv:usbhid dev:6-1:1.1 complete after 733.400 msecs
[142859.569335] PM: resume of drv: dev:ep_81 complete after 733.437 msecs
[142859.569341] PM: resume of drv: dev:ep_82 complete after 733.398 msecs
[142859.788097] firewire_core: rediscovered device fw0
[142864.352031] ata5: link is slow to respond, please be patient (ready=0)
[142864.672031] ata4.00: link is slow to respond, please be patient (ready=0)
[142864.672310] ata3.00: link is slow to respond, please be patient (ready=0)
[142864.952079] ata4.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[142864.952093] ata4.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[142864.960150] ata4.01: ACPI cmd ef/03:44:00:00:00:b0 (SET FEATURES) filtered out
[142864.960154] ata4.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[142864.968156] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[142864.968161] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[142864.968264] ata4.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[142864.992276] ata4.00: configured for UDMA/133
[142865.008153] ata4.01: configured for UDMA/66
[142865.028301] PM: resume of drv:sd dev:3:0:0:0 complete after 6192.720 msecs
[142865.028311] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 6192.699 msecs
[142865.136063] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[142865.144146] ata5.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[142865.144151] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[142865.144245] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[142865.168292] ata5.00: configured for UDMA/133
[142865.200812] PM: resume of drv:sd dev:4:0:0:0 complete after 6365.171 msecs
[142865.200823] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 6365.149 msecs
[142868.872031] ata3.00: SRST failed (errno=-16)
[142874.708031] ata3.00: link is slow to respond, please be patient (ready=0)
[142878.628072] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[142878.628086] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[142878.636153] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 (SET FEATURES) filtered out
[142878.636158] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
[142878.636720] ata3.01: ACPI cmd c6/00:10:00:00:00:b0 (SET MULTIPLE MODE) succeeded
[142878.656164] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[142878.656168] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[142878.686041] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[142878.708303] ata3.00: configured for UDMA/133
[142878.716829] ata3.01: configured for UDMA/133
[142878.727281] PM: resume of drv:sd dev:2:0:1:0 complete after 19891.752 msecs
[142878.727292] PM: resume of drv:scsi_device dev:2:0:1:0 complete after 19891.733 msecs
[142878.731551] PM: resume of drv:sd dev:2:0:0:0 complete after 19896.088 msecs
[142878.731565] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 19896.058 msecs
[142878.731574] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 19888.391 msecs
[142878.731809] PM: resume of devices complete after 19904.555 msecs
[142878.732057] PM: resume devices took 19.908 seconds
[142878.732058] ------------[ cut here ]------------
[142878.732064] WARNING: at /build/buildd/linux-3.2.0/kernel/power/suspend_test.c:53 suspend_test_finish+0x86/0x90()
[142878.732066] Hardware name: System Product Name
[142878.732068] Component: resume devices, time: 19908
[142878.732069] Modules linked in: usb_storage rfcomm bnep parport_pc ppdev binfmt_misc snd_oxygen snd_oxygen_lib snd_pcm snd_page_alloc snd_mpu401_uart btusb bluetooth snd_seq_midi joydev snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore nvidia(P) dm_multipath psmouse serio_raw mac_hid asus_atk0110 lp parport dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c firewire_ohci firewire_core hid_logitech_dj skge crc_itu_t usbhid hid sky2 pata_jmicron zram(C)
[142878.732102] Pid: 14863, comm: pm-suspend Tainted: P        WC O 3.2.0-56-generic #86-Ubuntu
[142878.732104] Call Trace:
[142878.732109]  [<ffffffff810681df>] warn_slowpath_common+0x7f/0xc0
[142878.732112]  [<ffffffff810682d6>] warn_slowpath_fmt+0x46/0x50
[142878.732115]  [<ffffffff810acbb6>] suspend_test_finish+0x86/0x90
[142878.732118]  [<ffffffff810ac8ab>] suspend_devices_and_enter+0x10b/0x200
[142878.732121]  [<ffffffff810aca71>] enter_state+0xd1/0x110
[142878.732124]  [<ffffffff810ab427>] state_store+0xb7/0x130
[142878.732128]  [<ffffffff813104af>] kobj_attr_store+0xf/0x30
[142878.732131]  [<ffffffff811eea1f>] sysfs_write_file+0xef/0x170
[142878.732135]  [<ffffffff8117a543>] vfs_write+0xb3/0x180
[142878.732138]  [<ffffffff8117a86a>] sys_write+0x4a/0x90
[142878.732142]  [<ffffffff81669802>] system_call_fastpath+0x16/0x1b
[142878.732144] ---[ end trace 9e4141bbdeb57250 ]---
[142878.732199] PM: Finishing wakeup.
[142878.732201] Restarting tasks ... done.
[142879.738322] sky2 0000:02:00.0: eth1: enabling interface
[142879.740182] ADDRCONF(NETDEV_UP): eth1: link is not ready
[142879.743274] skge 0000:05:04.0: eth2: enabling interface
[142879.747913] ADDRCONF(NETDEV_UP): eth2: link is not ready
[142882.331728] sky2 0000:02:00.0: eth1: Link is up at 1000 Mbps, full duplex, flow control both
[142882.332806] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[142893.192012] eth1: no IPv6 routers present
[149661.449409] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[149661.449416] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[149661.449422] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[149661.449430] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[149661.449443] end_request: I/O error, dev sr0, sector 64
[149661.449446] quiet_error: 36 callbacks suppressed
[149661.449449] Buffer I/O error on device sr0, logical block 16
[149661.449454] Buffer I/O error on device sr0, logical block 17
[149661.455326] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[149661.455332] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[149661.455338] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[149661.455345] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[149661.455357] end_request: I/O error, dev sr0, sector 64
[149661.455361] Buffer I/O error on device sr0, logical block 16
[149661.455365] Buffer I/O error on device sr0, logical block 17
[150245.068796] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.068803] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.068809] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.068817] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[150245.068830] end_request: I/O error, dev sr0, sector 0
[150245.068833] Buffer I/O error on device sr0, logical block 0
[150245.068837] Buffer I/O error on device sr0, logical block 1
[150245.068843] Buffer I/O error on device sr0, logical block 2
[150245.068846] Buffer I/O error on device sr0, logical block 3
[150245.068849] Buffer I/O error on device sr0, logical block 4
[150245.068853] Buffer I/O error on device sr0, logical block 5
[150245.068856] Buffer I/O error on device sr0, logical block 6
[150245.068860] Buffer I/O error on device sr0, logical block 7
[150245.069685] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.069690] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.069696] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.069701] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.069713] end_request: I/O error, dev sr0, sector 0
[150245.069716] Buffer I/O error on device sr0, logical block 0
[150245.070480] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.070486] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.070491] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.070497] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.070508] end_request: I/O error, dev sr0, sector 4
[150245.070512] Buffer I/O error on device sr0, logical block 1
[150245.071365] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.071371] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.071376] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.071382] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.071393] end_request: I/O error, dev sr0, sector 0
[150245.072164] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.072175] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.072186] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.072195] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.072223] end_request: I/O error, dev sr0, sector 4
[150245.073141] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.073148] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.073153] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.073160] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.073172] end_request: I/O error, dev sr0, sector 0
[150245.073981] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.073988] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.073993] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.073999] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.074011] end_request: I/O error, dev sr0, sector 4
[150245.074778] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.074784] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.074789] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.074795] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.074806] end_request: I/O error, dev sr0, sector 0
[150245.075572] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.075578] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.075583] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.075588] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.075600] end_request: I/O error, dev sr0, sector 4
[150245.076459] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.076465] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.076470] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.076476] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.076487] end_request: I/O error, dev sr0, sector 0
[150245.077253] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.077259] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.077264] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.077270] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.077282] end_request: I/O error, dev sr0, sector 4
[150245.078220] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.078226] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.078231] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.078236] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.078248] end_request: I/O error, dev sr0, sector 0
[150245.079060] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.079065] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.079070] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.079076] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.079087] end_request: I/O error, dev sr0, sector 4
[150245.079879] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.079884] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.079889] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.079895] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.079906] end_request: I/O error, dev sr0, sector 0
[150245.080676] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.080682] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.080687] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.080693] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.080705] end_request: I/O error, dev sr0, sector 4
[150245.081555] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.081561] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.081566] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.081572] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.081583] end_request: I/O error, dev sr0, sector 0
[150245.082355] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.082360] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.082365] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.082371] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.082382] end_request: I/O error, dev sr0, sector 4
[150245.083248] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.083253] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.083258] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.083264] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 01 00
[150245.083275] end_request: I/O error, dev sr0, sector 128
[150245.084093] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.084104] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.084115] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.084124] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 21 00 00 01 00
[150245.084152] end_request: I/O error, dev sr0, sector 132
[150245.084981] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.084987] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.084992] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.084998] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.085010] end_request: I/O error, dev sr0, sector 0
[150245.085775] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.085781] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.085786] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.085792] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.085804] end_request: I/O error, dev sr0, sector 4
[150245.086570] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.086575] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.086580] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.086586] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.086598] end_request: I/O error, dev sr0, sector 0
[150245.087388] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.087393] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.087398] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.087404] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.087416] end_request: I/O error, dev sr0, sector 4
[150245.088286] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.088292] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.088297] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.088303] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.088314] end_request: I/O error, dev sr0, sector 0
[150245.089122] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.089128] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.089133] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.089138] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.089150] end_request: I/O error, dev sr0, sector 4
[150245.089866] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.089872] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.089877] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.089883] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.089894] end_request: I/O error, dev sr0, sector 0
[150245.090672] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.090677] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.090682] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.090688] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.090700] end_request: I/O error, dev sr0, sector 4
[150245.091466] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.091471] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.091477] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.091482] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150245.091494] end_request: I/O error, dev sr0, sector 0
[150245.092284] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150245.092290] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150245.092295] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150245.092301] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150245.092313] end_request: I/O error, dev sr0, sector 4
[150390.874520] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.874528] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.874534] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.874542] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[150390.874554] end_request: I/O error, dev sr0, sector 0
[150390.874558] quiet_error: 26 callbacks suppressed
[150390.874561] Buffer I/O error on device sr0, logical block 0
[150390.874565] Buffer I/O error on device sr0, logical block 1
[150390.874570] Buffer I/O error on device sr0, logical block 2
[150390.874574] Buffer I/O error on device sr0, logical block 3
[150390.874577] Buffer I/O error on device sr0, logical block 4
[150390.874581] Buffer I/O error on device sr0, logical block 5
[150390.874584] Buffer I/O error on device sr0, logical block 6
[150390.874588] Buffer I/O error on device sr0, logical block 7
[150390.875395] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.875400] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.875406] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.875411] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.875423] end_request: I/O error, dev sr0, sector 0
[150390.875426] Buffer I/O error on device sr0, logical block 0
[150390.876190] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.876195] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.876199] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.876204] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.876213] end_request: I/O error, dev sr0, sector 4
[150390.876215] Buffer I/O error on device sr0, logical block 1
[150390.877143] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.877149] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.877155] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.877161] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.877173] end_request: I/O error, dev sr0, sector 0
[150390.877976] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.877982] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.877987] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.877993] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.878004] end_request: I/O error, dev sr0, sector 4
[150390.878808] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.878813] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.878817] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.878822] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.878831] end_request: I/O error, dev sr0, sector 0
[150390.879617] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.879623] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.879629] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.879635] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.879647] end_request: I/O error, dev sr0, sector 4
[150390.880414] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.880421] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.880426] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.880433] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.880445] end_request: I/O error, dev sr0, sector 0
[150390.881211] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.881217] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.881222] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.881228] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.881240] end_request: I/O error, dev sr0, sector 4
[150390.882165] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.882171] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.882176] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.882182] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.882193] end_request: I/O error, dev sr0, sector 0
[150390.883006] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.883011] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.883017] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.883023] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.883034] end_request: I/O error, dev sr0, sector 4
[150390.883807] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.883813] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.883818] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.883824] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.883835] end_request: I/O error, dev sr0, sector 0
[150390.884602] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.884606] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.884610] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.884615] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.884624] end_request: I/O error, dev sr0, sector 4
[150390.885475] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.885480] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.885485] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.885492] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.885503] end_request: I/O error, dev sr0, sector 0
[150390.886270] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.886276] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.886281] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.886287] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.886299] end_request: I/O error, dev sr0, sector 4
[150390.887143] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.887149] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.887154] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.887160] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.887171] end_request: I/O error, dev sr0, sector 0
[150390.887984] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.887989] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.887994] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.888000] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.888012] end_request: I/O error, dev sr0, sector 4
[150390.888796] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.888802] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.888807] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.888813] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 01 00
[150390.888825] end_request: I/O error, dev sr0, sector 128
[150390.889591] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.889596] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.889602] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.889608] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 21 00 00 01 00
[150390.889619] end_request: I/O error, dev sr0, sector 132
[150390.890387] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.890392] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.890397] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.890403] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.890415] end_request: I/O error, dev sr0, sector 0
[150390.891192] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.891198] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.891203] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.891209] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.891221] end_request: I/O error, dev sr0, sector 4
[150390.892200] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.892206] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.892212] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.892218] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.892229] end_request: I/O error, dev sr0, sector 0
[150390.893035] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.893041] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.893046] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.893052] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.893064] end_request: I/O error, dev sr0, sector 4
[150390.893849] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.893855] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.893860] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.893866] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.893877] end_request: I/O error, dev sr0, sector 0
[150390.894645] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.894651] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.894656] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.894662] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.894673] end_request: I/O error, dev sr0, sector 4
[150390.895441] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.895447] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.895452] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.895458] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.895469] end_request: I/O error, dev sr0, sector 0
[150390.896242] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.896248] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.896253] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.896259] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.896271] end_request: I/O error, dev sr0, sector 4
[150390.897431] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.897436] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.897442] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.897448] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[150390.897459] end_request: I/O error, dev sr0, sector 0
[150390.898198] sr 3:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[150390.898204] sr 3:0:1:0: [sr0]  Sense Key : Illegal Request [current] 
[150390.898209] sr 3:0:1:0: [sr0]  Add. Sense: Illegal mode for this track
[150390.898215] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[150390.898227] end_request: I/O error, dev sr0, sector 4
robert@robert-System-Product-Name:~$ 

```

---

### Post by andrew.46 on 2013-11-19
Are you trying to burn iso to dvd or other?

---

### Post by killabee44 on 2013-11-19
I was trying to burn dvd to dvd via ISO

---

### Post by andrew.46 on 2013-11-21
If the dvd is not copy protected dd is the easiest tool to use:

```

dd if=/dev/dvd of=example.iso bs=2048

```

and then to burn to dvd even simpler:

```

growisofs -dvd-compat -Z /dev/dvd=example.iso

```

Sometime eliminating complex gui tools removes problems, hopefully this will be true in your case :). The technique differs a little if the dvd has copy protection...

---

### Post by killabee44 on 2013-11-21
Thanks for your reply.. but it did not work. Here is the output:

```
robert@robert-System-Product-Name:~$ dd if=/dev/dvd of=example.iso bs=2048
dd: reading `/dev/dvd': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 8.14965 s, 0.0 kB/s

```

---

### Post by andrew.46 on 2013-11-22
If /dev/dvd does not work perhaps try*[COLOR="#FF0000"] /dev/sr0[/COLOR]*.....
Seems odd as I see this as output in your original post:

```

       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0

```

---

### Post by killabee44 on 2013-11-22
> **andrew.46 said:**
> If /dev/dvd does not work perhaps try*[COLOR="#FF0000"] /dev/sr0[/COLOR]*.....
Seems odd as I see this as output in your original post:

```

       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0

```

So after trying /dev/sr0:

```
dd: opening `/dev/sr0': No medium found

```

Then, 

```
robert@robert-System-Product-Name:~$ growisofs -dvd-compat -Z /dev/sr0=example.iso
:-( /dev/sr0: media is not recognized as recordable DVD: 0
```

---

### Post by andrew.46 on 2013-11-23
Hmmm.... for the dd command was there a dvd physically in the drive? 'no medium found' could simply mean this or a deeper problem...

---

### Post by kurt18947 on 2013-11-23
What package were you using?  Brasero can be weird, for want of a better term.  I generally install k3b for CD/DVD burning, it seems more reliable.

---

### Post by killabee44 on 2013-11-24
> **andrew.46 said:**
> Hmmm.... for the dd command was there a dvd physically in the drive? 'no medium found' could simply mean this or a deeper problem...

Yes, there was a DVD disk in the drive when I tried all commands.

---

### Post by killabee44 on 2013-11-24
> **kurt18947 said:**
> What package were you using?  Brasero can be weird, for want of a better term.  I generally install k3b for CD/DVD burning, it seems more reliable.

Im currently running Ubuntu 12.04.3 LTS. I have also tried burning with k3b.

---

