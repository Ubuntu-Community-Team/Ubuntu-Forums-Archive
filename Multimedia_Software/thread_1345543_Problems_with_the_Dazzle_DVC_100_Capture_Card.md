---
title: "Problems with the Dazzle DVC 100 Capture Card"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Lyon on 2009-12-04
I've just bought a Dazzle DVC 100 capture card to stream content from my tv to sites like livestream/ustream.

When I log into the studio in livestream, the video appears only half the time in the preview screen (usually after a reboot), and then goes black when it is cued to go live. Also of note is that the colours seem to be inverted in the preview.

I had webcamstudio4linux installed, and I think the video4linux module might be causing the issues.

Here is the output of my dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=b8a849e1-8ba4-459e-9893-47399385a5d1 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D7FFF write-protect
[    0.000000]   D8000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007fed0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fed0000 page 4k
[    0.000000] kernel direct mapping tables up to 7fed0000 @ 8000-c000
[    0.000000] RAMDISK: 3786e000 - 37fefb74
[    0.000000] ACPI: RSDP 00000000000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 000000007fed5b59 0007C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000007fedfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 000000007fed703c 08BBC (v01 HP     30D2     06040000 INTL 20061109)
[    0.000000] ACPI: FACS 000000007fee2fc0 00040
[    0.000000] ACPI: HPET 000000007fedfd60 00038 (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 000000007fedfd98 0003C (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 000000007fedfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC 000000007fedfdfa 00068 (v01 HP     30D2     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000007fedfe62 00028 (v01 HP     30D2     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 000000007fedfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 000000007fed6d5f 002DD (v01 HP     30D2     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fed6161 0025F (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fed60bb 000A6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 000000007fed5bd5 004E6 (v01  HP     30D2    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fed0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fed0000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001efdf] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007fed0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [003786e000 - 0037fefb74]          RAMDISK ==> [003786e000 - 0037fefb74]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e51a0]              BRK ==> [00019e5000 - 00019e51a0]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f8520] f8520
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523882
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3837 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512780 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
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
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f6000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516617
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=b8a849e1-8ba4-459e-9893-47399385a5d1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2048624k/2095936k available (5315k kernel code, 408k absent, 46904k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2195.039 MHz processor.
[    0.001942] Console: colour VGA+ 80x25
[    0.001945] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.07 BogoMIPS (lpj=21950390)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 4096K
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
[    0.017646] Setting APIC routing to flat
[    0.017990] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.118026] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4389.52 BogoMIPS (lpj=21947637)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 4096K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271543] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.271553] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280022] Brought up 2 CPUs
[    0.280025] Total of 2 processors activated (8779.60 BogoMIPS).
[    0.280078] CPU0 attaching sched-domain:
[    0.280081]  domain 0: span 0-1 level MC
[    0.280083]   groups: 0 1
[    0.280088] CPU1 attaching sched-domain:
[    0.280090]  domain 0: span 0-1 level MC
[    0.280092]   groups: 1 0
[    0.280163] Booting paravirtualized kernel on bare hardware
[    0.280163] regulator: core version 0.5
[    0.280163] Time:  9:45:53  Date: 12/04/09
[    0.280163] NET: Registered protocol family 16
[    0.280205] ACPI: bus type pci registered
[    0.280271] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.280273] PCI: MCFG area at e0000000 reserved in E820
[    0.284759] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.284761] PCI: Using configuration type 1 for base access
[    0.285550] bio: create slab <bio-0> at 0
[    0.285550] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.285550] ACPI: EC: Look up EC in DSDT
[    0.291505] ACPI: BIOS _OSI(Linux) query ignored
[    0.292683] ACPI: Interpreter enabled
[    0.292686] ACPI: (supports S0 S3 S4 S5)
[    0.292705] ACPI: Using IOAPIC for interrupt routing
[    0.294275] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.310634] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.310634] ACPI: EC: driver started in interrupt mode
[    0.310853] ACPI: No dock devices found.
[    0.320275] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.320379] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.320382] pci 0000:00:01.0: PME# disabled
[    0.320471] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.320535] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.320602] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8404800-0xf8404bff]
[    0.320665] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.320670] pci 0000:00:1a.7: PME# disabled
[    0.320725] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8400000-0xf8403fff]
[    0.320787] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.320792] pci 0000:00:1b.0: PME# disabled
[    0.320879] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.320884] pci 0000:00:1c.0: PME# disabled
[    0.320974] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.320979] pci 0000:00:1c.1: PME# disabled
[    0.321068] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.321073] pci 0000:00:1c.5: PME# disabled
[    0.321146] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.321227] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.321295] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.321363] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8404c00-0xf8404fff]
[    0.321426] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.321431] pci 0000:00:1d.7: PME# disabled
[    0.321596] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.321600] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.321608] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0380 (mask 0007)
[    0.321661] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.321669] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.321677] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.321685] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.321693] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.321768] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    0.321775] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.321783] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    0.321790] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.321797] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.321805] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8404000-0xf84047ff]
[    0.321849] pci 0000:00:1f.2: PME# supported from D3hot
[    0.321853] pci 0000:00:1f.2: PME# disabled
[    0.321886] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.321911] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.321989] pci 0000:01:00.0: reg 10 32bit mmio: [0xce000000-0xceffffff]
[    0.322005] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.322021] pci 0000:01:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]
[    0.322031] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.322040] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.322150] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.322153] pci 0000:00:01.0: bridge 32bit mmio: [0xcc000000-0xceffffff]
[    0.322157] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.322245] pci 0000:02:00.0: reg 10 64bit mmio: [0xf4000000-0xf4001fff]
[    0.322358] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.322365] pci 0000:02:00.0: PME# disabled
[    0.322446] pci 0000:00:1c.0: bridge io port: [0x4000-0x7fff]
[    0.322451] pci 0000:00:1c.0: bridge 32bit mmio: [0xf4000000-0xf5ffffff]
[    0.322458] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.322520] pci 0000:00:1c.1: bridge io port: [0x8000-0xbfff]
[    0.322525] pci 0000:00:1c.1: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.322533] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.322608] pci 0000:08:00.0: reg 10 io port: [0xc000-0xc0ff]
[    0.322636] pci 0000:08:00.0: reg 18 64bit mmio: [0xf8000000-0xf8000fff]
[    0.322664] pci 0000:08:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.322725] pci 0000:08:00.0: supports D1 D2
[    0.322727] pci 0000:08:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.322733] pci 0000:08:00.0: PME# disabled
[    0.322812] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.322816] pci 0000:00:1c.5: bridge 32bit mmio: [0xf8000000-0xf80fffff]
[    0.322882] pci 0000:09:09.0: reg 10 32bit mmio: [0xf8100000-0xf81007ff]
[    0.322943] pci 0000:09:09.0: supports D1 D2
[    0.322945] pci 0000:09:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.322950] pci 0000:09:09.0: PME# disabled
[    0.322992] pci 0000:09:09.1: reg 10 32bit mmio: [0xf8100800-0xf81008ff]
[    0.323052] pci 0000:09:09.1: supports D1 D2
[    0.323054] pci 0000:09:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.323059] pci 0000:09:09.1: PME# disabled
[    0.323101] pci 0000:09:09.2: reg 10 32bit mmio: [0xf8100c00-0xf8100cff]
[    0.323161] pci 0000:09:09.2: supports D1 D2
[    0.323162] pci 0000:09:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.323167] pci 0000:09:09.2: PME# disabled
[    0.323209] pci 0000:09:09.3: reg 10 32bit mmio: [0xf8101000-0xf81010ff]
[    0.323270] pci 0000:09:09.3: supports D1 D2
[    0.323272] pci 0000:09:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.323277] pci 0000:09:09.3: PME# disabled
[    0.323320] pci 0000:09:09.4: reg 10 32bit mmio: [0xf8101400-0xf81014ff]
[    0.323381] pci 0000:09:09.4: supports D1 D2
[    0.323383] pci 0000:09:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.323388] pci 0000:09:09.4: PME# disabled
[    0.323440] pci 0000:00:1e.0: transparent bridge
[    0.323448] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8100000-0xf81fffff]
[    0.323486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.323661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.323742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.323814] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.323879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.323974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.331875] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.331975] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.332073] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.332170] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.332268] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.332365] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.332463] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.332560] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.332718] SCSI subsystem initialized
[    0.332737] libata version 3.00 loaded.
[    0.332737] usbcore: registered new interface driver usbfs
[    0.332737] usbcore: registered new interface driver hub
[    0.332737] usbcore: registered new device driver usb
[    0.332737] ACPI: WMI: Mapper loaded
[    0.332737] PCI: Using ACPI for IRQ routing
[    0.360007] Bluetooth: Core ver 2.15
[    0.360022] NET: Registered protocol family 31
[    0.360022] Bluetooth: HCI device and connection manager initialized
[    0.360022] Bluetooth: HCI socket layer initialized
[    0.360022] NetLabel: Initializing
[    0.360022] NetLabel:  domain hash size = 128
[    0.360022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360031] NetLabel:  unlabeled traffic allowed by default
[    0.360074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.360078] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.400004] pnp: PnP ACPI init
[    0.400013] ACPI: bus type pnp registered
[    0.404529] pnp: PnP ACPI: found 11 devices
[    0.404531] ACPI: ACPI bus type pnp unregistered
[    0.404541] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.404544] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.404546] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.404549] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.404551] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.404554] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.404557] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.404559] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.404565] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.404571] system 00:06: ioport range 0x380-0x383 has been reserved
[    0.404573] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.404576] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.404578] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.404581] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.404583] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.404586] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.404591] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.404593] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.409253] AppArmor: AppArmor Filesystem Enabled
[    0.409320] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.409323] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.409326] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.409330] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.409333] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.409338] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.409341] pci 0000:00:1c.0:   IO window: 0x4000-0x7fff
[    0.409347] pci 0000:00:1c.0:   MEM window: 0xf4000000-0xf5ffffff
[    0.409352] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.409360] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.409363] pci 0000:00:1c.1:   IO window: 0x8000-0xbfff
[    0.409370] pci 0000:00:1c.1:   MEM window: 0xf6000000-0xf7ffffff
[    0.409374] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.409383] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.409386] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.409392] pci 0000:00:1c.5:   MEM window: 0xf8000000-0xf80fffff
[    0.409397] pci 0000:00:1c.5:   PREFETCH window: 0x80000000-0x800fffff
[    0.409403] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.409404] pci 0000:00:1e.0:   IO window: disabled
[    0.409410] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xf81fffff
[    0.409415] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.409425]   alloc irq_desc for 16 on node 0
[    0.409427]   alloc kstat_irqs on node 0
[    0.409431] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.409435] pci 0000:00:01.0: setting latency timer to 64
[    0.409442]   alloc irq_desc for 17 on node 0
[    0.409443]   alloc kstat_irqs on node 0
[    0.409446] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.409451] pci 0000:00:1c.0: setting latency timer to 64
[    0.409459] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.409464] pci 0000:00:1c.1: setting latency timer to 64
[    0.409472] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.409476] pci 0000:00:1c.5: setting latency timer to 64
[    0.409483] pci 0000:00:1e.0: setting latency timer to 64
[    0.409487] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.409490] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.409492] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.409494] pci_bus 0000:01: resource 1 mem: [0xcc000000-0xceffffff]
[    0.409496] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.409499] pci_bus 0000:02: resource 0 io:  [0x4000-0x7fff]
[    0.409501] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xf5ffffff]
[    0.409503] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.409505] pci_bus 0000:04: resource 0 io:  [0x8000-0xbfff]
[    0.409507] pci_bus 0000:04: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.409509] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.409511] pci_bus 0000:08: resource 0 io:  [0xc000-0xcfff]
[    0.409513] pci_bus 0000:08: resource 1 mem: [0xf8000000-0xf80fffff]
[    0.409515] pci_bus 0000:08: resource 2 pref mem [0x80000000-0x800fffff]
[    0.409518] pci_bus 0000:09: resource 1 mem: [0xf8100000-0xf81fffff]
[    0.409520] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.409522] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.409550] NET: Registered protocol family 2
[    0.409674] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.410415] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.412163] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.412720] TCP: Hash tables configured (established 262144 bind 65536)
[    0.412723] TCP reno registered
[    0.412832] NET: Registered protocol family 1
[    0.412902] Trying to unpack rootfs image as initramfs...
[    0.501570] Switched to high resolution mode on CPU 1
[    0.509991] Switched to high resolution mode on CPU 0
[    0.582506] Freeing initrd memory: 7686k freed
[    0.586532] Simple Boot Flag at 0x35 set to 0x1
[    0.586715] Scanning for low memory corruption every 60 seconds
[    0.586861] audit: initializing netlink socket (disabled)
[    0.586879] type=2000 audit(1259919953.580:1): initialized
[    0.596031] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.597331] VFS: Disk quotas dquot_6.5.2
[    0.597381] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.597915] fuse init (API version 7.12)
[    0.597988] msgmni has been set to 4016
[    0.598183] alg: No test for stdrng (krng)
[    0.598195] io scheduler noop registered
[    0.598197] io scheduler anticipatory registered
[    0.598199] io scheduler deadline registered
[    0.598235] io scheduler cfq registered (default)
[    0.598391] pci 0000:01:00.0: Boot video device
[    0.598528]   alloc irq_desc for 24 on node 0
[    0.598531]   alloc kstat_irqs on node 0
[    0.598540] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.598546] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.598697]   alloc irq_desc for 25 on node 0
[    0.598699]   alloc kstat_irqs on node 0
[    0.598708] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.598719] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.598888]   alloc irq_desc for 26 on node 0
[    0.598889]   alloc kstat_irqs on node 0
[    0.598898] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.598909] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.599084]   alloc irq_desc for 27 on node 0
[    0.599086]   alloc kstat_irqs on node 0
[    0.599095] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.599105] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.599211] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.599330] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.602474] ACPI: AC Adapter [ACAD] (on-line)
[    0.602545] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.602549] ACPI: Power Button [PWRF]
[    0.602604] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.602611] ACPI: Power Button [PWRB]
[    0.602651] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.602653] ACPI: Sleep Button [SLPB]
[    0.602695] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.605612] ACPI: Lid Switch [LID]
[    0.606230] ACPI: SSDT 000000007fed6a1d 0027A (v01  HP    30D2     00003000 INTL 20061109)
[    0.606685] ACPI: SSDT 000000007fed63c0 005D8 (v01  HP    30D2     00003001 INTL 20061109)
[    0.608924] Monitor-Mwait will be used to enter C-1 state
[    0.608947] Monitor-Mwait will be used to enter C-2 state
[    0.608966] Monitor-Mwait will be used to enter C-3 state
[    0.608973] Marking TSC unstable due to TSC halts in idle
[    0.608993] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.609014] processor LNXCPU:00: registered as cooling_device0
[    0.609017] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.609358] ACPI: SSDT 000000007fed6c97 000C8 (v01  HP    30D2     00003000 INTL 20061109)
[    0.609663] ACPI: SSDT 000000007fed6998 00085 (v01  HP    30D2     00003000 INTL 20061109)
[    0.610578] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.610595] processor LNXCPU:01: registered as cooling_device1
[    0.610599] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.618803] ACPI Exception: AE_OK, No or invalid critical threshold 20090521 thermal-384
[    0.619863] Linux agpgart interface v0.103
[    0.619872] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.620988] brd: module loaded
[    0.621392] loop: module loaded
[    0.621453] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.621556] ahci 0000:00:1f.2: version 3.0
[    0.621571]   alloc irq_desc for 19 on node 0
[    0.621573]   alloc kstat_irqs on node 0
[    0.621578] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.621608]   alloc irq_desc for 28 on node 0
[    0.621610]   alloc kstat_irqs on node 0
[    0.621619] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.621682] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.621685] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    0.621690] ahci 0000:00:1f.2: setting latency timer to 64
[    0.622445] scsi0 : ahci
[    0.622531] scsi1 : ahci
[    0.623105] scsi2 : ahci
[    0.623225] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 28
[    0.623228] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 28
[    0.623232] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 28
[    0.623865] ata_piix 0000:00:1f.1: version 2.13
[    0.623873] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.623910] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.623980] scsi3 : ata_piix
[    0.624032] scsi4 : ata_piix
[    0.624581] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.624584] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.625323] Fixed MDIO Bus: probed
[    0.625352] PPP generic driver version 2.4.2
[    0.625433] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.626089]   alloc irq_desc for 18 on node 0
[    0.626091]   alloc kstat_irqs on node 0
[    0.626095] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.626112] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.626116] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.626171] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.630094] ehci_hcd 0000:00:1a.7: debug port 1
[    0.630101] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.630114] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[    0.650013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.650076] usb usb1: configuration #1 chosen from 1 choice
[    0.650104] hub 1-0:1.0: USB hub found
[    0.650110] hub 1-0:1.0: 4 ports detected
[    0.650193]   alloc irq_desc for 23 on node 0
[    0.650195]   alloc kstat_irqs on node 0
[    0.650199] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.650208] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.650211] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.650238] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.654138] ehci_hcd 0000:00:1d.7: debug port 1
[    0.654144] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.654157] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    0.670320] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.670380] usb usb2: configuration #1 chosen from 1 choice
[    0.670403] hub 2-0:1.0: USB hub found
[    0.670409] hub 2-0:1.0: 6 ports detected
[    0.670495] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.670510] uhci_hcd: USB Universal Host Controller Interface driver
[    0.671078] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.671084] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.671088] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.671119] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.671154] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.671225] usb usb3: configuration #1 chosen from 1 choice
[    0.671247] hub 3-0:1.0: USB hub found
[    0.671254] hub 3-0:1.0: 2 ports detected
[    0.671320]   alloc irq_desc for 21 on node 0
[    0.671322]   alloc kstat_irqs on node 0
[    0.671326] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.671332] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.671336] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.671362] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.671398] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.671469] usb usb4: configuration #1 chosen from 1 choice
[    0.671491] hub 4-0:1.0: USB hub found
[    0.671501] hub 4-0:1.0: 2 ports detected
[    0.671566] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.671572] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.671576] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.671606] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.671633] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.671704] usb usb5: configuration #1 chosen from 1 choice
[    0.671729] hub 5-0:1.0: USB hub found
[    0.671734] hub 5-0:1.0: 2 ports detected
[    0.671797] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.671804] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.671807] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.671836] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.671871] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.671941] usb usb6: configuration #1 chosen from 1 choice
[    0.671963] hub 6-0:1.0: USB hub found
[    0.671969] hub 6-0:1.0: 2 ports detected
[    0.672108] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.672114] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.672118] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.672144] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.672172] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.672242] usb usb7: configuration #1 chosen from 1 choice
[    0.672265] hub 7-0:1.0: USB hub found
[    0.672272] hub 7-0:1.0: 2 ports detected
[    0.672366] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.714903] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.714908] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.714962] mice: PS/2 mouse device common for all mice
[    0.715076] rtc_cmos 00:08: RTC can wake from S4
[    0.715109] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.715142] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.715225] device-mapper: uevent: version 1.0.3
[    0.717341] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.717407] device-mapper: multipath: version 1.1.0 loaded
[    0.717411] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.717615] cpuidle: using governor ladder
[    0.717720] cpuidle: using governor menu
[    0.718075] TCP cubic registered
[    0.718193] NET: Registered protocol family 10
[    0.718579] lo: Disabled Privacy Extensions
[    0.718837] NET: Registered protocol family 17
[    0.718853] Bluetooth: L2CAP ver 2.13
[    0.718855] Bluetooth: L2CAP socket layer initialized
[    0.718858] Bluetooth: SCO (Voice Link) ver 0.6
[    0.718860] Bluetooth: SCO socket layer initialized
[    0.718889] Bluetooth: RFCOMM TTY layer initialized
[    0.718892] Bluetooth: RFCOMM socket layer initialized
[    0.718893] Bluetooth: RFCOMM ver 1.11
[    0.719487] PM: Resume from disk failed.
[    0.719497] registered taskstats version 1
[    0.719603]   Magic number: 5:525:777
[    0.719626] misc rfkill: hash matches
[    0.719704] rtc_cmos 00:08: setting system clock to 2009-12-04 09:45:54 UTC (1259919954)
[    0.719707] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.719709] EDD information not available.
[    0.741298] ACPI: Battery Slot [BAT0] (battery present)
[    0.761283] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.802952] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, HH18, max MWDMA2
[    0.840515] ata4.00: configured for MWDMA2
[    0.970279] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.970290] ata2: SATA link down (SStatus 0 SControl 300)
[    0.970318] ata3: SATA link down (SStatus 0 SControl 300)
[    0.971139] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    0.971143] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[    0.971145] ata1.00: 488397168 sectors, multi 16: LBA48 
[    0.972098] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    0.972112] ata1.00: configured for UDMA/100
[    0.990299] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    0.990396] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[    0.990558] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.990592] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.990632] sd 0:0:0:0: [sda] Write Protect is off
[    0.990640] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.990659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.990757]  sda:
[    0.991395] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D HH18 PQ: 0 ANSI: 5
[    0.993791] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.993795] Uniform CD-ROM driver Revision: 3.20
[    0.993921] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    0.993984] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.002559] Clocksource tsc unstable (delta = -214026019 ns)
[    1.016256]  sda1 sda2 sda3
[    1.045223] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.045262] Freeing unused kernel memory: 660k freed
[    1.045500] Write protecting the kernel read-only data: 7584k
[    1.134909] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.134948] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.135012] r8169 0000:08:00.0: setting latency timer to 64
[    1.135093]   alloc irq_desc for 29 on node 0
[    1.135095]   alloc kstat_irqs on node 0
[    1.135116] r8169 0000:08:00.0: irq 29 for MSI/MSI-X
[    1.135694] eth0: RTL8101e at 0xffffc90000368000, 00:1b:24:e0:a3:8a, XID 34200000 IRQ 29
[    1.159790] usb 2-1: configuration #1 chosen from 1 choice
[    1.188627]   alloc irq_desc for 20 on node 0
[    1.188630]   alloc kstat_irqs on node 0
[    1.188638] ohci1394 0000:09:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.222119] acpi device:06: registered as cooling_device2
[    1.222244] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[    1.222292] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.242083] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.460048] usb 2-4: new high speed USB device using ehci_hcd and address 5
[    1.619203] usb 2-4: configuration #1 chosen from 1 choice
[    1.910048] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.114759] usb 5-2: configuration #1 chosen from 1 choice
[    2.122630] usbcore: registered new interface driver hiddev
[    2.174445] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input7
[    2.174513] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:1d.0-2/input0
[    2.174525] usbcore: registered new interface driver usbhid
[    2.174528] usbhid: v2.6:USB HID core driver
[    2.400037] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    2.560500] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0080f88f00]
[    2.570980] usb 6-1: configuration #1 chosen from 1 choice
[    2.655561] PM: Starting manual resume from disk
[    2.655565] PM: Resume from partition 8:1
[    2.655567] PM: Checking hibernation image.
[    2.655757] PM: Resume from disk failed.
[    2.709240] EXT4-fs (sda2): barriers enabled
[    2.728975] kjournald2 starting: pid 442, dev sda2:8, commit interval 5 seconds
[    2.728989] EXT4-fs (sda2): delayed allocation enabled
[    2.728994] EXT4-fs: file extents enabled
[    2.729463] EXT4-fs: mballoc enabled
[    2.729475] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.309296] type=1505 audit(1259919957.080:2): operation="profile_load" pid=465 name=/usr/share/gdm/guest-session/Xsession
[    3.311554] type=1505 audit(1259919957.090:3): operation="profile_load" pid=466 name=/sbin/dhclient3
[    3.312284] type=1505 audit(1259919957.090:4): operation="profile_load" pid=466 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.312641] type=1505 audit(1259919957.090:5): operation="profile_load" pid=466 name=/usr/lib/connman/scripts/dhclient-script
[    3.356198] type=1505 audit(1259919957.130:6): operation="profile_load" pid=467 name=/usr/bin/evince
[    3.366034] type=1505 audit(1259919957.140:7): operation="profile_load" pid=467 name=/usr/bin/evince-previewer
[    3.371848] type=1505 audit(1259919957.150:8): operation="profile_load" pid=467 name=/usr/bin/evince-thumbnailer
[    3.397385] type=1505 audit(1259919957.170:9): operation="profile_load" pid=469 name=/usr/lib/cups/backend/cups-pdf
[    4.140062] Adding 1044216k swap on /dev/sda1.  Priority:-1 extents:1 across:1044216k 
[    4.838091] EXT4-fs (sda2): internal journal on sda2:8
[    5.246522] udev: starting version 147
[    6.528621] lp: driver loaded but no devices found
[    6.860175] Linux video capture interface: v2.00
[    6.892655] em28xx: New device Pinnacle Systems GmbH DVC100 @ 480 Mbps (2304:021a, interface 0, class 0)
[    6.893158] em28xx #0: chip ID is em2820 (or em2710)
[    6.920136] cfg80211: Calling CRDA to update world regulatory domain
[    7.041695] ricoh-mmc: Ricoh MMC Controller disabling driver
[    7.041697] ricoh-mmc: Copyright(c) Philip Langdale
[    7.041931] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[    7.041948] ricoh-mmc: Controller is now disabled.
[    7.066350] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 1a 02 12 00 11 03 98 10 6a 2e
[    7.066366] em28xx #0: i2c eeprom 10: 00 00 06 57 4e 00 00 00 60 00 00 00 02 00 00 00
[    7.066382] em28xx #0: i2c eeprom 20: 02 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00
[    7.066397] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 10 01 00 00 00 00 00 00
[    7.066412] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    7.066427] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    7.066442] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 2e 03 50 00 69 00
[    7.066450] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[    7.066458] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 20 00 47 00
[    7.066465] em28xx #0: i2c eeprom 90: 6d 00 62 00 48 00 00 00 10 03 44 00 56 00 43 00
[    7.066473] em28xx #0: i2c eeprom a0: 31 00 30 00 30 00 00 00 32 00 30 00 33 00 35 00
[    7.066480] em28xx #0: i2c eeprom b0: 36 00 30 00 37 00 35 00 31 00 33 00 34 00 31 00
[    7.066488] em28xx #0: i2c eeprom c0: 30 00 32 00 30 00 30 00 30 00 31 00 00 00 32 00
[    7.066495] em28xx #0: i2c eeprom d0: 33 00 31 00 32 00 33 00 00 00 00 00 00 00 00 00
[    7.066502] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[    7.066510] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 2f 64 ec 04 99 62 5d 0e
[    7.066518] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xa10d9684
[    7.066520] em28xx #0: EEPROM info:
[    7.066521] em28xx #0:	AC97 audio (5 sample rates)
[    7.066523] em28xx #0:	300mA max power
[    7.066524] em28xx #0:	Table at 0x06, strings=0x1098, 0x2e6a, 0x0000
[    7.067244] em28xx #0: Identified as Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker (card=9)
[    7.599822] sdhci: Secure Digital Host Controller Interface driver
[    7.599825] sdhci: Copyright(c) Pierre Ossman
[    7.722761] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[    7.725361] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8
[    7.725440] usbcore: registered new interface driver uvcvideo
[    7.725449] USB Video Class driver (v0.1.0)
[    8.221122] cfg80211: World regulatory domain updated:
[    8.221125] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.221127] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.221130] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.221132] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.221134] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.221136] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.064972] nvidia: module license 'NVIDIA' taints kernel.
[    9.064976] Disabling lock debugging due to kernel taint
[    9.072477] sdhci-pci 0000:09:09.1: SDHCI controller found [1180:0822] (rev 22)
[    9.072496] sdhci-pci 0000:09:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    9.074569] Registered led device: mmc0::
[    9.075602] mmc0: SDHCI controller on PCI [0000:09:09.1] using PIO
[    9.326252] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.326263] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.326271] nvidia 0000:01:00.0: setting latency timer to 64
[    9.326431] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
[    9.800478] saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[   10.432011] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.432014] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.432368] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.432377] iwlagn 0000:02:00.0: setting latency timer to 64
[   10.432407] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   10.474783] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.474844]   alloc irq_desc for 30 on node 0
[   10.474846]   alloc kstat_irqs on node 0
[   10.474866] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[   10.867576] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.030226] em28xx #0: Config register raw data: 0x12
[   11.059375] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.071610] em28xx #0: AC97 vendor ID = 0xffffffff
[   11.090230] em28xx #0: AC97 features = 0x6a90
[   11.090234] em28xx #0: Empia 202 AC97 audio processor detected
[   11.493572]   alloc irq_desc for 22 on node 0
[   11.493576]   alloc kstat_irqs on node 0
[   11.493582] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.493618] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.704106] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   11.725615] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   11.767574] EXT4-fs (sda3): barriers enabled
[   11.780365] kjournald2 starting: pid 870, dev sda3:8, commit interval 5 seconds
[   11.780636] EXT4-fs (sda3): internal journal on sda3:8
[   11.780642] EXT4-fs (sda3): delayed allocation enabled
[   11.780647] EXT4-fs: file extents enabled
[   11.790279] EXT4-fs: mballoc enabled
[   11.790291] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   11.831905] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   11.850096] em28xx #0: v4l2 driver version 0.1.2
[   13.250172] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0
[   13.250197] em28xx audio device (2304:021a): interface 1, class 1
[   13.250214] em28xx audio device (2304:021a): interface 2, class 1
[   13.250253] usbcore: registered new interface driver em28xx
[   13.250256] em28xx driver loaded
[   13.315047] usbcore: registered new interface driver snd-usb-audio
[   14.507693] __ratelimit: 6 callbacks suppressed
[   14.507696] type=1505 audit(1259919968.280:12): operation="profile_replace" pid=978 name=/usr/share/gdm/guest-session/Xsession
[   14.509045] type=1505 audit(1259919968.280:13): operation="profile_replace" pid=979 name=/sbin/dhclient3
[   14.509648] type=1505 audit(1259919968.280:14): operation="profile_replace" pid=979 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.509984] type=1505 audit(1259919968.280:15): operation="profile_replace" pid=979 name=/usr/lib/connman/scripts/dhclient-script
[   14.512906] type=1505 audit(1259919968.290:16): operation="profile_replace" pid=980 name=/usr/bin/evince
[   14.523891] type=1505 audit(1259919968.300:17): operation="profile_replace" pid=980 name=/usr/bin/evince-previewer
[   14.529795] type=1505 audit(1259919968.300:18): operation="profile_replace" pid=980 name=/usr/bin/evince-thumbnailer
[   14.538167] type=1505 audit(1259919968.310:19): operation="profile_replace" pid=982 name=/usr/lib/cups/backend/cups-pdf
[   14.538871] type=1505 audit(1259919968.310:20): operation="profile_replace" pid=982 name=/usr/sbin/cupsd
[   14.540907] type=1505 audit(1259919968.320:21): operation="profile_replace" pid=983 name=/usr/sbin/tcpdump
[   14.801478] usplash:404 freeing invalid memtype ffffffffcd000000-ffffffffcde00000
[   16.611515] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.717756] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[   16.953123] Registered led device: iwl-phy0::radio
[   16.953155] Registered led device: iwl-phy0::assoc
[   16.953185] Registered led device: iwl-phy0::RX
[   16.953210] Registered led device: iwl-phy0::TX
[   17.041953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.119128] r8169: eth0: link down
[   17.119353] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.285380] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.285383] vboxdrv: Successfully done.
[   20.285385] vboxdrv: Found 2 processor cores.
[   20.285435] VBoxDrv: dbg - g_abExecMemory=ffffffffa0c5c280
[   20.285490] vboxdrv: fAsync=0 offMin=0x13f offMax=0x1f53
[   20.285526] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.285528] vboxdrv: Successfully loaded version 3.1.0 (interface 0x00100001).
[   21.395771] ppdev: user-space parallel port driver
[   49.259468] UDF-fs: Partition marked readonly; forcing readonly mount
[   49.297467] UDF-fs INFO UDF: Mounting volume 'ARRESTED_D3', timestamp 2004/08/09 18:12 (1e5c)
[   63.492982] wlan0: authenticate with AP 00:21:29:71:93:d1
[   63.495052] wlan0: authenticated
[   63.495056] wlan0: associate with AP 00:21:29:71:93:d1
[   63.503791] wlan0: RX AssocResp from 00:21:29:71:93:d1 (capab=0x401 status=0 aid=1)
[   63.503797] wlan0: associated
[   63.524305] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.810021] wlan0: no IPv6 routers present
[   79.193069] CE: hpet increasing min_delta_ns to 15000 nsec
[  152.002658] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  152.211379] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  200.146612] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  206.912777] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  261.385244] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  261.642385] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  367.826666] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  367.996455] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  391.690405] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:21:29:71:93:d1 tid = 0
[  515.847420] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:21:29:71:93:d1 tid = 6

```

I don't know much about it, but these lines seem to be the most relevant

```
[   11.850096] em28xx #0: v4l2 driver version 0.1.2
[   13.250172] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0
[   13.250197] em28xx audio device (2304:021a): interface 1, class 1
[   13.250214] em28xx audio device (2304:021a): interface 2, class 1
[   13.250253] usbcore: registered new interface driver em28xx
[   13.250256] em28xx driver loaded
```

and

```
[  152.002658] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  152.211379] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  200.146612] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  206.912777] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  261.385244] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  261.642385] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  367.826666] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  367.996455] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh

```

If anyone has any suggestions I would greatly appreciate it. I would love to not have to do a fresh installation of ubuntu just because one module is creating compatibility issues.

---

### Post by Lyon on 2009-12-04
Well, I tried a fresh installation of 9.10 and the problem still persists. When trying to connect to livestream, I can stream audio, but video does not show. In dmesg I'm getting the same as before:

```
[  461.509123] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  464.776173] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh
[  471.565619] em28xx #0: vidioc_s_fmt_vid_cap device in use by another fh

```

It seems that it thinks I'm using video in another application when I've literally only got firefox with the livestream studio (which runs in flash) open.

A google of that vidioc_s_fmt_vid_cap device line seems to only yield source code for the driver

---

### Post by Lyon on 2009-12-05
One final desperate bump. It doesn't seem to be just the capture card now that I've done more digging. The laptop's internal webcam seems to fail and give the same dmesg output as the capture card. I'd really like to get this working. Has no one had any experience with this?

---

### Post by Dynx on 2010-08-29
I have the same problem, before upgrading to 10.04 my DVC100 worked just fine.

---

### Post by no2498 on 2010-08-29
if i think rite the 

 13.250172] em28xx #0: V4L2 device registered as /dev/video1 and /dev/vbi0

is what the webcam uses

the card needs to be set to something else

hope this gets you thinking of the old settings you had

---

