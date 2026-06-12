---
title: "Input levels show sound, but nothing heard"
date: 2010-02-02
forum: Multimedia Software
---

### Post by Fitch on 2010-02-02
I wanted to play music via the line in of my audio card and got nothing
I right clicked on the loudspeaker icon on the top of the screen and chose Sound preferences > Input
and the input level dances quite happily, showing that there is no problem there.

I type alsamixer on a command line, and now I only have the "Master" control showing whereas I used to have lots, including the line in, which was unmuted.

But I still don't have sound from the line in, even when I did have all the other volume controls showing.

so something has gone awry.

Any ideas?

---

### Post by Fitch on 2010-03-20
bump

---

### Post by hxcobd on 2010-03-20
Jump into Synaptic and download all of the PulseAudio packages that begin with PA. I think PAPREFS or PAVUCONTROL is the primary one you want.

That'll add PulseAudio Volume Control to your Applications -> Sound and Video menu. Tweak the settings in that, rather than alsamixer.

---

### Post by Fitch on 2010-03-21
paprefs is some network audio system
pavucontrol shows no soundcard either.
OSS is installed because of tkvoice for the answering machine (US Robotics sportster)
in the tkvoice audio setup, there is "ossdsp" "sunau" and an "other" button, but I don't know what to put into it as I think it os oss that has caused the problem.

I have completely remove all of alsa and all of pulse, the re-installed.  Still no AC97 sound card.

---

### Post by Fitch on 2010-03-22
To be more precise about Pulse Audio Volume Control.

It has "Dummy Output" for device, and in the configuration tab, it is empty with "There are no cards available for configuration"

I was giving up smoking, but the daily hypnosis file is on the hard drive with no way to listen to it any more.

I've restarted smoking..

---

### Post by Fitch on 2010-03-22
I did read somewhere that installing the latest linux generic and generic headers would work. 
Nope!

When I use alsaconf, everything is great, it finds the card, does its job and at the end says that it will now play a tune to check, and finishes with "Have a lot of fun"

but no tune ever comes...

lspci does see it:
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)

my dmesg is quite large and somewhat messy:

[    0.000000] Initializing cgroup subsys cpuset
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bbff0000 - 00000000bbff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbff3000 - 00000000bc000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bc000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbbff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 base 0100000000 mask FFC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bbff0000 (usable)
[    0.000000]  modified: 00000000bbff0000 - 00000000bbff3000 (ACPI NVS)
[    0.000000]  modified: 00000000bbff3000 - 00000000bc000000 (ACPI data)
[    0.000000]  modified: 00000000bc000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a1000 - 37fef6e5
[    0.000000] Allocated new RAMDISK: 008b2000 - 010006e5
[    0.000000] Move RAMDISK from 00000000378a1000 - 0000000037fef6e4 to 008b2000 - 010006e4
[    0.000000] ACPI: RSDP 000f7ee0 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT bbff3040 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: FACP bbff30c0 00074 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: DSDT bbff3180 06498 (v01 NVIDIA NVDAACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS bbff0000 00040
[    0.000000] ACPI: SSDT bbff9740 00206 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET bbff99c0 00038 (v01 Nvidia NVDAACPI 42302E31 NVDA 00000098)
[    0.000000] ACPI: MCFG bbff9a40 0003C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: APIC bbff9680 0007C (v01 Nvidia NVDAACPI 42302E31 NVDA 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2119MB HIGHMEM available.
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
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b11b9]              BRK ==> [00008ae000 - 00008b11b9]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008b2000 - 00010006e5]      NEW RAMDISK ==> [00008b2000 - 00010006e5]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f3d60] f3d60
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bbff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bbff0
[    0.000000] On node 0 totalpages: 769919
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4240 pages used for memmap
[    0.000000]   HighMem zone: 538466 pages, LIFO batch:31
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
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2791000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 763903
[    0.000000] Kernel command line: root=UUID=602dc57e-fedf-4205-b18f-3593554920c3 ro xforcevesa quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15400320 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bbff0)
[    0.000000] Memory: 3023280k/3080128k available (4578k kernel code, 55456k reserved, 2146k data, 540k init, 2170824k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2109.238 MHz processor.
[    0.000013] spurious 8259A interrupt: IRQ7.
[    0.003076] Console: colour VGA+ 80x25
[    0.003080] console [tty0] enabled
[    0.003266] hpet clockevent registered
[    0.003269] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.003276] Calibrating delay loop (skipped), value calculated using timer frequency.. 4218.47 BogoMIPS (lpj=8436952)
[    0.003299] Security Framework initialized
[    0.003325] AppArmor: AppArmor initialized
[    0.003332] Mount-cache hash table entries: 512
[    0.003484] Initializing cgroup subsys ns
[    0.003488] Initializing cgroup subsys cpuacct
[    0.003493] Initializing cgroup subsys memory
[    0.003499] Initializing cgroup subsys freezer
[    0.003502] Initializing cgroup subsys net_cls
[    0.003516] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.003519] CPU: L2 Cache: 512K (64 bytes/line)
[    0.003521] CPU: Physical Processor ID: 0
[    0.003523] CPU: Processor Core ID: 0
[    0.003527] mce: CPU supports 5 MCE banks
[    0.003538] using C1E aware idle routine
[    0.003547] Performance Counters: AMD PMU driver.
[    0.003553] ... version:                 0
[    0.003555] ... bit width:               48
[    0.003557] ... generic counters:        4
[    0.003559] ... value mask:              0000ffffffffffff
[    0.003561] ... max period:              00007fffffffffff
[    0.003563] ... fixed-purpose counters:  0
[    0.003565] ... counter mask:            000000000000000f
[    0.003569] Checking 'hlt' instruction... OK.
[    0.018187] ACPI: Core revision 20090521
[    0.028614] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070610] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4219.23 BogoMIPS (lpj=8438476)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.156517] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.156544] Brought up 2 CPUs
[    0.156546] Total of 2 processors activated (8437.71 BogoMIPS).
[    0.156648] CPU0 attaching sched-domain:
[    0.156651]  domain 0: span 0-1 level MC
[    0.156654]   groups: 0 1
[    0.156660] CPU1 attaching sched-domain:
[    0.156662]  domain 0: span 0-1 level MC
[    0.156664]   groups: 1 0
[    0.156735] Booting paravirtualized kernel on bare hardware
[    0.156735] regulator: core version 0.5
[    0.156735] Time: 18:09:25  Date: 03/22/10
[    0.156735] NET: Registered protocol family 16
[    0.156735] EISA bus registered
[    0.156735] ACPI: bus type pci registered
[    0.156735] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.156735] PCI: MCFG area at f0000000 reserved in E820
[    0.156735] PCI: Using MMCONFIG for extended config space
[    0.156735] PCI: Using configuration type 1 for base access
[    0.157216] bio: create slab <bio-0> at 0
[    0.157216] ACPI: EC: Look up EC in DSDT
[    0.168031] ACPI: Interpreter enabled
[    0.168035] ACPI: (supports S0 S1 S4 S5)
[    0.168058] ACPI: Using IOAPIC for interrupt routing
[    0.176863] ACPI: No dock devices found.
[    0.177825] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.178080] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178083] pci 0000:00:02.0: PME# disabled
[    0.178114] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178117] pci 0000:00:03.0: PME# disabled
[    0.178147] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178150] pci 0000:00:04.0: PME# disabled
[    0.178170] pci 0000:00:05.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.178176] pci 0000:00:05.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.178181] pci 0000:00:05.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
[    0.178186] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.178426] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.178431] pci 0000:00:0a.1: reg 24 io port: [0x1c40-0x1c7f]
[    0.178455] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.178461] pci 0000:00:0a.1: PME# disabled
[    0.178524] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.178552] pci 0000:00:0b.0: supports D1 D2
[    0.178554] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178558] pci 0000:00:0b.0: PME# disabled
[    0.178584] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
[    0.178613] pci 0000:00:0b.1: supports D1 D2
[    0.178615] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178619] pci 0000:00:0b.1: PME# disabled
[    0.178656] pci 0000:00:0d.0: reg 20 io port: [0xf400-0xf40f]
[    0.178697] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.178702] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.178706] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.178711] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.178716] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
[    0.178721] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.178767] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
[    0.178771] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
[    0.178776] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
[    0.178781] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
[    0.178786] pci 0000:00:0f.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.178791] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.178866] pci 0000:00:10.2: reg 10 io port: [0xc800-0xc8ff]
[    0.178871] pci 0000:00:10.2: reg 14 io port: [0xc400-0xc4ff]
[    0.178876] pci 0000:00:10.2: reg 18 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.178899] pci 0000:00:10.2: supports D1 D2
[    0.178928] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.178933] pci 0000:00:14.0: reg 14 io port: [0xc000-0xc007]
[    0.178956] pci 0000:00:14.0: supports D1 D2
[    0.178958] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.178962] pci 0000:00:14.0: PME# disabled
[    0.179073] pci 0000:00:02.0: bridge io port: [0x8000-0x8fff]
[    0.179077] pci 0000:00:02.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
[    0.179081] pci 0000:00:02.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
[    0.179118] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]
[    0.179121] pci 0000:00:03.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.179125] pci 0000:00:03.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.179165] pci 0000:00:04.0: bridge io port: [0x9000-0x9fff]
[    0.179168] pci 0000:00:04.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.179172] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
[    0.179206] pci 0000:04:07.0: reg 10 32bit mmio: [0xfdbff000-0xfdbff3ff]
[    0.179241] pci 0000:04:07.0: supports D1 D2
[    0.179270] pci 0000:00:10.0: transparent bridge
[    0.179273] pci 0000:00:10.0: bridge io port: [0xb000-0xbfff]
[    0.179277] pci 0000:00:10.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.179281] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
[    0.179290] pci_bus 0000:00: on NUMA node 0
[    0.179296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.179507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.240865] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.241009] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.241151] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.241293] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.241434] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.241580] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.241722] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[    0.241864] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.242007] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.242148] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.242291] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.242433] ACPI: PCI Interrupt Link [LACI] (IRQs *5 7 9 10 11 14 15)
[    0.242575] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.242718] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    0.242859] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.243002] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.243147] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.243289] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.243432] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.243575] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.243759] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.243937] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.244121] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.244298] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.244476] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.244652] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.244830] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.245007] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.245184] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.245363] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.245542] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.245720] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.245898] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.246077] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.246256] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.246435] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.246614] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.246792] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.246971] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.247150] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.247331] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.247535] SCSI subsystem initialized
[    0.247601] libata version 3.00 loaded.
[    0.247601] usbcore: registered new interface driver usbfs
[    0.247601] usbcore: registered new interface driver hub
[    0.247601] usbcore: registered new device driver usb
[    0.247601] ACPI: WMI: Mapper loaded
[    0.247601] PCI: Using ACPI for IRQ routing
[    0.260009] Bluetooth: Core ver 2.15
[    0.260025] NET: Registered protocol family 31
[    0.260025] Bluetooth: HCI device and connection manager initialized
[    0.260025] Bluetooth: HCI socket layer initialized
[    0.260025] NetLabel: Initializing
[    0.260025] NetLabel:  domain hash size = 128
[    0.260025] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.260039] NetLabel:  unlabeled traffic allowed by default
[    0.260073] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.260078] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.268028] Switched to high resolution mode on CPU 0
[    0.268557] Switched to high resolution mode on CPU 1
[    0.276024] pnp: PnP ACPI init
[    0.276045] ACPI: bus type pnp registered
[    0.282176] pnp: PnP ACPI: found 16 devices
[    0.282179] ACPI: ACPI bus type pnp unregistered
[    0.282183] PnPBIOS: Disabled by ACPI PNP
[    0.282196] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.282199] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.282202] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.282205] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.282208] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.282211] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.282214] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.282217] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.282221] system 00:01: iomem range 0xfec80000-0xfecbffff has been reserved
[    0.282224] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.282227] system 00:01: iomem range 0xbc000000-0xbfffffff has been reserved
[    0.282233] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.282236] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.282239] system 00:02: ioport range 0x290-0x299 has been reserved
[    0.282242] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.282251] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.282256] system 00:0f: iomem range 0xf0000-0xfffff could not be reserved
[    0.282259] system 00:0f: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.282263] system 00:0f: iomem range 0xbbff0000-0xbbffffff could not be reserved
[    0.282266] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[    0.282269] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.282272] system 00:0f: iomem range 0x100000-0xbbfeffff could not be reserved
[    0.282276] system 00:0f: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.282279] system 00:0f: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.282283] system 00:0f: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.282286] system 00:0f: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.282289] system 00:0f: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.282292] system 00:0f: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.316978] AppArmor: AppArmor Filesystem Enabled
[    0.317022] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.317025] pci 0000:00:02.0:   IO window: 0x8000-0x8fff
[    0.317029] pci 0000:00:02.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.317033] pci 0000:00:02.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.317037] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.317040] pci 0000:00:03.0:   IO window: 0xa000-0xafff
[    0.317043] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
[    0.317046] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.317050] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.317053] pci 0000:00:04.0:   IO window: 0x9000-0x9fff
[    0.317056] pci 0000:00:04.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.317059] pci 0000:00:04.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.317063] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.317066] pci 0000:00:10.0:   IO window: 0xb000-0xbfff
[    0.317071] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.317075] pci 0000:00:10.0:   PREFETCH window: 0xfda00000-0xfdafffff
[    0.317086] pci 0000:00:02.0: setting latency timer to 64
[    0.317091] pci 0000:00:03.0: setting latency timer to 64
[    0.317095] pci 0000:00:04.0: setting latency timer to 64
[    0.317100] pci 0000:00:10.0: setting latency timer to 64
[    0.317105] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.317108] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.317111] pci_bus 0000:01: resource 0 io:  [0x8000-0x8fff]
[    0.317114] pci_bus 0000:01: resource 1 mem: [0xfd800000-0xfd8fffff]
[    0.317116] pci_bus 0000:01: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    0.317119] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.317122] pci_bus 0000:02: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.317125] pci_bus 0000:02: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.317128] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]
[    0.317130] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.317133] pci_bus 0000:03: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.317136] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.317139] pci_bus 0000:04: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.317141] pci_bus 0000:04: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.317144] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.317147] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.317190] NET: Registered protocol family 2
[    0.317291] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.317648] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.318518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.318997] TCP: Hash tables configured (established 131072 bind 65536)
[    0.319000] TCP reno registered
[    0.319104] NET: Registered protocol family 1
[    0.319181] Trying to unpack rootfs image as initramfs...
[    0.522042] Freeing initrd memory: 7481k freed
[    0.528776] cpufreq-nforce2: No nForce2 chipset.
[    0.528803] Scanning for low memory corruption every 60 seconds
[    0.528919] audit: initializing netlink socket (disabled)
[    0.528938] type=2000 audit(1269281365.528:1): initialized
[    0.537715] highmem bounce pool size: 64 pages
[    0.537721] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.539088] VFS: Disk quotas dquot_6.5.2
[    0.539151] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.539841] fuse init (API version 7.12)
[    0.539940] msgmni has been set to 1681
[    0.540212] alg: No test for stdrng (krng)
[    0.540240] io scheduler noop registered
[    0.540242] io scheduler anticipatory registered
[    0.540244] io scheduler deadline registered
[    0.540289] io scheduler cfq registered (default)
[    0.540340] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.540363] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.540389] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.540396] pci 0000:00:05.0: Boot video device
[    0.556079] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.556087] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.556143] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.556151] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    0.556208] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.556214] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.556339]   alloc irq_desc for 24 on node -1
[    0.556341]   alloc kstat_irqs on node -1
[    0.556351] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.556356] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.556423]   alloc irq_desc for 25 on node -1
[    0.556425]   alloc kstat_irqs on node -1
[    0.556429] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.556433] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.556497]   alloc irq_desc for 26 on node -1
[    0.556499]   alloc kstat_irqs on node -1
[    0.556504] pcieport-driver 0000:00:04.0: irq 26 for MSI/MSI-X
[    0.556508] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    0.556565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.556591] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.556734] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.556738] ACPI: Power Button [PWRF]
[    0.556791] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.556794] ACPI: Power Button [PWRB]
[    0.556860] fan PNP0C0B:00: registered as cooling_device0
[    0.556866] ACPI: Fan [FAN] (on)
[    0.557261] processor LNXCPU:00: registered as cooling_device1
[    0.557300] processor LNXCPU:01: registered as cooling_device2
[    0.561770] thermal LNXTHERM:01: registered as thermal_zone0
[    0.561778] ACPI: Thermal Zone [THRM] (63 C)
[    0.561832] isapnp: Scanning for PnP cards...
[    0.914806] isapnp: No Plug & Play device found
[    0.915955] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.916094] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.916193] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.916459] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.917450] brd: module loaded
[    0.917892] loop: module loaded
[    0.917967] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.918192] sata_nv 0000:00:0e.0: version 3.5
[    0.918523] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.918531]   alloc irq_desc for 23 on node -1
[    0.918534]   alloc kstat_irqs on node -1
[    0.918546] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.918549] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.918603] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.918841] scsi0 : sata_nv
[    0.918956] scsi1 : sata_nv
[    0.919110] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    0.919113] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    0.919413] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.919416]   alloc irq_desc for 22 on node -1
[    0.919418]   alloc kstat_irqs on node -1
[    0.919427] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.919429] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    0.919471] sata_nv 0000:00:0f.0: setting latency timer to 64
[    0.919637] scsi2 : sata_nv
[    0.919703] scsi3 : sata_nv
[    0.919839] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
[    0.919843] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
[    0.919963] pata_amd 0000:00:0d.0: version 0.4.1
[    0.920034] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.920117] scsi4 : pata_amd
[    0.920177] scsi5 : pata_amd
[    0.920833] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    0.920837] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    0.921557] Fixed MDIO Bus: probed
[    0.921594] PPP generic driver version 2.4.2
[    0.921721] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.922026] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.922030]   alloc irq_desc for 21 on node -1
[    0.922032]   alloc kstat_irqs on node -1
[    0.922042] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.922055] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.922059] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.922091] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.922123] ehci_hcd 0000:00:0b.1: debug port 1
[    0.922128] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.922147] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    0.932015] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.932095] usb usb1: configuration #1 chosen from 1 choice
[    0.932126] hub 1-0:1.0: USB hub found
[    0.932136] hub 1-0:1.0: 8 ports detected
[    0.932196] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.932486] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.932490]   alloc irq_desc for 20 on node -1
[    0.932491]   alloc kstat_irqs on node -1
[    0.932500] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.932508] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.932510] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.932540] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.932569] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
[    0.990061] usb usb2: configuration #1 chosen from 1 choice
[    0.990084] hub 2-0:1.0: USB hub found
[    0.990101] hub 2-0:1.0: 8 ports detected
[    0.990154] uhci_hcd: USB Universal Host Controller Interface driver
[    0.990256] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.990620] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.990626] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.990709] mice: PS/2 mouse device common for all mice
[    0.990802] rtc_cmos 00:05: RTC can wake from S4
[    0.990836] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.990874] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.990994] device-mapper: uevent: version 1.0.3
[    0.991102] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.991214] device-mapper: multipath: version 1.1.0 loaded
[    0.991217] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.991374] EISA: Probing bus 0 at eisa.0
[    0.991381] Cannot allocate resource for EISA slot 1
[    0.991383] Cannot allocate resource for EISA slot 2
[    0.991399] Cannot allocate resource for EISA slot 8
[    0.991401] EISA: Detected 0 cards.
[    0.991526] cpuidle: using governor ladder
[    0.991529] cpuidle: using governor menu
[    0.992026] TCP cubic registered
[    0.992166] NET: Registered protocol family 10
[    0.992594] lo: Disabled Privacy Extensions
[    0.992896] NET: Registered protocol family 17
[    0.992919] Bluetooth: L2CAP ver 2.13
[    0.992921] Bluetooth: L2CAP socket layer initialized
[    0.992924] Bluetooth: SCO (Voice Link) ver 0.6
[    0.992926] Bluetooth: SCO socket layer initialized
[    0.992972] Bluetooth: RFCOMM TTY layer initialized
[    0.992975] Bluetooth: RFCOMM socket layer initialized
[    0.992977] Bluetooth: RFCOMM ver 1.11
[    0.993015] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)
[    0.993064] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
[    0.993067] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
[    0.993070] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
[    0.993073] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.993144] Using IPI No-Shortcut mode
[    0.993214] PM: Resume from disk failed.
[    0.993229] registered taskstats version 1
[    0.993380]   Magic number: 2:161:191
[    0.993454] acpi device:1d: hash matches
[    0.993508] rtc_cmos 00:05: setting system clock to 2010-03-22 18:09:26 UTC (1269281366)
[    0.993512] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.993514] EDD information not available.
[    1.009219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.084425] ata5.00: ATA-6: SAMSUNG SV4012H, RM100-08, max UDMA/100
[    1.084428] ata5.00: 78242976 sectors, multi 16: LBA 
[    1.084454] ata5: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (20:600:0x13)
[    1.093349] ata5.00: configured for UDMA/100
[    1.243454] ata3: SATA link down (SStatus 0 SControl 300)
[    1.384040] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.393268] ata1.00: ATA-7: WDC WD800JD-55MUA1, 10.01E01, max UDMA/133
[    1.393271] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.400284] ata1.00: configured for UDMA/133
[    1.400409] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-55MU 10.0 PQ: 0 ANSI: 5
[    1.400525] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.400565] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.400608] sd 0:0:0:0: [sda] Write Protect is off
[    1.400611] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.400632] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.400760]  sda: sda1
[    1.415767] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.660018] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    1.723454] ata2: SATA link down (SStatus 0 SControl 300)
[    1.884094] usb 2-1: configuration #1 chosen from 1 choice
[    2.043453] ata4: SATA link down (SStatus 0 SControl 300)
[    2.043535] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG SV4012H  RM10 PQ: 0 ANSI: 5
[    2.043640] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.043674] sd 4:0:0:0: [sdb] 78242976 512-byte logical blocks: (40.0 GB/37.3 GiB)
[    2.043712] sd 4:0:0:0: [sdb] Write Protect is off
[    2.043715] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.043735] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.043834]  sdb: sdb1 sdb2 < sdb5 >
[    2.086394] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.188013] usb 2-7: new full speed USB device using ohci_hcd and address 3
[    2.212339] ata6.00: ATAPI: _NEC DVD_RW ND-3540A, 1.04, max UDMA/33
[    2.212367] ata6.01: ATAPI: HL-DT-ST GCE-8400B, 1.02, max MWDMA2
[    2.212391] ata6: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc600c000) ACPI=0x701f (60:120:0x1b)
[    2.212397] ata6: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600c000) ACPI=0x39f (60:120:0x1b)
[    2.228288] ata6.00: configured for UDMA/33
[    2.244255] ata6.01: configured for MWDMA2
[    2.245679] scsi 5:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.04 PQ: 0 ANSI: 5
[    2.248624] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.248627] Uniform CD-ROM driver Revision: 3.20
[    2.248692] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.248730] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    2.248989] scsi 5:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  1.02 PQ: 0 ANSI: 5
[    2.250704] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.250766] sr 5:0:1:0: Attached scsi CD-ROM sr1
[    2.250801] sr 5:0:1:0: Attached scsi generic sg3 type 5
[    2.250832] Freeing unused kernel memory: 540k freed
[    2.251283] Write protecting the kernel text: 4580k
[    2.251320] Write protecting the kernel read-only data: 1840k
[    2.421127] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.421531] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.421538] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.421544] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.421601] nv_probe: set workaround bit for reversed mac addr
[    2.421613] usb 2-7: configuration #1 chosen from 1 choice
[    2.436505] Floppy drive(s): fd0 is 1.44M
[    2.460996] FDC 0 is a post-1991 82077
[    2.501169] Initializing USB Mass Storage driver...
[    2.503584] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.503715] usbcore: registered new interface driver usb-storage
[    2.503719] USB Mass Storage support registered.
[    2.503809] usb-storage: device found at 2
[    2.503811] usb-storage: waiting for device to settle before scanning
[    2.940874] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1c:25:34:d8:64
[    2.940880] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    3.543801] PM: Starting manual resume from disk
[    3.543806] PM: Resume from partition 8:21
[    3.543808] PM: Checking hibernation image.
[    3.544058] PM: Resume from disk failed.
[    3.573279] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.573283] EXT3-fs: write access will be enabled during recovery.
[    6.498099] kjournald starting.  Commit interval 5 seconds
[    6.498120] EXT3-fs: sdb1: orphan cleanup on readonly fs
[    6.498128] ext3_orphan_cleanup: deleting unreferenced inode 631335
[    6.498184] ext3_orphan_cleanup: deleting unreferenced inode 631334
[    6.498194] ext3_orphan_cleanup: deleting unreferenced inode 631011
[    6.498204] ext3_orphan_cleanup: deleting unreferenced inode 631010
[    6.498213] ext3_orphan_cleanup: deleting unreferenced inode 630967
[    6.498223] ext3_orphan_cleanup: deleting unreferenced inode 630965
[    6.498233] ext3_orphan_cleanup: deleting unreferenced inode 630964
[    6.498241] EXT3-fs: sdb1: 7 orphan inodes deleted
[    6.498243] EXT3-fs: recovery complete.
[    6.503425] EXT3-fs: mounted filesystem with writeback data mode.
[    7.456930] type=1505 audit(1269281372.959:2): operation="profile_load" pid=441 name=/usr/share/gdm/guest-session/Xsession
[    7.490128] type=1505 audit(1269281372.995:3): operation="profile_load" pid=442 name=/sbin/dhclient3
[    7.490414] type=1505 audit(1269281372.995:4): operation="profile_load" pid=442 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.490576] type=1505 audit(1269281372.995:5): operation="profile_load" pid=442 name=/usr/lib/connman/scripts/dhclient-script
[    7.506092] usb-storage: device scan complete
[    7.513075] scsi 6:0:0:0: Direct-Access     HP                        1.00 PQ: 0 ANSI: 2
[    7.513516] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    7.530746] type=1505 audit(1269281373.035:6): operation="profile_load" pid=443 name=/usr/bin/evince
[    7.535646] type=1505 audit(1269281373.039:7): operation="profile_load" pid=443 name=/usr/bin/evince-previewer
[    7.538519] type=1505 audit(1269281373.043:8): operation="profile_load" pid=443 name=/usr/bin/evince-thumbnailer
[    7.546066] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    7.587833] type=1505 audit(1269281373.091:9): operation="profile_load" pid=451 name=/usr/bin/freshclam
[   42.140319] udev: starting version 147
[   42.180780] Adding 1646620k swap on /dev/sdb5.  Priority:-1 extents:1 across:1646620k 
[   42.233714] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   42.233737] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   42.241303] Linux agpgart interface v0.103
[   42.257112] parport_pc 00:0b: reported by Plug and Play ACPI
[   42.257169] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.362598] nvidia: module license 'NVIDIA' taints kernel.
[   42.362607] Disabling lock debugging due to kernel taint
[   42.371155] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   42.373224] lp0: using parport0 (interrupt-driven).
[   42.391749] Linux video capture interface: v2.00
[   42.485466] saa7130/34: v4l2 driver version 0.2.15 loaded
[   42.485893] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   42.485899]   alloc irq_desc for 16 on node -1
[   42.485901]   alloc kstat_irqs on node -1
[   42.485914] saa7134 0000:04:07.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   42.485921] saa7134[0]: found at 0000:04:07.0, rev: 1, irq: 16, latency: 16, mmio: 0xfdbff000
[   42.485928] saa7134[0]: subsystem: 5168:0138, board: LifeView FlyVIDEO3000 [card=2,autodetected]
[   42.485949] saa7134[0]: board init: gpio is 38000
[   42.485952] saa7134[0]: there are different flyvideo cards with different tuners
[   42.485954] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[   42.485955] saa7134[0]: option to override the default value.
[   42.486023] input: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:10.0/0000:04:07.0/input/input4
[   42.486084] IRQ 16/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   42.490600] ppdev: user-space parallel port driver
[   42.493849] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.515845] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3B11
[   42.515875] usbcore: registered new interface driver usblp
[   42.628312] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   42.628320] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   42.628327] nvidia 0000:00:05.0: setting latency timer to 64
[   42.628621] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   42.647565] saa7134[0]: i2c eeprom 00: 68 51 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   42.647577] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647587] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647596] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647605] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647614] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647623] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647631] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647640] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647649] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647658] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647667] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647676] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647685] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647693] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647702] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.647714] i2c-adapter i2c-2: Invalid 7-bit address 0x7a
[   42.655680] irda_init()
[   42.655701] NET: Registered protocol family 23
[   42.660064] SigmaTel STIr4200 IRDA/USB found at address 3, Vendor: 66f, Product: 4200
[   42.660872] stir4200 2-7:1.0: IrDA: Registered SigmaTel device irda0
[   42.660898] usbcore: registered new interface driver stir4200
[   42.667579] EXT3 FS on sdb1, internal journal
[   42.670014] tuner 2-0061: chip found @ 0xc2 (saa7134[0])
[   42.691338] tuner-simple 2-0061: creating new instance
[   42.691344] tuner-simple 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   42.713193] saa7134[0]: registered device video0 [v4l2]
[   42.713224] saa7134[0]: registered device vbi0
[   42.713246] saa7134[0]: registered device radio0
[   42.786386] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   42.786392] saa7134_alsa: Unknown symbol snd_ctl_add
[   42.786487] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   42.786490] saa7134_alsa: Unknown symbol snd_pcm_new
[   42.787017] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   42.787019] saa7134_alsa: Unknown symbol snd_pcm_stop
[   42.787203] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   42.787206] saa7134_alsa: Unknown symbol snd_ctl_new1
[   42.787759] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   42.787762] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   42.788037] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   42.788039] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   42.788323] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   42.788326] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   42.788817] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   42.788819] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   42.788904] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   42.788907] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   42.817083] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   42.817089] saa7134_alsa: Unknown symbol snd_ctl_add
[   42.817184] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   42.817186] saa7134_alsa: Unknown symbol snd_pcm_new
[   42.817712] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   42.817714] saa7134_alsa: Unknown symbol snd_pcm_stop
[   42.817898] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   42.817900] saa7134_alsa: Unknown symbol snd_ctl_new1
[   42.818439] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   42.818441] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   42.818716] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   42.818718] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   42.818992] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   42.818995] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   42.819484] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   42.819487] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   42.819572] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   42.819574] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   42.910048] psmouse serio1: ID: 10 00 64
[   42.958042] type=1505 audit(1269281408.463:10): operation="profile_replace" pid=985 name=/usr/share/gdm/guest-session/Xsession
[   42.959944] type=1505 audit(1269281408.463:11): operation="profile_replace" pid=986 name=/sbin/dhclient3
[   42.960288] type=1505 audit(1269281408.463:12): operation="profile_replace" pid=986 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   42.960453] type=1505 audit(1269281408.463:13): operation="profile_replace" pid=986 name=/usr/lib/connman/scripts/dhclient-script
[   42.965776] type=1505 audit(1269281408.471:14): operation="profile_replace" pid=987 name=/usr/bin/evince
[   42.971077] type=1505 audit(1269281408.475:15): operation="profile_replace" pid=987 name=/usr/bin/evince-previewer
[   42.974106] type=1505 audit(1269281408.479:16): operation="profile_replace" pid=987 name=/usr/bin/evince-thumbnailer
[   42.979942] type=1505 audit(1269281408.483:17): operation="profile_replace" pid=989 name=/usr/bin/freshclam
[   42.984213] type=1505 audit(1269281408.487:18): operation="profile_load" pid=991 name=/usr/lib/cups/backend/cups-pdf
[   42.984571] type=1505 audit(1269281408.487:19): operation="profile_load" pid=991 name=/usr/sbin/cupsd
[   43.521249] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[   48.665222] usb 2-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   51.511658] __ratelimit: 9 callbacks suppressed
[   51.511663] type=1503 audit(1269281417.014:23): operation="open" pid=2129 parent=2128 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   51.656808] type=1503 audit(1269281417.162:24): operation="open" pid=2150 parent=2149 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   52.373611] type=1503 audit(1269281417.878:25): operation="open" pid=2273 parent=2157 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   52.778560] type=1503 audit(1269281418.283:26): operation="open" pid=2292 parent=2291 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   52.865924] type=1503 audit(1269281418.371:27): operation="open" pid=2303 parent=2302 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   53.149023] eth0: no IPv6 routers present
[   53.863036] bttv: driver version 0.9.18 loaded
[   53.863041] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  115.001029] Clocksource tsc unstable (delta = -169743556 ns)

---

### Post by Fitch on 2010-03-23
I've also seen a fix using:
emerge alsa-lib

No such thing as emerge now.  What has it been replaced by?

---

### Post by Fitch on 2010-03-23
Forget it..
Replaced the hard drive.
So far so good...

---

