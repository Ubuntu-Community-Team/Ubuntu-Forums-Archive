---
title: "tv capture card not recognized!!!"
date: 2010-04-09
forum: Multimedia Software
---

### Post by kezeb on 2010-04-09
i've no idea what the heck is going on with my TV capture card, i went to the other posts about my Hauppauge Inc. HDPVR-1250 model 1196 but it all didn't work i have the ubuntu-restricted extras installed but mythtv is not picking up the card i seriously need help!!!!!!!! i'm running ubuntu karmic.

---

### Post by mikewhatever on 2010-04-09
I've no experience with tv capture hardware, but nevertheless, ubuntu-restricted-extras is just a bunch of codecs, and if your capture card is not recognized, what you need is a driver. Perhaps the xserver-xorg-video-ivtv package, found in the repositories. Did the 'other posts' mention that?

---

### Post by keplerspeed on 2010-04-09
Firstly check if card is supported by the v4l-dvb kernel module out of the box, by entering this to the terminal:

```

dmesg

```

If you need help seeing if the card is supported out of the box, post the output of the dmesg command here.

If your card is not supported, [try the latest v4l-dvb kernel module from here]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").

If you have a pinnacle/empia card, things can get messy. There was a branch of the em28xx driver made by the initial writer of this driver. Some cards are supported by the em28xx module in the kernel, some card supported by the branch em28xx-new, some supported by both. [See here for further reading.]("http://rg03.wordpress.com/2009/12/15/when-your-hobby-becomes-a-job-reflections-on-the-em28xx-driver-situation/")

Since you have a hauppauge card I would assume you should have support either in kernel or the latest 4vl-dvb module, from my link above.

---

### Post by halj32 on 2010-04-09
have you installed "linux-firmware-nonfree"????  this is needed for the card to work, then you should be able to scan for channels in Kaffeine or some other media players
 if you dont know how to install try synaptic package manager
  hope this helps

---

### Post by keplerspeed on 2010-04-09
Once you run the "dmesg" command we will know if firmware is needed, and what firmware the card is asking for. Then we can install the correct package, containing the correct firmware.

So please run this command and post the output.
```

dmesg

```

---

### Post by kezeb on 2010-04-11
got the reply sorry i haven't been home to respond to all of your posts 
 i've also installed the linux-firmware-nonfree and the xserver-xorg-video-ivtv.


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcff90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  modified: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  modified: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37819000 - 37fefa28
[    0.000000] Allocated new RAMDISK: 008ad000 - 01083a28
[    0.000000] Move RAMDISK from 0000000037819000 - 0000000037fefa27 to 008ad000 - 01083a27
[    0.000000] ACPI: RSDP 000fb8b0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT cff90100 00054 (v01 033109 XSDT1123 20090331 MSFT 00000097)
[    0.000000] ACPI: FACP cff90290 000F4 (v03 033109 FACP1123 20090331 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 20090521 tbfadt-558
[    0.000000] ACPI: DSDT cff90440 0D92C (v01  A1152 A1152000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS cffa8000 00040
[    0.000000] ACPI: APIC cff90390 0006C (v01 033109 APIC1123 20090331 MSFT 00000097)
[    0.000000] ACPI: MCFG cff90400 0003C (v01 033109 OEMMCFG  20090331 MSFT 00000097)
[    0.000000] ACPI: OEMB cffa8040 00072 (v01 033109 OEMB1123 20090331 MSFT 00000097)
[    0.000000] ACPI: HPET cff9f440 00038 (v01 033109 OEMHPET  20090331 MSFT 00000097)
[    0.000000] ACPI: SSDT cff9f480 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2439MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac22c]              BRK ==> [00008a9000 - 00008ac22c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0001083a28]      NEW RAMDISK ==> [00008ad000 - 0001083a28]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cff90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cff90
[    0.000000] On node 0 totalpages: 851743
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1084200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4880 pages used for memmap
[    0.000000]   HighMem zone: 619650 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2a94000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845087
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=f69c3f3d-c4cf-4fb8-aaa5-35a35a5e50fe ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 17036800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000cff90)
[    0.000000] Memory: 3345904k/3407424k available (4565k kernel code, 60252k reserved, 2143k data, 540k init, 2498120k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3210.300 MHz processor.
[    0.000007] spurious 8259A interrupt: IRQ7.
[    0.000700] Console: colour VGA+ 80x25
[    0.000701] console [tty0] enabled
[    0.000809] hpet clockevent registered
[    0.000814]   alloc irq_desc for 24 on node 0
[    0.000815]   alloc kstat_irqs on node 0
[    0.000818] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6420.60 BogoMIPS (lpj=12841200)
[    0.004015] Security Framework initialized
[    0.004026] AppArmor: AppArmor initialized
[    0.004030] Mount-cache hash table entries: 512
[    0.004094] Initializing cgroup subsys ns
[    0.004096] Initializing cgroup subsys cpuacct
[    0.004099] Initializing cgroup subsys memory
[    0.004102] Initializing cgroup subsys freezer
[    0.004104] Initializing cgroup subsys net_cls
[    0.004110] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004112] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004114] CPU: Physical Processor ID: 0
[    0.004115] CPU: Processor Core ID: 0
[    0.004117] mce: CPU supports 6 MCE banks
[    0.004123] using C1E aware idle routine
[    0.004126] Performance Counters: AMD PMU driver.
[    0.004129] ... version:                 0
[    0.004130] ... bit width:               48
[    0.004131] ... generic counters:        4
[    0.004133] ... value mask:              0000ffffffffffff
[    0.004134] ... max period:              00007fffffffffff
[    0.004135] ... fixed-purpose counters:  0
[    0.004136] ... counter mask:            000000000000000f
[    0.004138] Checking 'hlt' instruction... OK.
[    0.021352] ACPI: Core revision 20090521
[    0.036331] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076451] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6421.64 BogoMIPS (lpj=12843280)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.164831] CPU1: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.164839] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168017] System has AMD C1E enabled
[    0.168027] Switch to broadcast mode on CPU1
[    0.168050] Booting processor 2 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 6421.63 BogoMIPS (lpj=12843278)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.256830] CPU2: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.256846] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.260019] Switch to broadcast mode on CPU2
[    0.260049] Booting processor 3 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 6421.64 BogoMIPS (lpj=12843288)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.348836] CPU3: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.348859] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.352019] Brought up 4 CPUs
[    0.352021] Total of 4 processors activated (25685.52 BogoMIPS).
[    0.352018] Switch to broadcast mode on CPU3
[    0.352058] CPU0 attaching sched-domain:
[    0.352060]  domain 0: span 0-3 level MC
[    0.352062]   groups: 0 1 2 3
[    0.352066] CPU1 attaching sched-domain:
[    0.352068]  domain 0: span 0-3 level MC
[    0.352069]   groups: 1 2 3 0
[    0.352072] CPU2 attaching sched-domain:
[    0.352073]  domain 0: span 0-3 level MC
[    0.352075]   groups: 2 3 0 1
[    0.352078] CPU3 attaching sched-domain:
[    0.352079]  domain 0: span 0-3 level MC
[    0.352080]   groups: 3 0 1 2
[    0.352141] Switch to broadcast mode on CPU0
[    0.352141] Booting paravirtualized kernel on bare hardware
[    0.352141] regulator: core version 0.5
[    0.352141] Time: 11:45:57  Date: 04/11/10
[    0.352141] NET: Registered protocol family 16
[    0.352141] EISA bus registered
[    0.352141] ACPI: bus type pci registered
[    0.352171] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.352173] PCI: Not using MMCONFIG.
[    0.352785] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.352786] PCI: Using configuration type 1 for base access
[    0.352787] PCI: Using configuration type 1 for extended access
[    0.352805] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.352806] mtrr: probably your BIOS does not setup all CPUs.
[    0.352807] mtrr: corrected configuration.
[    0.353282] bio: create slab <bio-0> at 0
[    0.353282] ACPI: EC: Look up EC in DSDT
[    0.438487] ACPI: Interpreter enabled
[    0.438490] ACPI: (supports S0 S1 S3 S4 S5)
[    0.438507] ACPI: Using IOAPIC for interrupt routing
[    0.438546] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.442698] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.442700] PCI: Using MMCONFIG for extended config space
[    0.448344] ACPI Warning: Incorrect checksum in table [OEMB] - C2, should be B9 20090521 tbutils-246
[    0.448429] ACPI: No dock devices found.
[    0.448544] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448635] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.448637] pci 0000:00:05.0: PME# disabled
[    0.448662] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.448664] pci 0000:00:06.0: PME# disabled
[    0.448688] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.448690] pci 0000:00:07.0: PME# disabled
[    0.448737] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.448743] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.448749] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.448755] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.448761] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.448767] pci 0000:00:11.0: reg 24 32bit mmio: [0xfb9ffc00-0xfb9fffff]
[    0.448783] pci 0000:00:11.0: set SATA to AHCI mode
[    0.448823] pci 0000:00:12.0: reg 10 32bit mmio: [0xfb9fd000-0xfb9fdfff]
[    0.448871] pci 0000:00:12.1: reg 10 32bit mmio: [0xfb9fe000-0xfb9fefff]
[    0.448936] pci 0000:00:12.2: reg 10 32bit mmio: [0xfb9ff800-0xfb9ff8ff]
[    0.448983] pci 0000:00:12.2: supports D1 D2
[    0.448984] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.448988] pci 0000:00:12.2: PME# disabled
[    0.449015] pci 0000:00:13.0: reg 10 32bit mmio: [0xfb9fb000-0xfb9fbfff]
[    0.449064] pci 0000:00:13.1: reg 10 32bit mmio: [0xfb9fc000-0xfb9fcfff]
[    0.449128] pci 0000:00:13.2: reg 10 32bit mmio: [0xfb9ff400-0xfb9ff4ff]
[    0.449175] pci 0000:00:13.2: supports D1 D2
[    0.449177] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.449180] pci 0000:00:13.2: PME# disabled
[    0.449285] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.449290] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.449296] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.449302] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.449307] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.449366] pci 0000:00:14.2: reg 10 64bit mmio: [0xfb9f4000-0xfb9f7fff]
[    0.449404] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.449408] pci 0000:00:14.2: PME# disabled
[    0.449500] pci 0000:00:14.5: reg 10 32bit mmio: [0xfb9fa000-0xfb9fafff]
[    0.449612] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.449615] pci 0000:01:05.0: reg 14 io port: [0xc000-0xc0ff]
[    0.449618] pci 0000:01:05.0: reg 18 32bit mmio: [0xfbbe0000-0xfbbeffff]
[    0.449623] pci 0000:01:05.0: reg 24 32bit mmio: [0xfba00000-0xfbafffff]
[    0.449632] pci 0000:01:05.0: supports D1 D2
[    0.449646] pci 0000:01:05.1: reg 10 32bit mmio: [0xfbbfc000-0xfbbfffff]
[    0.449662] pci 0000:01:05.1: supports D1 D2
[    0.449697] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.449699] pci 0000:00:01.0: bridge 32bit mmio: [0xfba00000-0xfbbfffff]
[    0.449702] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.449748] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbc00000-0xfbdfffff]
[    0.449831] pci 0000:02:00.0: supports D1 D2
[    0.449832] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.449837] pci 0000:02:00.0: PME# disabled
[    0.449896] pci 0000:00:05.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.449937] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbec0000-0xfbefffff]
[    0.449944] pci 0000:03:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.449990] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.449994] pci 0000:03:00.0: PME# disabled
[    0.450044] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.450046] pci 0000:00:06.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.450108] pci 0000:04:00.0: reg 10 64bit mmio: [0xfbfff800-0xfbffffff]
[    0.450117] pci 0000:04:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.450189] pci 0000:04:00.0: supports D2
[    0.450191] pci 0000:04:00.0: PME# supported from D2 D3hot D3cold
[    0.450196] pci 0000:04:00.0: PME# disabled
[    0.450255] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.450257] pci 0000:00:07.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.450310] pci 0000:00:14.4: transparent bridge
[    0.450328] pci_bus 0000:00: on NUMA node 0
[    0.450331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.450476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.450527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.450566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.450604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.450664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.453517] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.453600] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.453682] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 *7 10 12 14 15)
[    0.453763] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.453845] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.453927] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.454009] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.454091] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.454190] SCSI subsystem initialized
[    0.454206] libata version 3.00 loaded.
[    0.454206] usbcore: registered new interface driver usbfs
[    0.454206] usbcore: registered new interface driver hub
[    0.454206] usbcore: registered new device driver usb
[    0.454206] ACPI: WMI: Mapper loaded
[    0.454206] PCI: Using ACPI for IRQ routing
[    0.468006] Bluetooth: Core ver 2.15
[    0.468014] NET: Registered protocol family 31
[    0.468014] Bluetooth: HCI device and connection manager initialized
[    0.468014] Bluetooth: HCI socket layer initialized
[    0.468014] NetLabel: Initializing
[    0.468014] NetLabel:  domain hash size = 128
[    0.468014] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.468022] NetLabel:  unlabeled traffic allowed by default
[    0.468045] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.468048] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.472014] hpet: hpet2 irq 24 for MSI
[    0.500326] pnp: PnP ACPI init
[    0.500333] ACPI: bus type pnp registered
[    0.503650] pnp: PnP ACPI: found 14 devices
[    0.503651] ACPI: ACPI bus type pnp unregistered
[    0.503653] PnPBIOS: Disabled by ACPI PNP
[    0.503661] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.503663] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.503667] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.503669] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.503671] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.503672] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.503674] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.503676] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.503677] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.503679] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.503681] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.503683] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.503684] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.503686] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.503688] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.503690] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.503691] system 00:08: ioport range 0xb00-0xb3f has been reserved
[    0.503693] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.503695] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.503697] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.503699] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.503704] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.503706] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.503708] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.503715] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.503722] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.503723] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.503725] system 00:0b: ioport range 0xf40-0xf4f has been reserved
[    0.503727] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.503740] Switched to high resolution mode on CPU 3
[    0.503744] Switched to high resolution mode on CPU 1
[    0.503748] Switched to high resolution mode on CPU 2
[    0.503743] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.503747] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.503749] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.503750] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.503752] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.503754] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.504015] Switched to high resolution mode on CPU 0
[    0.538340] AppArmor: AppArmor Filesystem Enabled
[    0.538363] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.538365] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.538367] pci 0000:00:01.0:   MEM window: 0xfba00000-0xfbbfffff
[    0.538369] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.538372] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.538373] pci 0000:00:05.0:   IO window: disabled
[    0.538376] pci 0000:00:05.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.538377] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.538379] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
[    0.538381] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.538383] pci 0000:00:06.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.538385] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.538387] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
[    0.538388] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.538391] pci 0000:00:07.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.538392] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.538394] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    0.538396] pci 0000:00:14.4:   IO window: disabled
[    0.538400] pci 0000:00:14.4:   MEM window: disabled
[    0.538403] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.538411]   alloc irq_desc for 17 on node -1
[    0.538413]   alloc kstat_irqs on node -1
[    0.538415] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.538418] pci 0000:00:05.0: setting latency timer to 64
[    0.538421]   alloc irq_desc for 18 on node -1
[    0.538422]   alloc kstat_irqs on node -1
[    0.538424] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.538426] pci 0000:00:06.0: setting latency timer to 64
[    0.538429]   alloc irq_desc for 19 on node -1
[    0.538430]   alloc kstat_irqs on node -1
[    0.538432] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.538434] pci 0000:00:07.0: setting latency timer to 64
[    0.538439] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.538441] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.538443] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.538444] pci_bus 0000:01: resource 1 mem: [0xfba00000-0xfbbfffff]
[    0.538446] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.538448] pci_bus 0000:02: resource 1 mem: [0xfbc00000-0xfbdfffff]
[    0.538449] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.538451] pci_bus 0000:03: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.538452] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.538454] pci_bus 0000:04: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.538455] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.538457] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.538476] NET: Registered protocol family 2
[    0.538529] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.538698] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.539022] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.539184] TCP: Hash tables configured (established 131072 bind 65536)
[    0.539186] TCP reno registered
[    0.539229] NET: Registered protocol family 1
[    0.539261] Trying to unpack rootfs image as initramfs...
[    0.674233] Freeing initrd memory: 8026k freed
[    0.676269] cpufreq-nforce2: No nForce2 chipset.
[    0.676284] Scanning for low memory corruption every 60 seconds
[    0.676339] audit: initializing netlink socket (disabled)
[    0.676347] type=2000 audit(1270986357.676:1): initialized
[    0.681641] highmem bounce pool size: 64 pages
[    0.681645] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.682461] VFS: Disk quotas dquot_6.5.2
[    0.682495] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.682793] fuse init (API version 7.12)
[    0.682838] msgmni has been set to 1673
[    0.683010] alg: No test for stdrng (krng)
[    0.683019] io scheduler noop registered
[    0.683020] io scheduler anticipatory registered
[    0.683021] io scheduler deadline registered
[    0.683046] io scheduler cfq registered (default)
[    0.824294] pci 0000:01:05.0: Boot video device
[    0.824368]   alloc irq_desc for 25 on node -1
[    0.824369]   alloc kstat_irqs on node -1
[    0.824375] pcieport-driver 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.824379] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    0.824431]   alloc irq_desc for 26 on node -1
[    0.824432]   alloc kstat_irqs on node -1
[    0.824435] pcieport-driver 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.824438] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.824486]   alloc irq_desc for 27 on node -1
[    0.824487]   alloc kstat_irqs on node -1
[    0.824491] pcieport-driver 0000:00:07.0: irq 27 for MSI/MSI-X
[    0.824494] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.824532] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.824545] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.824615] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.824617] ACPI: Power Button [PWRF]
[    0.824651] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.824655] ACPI: Power Button [PWRB]
[    0.825262] processor LNXCPU:00: registered as cooling_device0
[    0.825264] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.825635] processor LNXCPU:01: registered as cooling_device1
[    0.826010] processor LNXCPU:02: registered as cooling_device2
[    0.826383] processor LNXCPU:03: registered as cooling_device3
[    0.828362] isapnp: Scanning for PnP cards...
[    1.182157] isapnp: No Plug & Play device found
[    1.182775] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.182873] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.183100] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.183613] brd: module loaded
[    1.183842] loop: module loaded
[    1.183879] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.183915] ahci 0000:00:11.0: version 3.0
[    1.183924]   alloc irq_desc for 22 on node -1
[    1.183926]   alloc kstat_irqs on node -1
[    1.183929] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.184031] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.184033] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.184255] scsi0 : ahci
[    1.184310] scsi1 : ahci
[    1.184346] scsi2 : ahci
[    1.184384] scsi3 : ahci
[    1.184441] ata1: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed
[    1.184444] ata2: SATA max UDMA/133 abar m1024@0xfb9ffc00 port 0xfb9ffd80 irq 22
[    1.184446] ata3: SATA max UDMA/133 abar m1024@0xfb9ffc00 port 0xfb9ffe00 irq 22
[    1.184449] ata4: SATA max UDMA/133 abar m1024@0xfb9ffc00 port 0xfb9ffe80 irq 22
[    1.184604]   alloc irq_desc for 16 on node -1
[    1.184605]   alloc kstat_irqs on node -1
[    1.184608] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.184625] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.184691] scsi4 : pata_atiixp
[    1.184734] scsi5 : pata_atiixp
[    1.185572] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.185574] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.185960] Fixed MDIO Bus: probed
[    1.185978] PPP generic driver version 2.4.2
[    1.186024] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.186036] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.186044] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.186069] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.186084] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.186099] ehci_hcd 0000:00:12.2: debug port 1
[    1.186110] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfb9ff800
[    1.196282] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.196322] usb usb1: configuration #1 chosen from 1 choice
[    1.196338] hub 1-0:1.0: USB hub found
[    1.196343] hub 1-0:1.0: 6 ports detected
[    1.196383] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.196388] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.196405] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.196418] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.196433] ehci_hcd 0000:00:13.2: debug port 1
[    1.196443] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfb9ff400
[    1.208276] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.208305] usb usb2: configuration #1 chosen from 1 choice
[    1.208318] hub 2-0:1.0: USB hub found
[    1.208322] hub 2-0:1.0: 6 ports detected
[    1.208360] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.208369] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.208376] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.208391] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.208408] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfb9fd000
[    1.268297] usb usb3: configuration #1 chosen from 1 choice
[    1.268312] hub 3-0:1.0: USB hub found
[    1.268318] hub 3-0:1.0: 3 ports detected
[    1.268348] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.268353] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.268370] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.268380] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfb9fe000
[    1.328291] usb usb4: configuration #1 chosen from 1 choice
[    1.328305] hub 4-0:1.0: USB hub found
[    1.328311] hub 4-0:1.0: 3 ports detected
[    1.328340] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.328347] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.328361] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.328380] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfb9fb000
[    1.364716] ata5.00: ATAPI: PHILIPS SPD2410L1, M5P4, max UDMA/66
[    1.364730] ata5.00: limited to UDMA/33 due to 40-wire cable
[    1.388310] usb usb5: configuration #1 chosen from 1 choice
[    1.388326] hub 5-0:1.0: USB hub found
[    1.388333] hub 5-0:1.0: 3 ports detected
[    1.388370] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.388378] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.388396] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.388408] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfb9fc000
[    1.396679] ata5.00: configured for UDMA/33
[    1.448307] usb usb6: configuration #1 chosen from 1 choice
[    1.448323] hub 6-0:1.0: USB hub found
[    1.448329] hub 6-0:1.0: 3 ports detected
[    1.448371] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.448381] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.448399] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.448411] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfb9fa000
[    1.504310] ata3: SATA link down (SStatus 0 SControl 300)
[    1.504340] ata2: SATA link down (SStatus 0 SControl 300)
[    1.504363] ata4: SATA link down (SStatus 0 SControl 300)
[    1.508299] usb usb7: configuration #1 chosen from 1 choice
[    1.508315] hub 7-0:1.0: USB hub found
[    1.508321] hub 7-0:1.0: 2 ports detected
[    1.508350] uhci_hcd: USB Universal Host Controller Interface driver
[    1.508396] PNP: No PS/2 controller found. Probing ports directly.
[    1.508533] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.509021] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.509031] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.509088] mice: PS/2 mouse device common for all mice
[    1.509144] rtc_cmos 00:03: RTC can wake from S4
[    1.509162] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.509184] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.509248] device-mapper: uevent: version 1.0.3
[    1.509307] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.509413] device-mapper: multipath: version 1.1.0 loaded
[    1.509414] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.509493] EISA: Probing bus 0 at eisa.0
[    1.509522] Cannot allocate resource for EISA slot 7
[    1.509524] Cannot allocate resource for EISA slot 8
[    1.509525] EISA: Detected 0 cards.
[    1.509682] cpuidle: using governor ladder
[    1.509683] cpuidle: using governor menu
[    1.509957] TCP cubic registered
[    1.510039] NET: Registered protocol family 10
[    1.510307] lo: Disabled Privacy Extensions
[    1.510497] NET: Registered protocol family 17
[    1.510506] Bluetooth: L2CAP ver 2.13
[    1.510507] Bluetooth: L2CAP socket layer initialized
[    1.510508] Bluetooth: SCO (Voice Link) ver 0.6
[    1.510509] Bluetooth: SCO socket layer initialized
[    1.510548] Bluetooth: RFCOMM TTY layer initialized
[    1.510550] Bluetooth: RFCOMM socket layer initialized
[    1.510551] Bluetooth: RFCOMM ver 1.11
[    1.510572] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor processors (4 cpu cores) (version 2.20.00)
[    1.510596] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.510597] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.510599] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.510600] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.511080] Using IPI No-Shortcut mode
[    1.511113] PM: Resume from disk failed.
[    1.511118] registered taskstats version 1
[    1.511191]   Magic number: 6:215:782
[    1.511244] rtc_cmos 00:03: setting system clock to 2010-04-11 11:45:58 UTC (1270986358)
[    1.511246] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.511247] EDD information not available.
[    1.656434] usb 1-2: configuration #1 chosen from 1 choice
[    2.072293] ata1: softreset failed (device not ready)
[    2.072296] ata1: applying SB600 PMP SRST workaround and retrying
[    2.144284] usb 5-1: new low speed USB device using ohci_hcd and address 2
[    2.236296] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.237640] ata1.00: ATA-8: WDC WD3200AAKS-00M9A0, 05.01D05, max UDMA/133
[    2.237642] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.239292] ata1.00: configured for UDMA/133
[    2.252344] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 05.0 PQ: 0 ANSI: 5
[    2.252415] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.252437] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.252458] sd 0:0:0:0: [sda] Write Protect is off
[    2.252460] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.252470] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.252531]  sda:
[    2.253787] scsi 4:0:0:0: CD-ROM            PHILIPS  SPD2410L1        M5P4 PQ: 0 ANSI: 5
[    2.259475] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.259478] Uniform CD-ROM driver Revision: 3.20
[    2.259523] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.259549] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.262176]  sda1 sda2 sda3 sda4 < sda5 >
[    2.294060] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.317772] usb 5-1: configuration #1 chosen from 1 choice
[    2.423359] Freeing unused kernel memory: 540k freed
[    2.423519] Write protecting the kernel text: 4568k
[    2.423542] Write protecting the kernel read-only data: 1836k
[    2.511505] ATL1E 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.511514] ATL1E 0000:03:00.0: setting latency timer to 64
[    2.518010] ohci1394 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.518017] ohci1394 0000:04:00.0: setting latency timer to 64
[    2.518958] Floppy drive(s): fd0 is 1.44M
[    2.524686] usbcore: registered new interface driver hiddev
[    2.524730] usbcore: registered new interface driver usbhid
[    2.524732] usbhid: v2.6:USB HID core driver
[    2.530931] input: MLK Wireless Keyboard& Laser Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
[    2.530971] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Wireless Keyboard& Laser Mouse] on usb-0000:00:13.0-1/input0
[    2.537300] FDC 0 is a post-1991 82077
[    2.538543] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
[    2.538972] input: MLK Wireless Keyboard& Laser Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input4
[    2.539030] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Wireless Keyboard& Laser Mouse] on usb-0000:00:13.0-1/input1
[    2.574797] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbfff800-fbffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.593776] usb 5-2: new low speed USB device using ohci_hcd and address 3
[    2.766888] usb 5-2: configuration #1 chosen from 1 choice
[    2.779975] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input5
[    2.780017] generic-usb 0003:046D:C50E.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:13.0-2/input0
[    3.041525] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    3.212973] usb 6-2: configuration #1 chosen from 1 choice
[    3.218379] Initializing USB Mass Storage driver...
[    3.218477] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.218538] usb-storage: device found at 2
[    3.218539] usb-storage: waiting for device to settle before scanning
[    3.218543] usbcore: registered new interface driver usb-storage
[    3.218545] USB Mass Storage support registered.
[    3.315853] xor: automatically using best checksumming function: pIII_sse
[    3.333507]    pIII_sse  : 12877.000 MB/sec
[    3.333509] xor: using function: pIII_sse (12877.000 MB/sec)
[    3.334910] device-mapper: dm-raid45: initialized v0.2594b
[    3.494242] PM: Starting manual resume from disk
[    3.494244] PM: Resume from partition 8:5
[    3.494245] PM: Checking hibernation image.
[    3.494624] PM: Resume from disk failed.
[    3.526140] EXT4-fs (sda3): barriers enabled
[    3.535725] kjournald2 starting: pid 450, dev sda3:8, commit interval 5 seconds
[    3.535737] EXT4-fs (sda3): delayed allocation enabled
[    3.535739] EXT4-fs: file extents enabled
[    3.537703] EXT4-fs: mballoc enabled
[    3.537710] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    3.853894] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d41ebe]
[    4.555445] Adding 200772k swap on /dev/sda5.  Priority:-1 extents:1 across:200772k 
[    4.954744] EXT4-fs (sda3): internal journal on sda3:8
[    5.191251] udev: starting version 147
[    5.791721] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    5.791724] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    5.791741] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.794569] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    5.794571] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.794575] piix4_smbus: probe of 0000:00:14.0 failed with error -16
[    5.907071] lp: driver loaded but no devices found
[    5.933368] Linux agpgart interface v0.103
[    6.248989] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    6.248992] Disabling lock debugging due to kernel taint
[    6.263194] [fglrx] Maximum main memory to use for locked dma buffers: 3126 MBytes.
[    6.263208] [fglrx]   vendor: 1002 device: 9614 count: 1
[    6.263413] [fglrx] ioport: bar 1, base 0xc000, size: 0x100
[    6.263422] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.263425] pci 0000:01:05.0: setting latency timer to 64
[    6.263640] [fglrx] Kernel PAT support is enabled
[    6.263653] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[    6.520485] Linux video capture interface: v2.00
[    6.710747] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.939430] cx23885 driver version 0.0.2 loaded
[    6.939461] cx23885 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.939464] cx23885[0]: Your board isn't known (yet) to the driver.
[    6.939465] cx23885[0]: Try to pick one of the existing card configs via
[    6.939465] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    6.939466] cx23885[0]: version might help as well.
[    6.939468] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    6.939469] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    6.939470] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    6.939472] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    6.939473] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    6.939474] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    6.939475] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    6.939476] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    6.939478] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    6.939479] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    6.939480] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    6.939481] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    6.939483] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    6.939484] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    6.939485] cx23885[0]:    card=13 -> Compro VideoMate E650F
[    6.939486] cx23885[0]:    card=14 -> TurboSight TBS 6920
[    6.939488] cx23885[0]:    card=15 -> TeVii S470
[    6.939489] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    6.939490] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    6.939491] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[    6.939492] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[    6.939493] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[    6.939495] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[    6.939496] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[    6.939527] CORE cx23885[0]: subsystem: 1461:d439, board: UNKNOWN/GENERIC [card=0,autodetected]
[    7.066402] cx23885_dev_checkrevision() Hardware revision = 0xb1
[    7.066409] cx23885[0]/0: found at 0000:02:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfbc00000
[    7.066415] cx23885 0000:02:00.0: setting latency timer to 64
[    7.066418] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.123572] eth1: register 'asix' at usb-0000:00:12.2-2, ASIX AX88772 USB 2.0 Ethernet, 00:50:b6:04:2d:46
[    7.123591] usbcore: registered new interface driver asix
[    7.227213] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.320460] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.320475] HDA Intel 0000:01:05.1: setting latency timer to 64
[    8.218954] usb-storage: device scan complete
[    8.224809] scsi 6:0:0:0: Direct-Access              USB CompactFlash 1.27 PQ: 0 ANSI: 0 CCS
[    8.230947] scsi 6:0:0:1: Direct-Access              USB SmartMedia   1.27 PQ: 0 ANSI: 0 CCS
[    8.236805] scsi 6:0:0:2: Direct-Access              USB MMC/SD       1.27 PQ: 0 ANSI: 0 CCS
[    8.242948] scsi 6:0:0:3: Direct-Access              USB MS/MS Pro    1.27 PQ: 0 ANSI: 0 CCS
[    8.243202] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    8.243260] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    8.243317] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    8.243371] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    8.313795] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.323962] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    8.339231]   alloc irq_desc for 28 on node -1
[    8.339233]   alloc kstat_irqs on node -1
[    8.339244] ATL1E 0000:03:00.0: irq 28 for MSI/MSI-X
[    8.339474] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.340406] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[    8.345494] eth1: link down
[    8.349772] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.369991] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.473788] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    8.483985] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   21.944889] [fglrx] GART Table is not in FRAME_BUFFER range 
[   21.945008]   alloc irq_desc for 29 on node -1
[   21.945010]   alloc kstat_irqs on node -1
[   21.945017] fglrx_pci 0000:01:05.0: irq 29 for MSI/MSI-X
[   21.945339] [fglrx] Firegl kernel thread PID: 2245
[   22.882565] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.882567] vboxdrv: Successfully done.
[   22.882568] vboxdrv: Found 4 processor cores.
[   22.882649] vboxdrv: fAsync=0 offMin=0x532 offMax=0x5e3c
[   22.882675] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.882677] vboxdrv: Successfully loaded version 3.1.6 (interface 0x00100001).
[   23.414108] ppdev: user-space parallel port driver
[   23.546356] [fglrx] Gart USWC size:1022 M.
[   23.546359] [fglrx] Gart cacheable size:405 M.
[   23.546363] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   23.546365] [fglrx] Reserved FB block: Unshared offset:17ffb000, size:5000 
[   29.120603] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

---

### Post by mikewhatever on 2010-04-11
I'd just run *lspci* to see if the card got recognized. Needless to say, you need to reboot after installing the driver.

---

### Post by keplerspeed on 2010-04-11
```

[ 6.520485] Linux video capture interface: v2.00
....
[ 6.939430] cx23885 driver version 0.0.2 loaded
[ 6.939461] cx23885 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 6.939464] cx23885[0]: Your board isn't known (yet) to the driver.
[ 6.939465] cx23885[0]: Try to pick one of the existing card configs via
[ 6.939465] cx23885[0]: card=<n> insmod option. Updating to the latest
[ 6.939466] cx23885[0]: version might help as well.
[ 6.939468] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[ 6.939469] cx23885[0]: card=0 -> UNKNOWN/GENERIC
[ 6.939470] cx23885[0]: card=1 -> Hauppauge WinTV-HVR1800lp
[ 6.939472] cx23885[0]: card=2 -> Hauppauge WinTV-HVR1800
[ 6.939473] cx23885[0]: card=3 -> Hauppauge WinTV-HVR1250
[ 6.939474] cx23885[0]: card=4 -> DViCO FusionHDTV5 Express
[ 6.939475] cx23885[0]: card=5 -> Hauppauge WinTV-HVR1500Q
[ 6.939476] cx23885[0]: card=6 -> Hauppauge WinTV-HVR1500
[ 6.939478] cx23885[0]: card=7 -> Hauppauge WinTV-HVR1200
[ 6.939479] cx23885[0]: card=8 -> Hauppauge WinTV-HVR1700
[ 6.939480] cx23885[0]: card=9 -> Hauppauge WinTV-HVR1400
[ 6.939481] cx23885[0]: card=10 -> DViCO FusionHDTV7 Dual Express
[ 6.939483] cx23885[0]: card=11 -> DViCO FusionHDTV DVB-T Dual Express
[ 6.939484] cx23885[0]: card=12 -> Leadtek Winfast PxDVR3200 H
[ 6.939485] cx23885[0]: card=13 -> Compro VideoMate E650F
[ 6.939486] cx23885[0]: card=14 -> TurboSight TBS 6920
[ 6.939488] cx23885[0]: card=15 -> TeVii S470
[ 6.939489] cx23885[0]: card=16 -> DVBWorld DVB-S2 2005
[ 6.939490] cx23885[0]: card=17 -> NetUP Dual DVB-S2 CI
[ 6.939491] cx23885[0]: card=18 -> Hauppauge WinTV-HVR1270
[ 6.939492] cx23885[0]: card=19 -> Hauppauge WinTV-HVR1275
[ 6.939493] cx23885[0]: card=20 -> Hauppauge WinTV-HVR1255
[ 6.939495] cx23885[0]: card=21 -> Hauppauge WinTV-HVR1210
[ 6.939496] cx23885[0]: card=22 -> Mygica X8506 DMB-TH
[\CODE]
This part is concerning the TV capture card. The driver does not recognise the card, as it is not supported by that driver or driver version.

Please enter this to the terminal so that we know exactly what card you have. Then we can find the correct driver/driver version.

If it is a USB tv card:
[CODE]
lsusb

```

For other pci-e etc type tv cards:
```

lshw

```

---

### Post by kezeb on 2010-04-11
this is it man just got back from church

home
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00B2001E-8C00-01D4-1EBE-00248C661695
  *-core
       description: Motherboard
       product: M4A78T-E
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MS1C93BC2J00847
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1001 (03/31/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 955 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 955 Processor
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:c000(size=4096) memory:fba00000-fbbfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Radeon HD 3300 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:d0000000-dfffffff(prefetchable) ioport:c000(size=256) memory:fbbe0000-fbbeffff memory:fba00000-fbafffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fbbfc000-fbbfffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fbc00000-fbdfffff
           *-multimedia
                description: Multimedia video controller
                product: Hauppauge Inc. HDPVR-1250 model 1196
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 0f
                width: 64 bits
                clock: 33MHz
                capabilities: pciexpress pm vpd msi bus_master cap_list
                configuration: driver=cx23885 latency=0
                resources: irq:17 memory:fbc00000-fbdfffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:fbe00000-fbefffff
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:24:8c:66:16:95
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.2.4 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
                resources: irq:28 memory:fbec0000-fbefffff ioport:dc00(size=128)
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:19 memory:fbfff800-fbffffff ioport:e800(size=256)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fb9ffc00-fb9fffff
           *-disk
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAVC0305640
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=aa3cd9bb
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 46b8fa00-278b-4890-ac7b-7ed843fcfc0c
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-02-24 14:58:40 filesystem=ntfs label=30 GB state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 11d8bab5-fc76-4ca0-b531-2ebc557f4766
                   size: 244GiB
                   capacity: 244GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-09-11 21:43:07 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 0acc3c30-4019-40a3-a672-68227de395e1
                   size: 25GiB
                   capacity: 25GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-04-11 08:34:43 filesystem=ext3 modified=2010-04-11 08:39:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-04-11 13:18:19 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 196MiB
                   capacity: 196MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 196MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fb9fd000-fb9fdfff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fb9fe000-fb9fefff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fb9ff800-fb9ff8ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fb9fb000-fb9fbfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fb9fc000-fb9fcfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fb9ff400-fb9ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: SPD2410L1
                vendor: PHILIPS
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: M5P4
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fb9f4000-fb9f7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fb9fa000-fb9fafff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@6:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:50:b6:04:2d:46
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=half firmware=ASIX AX88772 USB 2.0 Ethernet link=no multicast=yes port=MII speed=10MB/s

---

### Post by kezeb on 2010-04-11
i think this is what you're talking 'bout

*-multimedia
description: Multimedia video controller
product: Hauppauge Inc. HDPVR-1250 model 1196
vendor: Conexant Systems, Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 0f
width: 64 bits
clock: 33MHz
capabilities: pciexpress pm vpd msi bus_master cap_list
configuration: driver=cx23885 latency=0
resources: irq:17 memory:fbc00000-fbdfffff

---

### Post by xc3RnbFO8P on 2010-04-11
Read this:
[http://www.linuxtv.org/wiki/index.php/AVerMedia_M791_PCIe_Combo_%28OEM%29]("http://www.linuxtv.org/wiki/index.php/AVerMedia_M791_PCIe_Combo_%28OEM%29")

---

### Post by kezeb on 2010-04-11
the darn thing ain't even supported!!!!!!! damn man!!!! o well thanks man!!! at lease i ain't gotta suffer for it no more!!!!!!!!

---

### Post by markkingfw on 2010-04-27
-multimedia
                description: Multimedia video controller
                product: CX23885 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx23885 latency=0
                resources: irq:17 memory:fe800000-fe9fffff
 okay, I follwed the previous steps for the other user. Can you help me figure out what kind of driver I need to get this up and running and HOW to install the driver...thanks

Markkingfw

---

### Post by marcellux on 2010-04-27
> **kezeb said:**
> the darn thing ain't even supported!!!!!!! damn man!!!! o well thanks man!!! at lease i ain't gotta suffer for it no more!!!!!!!!

hi,
you said you have a hauppauge dvb-t for terrestrian tv, right?
I am using the same antenna and it works! Go to menu > system > administration > hardware drivers, ubuntu will search for available driver for devices connected to the machine. then, u can choose either to activate it or not.

I had some problems too with specific programs for watching tv, they wunna recognize my tv card either, like most of the KDE programs, but KLEAR (*).
the best one I recommend you to try is ME-TV, easy to use and has a tv scan icluded in its software, only thing you have to do is to choose the country and the city where u are.

(*) KLEAR is also good and uses less resources than me-tv but you have to set it up yourself, before you start it! first thing to do is to go to its web and look here [http://www.klear.org/channellists/DVB-T/](http://www.klear.org/channellists/DVB-T/) for your city, download it and save it. then u have to open nautilus as root and go to your home folder, once there, press CTRL+H to be able to see hidden files. go to ".klear", open it and paste the "channels.conf" file you downloaded from the web. the start the program and it should work fine!

---

