---
title: "sony vaio VPCF23EFX"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by jumbobits on 2012-04-25
I just recently bought a sony vaio VPCF23EFX. it has currently has Ubuntu 11.10 installed, but the wireless network card does not seem to be working. it was working when windows was on it, so its not broken, or at least i don't think so. the wired networking is working fine, although updates when i do apt-get update and upgrade go very slow at under 200 kilobytes per second, and i normally can sometimes get over 3 megabytes per second.

I completely wiped the drive of all partitions and set up 1 400 gig ex4 partition and 1 20 gig swap, i did the partitioning with gparted in the ubuntu live cd.

i am very sorry if this question is dumb, but this is very frustrating.

```
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr xxxxxxxxx
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2bf:97ff:fede:1e82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8399626 (8.3 MB)  TX bytes:1041951 (1.0 MB)
          Interrupt:49 Base address:0xa000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=df189f1e-9de4-4f9d-af9e-b3d34fe56ef4 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf426000 (usable)
[    0.000000]  BIOS-e820: 00000000cf426000 - 00000000cf58e000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf58e000 - 00000000cf591000 (usable)
[    0.000000]  BIOS-e820: 00000000cf591000 - 00000000cf5e8000 (reserved)
[    0.000000]  BIOS-e820: 00000000cf5e8000 - 00000000cf741000 (usable)
[    0.000000]  BIOS-e820: 00000000cf741000 - 00000000cf791000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf791000 - 00000000cf795000 (usable)
[    0.000000]  BIOS-e820: 00000000cf795000 - 00000000cf7e8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf7e8000 - 00000000cf7fd000 (usable)
[    0.000000]  BIOS-e820: 00000000cf7fd000 - 00000000cf800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf800000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000012f800000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: Sony Corporation VPCF23EFX/VAIO, BIOS R2150V3 07/22/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x12f800 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 120000000 mask FF0000000 write-back
[    0.000000]   5 base 12F800000 mask FFF800000 uncachable
[    0.000000]   6 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xcf7fd max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcba0] fcba0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000cf7fd000
[    0.000000]  0000000000 - 00cf600000 page 2M
[    0.000000]  00cf600000 - 00cf7fd000 page 4k
[    0.000000] kernel direct mapping tables up to cf7fd000 @ cf7f7000-cf7fd000
[    0.000000] init_memory_mapping: 0000000100000000-000000012f800000
[    0.000000]  0100000000 - 012f800000 page 2M
[    0.000000] kernel direct mapping tables up to 12f800000 @ 12f7fa000-12f800000
[    0.000000] RAMDISK: 365bc000 - 372d6000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02   Sony)
[    0.000000] ACPI: XSDT 00000000cf7fee18 00064 (v01   Sony     VAIO 20110722 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cf79bd98 000F4 (v04   Sony     VAIO 20110722 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCF7E5E40/0x00000000CF7E5D40, using 32 (20110413/tbfadt-489)
[    0.000000] ACPI: DSDT 00000000cf781018 09A1D (v01   Sony     VAIO 20110722 INTL 20091112)
[    0.000000] ACPI: FACS 00000000cf7e5e40 00040
[    0.000000] ACPI: APIC 00000000cf7fdf18 000CC (v02   Sony     VAIO 20110722 MSFT 00010013)
[    0.000000] ACPI: HPET 00000000cf7e6d18 00038 (v01   Sony     VAIO 20110722 MSFT 00000003)
[    0.000000] ACPI: SLIC 00000000cf79cc18 00176 (v01   Sony     VAIO 20110722 Sony 01000000)
[    0.000000] ACPI: MCFG 00000000cf7e6c98 0003C (v01   Sony     VAIO 20110722 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cf790018 00A03 (v01   Sony     VAIO 20110722 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cf78f018 00A4A (v01   Sony     VAIO 20110722 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cf79bc18 00137 (v01   Sony     VAIO 20110722 INTL 20091112)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000012f800000
[    0.000000] Initmem setup node 0 0000000000000000-000000012f800000
[    0.000000]   NODE_DATA [000000012f7fb000 - 000000012f7fffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012ae00000-ffff88012e7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0012f800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cf426
[    0.000000]     0: 0x000cf58e -> 0x000cf591
[    0.000000]     0: 0x000cf5e8 -> 0x000cf741
[    0.000000]     0: 0x000cf791 -> 0x000cf795
[    0.000000]     0: 0x000cf7e8 -> 0x000cf7fd
[    0.000000]     0: 0x00100000 -> 0x0012f800
[    0.000000] On node 0 totalpages: 1043753
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 830931 pages, LIFO batch:31
[    0.000000]   Normal zone: 2660 pages used for memmap
[    0.000000]   Normal zone: 191900 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 8 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cf426000 - 00000000cf58e000
[    0.000000] PM: Registered nosave memory: 00000000cf591000 - 00000000cf5e8000
[    0.000000] PM: Registered nosave memory: 00000000cf741000 - 00000000cf791000
[    0.000000] PM: Registered nosave memory: 00000000cf795000 - 00000000cf7e8000
[    0.000000] PM: Registered nosave memory: 00000000cf7fd000 - 00000000cf800000
[    0.000000] PM: Registered nosave memory: 00000000cf800000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:28000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012f400000 s79616 r8192 d22784 u131072
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1026752
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=df189f1e-9de4-4f9d-af9e-b3d34fe56ef4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4020916k/4972544k available (6104k kernel code, 797532k absent, 154096k reserved, 4880k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:808 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2194.976 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.95 BogoMIPS (lpj=8779904)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000469] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001690] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002115] Mount-cache hash table entries: 256
[    0.002225] Initializing cgroup subsys cpuacct
[    0.002230] Initializing cgroup subsys memory
[    0.002236] Initializing cgroup subsys devices
[    0.002238] Initializing cgroup subsys freezer
[    0.002240] Initializing cgroup subsys net_cls
[    0.002241] Initializing cgroup subsys blkio
[    0.002246] Initializing cgroup subsys perf_event
[    0.002273] CPU: Physical Processor ID: 0
[    0.002274] CPU: Processor Core ID: 0
[    0.002279] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002280] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002283] mce: CPU supports 9 MCE banks
[    0.002297] CPU0: Thermal monitoring enabled (TM1)
[    0.002304] using mwait in idle threads.
[    0.004798] ACPI: Core revision 20110413
[    0.238712] ftrace: allocating 25651 entries in 101 pages
[    0.248801] x2apic not enabled, IRQ remapping init failed
[    0.248805] Switched APIC routing to physical flat.
[    0.249134] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.288774] CPU0: Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz stepping 07
[    0.395514] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.395520] ... version:                3
[    0.395521] ... bit width:              48
[    0.395523] ... generic registers:      4
[    0.395524] ... value mask:             0000ffffffffffff
[    0.395525] ... max period:             000000007fffffff
[    0.395527] ... fixed-purpose events:   3
[    0.395528] ... event mask:             000000070000000f
[    0.395911] Booting Node   0, Processors  #1
[    0.395914] smpboot cpu 1: start_ip = 99000
[    0.503547]  #2
[    0.503549] smpboot cpu 2: start_ip = 99000
[    0.611477]  #3
[    0.611479] smpboot cpu 3: start_ip = 99000
[    0.719333]  #4
[    0.719335] smpboot cpu 4: start_ip = 99000
[    0.827175]  #5
[    0.827177] smpboot cpu 5: start_ip = 99000
[    0.935105]  #6
[    0.935107] smpboot cpu 6: start_ip = 99000
[    1.042935]  #7
[    1.042937] smpboot cpu 7: start_ip = 99000
[    1.150800] Brought up 8 CPUs
[    1.150803] Total of 8 processors activated (35118.82 BogoMIPS).
[    1.156538] devtmpfs: initialized
[    1.156657] PM: Registering ACPI NVS region at cf741000 (327680 bytes)
[    1.156664] PM: Registering ACPI NVS region at cf795000 (339968 bytes)
[    1.157989] print_constraints: dummy:
[    1.158015] Time: 21:08:14  Date: 04/25/12
[    1.158049] NET: Registered protocol family 16
[    1.158137] Trying to unpack rootfs image as initramfs...
[    1.158145] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.158147] ACPI: bus type pci registered
[    1.158206] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    1.158209] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    1.173399] PCI: Using configuration type 1 for base access
[    1.174024] bio: create slab <bio-0> at 0
[    1.175584] ACPI: EC: Look up EC in DSDT
[    1.177009] ACPI: Executed 1 blocks of module-level executable AML code
[    1.202628] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.203033] ACPI: SSDT 00000000cf5bc798 00725 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    1.203415] ACPI: Dynamic OEM Table Load:
[    1.203418] ACPI: SSDT           (null) 00725 (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
[    1.234834] ACPI: SSDT 00000000cf5bda98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    1.235248] ACPI: Dynamic OEM Table Load:
[    1.235250] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
[    1.266633] ACPI: SSDT 00000000cf5bbd98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    1.267013] ACPI: Dynamic OEM Table Load:
[    1.267015] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
[    1.396593] Freeing initrd memory: 13416k freed
[    2.089713] ACPI: Interpreter enabled
[    2.089719] ACPI: (supports S0 S3 S4 S5)
[    2.089743] ACPI: Using IOAPIC for interrupt routing
[    2.110770] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    2.110951] ACPI: No dock devices found.
[    2.110953] HEST: Table not found.
[    2.110955] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.111200] \_SB_.PCI0:_OSC invalid UUID
[    2.111202] _OSC request data:1 8 1f
[    2.111206] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    2.111617] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.111619] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.111621] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.111624] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    2.111625] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    2.111627] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    2.111629] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    2.111631] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    2.111633] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    2.111636] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xfeafffff]
[    2.111638] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    2.111650] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    2.111684] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
[    2.111710] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    2.111713] pci 0000:00:01.0: PME# disabled
[    2.111756] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    2.111780] pci 0000:00:16.0: reg 10: [mem 0xf7a0a000-0xf7a0a00f 64bit]
[    2.111843] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    2.111847] pci 0000:00:16.0: PME# disabled
[    2.111879] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    2.111900] pci 0000:00:1a.0: reg 10: [mem 0xf7a08000-0xf7a083ff]
[    2.111974] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    2.111978] pci 0000:00:1a.0: PME# disabled
[    2.112001] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    2.112016] pci 0000:00:1b.0: reg 10: [mem 0xf7a00000-0xf7a03fff 64bit]
[    2.112072] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.112075] pci 0000:00:1b.0: PME# disabled
[    2.112095] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    2.112158] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.112162] pci 0000:00:1c.0: PME# disabled
[    2.112185] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    2.112249] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    2.112252] pci 0000:00:1c.1: PME# disabled
[    2.112274] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
[    2.112337] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    2.112341] pci 0000:00:1c.2: PME# disabled
[    2.112362] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    2.112426] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    2.112429] pci 0000:00:1c.3: PME# disabled
[    2.112460] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    2.112482] pci 0000:00:1d.0: reg 10: [mem 0xf7a07000-0xf7a073ff]
[    2.112556] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    2.112560] pci 0000:00:1d.0: PME# disabled
[    2.112583] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    2.112698] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    2.112717] pci 0000:00:1f.2: reg 10: [io  0xe070-0xe077]
[    2.112724] pci 0000:00:1f.2: reg 14: [io  0xe060-0xe063]
[    2.112732] pci 0000:00:1f.2: reg 18: [io  0xe050-0xe057]
[    2.112740] pci 0000:00:1f.2: reg 1c: [io  0xe040-0xe043]
[    2.112748] pci 0000:00:1f.2: reg 20: [io  0xe020-0xe03f]
[    2.112756] pci 0000:00:1f.2: reg 24: [mem 0xf7a06000-0xf7a067ff]
[    2.112789] pci 0000:00:1f.2: PME# supported from D3hot
[    2.112792] pci 0000:00:1f.2: PME# disabled
[    2.112808] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    2.112823] pci 0000:00:1f.3: reg 10: [mem 0xf7a05000-0xf7a050ff 64bit]
[    2.112845] pci 0000:00:1f.3: reg 20: [io  0xe000-0xe01f]
[    2.112900] pci 0000:01:00.0: [10de:0df4] type 0 class 0x000300
[    2.112908] pci 0000:01:00.0: reg 10: [mem 0xf4000000-0xf4ffffff]
[    2.112918] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.112927] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit pref]
[    2.112934] pci 0000:01:00.0: reg 24: [io  0xd000-0xd07f]
[    2.112941] pci 0000:01:00.0: reg 30: [mem 0xf5000000-0xf507ffff pref]
[    2.112978] pci 0000:01:00.1: [10de:0bea] type 0 class 0x000403
[    2.112986] pci 0000:01:00.1: reg 10: [mem 0xf5080000-0xf5083fff]
[    2.113046] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.113049] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    2.113052] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf50fffff]
[    2.113056] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe1ffffff 64bit pref]
[    2.113121] pci 0000:02:00.0: [168c:002e] type 0 class 0x000280
[    2.113149] pci 0000:02:00.0: reg 10: [mem 0xf7000000-0xf700ffff 64bit]
[    2.113254] pci 0000:02:00.0: supports D1
[    2.113255] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    2.113261] pci 0000:02:00.0: PME# disabled
[    2.113298] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.113301] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    2.113305] pci 0000:00:1c.0:   bridge window [mem 0xf7000000-0xf79fffff]
[    2.113312] pci 0000:00:1c.0:   bridge window [mem 0xe4200000-0xe4bfffff 64bit pref]
[    2.113425] pci 0000:03:00.0: [1180:e823] type 0 class 0x000805
[    2.113449] pci 0000:03:00.0: reg 10: [mem 0xf6602000-0xf66020ff]
[    2.113583] pci 0000:03:00.0: supports D1 D2
[    2.113585] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.113590] pci 0000:03:00.0: PME# disabled
[    2.113638] pci 0000:03:00.1: [1180:e232] type 0 class 0x000880
[    2.113659] pci 0000:03:00.1: reg 10: [mem 0xf6601000-0xf66010ff]
[    2.113789] pci 0000:03:00.1: supports D1 D2
[    2.113791] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    2.113797] pci 0000:03:00.1: PME# disabled
[    2.113841] pci 0000:03:00.3: [1180:e832] type 0 class 0x000c00
[    2.113862] pci 0000:03:00.3: reg 10: [mem 0xf6600000-0xf66007ff]
[    2.113992] pci 0000:03:00.3: supports D1 D2
[    2.113993] pci 0000:03:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    2.113999] pci 0000:03:00.3: PME# disabled
[    2.114064] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.114068] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    2.114072] pci 0000:00:1c.1:   bridge window [mem 0xf6600000-0xf6ffffff]
[    2.114078] pci 0000:00:1c.1:   bridge window [mem 0xe3700000-0xe40fffff 64bit pref]
[    2.114147] pci 0000:04:00.0: [1033:0194] type 0 class 0x000c03
[    2.114173] pci 0000:04:00.0: reg 10: [mem 0xf5c00000-0xf5c01fff 64bit]
[    2.114281] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    2.114287] pci 0000:04:00.0: PME# disabled
[    2.114328] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    2.114332] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    2.114336] pci 0000:00:1c.2:   bridge window [mem 0xf5c00000-0xf65fffff]
[    2.114342] pci 0000:00:1c.2:   bridge window [mem 0xe2c00000-0xe35fffff 64bit pref]
[    2.114450] pci 0000:05:00.0: [10ec:8168] type 0 class 0x000200
[    2.114512] pci 0000:05:00.0: reg 10: [io  0x9000-0x90ff]
[    2.114624] pci 0000:05:00.0: reg 18: [mem 0xe2104000-0xe2104fff 64bit pref]
[    2.114692] pci 0000:05:00.0: reg 20: [mem 0xe2100000-0xe2103fff 64bit pref]
[    2.114889] pci 0000:05:00.0: supports D1 D2
[    2.114891] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    2.114904] pci 0000:05:00.0: PME# disabled
[    2.115021] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    2.115025] pci 0000:00:1c.3:   bridge window [io  0x9000-0x9fff]
[    2.115029] pci 0000:00:1c.3:   bridge window [mem 0xf5200000-0xf5bfffff]
[    2.115035] pci 0000:00:1c.3:   bridge window [mem 0xe2100000-0xe2afffff 64bit pref]
[    2.115058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.115168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    2.115223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    2.115252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    2.115279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    2.115308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    2.115378] \_SB_.PCI0:_OSC invalid UUID
[    2.115379] _OSC request data:1 1f 1f
[    2.115383]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.115411] \_SB_.PCI0:_OSC invalid UUID
[    2.115413] _OSC request data:1 0 1d
[    2.115416]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    2.115418] ACPI _OSC control for PCIe not granted, disabling ASPM
[    2.118439] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    2.118483] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    2.118523] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    2.118563] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 *3 4 5 6 10 11 12 14 15)
[    2.118603] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 *4 5 6 10 11 12 14 15)
[    2.118642] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    2.118682] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    2.118722] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 10 11 12 14 15)
[    2.118805] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.118809] vgaarb: loaded
[    2.118811] vgaarb: bridge control possible 0000:01:00.0
[    2.118952] SCSI subsystem initialized
[    2.119001] libata version 3.00 loaded.
[    2.119035] usbcore: registered new interface driver usbfs
[    2.119043] usbcore: registered new interface driver hub
[    2.119067] usbcore: registered new device driver usb
[    2.119134] PCI: Using ACPI for IRQ routing
[    2.120702] PCI: pci_cache_line_size set to 64 bytes
[    2.120779] reserve RAM buffer: 000000000009e800 - 000000000009ffff
[    2.120781] reserve RAM buffer: 00000000cf426000 - 00000000cfffffff
[    2.120784] reserve RAM buffer: 00000000cf591000 - 00000000cfffffff
[    2.120787] reserve RAM buffer: 00000000cf741000 - 00000000cfffffff
[    2.120789] reserve RAM buffer: 00000000cf795000 - 00000000cfffffff
[    2.120791] reserve RAM buffer: 00000000cf7fd000 - 00000000cfffffff
[    2.120793] reserve RAM buffer: 000000012f800000 - 000000012fffffff
[    2.120872] NetLabel: Initializing
[    2.120874] NetLabel:  domain hash size = 128
[    2.120875] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.120884] NetLabel:  unlabeled traffic allowed by default
[    2.120920] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    2.120926] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    2.122941] Switching to clocksource hpet
[    2.125527] Switched to NOHz mode on CPU #0
[    2.125617] Switched to NOHz mode on CPU #4
[    2.125620] Switched to NOHz mode on CPU #1
[    2.125630] Switched to NOHz mode on CPU #6
[    2.125659] Switched to NOHz mode on CPU #3
[    2.125673] Switched to NOHz mode on CPU #5
[    2.125675] Switched to NOHz mode on CPU #2
[    2.125684] Switched to NOHz mode on CPU #7
[    2.127781] AppArmor: AppArmor Filesystem Enabled
[    2.127798] pnp: PnP ACPI init
[    2.127809] ACPI: bus type pnp registered
[    2.128040] pnp 00:00: [bus 00-3e]
[    2.128043] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.128044] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.128046] pnp 00:00: [io  0x0d00-0xffff window]
[    2.128048] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.128050] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    2.128052] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    2.128053] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    2.128055] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    2.128057] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    2.128059] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    2.128061] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    2.128062] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    2.128064] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    2.128066] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    2.128068] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    2.128069] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    2.128071] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    2.128073] pnp 00:00: [mem 0xd0000000-0xfeafffff window]
[    2.128075] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    2.128133] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.128144] pnp 00:01: [io  0x0000-0x001f]
[    2.128145] pnp 00:01: [io  0x0081-0x0091]
[    2.128147] pnp 00:01: [io  0x0093-0x009f]
[    2.128148] pnp 00:01: [io  0x00c0-0x00df]
[    2.128150] pnp 00:01: [dma 4]
[    2.128166] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.128173] pnp 00:02: [mem 0xff000000-0xffffffff]
[    2.128188] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    2.128255] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    2.128271] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.128279] pnp 00:04: [io  0x00f0]
[    2.128288] pnp 00:04: [irq 13]
[    2.128303] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.128312] pnp 00:05: [io  0x002e-0x002f]
[    2.128314] pnp 00:05: [io  0x004e-0x004f]
[    2.128315] pnp 00:05: [io  0x0061]
[    2.128317] pnp 00:05: [io  0x0063]
[    2.128318] pnp 00:05: [io  0x0065]
[    2.128319] pnp 00:05: [io  0x0067]
[    2.128321] pnp 00:05: [io  0x0070]
[    2.128322] pnp 00:05: [io  0x0080]
[    2.128324] pnp 00:05: [io  0x0092]
[    2.128327] pnp 00:05: [io  0x00b2-0x00b3]
[    2.128329] pnp 00:05: [io  0x1000-0x100f]
[    2.128330] pnp 00:05: [io  0x1100-0x1103]
[    2.128332] pnp 00:05: [io  0x0400-0x047f]
[    2.128333] pnp 00:05: [io  0x0500-0x057f]
[    2.128335] pnp 00:05: [io  0x164e-0x164f]
[    2.128373] system 00:05: [io  0x1000-0x100f] has been reserved
[    2.128376] system 00:05: [io  0x1100-0x1103] has been reserved
[    2.128378] system 00:05: [io  0x0400-0x047f] has been reserved
[    2.128380] system 00:05: [io  0x0500-0x057f] has been reserved
[    2.128382] system 00:05: [io  0x164e-0x164f] has been reserved
[    2.128385] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.128392] pnp 00:06: [io  0x0070-0x0077]
[    2.128397] pnp 00:06: [irq 8]
[    2.128413] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.128431] pnp 00:07: [io  0x0454-0x0457]
[    2.128458] system 00:07: [io  0x0454-0x0457] has been reserved
[    2.128460] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    2.128468] pnp 00:08: [io  0x0060]
[    2.128469] pnp 00:08: [io  0x0064]
[    2.128473] pnp 00:08: [irq 1]
[    2.128492] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.128502] pnp 00:09: [irq 12]
[    2.128519] pnp 00:09: Plug and Play ACPI device, IDs SYN2703 PNP0f13 (active)
[    2.128717] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    2.128719] pnp 00:0a: [mem 0xfed10000-0xfed17fff]
[    2.128720] pnp 00:0a: [mem 0xfed18000-0xfed18fff]
[    2.128722] pnp 00:0a: [mem 0xfed19000-0xfed19fff]
[    2.128724] pnp 00:0a: [mem 0xf8000000-0xfbffffff]
[    2.128725] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    2.128727] pnp 00:0a: [mem 0xfed90000-0xfed93fff]
[    2.128728] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    2.128730] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    2.128732] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    2.128733] pnp 00:0a: [mem 0xe4c00000-0xe4c00fff]
[    2.128789] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.128791] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    2.128794] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    2.128796] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    2.128798] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    2.128800] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.128802] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    2.128805] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    2.128807] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    2.128809] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    2.128812] system 00:0a: [mem 0xe4c00000-0xe4c00fff] has been reserved
[    2.128814] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.128910] pnp 00:0b: can't evaluate _CRS: 12311
[    2.128957] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.135537] pnp: PnP ACPI: found 12 devices
[    2.135538] ACPI: ACPI bus type pnp unregistered
[    2.141094] PCI: max bus depth: 1 pci_try_num: 2
[    2.141129] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.141132] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    2.141135] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf50fffff]
[    2.141138] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xe1ffffff 64bit pref]
[    2.141142] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    2.141145] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    2.141150] pci 0000:00:1c.0:   bridge window [mem 0xf7000000-0xf79fffff]
[    2.141154] pci 0000:00:1c.0:   bridge window [mem 0xe4200000-0xe4bfffff 64bit pref]
[    2.141160] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    2.141163] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    2.141168] pci 0000:00:1c.1:   bridge window [mem 0xf6600000-0xf6ffffff]
[    2.141172] pci 0000:00:1c.1:   bridge window [mem 0xe3700000-0xe40fffff 64bit pref]
[    2.141178] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    2.141181] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    2.141186] pci 0000:00:1c.2:   bridge window [mem 0xf5c00000-0xf65fffff]
[    2.141190] pci 0000:00:1c.2:   bridge window [mem 0xe2c00000-0xe35fffff 64bit pref]
[    2.141196] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    2.141199] pci 0000:00:1c.3:   bridge window [io  0x9000-0x9fff]
[    2.141204] pci 0000:00:1c.3:   bridge window [mem 0xf5200000-0xf5bfffff]
[    2.141208] pci 0000:00:1c.3:   bridge window [mem 0xe2100000-0xe2afffff 64bit pref]
[    2.141224] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.141228] pci 0000:00:01.0: setting latency timer to 64
[    2.141236] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.141240] pci 0000:00:1c.0: setting latency timer to 64
[    2.141249] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.141253] pci 0000:00:1c.1: setting latency timer to 64
[    2.141262] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.141266] pci 0000:00:1c.2: setting latency timer to 64
[    2.141275] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.141279] pci 0000:00:1c.3: setting latency timer to 64
[    2.141282] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.141284] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.141286] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.141288] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    2.141290] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    2.141292] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    2.141294] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    2.141296] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    2.141298] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    2.141299] pci_bus 0000:00: resource 13 [mem 0xd0000000-0xfeafffff]
[    2.141301] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    2.141303] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.141305] pci_bus 0000:01: resource 1 [mem 0xf4000000-0xf50fffff]
[    2.141307] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xe1ffffff 64bit pref]
[    2.141309] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    2.141311] pci_bus 0000:02: resource 1 [mem 0xf7000000-0xf79fffff]
[    2.141313] pci_bus 0000:02: resource 2 [mem 0xe4200000-0xe4bfffff 64bit pref]
[    2.141315] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    2.141317] pci_bus 0000:03: resource 1 [mem 0xf6600000-0xf6ffffff]
[    2.141319] pci_bus 0000:03: resource 2 [mem 0xe3700000-0xe40fffff 64bit pref]
[    2.141321] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    2.141323] pci_bus 0000:04: resource 1 [mem 0xf5c00000-0xf65fffff]
[    2.141325] pci_bus 0000:04: resource 2 [mem 0xe2c00000-0xe35fffff 64bit pref]
[    2.141327] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    2.141329] pci_bus 0000:05: resource 1 [mem 0xf5200000-0xf5bfffff]
[    2.141331] pci_bus 0000:05: resource 2 [mem 0xe2100000-0xe2afffff 64bit pref]
[    2.141359] NET: Registered protocol family 2
[    2.141502] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.142433] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.144168] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.144379] TCP: Hash tables configured (established 524288 bind 65536)
[    2.144381] TCP reno registered
[    2.144391] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.144413] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.144523] NET: Registered protocol family 1
[    2.144614] pci 0000:01:00.0: Boot video device
[    2.144666] PCI: CLS 64 bytes, default 64
[    2.144668] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.144670] Placing 64MB software IO TLB between ffff8800cb426000 - ffff8800cf426000
[    2.144672] software IO TLB at phys 0xcb426000 - 0xcf426000
[    2.145209] audit: initializing netlink socket (disabled)
[    2.145217] type=2000 audit(1335388094.692:1): initialized
[    2.171780] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.184605] VFS: Disk quotas dquot_6.5.2
[    2.184657] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.185143] fuse init (API version 7.16)
[    2.185211] msgmni has been set to 7879
[    2.185500] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.185524] io scheduler noop registered
[    2.185526] io scheduler deadline registered
[    2.185558] io scheduler cfq registered (default)
[    2.185642] pcieport 0000:00:01.0: setting latency timer to 64
[    2.185669] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.185884] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.185904] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.185936] intel_idle: MWAIT substates: 0x21120
[    2.185937] intel_idle: v0.4 model 0x2A
[    2.185939] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.187762] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.188848] ACPI: AC Adapter [ADP1] (on-line)
[    2.188945] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.190952] ACPI: Lid Switch [LID0]
[    2.190992] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.190996] ACPI: Power Button [PWRB]
[    2.191017] ACPI: acpi_idle yielding to intel_idle
[    2.207860] thermal LNXTHERM:00: registered as thermal_zone0
[    2.207866] ACPI: Thermal Zone [TZ00] (57 C)
[    2.207896] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.207907] ERST: Table is not found!
[    2.207948] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.251278] ACPI: Battery Slot [BAT0] (battery present)
[    2.343175] Linux agpgart interface v0.103
[    2.344071] brd: module loaded
[    2.344454] loop: module loaded
[    2.344748] Fixed MDIO Bus: probed
[    2.344764] PPP generic driver version 2.4.2
[    2.344788] tun: Universal TUN/TAP device driver, 1.6
[    2.344790] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.344843] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.344862] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.344885] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.344888] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.344917] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.344943] ehci_hcd 0000:00:1a.0: debug port 2
[    2.348835] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.348849] ehci_hcd 0000:00:1a.0: irq 20, io mem 0xf7a08000
[    2.362606] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.362767] hub 1-0:1.0: USB hub found
[    2.362771] hub 1-0:1.0: 2 ports detected
[    2.362821] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.362832] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.362835] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.362864] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.362884] ehci_hcd 0000:00:1d.0: debug port 2
[    2.366760] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.366772] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7a07000
[    2.382587] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.382738] hub 2-0:1.0: USB hub found
[    2.382743] hub 2-0:1.0: 2 ports detected
[    2.382786] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.382794] uhci_hcd: USB Universal Host Controller Interface driver
[    2.382837] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.388025] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.388030] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.388123] mousedev: PS/2 mouse device common for all mice
[    2.388205] rtc_cmos 00:06: RTC can wake from S4
[    2.388287] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.388312] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.388392] device-mapper: uevent: version 1.0.3
[    2.388444] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    2.388623] cpuidle: using governor ladder
[    2.388914] cpuidle: using governor menu
[    2.388916] EFI Variables Facility v0.08 2004-May-17
[    2.389088] TCP cubic registered
[    2.389181] NET: Registered protocol family 10
[    2.389536] NET: Registered protocol family 17
[    2.389547] Registering the dns_resolver key type
[    2.389617] PM: Hibernation image not present or could not be loaded.
[    2.389624] registered taskstats version 1
[    2.401663]   Magic number: 8:160:147
[    2.401703] acpi device:18: hash matches
[    2.401769] rtc_cmos 00:06: setting system clock to 2012-04-25 21:08:15 UTC (1335388095)
[    2.403495] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.403496] EDD information not available.
[    2.404836] Freeing unused kernel memory: 984k freed
[    2.404934] Write protecting the kernel read-only data: 10240k
[    2.405279] Freeing unused kernel memory: 20k freed
[    2.408444] Freeing unused kernel memory: 1400k freed
[    2.411191] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.420109] udevd[99]: starting version 173
[    2.438613] sdhci: Secure Digital Host Controller Interface driver
[    2.438616] sdhci: Copyright(c) Pierre Ossman
[    2.438875] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e823] (rev 6)
[    2.438896] sdhci-pci 0000:03:00.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.438926] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.438933] sdhci-pci 0000:03:00.0: setting latency timer to 64
[    2.438956] mmc0: no vmmc regulator found
[    2.438982] Registered led device: mmc0::
[    2.439024] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    2.439219] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.439241] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    2.439245] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.439313] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    2.439478] xhci_hcd 0000:04:00.0: irq 18, io mem 0xf5c00000
[    2.439550] xhci_hcd 0000:04:00.0: irq 41 for MSI/MSI-X
[    2.439556] xhci_hcd 0000:04:00.0: irq 42 for MSI/MSI-X
[    2.439562] xhci_hcd 0000:04:00.0: irq 43 for MSI/MSI-X
[    2.439567] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    2.439573] xhci_hcd 0000:04:00.0: irq 45 for MSI/MSI-X
[    2.439578] xhci_hcd 0000:04:00.0: irq 46 for MSI/MSI-X
[    2.439584] xhci_hcd 0000:04:00.0: irq 47 for MSI/MSI-X
[    2.439589] xhci_hcd 0000:04:00.0: irq 48 for MSI/MSI-X
[    2.439793] xHCI xhci_add_endpoint called for root hub
[    2.439796] xHCI xhci_check_bandwidth called for root hub
[    2.439825] hub 3-0:1.0: USB hub found
[    2.439834] hub 3-0:1.0: 2 ports detected
[    2.439908] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.439946] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    2.440230] firewire_ohci 0000:03:00.3: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.440240] firewire_ohci 0000:03:00.3: setting latency timer to 64
[    2.440563] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.440581] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.440634] r8169 0000:05:00.0: setting latency timer to 64
[    2.440739] r8169 0000:05:00.0: irq 49 for MSI/MSI-X
[    2.441151] r8169 0000:05:00.0: eth0: RTL8168e/8111e at 0xffffc9000065a000, f0:bf:97:de:1e:82, XID 0c200000 IRQ 49
[    2.442628] ahci 0000:00:1f.2: version 3.0
[    2.442639] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.442693] ahci 0000:00:1f.2: irq 50 for MSI/MSI-X
[    2.442766] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    2.442770] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part apst
[    2.442778] ahci 0000:00:1f.2: setting latency timer to 64
[    2.443029] xHCI xhci_add_endpoint called for root hub
[    2.443032] xHCI xhci_check_bandwidth called for root hub
[    2.443305] hub 4-0:1.0: USB hub found
[    2.443314] hub 4-0:1.0: 2 ports detected
[    2.443503] scsi0 : ahci
[    2.443773] scsi1 : ahci
[    2.443883] scsi2 : ahci
[    2.443995] scsi3 : ahci
[    2.444068] scsi4 : ahci
[    2.444138] scsi5 : ahci
[    2.444391] ata1: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06100 irq 50
[    2.444393] ata2: DUMMY
[    2.444394] ata3: DUMMY
[    2.444395] ata4: DUMMY
[    2.444398] ata5: SATA max UDMA/133 abar m2048@0xf7a06000 port 0xf7a06300 irq 50
[    2.444399] ata6: DUMMY
[    2.494656] firewire_ohci 0000:03:00.3: irq 51 for MSI/MSI-X
[    2.494727] firewire_ohci: Added fw-ohci device 0000:03:00.3, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    2.674357] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.762263] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.762305] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.763291] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.764206] ata5.00: ATAPI: MATSHITADVD-RAM UJ8B0, 1.00, max UDMA/100
[    2.766617] ata5.00: configured for UDMA/100
[    2.792322] ata1.00: ATA-8: TOSHIBA MK5061GSY, MJ000H, max UDMA/100
[    2.792332] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.793513] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.793753] ata1.00: configured for UDMA/100
[    2.793994] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK5061GS MJ00 PQ: 0 ANSI: 5
[    2.794103] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.794135] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.794150] sd 0:0:0:0: [sda] Write Protect is off
[    2.794152] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.794164] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.796040] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8B0    1.00 PQ: 0 ANSI: 5
[    2.798057] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.798064] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.798265] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.798313] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.806797] hub 1-1:1.0: USB hub found
[    2.806922] hub 1-1:1.0: 6 ports detected
[    2.861626]  sda: sda1 sda2
[    2.861947] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.918111] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.994133] firewire_core: created device fw0: GUID 080046030356dd61, S400
[    3.050530] hub 2-1:1.0: USB hub found
[    3.050622] hub 2-1:1.0: 6 ports detected
[    3.121939] usb 1-1.2: new high speed USB device number 3 using ehci_hcd
[    3.141823] Refined TSC clocksource calibration: 2195.013 MHz.
[    3.141836] Switching to clocksource tsc
[    3.250335] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.672317] udevd[391]: starting version 173
[   10.675742] Adding 20479996k swap on /dev/sda2.  Priority:-1 extents:1 across:20479996k
[   10.731142] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.731516] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.731522] mei 0000:00:16.0: setting latency timer to 64
[   10.732383] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[   10.733025] lp: driver loaded but no devices found
[   10.735300] cfg80211: Calling CRDA to update world regulatory domain
[   10.743074] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.743085] ath9k 0000:02:00.0: setting latency timer to 64
[   10.750688] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.750754] HDA Intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[   10.750780] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.752703] wmi: Mapper loaded
[   10.755944] sony_laptop: Sony Notebook Control Driver v0.6
[   10.772468] cfg80211: World regulatory domain updated:
[   10.772471] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.772475] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.772477] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.772480] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.772482] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.772485] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.791268] hda_codec: ALC275: BIOS auto-probing.
[   10.794914] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   10.794961] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   10.795045] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.795046] hda_intel: Disabling MSI
[   10.795120] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.818169] Linux video capture interface: v2.00
[   10.818559] uvcvideo: Found UVC 1.00 device USB2.0 Camera (05ca:18c0)
[   10.819851] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[   10.819893] usbcore: registered new interface driver uvcvideo
[   10.819895] USB Video Class driver (v1.1.0)
[   10.831165] ath: EEPROM regdomain: 0x65
[   10.831167] ath: EEPROM indicates we should expect a direct regpair map
[   10.831169] ath: Country alpha2 being used: 00
[   10.831170] ath: Regpair used: 0x65
[   10.831172] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.831174] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831176] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.831178] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831179] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.831180] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831182] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.831183] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831185] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.831186] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831187] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.831189] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831190] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.831192] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831193] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.831195] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831196] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.831197] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831199] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.831200] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831202] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.831203] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831205] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.831206] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831207] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.831209] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   10.831210] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.832175] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.833854] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.834234] Registered led device: ath9k-phy0
[   10.834241] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc900050a0000, irq=16
[   10.856415] acpi device:20: registered as cooling_device8
[   10.858081] type=1400 audit(1335388103.964:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=577 comm="apparmor_parser"
[   10.859035] type=1400 audit(1335388103.964:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=500 comm="apparmor_parser"
[   10.859042] type=1400 audit(1335388103.964:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=680 comm="apparmor_parser"
[   10.859046] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input6
[   10.859119] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[   10.859154] type=1400 audit(1335388103.964:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=577 comm="apparmor_parser"
[   10.859171] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[   10.859343] type=1400 audit(1335388103.964:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=577 comm="apparmor_parser"
[   10.859484] type=1400 audit(1335388103.964:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=500 comm="apparmor_parser"
[   10.859504] type=1400 audit(1335388103.964:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=680 comm="apparmor_parser"
[   10.859768] type=1400 audit(1335388103.964:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=500 comm="apparmor_parser"
[   10.859786] type=1400 audit(1335388103.964:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=680 comm="apparmor_parser"
[   10.870473] acpi device:21: registered as cooling_device9
[   10.870539] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1f/LNXVIDEO:00/input/input8
[   10.870601] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   10.873366] [drm] Initialized drm 1.1.0 20060810
[   10.877116] MXM: GUID detected in BIOS
[   11.403776] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.573055] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   11.608446] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   11.623411] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   11.640466] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   11.672369] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   11.674673] type=1400 audit(1335388104.780:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=835 comm="apparmor_parser"
[   11.704329] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   11.720393] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   11.720469] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   11.720521] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   11.720574] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   11.720878] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.720883] nouveau 0000:01:00.0: setting latency timer to 64
[   11.723067] [drm] nouveau 0000:01:00.0: Detected an NVc0 generation card (0x0c1a00a1)
[   11.731099] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   11.734618] init: failsafe main process (770) killed by TERM signal
[   11.734948] init: apport pre-start process (872) terminated with status 1
[   11.739400] init: apport post-stop process (904) terminated with status 1
[   11.784045] r8169 0000:05:00.0: eth0: link down
[   11.784317] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.793314] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   11.793316] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   11.793319] [drm] nouveau 0000:01:00.0: Bios version 70.08.58.00
[   11.793320] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[   11.793323] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[   11.793324] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   11.793326] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000323 00010034
[   11.793328] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02011300 00000000
[   11.793330] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02422362 00020010
[   11.793331] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0000000e 00000000
[   11.793333] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   11.793335] [drm] nouveau 0000:01:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[   11.793337] [drm] nouveau 0000:01:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   11.793338] [drm] nouveau 0000:01:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
[   11.793342] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD607
[   11.813347] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDC63
[   11.820324] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xEE69
[   11.820326] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEE6D
[   11.820368] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEF55
[   11.820369] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEFBA
[   11.840195] [drm] nouveau 0000:01:00.0: 0xD540: Condition still not met after 20ms, skipping following opcodes
[   11.851838] Bluetooth: Core ver 2.16
[   11.851858] NET: Registered protocol family 31
[   11.851859] Bluetooth: HCI device and connection manager initialized
[   11.851861] Bluetooth: HCI socket layer initialized
[   11.851863] Bluetooth: L2CAP socket layer initialized
[   11.851891] Bluetooth: SCO socket layer initialized
[   11.853520] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.853523] Bluetooth: BNEP filters: protocol multicast
[   11.855718] Bluetooth: RFCOMM TTY layer initialized
[   11.855722] Bluetooth: RFCOMM socket layer initialized
[   11.855724] Bluetooth: RFCOMM ver 1.11
[   11.858953] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[   11.858957] [drm] nouveau 0000:01:00.0: 0: memory 135MHz core 50MHz shader 101MHz voltage 830mV timing 0
[   11.858960] [drm] nouveau 0000:01:00.0: 1: memory 324MHz core 202MHz shader 405MHz voltage 830mV timing 1
[   11.858963] [drm] nouveau 0000:01:00.0: 3: memory 900MHz core 672MHz shader 1344MHz voltage 980mV timing 2
[   11.859015] [TTM] Zone  kernel: Available graphics memory: 2018368 kiB.
[   11.859017] [TTM] Initializing pool allocator.
[   11.859029] [drm] nouveau 0000:01:00.0: Detected 512MiB VRAM
[   11.864970] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   11.864978] [drm] nouveau 0000:01:00.0: PGRAPH: unsupported chipset, please report!
[   11.872145] [drm] nouveau 0000:01:00.0: ACPI backlight interface available, not registering our own
[   11.873109] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.873111] [drm] No driver support for vblank timestamp query.
[   12.038343] [drm] nouveau 0000:01:00.0: allocated 1920x1080 fb: 0x8020000, bo ffff880124fc3800
[   12.038401] fbcon: nouveaufb (fb0) is primary device
[   12.038523] Console: switching to colour frame buffer device 240x67
[   12.038558] fb0: nouveaufb frame buffer device
[   12.038559] drm: registered panic notifier
[   12.038566] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   12.413841] ppdev: user-space parallel port driver
[   12.707544] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.056851] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   64.188886] r8169 0000:05:00.0: eth0: link up
[   64.189196] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   74.455697] eth0: no IPv6 routers present
```network config


```
  *-network DISABLED
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: cc:af:78:b1:3c:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7000000-f700ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: f0:bf:97:de:1e:82
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:49 ioport:9000(size=256) memory:e2104000-e2104fff memory:e2100000-e2103fff
```will post more info on request, and i am kind of a noob, but i did try to research some solutions to this problem, namely articles on the ar9287, they mostly either suggested packages that are not for this version of ubuntu, or the ar9k config file

edit:
i fixed the slow apt-get by changing servers, but my wireless still appears to not work at all.

---

### Post by jumbobits on 2012-04-26
i did a fresh install of 12.04, and still no luck. Any help at all for be much appreciated, after all, i am a noob :icon_frown:

---

### Post by chili555 on 2012-04-26
> *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.This often means that the hardware switch is Off. Can you please check that and post:```
rfkill list all
```

---

### Post by jumbobits on 2012-04-27
thank you for the help


```
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

by hardware switch do you mean the wireless router (thats on, i am using it now,but not laptop i am trying to fix right now)

---

### Post by chili555 on 2012-04-27
By "hardware switch" I mean the slider right on the front of your computer. Please see attached where it is number 14.

Your readings strongly suggest it's switched to OFF.> 0: sony-wifi: Wireless LAN
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]
2: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]

---

### Post by jumbobits on 2012-04-27
> **chili555 said:**
> By "hardware switch" I mean the slider right on the front of your computer. Please see attached where it is number 14.

Your readings strongly suggest it's switched to OFF.

id send you a mountain of cake, but i have no idea where you live.

---

### Post by chili555 on 2012-04-27
May I assume 'mountain of cake' = Solved?

---

