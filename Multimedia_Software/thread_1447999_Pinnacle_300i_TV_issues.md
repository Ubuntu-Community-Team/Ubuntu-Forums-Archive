---
title: "Pinnacle 300i TV issues"
date: 2010-04-06
forum: Multimedia Software
---

### Post by Braik on 2010-04-06
Hi everybody,
 
I will explain my problem that is a little complex. I am little newbie with Linux since I am quite experienced with computers mostly M$, but wanting to leave the slavery of this editor I just started to use Ubuntu (regulary) like 3 months ago.
 
At the starting everything was going great, but recently I wanted to install a DVR so I tryed MythTv, everything was again working until the moment of tunning it and having a complete and definitive installation of it. At that moment the watch TV option just stoped to work. So I restarted a complete clean installation of MythTV, but (I don't know if is related) my Quickcam Pro 5000 just stoped to work.
 
I have searched in lot of forums and I was able to make this webcam work installing new drivers, v4l I think but I don't remember exactly. Up to this point I have restarted to install mythtv and sudenly my TVcard was not more visible, and this time I am almost sure that is related. I tryed some test like:
 
*scan /dev/dvb/dvb_t/ch-Citycable.conf*
 
and it tells me that /dev/dvb/adapter0/frontend0 is not found !!!!!
 
So I followed lot of other forums with commands like:
 
*lspci -v multimedia*
 
and it shows me that my PCI card is there but it tells me "access denied"
 
finally I do a:
 
*dmesg*
 
and it tells me that my chipset (saa7134, many entries) has unknown values.
 
Again following some forums I try to define values manualy:
 
*sudo modprobe saa7134 card=50 tuner=37*
 
And it tells me an error (don't remember which one, sorry I am on another computer)
 
Please help

---

### Post by Braik on 2010-04-06
So nobody?

Here are the outputs to:

[I]scan /dev/dvb/dvb_t/.....
[/I]> scanning /dev/dvb/dvb_t/.....
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory[I]lspci -v
[/I]> 01:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
    Subsystem: Pinnacle Systems Inc. Device 002d
    Flags: bus master, medium devsel, latency 32, IRQ 5
    Memory at fe9ff400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel modules: saa7134
[I]
dmesg[/I]
> [    0.000000] Initializing cgroup subsys cpuset
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  modified: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37867000 - 37fef175
[    0.000000] Allocated new RAMDISK: 008b2000 - 0103a175
[    0.000000] Move RAMDISK from 0000000037867000 - 0000000037fef174 to 008b2000 - 0103a174
[    0.000000] ACPI: RSDP 000f93d0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00034 (v01 A_M_I  OEMRSDT  08000721 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v02 A M I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb0440 05095 (v01  CRXR2 CRXR2203 00000203 INTL 02002026)
[    0.000000] ACPI: FACS 7ffc0000 00040
[    0.000000] ACPI: APIC 7ffb0390 0006C (v01 A_M_I  OEMAPIC  08000721 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 A_M_I  OEMMCFG  08000721 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffc0040 00046 (v01 A_M_I  AMI_OEM  08000721 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b112b]              BRK ==> [00008ae000 - 00008b112b]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008b2000 - 000103a175]      NEW RAMDISK ==> [00008b2000 - 000103a175]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c103b200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ed00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2045000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: root=UUID=4955d6e5-19bb-4322-b98f-f8092909abca ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2052120k/2096832k available (4578k kernel code, 43296k reserved, 2146k data, 540k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.336 MHz processor.
[    0.000826] Console: colour VGA+ 80x25
[    0.000830] console [tty0] enabled
[    0.000877] Calibrating delay loop (skipped), value calculated using timer frequency.. 3722.67 BogoMIPS (lpj=7445344)
[    0.000896] Security Framework initialized
[    0.000920] AppArmor: AppArmor initialized
[    0.000928] Mount-cache hash table entries: 512
[    0.001068] Initializing cgroup subsys ns
[    0.001073] Initializing cgroup subsys cpuacct
[    0.001077] Initializing cgroup subsys memory
[    0.001084] Initializing cgroup subsys freezer
[    0.001086] Initializing cgroup subsys net_cls
[    0.001102] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001105] CPU: L2 cache: 2048K
[    0.001108] CPU: Physical Processor ID: 0
[    0.001110] CPU: Processor Core ID: 0
[    0.001114] mce: CPU supports 6 MCE banks
[    0.001123] CPU0: Thermal monitoring enabled (TM2)
[    0.001127] using mwait in idle threads.
[    0.001134] Performance Counters: Core2 events, Intel PMU driver.
[    0.001143] ... version:                 2
[    0.001145] ... bit width:               40
[    0.001147] ... generic counters:        2
[    0.001149] ... value mask:              000000ffffffffff
[    0.001151] ... max period:              000000007fffffff
[    0.001153] ... fixed-purpose counters:  3
[    0.001155] ... counter mask:            0000000700000003
[    0.001159] Checking 'hlt' instruction... OK.
[    0.018699] ACPI: Core revision 20090521
[    0.026587] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066272] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[    0.068001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3723.28 BogoMIPS (lpj=7446575)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.153537] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[    0.153551] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.156025] Brought up 2 CPUs
[    0.156028] Total of 2 processors activated (7445.95 BogoMIPS).
[    0.156074] CPU0 attaching sched-domain:
[    0.156077]  domain 0: span 0-1 level MC
[    0.156080]   groups: 0 1
[    0.156086] CPU1 attaching sched-domain:
[    0.156088]  domain 0: span 0-1 level MC
[    0.156091]   groups: 1 0
[    0.156173] Booting paravirtualized kernel on bare hardware
[    0.156230] regulator: core version 0.5
[    0.156230] Time: 18:37:09  Date: 04/06/10
[    0.156230] NET: Registered protocol family 16
[    0.156230] EISA bus registered
[    0.156230] ACPI: bus type pci registered
[    0.156285] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support.
[    0.156291] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.156294] PCI: Not using MMCONFIG.
[    0.156461] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.156464] PCI: Using configuration type 1 for base access
[    0.157599] bio: create slab <bio-0> at 0
[    0.160667] ACPI: EC: Look up EC in DSDT
[    0.169349] ACPI: Interpreter enabled
[    0.169358] ACPI: (supports S0 S1 S3 S4 S5)
[    0.169382] ACPI: Using IOAPIC for interrupt routing
[    0.178335] ACPI Warning: Incorrect checksum in table [OEMB] - 03, should be F6 20090521 tbutils-246
[    0.178472] ACPI: No dock devices found.
[    0.178751] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.178860] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.178864] pci 0000:00:01.0: PME# disabled
[    0.178930] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f8000-0xfe8fbfff]
[    0.178975] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.178979] pci 0000:00:1b.0: PME# disabled
[    0.179038] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.179043] pci 0000:00:1c.0: PME# disabled
[    0.179107] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.179111] pci 0000:00:1c.4: PME# disabled
[    0.179172] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.179176] pci 0000:00:1c.5: PME# disabled
[    0.179223] pci 0000:00:1d.0: reg 20 io port: [0xb880-0xb89f]
[    0.179273] pci 0000:00:1d.1: reg 20 io port: [0xbc00-0xbc1f]
[    0.179324] pci 0000:00:1d.2: reg 20 io port: [0xc000-0xc01f]
[    0.179374] pci 0000:00:1d.3: reg 20 io port: [0xc080-0xc09f]
[    0.179430] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8ff800-0xfe8ffbff]
[    0.179483] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.179488] pci 0000:00:1d.7: PME# disabled
[    0.179613] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.179619] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.179623] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.179627] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0280 (mask 00ff)
[    0.179631] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0300 (mask 003f)
[    0.179676] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.179683] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.179690] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.179697] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.179704] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.179747] pci 0000:00:1f.2: reg 10 io port: [0xcc00-0xcc07]
[    0.179753] pci 0000:00:1f.2: reg 14 io port: [0xc880-0xc883]
[    0.179760] pci 0000:00:1f.2: reg 18 io port: [0xc800-0xc807]
[    0.179766] pci 0000:00:1f.2: reg 1c io port: [0xc480-0xc483]
[    0.179773] pci 0000:00:1f.2: reg 20 io port: [0xc400-0xc40f]
[    0.179779] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe8ffc00-0xfe8fffff]
[    0.179801] pci 0000:00:1f.2: PME# supported from D3hot
[    0.179805] pci 0000:00:1f.2: PME# disabled
[    0.179852] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.179906] pci 0000:05:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.179916] pci 0000:05:00.0: reg 18 64bit mmio: [0xfebe0000-0xfebeffff]
[    0.179922] pci 0000:05:00.0: reg 20 io port: [0xe000-0xe0ff]
[    0.179932] pci 0000:05:00.0: reg 30 32bit mmio: [0xfebc0000-0xfebdffff]
[    0.179952] pci 0000:05:00.0: supports D1 D2
[    0.179984] pci 0000:05:00.1: reg 10 64bit mmio: [0xfebf0000-0xfebfffff]
[    0.180024] pci 0000:05:00.1: supports D1 D2
[    0.180071] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.180075] pci 0000:00:01.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.180080] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.180130] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xcff00000-0xcfffffff]
[    0.180179] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xcfe00000-0xcfefffff]
[    0.180237] pci 0000:02:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.180260] pci 0000:02:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]
[    0.180284] pci 0000:02:00.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.180333] pci 0000:02:00.0: supports D1 D2
[    0.180336] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.180341] pci 0000:02:00.0: PME# disabled
[    0.180387] pci 0000:00:1c.5: bridge io port: [0xd000-0xdfff]
[    0.180391] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.180431] pci 0000:01:00.0: reg 10 32bit mmio: [0xfe9ff400-0xfe9ff7ff]
[    0.180481] pci 0000:01:00.0: supports D1 D2
[    0.180517] pci 0000:01:01.0: reg 10 32bit mmio: [0xfe9e0000-0xfe9effff]
[    0.180609] pci 0000:01:07.0: reg 10 32bit mmio: [0xfe9ff800-0xfe9fffff]
[    0.180617] pci 0000:01:07.0: reg 14 32bit mmio: [0xfe9f8000-0xfe9fbfff]
[    0.180663] pci 0000:01:07.0: supports D1 D2
[    0.180666] pci 0000:01:07.0: PME# supported from D0 D1 D2 D3hot
[    0.180671] pci 0000:01:07.0: PME# disabled
[    0.180711] pci 0000:00:1e.0: transparent bridge
[    0.180717] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.180743] pci_bus 0000:00: on NUMA node 0
[    0.180748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.180958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.181100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.181178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.181246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.190463] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.190580] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.190695] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.190809] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.190923] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.191039] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191152] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191266] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.191453] SCSI subsystem initialized
[    0.191474] libata version 3.00 loaded.
[    0.191474] usbcore: registered new interface driver usbfs
[    0.191474] usbcore: registered new interface driver hub
[    0.191474] usbcore: registered new device driver usb
[    0.191474] ACPI: WMI: Mapper loaded
[    0.191474] PCI: Using ACPI for IRQ routing
[    0.200008] Bluetooth: Core ver 2.15
[    0.200023] NET: Registered protocol family 31
[    0.200023] Bluetooth: HCI device and connection manager initialized
[    0.200023] Bluetooth: HCI socket layer initialized
[    0.200023] NetLabel: Initializing
[    0.200023] NetLabel:  domain hash size = 128
[    0.200023] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.200037] NetLabel:  unlabeled traffic allowed by default
[    0.200182] hpet clockevent registered
[    0.200185] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.200189] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.200195] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.216009] pnp: PnP ACPI init
[    0.216019] ACPI: bus type pnp registered
[    0.221285] pnp: PnP ACPI: found 18 devices
[    0.221287] ACPI: ACPI bus type pnp unregistered
[    0.221291] PnPBIOS: Disabled by ACPI PNP
[    0.221303] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.221313] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.221316] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.221319] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.221322] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.221326] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.221329] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.221335] system 00:0a: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.221346] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.221349] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.221357] system 00:0f: ioport range 0x290-0x29f has been reserved
[    0.221363] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[    0.221370] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[    0.221373] system 00:11: iomem range 0xc0000-0xcffff could not be reserved
[    0.221376] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[    0.221379] system 00:11: iomem range 0x100000-0x7fffffff could not be reserved
[    0.256047] AppArmor: AppArmor Filesystem Enabled
[    0.256101] pci 0000:00:01.0: PCI bridge, secondary bus 0000:05
[    0.256105] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.256109] pci 0000:00:01.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.256113] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.256118] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.256120] pci 0000:00:1c.0:   IO window: disabled
[    0.256125] pci 0000:00:1c.0:   MEM window: disabled
[    0.256129] pci 0000:00:1c.0:   PREFETCH window: 0x000000cff00000-0x000000cfffffff
[    0.256136] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.256138] pci 0000:00:1c.4:   IO window: disabled
[    0.256143] pci 0000:00:1c.4:   MEM window: disabled
[    0.256147] pci 0000:00:1c.4:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff
[    0.256153] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.256157] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.256162] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.256166] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.256171] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.256173] pci 0000:00:1e.0:   IO window: disabled
[    0.256178] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.256182] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.256193]   alloc irq_desc for 16 on node -1
[    0.256195]   alloc kstat_irqs on node -1
[    0.256200] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.256205] pci 0000:00:01.0: setting latency timer to 64
[    0.256213] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.256217] pci 0000:00:1c.0: setting latency timer to 64
[    0.256225] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.256229] pci 0000:00:1c.4: setting latency timer to 64
[    0.256236]   alloc irq_desc for 17 on node -1
[    0.256238]   alloc kstat_irqs on node -1
[    0.256242] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.256246] pci 0000:00:1c.5: setting latency timer to 64
[    0.256253] pci 0000:00:1e.0: setting latency timer to 64
[    0.256257] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.256260] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.256263] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.256266] pci_bus 0000:05: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.256269] pci_bus 0000:05: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.256272] pci_bus 0000:04: resource 2 pref mem [0xcff00000-0xcfffffff]
[    0.256275] pci_bus 0000:03: resource 2 pref mem [0xcfe00000-0xcfefffff]
[    0.256278] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.256281] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.256284] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.256286] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.256289] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.256325] NET: Registered protocol family 2
[    0.256433] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.256762] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257293] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.257531] TCP: Hash tables configured (established 131072 bind 65536)
[    0.257533] TCP reno registered
[    0.257614] NET: Registered protocol family 1
[    0.257678] Trying to unpack rootfs image as initramfs...
[    0.463850] Freeing initrd memory: 7712k freed
[    0.467572] cpufreq-nforce2: No nForce2 chipset.
[    0.467604] Scanning for low memory corruption every 60 seconds
[    0.467728] audit: initializing netlink socket (disabled)
[    0.467746] type=2000 audit(1270579029.464:1): initialized
[    0.477101] highmem bounce pool size: 64 pages
[    0.477107] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.478704] VFS: Disk quotas dquot_6.5.2
[    0.478772] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.479363] fuse init (API version 7.12)
[    0.479457] msgmni has been set to 1705
[    0.479695] alg: No test for stdrng (krng)
[    0.479710] io scheduler noop registered
[    0.479713] io scheduler anticipatory registered
[    0.479715] io scheduler deadline registered
[    0.479760] io scheduler cfq registered (default)
[    0.479859] pci 0000:05:00.0: Boot video device
[    0.479986]   alloc irq_desc for 24 on node -1
[    0.479988]   alloc kstat_irqs on node -1
[    0.479999] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.480006] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.480099]   alloc irq_desc for 25 on node -1
[    0.480101]   alloc kstat_irqs on node -1
[    0.480111] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.480120] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.480226]   alloc irq_desc for 26 on node -1
[    0.480228]   alloc kstat_irqs on node -1
[    0.480236] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.480244] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.480349]   alloc irq_desc for 27 on node -1
[    0.480351]   alloc kstat_irqs on node -1
[    0.480358] pcieport-driver 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.480366] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.480450] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.480472] Firmware did not grant requested _OSC control
[    0.480489] Firmware did not grant requested _OSC control
[    0.480502] Firmware did not grant requested _OSC control
[    0.480531] Firmware did not grant requested _OSC control
[    0.480544] Firmware did not grant requested _OSC control
[    0.480556] Firmware did not grant requested _OSC control
[    0.480571] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.480716] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.480721] ACPI: Power Button [PWRF]
[    0.480784] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.480787] ACPI: Power Button [PWRB]
[    0.481377] ACPI: SSDT 7ffc0090 001D2 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.481666] processor LNXCPU:00: registered as cooling_device0
[    0.481973] ACPI: SSDT 7ffc0270 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.482245] processor LNXCPU:01: registered as cooling_device1
[    0.485806] isapnp: Scanning for PnP cards...
[    0.701651] Switched to high resolution mode on CPU 1
[    0.704076] Switched to high resolution mode on CPU 0
[    0.839533] isapnp: No Plug & Play device found
[    0.840670] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.840772] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.841304] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.842414] brd: module loaded
[    0.842892] loop: module loaded
[    0.842961] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.843078] ata_piix 0000:00:1f.1: version 2.13
[    0.843090]   alloc irq_desc for 18 on node -1
[    0.843092]   alloc kstat_irqs on node -1
[    0.843099] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.843134] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.843203] scsi0 : ata_piix
[    0.843284] scsi1 : ata_piix
[    0.844788] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.844792] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.844815]   alloc irq_desc for 19 on node -1
[    0.844818]   alloc kstat_irqs on node -1
[    0.844822] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.844830] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.844869] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.844913] scsi2 : ata_piix
[    0.844979] scsi3 : ata_piix
[    0.844997] ata2: port disabled. ignoring.
[    0.845023] ata3: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 19
[    0.845026] ata4: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 19
[    0.846002] Fixed MDIO Bus: probed
[    0.846040] PPP generic driver version 2.4.2
[    0.846127] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.846144]   alloc irq_desc for 23 on node -1
[    0.846146]   alloc kstat_irqs on node -1
[    0.846151] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.846162] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.846166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.846200] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.846205] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.850109] ehci_hcd 0000:00:1d.7: debug port 1
[    0.850115] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.850128] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8ff800
[    0.864011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.864096] usb usb1: configuration #1 chosen from 1 choice
[    0.864126] hub 1-0:1.0: USB hub found
[    0.864134] hub 1-0:1.0: 8 ports detected
[    0.864197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.864215] uhci_hcd: USB Universal Host Controller Interface driver
[    0.864239] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.864245] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.864248] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.864278] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.864300] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b880
[    0.864375] usb usb2: configuration #1 chosen from 1 choice
[    0.864402] hub 2-0:1.0: USB hub found
[    0.864408] hub 2-0:1.0: 2 ports detected
[    0.864454] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.864460] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.864464] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.864492] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.864514] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bc00
[    0.864587] usb usb3: configuration #1 chosen from 1 choice
[    0.864614] hub 3-0:1.0: USB hub found
[    0.864620] hub 3-0:1.0: 2 ports detected
[    0.864668] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.864674] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.864677] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.864706] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.864735] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.864809] usb usb4: configuration #1 chosen from 1 choice
[    0.864838] hub 4-0:1.0: USB hub found
[    0.864845] hub 4-0:1.0: 2 ports detected
[    0.864888] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.864894] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.864897] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.864927] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.864956] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c080
[    0.865036] usb usb5: configuration #1 chosen from 1 choice
[    0.865066] hub 5-0:1.0: USB hub found
[    0.865073] hub 5-0:1.0: 2 ports detected
[    0.865187] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.867880] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.867886] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.867952] mice: PS/2 mouse device common for all mice
[    0.868065] rtc_cmos 00:03: RTC can wake from S4
[    0.868098] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.868124] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.868232] device-mapper: uevent: version 1.0.3
[    0.868316] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.868401] device-mapper: multipath: version 1.1.0 loaded
[    0.868404] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.868522] EISA: Probing bus 0 at eisa.0
[    0.868549] EISA: Detected 0 cards.
[    0.868641] cpuidle: using governor ladder
[    0.868643] cpuidle: using governor menu
[    0.869165] TCP cubic registered
[    0.869337] NET: Registered protocol family 10
[    0.869835] lo: Disabled Privacy Extensions
[    0.870202] NET: Registered protocol family 17
[    0.870219] Bluetooth: L2CAP ver 2.13
[    0.870221] Bluetooth: L2CAP socket layer initialized
[    0.870224] Bluetooth: SCO (Voice Link) ver 0.6
[    0.870226] Bluetooth: SCO socket layer initialized
[    0.870253] Bluetooth: RFCOMM TTY layer initialized
[    0.870257] Bluetooth: RFCOMM socket layer initialized
[    0.870259] Bluetooth: RFCOMM ver 1.11
[    0.870675] Using IPI No-Shortcut mode
[    0.870736] PM: Resume from disk failed.
[    0.870749] registered taskstats version 1
[    0.870877]   Magic number: 6:926:644
[    0.870940] rtc_cmos 00:03: setting system clock to 2010-04-06 18:37:10 UTC (1270579030)
[    0.870943] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.870945] EDD information not available.
[    0.893433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.016479] ata4.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    1.016483] ata4.00: 488397168 sectors, multi 16: LBA48 
[    1.016744] ata3.00: ATA-8: ST3500418AS, CC37, max UDMA/133
[    1.016747] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.024461] ata4.00: configured for UDMA/133
[    1.032390] ata3.00: configured for UDMA/133
[    1.176012] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.201138] ata1.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
[    1.201141] ata1.00: 117231408 sectors, multi 16: LBA 
[    1.201185] ata1.01: ATAPI: LITE-ON DVDRW LH-18A1H, HL06, max UDMA/66
[    1.217095] ata1.00: configured for UDMA/100
[    1.248208] ata1.01: configured for UDMA/66
[    1.250143] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
[    1.250263] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.250783] sd 0:0:0:0: [sda] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.251292] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LH-18A1H   HL06 PQ: 0 ANSI: 5
[    1.251312] sd 0:0:0:0: [sda] Write Protect is off
[    1.251315] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.251340] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.256359] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.256362] Uniform CD-ROM driver Revision: 3.20
[    1.256395]  sda:
[    1.256450] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.256492] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.256590] scsi 2:0:0:0: Direct-Access     ATA      ST3500418AS      CC37 PQ: 0 ANSI: 5
[    1.256693] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.256699] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.256746] sd 2:0:0:0: [sdb] Write Protect is off
[    1.256749] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.256775] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.256786] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    1.256896] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.256899]  sdb:
[    1.256984] sd 3:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.257032] sd 3:0:0:0: [sdc] Write Protect is off
[    1.257036] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.257060] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.257176]  sdc: sdb1
[    1.265435] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.268474]  sdc1
[    1.268651] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.276528]  sda1 sda2 < sda5 >
[    1.296593] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.296610] Freeing unused kernel memory: 540k freed
[    1.296910] Write protecting the kernel text: 4580k
[    1.296959] Write protecting the kernel read-only data: 1840k
[    1.416280] Linux agpgart interface v0.103
[    1.456158] usb 1-1: configuration #1 chosen from 1 choice
[    1.513550] [drm] Initialized drm 1.1.0 20060810
[    1.543631] [drm] radeon default to kernel modesetting DISABLED.
[    1.544183] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.544189] pci 0000:05:00.0: setting latency timer to 64
[    1.544315] [drm] Initialized radeon 1.31.0 20080528 for 0000:05:00.0 on minor 0
[    1.548565] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.548585] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.548629] r8169 0000:02:00.0: setting latency timer to 64
[    1.548689]   alloc irq_desc for 28 on node -1
[    1.548691]   alloc kstat_irqs on node -1
[    1.548707] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.549397] eth0: RTL8168b/8111b at 0xf82fc000, 00:13:8f:ab:52:8c, XID 30000000 IRQ 28
[    1.552855] Floppy drive(s): fd0 is 1.44M
[    1.556877]   alloc irq_desc for 22 on node -1
[    1.556881]   alloc kstat_irqs on node -1
[    1.556888] ohci1394 0000:01:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.575670] FDC 0 is a post-1991 82077
[    1.612549] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fe9ff800-fe9fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.688018] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    1.820427] usb 1-3: configuration #1 chosen from 1 choice
[    1.820692] hub 1-3:1.0: USB hub found
[    1.820743] hub 1-3:1.0: 2 ports detected
[    1.932021] usb 1-4: new high speed USB device using ehci_hcd and address 5
[    2.070410] usb 1-4: configuration #1 chosen from 1 choice
[    2.078289] Initializing USB Mass Storage driver...
[    2.080542] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.080676] usbcore: registered new interface driver usb-storage
[    2.080680] USB Mass Storage support registered.
[    2.080783] usb-storage: device found at 5
[    2.080785] usb-storage: waiting for device to settle before scanning
[    2.312010] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.411248] xor: automatically using best checksumming function: pIII_sse
[    2.428504]    pIII_sse  :  6614.000 MB/sec
[    2.428507] xor: using function: pIII_sse (6614.000 MB/sec)
[    2.430992] device-mapper: dm-raid45: initialized v0.2594b
[    2.507300] usb 2-2: configuration #1 chosen from 1 choice
[    2.512218] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.512345] usb-storage: device found at 2
[    2.512348] usb-storage: waiting for device to settle before scanning
[    2.713237] PM: Starting manual resume from disk
[    2.713242] PM: Resume from partition 8:5
[    2.713244] PM: Checking hibernation image.
[    2.713390] PM: Resume from disk failed.
[    2.753573] kjournald starting.  Commit interval 5 seconds
[    2.753580] EXT3-fs: mounted filesystem with writeback data mode.
[    2.884126] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[008f1300162e0000]
[    3.656673] type=1505 audit(1270579033.285:2): operation="profile_load" pid=477 name=/usr/share/gdm/guest-session/Xsession
[    3.681593] type=1505 audit(1270579033.309:3): operation="profile_load" pid=478 name=/sbin/dhclient3
[    3.682379] type=1505 audit(1270579033.309:4): operation="profile_load" pid=478 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.682804] type=1505 audit(1270579033.309:5): operation="profile_load" pid=478 name=/usr/lib/connman/scripts/dhclient-script
[    3.725632] type=1505 audit(1270579033.353:6): operation="profile_load" pid=479 name=/usr/bin/evince
[    3.738353] type=1505 audit(1270579033.365:7): operation="profile_load" pid=479 name=/usr/bin/evince-previewer
[    3.745787] type=1505 audit(1270579033.373:8): operation="profile_load" pid=479 name=/usr/bin/evince-thumbnailer
[    3.791981] type=1505 audit(1270579033.417:9): operation="profile_load" pid=481 name=/usr/lib/cups/backend/cups-pdf
[    3.792908] type=1505 audit(1270579033.421:10): operation="profile_load" pid=481 name=/usr/sbin/cupsd
[    7.080269] usb-storage: device scan complete
[    7.082126] scsi 4:0:0:0: Direct-Access     Hama     Card Reader   CF 1.9C PQ: 0 ANSI: 0 CCS
[    7.083995] scsi 4:0:0:1: Direct-Access     Hama     Card Reader   MS 1.9C PQ: 0 ANSI: 0 CCS
[    7.085870] scsi 4:0:0:2: Direct-Access     Hama     CardReaderMMC/SD 1.9C PQ: 0 ANSI: 0 CCS
[    7.087618] scsi 4:0:0:3: Direct-Access     Hama     Card Reader   SM 1.9C PQ: 0 ANSI: 0 CCS
[    7.088079] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    7.088177] sd 4:0:0:1: Attached scsi generic sg5 type 0
[    7.088274] sd 4:0:0:2: Attached scsi generic sg6 type 0
[    7.088370] sd 4:0:0:3: Attached scsi generic sg7 type 0
[    7.092849] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[    7.093853] sd 4:0:0:1: [sde] Attached SCSI removable disk
[    7.094724] sd 4:0:0:3: [sdg] Attached SCSI removable disk
[    7.095775] sd 4:0:0:2: [sdf] Attached SCSI removable disk
[    7.514898] usb-storage: device scan complete
[    7.628016] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[    7.904027] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[    8.188012] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[    8.464012] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[   20.457662] udev: starting version 147
[   20.490242] Adding 2433808k swap on /dev/sda5.  Priority:-1 extents:1 across:2433808k 
[   20.504869] intel_rng: FWH not detected
[   20.639175] Linux video capture interface: v2.00
[   20.644935] saa7134: Unknown symbol ir_codes_pinnacle_color
[   20.645189] saa7134: Unknown symbol ir_codes_avermedia
[   20.645557] saa7134: Unknown symbol ir_codes_flydvb
[   20.645918] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce
[   20.646012] saa7134: Unknown symbol ir_codes_gotview7135
[   20.646103] saa7134: Unknown symbol ir_codes_encore_enltv
[   20.646258] saa7134: Unknown symbol ir_codes_behold
[   20.646467] saa7134: Unknown symbol ir_codes_behold_columbus
[   20.646587] saa7134: Unknown symbol ir_codes_proteus_2309
[   20.646796] saa7134: Unknown symbol ir_codes_flyvideo
[   20.646965] saa7134: Unknown symbol ir_codes_eztv
[   20.647180] saa7134: Unknown symbol ir_codes_encore_enltv_fm53
[   20.647270] saa7134: Unknown symbol ir_codes_pixelview
[   20.647413] saa7134: Unknown symbol ir_codes_avermedia_a16d
[   20.647723] saa7134: Unknown symbol ir_rc5_timer_keyup
[   20.648048] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys
[   20.648138] saa7134: Unknown symbol ir_codes_asus_pc39
[   20.648323] saa7134: Unknown symbol ir_extract_bits
[   20.648414] saa7134: Unknown symbol ir_rc5_timer_end
[   20.648576] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus
[   20.649135] saa7134: Unknown symbol ir_input_init
[   20.649932] saa7134: Unknown symbol ir_codes_cinergy
[   20.650034] saa7134: Unknown symbol ir_input_nokey
[   20.650166] saa7134: Unknown symbol ir_codes_videomate_tv_pvr
[   20.650466] saa7134: Unknown symbol ir_codes_hauppauge_new
[   20.650842] saa7134: Unknown symbol ir_codes_pinnacle_grey
[   20.651046] saa7134: Unknown symbol ir_codes_purpletv
[   20.651449] saa7134: Unknown symbol ir_codes_pctv_sedna
[   20.651539] saa7134: Unknown symbol ir_codes_avermedia_m135a
[   20.651638] saa7134: Unknown symbol ir_input_keydown
[   20.651736] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog
[   20.651905] saa7134: Unknown symbol ir_codes_manli
[   20.662724] parport_pc 00:07: reported by Plug and Play ACPI
[   20.662780] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   20.686192] lp: driver loaded but no devices found
[   20.700404] EXT3 FS on sda1, internal journal
[   20.703551] saa7134: Unknown symbol ir_codes_pinnacle_color
[   20.703814] saa7134: Unknown symbol ir_codes_avermedia
[   20.704186] saa7134: Unknown symbol ir_codes_flydvb
[   20.704603] saa7134: Unknown symbol ir_codes_genius_tvgo_a11mce
[   20.704699] saa7134: Unknown symbol ir_codes_gotview7135
[   20.704791] saa7134: Unknown symbol ir_codes_encore_enltv
[   20.704948] saa7134: Unknown symbol ir_codes_behold
[   20.705161] saa7134: Unknown symbol ir_codes_behold_columbus
[   20.705284] saa7134: Unknown symbol ir_codes_proteus_2309
[   20.705497] saa7134: Unknown symbol ir_codes_flyvideo
[   20.705671] saa7134: Unknown symbol ir_codes_eztv
[   20.705887] saa7134: Unknown symbol ir_codes_encore_enltv_fm53
[   20.705979] saa7134: Unknown symbol ir_codes_pixelview
[   20.706124] saa7134: Unknown symbol ir_codes_avermedia_a16d
[   20.706440] saa7134: Unknown symbol ir_rc5_timer_keyup
[   20.706771] saa7134: Unknown symbol ir_codes_real_audio_220_32_keys
[   20.706862] saa7134: Unknown symbol ir_codes_asus_pc39
[   20.707049] saa7134: Unknown symbol ir_extract_bits
[   20.707141] saa7134: Unknown symbol ir_rc5_timer_end
[   20.707259] saa7134: Unknown symbol ir_codes_msi_tvanywhere_plus
[   20.707822] saa7134: Unknown symbol ir_input_init
[   20.708630] saa7134: Unknown symbol ir_codes_cinergy
[   20.708722] saa7134: Unknown symbol ir_input_nokey
[   20.708855] saa7134: Unknown symbol ir_codes_videomate_tv_pvr
[   20.709156] saa7134: Unknown symbol ir_codes_hauppauge_new
[   20.709535] saa7134: Unknown symbol ir_codes_pinnacle_grey
[   20.709743] saa7134: Unknown symbol ir_codes_purpletv
[   20.745619] saa7134: Unknown symbol ir_codes_pctv_sedna
[   20.745713] saa7134: Unknown symbol ir_codes_avermedia_m135a
[   20.745814] saa7134: Unknown symbol ir_input_keydown
[   20.745914] saa7134: Unknown symbol ir_codes_kworld_plus_tv_analog
[   20.746088] saa7134: Unknown symbol ir_codes_manli
[   20.755847] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.756087] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0161
[   20.756113] usbcore: registered new interface driver usblp
[   20.768709] lp0: using parport0 (interrupt-driven).
[   20.774780] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[   20.791681] ppdev: user-space parallel port driver
[   20.798265] input: UVC Camera (046d:08ce) as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input4
[   20.798326] usbcore: registered new interface driver uvcvideo
[   20.798330] USB Video Class driver (v0.1.0)
[   20.852046] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.852073] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.884745] psmouse serio1: ID: 10 00 64
[   20.885480] usbcore: registered new interface driver snd-usb-audio
[   20.928957] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   20.929149] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   20.960846] EXT4-fs (sdb1): barriers enabled
[   20.961042] kjournald2 starting: pid 991, dev sdb1:8, commit interval 5 seconds
[   20.961302] EXT4-fs (sdb1): internal journal on sdb1:8
[   20.961306] EXT4-fs (sdb1): delayed allocation enabled
[   20.961309] EXT4-fs: file extents enabled
[   20.984024] logips2pp: Detected unknown logitech mouse model 63
[   20.985617] EXT4-fs: mballoc enabled
[   20.985634] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   21.018698] EXT4-fs (sdc1): barriers enabled
[   21.018858] kjournald2 starting: pid 996, dev sdc1:8, commit interval 5 seconds
[   21.019072] EXT4-fs (sdc1): internal journal on sdc1:8
[   21.019076] EXT4-fs (sdc1): delayed allocation enabled
[   21.019080] EXT4-fs: file extents enabled
[   21.046516] EXT4-fs: mballoc enabled
[   21.046535] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[   21.595589] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   21.614048] r8169: eth0: link up
[   21.614054] r8169: eth0: link up
[   21.830935] __ratelimit: 9 callbacks suppressed
[   21.830938] type=1505 audit(1270571851.457:14): operation="profile_replace" pid=1246 name=/usr/share/gdm/guest-session/Xsession
[   21.832865] type=1505 audit(1270571851.461:15): operation="profile_replace" pid=1247 name=/sbin/dhclient3
[   21.833652] type=1505 audit(1270571851.461:16): operation="profile_replace" pid=1247 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.834078] type=1505 audit(1270571851.461:17): operation="profile_replace" pid=1247 name=/usr/lib/connman/scripts/dhclient-script
[   21.838246] type=1505 audit(1270571851.465:18): operation="profile_replace" pid=1248 name=/usr/bin/evince
[   21.852191] type=1505 audit(1270571851.481:19): operation="profile_replace" pid=1248 name=/usr/bin/evince-previewer
[   21.859625] type=1505 audit(1270571851.485:20): operation="profile_replace" pid=1248 name=/usr/bin/evince-thumbnailer
[   21.870906] type=1505 audit(1270571851.497:21): operation="profile_replace" pid=1250 name=/usr/lib/cups/backend/cups-pdf
[   21.871825] type=1505 audit(1270571851.497:22): operation="profile_replace" pid=1250 name=/usr/sbin/cupsd
[   21.874505] type=1505 audit(1270571851.501:23): operation="profile_replace" pid=1251 name=/usr/sbin/mysqld
[   24.586292] [drm] Setting GART location based on new memory map
[   24.587655] [drm] Loading R500 Microcode
[   24.587692] [drm] Num pipes: 1
[   24.587698] [drm] writeback test succeeded in 1 usecs
[   25.660545] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   32.068506] eth0: no IPv6 routers present
[   32.916020] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   40.928019] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   48.916018] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   56.928018] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   64.932018] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   72.932017] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   80.932017] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   88.932017] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[   89.107006] CPU0 attaching NULL sched-domain.
[   89.107011] CPU1 attaching NULL sched-domain.
[   89.124056] CPU0 attaching sched-domain:
[   89.124060]  domain 0: span 0-1 level MC
[   89.124063]   groups: 0 1
[   89.124068]   domain 1: span 0-1 level CPU
[   89.124071]    groups: 0-1 (__cpu_power = 2048)
[   89.124076] CPU1 attaching sched-domain:
[   89.124079]  domain 0: span 0-1 level MC
[   89.124081]   groups: 1 0
[   89.124085]   domain 1: span 0-1 level CPU
[   89.124088]    groups: 0-1 (__cpu_power = 2048)
[  121.929601] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[  144.386209] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  409.104548] usb 1-4: reset high speed USB device using ehci_hcd and address 5
[  602.100022] usb 1-4: reset high speed USB device using ehci_hcd and address 5*sudo modprobe saa7134 card=50 tuner=37*
> FATAL: Error inserting saa7134 (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134

Please I need some help

---

### Post by Braik on 2010-04-07
So, nobody want to help me? or nobody knows how to help me?
 
UP

---

