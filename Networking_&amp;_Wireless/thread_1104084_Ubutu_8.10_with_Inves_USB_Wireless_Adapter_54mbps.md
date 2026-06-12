---
title: "Ubutu 8.10 with Inves USB Wireless Adapter 54mbps"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by spnoe on 2009-03-23
I have been trying to get the Inves USB adapter to work without any success. The manufactures say that it should work out of the box with Ubuntu, but they did not offer any further advice. I down loaded new firmware zd1211 and despite help from another forum have had no success in installing this. The command line and information gathered mean nothing to me. I am a complete novice and so every step needs to be explained in detail.
I only bought this adapter because it said it was Linux compliant.
I am using an old Packard Bell iPower 5000.

Through the Sticky I have gathered the information that I understand you would need to start to work out what is and is not working. Couls some one with the knowledge please help me.

Thanks, Steve
[    0.427915] PCI: 0000:00:02.7 reg 14 io port: [e300, e37f]
[    0.427962] pci 0000:00:02.7: supports D1
[    0.427964] pci 0000:00:02.7: supports D2
[    0.427967] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.427972] pci 0000:00:02.7: PME# disabled
[    0.428006] PCI: 0000:00:03.0 reg 10 32bit mmio: [d8000, d8fff]
[    0.428084] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.428090] pci 0000:00:03.0: PME# disabled
[    0.428124] PCI: 0000:00:03.1 reg 10 32bit mmio: [da000, dafff]
[    0.428176] pci 0000:00:03.1: PME# supported from D0 D3hot D3cold
[    0.428181] pci 0000:00:03.1: PME# disabled
[    0.428215] PCI: 0000:00:03.2 reg 10 32bit mmio: [0, fff]
[    0.428266] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.428271] pci 0000:00:03.2: PME# disabled
[    0.428305] PCI: 0000:00:03.3 reg 10 32bit mmio: [f4001000, f4001fff]
[    0.428356] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.428362] pci 0000:00:03.3: PME# disabled
[    0.428403] PCI: 0000:00:04.0 reg 10 io port: [e400, e4ff]
[    0.428412] PCI: 0000:00:04.0 reg 14 32bit mmio: [f4002000, f4002fff]
[    0.428444] PCI: 0000:00:04.0 reg 30 32bit mmio: [0, 1ffff]
[    0.428462] pci 0000:00:04.0: supports D1
[    0.428464] pci 0000:00:04.0: supports D2
[    0.428466] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.428472] pci 0000:00:04.0: PME# disabled
[    0.428514] PCI: 0000:00:09.0 reg 10 32bit mmio: [0, fff]
[    0.428532] pci 0000:00:09.0: supports D1
[    0.428534] pci 0000:00:09.0: supports D2
[    0.428536] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.428542] pci 0000:00:09.0: PME# disabled
[    0.428617] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, e0ffffff]
[    0.428625] PCI: 0000:01:00.0 reg 14 32bit mmio: [90000000, 93ffffff]
[    0.428633] PCI: 0000:01:00.0 reg 18 32bit mmio: [94000000, 9407ffff]
[    0.428653] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.428709] PCI: bridge 0000:00:01.0 io port: [c000, dfff]
[    0.428714] PCI: bridge 0000:00:01.0 32bit mmio: [e0000000, efffffff]
[    0.428720] PCI: bridge 0000:00:01.0 32bit mmio pref: [90000000, 9fffffff]
[    0.428751] bus 00 -> node 0
[    0.428763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.428925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.VPCI._PRT]
[    0.443423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11)
[    0.443639] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.443849] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 10 11)
[    0.444084] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11)
[    0.444297] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 10)
[    0.444509] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 10)
[    0.444719] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 10)
[    0.444932] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10) *11
[    0.445204] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.445260] pnp: PnP ACPI init
[    0.445274] ACPI: bus type pnp registered
[    0.448985] pnp: PnP ACPI: found 11 devices
[    0.448989] ACPI: ACPI bus type pnp unregistered
[    0.448995] PnPBIOS: Disabled by ACPI PNP
[    0.449588] PCI: Using ACPI for IRQ routing
[    0.449765] NET: Registered protocol family 8
[    0.449765] NET: Registered protocol family 20
[    0.449765] NetLabel: Initializing
[    0.449765] NetLabel:  domain hash size = 128
[    0.449765] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.449765] NetLabel:  unlabeled traffic allowed by default
[    0.449765] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.449765]    actual entries 65620
[    0.449765] AppArmor: AppArmor Filesystem Enabled
[    0.449765] system 00:03: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.449765] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.449765] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.449765] system 00:05: ioport range 0x680-0x6ff has been reserved
[    0.449765] system 00:05: ioport range 0x77c-0x77f has been reserved
[    0.449765] system 00:05: ioport range 0x200-0x20f has been reserved
[    0.449765] system 00:05: ioport range 0x1000-0x10fe has been reserved
[    0.486071] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.486076] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.486084] pci 0000:00:01.0:   MEM window: 0xe0000000-0xefffffff
[    0.486090] pci 0000:00:01.0:   PREFETCH window: 0x00000090000000-0x0000009fffffff
[    0.486099] pci 0000:00:09.0: CardBus bridge, secondary bus 0000:02
[    0.486102] pci 0000:00:09.0:   IO window: 0x001400-0x0014ff
[    0.486108] pci 0000:00:09.0:   IO window: 0x001800-0x0018ff
[    0.486114] pci 0000:00:09.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.486119] pci 0000:00:09.0:   MEM window: 0x24000000-0x27ffffff
[    0.486520] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.486525] PCI: setting IRQ 10 as level-triggered
[    0.486531] pci 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.486539] bus: 00 index 0 io port: [0, ffff]
[    0.486542] bus: 00 index 1 mmio: [0, ffffffff]
[    0.486545] bus: 01 index 0 io port: [c000, dfff]
[    0.486547] bus: 01 index 1 mmio: [e0000000, efffffff]
[    0.486550] bus: 01 index 2 mmio: [90000000, 9fffffff]
[    0.486552] bus: 01 index 3 mmio: [0, 0]
[    0.486555] bus: 02 index 0 io port: [1400, 14ff]
[    0.486557] bus: 02 index 1 io port: [1800, 18ff]
[    0.486559] bus: 02 index 2 mmio: [20000000, 23ffffff]
[    0.486562] bus: 02 index 3 mmio: [24000000, 27ffffff]
[    0.486581] NET: Registered protocol family 2
[    0.486802] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.487125] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.487248] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.487366] TCP: Hash tables configured (established 16384 bind 16384)
[    0.487371] TCP reno registered
[    0.487501] NET: Registered protocol family 1
[    0.487680] checking if image is initramfs... it is
[    0.988091] Switched to high resolution mode on CPU 0
[    1.272962] Freeing initrd memory: 8013k freed
[    1.273279] Simple Boot Flag at 0x37 set to 0x1
[    1.273881] audit: initializing netlink socket (disabled)
[    1.273911] type=2000 audit(1237817785.272:1): initialized
[    1.279187] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.282274] VFS: Disk quotas dquot_6.5.1
[    1.282405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.282567] msgmni has been set to 749
[    1.282760] io scheduler noop registered
[    1.282764] io scheduler anticipatory registered
[    1.282767] io scheduler deadline registered
[    1.282787] io scheduler cfq registered (default)
[    1.282876] pci 0000:01:00.0: Boot video device
[    1.283377] isapnp: Scanning for PnP cards...
[    1.637284] isapnp: No Plug & Play device found
[    1.705768] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.706101] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    1.707229] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    1.707235] PCI: setting IRQ 5 as level-triggered
[    1.707240] serial 0000:00:02.6: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    1.707250] serial 0000:00:02.6: PCI INT C disabled
[    1.709828] brd: module loaded
[    1.709943] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.710138] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.715897] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.718908] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.718916] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.718920] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.718924] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.718927] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.719746] mice: PS/2 mouse device common for all mice
[    1.719977] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.720004] rtc0: alarms up to one year
[    1.720245] EISA: Probing bus 0 at eisa.0
[    1.720255] Cannot allocate resource for EISA slot 1
[    1.720284] EISA: Detected 0 cards.
[    1.720290] cpuidle: using governor ladder
[    1.720293] cpuidle: using governor menu
[    1.721013] TCP cubic registered
[    1.721060] Using IPI No-Shortcut mode
[    1.721521] registered taskstats version 1
[    1.721672]   Magic number: 1:912:283
[    1.721728] tty ttyve: hash matches
[    1.721915] rtc_cmos 00:01: setting system clock to 2009-03-23 14:16:26 UTC (1237817786)
[    1.721920] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.721922] EDD information not available.
[    1.722575] Freeing unused kernel memory: 424k freed
[    1.722640] Write protecting the kernel text: 2580k
[    1.722677] Write protecting the kernel read-only data: 940k
[    1.725652] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.024065] fuse init (API version 7.9)
[    2.165086] processor ACPI0007:00: registered as cooling_device0
[    2.165094] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.908355] No dock devices found.
[    2.981735] SCSI subsystem initialized
[    3.000498] ohci1394 0000:00:02.3: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.052331] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[f4000000-f40007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[    3.105476] usbcore: registered new interface driver usbfs
[    3.105517] usbcore: registered new interface driver hub
[    3.105581] usbcore: registered new device driver usb
[    3.164224] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.176099] libata version 3.00 loaded.
[    3.198337] sis900.c: v1.08.10 Apr. 2 2006
[    3.232757] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 6
[    3.232763] PCI: setting IRQ 6 as level-triggered
[    3.232769] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 6 (level, low) -> IRQ 6
[    3.232781] ohci_hcd 0000:00:03.0: setting latency timer to 64
[    3.232786] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.232880] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    3.232908] ohci_hcd 0000:00:03.0: irq 6, io mem 0x000d8000
[    3.290344] usb usb1: configuration #1 chosen from 1 choice
[    3.290388] hub 1-0:1.0: USB hub found
[    3.290407] hub 1-0:1.0: 2 ports detected
[    3.393295] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[    3.393303] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 5 (level, low) -> IRQ 5
[    3.393315] ohci_hcd 0000:00:03.1: setting latency timer to 64
[    3.393320] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.393388] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.393412] ohci_hcd 0000:00:03.1: irq 5, io mem 0x000da000
[    3.450326] usb usb2: configuration #1 chosen from 1 choice
[    3.450370] hub 2-0:1.0: USB hub found
[    3.450395] hub 2-0:1.0: 2 ports detected
[    3.552495] ohci_hcd 0000:00:03.2: enabling device (0000 -> 0002)
[    3.552872] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[    3.552878] ohci_hcd 0000:00:03.2: PCI INT C -> Link[LNKG] -> GSI 6 (level, low) -> IRQ 6
[    3.552900] ohci_hcd 0000:00:03.2: setting latency timer to 64
[    3.552905] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    3.552952] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[    3.552978] ohci_hcd 0000:00:03.2: irq 6, io mem 0x28040000
[    3.610533] usb usb3: configuration #1 chosen from 1 choice
[    3.610583] hub 3-0:1.0: USB hub found
[    3.610598] hub 3-0:1.0: 2 ports detected
[    3.816819] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.816827] ehci_hcd 0000:00:03.3: PCI INT D -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.816851] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.816899] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[    3.816949] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    3.816962] ehci_hcd 0000:00:03.3: irq 10, io mem 0xf4001000
[    3.828083] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.828379] usb usb4: configuration #1 chosen from 1 choice
[    3.828421] hub 4-0:1.0: USB hub found
[    3.828437] hub 4-0:1.0: 6 ports detected
[    3.933357] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.933363] PCI: setting IRQ 11 as level-triggered
[    3.933369] sis900 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.934553] 0000:00:04.0: ICS LAN PHY transceiver found at address 1.
[    3.946518] 0000:00:04.0: Using transceiver found at address 1 as default
[    3.947848] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 11, 00:40:d0:34:12:9a
[    3.954514] pata_sis 0000:00:02.5: version 0.5.2
[    3.955114] scsi0 : pata_sis
[    3.956091] scsi1 : pata_sis
[    3.957515] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    3.957520] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    4.004073] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    4.120463] ata1.00: ATA-6: FUJITSU MHS2040AT  D, 3003, max UDMA/100
[    4.120469] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.136532] ata1.00: configured for UDMA/100
[    4.221574] usb 3-2: configuration #1 chosen from 1 choice
[    4.247125] usbcore: registered new interface driver libusual
[    4.258395] Initializing USB Mass Storage driver...
[    4.259469] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.259624] usbcore: registered new interface driver usb-storage
[    4.259630] USB Mass Storage support registered.
[    4.259788] usb-storage: device found at 2
[    4.259792] usb-storage: waiting for device to settle before scanning
[    4.292483] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW-241, VX09, max UDMA/33
[    4.300316] ata2.00: configured for UDMA/33
[    4.300489] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHS2040A 3003 PQ: 0 ANSI: 5
[    4.300795] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.301399] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-241 VX09 PQ: 0 ANSI: 5
[    4.301638] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.354001] Driver 'sd' needs updating - please use bus_type methods
[    4.357038] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.357066] sd 0:0:0:0: [sda] Write Protect is off
[    4.357070] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.357110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.357240] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.357262] sd 0:0:0:0: [sda] Write Protect is off
[    4.357266] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.357305] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.357310]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.391874]  sda1 sda2 < sda5 >
[    4.428179] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.441325] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.441334] Uniform CD-ROM driver Revision: 3.20
[    4.441484] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.509153] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040d001000fe7d5]
[    4.857772] PM: Starting manual resume from disk
[    4.857778] PM: Resume from partition 8:5
[    4.857781] PM: Checking hibernation image.
[    4.858029] PM: Resume from disk failed.
[    4.966904] kjournald starting.  Commit interval 5 seconds
[    4.966931] EXT3-fs: mounted filesystem with ordered data mode.
[    9.257633] usb-storage: device scan complete
[    9.264597] scsi 2:0:0:0: Direct-Access     Generic  USB-SMC          0190 PQ: 0 ANSI: 0 CCS
[    9.271583] scsi 2:0:0:1: Direct-Access     Generic  USB-SDC/MMC/MSC  0190 PQ: 0 ANSI: 0 CCS
[    9.282694] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    9.282909] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.293697] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    9.293872] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   15.830473] udevd version 124 started
[   16.692231] Linux agpgart interface v0.103
[   16.847900] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.900532] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.957855] agpgart-sis 0000:00:00.0: SiS chipset [1039/0646]
[   16.963391] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xf0000000
[   17.192282] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1c00
[   17.340417] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   17.356069] ACPI: Power Button (FF) [PWRF]
[   17.356256] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   17.368049] ACPI: Sleep Button (CM) [SBTN]
[   17.368273] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   17.368665] ACPI: Lid Switch [LID]
[   17.514136] ACPI: Battery Slot [BAT0] (battery present)
[   17.514686] ACPI: AC Adapter [AC] (on-line)
[   17.860316] Yenta: CardBus bridge found at 0000:00:09.0 [1071:8640]
[   17.860343] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.860346] Yenta: Routing CardBus interrupts to PCI
[   17.860352] Yenta TI: socket 0000:00:09.0, mfunc 0x01021c72, devctl 0x44
[   18.096499] Yenta: ISA IRQ mask 0x0080, PCI irq 10
[   18.096505] Socket status: 30000006
[   18.414521] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/device:10/input/input5
[   18.428073] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.488281] irda_init()
[   18.488305] NET: Registered protocol family 23
[   18.579203] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
[   18.579246] nsc-ircc, chip->init
[   18.579258] nsc-ircc, Found chip at base=0x02e
[   18.579287] nsc-ircc, driver loaded (Dag Brattli)
[   18.579298] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.579331] nsc-ircc, Found chip at base=0x02e
[   18.579359] nsc-ircc, driver loaded (Dag Brattli)
[   18.579363] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.579581] nsc-ircc 00:09: disabled
[   18.620400] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.620514] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   19.096339] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   19.924059] intel8x0_measure_ac97_clock: measured 55363 usecs
[   19.924064] intel8x0: clocking to 48000
[   20.017006] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   20.323848] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   20.360611] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   22.715306] cs: IO port probe 0x100-0x3af: clean.
[   22.717134] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.717883] cs: IO port probe 0x820-0x8ff: clean.
[   22.718541] cs: IO port probe 0xc00-0xcf7: clean.
[   22.719403] cs: IO port probe 0xa00-0xaff: clean.
[   23.757472] lp0: using parport0 (interrupt-driven).
[   23.857108] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   23.955671] usbcore: registered new interface driver ndiswrapper
[   24.136821] Adding 1124508k swap on /dev/sda5.  Priority:-1 extents:1 across:1124508k
[   24.706188] EXT3 FS on sda1, internal journal
[   26.053437] type=1505 audit(1237817810.467:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3950
[   26.282322] type=1505 audit(1237817810.695:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3955
[   26.282782] type=1505 audit(1237817810.695:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3955
[   26.514079] ip_tables: (C) 2000-2006 Netfilter Core Team
[   27.559241] ACPI: WMI: Mapper loaded
[   28.923902] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   29.038082] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   29.038091] apm: overridden by ACPI.
[   29.313759] ppdev: user-space parallel port driver
[   31.284687] ttyS1: LSR safety check engaged!
[   31.540995] Bluetooth: Core ver 2.13
[   31.543519] NET: Registered protocol family 31
[   31.543528] Bluetooth: HCI device and connection manager initialized
[   31.543534] Bluetooth: HCI socket layer initialized
[   31.566677] Bluetooth: L2CAP ver 2.11
[   31.566686] Bluetooth: L2CAP socket layer initialized
[   31.581319] Bluetooth: SCO (Voice Link) ver 0.6
[   31.581327] Bluetooth: SCO socket layer initialized
[   31.598580] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.598588] Bluetooth: BNEP filters: protocol multicast
[   31.625900] Bridge firewalling registered
[   31.716751] Bluetooth: RFCOMM socket layer initialized
[   31.717732] Bluetooth: RFCOMM TTY layer initialized
[   31.717738] Bluetooth: RFCOMM ver 1.10
[   36.228091] NET: Registered protocol family 17
[   37.920792] eth0: Media Link On 100mbps full-duplex 
[   42.133200] NET: Registered protocol family 10
[   42.136075] lo: Disabled Privacy Extensions
[   52.888050] eth0: no IPv6 routers present
[  142.891197] ttyS1: LSR safety check engaged!
[  142.891232] type=1503 audit(1237817927.303:5): operation="capable" name="sys_admin" pid=5587 profile="/usr/sbin/cupsd"
[  143.192423] ppdev0: registered pardevice
[  143.240480] ppdev0: unregistered pardevice
[  145.700265] ppdev0: registered pardevice
[  145.748121] ppdev0: unregistered pardevice
[  147.023520] ppdev0: registered pardevice
[  147.073742] ppdev0: unregistered pardevice
[ 1038.920411] eth0: Media Link Off
[ 1124.432036] usb 4-2: new high speed USB device using ehci_hcd and address 2
[ 1124.572075] usb 4-2: configuration #1 chosen from 1 choice
[ 1124.748041] usb 4-2: reset high speed USB device using ehci_hcd and address 2
[ 1124.978876] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 1124.978909] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 1124.978920] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 1124.979057] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 1124.979070] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 1124.979087] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 1124.979121] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1124.979138] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 1124.979151] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 1124.979164] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1124.979177] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 1124.979190] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 1124.979203] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 1124.979221] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 1124.979234] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1124.979251] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1124.979264] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1124.979289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 1124.979337] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1124.979350] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1124.979363] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1124.979389] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1124.979407] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1124.979420] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1124.979433] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 1124.979446] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 1124.979459] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1124.979471] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 1124.979484] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 1124.979497] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 1124.979510] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1124.979523] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 1124.979536] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1124.979549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1124.979562] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 1124.979572] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 1124.979582] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 1124.979586] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathrusb'
[ 1124.991291] ndiswrapper (load_wrap_driver:108): couldn't load driver netathrusb; check system log for messages from 'loadndisdriver'
stephen@stephen-laptop:~$ sudo lshw -C network
[sudo] password for stephen: 
Sorry, try again.
[sudo] password for stephen: 
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:40:d0:34:12:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=128 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:05:eb:37:55:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
stephen@stephen-laptop:~$ lsb_release -d
Description:	Ubuntu 8.10
stephen@stephen-laptop:~$ uname -mr
2.6.27-11-generic i686
stephen@stephen-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
stephen@stephen-laptop:~$

---

