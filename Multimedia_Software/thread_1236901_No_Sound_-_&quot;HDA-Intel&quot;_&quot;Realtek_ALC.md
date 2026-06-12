---
title: "No Sound - &quot;HDA-Intel&quot; &quot;Realtek ALC1200&quot;"
date: 2009-08-10
forum: Multimedia Software
---

### Post by slipdipper on 2009-08-10
For whatever reason my sound does not work. im looking to use the audio outputs (analog) from the back of my system. i have 6 plus spidf but im only using two. 

one interesting thing is that my sound does work if i boot off of the live cd, however i dont have video (unrelated issue) so i cant really troubleshoot from the live cd. 

yes, my sound is on, verified via alsamixer and the sound applet, and preferences, etc..etc...etc...

i do have headphone unchecked and IEC958 & IEC958 Default PCM checked in the volume control applet. 

i've also try this fix:

```

cat /etc/modprobe.d/hda_intel.conf
options snd-hda-intel model=auto probe_mask=1

```

and here:

```
 
tail -1 /etc/modprobe.d/alsa-base.conf 
options snd-hda-intel probe_mask=1

```

then finally this one which someone just told me to try:

```
 
tail -1 /etc/modprobe.d/alsa-base.conf 
options snd-hda-intel model=ref

```

i've been testing sound with the gnome sound config applet (system -> preference -> sound) and randomly with youtube videos...

also i followed everything on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

heres some config info:

mobo: evga 123-yw-e175 nforce 750i sli (no FTW)
ubuntu ver: 9.04

```

uname -a
Linux computer 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

```

```

dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009b800/0009b800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 (Ubuntu 2.6.28-14.47-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbfee0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b800 (usable)
[    0.000000]  modified: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfee0000 (usable)
[    0.000000]  modified: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfef0000 - 00000000bff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef02b
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fac02b
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef02a to 0087b000 - 00fac02a
[    0.000000] ACPI: RSDP 000F7D30, 0014 (r0 EVGA  )
[    0.000000] ACPI: RSDT BFEE3000, 0034 (r1 EVGA   NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP BFEE3080, 0074 (r1 EVGA   NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20080926]
[    0.000000] ACPI: DSDT BFEE3100, 5470 (r1 EVGA   NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS BFEE0000, 0040
[    0.000000] ACPI: HPET BFEE8640, 0038 (r1 EVGA   NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG BFEE8680, 003C (r1 EVGA   NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC BFEE8580, 0098 (r1 EVGA   NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2186MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009b800 - 0000100000]    BIOS reserved ==> [000009b800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fac02b]      NEW RAMDISK ==> [000087b000 - 0000fac02b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f3c90] 000f3c90
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bfee0
[    0.000000] On node 0 totalpages: 786027
[    0.000000] free_area_init_node: node 0, pgdat c06ca500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4374 pages used for memmap
[    0.000000]   HighMem zone: 555468 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
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
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bff00000:20100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779885
[    0.000000] Kernel command line: root=UUID=0fc5ea0c-8352-465f-8266-aa0ecadd087b ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2666.954 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15722560 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3087172k/3144576k available (4115k kernel code, 56020k reserved, 2196k data, 532k init, 2239368k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0504def - 0xc0729e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504def   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.90 BogoMIPS (lpj=10667816)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017919] ACPI: Core revision 20080926
[    0.018936] ACPI: Checking initramfs for custom DSDT
[    0.240524] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.283177] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz stepping 0b
[    0.284001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5333.25 BogoMIPS (lpj=10666501)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.368521] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz stepping 0b
[    0.368534] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.372105] Booting processor 2 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 5333.32 BogoMIPS (lpj=10666645)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.460498] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz stepping 0b
[    0.460509] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.464075] Booting processor 3 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 5333.29 BogoMIPS (lpj=10666585)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.552443] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz stepping 0b
[    0.552457] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.556023] Brought up 4 CPUs
[    0.556026] Total of 4 processors activated (21333.77 BogoMIPS).
[    0.556113] CPU0 attaching sched-domain:
[    0.556114]  domain 0: span 0-1 level MC
[    0.556116]   groups: 0 1
[    0.556120]   domain 1: span 0-3 level CPU
[    0.556121]    groups: 0-1 2-3
[    0.556126] CPU1 attaching sched-domain:
[    0.556127]  domain 0: span 0-1 level MC
[    0.556129]   groups: 1 0
[    0.556131]   domain 1: span 0-3 level CPU
[    0.556133]    groups: 0-1 2-3
[    0.556136] CPU2 attaching sched-domain:
[    0.556137]  domain 0: span 2-3 level MC
[    0.556139]   groups: 2 3
[    0.556141]   domain 1: span 0-3 level CPU
[    0.556143]    groups: 2-3 0-1
[    0.556146] CPU3 attaching sched-domain:
[    0.556148]  domain 0: span 2-3 level MC
[    0.556149]   groups: 3 2
[    0.556152]   domain 1: span 0-3 level CPU
[    0.556153]    groups: 2-3 0-1
[    0.556247] net_namespace: 776 bytes
[    0.556247] Booting paravirtualized kernel on bare hardware
[    0.556265] Time: 19:47:18  Date: 08/10/09
[    0.556265] regulator: core version 0.5
[    0.556265] NET: Registered protocol family 16
[    0.556265] EISA bus registered
[    0.556265] ACPI: bus type pci registered
[    0.556265] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.556265] PCI: MCFG area at e0000000 reserved in E820
[    0.556265] PCI: Using MMCONFIG for extended config space
[    0.556265] PCI: Using configuration type 1 for base access
[    0.556854] ACPI: EC: Look up EC in DSDT
[    0.565702] ACPI: Interpreter enabled
[    0.565711] ACPI: (supports S0 S1 S3 S4 S5)
[    0.565729] ACPI: Using IOAPIC for interrupt routing
[    0.572886] ACPI: No dock devices found.
[    0.572895] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.573650] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.573653] pci 0000:00:03.0: PME# disabled
[    0.573687] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.573689] pci 0000:00:07.0: PME# disabled
[    0.573909] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.573914] pci 0000:00:0a.1: reg 24 io port: [0x1c80-0x1cbf]
[    0.573927] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.573932] pci 0000:00:0a.1: PME# disabled
[    0.573998] pci 0000:00:0b.0: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.574024] pci 0000:00:0b.0: supports D1 D2
[    0.574025] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.574028] pci 0000:00:0b.0: PME# disabled
[    0.574055] pci 0000:00:0b.1: reg 10 32bit mmio: [0xdfffe000-0xdfffe0ff]
[    0.574080] pci 0000:00:0b.1: supports D1 D2
[    0.574082] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.574085] pci 0000:00:0b.1: PME# disabled
[    0.574125] pci 0000:00:0d.0: reg 20 io port: [0xfd00-0xfd0f]
[    0.574165] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
[    0.574169] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
[    0.574174] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
[    0.574178] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.574182] pci 0000:00:0e.0: reg 20 io port: [0xf800-0xf80f]
[    0.574187] pci 0000:00:0e.0: reg 24 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.574226] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
[    0.574230] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
[    0.574235] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
[    0.574239] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
[    0.574243] pci 0000:00:0f.0: reg 20 io port: [0xf300-0xf30f]
[    0.574248] pci 0000:00:0f.0: reg 24 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.574321] pci 0000:00:10.1: reg 10 32bit mmio: [0xdfff4000-0xdfff7fff]
[    0.574347] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.574350] pci 0000:00:10.1: PME# disabled
[    0.574384] pci 0000:00:14.0: reg 10 32bit mmio: [0xdfffb000-0xdfffbfff]
[    0.574388] pci 0000:00:14.0: reg 14 io port: [0xf200-0xf207]
[    0.574408] pci 0000:00:14.0: supports D1 D2
[    0.574410] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.574413] pci 0000:00:14.0: PME# disabled
[    0.574460] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    0.574463] pci 0000:01:00.0: PME# disabled
[    0.574507] pci 0000:00:03.0: bridge io port: [0xd000-0xdfff]
[    0.574510] pci 0000:00:03.0: bridge 32bit mmio: [0xda000000-0xddffffff]
[    0.574514] pci 0000:00:03.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.574546] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.574549] pci 0000:02:00.0: PME# disabled
[    0.574584] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.574587] pci 0000:02:02.0: PME# disabled
[    0.574619] pci 0000:01:00.0: bridge io port: [0xd000-0xdfff]
[    0.574622] pci 0000:01:00.0: bridge 32bit mmio: [0xda000000-0xddffffff]
[    0.574627] pci 0000:01:00.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.574660] pci 0000:03:00.0: reg 10 32bit mmio: [0xdc000000-0xdcffffff]
[    0.574671] pci 0000:03:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.574681] pci 0000:03:00.0: reg 1c 64bit mmio: [0xda000000-0xdbffffff]
[    0.574687] pci 0000:03:00.0: reg 24 io port: [0xdf00-0xdf7f]
[    0.574693] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.574741] pci 0000:02:00.0: bridge io port: [0xd000-0xdfff]
[    0.574744] pci 0000:02:00.0: bridge 32bit mmio: [0xda000000-0xddffffff]
[    0.574749] pci 0000:02:00.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.574876] pci 0000:06:07.0: reg 10 32bit mmio: [0xdfeff000-0xdfeff7ff]
[    0.574882] pci 0000:06:07.0: reg 14 32bit mmio: [0xdfef8000-0xdfefbfff]
[    0.574911] pci 0000:06:07.0: supports D1 D2
[    0.574912] pci 0000:06:07.0: PME# supported from D0 D1 D2 D3hot
[    0.574916] pci 0000:06:07.0: PME# disabled
[    0.574937] pci 0000:06:0a.0: reg 10 io port: [0xef00-0xef07]
[    0.574942] pci 0000:06:0a.0: reg 14 io port: [0xee00-0xee07]
[    0.574948] pci 0000:06:0a.0: reg 18 io port: [0xed00-0xed07]
[    0.574954] pci 0000:06:0a.0: reg 1c io port: [0xec00-0xec07]
[    0.574959] pci 0000:06:0a.0: reg 20 io port: [0xeb00-0xeb07]
[    0.574965] pci 0000:06:0a.0: reg 24 io port: [0xea00-0xea0f]
[    0.574998] pci 0000:00:10.0: transparent bridge
[    0.575001] pci 0000:00:10.0: bridge io port: [0xe000-0xefff]
[    0.575003] pci 0000:00:10.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.575014] bus 00 -> node 0
[    0.575020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.575310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.633219] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633355] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633491] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[    0.633625] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.633759] ACPI: PCI Interrupt Link [LNK5] (IRQs *5 7 9 10 11 14 15)
[    0.633892] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634025] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634158] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634293] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.634429] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634564] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.634697] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634832] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.634964] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.635098] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.635232] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.635366] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.635498] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.635632] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.635769] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.635934] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.636108] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.636268] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.636426] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.636584] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.636743] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.636901] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.637070] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.637229] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.637389] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[    0.637548] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.637708] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[    0.637867] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[    0.638026] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.638185] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    0.638345] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.638503] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.638665] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.638825] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.638984] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.639143] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
[    0.639247] ACPI: WMI: Mapper loaded
[    0.639280] SCSI subsystem initialized
[    0.639280] libata version 3.00 loaded.
[    0.639280] usbcore: registered new interface driver usbfs
[    0.639280] usbcore: registered new interface driver hub
[    0.639280] usbcore: registered new device driver usb
[    0.639280] PCI: Using ACPI for IRQ routing
[    0.644012] Bluetooth: Core ver 2.13
[    0.644028] NET: Registered protocol family 31
[    0.644028] Bluetooth: HCI device and connection manager initialized
[    0.644028] Bluetooth: HCI socket layer initialized
[    0.644028] NET: Registered protocol family 8
[    0.644030] NET: Registered protocol family 20
[    0.644042] NetLabel: Initializing
[    0.644044] NetLabel:  domain hash size = 128
[    0.644046] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.644061] NetLabel:  unlabeled traffic allowed by default
[    0.644093] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.644096] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.652065] AppArmor: AppArmor Filesystem Enabled
[    0.656010] Switched to high resolution mode on CPU 0
[    0.656578] Switched to high resolution mode on CPU 1
[    0.657058] Switched to high resolution mode on CPU 3
[    0.657105] Switched to high resolution mode on CPU 2
[    0.659856] pnp: PnP ACPI init
[    0.659866] ACPI: bus type pnp registered
[    0.663504] pnp: PnP ACPI: found 13 devices
[    0.663505] ACPI: ACPI bus type pnp unregistered
[    0.663508] PnPBIOS: Disabled by ACPI PNP
[    0.663514] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.663516] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.663518] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.663520] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.663522] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.663524] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.663528] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.663530] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.663532] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.663538] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.663543] system 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[    0.663545] system 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.663547] system 00:0c: iomem range 0xbfee0000-0xbfefffff could not be reserved
[    0.663549] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.663551] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.663553] system 00:0c: iomem range 0x100000-0xbfedffff could not be reserved
[    0.663555] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.663556] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.663558] system 00:0c: iomem range 0xfeff0000-0xfeff03ff could not be reserved
[    0.698223] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
[    0.698226] pci 0000:02:00.0:   IO window: 0xd000-0xdfff
[    0.698230] pci 0000:02:00.0:   MEM window: 0xda000000-0xddffffff
[    0.698233] pci 0000:02:00.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.698238] pci 0000:02:02.0: PCI bridge, secondary bus 0000:04
[    0.698240] pci 0000:02:02.0:   IO window: disabled
[    0.698243] pci 0000:02:02.0:   MEM window: disabled
[    0.698246] pci 0000:02:02.0:   PREFETCH window: disabled
[    0.698251] pci 0000:01:00.0: PCI bridge, secondary bus 0000:02
[    0.698254] pci 0000:01:00.0:   IO window: 0xd000-0xdfff
[    0.698257] pci 0000:01:00.0:   MEM window: 0xda000000-0xddffffff
[    0.698261] pci 0000:01:00.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.698266] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.698268] pci 0000:00:03.0:   IO window: 0xd000-0xdfff
[    0.698270] pci 0000:00:03.0:   MEM window: 0xda000000-0xddffffff
[    0.698273] pci 0000:00:03.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.698276] pci 0000:00:07.0: PCI bridge, secondary bus 0000:05
[    0.698278] pci 0000:00:07.0:   IO window: disabled
[    0.698280] pci 0000:00:07.0:   MEM window: disabled
[    0.698283] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.698286] pci 0000:00:10.0: PCI bridge, secondary bus 0000:06
[    0.698288] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.698292] pci 0000:00:10.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.698295] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.698304] pci 0000:00:03.0: setting latency timer to 64
[    0.698310] pci 0000:01:00.0: setting latency timer to 64
[    0.698317] pci 0000:02:00.0: setting latency timer to 64
[    0.698324] pci 0000:02:02.0: setting latency timer to 64
[    0.698330] pci 0000:00:07.0: setting latency timer to 64
[    0.698334] pci 0000:00:10.0: setting latency timer to 64
[    0.698337] bus: 00 index 0 io port: [0x00-0xffff]
[    0.698338] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.698340] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.698342] bus: 01 index 1 mmio: [0xda000000-0xddffffff]
[    0.698343] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.698345] bus: 01 index 3 mmio: [0x0-0x0]
[    0.698346] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.698348] bus: 02 index 1 mmio: [0xda000000-0xddffffff]
[    0.698349] bus: 02 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.698351] bus: 02 index 3 mmio: [0x0-0x0]
[    0.698352] bus: 03 index 0 io port: [0xd000-0xdfff]
[    0.698354] bus: 03 index 1 mmio: [0xda000000-0xddffffff]
[    0.698355] bus: 03 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.698356] bus: 03 index 3 mmio: [0x0-0x0]
[    0.698358] bus: 04 index 0 mmio: [0x0-0x0]
[    0.698359] bus: 04 index 1 mmio: [0x0-0x0]
[    0.698361] bus: 04 index 2 mmio: [0x0-0x0]
[    0.698362] bus: 04 index 3 mmio: [0x0-0x0]
[    0.698363] bus: 05 index 0 mmio: [0x0-0x0]
[    0.698364] bus: 05 index 1 mmio: [0x0-0x0]
[    0.698366] bus: 05 index 2 mmio: [0x0-0x0]
[    0.698367] bus: 05 index 3 mmio: [0x0-0x0]
[    0.698368] bus: 06 index 0 io port: [0xe000-0xefff]
[    0.698370] bus: 06 index 1 mmio: [0xdfe00000-0xdfefffff]
[    0.698371] bus: 06 index 2 mmio: [0x0-0x0]
[    0.698373] bus: 06 index 3 io port: [0x00-0xffff]
[    0.698374] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.698380] NET: Registered protocol family 2
[    0.712082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.712279] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.712543] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.712682] TCP: Hash tables configured (established 131072 bind 65536)
[    0.712683] TCP reno registered
[    0.720101] NET: Registered protocol family 1
[    0.720210] checking if image is initramfs... it is
[    1.168911] Freeing initrd memory: 7364k freed
[    1.169236] cpufreq: No nForce2 chipset.
[    1.169334] audit: initializing netlink socket (disabled)
[    1.169348] type=2000 audit(1249933638.168:1): initialized
[    1.174670] highmem bounce pool size: 64 pages
[    1.174673] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.175725] VFS: Disk quotas dquot_6.5.1
[    1.175785] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.176240] fuse init (API version 7.10)
[    1.176336] msgmni has been set to 1672
[    1.176571] alg: No test for stdrng (krng)
[    1.176591] io scheduler noop registered
[    1.176593] io scheduler anticipatory registered
[    1.176594] io scheduler deadline registered
[    1.176609] io scheduler cfq registered (default)
[    1.176749] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<4>pci 0000:00:0b.0: OHCI: BIOS handoff failed (BIOS bug?) 00000784
[    9.976016] pci 0000:00:0b.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    9.976154] pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<6>pci 0000:00:10.1: Disabling HT MSI mapping<7>pci 0000:03:00.0: Boot video device
[    9.981311] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    9.981343] pcieport-driver 0000:00:03.0: found MSI capability
[    9.981362] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    9.981369] pci_express 0000:00:03.0:pcie00: allocate port service
[    9.981379] pci_express 0000:00:03.0:pcie03: allocate port service
[    9.981419] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    9.981449] pcieport-driver 0000:00:07.0: found MSI capability
[    9.981465] pcieport-driver 0000:00:07.0: irq 2302 for MSI/MSI-X
[    9.981472] pci_express 0000:00:07.0:pcie00: allocate port service
[    9.981481] pci_express 0000:00:07.0:pcie03: allocate port service
[    9.981535] pcieport-driver 0000:01:00.0: setting latency timer to 64
[    9.981603] pcieport-driver 0000:02:00.0: setting latency timer to 64
[    9.981666] pcieport-driver 0000:02:02.0: setting latency timer to 64
[    9.981734] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.981742] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    9.981867] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    9.981869] ACPI: Power Button (FF) [PWRF]
[    9.981899] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    9.981900] ACPI: Power Button (CM) [PWRB]
[    9.981947] fan PNP0C0B:00: registered as cooling_device0
[    9.981951] ACPI: Fan [FAN] (on)
[    9.982194] processor ACPI_CPU:00: registered as cooling_device1
[    9.982220] processor ACPI_CPU:01: registered as cooling_device2
[    9.982245] processor ACPI_CPU:02: registered as cooling_device3
[    9.982271] processor ACPI_CPU:03: registered as cooling_device4
[    9.985624] thermal LNXTHERM:01: registered as thermal_zone0
[    9.985936] ACPI: Thermal Zone [THRM] (40 C)
[    9.985975] isapnp: Scanning for PnP cards...
[   10.338937] isapnp: No Plug & Play device found
[   10.345722] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   10.345819] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.346144] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.346692] brd: module loaded
[   10.346908] loop: module loaded
[   10.346958] Fixed MDIO Bus: probed
[   10.346962] PPP generic driver version 2.4.2
[   10.347000] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[   10.347019] Driver 'sd' needs updating - please use bus_type methods
[   10.347026] Driver 'sr' needs updating - please use bus_type methods
[   10.347177] sata_nv 0000:00:0e.0: version 3.5
[   10.347427] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   10.347432] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[   10.347434] sata_nv 0000:00:0e.0: Using SWNCQ mode
[   10.347472] sata_nv 0000:00:0e.0: setting latency timer to 64
[   10.347592] scsi0 : sata_nv
[   10.347693] scsi1 : sata_nv
[   10.347875] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
[   10.347879] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
[   11.224036] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.271692] ata1.00: ATA-7: ST3750640AS, 3.AAK, max UDMA/133
[   11.271696] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   11.338334] ata1.00: configured for UDMA/133
[   12.070447] ata2: SATA link down (SStatus 0 SControl 300)
[   12.070548] scsi 0:0:0:0: Direct-Access     ATA      ST3750640AS      3.AA PQ: 0 ANSI: 5
[   12.070613] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[   12.070625] sd 0:0:0:0: [sda] Write Protect is off
[   12.070626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.070644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.070685] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[   12.070695] sd 0:0:0:0: [sda] Write Protect is off
[   12.070696] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.070713] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.070716]  sda: sda1 sda2 sda3
[   12.108018] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.108072] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.108389] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   12.108394] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[   12.108396] sata_nv 0000:00:0f.0: Using SWNCQ mode
[   12.108446] sata_nv 0000:00:0f.0: setting latency timer to 64
[   12.108557] scsi2 : sata_nv
[   12.108633] scsi3 : sata_nv
[   12.108764] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 23
[   12.108766] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 23
[   12.988036] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   12.996489] ata3.00: ATA-8: ST31500341AS, SD17, max UDMA/133
[   12.996492] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (not used)
[   12.996508] ata3.00: WARNING: device requires firmware update to be fully functional.
[   12.996511] ata3.00:          contact the vendor or visit http://ata.wiki.kernel.org.
[   13.012485] ata3.00: configured for UDMA/133
[   13.892035] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.900480] ata4.00: ATA-8: ST31500341AS, SD17, max UDMA/133
[   13.900483] ata4.00: 2930277168 sectors, multi 16: LBA48 NCQ (not used)
[   13.900499] ata4.00: WARNING: device requires firmware update to be fully functional.
[   13.900501] ata4.00:          contact the vendor or visit http://ata.wiki.kernel.org.
[   13.916477] ata4.00: configured for UDMA/133
[   13.916577] scsi 2:0:0:0: Direct-Access     ATA      ST31500341AS     SD17 PQ: 0 ANSI: 5
[   13.916656] sd 2:0:0:0: [sdb] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
[   13.916667] sd 2:0:0:0: [sdb] Write Protect is off
[   13.916669] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   13.916687] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.916727] sd 2:0:0:0: [sdb] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
[   13.916737] sd 2:0:0:0: [sdb] Write Protect is off
[   13.916739] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   13.916756] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.916758]  sdb: sdb1
[   13.933257] sd 2:0:0:0: [sdb] Attached SCSI disk
[   13.933308] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   13.933357] scsi 3:0:0:0: Direct-Access     ATA      ST31500341AS     SD17 PQ: 0 ANSI: 5
[   13.933413] sd 3:0:0:0: [sdc] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
[   13.933423] sd 3:0:0:0: [sdc] Write Protect is off
[   13.933425] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   13.933442] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.933476] sd 3:0:0:0: [sdc] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
[   13.933486] sd 3:0:0:0: [sdc] Write Protect is off
[   13.933487] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   13.933504] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.933507]  sdc: sdc1
[   13.943923] sd 3:0:0:0: [sdc] Attached SCSI disk
[   13.943967] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   13.944067] pata_amd 0000:00:0d.0: version 0.3.10
[   13.944095] pata_amd 0000:00:0d.0: setting latency timer to 64
[   13.944183] scsi4 : pata_amd
[   13.944251] scsi5 : pata_amd
[   13.944708] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
[   13.944710] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
[   14.108327] ata5.00: ATAPI: _NEC DVD_RW ND-3520AW, 3.05, max UDMA/33
[   14.108347] ata5: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[   14.124287] ata5.00: configured for UDMA/33
[   14.125385] ata6: port disabled. ignoring.
[   14.127781] scsi 4:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520AW 3.05 PQ: 0 ANSI: 5
[   14.129088] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   14.129091] Uniform CD-ROM driver Revision: 3.20
[   14.129200] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   14.129236] sr 4:0:0:0: Attached scsi generic sg3 type 5
[   14.129639] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   14.129893] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   14.129899] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[   14.129909] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[   14.129911] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   14.129955] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   14.129979] ehci_hcd 0000:00:0b.1: debug port 1
[   14.129983] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[   14.129996] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xdfffe000
[   14.140015] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[   14.140094] usb usb1: configuration #1 chosen from 1 choice
[   14.140127] hub 1-0:1.0: USB hub found
[   14.140136] hub 1-0:1.0: 8 ports detected
[   14.140217] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.140466] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   14.140470] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[   14.140478] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[   14.140480] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   14.140510] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   14.140527] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xdffff000
[   14.198034] usb usb2: configuration #1 chosen from 1 choice
[   14.198051] hub 2-0:1.0: USB hub found
[   14.198059] hub 2-0:1.0: 8 ports detected
[   14.198131] uhci_hcd: USB Universal Host Controller Interface driver
[   14.198190] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   14.198192] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   14.198671] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.200060] mice: PS/2 mouse device common for all mice
[   14.212103] rtc_cmos 00:05: RTC can wake from S4
[   14.212143] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   14.212187] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[   14.212228] device-mapper: uevent: version 1.0.3
[   14.212333] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   14.212482] device-mapper: multipath: version 1.0.5 loaded
[   14.212484] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.212589] EISA: Probing bus 0 at eisa.0
[   14.212598] Cannot allocate resource for EISA slot 1
[   14.212617] EISA: Detected 0 cards.
[   14.212739] cpuidle: using governor ladder
[   14.212740] cpuidle: using governor menu
[   14.213106] TCP cubic registered
[   14.213180] NET: Registered protocol family 10
[   14.213487] lo: Disabled Privacy Extensions
[   14.213717] NET: Registered protocol family 17
[   14.213729] Bluetooth: L2CAP ver 2.11
[   14.213730] Bluetooth: L2CAP socket layer initialized
[   14.213733] Bluetooth: SCO (Voice Link) ver 0.6
[   14.213734] Bluetooth: SCO socket layer initialized
[   14.213784] Bluetooth: RFCOMM socket layer initialized
[   14.213794] Bluetooth: RFCOMM TTY layer initialized
[   14.213796] Bluetooth: RFCOMM ver 1.10
[   14.213883] Using IPI No-Shortcut mode
[   14.213942] registered taskstats version 1
[   14.214069]   Magic number: 5:16:799
[   14.214139] rtc_cmos 00:05: setting system clock to 2009-08-10 19:47:32 UTC (1249933652)
[   14.214142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.214143] EDD information not available.
[   14.214329] Freeing unused kernel memory: 532k freed
[   14.214431] Write protecting the kernel text: 4116k
[   14.214464] Write protecting the kernel read-only data: 1524k
[   14.249750] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   14.405286] FDC 0 is a post-1991 82077
[   14.433404] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   14.433412] ohci1394 0000:06:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   14.433421] ohci1394 0000:06:07.0: setting latency timer to 64
[   14.479149] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   14.479474] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   14.479482] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[   14.479491] forcedeth 0000:00:14.0: setting latency timer to 64
[   14.479537] nv_probe: set workaround bit for reversed mac addr
[   14.483176] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfeff000-dfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.756154] usb 2-6: new full speed USB device using ohci_hcd and address 2
[   14.998510] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:bc:07:b1:3c
[   14.998512] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   15.014040] usb 2-6: configuration #1 chosen from 1 choice
[   15.019976] hub 2-6:1.0: USB hub found
[   15.022939] hub 2-6:1.0: 2 ports detected
[   15.073626] PM: Starting manual resume from disk
[   15.073628] PM: Resume from partition 8:3
[   15.073629] PM: Checking hibernation image.
[   15.073778] PM: Resume from disk failed.
[   15.078275] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[   15.078287] ReiserFS: sda2: using ordered data mode
[   15.097844] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   15.098076] ReiserFS: sda2: checking transaction log (sda2)
[   15.134124] ReiserFS: sda2: Using r5 hash to sort names
[   15.315927] usb 2-6.1: new low speed USB device using ohci_hcd and address 3
[   15.433958] usb 2-6.1: configuration #1 chosen from 1 choice
[   15.752182] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[808080050000044b]
[   20.420029] udev: starting version 141
[   20.727971] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   20.807937] usbcore: registered new interface driver hiddev
[   20.814303] usbcore: registered new interface driver usbhid
[   20.814306] usbhid: v2.6:USB HID core driver
[   21.027423] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   21.027432] parport_serial 0000:06:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   21.027450] parport0: PC-style at 0xed00 [PCSPP,TRISTATE,EPP]
[   21.062786] ACPI: I/O resource nForce2_smbus [0x1c00-0x1c3f] conflicts with ACPI region SM00 [0x1c00-0x1c05]
[   21.062788] ACPI: Device needs an ACPI driver
[   21.062822] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   21.062841] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   21.120264] 0000:06:0a.0: ttyS1 at I/O 0xef00 (irq = 18) is a 16550A
[   21.120404] 0000:06:0a.0: ttyS2 at I/O 0xee00 (irq = 18) is a 16550A
[   21.208726] ppdev: user-space parallel port driver
[   21.235764] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6.1/2-6.1:1.0/input/input5
[   21.244218] logitech 0003:046D:C704.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:0b.0-6.1/input0
[   21.256672] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6.1/2-6.1:1.1/input/input6
[   21.266604] logitech 0003:046D:C704.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6.1/input1
[   21.351681] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   21.351686] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   21.351864] HDA Intel 0000:00:10.1: setting latency timer to 64
[   24.922842] lp0: using parport0 (polling).
[   25.027120] Adding 514040k swap on /dev/sda3.  Priority:-1 extents:1 across:514040k
[   45.359771] type=1505 audit(1249948083.641:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2215
[   45.392451] type=1505 audit(1249948083.677:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2219
[   45.392510] type=1505 audit(1249948083.677:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2219
[   45.392537] type=1505 audit(1249948083.677:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2219
[   45.392563] type=1505 audit(1249948083.677:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2219
[   45.483692] type=1505 audit(1249948083.765:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2224
[   45.483808] type=1505 audit(1249948083.765:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2224
[   45.503490] type=1505 audit(1249948083.785:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2228
[   46.599619] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.599621] Bluetooth: BNEP filters: protocol multicast
[   46.645080] Bridge firewalling registered
[   48.919470] Linux agpgart interface v0.103
[   49.255962] nvidia: module license 'NVIDIA' taints kernel.
[   49.508686] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   49.508695] nvidia 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   49.508702] nvidia 0000:03:00.0: setting latency timer to 64
[   49.508963] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.31  Tue Jul 28 15:43:22 PDT 2009
[  106.788148] UDF-fs: No VRS found
[  106.818028] ISO 9660 Extensions: Microsoft Joliet Level 3
[  106.860616] ISO 9660 Extensions: RRIP_1991A
[ 1242.929481] HDA Intel 0000:00:10.1: PCI INT B disabled
[ 1243.077121] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[ 1243.077545] HDA Intel 0000:00:10.1: setting latency timer to 64


```

from: [http://www.alsa-project.org/db/?f=8195722c4a3be5635ada22a30a847cfeb6c434b0](http://www.alsa-project.org/db/?f=8195722c4a3be5635ada22a30a847cfeb6c434b0)

```

!!################################
!!ALSA Information Script v 0.4.57
!!################################

!!Script ran on: Mon Aug 10 19:54:35 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      
Product Name:      


!!Kernel Information
!!------------------

Kernel release:    2.6.28-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff4000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
06:0a.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
	Subsystem: 3842:1000


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : 0
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC1200
Address: 0
Vendor Id: 0x10ec0888
Subsystem Id: 0x10de0175
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x01 0x01]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x14 0x14]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x18567130: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Yellow
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19840: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19850: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181304f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4015e601: [N/A] Speaker at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01441120: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x01c46160: [Jack] SPDIF In at Ext Rear
    Conn = RCA, Color = Orange
    DefAssociation = 0x6, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 9 Aug 10 15:39 /dev/snd/controlC0
crw-rw----  1 root audio 116, 8 Aug 10 15:41 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 7 Aug 10 15:50 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 6 Aug 10 15:39 /dev/snd/pcmC0D1c
crw-rw----  1 root audio 116, 5 Aug 10 15:39 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 4 Aug 10 15:39 /dev/snd/pcmC0D2c
crw-rw----  1 root audio 116, 3 Aug 10 15:39 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Aug 10 15:39 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [NVidia]

Card hw:0 'NVidia'/'HDA NVidia at 0xdfff4000 irq 22'
  Mixer name	: 'Realtek ALC1200'
  Components	: 'HDA:10ec0888,10de0175,00100101'
  Controls      : 35
  Simple ctrls  : 19
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 26 [84%] [-7.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [off] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 1 [3%] [-15.00dB] [on]
  Front Right: Capture 1 [3%] [-15.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.NVidia {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 25
		value.1 25
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 0
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 0
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Side Playback Volume'
		value.0 0
		value.1 0
	}
	control.10 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Side Playback Switch'
		value.0 true
		value.1 true
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mic Boost'
		value.0 0
		value.1 0
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 1
		value.1 1
	}
	control.21 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.22 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
	control.23 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		value Mic
	}
	control.25 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 'Front Mic'
		comment.item.2 Line
		iface MIXER
		name 'Input Source'
		index 1
		value Mic
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.30 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 26
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.35 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
nvidia
agpgart
binfmt_misc
bridge
stp
bnep
video
output
input_polldev
sbp2
lp
snd_hda_intel
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
joydev
snd_timer
snd_seq_device
snd
hid_logitech
soundcore
ff_memless
ppdev
parport_serial
snd_page_alloc
i2c_nforce2
usbhid
parport_pc
parport
pcspkr
reiserfs
ohci1394
forcedeth
ieee1394
floppy
fbcon
tileblit
font
bitblit
softcursor


!!ALSA/HDA dmesg
!!------------------

[   21.541424] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   21.541428] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   21.541628] HDA Intel 0000:00:10.1: setting latency timer to 64
[   21.932019] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   25.045951] lp0: using parport0 (polling).




```


the only real error is 

```

[   21.932019] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

```

but nothing seems to fix it. 


ill throw this in there just for kicks.. 

 ```
 
alsactl init
Unknown hardware: "HDA-Intel" "Realtek ALC1200" "HDA:10ec0888,10de0175,00100101" "" ""
Hardware is initialized using a guess method

```

---

### Post by slipdipper on 2009-08-12
solved: upgraded to alsa drivers/util/lib/etc 1.0.20

---

