---
title: "Help with DVB-S2 installation"
date: 2010-03-18
forum: Mythbuntu
---

### Post by Conar on 2010-03-18
Hi.

First off let me clear up my linux knowledge level. I'm a gimp. Started using it a few days back really. I'm trying to set up Mythbuntu so I can use MythTV as my HTPC solution.

Hardware:
CPU - C2D E8400
MB - P5Q-EM with onboard x4500hd GPU
Tuner - Mystique Satix DVB-S2 Dual
HDD1 - OCZ SSD for Mythbuntu
HDD2 - 150GB Raptor for Win7 MCE
HDD3 - Samsung F1 750GB for storage

Background - Win7 is a bit heavy when all I want to do is watch movies and record TV so I decided to give MythTV a go.
Installed Mythbuntu 9.10 without any hiccups.
Tried the setup but couldn't find my capture card.
Only one that doesn't give an error of "Probed info: Failed to open" is the DVB DTV capture card (v3.x). Tried selecting that but no response in DVB Device Number.
Selected it anyway but nothing in MythTV frontend.

Followed the guide here to install drivers for my card:
[http://www.linuxtv.org/wiki/index.php/Mystique_SaTiX-S2_Dual#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Mystique_SaTiX-S2_Dual#Making_it_Work)
Had to install mercurial first to get it working but it seemed to work ok. There were some errors (I think) but it got through.
Back into the backend but no sign of a new card. Not even sure if there should be one.
I've scoured the web for an easy how to guide but that just doesn't seem to be the way things work in the linux world.

I can use Win7 so its not a major downer for me but I thought I'd post here in case people were feeling generous or time rich and wanted to help me out.

Can anyone assist at all or point me in the right direction?
I'd be very grateful for any assistance.

---

### Post by managementboy on 2010-03-19
have you tried getting it to work with Kaffeine first? or any other TV application for that matter... I would do that first, then start tweaking mythtv.

---

### Post by Conar on 2010-03-19
OK, in case it helps I've taken the output from "dmesg" and "lspci -vvvnn".
I reinstalled this morning by the way in case I had cocked it up somehow. All I have done is run the standard install and added the latest updates from update manager.
It looks like it detects the card but the drivers aren't loaded properly.

```
conor@Myth:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa053a0c-14f7-49c9-acc0-78014af96b07 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7d80000 (usable)
[    0.000000]  BIOS-e820: 00000000c7d80000 - 00000000c7d8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7d8e000 - 00000000c7dd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7dd0000 - 00000000c7e00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 0C7E00000 mask FFFE00000 uncachable
[    0.000000]   6 base 0C8000000 mask FF8000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c7e00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7d80 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000c7d80000 (usable)
[    0.000000]  modified: 00000000c7d80000 - 00000000c7d8e000 (ACPI data)
[    0.000000]  modified: 00000000c7d8e000 - 00000000c7dd0000 (ACPI NVS)
[    0.000000]  modified: 00000000c7dd0000 - 00000000c7e00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7d80000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c7c00000 page 2M
[    0.000000]  00c7c00000 - 00c7d80000 page 4k
[    0.000000] kernel direct mapping tables up to c7d80000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] RAMDISK: 3786d000 - 37fefa9d
[    0.000000] ACPI: RSDP 00000000000fb900 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000c7d80100 00064 (v01 A_M_I_ OEMXSDT  07000908 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000c7d80290 000F4 (v03 A_M_I_ OEMFACP  07000908 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000c7d80440 090EB (v01  A0982 A0982070 00000070 INTL 20060113)
[    0.000000] ACPI: FACS 00000000c7d8e000 00040
[    0.000000] ACPI: APIC 00000000c7d80390 0006C (v01 A_M_I_ OEMAPIC  07000908 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000c7d80400 0003C (v01 A_M_I_ OEMMCFG  07000908 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000c7d8e040 00089 (v01 A_M_I_ AMI_OEM  07000908 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000c7d89530 00038 (v01 A_M_I_ OEMHPET  07000908 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000c7d8e0d0 02024 (v01 A_M_I_ GMCHSCI  07000908 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000c7d89570 000B0 (v01 A_M_I_ OEMOSFR  07000908 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c7d90b50 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
[    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]
[    0.000000]   #3 [003786d000 - 0037fefa9d]          RAMDISK ==> [003786d000 - 0037fefa9d]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e9000 - 00019e9294]              BRK ==> [00019e9000 - 00019e9294]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c7d80
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1015055
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3823 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 800184 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
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
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c7d80000 - 00000000c7d8e000
[    0.000000] PM: Registered nosave memory: 00000000c7d8e000 - 00000000c7dd0000
[    0.000000] PM: Registered nosave memory: 00000000c7dd0000 - 00000000c7e00000
[    0.000000] PM: Registered nosave memory: 00000000c7e00000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c7e00000 (gap: c7e00000:37000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997927
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa053a0c-14f7-49c9-acc0-78014af96b07 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 3918360k/4980736k available (5327k kernel code, 920516k absent, 141860k reserved, 3014k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3000.025 MHz processor.
[    0.001012] Console: colour VGA+ 80x25
[    0.001015] console [tty0] enabled
[    0.010000] allocated 40632320 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.05 BogoMIPS (lpj=30000250)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.020051] Setting APIC routing to flat
[    0.020349] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.128377] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5999.33 BogoMIPS (lpj=29996670)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.281626] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.281633] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290019] Brought up 2 CPUs
[    0.290021] Total of 2 processors activated (11999.38 BogoMIPS).
[    0.290067] CPU0 attaching sched-domain:
[    0.290070]  domain 0: span 0-1 level MC
[    0.290072]   groups: 0 1
[    0.290075] CPU1 attaching sched-domain:
[    0.290077]  domain 0: span 0-1 level MC
[    0.290078]   groups: 1 0
[    0.290135] Booting paravirtualized kernel on bare hardware
[    0.290135] regulator: core version 0.5
[    0.290135] Time: 13:44:10  Date: 03/19/10
[    0.290135] NET: Registered protocol family 16
[    0.290159] ACPI: bus type pci registered
[    0.290212] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.290213] PCI: Not using MMCONFIG.
[    0.290215] PCI: Using configuration type 1 for base access
[    0.290776] bio: create slab <bio-0> at 0
[    0.290776] ACPI: EC: Look up EC in DSDT
[    0.303876] ACPI: Interpreter enabled
[    0.303879] ACPI: (supports S0 S1 S3 S4 S5)
[    0.303895] ACPI: Using IOAPIC for interrupt routing
[    0.303936] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.305967] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.310819] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.316439] ACPI Warning: Incorrect checksum in table [OEMB] - 0C, should be 0B 20090521 tbutils-246
[    0.317231] ACPI: No dock devices found.
[    0.317350] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.317411] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe000000-0xfe3fffff]
[    0.317415] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.317418] pci 0000:00:02.0: reg 20 io port: [0xcc00-0xcc07]
[    0.317443] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe700000-0xfe7fffff]
[    0.317513] pci 0000:00:1a.0: reg 20 io port: [0xc480-0xc49f]
[    0.317567] pci 0000:00:1a.1: reg 20 io port: [0xc800-0xc81f]
[    0.317620] pci 0000:00:1a.2: reg 20 io port: [0xc880-0xc89f]
[    0.317677] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe6fb000-0xfe6fb3ff]
[    0.317721] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.317725] pci 0000:00:1a.7: PME# disabled
[    0.317755] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe6f4000-0xfe6f7fff]
[    0.317787] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.317790] pci 0000:00:1b.0: PME# disabled
[    0.317834] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.317836] pci 0000:00:1c.0: PME# disabled
[    0.317881] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.317884] pci 0000:00:1c.1: PME# disabled
[    0.317930] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.317932] pci 0000:00:1c.4: PME# disabled
[    0.317977] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.317980] pci 0000:00:1c.5: PME# disabled
[    0.318021] pci 0000:00:1d.0: reg 20 io port: [0xc000-0xc01f]
[    0.318076] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.318129] pci 0000:00:1d.2: reg 20 io port: [0xc400-0xc41f]
[    0.318186] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe6fa000-0xfe6fa3ff]
[    0.318230] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.318233] pci 0000:00:1d.7: PME# disabled
[    0.318328] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.318331] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.318333] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.318376] pci 0000:00:1f.2: reg 10 io port: [0xac00-0xac07]
[    0.318380] pci 0000:00:1f.2: reg 14 io port: [0xa880-0xa883]
[    0.318384] pci 0000:00:1f.2: reg 18 io port: [0xa800-0xa807]
[    0.318389] pci 0000:00:1f.2: reg 1c io port: [0xa480-0xa483]
[    0.318393] pci 0000:00:1f.2: reg 20 io port: [0xa400-0xa40f]
[    0.318397] pci 0000:00:1f.2: reg 24 io port: [0xa080-0xa08f]
[    0.318433] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe6f9000-0xfe6f90ff]
[    0.318443] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.318476] pci 0000:00:1f.5: reg 10 io port: [0xbc00-0xbc07]
[    0.318480] pci 0000:00:1f.5: reg 14 io port: [0xb880-0xb883]
[    0.318484] pci 0000:00:1f.5: reg 18 io port: [0xb800-0xb807]
[    0.318488] pci 0000:00:1f.5: reg 1c io port: [0xb480-0xb483]
[    0.318492] pci 0000:00:1f.5: reg 20 io port: [0xb400-0xb40f]
[    0.318496] pci 0000:00:1f.5: reg 24 io port: [0xb080-0xb08f]
[    0.318554] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.318600] pci 0000:03:00.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.318614] pci 0000:03:00.0: reg 14 64bit mmio: [0xfeae0000-0xfeaeffff]
[    0.318718] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.318758] pci 0000:02:00.0: reg 10 io port: [0xec00-0xec07]
[    0.318765] pci 0000:02:00.0: reg 14 io port: [0xe880-0xe883]
[    0.318771] pci 0000:02:00.0: reg 18 io port: [0xe800-0xe807]
[    0.318778] pci 0000:02:00.0: reg 1c io port: [0xe480-0xe483]
[    0.318784] pci 0000:02:00.0: reg 20 io port: [0xe400-0xe40f]
[    0.318791] pci 0000:02:00.0: reg 24 32bit mmio: [0xfe9ffc00-0xfe9ffdff]
[    0.318825] pci 0000:02:00.0: supports D1
[    0.318826] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.318830] pci 0000:02:00.0: PME# disabled
[    0.318868] pci 0000:00:1c.4: bridge io port: [0xe000-0xefff]
[    0.318871] pci 0000:00:1c.4: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.318912] pci 0000:01:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.318929] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe8ff000-0xfe8fffff]
[    0.318940] pci 0000:01:00.0: reg 20 64bit mmio: [0xfdef0000-0xfdefffff]
[    0.318947] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe8c0000-0xfe8dffff]
[    0.318981] pci 0000:01:00.0: supports D1 D2
[    0.318982] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.318986] pci 0000:01:00.0: PME# disabled
[    0.319032] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
[    0.319035] pci 0000:00:1c.5: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.319040] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.319069] pci 0000:05:03.0: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.319106] pci 0000:05:03.0: supports D1 D2
[    0.319107] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.319111] pci 0000:05:03.0: PME# disabled
[    0.319146] pci 0000:00:1e.0: transparent bridge
[    0.319150] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.319171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.319270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.319327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.319367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.319411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.319449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.333059] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.333147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.333232] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.333318] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.333407] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.333492] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.333577] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.333662] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.333775] SCSI subsystem initialized
[    0.333787] libata version 3.00 loaded.
[    0.333787] usbcore: registered new interface driver usbfs
[    0.333787] usbcore: registered new interface driver hub
[    0.333787] usbcore: registered new device driver usb
[    0.333787] ACPI: WMI: Mapper loaded
[    0.333787] PCI: Using ACPI for IRQ routing
[    0.360008] Bluetooth: Core ver 2.15
[    0.360022] NET: Registered protocol family 31
[    0.360022] Bluetooth: HCI device and connection manager initialized
[    0.360022] Bluetooth: HCI socket layer initialized
[    0.360022] NetLabel: Initializing
[    0.360022] NetLabel:  domain hash size = 128
[    0.360022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360032] NetLabel:  unlabeled traffic allowed by default
[    0.360076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.360081] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400005] pnp: PnP ACPI init
[    0.400013] ACPI: bus type pnp registered
[    0.402304] pnp: PnP ACPI: found 15 devices
[    0.402305] ACPI: ACPI bus type pnp unregistered
[    0.402312] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.402316] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.402320] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.402322] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.402324] system 00:07: ioport range 0x500-0x57f could not be reserved
[    0.402326] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.402328] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.402330] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.402332] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.402336] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
[    0.402340] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.402342] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.402345] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.402349] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.402351] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    0.402352] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.402354] system 00:0e: iomem range 0x100000-0xc7dfffff could not be reserved
[    0.402356] system 00:0e: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.406967] AppArmor: AppArmor Filesystem Enabled
[    0.407004] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.407005] pci 0000:00:1c.0:   IO window: disabled
[    0.407009] pci 0000:00:1c.0:   MEM window: disabled
[    0.407012] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.407016] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.407017] pci 0000:00:1c.1:   IO window: disabled
[    0.407021] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.407024] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.407027] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    0.407029] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.407032] pci 0000:00:1c.4:   MEM window: 0xfe900000-0xfe9fffff
[    0.407035] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.407038] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
[    0.407040] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.407043] pci 0000:00:1c.5:   MEM window: 0xfe800000-0xfe8fffff
[    0.407046] pci 0000:00:1c.5:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.407051] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.407052] pci 0000:00:1e.0:   IO window: disabled
[    0.407055] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.407058] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.407065]   alloc irq_desc for 17 on node 0
[    0.407066]   alloc kstat_irqs on node 0
[    0.407070] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.407073] pci 0000:00:1c.0: setting latency timer to 64
[    0.407077]   alloc irq_desc for 16 on node 0
[    0.407079]   alloc kstat_irqs on node 0
[    0.407084] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.407087] pci 0000:00:1c.1: setting latency timer to 64
[    0.407092] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.407094] pci 0000:00:1c.4: setting latency timer to 64
[    0.407099] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.407102] pci 0000:00:1c.5: setting latency timer to 64
[    0.407106] pci 0000:00:1e.0: setting latency timer to 64
[    0.407109] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.407111] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.407113] pci_bus 0000:04: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.407114] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.407116] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.407117] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.407119] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.407120] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.407122] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.407123] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.407125] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.407126] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.407146] NET: Registered protocol family 2
[    0.407254] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.407993] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.410738] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.411141] TCP: Hash tables configured (established 524288 bind 65536)
[    0.411143] TCP reno registered
[    0.411246] NET: Registered protocol family 1
[    0.411296] Trying to unpack rootfs image as initramfs...
[    0.501648] Switched to high resolution mode on CPU 1
[    0.509988] Switched to high resolution mode on CPU 0
[    0.534114] Freeing initrd memory: 7690k freed
[    0.536350] Scanning for low memory corruption every 60 seconds
[    0.536460] audit: initializing netlink socket (disabled)
[    0.536474] type=2000 audit(1269006249.530:1): initialized
[    0.543051] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.543988] VFS: Disk quotas dquot_6.5.2
[    0.544027] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.544417] fuse init (API version 7.12)
[    0.544470] msgmni has been set to 7668
[    0.544619] alg: No test for stdrng (krng)
[    0.544628] io scheduler noop registered
[    0.544630] io scheduler anticipatory registered
[    0.544631] io scheduler deadline registered
[    0.544655] io scheduler cfq registered (default)
[    0.544665] pci 0000:00:02.0: Boot video device
[    0.544885]   alloc irq_desc for 24 on node 0
[    0.544886]   alloc kstat_irqs on node 0
[    0.544896] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.544902] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.545001]   alloc irq_desc for 25 on node 0
[    0.545002]   alloc kstat_irqs on node 0
[    0.545007] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.545013] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.545110]   alloc irq_desc for 26 on node 0
[    0.545112]   alloc kstat_irqs on node 0
[    0.545117] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.545122] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.545220]   alloc irq_desc for 27 on node 0
[    0.545221]   alloc kstat_irqs on node 0
[    0.545226] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.545231] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.545300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.545391] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.545481] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.545484] ACPI: Power Button [PWRF]
[    0.545525] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.545526] ACPI: Power Button [PWRB]
[    0.546071] ACPI: SSDT 00000000c7d90100 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.546430] ACPI: SSDT 00000000c7d90600 004B2 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    0.546855] Monitor-Mwait will be used to enter C-1 state
[    0.546871] Monitor-Mwait will be used to enter C-2 state
[    0.546887] Monitor-Mwait will be used to enter C-3 state
[    0.546892] Marking TSC unstable due to TSC halts in idle
[    0.546906] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.546922] processor LNXCPU:00: registered as cooling_device0
[    0.547246] ACPI: SSDT 00000000c7d90380 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.547498] ACPI: SSDT 00000000c7d90ac0 00085 (v01  PmRef  P002Cst 00003000 INTL 20060113)
[    0.547979] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.547991] processor LNXCPU:01: registered as cooling_device1
[    0.550451] Linux agpgart interface v0.103
[    0.550457] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.550540] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.550786] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.551436] brd: module loaded
[    0.551732] loop: module loaded
[    0.551776] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.551895] ata_piix 0000:00:1f.2: version 2.13
[    0.551904]   alloc irq_desc for 19 on node 0
[    0.551905]   alloc kstat_irqs on node 0
[    0.551909] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.551912] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.551942] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.551986] scsi0 : ata_piix
[    0.552039] scsi1 : ata_piix
[    0.553145] ata1: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[    0.553149] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[    0.553183] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.553187] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.553214] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.553243] scsi2 : ata_piix
[    0.553280] scsi3 : ata_piix
[    0.554205] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    0.554208] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    0.554472] pata_marvell 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.554489] pata_marvell 0000:02:00.0: setting latency timer to 64
[    0.554523] scsi4 : pata_marvell
[    0.554557] scsi5 : pata_marvell
[    0.554580] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    0.554581] ata6: DUMMY
[    0.554881] Fixed MDIO Bus: probed
[    0.554905] PPP generic driver version 2.4.2
[    0.554959] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.554986]   alloc irq_desc for 18 on node 0
[    0.554987]   alloc kstat_irqs on node 0
[    0.554990] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.555000] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.555002] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.555022] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.558929] ehci_hcd 0000:00:1a.7: debug port 1
[    0.558934] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.558942] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe6fb000
[    0.580027] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.580118] usb usb1: configuration #1 chosen from 1 choice
[    0.580147] hub 1-0:1.0: USB hub found
[    0.580154] hub 1-0:1.0: 6 ports detected
[    0.580310]   alloc irq_desc for 23 on node 0
[    0.580311]   alloc kstat_irqs on node 0
[    0.580314] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580320] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.580323] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.580341] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.584229] ehci_hcd 0000:00:1d.7: debug port 1
[    0.584233] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.584241] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe6fa000
[    0.600010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.600064] usb usb2: configuration #1 chosen from 1 choice
[    0.600088] hub 2-0:1.0: USB hub found
[    0.600093] hub 2-0:1.0: 6 ports detected
[    0.600151] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.600166] uhci_hcd: USB Universal Host Controller Interface driver
[    0.600226] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.600230] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.600232] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.600250] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.600268] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c480
[    0.600317] usb usb3: configuration #1 chosen from 1 choice
[    0.600333] hub 3-0:1.0: USB hub found
[    0.600337] hub 3-0:1.0: 2 ports detected
[    0.600384]   alloc irq_desc for 21 on node 0
[    0.600385]   alloc kstat_irqs on node 0
[    0.600388] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.600392] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.600394] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.600412] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.600436] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.600484] usb usb4: configuration #1 chosen from 1 choice
[    0.600500] hub 4-0:1.0: USB hub found
[    0.600504] hub 4-0:1.0: 2 ports detected
[    0.600552] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.600555] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.600558] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.600576] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.600594] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000c880
[    0.600641] usb usb5: configuration #1 chosen from 1 choice
[    0.600658] hub 5-0:1.0: USB hub found
[    0.600663] hub 5-0:1.0: 2 ports detected
[    0.600706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.600710] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.600712] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.600731] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.600749] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c000
[    0.600795] usb usb6: configuration #1 chosen from 1 choice
[    0.600812] hub 6-0:1.0: USB hub found
[    0.600816] hub 6-0:1.0: 2 ports detected
[    0.600859] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.600864] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.600867] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.600890] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.600908] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.600957] usb usb7: configuration #1 chosen from 1 choice
[    0.600973] hub 7-0:1.0: USB hub found
[    0.600977] hub 7-0:1.0: 2 ports detected
[    0.601024] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.601028] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.601030] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.601049] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.601067] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c400
[    0.601115] usb usb8: configuration #1 chosen from 1 choice
[    0.601130] hub 8-0:1.0: USB hub found
[    0.601134] hub 8-0:1.0: 2 ports detected
[    0.601201] PNP: No PS/2 controller found. Probing ports directly.
[    0.603863] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.603867] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.603906] mice: PS/2 mouse device common for all mice
[    0.603961] rtc_cmos 00:03: RTC can wake from S4
[    0.603984] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.604003] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.604080] device-mapper: uevent: version 1.0.3
[    0.604149] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.604195] device-mapper: multipath: version 1.1.0 loaded
[    0.604197] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.604354] cpuidle: using governor ladder
[    0.604426] cpuidle: using governor menu
[    0.604686] TCP cubic registered
[    0.604767] NET: Registered protocol family 10
[    0.605056] lo: Disabled Privacy Extensions
[    0.605247] NET: Registered protocol family 17
[    0.605259] Bluetooth: L2CAP ver 2.13
[    0.605260] Bluetooth: L2CAP socket layer initialized
[    0.605263] Bluetooth: SCO (Voice Link) ver 0.6
[    0.605264] Bluetooth: SCO socket layer initialized
[    0.605284] Bluetooth: RFCOMM TTY layer initialized
[    0.605287] Bluetooth: RFCOMM socket layer initialized
[    0.605288] Bluetooth: RFCOMM ver 1.11
[    0.605910] PM: Resume from disk failed.
[    0.605918] registered taskstats version 1
[    0.606008]   Magic number: 2:471:736
[    0.606067] rtc_cmos 00:03: setting system clock to 2010-03-19 13:44:10 UTC (1269006250)
[    0.606069] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.606070] EDD information not available.
[    0.910707] ata3: SATA link down (SStatus 0 SControl 300)
[    1.060066] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.080213] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-H62N, CL01, max UDMA/100
[    1.120230] ata4.00: configured for UDMA/100
[    1.181274] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.363672] usb 5-1: configuration #1 chosen from 1 choice
[    1.410075] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.410085] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.421319] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.421331] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.431703] ata1.00: ATA-8: OCZ CORE_SSD, 02.10103, max UDMA/100
[    1.431705] ata1.00: 118128640 sectors, multi 0: LBA 
[    1.450985] ata2.00: ATA-7: WDC WD1500ADFD-00NLR3, 21.07QR3, max UDMA/133
[    1.450988] ata2.00: 293046768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.451130] ata2.01: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    1.451133] ata2.01: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.470332] ata1.00: configured for UDMA/100
[    1.470406] scsi 0:0:0:0: Direct-Access     ATA      OCZ CORE_SSD     02.1 PQ: 0 ANSI: 5
[    1.470475] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.470499] sd 0:0:0:0: [sda] 118128640 512-byte logical blocks: (60.4 GB/56.3 GiB)
[    1.470528] sd 0:0:0:0: [sda] Write Protect is off
[    1.470530] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.470546] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.470628]  sda:
[    1.490880] ata2.00: configured for UDMA/133
[    1.510310] ata2.01: configured for UDMA/133
[    1.510369] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[    1.510463] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.510524] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    1.510609] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.510643] sd 1:0:0:0: [sdb] 293046768 512-byte logical blocks: (150 GB/139 GiB)
[    1.510671] sd 1:0:0:0: [sdb] Write Protect is off
[    1.510673] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.510688] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.510756]  sdb:
[    1.515206] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H62N  CL01 PQ: 0 ANSI: 5
[    1.525992]  sdb1 sdb2 <
[    1.526007] sd 1:0:1:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.535429]  sdb5 >
[    1.535468] sd 1:0:1:0: [sdc] Write Protect is off
[    1.535471] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.535493] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.535632]  sdc: sdc1
[    1.546334] sd 1:0:1:0: [sdc] Attached SCSI disk
[    1.546344] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.660026] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    1.846987] usb 7-1: configuration #1 chosen from 1 choice
[    1.849159] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.849161] Uniform CD-ROM driver Revision: 3.20
[    1.849203] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.849228] sr 3:0:0:0: Attached scsi generic sg3 type 5
[    2.278833]  sda1
[    2.279004] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.279024] Freeing unused kernel memory: 664k freed
[    2.279170] Write protecting the kernel read-only data: 7596k
[    2.338116] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
[    2.339436] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    2.341462] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.352290] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.352313] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.352361] r8169 0000:01:00.0: setting latency timer to 64
[    2.352401]   alloc irq_desc for 28 on node 0
[    2.352403]   alloc kstat_irqs on node 0
[    2.352416] r8169 0000:01:00.0: irq 28 for MSI/MSI-X
[    2.352834] eth0: RTL8168c/8111c at 0xffffc90000676000, 90:e6:ba:85:15:f1, XID 3c4000c0 IRQ 28
[    2.397644] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.397757] usbcore: registered new interface driver hiddev
[    2.412921] input: Microsoft Microsoft(R) Compact Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.412981] generic-usb 0003:045E:00A4.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft(R) Compact Optical Mouse] on usb-0000:00:1a.2-1/input0
[    2.425155] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4
[    2.425188] generic-usb 0003:046E:5577.0002: input,hidraw1: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:1d.1-1/input0
[    2.452013] [drm] Initialized drm 1.1.0 20060810
[    2.452051] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.459093] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.459103] i915 0000:00:02.0: setting latency timer to 64
[    2.468160] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    2.468162] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.468752] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input5
[    2.468833] generic-usb 0003:046E:5577.0003: input,hiddev96,hidraw2: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:1d.1-1/input1
[    2.468848] usbcore: registered new interface driver usbhid
[    2.468849] usbhid: v2.6:USB HID core driver
[    2.469317]   alloc irq_desc for 29 on node 0
[    2.469320]   alloc kstat_irqs on node 0
[    2.469328] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    2.474324] [drm] i2c_init DPDDC-B
[    2.484998] [drm] i2c_init DPDDC-C
[    2.537414] i2c-adapter i2c-1: unable to read EDID block.
[    2.537490] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    3.147226] [drm] fb0: inteldrmfb frame buffer device
[    3.147278] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.212716] [drm] TMDS-12: set mode 1920x1080 1f
[    3.236718] Console: switching to colour frame buffer device 240x67
[    3.443945] PM: Starting manual resume from disk
[    3.443948] PM: Resume from partition 8:21
[    3.443949] PM: Checking hibernation image.
[    3.444080] PM: Resume from disk failed.
[    3.446993] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.446996] EXT4-fs (sda1): write access will be enabled during recovery
[    3.447548] EXT4-fs (sda1): barriers enabled
[    3.791452] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000b83c84]
[    5.053577] kjournald2 starting: pid 466, dev sda1:8, commit interval 5 seconds
[    5.053657] EXT4-fs (sda1): delayed allocation enabled
[    5.053661] EXT4-fs: file extents enabled
[    5.056133] EXT4-fs: mballoc enabled
[    5.056143] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.056149] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1305
[    5.056214] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 600
[    5.056225] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 593
[    5.056237] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 571
[    5.056248] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 567
[    5.056259] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 563
[    5.056269] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 561
[    5.056281] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 512
[    5.056307] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 490
[    5.056318] EXT4-fs (sda1): 9 orphan inodes deleted
[    5.056320] EXT4-fs (sda1): recovery complete
[    5.077516] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.189383] type=1505 audit(1269006255.073:2): operation="profile_load" pid=491 name=/sbin/dhclient3
[    5.189939] type=1505 audit(1269006255.073:3): operation="profile_load" pid=491 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.190214] type=1505 audit(1269006255.083:4): operation="profile_load" pid=491 name=/usr/lib/connman/scripts/dhclient-script
[    5.200201] type=1505 audit(1269006255.093:5): operation="profile_load" pid=492 name=/usr/bin/evince
[    5.207758] type=1505 audit(1269006255.093:6): operation="profile_load" pid=492 name=/usr/bin/evince-previewer
[    5.212231] type=1505 audit(1269006255.103:7): operation="profile_load" pid=492 name=/usr/bin/evince-thumbnailer
[    5.218700] type=1505 audit(1269006255.103:8): operation="profile_load" pid=494 name=/usr/sbin/mysqld
[    5.220291] type=1505 audit(1269006255.113:9): operation="profile_load" pid=495 name=/usr/sbin/ntpd
[    5.221626] type=1505 audit(1269006255.113:10): operation="profile_load" pid=496 name=/usr/sbin/tcpdump
[    5.363585] Adding 2610520k swap on /dev/sdb5.  Priority:-1 extents:1 across:2610520k 
[    5.395077] EXT4-fs (sda1): internal journal on sda1:8
[    5.409927] udev: starting version 147
[    5.556368] RPC: Registered udp transport module.
[    5.556370] RPC: Registered tcp transport module.
[    5.613480] lp: driver loaded but no devices found
[    5.749046] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    5.825480]   alloc irq_desc for 22 on node 0
[    5.825482]   alloc kstat_irqs on node 0
[    5.825487] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.825533] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.837290] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.959834] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[    6.545901] r8169: eth0: link up
[    6.545903] r8169: eth0: link up
[    6.581169] type=1505 audit(1269006256.473:11): operation="profile_replace" pid=1087 name=/sbin/dhclient3
[    6.581656] type=1505 audit(1269006256.473:12): operation="profile_replace" pid=1087 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.581917] type=1505 audit(1269006256.473:13): operation="profile_replace" pid=1087 name=/usr/lib/connman/scripts/dhclient-script
[    6.584320] type=1505 audit(1269006256.473:14): operation="profile_replace" pid=1088 name=/usr/bin/evince
[    6.592206] type=1505 audit(1269006256.483:15): operation="profile_replace" pid=1088 name=/usr/bin/evince-previewer
[    6.596670] type=1505 audit(1269006256.483:16): operation="profile_replace" pid=1088 name=/usr/bin/evince-thumbnailer
[    6.602676] type=1505 audit(1269006256.493:17): operation="profile_replace" pid=1090 name=/usr/sbin/mysqld
[    6.603849] type=1505 audit(1269006256.493:18): operation="profile_replace" pid=1091 name=/usr/sbin/ntpd
[    6.605024] type=1505 audit(1269006256.493:19): operation="profile_replace" pid=1092 name=/usr/sbin/tcpdump
[    7.000023] Clocksource tsc unstable (delta = -90013549 ns)
[    7.952483] type=1503 audit(1269006257.843:20): operation="open" pid=1268 parent=1267 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[    8.255784] i2c-adapter i2c-1: unable to read EDID block.
[    8.255787] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.260197] i2c-adapter i2c-1: unable to read EDID block.
[    8.260198] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.990219] i2c-adapter i2c-1: unable to read EDID block.
[    8.990222] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.994689] i2c-adapter i2c-1: unable to read EDID block.
[    8.994691] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   10.637670] svc: failed to register lockdv1 RPC service (errno 97).
[   10.640260] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   10.640769] NFSD: starting 90-second grace period
[   10.984581] i2c-adapter i2c-1: unable to read EDID block.
[   10.984584] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   10.989046] i2c-adapter i2c-1: unable to read EDID block.
[   10.989048] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   13.346967] CPU0 attaching NULL sched-domain.
[   13.346971] CPU1 attaching NULL sched-domain.
[   13.390074] CPU0 attaching sched-domain:
[   13.390077]  domain 0: span 0-1 level MC
[   13.390079]   groups: 0 1
[   13.390084] CPU1 attaching sched-domain:
[   13.390085]  domain 0: span 0-1 level MC
[   13.390086]   groups: 1 0
[   14.094514] i2c-adapter i2c-1: unable to read EDID block.
[   14.094517] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.098927] i2c-adapter i2c-1: unable to read EDID block.
[   14.098928] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.784509] i2c-adapter i2c-1: unable to read EDID block.
[   14.784511] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.788921] i2c-adapter i2c-1: unable to read EDID block.
[   14.788922] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.281267] eth0: no IPv6 routers present

conor@Myth:~$ lspci -vvvnn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at cc00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fe700000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at c480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at c800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at c880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe6fb000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 [8086:3a40]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 [8086:3a48]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 [8086:3a4a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at c080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at c400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fe6fa000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90) (prog-if 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller [8086:3a20] (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at ac00 [size=8]
	Region 1: I/O ports at a880 [size=4]
	Region 2: I/O ports at a800 [size=8]
	Region 3: I/O ports at a480 [size=4]
	Region 4: I/O ports at a400 [size=16]
	Region 5: I/O ports at a080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 15
	Region 0: Memory at fe6f9000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller [8086:3a26] (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at bc00 [size=8]
	Region 1: I/O ports at b880 [size=4]
	Region 2: I/O ports at b800 [size=8]
	Region 3: I/O ports at b480 [size=4]
	Region 4: I/O ports at b400 [size=16]
	Region 5: I/O ports at b080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82c6]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: I/O ports at d800 [size=256]
	Region 2: Memory at fe8ff000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at fdef0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev c0) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82e0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at ec00 [size=8]
	Region 1: I/O ports at e880 [size=4]
	Region 2: I/O ports at e800 [size=8]
	Region 3: I/O ports at e480 [size=4]
	Region 4: I/O ports at e400 [size=16]
	Region 5: Memory at fe9ffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell

03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720]
	Subsystem: Micronas Semiconductor Holding AG Device [18c3:db01]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Region 1: Memory at feae0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8294]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```

Here's a screenshot of the Capture Cards config:

[IMG]http://img441.imageshack.us/img441/6117/myth.jpg[/IMG]

Any ideas where I should start?

---

### Post by Conar on 2010-03-19
> **managementboy said:**
> have you tried getting it to work with Kaffeine first? or any other TV application for that matter... I would do that first, then start tweaking mythtv.

No I haven't.
Sorry I'm so new to this that I haven't heard of Kaffeine.
I'll start digging on that now.

---

### Post by Conar on 2010-03-19
No immediate luck with Kaffeine.
I installed it, go in to Television->Channels and it doesn't show any source.
Seems I'm right about the drivers not being installed???
I'll try to follow:

Firmware
```
$ wget http://www.digitaldevices.de/download/ngene_15.fw
$ cp ngene_15.fw /lib/firmware/
```
Driver
```
$ hg clone http://linuxtv.org/hg/v4l-dvb/
$ cd v4l-dvb
$ make
$ make install
```

I'll see if it goes better this time.

---

### Post by Conar on 2010-03-19
OK, did that.
There are some errors, are they expected or does it mean it didn't work?
Any ideas?

```
conor@Myth:~$ sudo wget http://www.digitaldevices.de/download/ngene_15.fw
[sudo] password for conor: 
--2010-03-19 14:35:49--  http://www.digitaldevices.de/download/ngene_15.fw
Resolving www.digitaldevices.de... 81.169.145.73
Connecting to www.digitaldevices.de|81.169.145.73|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23466 (23K) [text/plain]
Saving to: `ngene_15.fw'

100%[======================================>] 23,466      43.9K/s   in 0.5s    

2010-03-19 14:35:51 (43.9 KB/s) - `ngene_15.fw' saved [23466/23466]

conor@Myth:~$ sudo cp ngene_15.fw /lib/firmware/
conor@Myth:~$ sudo hg clone http://linuxtv.org/hg/v4l-dvb/
sudo: hg: command not found
conor@Myth:~$ sudo apt-get install mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mercurial-common
Suggested packages:
  qct wish vim emacs kdiff3 tkdiff meld xxdiff python-pygments python-openssl
The following NEW packages will be installed:
  mercurial mercurial-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,130kB of archives.
After this operation, 4,874kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ie.archive.ubuntu.com karmic/universe mercurial-common 1.3.1-1 [1,073kB]
Get:2 http://ie.archive.ubuntu.com karmic/universe mercurial 1.3.1-1 [56.4kB]  
Fetched 1,130kB in 11s (99.7kB/s)                                              
Selecting previously deselected package mercurial-common.
(Reading database ... 115145 files and directories currently installed.)
Unpacking mercurial-common (from .../mercurial-common_1.3.1-1_all.deb) ...
Selecting previously deselected package mercurial.
Unpacking mercurial (from .../mercurial_1.3.1-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mercurial-common (1.3.1-1) ...

Setting up mercurial (1.3.1-1) ...

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version

Processing triggers for python-support ...
conor@Myth:~$ sudo hg clone http://linuxtv.org/hg/v4l-dvb/
destination directory: v4l-dvb
requesting all changes
adding changesets
adding manifests
adding file changes
added 14495 changesets with 35529 changes to 2689 files
updating working directory
1653 files updated, 0 files merged, 0 files removed, 0 files unresolved
conor@Myth:~$ cd v4l-dvb
conor@Myth:~/v4l-dvb$ sudo make
make -C /home/conor/v4l-dvb/v4l 
make[1]: Entering directory `/home/conor/v4l-dvb/v4l'
No version yet, using 2.6.31-20-generic
make[1]: Leaving directory `/home/conor/v4l-dvb/v4l'
make[1]: Entering directory `/home/conor/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.31

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_TVP7002: Requires at least kernel 2.6.34
SOC_CAMERA: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M111: Requires at least kernel 2.6.33
SOC_CAMERA_MT9T031: Requires at least kernel 2.6.33
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.33
SOC_CAMERA_TW9910: Requires at least kernel 2.6.33
SOC_CAMERA_PLATFORM: Requires at least kernel 2.6.33
SOC_CAMERA_OV772X: Requires at least kernel 2.6.33
VIDEO_PXA27x: Requires at least kernel 2.6.32
VIDEO_SH_MOBILE_CEU: Requires at least kernel 2.6.32
VIDEO_TLG2300: Requires at least kernel 2.6.32
RADIO_SAA7706H: Requires at least kernel 2.6.34
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/conor/v4l-dvb/v4l'
make[1]: Entering directory `/home/conor/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-20-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/conor/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/conor/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/conor/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/conor/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-20-generic/build
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/conor/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/conor/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/conor/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/conor/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/conor/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/conor/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/conor/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/conor/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/conor/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/conor/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/conor/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/conor/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/conor/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /home/conor/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-if.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-input.o
  CC [M]  /home/conor/v4l-dvb/v4l/bttv-audio-hook.o
  CC [M]  /home/conor/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /home/conor/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /home/conor/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-alsa-main.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-alsa-pcm.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-driver.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-firmware.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-gpio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-queue.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-streams.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-fileops.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-ioctl.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-controls.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-irq.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-scb.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx18-io.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-audio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-avcore.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx231xx-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-dvb.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-417.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-ioctl.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-ir.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-input.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23888-ir.o
  CC [M]  /home/conor/v4l-dvb/v4l/netup-init.o
  CC [M]  /home/conor/v4l-dvb/v4l/cimax2.o
  CC [M]  /home/conor/v4l-dvb/v4l/netup-eeprom.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx23885-f300.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-dsp.o
  CC [M]  /home/conor/v4l-dvb/v4l/cx88-input.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/conor/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_av.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_ipack.o
  CC [M]  /home/conor/v4l-dvb/v4l/av7110_ir.o
  CC [M]  /home/conor/v4l-dvb/v4l/a800.o
  CC [M]  /home/conor/v4l-dvb/v4l/af9005-remote.o
  CC [M]  /home/conor/v4l-dvb/v4l/af9005.o
  CC [M]  /home/conor/v4l-dvb/v4l/af9005-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/af9015.o
  CC [M]  /home/conor/v4l-dvb/v4l/anysee.o
  CC [M]  /home/conor/v4l-dvb/v4l/au6610.o
  CC [M]  /home/conor/v4l-dvb/v4l/az6027.o
  CC [M]  /home/conor/v4l-dvb/v4l/ce6230.o
  CC [M]  /home/conor/v4l-dvb/v4l/cinergyT2-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/cinergyT2-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/cxusb.o
  CC [M]  /home/conor/v4l-dvb/v4l/dib0700_core.o
  CC [M]  /home/conor/v4l-dvb/v4l/dib0700_devices.o
  CC [M]  /home/conor/v4l-dvb/v4l/dibusb-common.o
  CC [M]  /home/conor/v4l-dvb/v4l/dibusb-mb.o
  CC [M]  /home/conor/v4l-dvb/v4l/dibusb-mc.o
  CC [M]  /home/conor/v4l-dvb/v4l/digitv.o
  CC [M]  /home/conor/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/conor/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/dtv5100.o
  CC [M]  /home/conor/v4l-dvb/v4l/dw2102.o
  CC [M]  /home/conor/v4l-dvb/v4l/ec168.o
  CC [M]  /home/conor/v4l-dvb/v4l/friio.o
  CC [M]  /home/conor/v4l-dvb/v4l/friio-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/gl861.o
  CC [M]  /home/conor/v4l-dvb/v4l/gp8psk.o
  CC [M]  /home/conor/v4l-dvb/v4l/gp8psk-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/m920x.o
  CC [M]  /home/conor/v4l-dvb/v4l/nova-t-usb2.o
  CC [M]  /home/conor/v4l-dvb/v4l/opera1.o
  CC [M]  /home/conor/v4l-dvb/v4l/ttusb2.o
  CC [M]  /home/conor/v4l-dvb/v4l/umt-010.o
  CC [M]  /home/conor/v4l-dvb/v4l/vp702x.o
  CC [M]  /home/conor/v4l-dvb/v4l/vp702x-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/vp7045.o
  CC [M]  /home/conor/v4l-dvb/v4l/vp7045-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-firmware.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-init.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-urb.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /home/conor/v4l-dvb/v4l/dvb-usb-remote.o
  CC [M]  /home/conor/v4l-dvb/v4l/usb-urb.o
  CC [M]  /home/conor/v4l-dvb/v4l/pt1.o
  CC [M]  /home/conor/v4l-dvb/v4l/va1j5jf8007s.o
  CC [M]  /home/conor/v4l-dvb/v4l/va1j5jf8007t.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-audio.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-video.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /home/conor/v4l-dvb/v4l/em28xx-vbi.o
  CC [M]  /home/conor/v4l-dvb/v4l/et61x251_core.o
/home/conor/v4l-dvb/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/conor/v4l-dvb/v4l/et61x251_core.c:2500: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/conor/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/conor/v4l-dvb/v4l/firedtv-avc.o
  CC [M]  /home/conor/v4l-dvb/v4l/firedtv-ci.o
  CC [M]  /home/conor/v4l-dvb/v4l/firedtv-dvb.o
  CC [M]  /home/conor/v4l-dvb/v4l/firedtv-fe.o
  CC [M]  /home/conor/v4l-dvb/v4l/firedtv-1394.o
/home/conor/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/conor/v4l-dvb/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/conor/v4l-dvb/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/conor/v4l-dvb/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:95: error: 'quadlet_t' undeclared (first use in this function)
/home/conor/v4l-dvb/v4l/firedtv-1394.c:95: error: (Each undeclared identifier is reported only once
/home/conor/v4l-dvb/v4l/firedtv-1394.c:95: error: for each function it appears in.)
/home/conor/v4l-dvb/v4l/firedtv-1394.c:95: error: 'd' undeclared (first use in this function)
/home/conor/v4l-dvb/v4l/firedtv-1394.c:96: warning: ISO C90 forbids mixed declarations and code
/home/conor/v4l-dvb/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_lock'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:99: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:107: error: implicit declaration of function 'hpsb_node_read'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:112: error: implicit declaration of function 'hpsb_node_write'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:123: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:123: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:125: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/conor/v4l-dvb/v4l/firedtv-1394.c:127: warning: assignment makes pointer from integer without a cast
/home/conor/v4l-dvb/v4l/firedtv-1394.c:134: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:137: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:148: error: implicit declaration of function 'hpsb_iso_stop'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/conor/v4l-dvb/v4l/firedtv-1394.c:163: warning: 'struct hpsb_host' declared inside parameter list
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:191: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:191: warning: type defaults to 'int' in declaration of '__mptr'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:191: warning: initialization from incompatible pointer type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:191: error: invalid use of undefined type 'struct unit_directory'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:198: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:198: warning: assignment makes pointer from integer without a cast
/home/conor/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/conor/v4l-dvb/v4l/firedtv-1394.c:257: warning: 'struct unit_directory' declared inside parameter list
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:259: error: dereferencing pointer to incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/conor/v4l-dvb/v4l/firedtv-1394.c:267: error: variable 'fdtv_driver' has initializer but incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:268: error: unknown field 'name' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:268: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:268: warning: (near initialization for 'fdtv_driver')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'id_table' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'update' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'driver' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:271: error: extra brace group at end of initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:271: error: (near initialization for 'fdtv_driver')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_driver')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:277: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/conor/v4l-dvb/v4l/firedtv-1394.c:278: error: unknown field 'name' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:278: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:278: warning: (near initialization for 'fdtv_highlevel')
/home/conor/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'fcp_request' specified in initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/conor/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/home/conor/v4l-dvb/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/conor/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/conor/v4l-dvb/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/conor/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/conor/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/conor/v4l-dvb/v4l'
make: *** [all] Error 2
conor@Myth:~/v4l-dvb$ sudo make install
make -C /home/conor/v4l-dvb/v4l install
make[1]: Entering directory `/home/conor/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.31-20-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.31-20-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.31-20-generic/kernel/drivers/media/common:
ir-common.ko 
-e 
Removing obsolete files from /lib/modules/2.6.31-20-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.31-20-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.31-20-generic 
make -C firmware install
make[2]: Entering directory `/home/conor/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/conor/v4l-dvb/v4l/firmware'
make[1]: Leaving directory `/home/conor/v4l-dvb/v4l'

```

---

### Post by Conar on 2010-03-19
Latest dmesg

```
conor@Myth:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa053a0c-14f7-49c9-acc0-78014af96b07 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7d80000 (usable)
[    0.000000]  BIOS-e820: 00000000c7d80000 - 00000000c7d8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7d8e000 - 00000000c7dd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7dd0000 - 00000000c7e00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 0C7E00000 mask FFFE00000 uncachable
[    0.000000]   6 base 0C8000000 mask FF8000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c7e00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7d80 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000c7d80000 (usable)
[    0.000000]  modified: 00000000c7d80000 - 00000000c7d8e000 (ACPI data)
[    0.000000]  modified: 00000000c7d8e000 - 00000000c7dd0000 (ACPI NVS)
[    0.000000]  modified: 00000000c7dd0000 - 00000000c7e00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7d80000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c7c00000 page 2M
[    0.000000]  00c7c00000 - 00c7d80000 page 4k
[    0.000000] kernel direct mapping tables up to c7d80000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] RAMDISK: 3786d000 - 37fefa9d
[    0.000000] ACPI: RSDP 00000000000fb900 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000c7d80100 00064 (v01 A_M_I_ OEMXSDT  07000908 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000c7d80290 000F4 (v03 A_M_I_ OEMFACP  07000908 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000c7d80440 090EB (v01  A0982 A0982070 00000070 INTL 20060113)
[    0.000000] ACPI: FACS 00000000c7d8e000 00040
[    0.000000] ACPI: APIC 00000000c7d80390 0006C (v01 A_M_I_ OEMAPIC  07000908 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000c7d80400 0003C (v01 A_M_I_ OEMMCFG  07000908 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000c7d8e040 00089 (v01 A_M_I_ AMI_OEM  07000908 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000c7d89530 00038 (v01 A_M_I_ OEMHPET  07000908 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000c7d8e0d0 02024 (v01 A_M_I_ GMCHSCI  07000908 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000c7d89570 000B0 (v01 A_M_I_ OEMOSFR  07000908 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c7d90b50 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
[    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]
[    0.000000]   #3 [003786d000 - 0037fefa9d]          RAMDISK ==> [003786d000 - 0037fefa9d]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e9000 - 00019e9294]              BRK ==> [00019e9000 - 00019e9294]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c7d80
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1015055
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3823 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 800184 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
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
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c7d80000 - 00000000c7d8e000
[    0.000000] PM: Registered nosave memory: 00000000c7d8e000 - 00000000c7dd0000
[    0.000000] PM: Registered nosave memory: 00000000c7dd0000 - 00000000c7e00000
[    0.000000] PM: Registered nosave memory: 00000000c7e00000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c7e00000 (gap: c7e00000:37000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 997927
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=aa053a0c-14f7-49c9-acc0-78014af96b07 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 3918360k/4980736k available (5327k kernel code, 920516k absent, 141860k reserved, 3014k data, 664k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3000.025 MHz processor.
[    0.001012] Console: colour VGA+ 80x25
[    0.001015] console [tty0] enabled
[    0.010000] allocated 40632320 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6000.05 BogoMIPS (lpj=30000250)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.020051] Setting APIC routing to flat
[    0.020349] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.128377] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 5999.33 BogoMIPS (lpj=29996670)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 6144K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.281626] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 06
[    0.281633] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290019] Brought up 2 CPUs
[    0.290021] Total of 2 processors activated (11999.38 BogoMIPS).
[    0.290067] CPU0 attaching sched-domain:
[    0.290070]  domain 0: span 0-1 level MC
[    0.290072]   groups: 0 1
[    0.290075] CPU1 attaching sched-domain:
[    0.290077]  domain 0: span 0-1 level MC
[    0.290078]   groups: 1 0
[    0.290135] Booting paravirtualized kernel on bare hardware
[    0.290135] regulator: core version 0.5
[    0.290135] Time: 13:44:10  Date: 03/19/10
[    0.290135] NET: Registered protocol family 16
[    0.290159] ACPI: bus type pci registered
[    0.290212] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.290213] PCI: Not using MMCONFIG.
[    0.290215] PCI: Using configuration type 1 for base access
[    0.290776] bio: create slab <bio-0> at 0
[    0.290776] ACPI: EC: Look up EC in DSDT
[    0.303876] ACPI: Interpreter enabled
[    0.303879] ACPI: (supports S0 S1 S3 S4 S5)
[    0.303895] ACPI: Using IOAPIC for interrupt routing
[    0.303936] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.305967] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.310819] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.316439] ACPI Warning: Incorrect checksum in table [OEMB] - 0C, should be 0B 20090521 tbutils-246
[    0.317231] ACPI: No dock devices found.
[    0.317350] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.317411] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe000000-0xfe3fffff]
[    0.317415] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.317418] pci 0000:00:02.0: reg 20 io port: [0xcc00-0xcc07]
[    0.317443] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe700000-0xfe7fffff]
[    0.317513] pci 0000:00:1a.0: reg 20 io port: [0xc480-0xc49f]
[    0.317567] pci 0000:00:1a.1: reg 20 io port: [0xc800-0xc81f]
[    0.317620] pci 0000:00:1a.2: reg 20 io port: [0xc880-0xc89f]
[    0.317677] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe6fb000-0xfe6fb3ff]
[    0.317721] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.317725] pci 0000:00:1a.7: PME# disabled
[    0.317755] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe6f4000-0xfe6f7fff]
[    0.317787] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.317790] pci 0000:00:1b.0: PME# disabled
[    0.317834] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.317836] pci 0000:00:1c.0: PME# disabled
[    0.317881] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.317884] pci 0000:00:1c.1: PME# disabled
[    0.317930] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.317932] pci 0000:00:1c.4: PME# disabled
[    0.317977] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.317980] pci 0000:00:1c.5: PME# disabled
[    0.318021] pci 0000:00:1d.0: reg 20 io port: [0xc000-0xc01f]
[    0.318076] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.318129] pci 0000:00:1d.2: reg 20 io port: [0xc400-0xc41f]
[    0.318186] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe6fa000-0xfe6fa3ff]
[    0.318230] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.318233] pci 0000:00:1d.7: PME# disabled
[    0.318328] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.318331] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.318333] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.318376] pci 0000:00:1f.2: reg 10 io port: [0xac00-0xac07]
[    0.318380] pci 0000:00:1f.2: reg 14 io port: [0xa880-0xa883]
[    0.318384] pci 0000:00:1f.2: reg 18 io port: [0xa800-0xa807]
[    0.318389] pci 0000:00:1f.2: reg 1c io port: [0xa480-0xa483]
[    0.318393] pci 0000:00:1f.2: reg 20 io port: [0xa400-0xa40f]
[    0.318397] pci 0000:00:1f.2: reg 24 io port: [0xa080-0xa08f]
[    0.318433] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe6f9000-0xfe6f90ff]
[    0.318443] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.318476] pci 0000:00:1f.5: reg 10 io port: [0xbc00-0xbc07]
[    0.318480] pci 0000:00:1f.5: reg 14 io port: [0xb880-0xb883]
[    0.318484] pci 0000:00:1f.5: reg 18 io port: [0xb800-0xb807]
[    0.318488] pci 0000:00:1f.5: reg 1c io port: [0xb480-0xb483]
[    0.318492] pci 0000:00:1f.5: reg 20 io port: [0xb400-0xb40f]
[    0.318496] pci 0000:00:1f.5: reg 24 io port: [0xb080-0xb08f]
[    0.318554] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.318600] pci 0000:03:00.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.318614] pci 0000:03:00.0: reg 14 64bit mmio: [0xfeae0000-0xfeaeffff]
[    0.318718] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.318758] pci 0000:02:00.0: reg 10 io port: [0xec00-0xec07]
[    0.318765] pci 0000:02:00.0: reg 14 io port: [0xe880-0xe883]
[    0.318771] pci 0000:02:00.0: reg 18 io port: [0xe800-0xe807]
[    0.318778] pci 0000:02:00.0: reg 1c io port: [0xe480-0xe483]
[    0.318784] pci 0000:02:00.0: reg 20 io port: [0xe400-0xe40f]
[    0.318791] pci 0000:02:00.0: reg 24 32bit mmio: [0xfe9ffc00-0xfe9ffdff]
[    0.318825] pci 0000:02:00.0: supports D1
[    0.318826] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.318830] pci 0000:02:00.0: PME# disabled
[    0.318868] pci 0000:00:1c.4: bridge io port: [0xe000-0xefff]
[    0.318871] pci 0000:00:1c.4: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.318912] pci 0000:01:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.318929] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe8ff000-0xfe8fffff]
[    0.318940] pci 0000:01:00.0: reg 20 64bit mmio: [0xfdef0000-0xfdefffff]
[    0.318947] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe8c0000-0xfe8dffff]
[    0.318981] pci 0000:01:00.0: supports D1 D2
[    0.318982] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.318986] pci 0000:01:00.0: PME# disabled
[    0.319032] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
[    0.319035] pci 0000:00:1c.5: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.319040] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.319069] pci 0000:05:03.0: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.319106] pci 0000:05:03.0: supports D1 D2
[    0.319107] pci 0000:05:03.0: PME# supported from D0 D1 D2 D3hot
[    0.319111] pci 0000:05:03.0: PME# disabled
[    0.319146] pci 0000:00:1e.0: transparent bridge
[    0.319150] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.319171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.319270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.319327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.319367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.319411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.319449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.333059] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.333147] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.333232] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.333318] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.333407] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.333492] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.333577] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.333662] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.333775] SCSI subsystem initialized
[    0.333787] libata version 3.00 loaded.
[    0.333787] usbcore: registered new interface driver usbfs
[    0.333787] usbcore: registered new interface driver hub
[    0.333787] usbcore: registered new device driver usb
[    0.333787] ACPI: WMI: Mapper loaded
[    0.333787] PCI: Using ACPI for IRQ routing
[    0.360008] Bluetooth: Core ver 2.15
[    0.360022] NET: Registered protocol family 31
[    0.360022] Bluetooth: HCI device and connection manager initialized
[    0.360022] Bluetooth: HCI socket layer initialized
[    0.360022] NetLabel: Initializing
[    0.360022] NetLabel:  domain hash size = 128
[    0.360022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360032] NetLabel:  unlabeled traffic allowed by default
[    0.360076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.360081] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.400005] pnp: PnP ACPI init
[    0.400013] ACPI: bus type pnp registered
[    0.402304] pnp: PnP ACPI: found 15 devices
[    0.402305] ACPI: ACPI bus type pnp unregistered
[    0.402312] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.402316] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.402320] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.402322] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.402324] system 00:07: ioport range 0x500-0x57f could not be reserved
[    0.402326] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.402328] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.402330] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.402332] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.402336] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
[    0.402340] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.402342] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.402345] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.402349] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.402351] system 00:0e: iomem range 0xc0000-0xcffff has been reserved
[    0.402352] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.402354] system 00:0e: iomem range 0x100000-0xc7dfffff could not be reserved
[    0.402356] system 00:0e: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.406967] AppArmor: AppArmor Filesystem Enabled
[    0.407004] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.407005] pci 0000:00:1c.0:   IO window: disabled
[    0.407009] pci 0000:00:1c.0:   MEM window: disabled
[    0.407012] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.407016] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.407017] pci 0000:00:1c.1:   IO window: disabled
[    0.407021] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.407024] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.407027] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:02
[    0.407029] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.407032] pci 0000:00:1c.4:   MEM window: 0xfe900000-0xfe9fffff
[    0.407035] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.407038] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:01
[    0.407040] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.407043] pci 0000:00:1c.5:   MEM window: 0xfe800000-0xfe8fffff
[    0.407046] pci 0000:00:1c.5:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.407051] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.407052] pci 0000:00:1e.0:   IO window: disabled
[    0.407055] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.407058] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.407065]   alloc irq_desc for 17 on node 0
[    0.407066]   alloc kstat_irqs on node 0
[    0.407070] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.407073] pci 0000:00:1c.0: setting latency timer to 64
[    0.407077]   alloc irq_desc for 16 on node 0
[    0.407079]   alloc kstat_irqs on node 0
[    0.407084] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.407087] pci 0000:00:1c.1: setting latency timer to 64
[    0.407092] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.407094] pci 0000:00:1c.4: setting latency timer to 64
[    0.407099] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.407102] pci 0000:00:1c.5: setting latency timer to 64
[    0.407106] pci 0000:00:1e.0: setting latency timer to 64
[    0.407109] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.407111] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.407113] pci_bus 0000:04: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.407114] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.407116] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.407117] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.407119] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.407120] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.407122] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.407123] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.407125] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.407126] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.407146] NET: Registered protocol family 2
[    0.407254] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.407993] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.410738] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.411141] TCP: Hash tables configured (established 524288 bind 65536)
[    0.411143] TCP reno registered
[    0.411246] NET: Registered protocol family 1
[    0.411296] Trying to unpack rootfs image as initramfs...
[    0.501648] Switched to high resolution mode on CPU 1
[    0.509988] Switched to high resolution mode on CPU 0
[    0.534114] Freeing initrd memory: 7690k freed
[    0.536350] Scanning for low memory corruption every 60 seconds
[    0.536460] audit: initializing netlink socket (disabled)
[    0.536474] type=2000 audit(1269006249.530:1): initialized
[    0.543051] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.543988] VFS: Disk quotas dquot_6.5.2
[    0.544027] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.544417] fuse init (API version 7.12)
[    0.544470] msgmni has been set to 7668
[    0.544619] alg: No test for stdrng (krng)
[    0.544628] io scheduler noop registered
[    0.544630] io scheduler anticipatory registered
[    0.544631] io scheduler deadline registered
[    0.544655] io scheduler cfq registered (default)
[    0.544665] pci 0000:00:02.0: Boot video device
[    0.544885]   alloc irq_desc for 24 on node 0
[    0.544886]   alloc kstat_irqs on node 0
[    0.544896] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.544902] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.545001]   alloc irq_desc for 25 on node 0
[    0.545002]   alloc kstat_irqs on node 0
[    0.545007] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.545013] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.545110]   alloc irq_desc for 26 on node 0
[    0.545112]   alloc kstat_irqs on node 0
[    0.545117] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.545122] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.545220]   alloc irq_desc for 27 on node 0
[    0.545221]   alloc kstat_irqs on node 0
[    0.545226] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.545231] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.545300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.545391] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.545481] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.545484] ACPI: Power Button [PWRF]
[    0.545525] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.545526] ACPI: Power Button [PWRB]
[    0.546071] ACPI: SSDT 00000000c7d90100 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.546430] ACPI: SSDT 00000000c7d90600 004B2 (v01  PmRef  P001Cst 00003001 INTL 20060113)
[    0.546855] Monitor-Mwait will be used to enter C-1 state
[    0.546871] Monitor-Mwait will be used to enter C-2 state
[    0.546887] Monitor-Mwait will be used to enter C-3 state
[    0.546892] Marking TSC unstable due to TSC halts in idle
[    0.546906] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.546922] processor LNXCPU:00: registered as cooling_device0
[    0.547246] ACPI: SSDT 00000000c7d90380 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.547498] ACPI: SSDT 00000000c7d90ac0 00085 (v01  PmRef  P002Cst 00003000 INTL 20060113)
[    0.547979] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.547991] processor LNXCPU:01: registered as cooling_device1
[    0.550451] Linux agpgart interface v0.103
[    0.550457] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.550540] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.550786] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.551436] brd: module loaded
[    0.551732] loop: module loaded
[    0.551776] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.551895] ata_piix 0000:00:1f.2: version 2.13
[    0.551904]   alloc irq_desc for 19 on node 0
[    0.551905]   alloc kstat_irqs on node 0
[    0.551909] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.551912] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.551942] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.551986] scsi0 : ata_piix
[    0.552039] scsi1 : ata_piix
[    0.553145] ata1: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 19
[    0.553149] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 19
[    0.553183] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.553187] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.553214] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.553243] scsi2 : ata_piix
[    0.553280] scsi3 : ata_piix
[    0.554205] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 19
[    0.554208] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 19
[    0.554472] pata_marvell 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.554489] pata_marvell 0000:02:00.0: setting latency timer to 64
[    0.554523] scsi4 : pata_marvell
[    0.554557] scsi5 : pata_marvell
[    0.554580] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    0.554581] ata6: DUMMY
[    0.554881] Fixed MDIO Bus: probed
[    0.554905] PPP generic driver version 2.4.2
[    0.554959] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.554986]   alloc irq_desc for 18 on node 0
[    0.554987]   alloc kstat_irqs on node 0
[    0.554990] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.555000] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.555002] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.555022] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.558929] ehci_hcd 0000:00:1a.7: debug port 1
[    0.558934] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.558942] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe6fb000
[    0.580027] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.580118] usb usb1: configuration #1 chosen from 1 choice
[    0.580147] hub 1-0:1.0: USB hub found
[    0.580154] hub 1-0:1.0: 6 ports detected
[    0.580310]   alloc irq_desc for 23 on node 0
[    0.580311]   alloc kstat_irqs on node 0
[    0.580314] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580320] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.580323] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.580341] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.584229] ehci_hcd 0000:00:1d.7: debug port 1
[    0.584233] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.584241] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe6fa000
[    0.600010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.600064] usb usb2: configuration #1 chosen from 1 choice
[    0.600088] hub 2-0:1.0: USB hub found
[    0.600093] hub 2-0:1.0: 6 ports detected
[    0.600151] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.600166] uhci_hcd: USB Universal Host Controller Interface driver
[    0.600226] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.600230] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.600232] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.600250] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.600268] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c480
[    0.600317] usb usb3: configuration #1 chosen from 1 choice
[    0.600333] hub 3-0:1.0: USB hub found
[    0.600337] hub 3-0:1.0: 2 ports detected
[    0.600384]   alloc irq_desc for 21 on node 0
[    0.600385]   alloc kstat_irqs on node 0
[    0.600388] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.600392] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.600394] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.600412] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.600436] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.600484] usb usb4: configuration #1 chosen from 1 choice
[    0.600500] hub 4-0:1.0: USB hub found
[    0.600504] hub 4-0:1.0: 2 ports detected
[    0.600552] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.600555] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.600558] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.600576] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.600594] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000c880
[    0.600641] usb usb5: configuration #1 chosen from 1 choice
[    0.600658] hub 5-0:1.0: USB hub found
[    0.600663] hub 5-0:1.0: 2 ports detected
[    0.600706] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.600710] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.600712] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.600731] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.600749] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c000
[    0.600795] usb usb6: configuration #1 chosen from 1 choice
[    0.600812] hub 6-0:1.0: USB hub found
[    0.600816] hub 6-0:1.0: 2 ports detected
[    0.600859] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.600864] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.600867] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.600890] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.600908] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.600957] usb usb7: configuration #1 chosen from 1 choice
[    0.600973] hub 7-0:1.0: USB hub found
[    0.600977] hub 7-0:1.0: 2 ports detected
[    0.601024] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.601028] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.601030] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.601049] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.601067] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c400
[    0.601115] usb usb8: configuration #1 chosen from 1 choice
[    0.601130] hub 8-0:1.0: USB hub found
[    0.601134] hub 8-0:1.0: 2 ports detected
[    0.601201] PNP: No PS/2 controller found. Probing ports directly.
[    0.603863] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.603867] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.603906] mice: PS/2 mouse device common for all mice
[    0.603961] rtc_cmos 00:03: RTC can wake from S4
[    0.603984] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.604003] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.604080] device-mapper: uevent: version 1.0.3
[    0.604149] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.604195] device-mapper: multipath: version 1.1.0 loaded
[    0.604197] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.604354] cpuidle: using governor ladder
[    0.604426] cpuidle: using governor menu
[    0.604686] TCP cubic registered
[    0.604767] NET: Registered protocol family 10
[    0.605056] lo: Disabled Privacy Extensions
[    0.605247] NET: Registered protocol family 17
[    0.605259] Bluetooth: L2CAP ver 2.13
[    0.605260] Bluetooth: L2CAP socket layer initialized
[    0.605263] Bluetooth: SCO (Voice Link) ver 0.6
[    0.605264] Bluetooth: SCO socket layer initialized
[    0.605284] Bluetooth: RFCOMM TTY layer initialized
[    0.605287] Bluetooth: RFCOMM socket layer initialized
[    0.605288] Bluetooth: RFCOMM ver 1.11
[    0.605910] PM: Resume from disk failed.
[    0.605918] registered taskstats version 1
[    0.606008]   Magic number: 2:471:736
[    0.606067] rtc_cmos 00:03: setting system clock to 2010-03-19 13:44:10 UTC (1269006250)
[    0.606069] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.606070] EDD information not available.
[    0.910707] ata3: SATA link down (SStatus 0 SControl 300)
[    1.060066] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.080213] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-H62N, CL01, max UDMA/100
[    1.120230] ata4.00: configured for UDMA/100
[    1.181274] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.363672] usb 5-1: configuration #1 chosen from 1 choice
[    1.410075] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.410085] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.421319] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.421331] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.431703] ata1.00: ATA-8: OCZ CORE_SSD, 02.10103, max UDMA/100
[    1.431705] ata1.00: 118128640 sectors, multi 0: LBA 
[    1.450985] ata2.00: ATA-7: WDC WD1500ADFD-00NLR3, 21.07QR3, max UDMA/133
[    1.450988] ata2.00: 293046768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.451130] ata2.01: ATA-7: SAMSUNG HD753LJ, 1AA01113, max UDMA7
[    1.451133] ata2.01: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.470332] ata1.00: configured for UDMA/100
[    1.470406] scsi 0:0:0:0: Direct-Access     ATA      OCZ CORE_SSD     02.1 PQ: 0 ANSI: 5
[    1.470475] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.470499] sd 0:0:0:0: [sda] 118128640 512-byte logical blocks: (60.4 GB/56.3 GiB)
[    1.470528] sd 0:0:0:0: [sda] Write Protect is off
[    1.470530] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.470546] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.470628]  sda:
[    1.490880] ata2.00: configured for UDMA/133
[    1.510310] ata2.01: configured for UDMA/133
[    1.510369] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[    1.510463] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.510524] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    1.510609] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    1.510643] sd 1:0:0:0: [sdb] 293046768 512-byte logical blocks: (150 GB/139 GiB)
[    1.510671] sd 1:0:0:0: [sdb] Write Protect is off
[    1.510673] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.510688] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.510756]  sdb:
[    1.515206] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H62N  CL01 PQ: 0 ANSI: 5
[    1.525992]  sdb1 sdb2 <
[    1.526007] sd 1:0:1:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.535429]  sdb5 >
[    1.535468] sd 1:0:1:0: [sdc] Write Protect is off
[    1.535471] sd 1:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    1.535493] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.535632]  sdc: sdc1
[    1.546334] sd 1:0:1:0: [sdc] Attached SCSI disk
[    1.546344] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.660026] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    1.846987] usb 7-1: configuration #1 chosen from 1 choice
[    1.849159] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.849161] Uniform CD-ROM driver Revision: 3.20
[    1.849203] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.849228] sr 3:0:0:0: Attached scsi generic sg3 type 5
[    2.278833]  sda1
[    2.279004] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.279024] Freeing unused kernel memory: 664k freed
[    2.279170] Write protecting the kernel read-only data: 7596k
[    2.338116] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
[    2.339436] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[    2.341462] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.352290] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.352313] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.352361] r8169 0000:01:00.0: setting latency timer to 64
[    2.352401]   alloc irq_desc for 28 on node 0
[    2.352403]   alloc kstat_irqs on node 0
[    2.352416] r8169 0000:01:00.0: irq 28 for MSI/MSI-X
[    2.352834] eth0: RTL8168c/8111c at 0xffffc90000676000, 90:e6:ba:85:15:f1, XID 3c4000c0 IRQ 28
[    2.397644] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.397757] usbcore: registered new interface driver hiddev
[    2.412921] input: Microsoft Microsoft(R) Compact Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3
[    2.412981] generic-usb 0003:045E:00A4.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft(R) Compact Optical Mouse] on usb-0000:00:1a.2-1/input0
[    2.425155] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4
[    2.425188] generic-usb 0003:046E:5577.0002: input,hidraw1: USB HID v1.11 Keyboard [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:1d.1-1/input0
[    2.452013] [drm] Initialized drm 1.1.0 20060810
[    2.452051] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    2.459093] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.459103] i915 0000:00:02.0: setting latency timer to 64
[    2.468160] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    2.468162] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    2.468752] input: BTC USB Multimedia Cordless Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input5
[    2.468833] generic-usb 0003:046E:5577.0003: input,hiddev96,hidraw2: USB HID v1.11 Mouse [BTC USB Multimedia Cordless Keyboard] on usb-0000:00:1d.1-1/input1
[    2.468848] usbcore: registered new interface driver usbhid
[    2.468849] usbhid: v2.6:USB HID core driver
[    2.469317]   alloc irq_desc for 29 on node 0
[    2.469320]   alloc kstat_irqs on node 0
[    2.469328] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    2.474324] [drm] i2c_init DPDDC-B
[    2.484998] [drm] i2c_init DPDDC-C
[    2.537414] i2c-adapter i2c-1: unable to read EDID block.
[    2.537490] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    3.147226] [drm] fb0: inteldrmfb frame buffer device
[    3.147278] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.212716] [drm] TMDS-12: set mode 1920x1080 1f
[    3.236718] Console: switching to colour frame buffer device 240x67
[    3.443945] PM: Starting manual resume from disk
[    3.443948] PM: Resume from partition 8:21
[    3.443949] PM: Checking hibernation image.
[    3.444080] PM: Resume from disk failed.
[    3.446993] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.446996] EXT4-fs (sda1): write access will be enabled during recovery
[    3.447548] EXT4-fs (sda1): barriers enabled
[    3.791452] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000b83c84]
[    5.053577] kjournald2 starting: pid 466, dev sda1:8, commit interval 5 seconds
[    5.053657] EXT4-fs (sda1): delayed allocation enabled
[    5.053661] EXT4-fs: file extents enabled
[    5.056133] EXT4-fs: mballoc enabled
[    5.056143] EXT4-fs (sda1): orphan cleanup on readonly fs
[    5.056149] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1305
[    5.056214] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 600
[    5.056225] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 593
[    5.056237] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 571
[    5.056248] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 567
[    5.056259] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 563
[    5.056269] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 561
[    5.056281] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 512
[    5.056307] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 490
[    5.056318] EXT4-fs (sda1): 9 orphan inodes deleted
[    5.056320] EXT4-fs (sda1): recovery complete
[    5.077516] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.189383] type=1505 audit(1269006255.073:2): operation="profile_load" pid=491 name=/sbin/dhclient3
[    5.189939] type=1505 audit(1269006255.073:3): operation="profile_load" pid=491 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.190214] type=1505 audit(1269006255.083:4): operation="profile_load" pid=491 name=/usr/lib/connman/scripts/dhclient-script
[    5.200201] type=1505 audit(1269006255.093:5): operation="profile_load" pid=492 name=/usr/bin/evince
[    5.207758] type=1505 audit(1269006255.093:6): operation="profile_load" pid=492 name=/usr/bin/evince-previewer
[    5.212231] type=1505 audit(1269006255.103:7): operation="profile_load" pid=492 name=/usr/bin/evince-thumbnailer
[    5.218700] type=1505 audit(1269006255.103:8): operation="profile_load" pid=494 name=/usr/sbin/mysqld
[    5.220291] type=1505 audit(1269006255.113:9): operation="profile_load" pid=495 name=/usr/sbin/ntpd
[    5.221626] type=1505 audit(1269006255.113:10): operation="profile_load" pid=496 name=/usr/sbin/tcpdump
[    5.363585] Adding 2610520k swap on /dev/sdb5.  Priority:-1 extents:1 across:2610520k 
[    5.395077] EXT4-fs (sda1): internal journal on sda1:8
[    5.409927] udev: starting version 147
[    5.556368] RPC: Registered udp transport module.
[    5.556370] RPC: Registered tcp transport module.
[    5.613480] lp: driver loaded but no devices found
[    5.749046] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    5.825480]   alloc irq_desc for 22 on node 0
[    5.825482]   alloc kstat_irqs on node 0
[    5.825487] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.825533] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.837290] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.959834] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[    6.545901] r8169: eth0: link up
[    6.545903] r8169: eth0: link up
[    6.581169] type=1505 audit(1269006256.473:11): operation="profile_replace" pid=1087 name=/sbin/dhclient3
[    6.581656] type=1505 audit(1269006256.473:12): operation="profile_replace" pid=1087 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.581917] type=1505 audit(1269006256.473:13): operation="profile_replace" pid=1087 name=/usr/lib/connman/scripts/dhclient-script
[    6.584320] type=1505 audit(1269006256.473:14): operation="profile_replace" pid=1088 name=/usr/bin/evince
[    6.592206] type=1505 audit(1269006256.483:15): operation="profile_replace" pid=1088 name=/usr/bin/evince-previewer
[    6.596670] type=1505 audit(1269006256.483:16): operation="profile_replace" pid=1088 name=/usr/bin/evince-thumbnailer
[    6.602676] type=1505 audit(1269006256.493:17): operation="profile_replace" pid=1090 name=/usr/sbin/mysqld
[    6.603849] type=1505 audit(1269006256.493:18): operation="profile_replace" pid=1091 name=/usr/sbin/ntpd
[    6.605024] type=1505 audit(1269006256.493:19): operation="profile_replace" pid=1092 name=/usr/sbin/tcpdump
[    7.000023] Clocksource tsc unstable (delta = -90013549 ns)
[    7.952483] type=1503 audit(1269006257.843:20): operation="open" pid=1268 parent=1267 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[    8.255784] i2c-adapter i2c-1: unable to read EDID block.
[    8.255787] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.260197] i2c-adapter i2c-1: unable to read EDID block.
[    8.260198] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.990219] i2c-adapter i2c-1: unable to read EDID block.
[    8.990222] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    8.994689] i2c-adapter i2c-1: unable to read EDID block.
[    8.994691] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   10.637670] svc: failed to register lockdv1 RPC service (errno 97).
[   10.640260] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   10.640769] NFSD: starting 90-second grace period
[   10.984581] i2c-adapter i2c-1: unable to read EDID block.
[   10.984584] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   10.989046] i2c-adapter i2c-1: unable to read EDID block.
[   10.989048] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   13.346967] CPU0 attaching NULL sched-domain.
[   13.346971] CPU1 attaching NULL sched-domain.
[   13.390074] CPU0 attaching sched-domain:
[   13.390077]  domain 0: span 0-1 level MC
[   13.390079]   groups: 0 1
[   13.390084] CPU1 attaching sched-domain:
[   13.390085]  domain 0: span 0-1 level MC
[   13.390086]   groups: 1 0
[   14.094514] i2c-adapter i2c-1: unable to read EDID block.
[   14.094517] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.098927] i2c-adapter i2c-1: unable to read EDID block.
[   14.098928] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.784509] i2c-adapter i2c-1: unable to read EDID block.
[   14.784511] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   14.788921] i2c-adapter i2c-1: unable to read EDID block.
[   14.788922] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   17.281267] eth0: no IPv6 routers present

```

and latest lspci
```
conor@Myth:~$ lspci -vvvnn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d3]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at cc00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8276]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fe700000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at c480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at c800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at c880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe6fb000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82fe]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fe6f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 [8086:3a40]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5 [8086:3a48]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 [8086:3a4a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at c080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at c400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fe6fa000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90) (prog-if 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller [8086:3a20] (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at ac00 [size=8]
	Region 1: I/O ports at a880 [size=4]
	Region 2: I/O ports at a800 [size=8]
	Region 3: I/O ports at a480 [size=4]
	Region 4: I/O ports at a400 [size=16]
	Region 5: I/O ports at a080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 15
	Region 0: Memory at fe6f9000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller [8086:3a26] (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at bc00 [size=8]
	Region 1: I/O ports at b880 [size=4]
	Region 2: I/O ports at b800 [size=8]
	Region 3: I/O ports at b480 [size=4]
	Region 4: I/O ports at b400 [size=16]
	Region 5: I/O ports at b080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82c6]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: I/O ports at d800 [size=256]
	Region 2: Memory at fe8ff000 (64-bit, non-prefetchable) [size=4K]
	Region 4: Memory at fdef0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev c0) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82e0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at ec00 [size=8]
	Region 1: I/O ports at e880 [size=4]
	Region 2: I/O ports at e800 [size=8]
	Region 3: I/O ports at e480 [size=4]
	Region 4: I/O ports at e400 [size=16]
	Region 5: Memory at fe9ffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell

03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720]
	Subsystem: Micronas Semiconductor Holding AG Device [18c3:db01]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
	Region 1: Memory at feae0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:03.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8294]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 6000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```

Still nothing in Kaffeine or MythTV Setup.
Can anyone assist getting the card installed?

---

### Post by foersterben on 2010-03-19
Hi,
do the following:
```

$ cd /usr/src/
$ hg clone http://linuxtv.org/hg/v4l-dvb/
$ cd v4l-dvb
$ make menuconfig
	Multimedia Support --->
		DVB/ATSC adapters  --->
			[ ] FireDTV and FloppyDTV		# please remove, due to compile error
$ make
$ make install

```
Important: Remove option FireDTV in menuconfig.

Don't forget to
```

$ sudo echo "ngene"  >> /etc/modules
$ sudo reboot                              

```

greetings,
ben

---

### Post by Conar on 2010-03-19
> **foersterben said:**
> Hi,
do the following:
```

$ cd /usr/src/
$ hg clone http://linuxtv.org/hg/v4l-dvb/
$ cd v4l-dvb
$ make menuconfig
	Multimedia Support --->
		DVB/ATSC adapters  --->
			[ ] FireDTV and FloppyDTV		# please remove, due to compile error
$ make
$ make install

```
Important: Remove option FireDTV in menuconfig.

Don't forget to
```

$ sudo echo "ngene"  >> /etc/modules
$ sudo reboot                              

```

greetings,
ben

Cheers Ben.
That seems to have done the trick.
The card is now picked up in MythTV.
I just need to figure out how to set that up now.
I'll probably be back but I'll try to figure it out on my own if I can.

BTW the only part that didn't work was:
```
conor@Myth:/usr/src/v4l-dvb$ sudo echo "ngene"  >> /etc/modules
bash: /etc/modules: Permission denied
```
What was that for? Does it matter that it didn't work?

---

### Post by foersterben on 2010-03-19
Hi Conar,

```
$ sudo echo "ngene"  >> /etc/modules
```This is to insert ngene into the modules file to load ngene at boot time.

You can edit /etc/modules **as root** with your favorite editor like vi, vim or nano like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ngene

```Try
```

lsmod | grep ngene

```
Only if the ngene module is loaded you will b e able to setup the card.

greetings,
ben

---

### Post by Conar on 2010-03-19
> **foersterben said:**
> Hi Conar,

```
$ sudo echo "ngene"  >> /etc/modules
```This is to insert ngene into the modules file to load ngene at boot time.

You can edit /etc/modules **as root** with your favorite editor like vi, vim or nano like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ngene

```Try
```

lsmod | grep ngene

```
Only if the ngene module is loaded you will b e able to setup the card.

greetings,
ben

Did that. Cheers Ben!

Rebooted and will see if I can scan etc now.

---

### Post by Conar on 2010-03-19
Hmmmm, still can't scan.
Followed the guide [here ]("http://parker1.co.uk/mythtv_freesat.php") and did a channel scan but got the following for every freq:
[HTML]DVB-S IF freq is 1802000
WARNING: >>> tuning failed!!!
>>> tune to: 12402:v:0:27500 (tuning failed)
DVB-S IF freq is 1802000
WARNING: >>> tuning failed!!!
>>> tune to: 12441:v:0:27500
DVB-S IF freq is 1841000
WARNING: >>> tuning failed!!!
>>> tune to: 12441:v:0:27500 (tuning failed)
DVB-S IF freq is 1841000[/HTML]

Any ideas?
Thanks a million for your help by the way.
I'm making progress at least thanks to you.

---

### Post by Conar on 2010-03-19
Think I got it.
Its picking up channels when I run ```
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
```
It was a brain fart moment, I have only 1 feed into my dual tuner at the moment so it was looking to the wrong input. Changed it to the other input and its finding channels now.
Looks like I'm on the final stretch.

---

### Post by Conar on 2010-03-19
[IMG]http://img689.imageshack.us/img689/4167/mythc.jpg[/IMG]

---

### Post by RockDr on 2010-09-22
Hi!
I'm also relatively new to Linux, but am gradually picking up pace.
I have a Terratec Cinergy 2400iDT card. Reading [here]("http://www.linuxtv.org/wiki/index.php/NGene_devices") and [here]("http://www.linuxtv.org/wiki/index.php/Media-Pointer_MP-S2%C2%B2") and [here]("http://www.linuxtv.org/wiki/index.php/Mystique_SaTiX-S2_Dual#Making_it_Work"), they are essentially the same card, and therefore the steps described in this post should work.
Unfortunately, after following the instructions above step by step, the card is not seen by TVHeadend.
I also have a Hauppauge WinTV-HVR1200 card inserted, and this works fine. I was hoping however to make use of the dual tuner capability of the Terratec.
My dmesg is as follows:
```
[    2.146864] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.146867] pci 0000:00:01.0: setting latency timer to 64
[    2.146872] pci 0000:00:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.146875] pci 0000:00:06.0: setting latency timer to 64
[    2.146882] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.146885] pci 0000:00:1c.0: setting latency timer to 64
[    2.146891] pci 0000:00:1e.0: setting latency timer to 64
[    2.146895] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    2.146897] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    2.146899] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    2.146901] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    2.146903] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.146906] pci_bus 0000:02: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    2.146908] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    2.146910] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7efffff]
[    2.146912] pci_bus 0000:03: resource 2 [mem 0xfc000000-0xfc1fffff 64bit pref]
[    2.146914] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    2.146916] pci_bus 0000:04: resource 1 [mem 0xf0000000-0xf7bfffff]
[    2.146918] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    2.146920] pci_bus 0000:04: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    2.146951] NET: Registered protocol family 2
[    2.147093] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.148162] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.151859] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.152355] TCP: Hash tables configured (established 524288 bind 65536)
[    2.152358] TCP reno registered
[    2.152367] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.152406] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.152571] NET: Registered protocol family 1
[    2.152760] pci 0000:01:00.0: Boot video device
[    2.152773] PCI: CLS 64 bytes, default 64
[    2.152776] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.152779] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    2.152781] software IO TLB at phys 0x1fde000 - 0x5fde000
[    2.152828] Simple Boot Flag at 0x7a set to 0x80
[    2.153087] Scanning for low memory corruption every 60 seconds
[    2.153239] audit: initializing netlink socket (disabled)
[    2.153250] type=2000 audit(1285152293.150:1): initialized
[    2.166204] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.167510] VFS: Disk quotas dquot_6.5.2
[    2.167559] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.168082] fuse init (API version 7.14)
[    2.168157] msgmni has been set to 7786
[    2.170478] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.170482] io scheduler noop registered
[    2.170483] io scheduler deadline registered
[    2.170516] io scheduler cfq registered (default)
[    2.170607] pcieport 0000:00:01.0: setting latency timer to 64
[    2.170628]   alloc irq_desc for 40 on node -1
[    2.170630]   alloc kstat_irqs on node -1
[    2.170640] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.170683] pcieport 0000:00:06.0: setting latency timer to 64
[    2.170702]   alloc irq_desc for 41 on node -1
[    2.170703]   alloc kstat_irqs on node -1
[    2.170720] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    2.170772] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.170799]   alloc irq_desc for 42 on node -1
[    2.170801]   alloc kstat_irqs on node -1
[    2.170807] pcieport 0000:00:1c.0: irq 42 for MSI/MSI-X
[    2.170883] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.170930] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.170992] intel_idle: MWAIT substates: 0x20
[    2.170994] intel_idle: does not run on family 6 model 15
[    2.171070] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.171074] ACPI: Power Button [VBTN]
[    2.171113] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.171116] ACPI: Power Button [PWRF]
[    2.171876] ACPI: acpi_idle registered with cpuidle
[    2.285125] ERST: Table is not found!
[    2.286423] Linux agpgart interface v0.103
[    2.286441] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.287492] brd: module loaded
[    2.287906] loop: module loaded
[    2.288279] Fixed MDIO Bus: probed
[    2.288308] PPP generic driver version 2.4.2
[    2.288333] tun: Universal TUN/TAP device driver, 1.6
[    2.288335] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.288391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.288409]   alloc irq_desc for 22 on node -1
[    2.288411]   alloc kstat_irqs on node -1
[    2.288418] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.288444] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.288447] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.288479] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.288509] ehci_hcd 0000:00:1a.7: debug port 1
[    2.292412] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    2.292426] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfbfdec00
[    2.310655] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.310801] hub 1-0:1.0: USB hub found
[    2.310806] hub 1-0:1.0: 6 ports detected
[    2.310862]   alloc irq_desc for 23 on node -1
[    2.310863]   alloc kstat_irqs on node -1
[    2.310867] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.310876] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.310879] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.310909] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.310932] ehci_hcd 0000:00:1d.7: debug port 1
[    2.314805] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.314818] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    2.330653] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.330771] hub 2-0:1.0: USB hub found
[    2.330781] hub 2-0:1.0: 6 ports detected
[    2.330840] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.330851] uhci_hcd: USB Universal Host Controller Interface driver
[    2.330891] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.330897] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.330900] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.330925] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.330953] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    2.331045] hub 3-0:1.0: USB hub found
[    2.331050] hub 3-0:1.0: 2 ports detected
[    2.331095]   alloc irq_desc for 17 on node -1
[    2.331097]   alloc kstat_irqs on node -1
[    2.331101] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.331106] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.331109] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.331135] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.331163] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    2.331253] hub 4-0:1.0: USB hub found
[    2.331257] hub 4-0:1.0: 2 ports detected
[    2.331309] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.331314] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.331316] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.331347] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.331368] uhci_hcd 0000:00:1a.2: irq 22, io base 0x0000ecc0
[    2.331459] hub 5-0:1.0: USB hub found
[    2.331463] hub 5-0:1.0: 2 ports detected
[    2.331511] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.331516] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.331519] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.331543] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.331564] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    2.331657] hub 6-0:1.0: USB hub found
[    2.331660] hub 6-0:1.0: 2 ports detected
[    2.331706] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.331711] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.331714] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.331741] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.331761] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    2.331848] hub 7-0:1.0: USB hub found
[    2.331852] hub 7-0:1.0: 2 ports detected
[    2.331897]   alloc irq_desc for 18 on node -1
[    2.331898]   alloc kstat_irqs on node -1
[    2.331902] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.331910] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.331912] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.331937] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.331966] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.332054] hub 8-0:1.0: USB hub found
[    2.332057] hub 8-0:1.0: 2 ports detected
[    2.332139] PNP: No PS/2 controller found. Probing ports directly.
[    2.334910] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.334917] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.334979] mice: PS/2 mouse device common for all mice
[    2.335075] rtc_cmos 00:05: RTC can wake from S4
[    2.335105] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.335127] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.335203] device-mapper: uevent: version 1.0.3
[    2.335317] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.335473] device-mapper: multipath: version 1.1.1 loaded
[    2.335476] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.335795] cpuidle: using governor ladder
[    2.335798] cpuidle: using governor menu
[    2.336107] TCP cubic registered
[    2.336210] NET: Registered protocol family 10
[    2.336529] lo: Disabled Privacy Extensions
[    2.336694] NET: Registered protocol family 17
[    2.336816] PM: Resume from disk failed.
[    2.336828] registered taskstats version 1
[    2.337093]   Magic number: 10:415:730
[    2.337159] rtc_cmos 00:05: setting system clock to 2010-09-22 10:44:54 UTC (1285152294)
[    2.337167] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.337168] EDD information not available.
[    2.337236] Freeing unused kernel memory: 908k freed
[    2.337472] Write protecting the kernel read-only data: 10240k
[    2.337660] Freeing unused kernel memory: 424k freed
[    2.337909] Freeing unused kernel memory: 1644k freed
[    2.352627] udev[97]: starting version 162
[    2.389228] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    2.389231] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    2.389266]   alloc irq_desc for 21 on node -1
[    2.389268]   alloc kstat_irqs on node -1
[    2.389276] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.389288] e1000e 0000:00:19.0: setting latency timer to 64
[    2.389396]   alloc irq_desc for 43 on node -1
[    2.389398]   alloc kstat_irqs on node -1
[    2.389408] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    2.396487] firewire_ohci 0000:04:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.450057] firewire_ohci: Added fw-ohci device 0000:04:0a.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.630077] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    2.788839] Initializing USB Mass Storage driver...
[    2.788996] scsi0 : usb-storage 1-4:1.0
[    2.789132] usbcore: registered new interface driver usb-storage
[    2.789135] USB Mass Storage support registered.
[    2.832981] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1d:09:17:ee:fc
[    2.832984] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.833006] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: 1031ff-0ff
[    2.833024] ahci 0000:00:1f.2: version 3.0
[    2.833036]   alloc irq_desc for 20 on node -1
[    2.833039]   alloc kstat_irqs on node -1
[    2.833046] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    2.833099]   alloc irq_desc for 44 on node -1
[    2.833100]   alloc kstat_irqs on node -1
[    2.833108] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    2.833116] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    2.833180] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    2.833183] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pmp pio slum part ccc ems sxs 
[    2.833187] ahci 0000:00:1f.2: setting latency timer to 64
[    2.930104] scsi1 : ahci
[    2.930221] scsi2 : ahci
[    2.930294] scsi3 : ahci
[    2.930376] scsi4 : ahci
[    2.930449] scsi5 : ahci
[    2.930530] scsi6 : ahci
[    2.930582] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 44
[    2.930585] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 44
[    2.930588] ata3: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970200 irq 44
[    2.930590] ata4: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970280 irq 44
[    2.930593] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 44
[    2.930595] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 44
[    2.960115] firewire_core: created device fw0: GUID 8000000a551df0cf, S400
[    3.030033] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    3.235667] scsi7 : usb-storage 2-2:1.0
[    3.281940] ata5: SATA link down (SStatus 4 SControl 300)
[    3.281965] ata6: SATA link down (SStatus 0 SControl 300)
[    3.350052] usb 2-3: new high speed USB device using ehci_hcd and address 4
[    3.461910] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.461927] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.461939] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.461950] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.468170] ata1.00: ATA-8: SAMSUNG HD321KJ, CP100-12, max UDMA7
[    3.468173] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.468308] ata2.00: ATA-7: SAMSUNG HD103UJ, 1AA01112, max UDMA7
[    3.468312] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.470224] ata1.00: configured for UDMA/133
[    3.471334] ata3.00: ATAPI: PBDS CD-RW/DVD-ROM DH-48C2S, ND11, max UDMA/100
[    3.474366] ata4.00: ATAPI: PBDS DVD+/-RW DH-16W1S, 2D14, max UDMA/100
[    3.474739] ata2.00: configured for UDMA/133
[    3.481178] ata3.00: configured for UDMA/100
[    3.487200] ata4.00: configured for UDMA/100
[    3.487347] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[    3.487493] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.487525] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    3.487577] sd 1:0:0:0: [sda] Write Protect is off
[    3.487579] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.487599] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.487724]  sda: sda1 sda2 sda3 <
[    3.492669] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[    3.492772] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.492793] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.492825] sd 2:0:0:0: [sdb] Write Protect is off
[    3.492828] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.492856] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.493002]  sdb: sdb1
[    3.498020] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.503071] scsi 3:0:0:0: CD-ROM            PBDS     CDRWDVD DH-48C2S ND11 PQ: 0 ANSI: 5
[    3.503730] hub 2-3:1.0: USB hub found
[    3.504061] hub 2-3:1.0: 4 ports detected
[    3.509204] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[    3.509208] Uniform CD-ROM driver Revision: 3.20
[    3.509327] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.509373] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    3.510294] scsi 4:0:0:0: CD-ROM            PBDS     DVD+-RW DH-16W1S 2D14 PQ: 0 ANSI: 5
[    3.511876]  sda5 >
[    3.512171] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.514911] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.515026] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    3.515075] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    3.780026] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    3.782535] scsi 0:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[    3.783016] sd 0:0:0:0: Attached scsi generic sg4 type 0
[    3.783518] sd 0:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.784018] sd 0:0:0:0: [sdc] Write Protect is off
[    3.784022] sd 0:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    3.784025] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    3.785165] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    3.785171]  sdc: sdc1
[    3.791778] sd 0:0:0:0: [sdc] Assuming drive cache: write through
[    3.791782] sd 0:0:0:0: [sdc] Attached SCSI disk
[    3.874558] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.981554] hub 6-1:1.0: USB hub found
[    3.983498] hub 6-1:1.0: 3 ports detected
[    4.067902] usb 2-3.4: new high speed USB device using ehci_hcd and address 5
[    4.191189] hub 2-3.4:1.0: USB hub found
[    4.191261] hub 2-3.4:1.0: 7 ports detected
[    4.242413] scsi 7:0:0:0: Direct-Access     DELL     USB   HS-CF Card 7.12 PQ: 0 ANSI: 0
[    4.246283] scsi 7:0:0:1: Direct-Access     DELL     USB   HS-xD/SM   7.12 PQ: 0 ANSI: 0
[    4.249775] scsi 7:0:0:2: Direct-Access     DELL     USB   HS-MS Card 7.12 PQ: 0 ANSI: 0
[    4.252900] scsi 7:0:0:3: Direct-Access     DELL     USB   HS-SD Card 7.12 PQ: 0 ANSI: 0
[    4.253282] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    4.253414] sd 7:0:0:1: Attached scsi generic sg6 type 0
[    4.253536] sd 7:0:0:2: Attached scsi generic sg7 type 0
[    4.253644] sd 7:0:0:3: Attached scsi generic sg8 type 0
[    4.270765] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    4.275512] sd 7:0:0:1: [sde] Attached SCSI removable disk
[    4.280016] sd 7:0:0:2: [sdf] Attached SCSI removable disk
[    4.282477] usb 6-1.1: new full speed USB device using uhci_hcd and address 3
[    4.287885] sd 7:0:0:3: [sdg] Attached SCSI removable disk
[    4.542459] usb 6-1.2: new full speed USB device using uhci_hcd and address 4
[    4.790668] usb 6-1.3: new full speed USB device using uhci_hcd and address 5
[    5.030214] usb 2-3.4.3: new low speed USB device using ehci_hcd and address 6
[    5.380200] usb 2-3.4.4: new full speed USB device using ehci_hcd and address 7
[   18.566336] udev[367]: starting version 162
[   18.576480] Adding 7728124k swap on /dev/sda5.  Priority:-1 extents:1 across:7728124k 
[   18.613484] lp: driver loaded but no devices found
[   18.614585] EDAC MC: Ver: 2.1.0 Aug 29 2010
[   18.649249] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.673410] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[   18.701228] IR NEC protocol handler initialized
[   18.713328] type=1400 audit(1285152310.864:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=578 comm="apparmor_parser"
[   18.713942] type=1400 audit(1285152310.864:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=578 comm="apparmor_parser"
[   18.714271] type=1400 audit(1285152310.864:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=578 comm="apparmor_parser"
[   18.715570] usbcore: registered new interface driver hiddev
[   18.720883] WARNING: You're using an experimental version of the DVB stack. As the driver
[   18.720885]          is backported to an older kernel, it doesn't offer enough quality for
[   18.720886]          its usage in production.
[   18.720887]          Use it with care.
[   18.721777] type=1400 audit(1285152310.874:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=607 comm="apparmor_parser"
[   18.721810] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.2/6-1.2:1.0/input/input2
[   18.721900] generic-usb 0003:046D:C718.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.2/input0
[   18.733760] Bluetooth: Core ver 2.15
[   18.733790] NET: Registered protocol family 31
[   18.733792] Bluetooth: HCI device and connection manager initialized
[   18.733795] Bluetooth: HCI socket layer initialized
[   18.739879] IR RC5(x) protocol handler initialized
[   18.739894] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   18.740049] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.3/6-1.3:1.0/input/input3
[   18.740257] generic-usb 0003:046D:C719.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.3/input0
[   18.740500] usbcore: registered new interface driver usbhid
[   18.740502] usbhid: USB HID core driver
[   18.740585] nvidia: module license 'NVIDIA' taints kernel.
[   18.740589] Disabling lock debugging due to kernel taint
[   18.742180] Linux video capture interface: v2.00
[   18.742183] WARNING: You're using an experimental version of the V4L stack. As the driver
[   18.742184]          is backported to an older kernel, it doesn't offer enough quality for
[   18.742185]          its usage in production.
[   18.742185]          Use it with care.
[   18.752324] usbcore: registered new interface driver btusb
[   18.752698] ortek 0003:05A4:2000.0005: Fixing up Ortek WKB-2000 report descriptor.
[   18.752792] IR RC6 protocol handler initialized
[   18.752925] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4.3/2-3.4.3:1.0/input/input4
[   18.753102] gyration 0003:0C16:0002.0003: input,hiddev97,hidraw2: USB HID v1.10 Keyboard [Gyration Gyration RF Technology Receiver] on usb-0000:00:1d.7-3.4.3/input0
[   18.753315] input: ORTEK Smartpad Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4.4/2-3.4.4:1.0/input/input5
[   18.753612] ortek 0003:05A4:2000.0005: input,hidraw3: USB HID v1.10 Keyboard [ORTEK Smartpad Keyboard] on usb-0000:00:1d.7-3.4.4/input0
[   18.758133] input: Gyration Gyration RF Technology Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4.3/2-3.4.3:1.1/input/input6
[   18.758289] gyration 0003:0C16:0002.0004: input,hiddev98,hidraw4: USB HID v1.20 Mouse [Gyration Gyration RF Technology Receiver] on usb-0000:00:1d.7-3.4.3/input1
[   18.758604] input: ORTEK Smartpad Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4.4/2-3.4.4:1.1/input/input7
[   18.759330] ortek 0003:05A4:2000.0006: input,hiddev99,hidraw5: USB HID v1.10 Mouse [ORTEK Smartpad Keyboard] on usb-0000:00:1d.7-3.4.4/input1
[   18.761004] cx23885 driver version 0.0.2 loaded
[   18.761056] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.761625] CORE cx23885[0]: subsystem: 0070:71d1, board: Hauppauge WinTV-HVR1200 [card=7,autodetected]
[   18.822931] SB-XFi 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.839245] IR JVC protocol handler initialized
[   18.843203] nGene PCIE bridge driver, Copyright (C) 2005-2007 Micronas
[   18.929298] tveeprom 0-0050: Hauppauge model 71999, rev J1E9, serial# 3544323
[   18.929301] tveeprom 0-0050: MAC address is 00:0d:fe:36:15:03
[   18.929304] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   18.929307] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   18.929309] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[   18.929312] tveeprom 0-0050: decoder processor is CX23885B (idx 41)
[   18.929314] tveeprom 0-0050: has no radio
[   18.929315] cx23885[0]: hauppauge eeprom: model=71999
[   18.929318] cx23885_dvb_register() allocating 1 frontend(s)
[   18.929320] cx23885[0]: cx23885 based dvb card
[   18.948529] tda829x 1-0042: type set to tda8295
[   18.983149] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.988473] tda18271 1-0060: creating new instance
[   19.030970] TDA18271HD/C1 detected @ 1-0060
[   19.221601] IR Sony protocol handler initialized
[   19.471376] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.471391] nvidia 0000:01:00.0: setting latency timer to 64
[   19.471396] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.471651] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.53  Fri Aug 27 20:27:48 PDT 2010
[   20.572704] DVB: registering new adapter (cx23885[0])
[   20.572710] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   20.573150] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   20.573158] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xf7c00000
[   20.573165] cx23885 0000:03:00.0: setting latency timer to 64
[   20.900064] type=1400 audit(1285152313.044:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=900 comm="apparmor_parser"
[   20.900122] type=1400 audit(1285152313.044:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=901 comm="apparmor_parser"
[   20.900747] type=1400 audit(1285152313.054:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[   20.901094] type=1400 audit(1285152313.054:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   20.901508] type=1400 audit(1285152313.054:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=904 comm="apparmor_parser"
[   20.901709] type=1400 audit(1285152313.054:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=905 comm="apparmor_parser"
[   21.230637] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   21.260890] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   21.294302] tda10048_firmware_upload: Upload failed. (file not found?)
[   21.320778] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   21.321488] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.757403] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.757406] vboxdrv: Successfully done.
[   21.757408] vboxdrv: Found 4 processor cores.
[   21.757600] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e1bd60
[   21.757651] vboxdrv: fAsync=0 offMin=0x5b2 offMax=0x1677
[   21.758109] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.758111] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).
[   21.863394] Bluetooth: L2CAP ver 2.14
[   21.863397] Bluetooth: L2CAP socket layer initialized
[   21.867330] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.867332] Bluetooth: BNEP filters: protocol multicast
[   21.870857] Bluetooth: SCO (Voice Link) ver 0.6
[   21.870860] Bluetooth: SCO socket layer initialized
[   21.932785] ppdev: user-space parallel port driver
[   22.022442] Bluetooth: RFCOMM TTY layer initialized
[   22.022448] Bluetooth: RFCOMM socket layer initialized
[   22.022449] Bluetooth: RFCOMM ver 1.11
[   22.324329] ata1.00: configured for UDMA/133
[   22.324336] ata1: EH complete
[   22.464163] ata2.00: configured for UDMA/133
[   22.464167] ata2: EH complete
[   22.721593] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   22.721597] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   22.722056] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.678294] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   33.030634] eth0: no IPv6 routers present
[   37.311577] lo: Disabled Privacy Extensions
[   53.069285] lo: Disabled Privacy Extensions
[   71.930474] lo: Disabled Privacy Extensions
james-sarah@jamessarah-desktop:~$ 

```

Thanks in advance.
James

---

