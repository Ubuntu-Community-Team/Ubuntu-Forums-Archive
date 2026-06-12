---
title: "Belkin 54 USB Wireless Adaptor"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by gdn1947 on 2009-03-05
hi

Have posted this query in Absolute Beginners forum with plenty of advice (thanks guys) but not much progress.

Am trying to connect a Belkin 54 USB wireless adaptor but the system (Ubuntu 8.10) doesn't appear to recognise it.

ould appreciate some step by step guidance to find out what is, or is not, going on.

Thanks

---

### Post by nidelius on 2009-03-05
open applications -> accessories -> new terminal

type.

```
lspci
```

to see if there is any device connected

also try

```
dmesg
```

just after you connected the device to see if there is anything of value

Post the result if you find something interesting. like "device driver not found" or similar

---

### Post by gdn1947 on 2009-03-05
this is the result of lspci

george@george-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5901 100Base-TX (rev 01)
00:0c.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

and this the result of dmesg

    0.579422] PCI: 0000:00:0f.0 reg 20 io port: [8080, 808f]
[    0.579508] PCI: 0000:01:05.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.579517] PCI: 0000:01:05.0 reg 14 io port: [d000, d0ff]
[    0.579524] PCI: 0000:01:05.0 reg 18 32bit mmio: [e8100000, e810ffff]
[    0.579544] PCI: 0000:01:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.579562] pci 0000:01:05.0: supports D1
[    0.579564] pci 0000:01:05.0: supports D2
[    0.579600] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.579605] PCI: bridge 0000:00:01.0 32bit mmio: [e8100000, e81fffff]
[    0.579611] PCI: bridge 0000:00:01.0 32bit mmio pref: [f8000000, fbffffff]
[    0.579636] bus 00 -> node 0
[    0.579660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.579795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.585036] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11)
[    0.585463] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11)
[    0.585876] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11)
[    0.586197] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.586526] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.586942] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11)
[    0.587356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11)
[    0.587770] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 10 *11)
[    0.589007] ACPI: Power Resource [PUBS] (on)
[    0.589394] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.589522] pnp: PnP ACPI init
[    0.589562] ACPI: bus type pnp registered
[    0.596494] pnp: PnP ACPI: found 10 devices
[    0.596505] ACPI: ACPI bus type pnp unregistered
[    0.596515] PnPBIOS: Disabled by ACPI PNP
[    0.597904] PCI: Using ACPI for IRQ routing
[    0.598199] NET: Registered protocol family 8
[    0.598199] NET: Registered protocol family 20
[    0.598199] NetLabel: Initializing
[    0.598199] NetLabel:  domain hash size = 128
[    0.598199] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.598199] NetLabel:  unlabeled traffic allowed by default
[    0.598199] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.598199]    actual entries 65620
[    0.598199] AppArmor: AppArmor Filesystem Enabled
[    0.598199] ACPI: RTC can wake from S4
[    0.598199] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.598199] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.598199] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.598199] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.598199] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.598199] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.598199] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.598199] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.598199] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.598199] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.598199] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.598199] system 00:00: iomem range 0x100000-0x2effffff could not be reserved
[    0.598199] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.598199] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.598199] system 00:02: ioport range 0x480-0x48f has been reserved
[    0.598199] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.598199] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.598199] system 00:02: ioport range 0xfe10-0xfe11 has been reserved
[    0.598199] system 00:02: ioport range 0x370-0x371 has been reserved
[    0.598199] system 00:02: ioport range 0x8000-0x807f could not be reserved
[    0.598199] system 00:02: ioport range 0x1600-0x167f has been reserved
[    0.598199] system 00:02: iomem range 0xe8013000-0xe8013fff has been reserved
[    0.636355] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.636365] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.636372] pci 0000:00:01.0:   MEM window: 0xe8100000-0xe81fffff
[    0.636378] pci 0000:00:01.0:   PREFETCH window: 0x000000f8000000-0x000000fbffffff
[    0.636386] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
[    0.636390] pci 0000:00:0c.0:   IO window: 0x001000-0x0010ff
[    0.636395] pci 0000:00:0c.0:   IO window: 0x001400-0x0014ff
[    0.636401] pci 0000:00:0c.0:   PREFETCH window: 0x40000000-0x43ffffff
[    0.636407] pci 0000:00:0c.0:   MEM window: 0x44000000-0x47ffffff
[    0.637304] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.637314] PCI: setting IRQ 11 as level-triggered
[    0.637322] pci 0000:00:0c.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.637332] bus: 00 index 0 io port: [0, ffff]
[    0.637336] bus: 00 index 1 mmio: [0, ffffffff]
[    0.637339] bus: 01 index 0 io port: [d000, dfff]
[    0.637342] bus: 01 index 1 mmio: [e8100000, e81fffff]
[    0.637346] bus: 01 index 2 mmio: [f8000000, fbffffff]
[    0.637349] bus: 01 index 3 mmio: [0, 0]
[    0.637353] bus: 02 index 0 io port: [1000, 10ff]
[    0.637356] bus: 02 index 1 io port: [1400, 14ff]
[    0.637359] bus: 02 index 2 mmio: [40000000, 43ffffff]
[    0.637362] bus: 02 index 3 mmio: [44000000, 47ffffff]
[    0.637398] NET: Registered protocol family 2
[    0.637765] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.638477] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.641078] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.642450] TCP: Hash tables configured (established 131072 bind 65536)
[    0.642462] TCP reno registered
[    0.642860] NET: Registered protocol family 1
[    0.643155] checking if image is initramfs... it is
[    1.140136] Switched to high resolution mode on CPU 0
[    1.686885] Freeing initrd memory: 7996k freed
[    1.687460] Simple Boot Flag at 0x35 set to 0x1
[    1.688795] audit: initializing netlink socket (disabled)
[    1.688838] type=2000 audit(1236239103.688:1): initialized
[    1.695588] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.702661] VFS: Disk quotas dquot_6.5.1
[    1.702953] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.703310] msgmni has been set to 1477
[    1.703733] io scheduler noop registered
[    1.703740] io scheduler anticipatory registered
[    1.703744] io scheduler deadline registered
[    1.703798] io scheduler cfq registered (default)
[    1.703913] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    1.703939] pci 0000:01:05.0: Boot video device
[    1.705128] isapnp: Scanning for PnP cards...
[    2.059682] isapnp: No Plug & Play device found
[    2.333875] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.338216] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[    2.338231] serial 0000:00:03.0: PCI INT A -> Link[LNKG] -> GSI 11 (level, low) -> IRQ 11
[    2.338243] serial 0000:00:03.0: PCI INT A disabled
[    2.343957] brd: module loaded
[    2.344364] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.344754] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.346382] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.346395] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.348531] mice: PS/2 mouse device common for all mice
[    2.349300] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.349357] rtc0: alarms up to one month, y3k
[    2.349811] EISA: Probing bus 0 at eisa.0
[    2.349854] Cannot allocate resource for EISA slot 1
[    2.349906] Cannot allocate resource for EISA slot 8
[    2.349909] EISA: Detected 0 cards.
[    2.349916] cpuidle: using governor ladder
[    2.349920] cpuidle: using governor menu
[    2.350984] TCP cubic registered
[    2.351081] Using IPI No-Shortcut mode
[    2.352788] registered taskstats version 1
[    2.353000]   Magic number: 1:332:773
[    2.353238] tty ptyp9: hash matches
[    2.353403] rtc_cmos 00:06: setting system clock to 2009-03-05 07:45:04 UTC (1236239104)
[    2.353410] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.353413] EDD information not available.
[    2.354401] Freeing unused kernel memory: 424k freed
[    2.354491] Write protecting the kernel text: 2580k
[    2.354547] Write protecting the kernel read-only data: 940k
[    2.355890] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.820970] fuse init (API version 7.9)
[    3.108262] ACPI: IBM ThinkPad R40e detected - limiting to C1 max_cstate. Override with "processor.max_cstate=9"
[    3.108271] ACPI: processor limited to max C-state 1
[    3.132062] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.140073] processor ACPI0007:00: registered as cooling_device0
[    3.140087] ACPI: Processor [CPU] (supports 8 throttling states)
[    3.184113] thermal LNXTHERM:01: registered as thermal_zone0
[    3.187310] ACPI: Thermal Zone [THM0] (19 C)
[    4.757692] usbcore: registered new interface driver usbfs
[    4.757758] usbcore: registered new interface driver hub
[    4.757898] usbcore: registered new device driver usb
[    4.780337] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.781135] ohci_hcd 0000:00:02.0: power state changed by ACPI to D0
[    4.781899] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 11
[    4.781909] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNKI] -> GSI 11 (level, low) -> IRQ 11
[    4.781939] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.782093] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    4.782132] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe8010000
[    4.836673] usb usb1: configuration #1 chosen from 1 choice
[    4.836752] hub 1-0:1.0: USB hub found
[    4.836791] hub 1-0:1.0: 2 ports detected
[    4.904086] No dock devices found.
[    4.941005] tg3.c:v3.94 (August 14, 2008)
[    4.941854] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.941866] tg3 0000:00:0b.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.073590] SCSI subsystem initialized
[    5.141730] eth0: Tigon3 [partno(BCM95901A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100Base-TX Ethernet 00:06:1b:e3:77:5a
[    5.141740] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.141744] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    5.174135] libata version 3.00 loaded.
[    5.192524] pata_ali 0000:00:0f.0: can't derive routing for PCI INT A
[    5.192627] pata_ali 0000:00:0f.0: setting latency timer to 64
[    5.198047] scsi0 : pata_ali
[    5.198362] scsi1 : pata_ali
[    5.200274] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    5.200281] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    5.364562] ata1.00: ATA-5: HITACHI_DK23EA-30B, 00K4A0B6, max UDMA/100
[    5.364570] ata1.00: 58605120 sectors, multi 16: LBA 
[    5.372492] ata1.00: configured for UDMA/100
[    5.536392] ata2.00: ATAPI: DW-224E, B.2A, max UDMA/33
[    5.536417] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    5.536421] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    5.552389] ata2.00: configured for UDMA/33
[    5.552712] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23EA-3 00K4 PQ: 0 ANSI: 5
[    5.553992] scsi 1:0:0:0: CD-ROM            TEAC     DW-224E          B.2A PQ: 0 ANSI: 5
[    7.073953] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.074154] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.126870] Driver 'sd' needs updating - please use bus_type methods
[    7.130909] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    7.130955] sd 0:0:0:0: [sda] Write Protect is off
[    7.130961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.131027] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.131274] sd 0:0:0:0: [sda] 58605120 512-byte hardware sectors (30006 MB)
[    7.131314] sd 0:0:0:0: [sda] Write Protect is off
[    7.131319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.131382] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.131392]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.160530]  sda1 sda2 < sda5 >
[    7.187762] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.199367] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    7.199381] Uniform CD-ROM driver Revision: 3.20
[    7.199626] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.615427] PM: Starting manual resume from disk
[    7.615439] PM: Resume from partition 8:5
[    7.615442] PM: Checking hibernation image.
[    7.615775] PM: Resume from disk failed.
[    7.715506] kjournald starting.  Commit interval 5 seconds
[    7.715555] EXT3-fs: mounted filesystem with ordered data mode.
[   16.619460] udevd version 124 started
[   17.668322] Linux agpgart interface v0.103
[   17.728485] agpgart-ati 0000:00:00.0: Ati IGP330/340/345/350/M chipset
[   17.808405] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.836103] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xec000000
[   17.868580] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.529551] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   18.544136] ACPI: Power Button (FF) [PWRF]
[   18.544442] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   18.545175] ACPI: Lid Switch [LID]
[   18.545494] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   18.560105] ACPI: Sleep Button (CM) [SLPB]
[   18.692515] Yenta: CardBus bridge found at 0000:00:0c.0 [1014:0528]
[   18.692542] Yenta: Using INTVAL to route CSC interrupts to PCI
[   18.692545] Yenta: Routing CardBus interrupts to PCI
[   18.692553] Yenta TI: socket 0000:00:0c.0, mfunc 0x01d01002, devctl 0x64
[   18.928805] Yenta: ISA IRQ mask 0x04f8, PCI irq 11
[   18.928813] Socket status: 30000007
[   18.988417] ali15x3_smbus 0000:00:06.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   18.988431] ali15x3_smbus 0000:00:06.0: ALI15X3 not detected, module not inserted.
[   19.884496] parport_pc 00:09: reported by Plug and Play ACPI
[   19.884558] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   20.109054] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/device:03/input/input5
[   20.128099] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   20.480240] ACPI: AC Adapter [AC] (on-line)
[   20.585288] ACPI: Battery Slot [BAT0] (battery absent)
[   20.931763] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   21.775428] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   21.775442] ALI 5451 0000:00:04.0: PCI INT A -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[   21.810228] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.826484] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input7
[   25.733412] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   25.737567] cs: IO port probe 0x3e0-0x4ff: clean.
[   25.739192] cs: IO port probe 0x820-0x8ff: clean.
[   25.740786] cs: IO port probe 0xc00-0xcf7: clean.
[   25.742754] cs: IO port probe 0xa00-0xaff: clean.
[   26.448044] AC'97 1 does not respond - RESET
[   26.464040] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   26.464056] ali mixer 1 creating error.
[   27.608523] lp0: using parport0 (interrupt-driven).
[   27.977423] Adding 1253028k swap on /dev/sda5.  Priority:-1 extents:1 across:1253028k
[   28.593794] EXT3 FS on sda1, internal journal
[   30.207041] type=1505 audit(1236239132.845:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3761
[   30.550619] type=1505 audit(1236239133.189:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3766
[   30.551302] type=1505 audit(1236239133.189:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3766
[   30.821085] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.618997] NET: Registered protocol family 17
[   32.931134] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   32.931142] tg3: eth0: Flow control is on for TX and on for RX.
[   45.684816] NET: Registered protocol family 10
[   45.685823] lo: Disabled Privacy Extensions
[   46.782227] ACPI: WMI: Mapper loaded
[   47.560833] ACPI: Invalid _PSS data: freq is zero
[   48.808278] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   49.187784] IBM machine detected. Enabling interrupts during APM calls.
[   49.187845] apm: BIOS not found.
[   49.479741] ppdev: user-space parallel port driver
[   50.355167] Non-volatile memory driver v1.2
[   50.445352] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   50.445366] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   50.445371] thinkpad_acpi: ThinkPad BIOS 1SET70WW (1.38 ), EC unknown
[   50.456403] Registered led device: tpacpi::thinklight
[   50.457988] Registered led device: tpacpi::power
[   50.459259] Registered led device: tpacpi:orange:batt
[   50.460662] Registered led device: tpacpi:green:batt
[   50.461937] Registered led device: tpacpi::dock_active
[   50.463285] Registered led device: tpacpi::bay_active
[   50.464680] Registered led device: tpacpi::dock_batt
[   50.465995] Registered led device: tpacpi::unknown_led
[   50.467359] Registered led device: tpacpi::standby
[   50.470461] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   53.136995] Bluetooth: Core ver 2.13
[   53.141410] NET: Registered protocol family 31
[   53.141423] Bluetooth: HCI device and connection manager initialized
[   53.141432] Bluetooth: HCI socket layer initialized
[   53.173169] Bluetooth: L2CAP ver 2.11
[   53.173182] Bluetooth: L2CAP socket layer initialized
[   53.203356] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   53.203369] Bluetooth: BNEP filters: protocol multicast
[   53.244735] Bluetooth: RFCOMM socket layer initialized
[   53.245342] Bluetooth: RFCOMM TTY layer initialized
[   53.245360] Bluetooth: RFCOMM ver 1.10
[   53.289702] Bridge firewalling registered
[   53.323901] Bluetooth: SCO (Voice Link) ver 0.6
[   53.323917] Bluetooth: SCO socket layer initialized
[   55.773876] pci 0000:01:05.0: power state changed by ACPI to D0
[   55.776402] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   55.776428] pci 0000:01:05.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   56.088449] [drm] Initialized drm 1.1.0 20060810
[   56.107409] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   56.110056] mtrr: no more MTRRs available
[   56.222291] mtrr: no more MTRRs available
[   56.384092] eth0: no IPv6 routers present
[   56.551286] mtrr: no more MTRRs available
[   56.553051] mtrr: no more MTRRs available
[   56.554570] mtrr: no more MTRRs available
[   56.556726] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   56.556779] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   56.556832] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   56.711512] [drm] Setting GART location based on new memory map
[   56.711541] [drm] Loading R100 Microcode
[   56.711596] [drm] writeback test succeeded in 1 usecs
[   97.480111] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   97.955457] usb 1-1: configuration #1 chosen from 1 choice
[   98.809365] phy0: Selected rate control algorithm 'pid'
[   98.986233] Registered led device: rt73usb-phy0:radio
[   98.987760] Registered led device: rt73usb-phy0:assoc
[   98.988412] Registered led device: rt73usb-phy0:quality
[   98.997716] usbcore: registered new interface driver rt73usb
[   99.101635] usbcore: registered new interface driver rt2500usb
[  103.325205] firmware: requesting rt73.bin
[  104.548321] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  168.846715] ppdev0: registered pardevice
[  168.897439] ppdev0: unregistered pardevice
[  171.036983] ppdev0: registered pardevice
[  171.080640] ppdev0: unregistered pardevice
[  172.224596] ppdev0: registered pardevice
[  172.272231] ppdev0: unregistered pardevice
[ 1995.328082] usb 1-1: USB disconnect, address 2
[ 1995.338120] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[ 1995.339670] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[ 1995.341730] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[ 1995.344287] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[ 1995.344306] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[ 1995.348963] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 1995.351383] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 1995.354106] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 1995.356600] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 2320.772063] usb 1-1: new full speed USB device using ohci_hcd and address 3
[ 2321.221844] usb 1-1: configuration #1 chosen from 1 choice
[ 2321.543265] phy1: Selected rate control algorithm 'pid'
[ 2321.547517] Registered led device: rt73usb-phy1:radio
[ 2321.549192] Registered led device: rt73usb-phy1:assoc
[ 2321.550586] Registered led device: rt73usb-phy1:quality
[ 2325.681136] firmware: requesting rt73.bin
[ 2326.821182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2911.072729] ppdev0: registered pardevice
[ 2911.120945] ppdev0: unregistered pardevice
[ 2911.762687] ppdev0: registered pardevice
[ 2911.812563] ppdev0: unregistered pardevice
[ 2912.879505] ppdev0: registered pardevice
[ 2912.928164] ppdev0: unregistered pardevice
[ 8327.510216] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 8327.510242] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 8327.510247] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 9087.626335] usb 1-1: USB disconnect, address 3
[ 9087.635647] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[ 9087.638204] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[ 9087.640563] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[ 9087.642818] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[ 9087.642834] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[ 9087.647387] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9087.650062] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9087.652642] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9087.652725] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9088.312117] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 9088.765207] usb 1-1: configuration #1 chosen from 1 choice
[ 9089.084555] phy2: Selected rate control algorithm 'pid'
[ 9089.088764] Registered led device: rt73usb-phy2:radio
[ 9089.090290] Registered led device: rt73usb-phy2:assoc
[ 9089.091809] Registered led device: rt73usb-phy2:quality
[ 9093.229318] firmware: requesting rt73.bin
[ 9094.371573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9151.550278] usb 1-1: USB disconnect, address 4
[ 9151.559454] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[ 9151.561966] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[ 9151.564301] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[ 9151.566522] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[ 9151.566538] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[ 9151.571145] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9151.573808] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9151.576326] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9151.576390] phy2 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 9156.532119] usb 1-1: new full speed USB device using ohci_hcd and address 5
[ 9156.979314] usb 1-1: configuration #1 chosen from 1 choice
[ 9157.299404] phy3: Selected rate control algorithm 'pid'
[ 9157.303526] Registered led device: rt73usb-phy3:radio
[ 9157.305158] Registered led device: rt73usb-phy3:assoc
[ 9157.306579] Registered led device: rt73usb-phy3:quality
[ 9161.453193] firmware: requesting rt73.bin
[ 9162.598259] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15400.723646] usb 1-1: USB disconnect, address 5
[15400.733311] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[15400.735725] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[15400.738092] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[15400.740481] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[15400.740498] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[15400.745109] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[15400.747580] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[15400.750179] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[15400.750245] phy3 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[23159.600071] usb 1-1: new full speed USB device using ohci_hcd and address 6
[23160.049351] usb 1-1: configuration #1 chosen from 1 choice
[23160.377301] phy4: Selected rate control algorithm 'pid'
[23160.381503] Registered led device: rt73usb-phy4:radio
[23160.383024] Registered led device: rt73usb-phy4:assoc
[23160.384553] Registered led device: rt73usb-phy4:quality
[23164.521180] firmware: requesting rt73.bin
[23165.665253] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23720.624198] usb 1-1: USB disconnect, address 6
[23720.633870] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[23720.636380] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[23720.638599] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[23720.640824] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[23720.640842] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[23720.645366] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[23720.647901] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[23720.650432] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[23720.650505] phy4 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[27256.672086] usb 1-1: new full speed USB device using ohci_hcd and address 7
[27257.122771] usb 1-1: configuration #1 chosen from 1 choice
[27257.443785] phy5: Selected rate control algorithm 'pid'
[27257.447983] Registered led device: rt73usb-phy5:radio
[27257.449601] Registered led device: rt73usb-phy5:assoc
[27257.450974] Registered led device: rt73usb-phy5:quality
[27261.589501] firmware: requesting rt73.bin
[27262.743194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
george@george-laptop:~$

---

### Post by nidelius on 2009-03-05
Seems to be a problem withe the drivers for your card

If it's a card with the modell WUSB54GC someone used ndiswrapper and the windows drivers and got it working. That's usually working fine:

[http://ubuntuforums.org/showthread.php?t=694470](http://ubuntuforums.org/showthread.php?t=694470)

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by FreewheelinFrank on 2009-03-05
This adapter works with Ubuntu but gdn1947 seems to have made some changes that disabled it.

This was the result of iwconfig:

```
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=8 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

These were the changes the user remembered making:

```
auto eth0
iface eth0 inet dhcp
```

This Belkin adapter works for me and others "out of the box".

[http://ubuntuforums.org/showthread.php?t=1087501](http://ubuntuforums.org/showthread.php?t=1087501)

---

### Post by FreewheelinFrank on 2009-03-05
> **nidelius said:**
> Seems to be a problem withe the drivers for your card

If it's a card with the modell WUSB54GC someone used ndiswrapper and the windows drivers and got it working. That's usually working fine:

[http://ubuntuforums.org/showthread.php?t=694470](http://ubuntuforums.org/showthread.php?t=694470)

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

The first link applies to 8.04 only in which the Belkin adapter sometimes caused problems- kernel panic. That was fixed in 8.10.

The second link is way out of date- the adapter is supported now.

---

### Post by FreewheelinFrank on 2009-03-05
Try editing /etc/network/interfaces and adding "auto wlan0" (without quotes) if not present.

```
gksudo gedit
```

will do it.

You may need to disable your previous changes by pre-pending a hash before adding the new line:

```
#auto eth0
#iface eth0 inet dhcp

auto wlan0
```

Give that a whirl and reboot.

---

