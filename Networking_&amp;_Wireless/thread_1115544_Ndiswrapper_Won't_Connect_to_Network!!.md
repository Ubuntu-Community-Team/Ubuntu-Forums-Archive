---
title: "Ndiswrapper Won't Connect to Network!!"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by iswear on 2009-04-03
I click on the Network Manager and i can choose what network i want to connect to but when i click on it it never connects. Some please help!

---

### Post by 73ckn797 on 2009-04-03
Is the network unsecured or does it require a password?

Need system specifications of hardware and network card.

---

### Post by iswear on 2009-04-04
Theres no key and i have a bcm4360 802.11 (rev03)

When i type iwconfig in the teminal i get this:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=88/100  Signal level:-42 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

And when i type dmesg i get this:

[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003dee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003dee0
[    0.000000] On node 0 totalpages: 253567
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 24074 pages, LIFO batch:3
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (018bc000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251337
[    0.000000] Kernel command line: root=UUID=0a99804e-37a2-4c9b-81d7-09b604e6af3e ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1296.746 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 991236k/1014656k available (2576k kernel code, 22724k reserved, 1165k data, 424k init, 97152k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.49 BogoMIPS (lpj=5186984)
[    0.004046] Security Framework initialized
[    0.004059] SELinux:  Disabled at boot.
[    0.004090] AppArmor: AppArmor initialized
[    0.004103] Mount-cache hash table entries: 512
[    0.004364] Initializing cgroup subsys ns
[    0.004373] Initializing cgroup subsys cpuacct
[    0.004378] Initializing cgroup subsys memory
[    0.004403] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004407] CPU: L2 cache: 1024K
[    0.004430] Checking 'hlt' instruction... OK.
[    0.020694] SMP alternatives: switching to UP code
[    0.028017] Freeing SMP alternatives: 11k freed
[    0.028022] ACPI: Core revision 20080609
[    0.031091] ACPI: Checking initramfs for custom DSDT
[    0.550100] ACPI: setting ELCR to 0200 (from 0c20)
[    0.552099] weird, boot CPU (#0) not listedby the BIOS.
[    0.552103] SMP motherboard not detected.
[    0.552107] Local APIC not detected. Using dummy APIC emulation.
[    0.552111] SMP disabled
[    0.552203] Brought up 1 CPUs
[    0.552207] Total of 1 processors activated (2593.49 BogoMIPS).
[    0.552224] CPU0 attaching NULL sched-domain.
[    0.552527] net_namespace: 840 bytes
[    0.552546] Booting paravirtualized kernel on bare hardware
[    0.552818] Time: 19:16:02  Date: 04/04/09
[    0.552857] NET: Registered protocol family 16
[    0.553275] EISA bus registered
[    0.553297] ACPI: bus type pci registered
[    0.556764] PCI: PCI BIOS revision 2.10 entry at 0xfd9a2, last bus=2
[    0.556768] PCI: Using configuration type 1 for base access
[    0.559047] ACPI: EC: Look up EC in DSDT
[    0.562679] ACPI: Interpreter enabled
[    0.562687] ACPI: (supports S0 S3 S4 S5)
[    0.562709] ACPI: Using PIC for interrupt routing
[    0.563150] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.581314] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.581319] ACPI: EC: driver started in interrupt mode
[    0.581391] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.581578] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8000000, efffffff]
[    0.581585] PCI: 0000:00:02.0 reg 14 32bit mmio: [e0000000, e007ffff]
[    0.581592] PCI: 0000:00:02.0 reg 18 io port: [1800, 1807]
[    0.581613] pci 0000:00:02.0: supports D1
[    0.581630] PCI: 0000:00:02.1 reg 10 32bit mmio: [f0000000, f7ffffff]
[    0.581637] PCI: 0000:00:02.1 reg 14 32bit mmio: [e0080000, e00fffff]
[    0.581660] pci 0000:00:02.1: supports D1
[    0.581730] PCI: 0000:00:1d.0 reg 20 io port: [1820, 183f]
[    0.581780] PCI: 0000:00:1d.1 reg 20 io port: [1840, 185f]
[    0.581829] PCI: 0000:00:1d.2 reg 20 io port: [1860, 187f]
[    0.581885] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e0100000, e01003ff]
[    0.581936] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.581943] pci 0000:00:1d.7: PME# disabled
[    0.582014] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.582023] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.582028] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.582048] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.582055] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.582063] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.582071] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.582078] PCI: 0000:00:1f.1 reg 20 io port: [1810, 181f]
[    0.582086] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.582133] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.582174] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.582181] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.582189] PCI: 0000:00:1f.5 reg 18 32bit mmio: [e0100c00, e0100dff]
[    0.582197] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [e0100800, e01008ff]
[    0.582223] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.582228] pci 0000:00:1f.5: PME# disabled
[    0.582253] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.582260] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.582294] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.582299] pci 0000:00:1f.6: PME# disabled
[    0.582333] PCI: 0000:02:00.0 reg 10 io port: [3000, 30ff]
[    0.582340] PCI: 0000:02:00.0 reg 14 32bit mmio: [e0202000, e02020ff]
[    0.582375] pci 0000:02:00.0: supports D1
[    0.582378] pci 0000:02:00.0: supports D2
[    0.582381] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.582386] pci 0000:02:00.0: PME# disabled
[    0.582418] PCI: 0000:02:05.0 reg 10 32bit mmio: [0, fff]
[    0.582433] pci 0000:02:05.0: supports D1
[    0.582435] pci 0000:02:05.0: supports D2
[    0.582438] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.582444] pci 0000:02:05.0: PME# disabled
[    0.582460] PCI: 0000:02:06.0 reg 10 32bit mmio: [e0200000, e0201fff]
[    0.582518] pci 0000:00:1e.0: transparent bridge
[    0.582524] PCI: bridge 0000:00:1e.0 io port: [3000, 3fff]
[    0.582531] PCI: bridge 0000:00:1e.0 32bit mmio: [e0200000, e02fffff]
[    0.582557] bus 00 -> node 0
[    0.582567] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.583009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.589252] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.589462] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.589668] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[    0.589875] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.590081] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.590288] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[    0.590494] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[    0.590700] ACPI: PCI Interrupt Link [LNKH] (IRQs *11)
[    0.590933] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.590988] pnp: PnP ACPI init
[    0.590999] ACPI: bus type pnp registered
[    0.594984] pnp: PnP ACPI: found 7 devices
[    0.594987] ACPI: ACPI bus type pnp unregistered
[    0.594993] PnPBIOS: Disabled by ACPI PNP
[    0.595488] PCI: Using ACPI for IRQ routing
[    0.595633] NET: Registered protocol family 8
[    0.595633] NET: Registered protocol family 20
[    0.595633] NetLabel: Initializing
[    0.595633] NetLabel:  domain hash size = 128
[    0.595633] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.595633] NetLabel:  unlabeled traffic allowed by default
[    0.596261] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.596266]    actual entries 65620
[    0.596408] AppArmor: AppArmor Filesystem Enabled
[    0.596428] ACPI: RTC can wake from S4
[    0.596491] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.596496] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.596501] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.596505] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.596510] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.631808] pci 0000:02:05.0: CardBus bridge, secondary bus 0000:03
[    0.631812] pci 0000:02:05.0:   IO window: 0x003400-0x0034ff
[    0.631818] pci 0000:02:05.0:   IO window: 0x003800-0x0038ff
[    0.631824] pci 0000:02:05.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.631830] pci 0000:02:05.0:   MEM window: 0x58000000-0x5bffffff
[    0.631835] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.631840] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.631847] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    0.631853] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.631872] pci 0000:00:1e.0: setting latency timer to 64
[    0.632201] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    0.632205] PCI: setting IRQ 11 as level-triggered
[    0.632212] pci 0000:02:05.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    0.632219] bus: 00 index 0 io port: [0, ffff]
[    0.632223] bus: 00 index 1 mmio: [0, ffffffff]
[    0.632226] bus: 02 index 0 io port: [3000, 3fff]
[    0.632230] bus: 02 index 1 mmio: [e0200000, e02fffff]
[    0.632233] bus: 02 index 2 mmio: [50000000, 53ffffff]
[    0.632236] bus: 02 index 3 io port: [0, ffff]
[    0.632239] bus: 02 index 4 mmio: [0, ffffffff]
[    0.632243] bus: 03 index 0 io port: [3400, 34ff]
[    0.632246] bus: 03 index 1 io port: [3800, 38ff]
[    0.632249] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    0.632252] bus: 03 index 3 mmio: [58000000, 5bffffff]
[    0.632268] NET: Registered protocol family 2
[    0.632450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.632808] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.634332] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.635427] TCP: Hash tables configured (established 131072 bind 65536)
[    0.635433] TCP reno registered
[    0.635685] NET: Registered protocol family 1
[    0.635902] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.146544]  it is
[    1.700255] Freeing initrd memory: 8016k freed
[    1.700804] Simple Boot Flag at 0x36 set to 0x1
[    1.701357] audit: initializing netlink socket (disabled)
[    1.701385] type=2000 audit(1238872562.700:1): initialized
[    1.710862] highmem bounce pool size: 64 pages
[    1.710873] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.714179] VFS: Disk quotas dquot_6.5.1
[    1.714306] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.714464] msgmni has been set to 1762
[    1.714651] io scheduler noop registered
[    1.714655] io scheduler anticipatory registered
[    1.714659] io scheduler deadline registered
[    1.714678] io scheduler cfq registered (default)
[    1.714702] pci 0000:00:02.0: Boot video device
[    1.715238] isapnp: Scanning for PnP cards...
[    2.069028] isapnp: No Plug & Play device found
[    2.119727] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.121264] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    2.121270] PCI: setting IRQ 5 as level-triggered
[    2.121277] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    2.121287] serial 0000:00:1f.6: PCI INT B disabled
[    2.123429] brd: module loaded
[    2.123532] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.123707] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 irq 1,12
[    2.126282] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.126289] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.126743] mice: PS/2 mouse device common for all mice
[    2.126937] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.126956] rtc0: alarms up to one month, y3k
[    2.127119] EISA: Probing bus 0 at eisa.0
[    2.127128] Cannot allocate resource for EISA slot 1
[    2.127132] Cannot allocate resource for EISA slot 2
[    2.127136] Cannot allocate resource for EISA slot 3
[    2.127159] EISA: Detected 0 cards.
[    2.127164] cpuidle: using governor ladder
[    2.127167] cpuidle: using governor menu
[    2.127912] TCP cubic registered
[    2.127956] Using IPI No-Shortcut mode
[    2.128285] registered taskstats version 1
[    2.128436]   Magic number: 5:23:293
[    2.128472] tty ttyz7: hash matches
[    2.128490] tty ttywa: hash matches
[    2.128628] tty tty26: hash matches
[    2.128695] rtc_cmos 00:01: setting system clock to 2009-04-04 19:16:04 UTC (1238872564)
[    2.128700] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.128703] EDD information not available.
[    2.129006] Freeing unused kernel memory: 424k freed
[    2.129076] Write protecting the kernel text: 2580k
[    2.129118] Write protecting the kernel read-only data: 940k
[    2.156690] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.440067] fuse init (API version 7.9)
[    2.740025] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.741700] processor ACPI0007:00: registered as cooling_device0
[    2.746094] Marking TSC unstable due to TSC halts in idle
[    2.746913] thermal LNXTHERM:01: registered as thermal_zone0
[    2.748210] ACPI: Thermal Zone [THRM] (76 C)
[    3.610891] usbcore: registered new interface driver usbfs
[    3.610935] usbcore: registered new interface driver hub
[    3.628294] No dock devices found.
[    3.652297] usbcore: registered new device driver usb
[    3.717546] SCSI subsystem initialized
[    3.721742] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.721779] 8139cp 0000:02:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.721785] 8139cp 0000:02:00.0: Try the "8139too" driver instead.
[    3.727577] 8139too Fast Ethernet driver 0.9.28
[    3.732479] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    3.732484] PCI: setting IRQ 10 as level-triggered
[    3.732491] 8139too 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.733977] eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:75:09:23, IRQ 10
[    3.733981] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.734384] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.734389] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.734404] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.734409] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.734477] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.738392] ehci_hcd 0000:00:1d.7: debug port 1
[    3.738400] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.738413] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    3.745721] USB Universal Host Controller Interface driver v3.0
[    3.756125] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.756407] usb usb1: configuration #1 chosen from 1 choice
[    3.756452] hub 1-0:1.0: USB hub found
[    3.756469] hub 1-0:1.0: 6 ports detected
[    3.848085] libata version 3.00 loaded.
[    3.860467] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.860482] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.860488] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.860524] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.860554] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[    3.860696] usb usb2: configuration #1 chosen from 1 choice
[    3.860737] hub 2-0:1.0: USB hub found
[    3.860747] hub 2-0:1.0: 2 ports detected
[    3.965083] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.965092] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.965106] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.965111] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.965161] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.965190] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    3.965361] usb usb3: configuration #1 chosen from 1 choice
[    3.965401] hub 3-0:1.0: USB hub found
[    3.965412] hub 3-0:1.0: 2 ports detected
[    4.068767] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.068776] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.068789] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.068794] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.068836] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.068865] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    4.069014] usb usb4: configuration #1 chosen from 1 choice
[    4.069056] hub 4-0:1.0: USB hub found
[    4.069066] hub 4-0:1.0: 2 ports detected
[    4.172493] b43-pci-bridge 0000:02:06.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.176729] ssb: Sonics Silicon Backplane found on PCI device 0000:02:06.0
[    4.177114] ata_piix 0000:00:1f.1: version 2.12
[    4.177125] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    4.177133] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.177182] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.178382] scsi0 : ata_piix
[    4.178541] scsi1 : ata_piix
[    4.180188] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    4.180193] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    4.395484] ata1.00: ATA-8: WDC WD1200BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.395491] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.409117] ata1.00: configured for UDMA/100
[    4.572316] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4243N, 1.07, max MWDMA2
[    4.588264] ata2.00: configured for MWDMA2
[    4.588435] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.592539] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N 1.07 PQ: 0 ANSI: 5
[    4.619976] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.620091] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.651336] Driver 'sd' needs updating - please use bus_type methods
[    4.651502] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.651526] sd 0:0:0:0: [sda] Write Protect is off
[    4.651530] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.651565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.651664] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.651685] sd 0:0:0:0: [sda] Write Protect is off
[    4.651689] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.651723] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.651730]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    4.670234]  sda5 sda6 sda7 sda8 sda9 >
[    4.752946] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.769892] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.769901] Uniform CD-ROM driver Revision: 3.20
[    4.770053] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.415275] PM: Starting manual resume from disk
[    5.415282] PM: Resume from partition 8:9
[    5.415284] PM: Checking hibernation image.
[    5.415556] PM: Resume from disk failed.
[    5.482977] kjournald starting.  Commit interval 5 seconds
[    5.483000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.208300] udevd version 124 started
[   12.361072] Linux agpgart interface v0.103
[   12.424264] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   12.424574] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[   12.500030] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   12.652066] intel_rng: FWH not detected
[   12.740239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.808962] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.888224] iTCO_vendor_support: vendor-support=0
[   12.952213] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.960191] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   12.960426] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.476279] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   13.517519] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.540055] ACPI: Power Button (FF) [PWRF]
[   13.540227] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   13.540328] ACPI: Lid Switch [LID0]
[   13.540426] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   13.552061] ACPI: Power Button (CM) [PWRB]
[   13.675943] ACPI: AC Adapter [ACAD] (on-line)
[   13.796912] ACPI: Battery Slot [BAT0] (battery present)
[   13.797534] ACPI: WMI: Mapper loaded
[   14.292283] Yenta: CardBus bridge found at 0000:02:05.0 [103c:3084]
[   14.292307] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.292310] Yenta: Routing CardBus interrupts to PCI
[   14.292316] Yenta TI: socket 0000:02:05.0, mfunc 0x01111112, devctl 0x64
[   14.524627] Yenta: ISA IRQ mask 0x00d8, PCI irq 11
[   14.524633] Socket status: 30000006
[   14.524638] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   14.524647] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   14.524652] cs: IO port probe 0x3000-0x3fff: clean.
[   14.524982] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   14.524987] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   15.192833] acpi device:05: registered as cooling_device1
[   15.193054] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/input/input6
[   15.204390] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   15.350100] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   15.382157] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.522637] b43-phy0: Broadcom 4306 WLAN found
[   16.600907] phy0: Selected rate control algorithm 'pid'
[   16.628548] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.628581] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   16.948064] intel8x0_measure_ac97_clock: measured 53950 usecs
[   16.948069] intel8x0: clocking to 48000
[   17.027262] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   19.132348] cs: IO port probe 0x100-0x3af: clean.
[   19.134074] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.134792] cs: IO port probe 0x820-0x8ff: clean.
[   19.135388] cs: IO port probe 0xc00-0xcf7: clean.
[   19.136212] cs: IO port probe 0xa00-0xaff: clean.
[   20.269097] lp: driver loaded but no devices found
[   20.613297] Adding 2425772k swap on /dev/sda9.  Priority:-1 extents:1 across:2425772k
[   21.209549] EXT3 FS on sda8, internal journal
[   22.290882] type=1505 audit(1238872584.213:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3884
[   22.594346] type=1505 audit(1238872584.517:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3889
[   22.594778] type=1505 audit(1238872584.517:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3889
[   22.779229] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.563655] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   24.613951] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   24.613959] apm: overridden by ACPI.
[   24.771839] ppdev: user-space parallel port driver
[   26.561676] Bluetooth: Core ver 2.13
[   26.564818] NET: Registered protocol family 31
[   26.564825] Bluetooth: HCI device and connection manager initialized
[   26.564830] Bluetooth: HCI socket layer initialized
[   26.588137] Bluetooth: L2CAP ver 2.11
[   26.588144] Bluetooth: L2CAP socket layer initialized
[   26.602772] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.602779] Bluetooth: BNEP filters: protocol multicast
[   26.636082] Bridge firewalling registered
[   26.676897] Bluetooth: SCO (Voice Link) ver 0.6
[   26.676905] Bluetooth: SCO socket layer initialized
[   26.700433] Bluetooth: RFCOMM socket layer initialized
[   26.700769] Bluetooth: RFCOMM TTY layer initialized
[   26.700775] Bluetooth: RFCOMM ver 1.10
[   30.377544] [drm] Initialized drm 1.1.0 20060810
[   30.397230] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   30.397241] pci 0000:00:02.0: setting latency timer to 64
[   30.398717] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.398734] pci 0000:00:02.1: setting latency timer to 64
[   30.402052] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   30.860405] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.882241] input: b43-phy0 as /devices/virtual/input/input8
[   30.944054] firmware: requesting b43/ucode5.fw
[   31.002362] firmware: requesting b43/pcm5.fw
[   31.008175] firmware: requesting b43/b0g0initvals5.fw
[   31.013885] firmware: requesting b43/b0g0bsinitvals5.fw
[   31.132061] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.287150] Registered led device: b43-phy0::tx
[   31.287490] Registered led device: b43-phy0::rx
[   31.287703] Registered led device: b43-phy0::radio
[   31.485595] NET: Registered protocol family 17
[   36.109452] NET: Registered protocol family 10
[   36.112204] lo: Disabled Privacy Extensions
[   36.114462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.952036] eth0: no IPv6 routers present
[   65.508915] eth0: link down
[  217.421644] wlan0: authenticate with AP 00:23:51:28:2c:f9
[  217.423447] wlan0: authenticated
[  217.423455] wlan0: associate with AP 00:23:51:28:2c:f9
[  217.431356] wlan0: RX AssocResp from 00:23:51:28:2c:f9 (capab=0x431 status=0 aid=2)
[  217.431363] wlan0: associated
[  217.437653] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  227.988031] wlan0: no IPv6 routers present
[  298.519994] wlan0: disassociating by local choice (reason=3)
[  305.487701] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

If any one can help i would appreciate it.

---

