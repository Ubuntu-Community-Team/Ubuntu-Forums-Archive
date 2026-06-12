---
title: "installed mythbuntu 9.04 - can't find channels on avermedia avertvhd card"
date: 2009-10-19
forum: Mythbuntu
---

### Post by luigidk on 2009-10-19
I installed mythbuntu 9.04 on a hardware solution that was built by monolithmc.  (my hd crashed so I had to start over).  monolithmc was on ubuntu 7.1 with a customized mythtv install.  

The box has two capture cards:  PVR-150 and Avermedia AVERTVHD card - can not tell what model - but it is about 3 years old.

I have had no issues getting the PVR-150 to work - scanned channels -  ok.

I have created a DVB capture and have a localbroadcast set up in schedulesdirect (this is the same setup I had on monolith.

I using COMCAST cable for my localbroadcast HD channels...   

I have tried every combination of cable/broadcast and qam-256/64/etc...  

Just can't find any channels.

help!

---

### Post by luigidk on 2009-10-19
Update: It appears that i have to remove the capture device DVB:  avermedia avertvhd card or the system does not work?  

WHen I have only the PVR-150 card set up as a capture device - MythTV works fine.  When I add the avermedia capture device - then nothing works...

---

### Post by mars76 on 2009-10-19
Hi,

  I have the same Tuner Cards and i couldn't make either of them work..

  Could you pls post the outputs for the following. Also if you can post the versions ( Chipset) of these cards it will be really helpful.

  $ lspci
  $ lsusb

Thanks
mars

---

### Post by luigidk on 2009-10-19
The $lspci and lsusb are below.  Not sure how I get the chipset info?

$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev                                                a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                               nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                                Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                               troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                               neous Control
04:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OH                                               CI Link Layer Controller (rev 80)
04:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416)                                                MPEG-2 Encoder (rev 01)
04:0e.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Vi                                               deo Broadcast Decoder (rev d1)


$ lsusb

Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

---

### Post by klc5555 on 2009-10-19
Cards using a flavor of cheap Philips tuner are frequently a bit tricky to get working. The trouble is that there are a large number of different varieties (digital and analog), none  of which properly identify themselves so that modprobe can load the right driver with the right parameters. You must therefore determine the correct version and pass the appropriate parameters yourself (as necessary) via modprobe. You may have to blacklist the driver module in order to keep it from automatically loading with the incorrect parameters, so that you will then be able to load it correctly with modprobe. In addition, many of the cheap Philips tuners require additional firmware, which in some cases must be downloaded and installed separately.

One of the more useful docs pertaining to these cards and their appropriate drivers is found at the V4L site: [http://linuxtv.org/wiki/index.php/Saa713x_devices](http://linuxtv.org/wiki/index.php/Saa713x_devices)

Many of these cards are also written up on the Myth wiki: [http://www.mythtv.org/wiki/Category:Video_capture_cards](http://www.mythtv.org/wiki/Category:Video_capture_cards)

And some of them (like the AverMedia A180) have been discussed from time to time in this forum, which discussions should be easily retrievable with a search.

---

### Post by mars76 on 2009-10-20
Hi,

  Here is the error i am getting in my logs..I am using Avermedia A180 MCE Version

```

2009-10-20 20:39:55.937 MainServer::HandleAnnounce Playback
2009-10-20 20:39:55.965 adding: my-pvr as a client (events: 0)
2009-10-20 20:39:55.976 TVRec(1): Changing from None to WatchingLiveTV
2009-10-20 20:39:55.983 TVRec(1): HW Tuner: 1->1
2009-10-20 20:39:55.986 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-10-20 20:39:55.987 DVBChan(1:0) Error: SetChannelByString(5): Failed to initialize multiplex options
2009-10-20 20:39:55.988 TVRec(1) Error: Failed to set channel to 5. Reverting to kState_None
2009-10-20 20:39:55.988 TVRec(1): Changing from WatchingLiveTV to None

```And i don't see any other errors in my forntend..

And strangely the following command didn't return anything..

```

dmesg | grep ivtv

```

Complete output of dmesg ..

```

 dmesg 
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  modified: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  modified: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378ad000 - 37fef4f9
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fbf4f9
[    0.000000] Move RAMDISK from 00000000378ad000 - 0000000037fef4f8 to 0087d000 - 00fbf4f8
[    0.000000] ACPI: RSDP 000F78B0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT CFEE3000, 0034 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP CFEE3080, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT CFEE3100, 4EC3 (r1 INTELR AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: MCFG CFEE80C0, 003C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC CFEE8000, 0084 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT CFEE8A20, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2442MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fbf4f9]      NEW RAMDISK ==> [000087d000 - 0000fbf4f9]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f3930] 000f3930
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000cfee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfee0
[    0.000000] On node 0 totalpages: 851567
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4886 pages used for memmap
[    0.000000]   HighMem zone: 620492 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 844913
[    0.000000] Kernel command line: root=UUID=d6a3ee7c-1abb-4332-a10e-002112269c63 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2380.141 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 17033280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3345920k/3406720k available (4116k kernel code, 59424k reserved, 2199k data, 532k init, 2501512k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4760.28 BogoMIPS (lpj=9520564)
[    0.004025] Security Framework initialized
[    0.004032] SELinux:  Disabled at boot.
[    0.004049] AppArmor: AppArmor initialized
[    0.004056] Mount-cache hash table entries: 512
[    0.004174] Initializing cgroup subsys ns
[    0.004178] Initializing cgroup subsys cpuacct
[    0.004180] Initializing cgroup subsys memory
[    0.004184] Initializing cgroup subsys freezer
[    0.004196] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004198] CPU: L2 cache: 2048K
[    0.004200] CPU: Physical Processor ID: 0
[    0.004201] CPU: Processor Core ID: 0
[    0.004205] using mwait in idle threads.
[    0.004212] Checking 'hlt' instruction... OK.
[    0.022150] ACPI: Core revision 20080926
[    0.023868] ACPI: Checking initramfs for custom DSDT
[    0.288382] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.331113] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.332001] Booting processor 1 APIC 0x2 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4760.30 BogoMIPS (lpj=9520619)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.416513] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.416525] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.420091] Booting processor 2 APIC 0x3 ip 0x6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4760.33 BogoMIPS (lpj=9520671)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.508445] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.508458] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.512082] Booting processor 3 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4760.29 BogoMIPS (lpj=9520591)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.600475] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz stepping 07
[    0.600498] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.604038] Brought up 4 CPUs
[    0.604041] Total of 4 processors activated (19041.22 BogoMIPS).
[    0.604097] CPU0 attaching sched-domain:
[    0.604099]  domain 0: span 0,3 level MC
[    0.604101]   groups: 0 3
[    0.604105]   domain 1: span 0-3 level CPU
[    0.604107]    groups: 0,3 1-2
[    0.604111] CPU1 attaching sched-domain:
[    0.604113]  domain 0: span 1-2 level MC
[    0.604114]   groups: 1 2
[    0.604117]   domain 1: span 0-3 level CPU
[    0.604119]    groups: 1-2 0,3
[    0.604122] CPU2 attaching sched-domain:
[    0.604124]  domain 0: span 1-2 level MC
[    0.604126]   groups: 2 1
[    0.604128]   domain 1: span 0-3 level CPU
[    0.604130]    groups: 1-2 0,3
[    0.604134] CPU3 attaching sched-domain:
[    0.604136]  domain 0: span 0,3 level MC
[    0.604137]   groups: 3 0
[    0.604140]   domain 1: span 0-3 level CPU
[    0.604142]    groups: 0,3 1-2
[    0.604259] net_namespace: 776 bytes
[    0.604259] Booting paravirtualized kernel on bare hardware
[    0.604291] Time:  2:43:20  Date: 10/21/09
[    0.604291] regulator: core version 0.5
[    0.604291] NET: Registered protocol family 16
[    0.604291] EISA bus registered
[    0.604291] ACPI: bus type pci registered
[    0.604291] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.604291] PCI: MCFG area at e0000000 reserved in E820
[    0.604291] PCI: Using MMCONFIG for extended config space
[    0.604291] PCI: Using configuration type 1 for base access
[    0.604891] ACPI: EC: Look up EC in DSDT
[    0.612496] ACPI: Interpreter enabled
[    0.612506] ACPI: (supports S0 S3 S4 S5)
[    0.612523] ACPI: Using IOAPIC for interrupt routing
[    0.616619] ACPI: No dock devices found.
[    0.616631] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.616700] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.616703] pci 0000:00:01.0: PME# disabled
[    0.616761] pci 0000:00:1a.0: reg 20 io port: [0xff00-0xff1f]
[    0.616813] pci 0000:00:1a.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.616864] pci 0000:00:1a.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.616907] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.616939] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.616943] pci 0000:00:1a.7: PME# disabled
[    0.616973] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.616996] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.617000] pci 0000:00:1b.0: PME# disabled
[    0.617036] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.617039] pci 0000:00:1c.0: PME# disabled
[    0.617078] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.617081] pci 0000:00:1c.1: PME# disabled
[    0.617119] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.617122] pci 0000:00:1c.2: PME# disabled
[    0.617169] pci 0000:00:1d.0: reg 20 io port: [0xfc00-0xfc1f]
[    0.617220] pci 0000:00:1d.1: reg 20 io port: [0xfb00-0xfb1f]
[    0.617272] pci 0000:00:1d.2: reg 20 io port: [0xfa00-0xfa1f]
[    0.617314] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.617347] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.617350] pci 0000:00:1d.7: PME# disabled
[    0.617444] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.617447] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.617480] pci 0000:00:1f.2: reg 10 io port: [0xf900-0xf907]
[    0.617485] pci 0000:00:1f.2: reg 14 io port: [0xf800-0xf803]
[    0.617490] pci 0000:00:1f.2: reg 18 io port: [0xf700-0xf707]
[    0.617494] pci 0000:00:1f.2: reg 1c io port: [0xf600-0xf603]
[    0.617499] pci 0000:00:1f.2: reg 20 io port: [0xf500-0xf50f]
[    0.617503] pci 0000:00:1f.2: reg 24 io port: [0xf400-0xf40f]
[    0.617532] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfdffd000-0xfdffd0ff]
[    0.617544] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.617578] pci 0000:00:1f.5: reg 10 io port: [0xf200-0xf207]
[    0.617582] pci 0000:00:1f.5: reg 14 io port: [0xf100-0xf103]
[    0.617587] pci 0000:00:1f.5: reg 18 io port: [0xf000-0xf007]
[    0.617592] pci 0000:00:1f.5: reg 1c io port: [0xef00-0xef03]
[    0.617596] pci 0000:00:1f.5: reg 20 io port: [0xee00-0xee0f]
[    0.617601] pci 0000:00:1f.5: reg 24 io port: [0xed00-0xed0f]
[    0.617640] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.617647] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.617655] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]
[    0.617659] pci 0000:01:00.0: reg 24 io port: [0xaf00-0xaf7f]
[    0.617664] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.617703] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.617705] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    0.617709] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.617741] pci 0000:00:1c.0: bridge io port: [0x9000-0x9fff]
[    0.617745] pci 0000:00:1c.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.617750] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.617800] pci 0000:03:00.0: reg 10 io port: [0xdf00-0xdf07]
[    0.617808] pci 0000:03:00.0: reg 14 io port: [0xde00-0xde03]
[    0.617816] pci 0000:03:00.0: reg 18 io port: [0xdd00-0xdd07]
[    0.617824] pci 0000:03:00.0: reg 1c io port: [0xdc00-0xdc03]
[    0.617832] pci 0000:03:00.0: reg 20 io port: [0xdb00-0xdb0f]
[    0.617847] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.617900] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.617904] pci 0000:00:1c.1: bridge 32bit mmio: [0xfd700000-0xfd7fffff]
[    0.617909] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.617961] pci 0000:04:00.0: reg 10 64bit mmio: [0xfddfc000-0xfddfffff]
[    0.617968] pci 0000:04:00.0: reg 18 io port: [0xbe00-0xbeff]
[    0.617992] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.618002] pci 0000:04:00.0: supports D1 D2
[    0.618003] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.618008] pci 0000:04:00.0: PME# disabled
[    0.618043] pci 0000:00:1c.2: bridge io port: [0xb000-0xbfff]
[    0.618046] pci 0000:00:1c.2: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.618051] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.618091] pci 0000:00:1e.0: transparent bridge
[    0.618094] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.618097] pci 0000:00:1e.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
[    0.618102] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
[    0.618120] bus 00 -> node 0
[    0.618125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.618325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.618413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.618504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.618598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.633125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11 12)
[    0.633229] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.633339] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12)
[    0.633442] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633547] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.633651] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.633753] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12)
[    0.633856] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12)
[    0.633966] ACPI: WMI: Mapper loaded
[    0.634000] SCSI subsystem initialized
[    0.634000] libata version 3.00 loaded.
[    0.634000] usbcore: registered new interface driver usbfs
[    0.634000] usbcore: registered new interface driver hub
[    0.634000] usbcore: registered new device driver usb
[    0.634000] PCI: Using ACPI for IRQ routing
[    0.640009] Bluetooth: Core ver 2.13
[    0.640035] NET: Registered protocol family 31
[    0.640035] Bluetooth: HCI device and connection manager initialized
[    0.640035] Bluetooth: HCI socket layer initialized
[    0.640035] NET: Registered protocol family 8
[    0.640035] NET: Registered protocol family 20
[    0.640041] NetLabel: Initializing
[    0.640042] NetLabel:  domain hash size = 128
[    0.640043] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640055] NetLabel:  unlabeled traffic allowed by default
[    0.640122] AppArmor: AppArmor Filesystem Enabled
[    0.644010] pnp: PnP ACPI init
[    0.644016] ACPI: bus type pnp registered
[    0.646047] pnp: PnP ACPI: found 11 devices
[    0.646049] ACPI: ACPI bus type pnp unregistered
[    0.646052] PnPBIOS: Disabled by ACPI PNP
[    0.646060] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.646062] system 00:01: ioport range 0x290-0x30f has been reserved
[    0.646064] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.646070] system 00:07: ioport range 0x400-0x4bf could not be reserved
[    0.646074] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.646079] system 00:0a: iomem range 0xf0000-0xfffff could not be reserved
[    0.646081] system 00:0a: iomem range 0xcff00000-0xcfffffff has been reserved
[    0.646083] system 00:0a: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.646085] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.646087] system 00:0a: iomem range 0x100000-0xcfedffff could not be reserved
[    0.646090] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.646092] system 00:0a: iomem range 0xfed14000-0xfed1dfff has been reserved
[    0.646094] system 00:0a: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.646096] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.646098] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.646100] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.646102] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.680750] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.680753] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.680756] pci 0000:00:01.0:   MEM window: 0xf8000000-0xfbffffff
[    0.680759] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.680762] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.680764] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.680768] pci 0000:00:1c.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.680772] pci 0000:00:1c.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.680777] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.680779] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.680783] pci 0000:00:1c.1:   MEM window: 0xfd700000-0xfd7fffff
[    0.680786] pci 0000:00:1c.1:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.680791] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.680794] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    0.680797] pci 0000:00:1c.2:   MEM window: 0xfdd00000-0xfddfffff
[    0.680801] pci 0000:00:1c.2:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.680805] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.680808] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.680812] pci 0000:00:1e.0:   MEM window: 0xfda00000-0xfdafffff
[    0.680815] pci 0000:00:1e.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.680825] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.680828] pci 0000:00:01.0: setting latency timer to 64
[    0.680834] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.680837] pci 0000:00:1c.0: setting latency timer to 64
[    0.680843] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.680847] pci 0000:00:1c.1: setting latency timer to 64
[    0.680853] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.680856] pci 0000:00:1c.2: setting latency timer to 64
[    0.680861] pci 0000:00:1e.0: setting latency timer to 64
[    0.680865] bus: 00 index 0 io port: [0x00-0xffff]
[    0.680867] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.680868] bus: 01 index 0 io port: [0xa000-0xafff]
[    0.680870] bus: 01 index 1 mmio: [0xf8000000-0xfbffffff]
[    0.680872] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.680873] bus: 01 index 3 mmio: [0x0-0x0]
[    0.680875] bus: 02 index 0 io port: [0x9000-0x9fff]
[    0.680876] bus: 02 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.680878] bus: 02 index 2 mmio: [0xfd800000-0xfd8fffff]
[    0.680879] bus: 02 index 3 mmio: [0x0-0x0]
[    0.680881] bus: 03 index 0 io port: [0xd000-0xdfff]
[    0.680883] bus: 03 index 1 mmio: [0xfd700000-0xfd7fffff]
[    0.680884] bus: 03 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.680886] bus: 03 index 3 mmio: [0x0-0x0]
[    0.680887] bus: 04 index 0 io port: [0xb000-0xbfff]
[    0.680889] bus: 04 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.680890] bus: 04 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.680892] bus: 04 index 3 mmio: [0x0-0x0]
[    0.680893] bus: 05 index 0 io port: [0xc000-0xcfff]
[    0.680895] bus: 05 index 1 mmio: [0xfda00000-0xfdafffff]
[    0.680896] bus: 05 index 2 mmio: [0xfd900000-0xfd9fffff]
[    0.680898] bus: 05 index 3 io port: [0x00-0xffff]
[    0.680899] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.680906] NET: Registered protocol family 2
[    0.696043] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.696223] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.696579] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.696769] TCP: Hash tables configured (established 131072 bind 65536)
[    0.696771] TCP reno registered
[    0.704069] NET: Registered protocol family 1
[    0.704167] checking if image is initramfs... it is
[    1.180533] Switched to high resolution mode on CPU 3
[    1.180557] Switched to high resolution mode on CPU 2
[    1.180621] Switched to high resolution mode on CPU 1
[    1.183995] Switched to high resolution mode on CPU 0
[    1.235916] Freeing initrd memory: 7433k freed
[    1.236270] cpufreq: No nForce2 chipset.
[    1.236393] audit: initializing netlink socket (disabled)
[    1.236413] type=2000 audit(1256093000.233:1): initialized
[    1.242740] highmem bounce pool size: 64 pages
[    1.242744] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.243951] VFS: Disk quotas dquot_6.5.1
[    1.243997] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.244518] fuse init (API version 7.10)
[    1.244588] msgmni has been set to 1665
[    1.244781] alg: No test for stdrng (krng)
[    1.244795] io scheduler noop registered
[    1.244796] io scheduler anticipatory registered
[    1.244798] io scheduler deadline registered
[    1.244809] io scheduler cfq registered (default)
[    1.244951] pci 0000:01:00.0: Boot video device
[    1.247594] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.247620] pcieport-driver 0000:00:01.0: found MSI capability
[    1.247638] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.247645] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.247656] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.247691] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.247718] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.247737] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.247746] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.247756] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.247765] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.247808] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.247834] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.247853] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.247863] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.247872] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.247884] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.247927] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.247954] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.247973] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.247982] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.247992] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.248004] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.248056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.248327] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.248443] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.248445] ACPI: Power Button (FF) [PWRF]
[    1.248480] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.248482] ACPI: Power Button (CM) [PWRB]
[    1.248527] fan PNP0C0B:00: registered as cooling_device0
[    1.248531] ACPI: Fan [FAN] (on)
[    1.248868] ACPI: SSDT CFEE8140, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    1.249056] processor ACPI_CPU:00: registered as cooling_device1
[    1.249228] ACPI: SSDT CFEE8600, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    1.249403] processor ACPI_CPU:01: registered as cooling_device2
[    1.249583] ACPI: SSDT CFEE8760, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20041203)
[    1.249755] processor ACPI_CPU:02: registered as cooling_device3
[    1.249933] ACPI: SSDT CFEE88C0, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20041203)
[    1.250105] processor ACPI_CPU:03: registered as cooling_device4
[    1.448283] thermal LNXTHERM:01: registered as thermal_zone0
[    1.848085] ACPI: Thermal Zone [THRM] (44 C)
[    1.848124] isapnp: Scanning for PnP cards...
[    2.199585] isapnp: No Plug & Play device found
[    2.209606] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.210403] brd: module loaded
[    2.210637] loop: module loaded
[    2.210693] Fixed MDIO Bus: probed
[    2.210698] PPP generic driver version 2.4.2
[    2.210741] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.210763] Driver 'sd' needs updating - please use bus_type methods
[    2.210770] Driver 'sr' needs updating - please use bus_type methods
[    2.210825] ata_piix 0000:00:1f.2: version 2.12
[    2.210837] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.210840] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    2.210873] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.210945] scsi0 : ata_piix
[    2.211043] scsi1 : ata_piix
[    2.211563] ata1: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[    2.211566] ata2: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[    2.684048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.692184] ata1.00: ATAPI: HL-DT-STDVD+-RW GSA-H31N, B110, max UDMA/100
[    2.708197] ata1.00: configured for UDMA/100
[    3.184036] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.204158] ata2.00: ATA-7: WDC WD7500AAKS-00RBA0, 30.04G30, max UDMA/133
[    3.204161] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.220629] ata2.00: configured for UDMA/133
[    3.222362] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H31N B110 PQ: 0 ANSI: 5
[    3.228130] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.228133] Uniform CD-ROM driver Revision: 3.20
[    3.228207] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.228239] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.228305] scsi 1:0:0:0: Direct-Access     ATA      WDC WD7500AAKS-0 30.0 PQ: 0 ANSI: 5
[    3.228376] sd 1:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.228389] sd 1:0:0:0: [sda] Write Protect is off
[    3.228391] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.228410] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.228454] sd 1:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.228465] sd 1:0:0:0: [sda] Write Protect is off
[    3.228467] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.228486] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.228488]  sda: sda1 sda2 < sda5 sda6 >
[    3.254769] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.254807] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.254832] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.254835] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.254868] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.254918] scsi2 : ata_piix
[    3.255012] scsi3 : ata_piix
[    3.255280] ata3: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[    3.255283] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[    3.582065] ata3: SATA link down (SStatus 0 SControl 300)
[    3.910542] ata4: SATA link down (SStatus 0 SControl 300)
[    3.910842] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.910861] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    3.910937] scsi4 : pata_jmicron
[    3.911015] scsi5 : pata_jmicron
[    3.911416] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 17
[    3.911418] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 17
[    4.220310] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.220323] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.220349] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.220352] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.220402] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.224306] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.224316] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    4.236012] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.236070] usb usb1: configuration #1 chosen from 1 choice
[    4.236091] hub 1-0:1.0: USB hub found
[    4.236095] hub 1-0:1.0: 6 ports detected
[    4.236177] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.236185] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.236187] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.236222] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.240114] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.240124] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    4.252012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.252051] usb usb2: configuration #1 chosen from 1 choice
[    4.252072] hub 2-0:1.0: USB hub found
[    4.252076] hub 2-0:1.0: 6 ports detected
[    4.252145] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.252157] uhci_hcd: USB Universal Host Controller Interface driver
[    4.252176] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.252182] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.252184] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.252217] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.252241] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    4.252292] usb usb3: configuration #1 chosen from 1 choice
[    4.252311] hub 3-0:1.0: USB hub found
[    4.252315] hub 3-0:1.0: 2 ports detected
[    4.252378] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.252383] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.252385] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.252421] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.252444] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    4.252495] usb usb4: configuration #1 chosen from 1 choice
[    4.252513] hub 4-0:1.0: USB hub found
[    4.252517] hub 4-0:1.0: 2 ports detected
[    4.252580] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.252584] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.252587] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.252619] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.252637] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[    4.252689] usb usb5: configuration #1 chosen from 1 choice
[    4.252707] hub 5-0:1.0: USB hub found
[    4.252712] hub 5-0:1.0: 2 ports detected
[    4.252774] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.252778] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.252780] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.252819] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.252837] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    4.252886] usb usb6: configuration #1 chosen from 1 choice
[    4.252907] hub 6-0:1.0: USB hub found
[    4.252911] hub 6-0:1.0: 2 ports detected
[    4.252972] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.252977] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.252979] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.253023] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.253041] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    4.253094] usb usb7: configuration #1 chosen from 1 choice
[    4.253115] hub 7-0:1.0: USB hub found
[    4.253119] hub 7-0:1.0: 2 ports detected
[    4.253179] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.253183] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.253185] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.253218] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.253236] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    4.253288] usb usb8: configuration #1 chosen from 1 choice
[    4.253306] hub 8-0:1.0: USB hub found
[    4.253311] hub 8-0:1.0: 2 ports detected
[    4.253422] PNP: No PS/2 controller found. Probing ports directly.
[    4.256213] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.256218] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.261035] mice: PS/2 mouse device common for all mice
[    4.273058] rtc_cmos 00:03: RTC can wake from S4
[    4.273083] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.273103] rtc0: alarms up to one month, 242 bytes nvram
[    4.273150] device-mapper: uevent: version 1.0.3
[    4.273245] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.273562] device-mapper: multipath: version 1.0.5 loaded
[    4.273564] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.273669] EISA: Probing bus 0 at eisa.0
[    4.273692] EISA: Detected 0 cards.
[    4.273955] cpuidle: using governor ladder
[    4.273957] cpuidle: using governor menu
[    4.274366] TCP cubic registered
[    4.274445] NET: Registered protocol family 10
[    4.274776] lo: Disabled Privacy Extensions
[    4.275031] NET: Registered protocol family 17
[    4.275044] Bluetooth: L2CAP ver 2.11
[    4.275046] Bluetooth: L2CAP socket layer initialized
[    4.275048] Bluetooth: SCO (Voice Link) ver 0.6
[    4.275050] Bluetooth: SCO socket layer initialized
[    4.275120] Bluetooth: RFCOMM socket layer initialized
[    4.275126] Bluetooth: RFCOMM TTY layer initialized
[    4.275128] Bluetooth: RFCOMM ver 1.10
[    4.275927] Using IPI No-Shortcut mode
[    4.275987] registered taskstats version 1
[    4.276108]   Magic number: 13:495:713
[    4.276177] rtc_cmos 00:03: setting system clock to 2009-10-21 02:43:24 UTC (1256093004)
[    4.276179] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.276181] EDD information not available.
[    4.276361] Freeing unused kernel memory: 532k freed
[    4.276475] Write protecting the kernel text: 4120k
[    4.276522] Write protecting the kernel read-only data: 1524k
[    4.413209] Floppy drive(s): fd0 is 1.44M
[    4.433107] FDC 0 is a post-1991 82077
[    4.433186] sky2 driver version 1.22
[    4.433230] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.433242] sky2 0000:04:00.0: setting latency timer to 64
[    4.433291] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
[    4.465217] sky2 0000:04:00.0: Marvell Yukon 88E8056 Gigabit Ethernet Controller
[    4.465220]  Part Number: Yukon 88E8056
[    4.465222]  Engineering Level: Rev. 1.3
[    4.465223]  Manufacturer: Marvell
[    4.465294] sky2 0000:04:00.0: irq 2299 for MSI/MSI-X
[    4.465932] sky2 eth0: addr 00:50:8d:9c:9e:47
[    4.721711] PM: Starting manual resume from disk
[    4.721714] PM: Resume from partition 8:5
[    4.721715] PM: Checking hibernation image.
[    4.721907] PM: Resume from disk failed.
[    4.744767] kjournald starting.  Commit interval 5 seconds
[    4.744775] EXT3-fs: mounted filesystem with ordered data mode.
[    4.873012] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    5.049292] usb 3-2: configuration #1 chosen from 1 choice
[    5.292015] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.461474] usb 4-2: configuration #1 chosen from 1 choice
[    5.773154] udev: starting version 141
[    6.294264] usbcore: registered new interface driver hiddev
[    6.294352] usbcore: registered new interface driver usbhid
[    6.294355] usbhid: v2.6:USB HID core driver
[    6.297225] lirc_dev: IR Remote Control driver registered, major 61 
[    6.336153] Linux agpgart interface v0.103
[    6.341377] iTCO_vendor_support: vendor-support=0
[    6.349888] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    6.350118] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0460)
[    6.350193] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    6.366753] input: PC Speaker as /devices/platform/pcspkr/input/input3
[    6.456398] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    6.461132] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-2/input0
[    6.489144] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    6.489798] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input5
[    6.500172] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-2/input1
[    6.505208] 
[    6.505211] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    6.505213] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[    6.616014] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[    6.712796] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.712896] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.745906] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    6.772332] lirc_dev: lirc_register_plugin: sample_rate: 0
[    6.776323] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb4:2
[    6.776355] usbcore: registered new interface driver lirc_mceusb2
[    7.295679] lp: driver loaded but no devices found
[    7.486415] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[    8.125294] EXT3 FS on sda1, internal journal
[    8.961068] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[    8.961697] SGI XFS Quota Management subsystem
[    8.993743] XFS mounting filesystem sda6
[    9.104583] Ending clean XFS mount for filesystem: sda6
[    9.667731] type=1505 audit(1256093009.888:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2065
[    9.667811] type=1505 audit(1256093009.888:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2065
[    9.667841] type=1505 audit(1256093009.888:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2065
[    9.667872] type=1505 audit(1256093009.888:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2065
[    9.769572] type=1505 audit(1256093009.992:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2070
[    9.769719] type=1505 audit(1256093009.992:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2070
[    9.790668] type=1505 audit(1256093010.013:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2074
[    9.811463] type=1505 audit(1256093010.031:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2078
[   10.170178] RPC: Registered udp transport module.
[   10.170181] RPC: Registered tcp transport module.
[   10.249655] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   12.037409] usbcore: registered new interface driver lirc_mceusb
[   12.037413] lirc_mceusb: USB Microsoft IR Transceiver Driver v0.2
[   13.779893] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   13.795733] NFSD: starting 90-second grace period
[   20.002547] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.002550] Bluetooth: BNEP filters: protocol multicast
[   20.043282] Bridge firewalling registered
[   21.748401] ppdev: user-space parallel port driver
[   25.781471] sky2 eth0: enabling interface
[   25.781626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.969411] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   28.969561] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   39.560006] eth0: no IPv6 routers present


```

The exact version of the Video Card
```

$lspic
.....
Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```And the IR Blaster Info

```

$lsusb
....
SMK Manufacturing, Inc. eHome Infrared Receiver

```I have installled the bleeding edge version of the ivtv driver and when i tried the following command

```

cat /dev/video0 > test.mpg

cat /dev/video0 | vlc

```It created a 1GB file!!! I cannot open this file using either vlc or totem.

I tried using the ivtv-tune to set the channel and i tried setting it to 1 , 5 and still no luck in viewing the video in vlc

One thing i am unable to understand is ivtv-tune has an option to list all the channels and it showed 

```

ivtv-tune -l
Channels/Frequencies (MHz) for 'us-cable':
1    73.250
2    55.250
..
125
T7    8.250
T8    14.250
T9    20.250
T10    26.250
T11    32.250
T12    38.250
T13    44.250
T14    50.250


```Why it is showing only 125 Channels. Are these the channels that are available in TV but not in the Cable STB ? If so i should only be setting the channel to 3 ? I tried it and still the vlc didn't show any video


Thanks
Mars

---

### Post by luigidk on 2009-10-21
I just powered up my MythTV today and nothing was working!

Looked at my Capture cards - and my PVR-150 was saying it was my AverTVHD a180 card????  (no question that I set this up correctly).

This happened 1 time before when I was setting it all up.

So I physically removed my AVERTVHD a180 card - so far so good.

The reason I upgraded to 9.04 was that my monolithmc mythtv distro (on ubuntu 7.10) was wiped out when I had a disk crash during a storm... I think my AVERMEDIA card may have been hit also???

---

### Post by mars76 on 2009-10-21
Hi,

  I have used the get_dvb_firmware script to load the firmware for A180 and restarted my machine now i am getting the following.

 ```

 $ lspci -vv
05:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at fdaff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```And when i use dmesg

```

6.806677] saa7133[0]: found at 0000:05:04.0, rev: 209, irq: 22, latency: 0, mmio: 0xfdaff000
[    6.806684] saa7133[0]: subsystem: 0000:0000, board: AVerMedia AVerTVHD MCE A180 [card=75,insmod option]
[    6.806732] saa7133[0]: board init: gpio is 10400
[    6.908582] saa7133[0]: Huh, no eeprom present (err=-5)?
[    6.909110] saa7133[0]: registered device video0 [v4l2]
[    6.909148] saa7133[0]: registered device vbi0
[    6.927748] saa7133[0]/alsa: saa7133[0] at 0xfdaff000 irq 22 registered as card -2
[    7.046869] saa7133[0]/dvb: frontend initialization failed

```  Could some one pls let me know why it is getting registered as -2 ?? What's the solution for this..

And i don't see /dev/dvb/ any more ..

Thanks
mars

---

### Post by klc5555 on 2009-10-22
> **mars76 said:**
> Hi,

  I have used the get_dvb_firmware script to load the firmware for A180 and restarted my machine now i am getting the following.

 ```

 $ lspci -vv
05:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at fdaff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```And when i use dmesg

```

6.806677] saa7133[0]: found at 0000:05:04.0, rev: 209, irq: 22, latency: 0, mmio: 0xfdaff000
[    6.806684] saa7133[0]: subsystem: 0000:0000, board: AVerMedia AVerTVHD MCE A180 [card=75,insmod option]
[    6.806732] saa7133[0]: board init: gpio is 10400
[    6.908582] saa7133[0]: Huh, no eeprom present (err=-5)?
[    6.909110] saa7133[0]: registered device video0 [v4l2]
[    6.909148] saa7133[0]: registered device vbi0
[    6.927748] saa7133[0]/alsa: saa7133[0] at 0xfdaff000 irq 22 registered as card -2
[    7.046869] saa7133[0]/dvb: frontend initialization failed

```  Could some one pls let me know why it is getting registered as -2 ?? What's the solution for this..

And i don't see /dev/dvb/ any more ..

Thanks
mars

Looks like the saa7134 module was loaded with the wrong parameters for an analog Philips tuner (/dev/video0).

Try the following:

Stop the backend.

From a terminal, unload the saa7134 module:

sudo rmmod saa7134-dvb
sudo rmmod saa7134

Now load the module manually by

sudo modprobe saa7134 card=75 tuner=68 disable_ir=1 

and see if this gets it going with the right parameters (producing a /dev/dvb)

---

### Post by mars76 on 2009-10-22
Hi klc5555,

  Thanks for the info..The Card is getting identified properly..

  I have reran the backend and front end setups and now i am getting the same error which i was getting earlier..

```

009-10-22 22:21:54.802 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-10-22 22:21:54.803 DVBChan(4:0) Error: SetChannelByString(1): Failed to initialize multiplex options
2009-10-22 22:21:54.803 TVRec(4) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-22 22:21:54.804 TVRec(4): Changing from WatchingLiveTV to None

2009-10-22 22:24:21.149 DVBChan(4:0) Error: Opening DVB frontend device failed.
            eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.

```I am not sure why the log says no valid capture cards are defined in the DB after adding the cards using myth backend..

 My ScheduleDirect trail has expired . Does it has any thing to do with info not getting stored into the DB.

 I have installed phpmyadmin and checked the "capturecard" table and there are no rows in it.

 Am i missing something. I ran the mythtv setup from the control center as well and got the same results.

 I added A180 as **DVB DTV capture card (v3.x). **

Thanks..

---

### Post by klc5555 on 2009-10-23
> **mars76 said:**
> Hi klc5555,

  Thanks for the info..The Card is getting identified properly..

  I have reran the backend and front end setups and now i am getting the same error which i was getting earlier..

```

009-10-22 22:21:54.802 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-10-22 22:21:54.803 DVBChan(4:0) Error: SetChannelByString(1): Failed to initialize multiplex options
2009-10-22 22:21:54.803 TVRec(4) Error: Failed to set channel to 1. Reverting to kState_None
2009-10-22 22:21:54.804 TVRec(4): Changing from WatchingLiveTV to None

2009-10-22 22:24:21.149 DVBChan(4:0) Error: Opening DVB frontend device failed.
            eno: No such file or directory (2)
ERROR: no valid capture cards are defined in the database.

```I am not sure why the log says no valid capture cards are defined in the DB after adding the cards using myth backend..

 My ScheduleDirect trail has expired . Does it has any thing to do with info not getting stored into the DB.

 I have installed phpmyadmin and checked the "capturecard" table and there are no rows in it.

 Am i missing something. I ran the mythtv setup from the control center as well and got the same results.

 I added A180 as **DVB DTV capture card (v3.x). **

Thanks..

Did the card scan successfully for channels and do channel locks when you did your scan under Input Connections in the backend setup?

---

### Post by mars76 on 2009-10-23
Yes,

  I am able to scan the channels successfully..The Signal Strength shows around 90%.

When i go to the channel Editor i see the channels ( i am using FIOS and hence the selected scan type is us-cable , Unencrypted QAM-256).

 Also i used mc2xml to fill the database.

  When i do cat /dev/video0 > test.mpg for few sec it generated a 150MB file. I cannot play this file ( nothing shows up in the video) using vlc.

Thanks

---

### Post by klc5555 on 2009-10-23
> **mars76 said:**
> Yes,

  I am able to scan the channels successfully..The Signal Strength shows around 90%.

When i go to the channel Editor i see the channels ( i am using FIOS and hence the selected scan type is us-cable , Unencrypted QAM-256).

 Also i used mc2xml to fill the database.

  When i do cat /dev/video0 > test.mpg for few sec it generated a 150MB file. I cannot play this file ( nothing shows up in the video) using vlc.

Thanks

There shouldn't be any output to /dev/video0. That output is for analog. QAM-256 is digital. 

If you're scanning and getting good signal strength but no channel locks on the unencrypted channels, that implies that you've specified the card correctly in the modprobe line, but not the tuner. If you're getting strong signals on the channel scans, and getting channel locks on the unencrypted channels, but the card still doesn't seem to be able to tune them, then in my experience it's usually been that the saa7134 firmware (that is the file "dvb-fe-nxt2004.fw") hasn't loaded correctly. 

You can usually check whether the firmware has loaded correctly at a prompt by issuing a command along the lines of:

dmesg |grep nxt

Then, finally, as the wiki page mentions, sometimes these cards get themselves into a state where it requires a shutdown and a cold start (a simple warm restart won't do it) before they begin tuning properly. 

This will of course require that you have blacklisted the saa7134 /saa7134-dvb modules so that they don't autoload at boot with the wrong parameters (they seem to ignore options files), and that you then load the saa7134 with the correct parameters, by including a modprobe line with the correct parameters in your rc.local.

---

### Post by mars76 on 2009-10-24
Hi,

   I have blocked the modules saa7134

  This is what my /etc/modprobe.d/options.conf looks like

```

options saa7134 card=75
options saa7134-dvb

```/etc/modprobe.d/blacklist
```

blacklist saa7134

```lspci -vnn
```

05:04.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Avermedia Technologies Inc Device [1461:1044]
    Flags: bus master, medium devsel, latency 84, IRQ 22
    Memory at fdaff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```dmesg | grep nxt2004

```

 7.724510] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[    7.724515] saa7134 0000:05:04.0: firmware: requesting dvb-fe-nxt2004.fw
[    7.769375] nxt2004: Waiting for firmware upload(2)...
[    9.308013] nxt2004: Firmware upload complete

```How ever when i try to scan the channels using /usr/bin/scan ( i have installed the dvb-apps and dvb-utils packages)

sudo /usr/sbin/scan  /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > .azap/channels.conf

I am getting 

warning >>> TUNING FAILED!! for all the frequencies.

I have stopped the mythtv-backend before starting the tuen ( otherwise it says the tuner is busy) . And the scan take lot of time.

I have cold started my machine before i performed all the above mentioned tasks..

Thanks..

---

