---
title: "SMC2532W-B card does not work"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by jemvyc on 2008-12-14
I have Ubuntu 8.10 installed in a dual boot configuration on a Compaq Presario 2135.  My SMC 2532W-B PCMCIA high power wireless adapter will not connect using Ubuntu.  That same card works OK using Windows XP, but using Intrepid, it apprears to be recognized, identifies the network, but apparently can't get an IP address, then disconnects. The network I am trying to use is unsecured. 

On the same computer, and the same network, my 8187 based USB adapter works on both operating systems.

Would someone please help me to diagnose the cause of this problem

Jim

---

### Post by ieee488 on 2008-12-14
Your card is suppose to be usable as-is with Linux.

Go to section 3.6 at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) which will show you how to troubleshoot

---

### Post by jemvyc on 2008-12-14
I am trying to work thru your suggestions, and first I find references to ndiswrapper.  As I am using intrepid and the network manager is supposed to be handling my card, I am reluctant to install ndiswrapper and mix the whole situation up with both drivers running.

Section 3.6.2 says to open System | Administration | Networking.  Intrepid does not have a networking under system administration.  Under system administration is only "network tools".  Network tools takes me to devices and other things presuming that I have a network working.  Thus I cannot find properties and also the enable roaming.

I guess the problem is that I haven't the slightest idea what these things are telling me.  I am ready to give up until I get to a place where I can access an ethernet connection.

What follows is the results I got from various terminal commands:

First with the SMC card, which does not work:

jim@jim-laptop:~$ sudo lshw -C network

  *-network               

       description: SMC2532W-B EliteConnect Wireless Adapter

       vendor: SMC

       physical id: 0

       slot: Socket 0

       resources: irq:3

  *-network

       description: Ethernet interface

       product: DP83815 (MacPhyter) Ethernet Controller

       vendor: National Semiconductor Corporation

       physical id: 12

       bus info: pci@0000:00:12.0

       logical name: eth0

       version: 00

       serial: 00:0b:cd:32:39:42

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s

  *-network:0

       description: Wireless interface

       physical id: 1

       logical name: wlan1

       serial: 00:04:e2:81:ff:36

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=hostap firmware=1.8.2 multicast=yes wireless=IEEE 802.11b

  *-network:1 DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: a2:14:ad:d2:44:d7

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

jim@jim-laptop:~$ 


Next with the TEW USB, which does work, but does not have the sensitivity to reach the network from this location.

jim@jim-laptop:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:32:39:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:35:dd:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:45:8b:6e:f7:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jim@jim-laptop

Next from dmesg after trying the SMC card

[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002bf70
[    0.000000] On node 0 totalpages: 179983
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 174437 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (01634000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c3f80000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 178400
[    0.000000] Kernel command line: root=UUID=eb9e7c10-64c4-4df2-85f8-cd17a6f2df35 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1794.227 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 699588k/720320k available (2572k kernel code, 20116k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xec800000 - 0xff3fe000   ( 299 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xebf70000   ( 703 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 3588.45 BogoMIPS (lpj=7176908)
[    0.004063] Security Framework initialized
[    0.004081] SELinux:  Disabled at boot.
[    0.004122] AppArmor: AppArmor initialized
[    0.004145] Mount-cache hash table entries: 512
[    0.004521] Initializing cgroup subsys ns
[    0.004536] Initializing cgroup subsys cpuacct
[    0.004542] Initializing cgroup subsys memory
[    0.004583] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004589] CPU: L2 cache: 256K
[    0.004594] CPU: Hyper-Threading is disabled
[    0.004629] Checking 'hlt' instruction... OK.
[    0.021028] SMP alternatives: switching to UP code
[    0.035842] Freeing SMP alternatives: 11k freed
[    0.035856] ACPI: Core revision 20080609
[    0.045352] ACPI: Checking initramfs for custom DSDT
[    0.584021] ACPI: setting ELCR to 0200 (from 0420)
[    0.586390] weird, boot CPU (#0) not listedby the BIOS.
[    0.586397] SMP motherboard not detected.
[    0.586403] Local APIC not detected. Using dummy APIC emulation.
[    0.586408] SMP disabled
[    0.586606] Brought up 1 CPUs
[    0.586614] Total of 1 processors activated (3588.45 BogoMIPS).
[    0.586644] CPU0 attaching sched-domain:
[    0.586652]  domain 0: span 0 level CPU
[    0.586657]   groups: 0
[    0.587385] net_namespace: 840 bytes
[    0.587414] Booting paravirtualized kernel on bare hardware
[    0.587820] Time: 16:29:15  Date: 12/14/08
[    0.587910] NET: Registered protocol family 16
[    0.589278] EISA bus registered
[    0.589348] ACPI: bus type pci registered
[    0.648471] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[    0.648480] PCI: Using configuration type 1 for base access
[    0.653762] ACPI: EC: Look up EC in DSDT
[    0.665423] ACPI: Interpreter enabled
[    0.665439] ACPI: (supports S0 S3 S4 S5)
[    0.665474] ACPI: Using PIC for interrupt routing
[    0.668133] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.701604] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.701612] ACPI: EC: driver started in interrupt mode
[    0.701835] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.702086] PCI: 0000:00:00.0 reg 10 32bit mmio: [d4000000, d7ffffff]
[    0.702098] PCI: 0000:00:00.0 reg 14 32bit mmio: [d0005000, d0005fff]
[    0.702184] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0000000, d0000fff]
[    0.702228] pci 0000:00:02.0: PME# supported from D3cold
[    0.702235] pci 0000:00:02.0: PME# disabled
[    0.702268] PCI: 0000:00:06.0 reg 10 io port: [1000, 10ff]
[    0.702277] PCI: 0000:00:06.0 reg 14 32bit mmio: [d0001000, d0001fff]
[    0.702315] pci 0000:00:06.0: supports D1
[    0.702318] pci 0000:00:06.0: supports D2
[    0.702321] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.702327] pci 0000:00:06.0: PME# disabled
[    0.702438] PCI: 0000:00:08.0 reg 10 32bit mmio: [d0002000, d0002fff]
[    0.702447] PCI: 0000:00:08.0 reg 14 io port: [1400, 14ff]
[    0.702483] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.702489] pci 0000:00:08.0: PME# disabled
[    0.702522] PCI: 0000:00:0a.0 reg 10 32bit mmio: [d0003000, d0003fff]
[    0.702538] pci 0000:00:0a.0: supports D1
[    0.702541] pci 0000:00:0a.0: supports D2
[    0.702545] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.702551] pci 0000:00:0a.0: PME# disabled
[    0.702602] PCI: 0000:00:10.0 reg 20 io port: [2000, 200f]
[    0.702685] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.702691] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.702724] PCI: 0000:00:12.0 reg 10 io port: [2400, 24ff]
[    0.702733] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0004000, d0004fff]
[    0.702760] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, ffff]
[    0.702776] pci 0000:00:12.0: supports D1
[    0.702778] pci 0000:00:12.0: supports D2
[    0.702782] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.702788] pci 0000:00:12.0: PME# disabled
[    0.702853] PCI: 0000:01:05.0 reg 10 32bit mmio: [d8000000, dfffffff]
[    0.702862] PCI: 0000:01:05.0 reg 14 io port: [9000, 90ff]
[    0.702871] PCI: 0000:01:05.0 reg 18 32bit mmio: [d0300000, d030ffff]
[    0.702892] PCI: 0000:01:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.702912] pci 0000:01:05.0: supports D1
[    0.702915] pci 0000:01:05.0: supports D2
[    0.702952] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.702958] PCI: bridge 0000:00:01.0 32bit mmio: [d0300000, d03fffff]
[    0.702965] PCI: bridge 0000:00:01.0 32bit mmio pref: [d8000000, dfffffff]
[    0.702994] bus 00 -> node 0
[    0.703017] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.703172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.709491] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[    0.709849] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[    0.710191] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 10) *0, disabled.
[    0.710530] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 10) *0, disabled.
[    0.710872] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[    0.711214] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[    0.711553] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[    0.711893] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[    0.712340] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 *10)
[    0.712972] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.713134] pnp: PnP ACPI init
[    0.713169] ACPI: bus type pnp registered
[    0.718029] pnp 00:07: io resource (0x8004-0x8005) overlaps 0000:00:11.0 BAR 7 (0x8000-0x803f), disabling
[    0.723030] pnp: PnP ACPI: found 10 devices
[    0.723041] ACPI: ACPI bus type pnp unregistered
[    0.723054] PnPBIOS: Disabled by ACPI PNP
[    0.724654] PCI: Using ACPI for IRQ routing
[    0.724975] NET: Registered protocol family 8
[    0.724975] NET: Registered protocol family 20
[    0.724975] NetLabel: Initializing
[    0.724975] NetLabel:  domain hash size = 128
[    0.724975] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.724975] NetLabel:  unlabeled traffic allowed by default
[    0.724975] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.724975]    actual entries 65620
[    0.725175] AppArmor: AppArmor Filesystem Enabled
[    0.725294] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.725294] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.725294] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.725294] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.725294] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.725294] system 00:07: ioport range 0xff00-0xff01 has been reserved
[    0.725294] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.725294] system 00:07: iomem range 0xd0005000-0xd0005fff has been reserved
[    0.763303] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.763314] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.763321] pci 0000:00:01.0:   MEM window: 0xd0300000-0xd03fffff
[    0.763327] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.763336] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.763340] pci 0000:00:0a.0:   IO window: 0x001800-0x0018ff
[    0.763347] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
[    0.763353] pci 0000:00:0a.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.763359] pci 0000:00:0a.0:   MEM window: 0x44000000-0x47ffffff
[    0.763390] pci 0000:00:0a.0: enabling device (0005 -> 0007)
[    0.763928] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[    0.763935] PCI: setting IRQ 11 as level-triggered
[    0.763943] pci 0000:00:0a.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[    0.763953] bus: 00 index 0 io port: [0, ffff]
[    0.763959] bus: 00 index 1 mmio: [0, ffffffff]
[    0.763964] bus: 01 index 0 io port: [9000, 9fff]
[    0.763968] bus: 01 index 1 mmio: [d0300000, d03fffff]
[    0.763972] bus: 01 index 2 mmio: [d8000000, dfffffff]
[    0.763975] bus: 01 index 3 mmio: [0, 0]
[    0.763980] bus: 02 index 0 io port: [1800, 18ff]
[    0.763983] bus: 02 index 1 io port: [1c00, 1cff]
[    0.763987] bus: 02 index 2 mmio: [40000000, 43ffffff]
[    0.763991] bus: 02 index 3 mmio: [44000000, 47ffffff]
[    0.764056] NET: Registered protocol family 2
[    0.764412] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.765069] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.767460] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.768914] TCP: Hash tables configured (established 131072 bind 65536)
[    0.768934] TCP reno registered
[    0.769353] NET: Registered protocol family 1
[    0.769648] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.290711]  it is
[    1.917715] Freeing initrd memory: 8004k freed
[    1.918306] Simple Boot Flag at 0x37 set to 0x1
[    1.919735] audit: initializing netlink socket (disabled)
[    1.919780] type=2000 audit(1229272155.916:1): initialized
[    1.927630] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.935683] VFS: Disk quotas dquot_6.5.1
[    1.936100] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.936508] msgmni has been set to 1382
[    1.936973] io scheduler noop registered
[    1.936983] io scheduler anticipatory registered
[    1.936991] io scheduler deadline registered
[    1.937048] io scheduler cfq registered (default)
[    2.152100] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    2.152153] pci 0000:01:05.0: Boot video device
[    2.153457] isapnp: Scanning for PnP cards...
[    2.507659] isapnp: No Plug & Play device found
[    2.798920] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.799257] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.806093] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.807721] serial 0000:00:08.0: enabling device (0000 -> 0003)
[    2.808399] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[    2.808408] PCI: setting IRQ 10 as level-triggered
[    2.808415] serial 0000:00:08.0: PCI INT A -> Link[LNK6] -> GSI 10 (level, low) -> IRQ 10
[    2.808430] serial 0000:00:08.0: PCI INT A disabled
[    2.820931] brd: module loaded
[    2.821190] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.821638] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.836786] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.836807] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.840138] mice: PS/2 mouse device common for all mice
[    2.841645] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.841688] rtc0: alarms up to one month, y3k
[    2.842208] EISA: Probing bus 0 at eisa.0
[    2.842226] Cannot allocate resource for EISA slot 1
[    2.842233] Cannot allocate resource for EISA slot 2
[    2.842265] Cannot allocate resource for EISA slot 8
[    2.842270] EISA: Detected 0 cards.
[    2.842280] cpuidle: using governor ladder
[    2.842286] cpuidle: using governor menu
[    2.843442] TCP cubic registered
[    2.843529] Using IPI No-Shortcut mode
[    2.846507] registered taskstats version 1
[    2.846818]   Magic number: 4:711:489
[    2.847217] rtc_cmos 00:02: setting system clock to 2008-12-14 16:29:20 UTC (1229272160)
[    2.847226] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.847232] EDD information not available.
[    2.848259] Freeing unused kernel memory: 424k freed
[    2.848366] Write protecting the kernel text: 2576k
[    2.848424] Write protecting the kernel read-only data: 936k
[    2.885433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.307019] fuse init (API version 7.9)
[    3.585848] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.591054] processor ACPI0007:00: registered as cooling_device0
[    3.591070] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.617613] thermal LNXTHERM:01: registered as thermal_zone0
[    3.619399] ACPI: Thermal Zone [THRM] (46 C)
[    5.440933] usbcore: registered new interface driver usbfs
[    5.441027] usbcore: registered new interface driver hub
[    5.454733] No dock devices found.
[    5.500875] usbcore: registered new device driver usb
[    5.622465] SCSI subsystem initialized
[    5.622715] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.623311] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[    5.623323] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNK8] -> GSI 10 (level, low) -> IRQ 10
[    5.623355] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.623497] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    5.623542] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[    5.628202] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    5.628207]   originally by Donald Becker <becker@scyld.com>
[    5.628212]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    5.676680] usb usb1: configuration #1 chosen from 1 choice
[    5.676766] hub 1-0:1.0: USB hub found
[    5.676792] hub 1-0:1.0: 4 ports detected
[    5.719366] libata version 3.00 loaded.
[    5.885321] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    5.885433] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    5.886079] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    5.886091] natsemi 0000:00:12.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    5.888559] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0b:cd:32:39:42, IRQ 10, port TP.
[    5.895987] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    5.898097] scsi0 : pata_ali
[    5.898458] scsi1 : pata_ali
[    5.898957] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    5.898966] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    6.060588] ata1.00: ATA-6: TOSHIBA MK6034GAX, AC101A, max UDMA/100
[    6.060597] ata1.00: 117210240 sectors, multi 16: LBA48 
[    6.068441] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    6.068555] ata1.00: configured for UDMA/100
[    6.232544] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2312, 1905, max MWDMA2
[    6.232568] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    6.232573] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    6.232584] ata2.00: simplex DMA is claimed by other device, disabling DMA
[    6.248511] ata2.00: configured for PIO4
[    6.248977] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6034GA AC10 PQ: 0 ANSI: 5
[    6.255417] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2312 1905 PQ: 0 ANSI: 5
[    6.276376] usb 1-2: configuration #1 chosen from 1 choice
[    6.280729] hub 1-2:1.0: USB hub found
[    6.282747] hub 1-2:1.0: 4 ports detected
[    6.597965] usb 1-2.2: new low speed USB device using ohci_hcd and address 3
[    6.712561] usb 1-2.2: configuration #1 chosen from 1 choice
[    7.730698] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.730915] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.794566] Driver 'sd' needs updating - please use bus_type methods
[    7.800849] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    7.800923] sd 0:0:0:0: [sda] Write Protect is off
[    7.800930] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.801022] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.801299] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    7.801358] sd 0:0:0:0: [sda] Write Protect is off
[    7.801365] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.801456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.801470]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.832133]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    7.863643] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.891167] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    7.891179] Uniform CD-ROM driver Revision: 3.20
[    7.891458] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.993497] Marking TSC unstable due to TSC halts in idle
[    8.412613] PM: Starting manual resume from disk
[    8.412625] PM: Resume from partition 8:5
[    8.412628] PM: Checking hibernation image.
[    8.413076] PM: Resume from disk failed.
[    8.495048] kjournald starting.  Commit interval 5 seconds
[    8.495097] EXT3-fs: mounted filesystem with ordered data mode.
[   15.852083] udevd version 124 started
[   17.124847] Linux agpgart interface v0.103
[   17.200518] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.261649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.339419] agpgart-ati 0000:00:00.0: Ati IGP330/340/345/350/M chipset
[   17.353781] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   17.744710] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:002a]
[   17.744742] Yenta O2: res at 0x94/0xD4: 00/ea
[   17.744746] Yenta O2: enabling read prefetch/write burst
[   17.876869] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   17.876878] Socket status: 30000411
[   18.038808] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   18.052171] ACPI: Power Button (FF) [PWRF]
[   18.052598] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   18.068154] ACPI: Power Button (CM) [PWRB]
[   18.068584] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   18.070449] ACPI: Lid Switch [LID]
[   18.105371] ACPI: AC Adapter [ACAD] (on-line)
[   18.242933] ACPI: Battery Slot [BAT1] (battery present)
[   18.250009] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   18.250027] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   18.556162] pccard: PCMCIA card inserted into slot 0
[   18.683334] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.178155] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
[   19.192195] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.469003] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[   21.505252] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   21.540685] parport_pc 00:08: reported by Plug and Play ACPI
[   21.540765] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.855337] ALI 5451 0000:00:06.0: enabling device (0005 -> 0007)
[   21.855892] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   21.855900] PCI: setting IRQ 5 as level-triggered
[   21.855908] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
[   24.536514] AC'97 1 does not respond - RESET
[   24.552206] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   24.552230] ali mixer 1 creating error.
[   25.834369] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   25.836777] cs: IO port probe 0x3e0-0x4ff: clean.
[   25.837729] cs: IO port probe 0x820-0x8ff: clean.
[   25.838680] cs: IO port probe 0xc00-0xcf7: clean.
[   25.840236] cs: IO port probe 0xa00-0xaff: clean.
[   25.841262] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   25.934758] pcmcia: registering new device pcmcia0.0
[   26.727817] ieee80211_crypt: registered algorithm 'NULL'
[   26.793129] hostap_cs: setting Vcc=33 (constant)
[   26.793153] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[   26.793158] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[   26.793162] io->flags = 0x0047, io.base=0x0000, len=128
[   26.794645] hostap_cs: Registered netdevice wifi0
[   26.834536] hostap_cs: index 0x01: , irq 3, io 0x0280-0x02ff
[   27.028417] prism2_hw_init: initialized in 196 ms
[   27.029413] wifi0: NIC: id=0x801b v1.0.0
[   27.030755] wifi0: PRI: id=0x15 v1.1.1
[   27.030940] wifi0: STA: id=0x1f v1.8.2
[   27.049830] wifi0: registered netdevice wlan0
[   27.062762] udev: renamed network interface wlan0 to wlan1
[   27.824241] lp0: using parport0 (interrupt-driven).
[   28.167767] Adding 963860k swap on /dev/sda5.  Priority:-1 extents:1 across:963860k
[   30.189431] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   30.189910] EXT3 FS on sda6, internal journal
[   31.813659] type=1505 audit(1229297389.253:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3753
[   32.176133] type=1505 audit(1229297389.617:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3758
[   32.176813] type=1505 audit(1229297389.617:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3758
[   32.481078] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.769905] ACPI: WMI: Mapper loaded
[   35.777268] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   35.895363] apm: BIOS not found.
[   36.153711] ppdev: user-space parallel port driver
[   38.741250] Bluetooth: Core ver 2.13
[   38.746660] NET: Registered protocol family 31
[   38.746679] Bluetooth: HCI device and connection manager initialized
[   38.746688] Bluetooth: HCI socket layer initialized
[   38.819840] Bluetooth: L2CAP ver 2.11
[   38.819858] Bluetooth: L2CAP socket layer initialized
[   38.875102] Bluetooth: RFCOMM socket layer initialized
[   38.878583] Bluetooth: RFCOMM TTY layer initialized
[   38.878615] Bluetooth: RFCOMM ver 1.10
[   38.883611] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.883628] Bluetooth: BNEP filters: protocol multicast
[   38.967709] Bridge firewalling registered
[   38.972144] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   39.023361] Bluetooth: SCO (Voice Link) ver 0.6
[   39.023379] Bluetooth: SCO socket layer initialized
[   41.397646] pci 0000:01:05.0: power state changed by ACPI to D0
[   41.400553] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[   41.400591] pci 0000:01:05.0: PCI INT A -> Link[LNK0] -> GSI 10 (level, low) -> IRQ 10
[   41.728900] [drm] Initialized drm 1.1.0 20060810
[   41.765336] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   42.194119] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   42.194191] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   42.194243] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   42.347826] [drm] Setting GART location based on new memory map
[   42.347866] [drm] Loading R100 Microcode
[   42.347921] [drm] writeback test succeeded in 1 usecs
[   43.221467] eth0: DSPCFG accepted after 0 usec.
[   43.257065] wifi0: LinkStatus=2 (Disconnected)
[   43.257293] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   43.406755] NET: Registered protocol family 17
[   43.416261] wifi0: LinkStatus=2 (Disconnected)
[   43.416658] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   84.809828] wifi0: LinkStatus=2 (Disconnected)
[   84.810046] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   84.829319] wifi0: LinkStatus=2 (Disconnected)
[   84.829581] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   84.842947] wlan1: Trying to join BSSID 00:14:a5:82:cb:31
[   84.868396] wifi0: LinkStatus=6 (Association failed)
[   84.869259] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   89.760056] Clocksource tsc unstable (delta = -79950717 ns)
[   95.373373] wifi0: LinkStatus=2 (Disconnected)
[   95.373624] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   95.388054] wifi0: LinkStatus=2 (Disconnected)
[   95.388352] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   95.401978] wlan1: Trying to join BSSID 00:14:a5:82:cb:31
[   95.426175] wifi0: LinkStatus=6 (Association failed)
[   95.426439] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  105.838283] wifi0: LinkStatus=2 (Disconnected)
[  105.838582] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  105.853570] wifi0: LinkStatus=2 (Disconnected)
[  105.853878] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  105.866525] wlan1: Trying to join BSSID 00:14:a5:82:cb:31
[  105.891766] wifi0: LinkStatus=6 (Association failed)
[  105.892069] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  109.393044] wifi0: LinkStatus=2 (Disconnected)
[  109.393335] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  109.825646] wifi0: LinkStatus=2 (Disconnected)
[  109.826374] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  109.843020] wifi0: LinkStatus=2 (Disconnected)
[  109.845004] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[  109.855642] wlan1: Trying to join BSSID 00:14:a5:82:cb:31
[  109.880243] wifi0: LinkStatus=1 (Connected)
[  109.881082] wifi0: LinkStatus: BSSID=00:14:a5:82:cb:31
[  110.560993] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[  118.560674] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[  134.560646] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[  149.562810] wifi0: invalid skb->cb magic (0x00000168, expected 0xf08a36a2)
[  151.920441] ppdev0: registered pardevice
[  151.968185] ppdev0: unregistered pardevice
[  153.534529] ppdev0: registered pardevice
[  153.586585] ppdev0: unregistered pardevice
[  154.101330] ppdev0: registered pardevice
[  154.152995] ppdev0: unregistered pardevice
[  155.110625] wifi0: invalid skb->cb magic (0x0000001a, expected 0xf08a36a2)
[  155.132932] wifi0: LinkStatus=2 (Disconnected)
[  155.138102] wifi0: LinkStatus: BSSID=00:14:a5:82:cb:31
jim@jim-laptop:~$ 


If anybody has the time to figure out what this data is trying to tell me, please help.  Meanwhile I will be using XP until I get home in a couple of months.

Sorry for being so impatient.

Jim

---

