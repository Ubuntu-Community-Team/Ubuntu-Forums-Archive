---
title: "Mercury Tv tuner Help"
date: 2008-05-26
forum: Multimedia Software
---

### Post by frmneo999 on 2008-05-26
I am confused about how to install driver for a tv tuner. The thing is , the board is detected and some video decoder driver is installed.But when tried to run Tvtime or MyTv, it shows no Tuner device.

Output of lspci

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)
05:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

```


Output of dmesg

```
[   37.026557] hub 4-0:1.0: USB hub found
[   37.026561] hub 4-0:1.0: 2 ports detected
[   37.130363] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   37.130437] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   37.130446] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   37.130451] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   37.130474] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   37.134387] ehci_hcd 0000:00:1d.7: debug port 1
[   37.134393] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   37.134399] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x54004000
[   37.154208] e100: eth0: e100_probe: addr 0x51000000, irq 21, MAC addr 00:19:d1:76:ef:78
[   37.162203] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   37.174192] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.174297] usb usb5: configuration #1 chosen from 1 choice
[   37.174321] hub 5-0:1.0: USB hub found
[   37.174326] hub 5-0:1.0: 8 ports detected
[   37.276762] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   37.276794] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   37.276805] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   37.276828] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   37.276845] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.276854] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   37.279816] ata_piix 0000:00:1f.1: version 2.12
[   37.279827] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   37.279849] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   37.279916] scsi0 : ata_piix
[   37.279961] scsi1 : ata_piix
[   37.280409] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[   37.280411] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[   37.607332] ata1.00: ATAPI: SONY    DVD RW AW-G170A, 1.62, max UDMA/66
[   37.607466] ata1.01: ATA-6: SAMSUNG SP4002H, QU100-61, max UDMA/100
[   37.607470] ata1.01: 78242976 sectors, multi 16: LBA 
[   37.607490] ata1.00: limited to UDMA/33 due to 40-wire cable
[   37.607493] ata1.01: limited to UDMA/33 due to 40-wire cable
[   37.765902] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   37.779187] ata1.00: configured for UDMA/33
[   37.786270] ata1.01: configured for UDMA/33
[   37.786315] ata2: port disabled. ignoring.
[   37.788002] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-G170A  1.62 PQ: 0 ANSI: 5
[   37.788182] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP4002H  QU10 PQ: 0 ANSI: 5
[   37.788256] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   37.788275] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   37.788305] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   37.788352] scsi2 : ata_piix
[   37.788391] scsi3 : ata_piix
[   37.788858] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20e4 bmdma 0x20a0 irq 19
[   37.788861] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e0 bmdma 0x20a8 irq 19
[   37.942114] usb 2-2: configuration #1 chosen from 1 choice
[   37.957967] usbcore: registered new interface driver hiddev
[   37.960613] ata3.00: ATA-7: WDC WD1600AABS-00PRA0, 05.06H05, max UDMA/133
[   37.960619] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.971172] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
[   37.975260] ata3.00: configured for UDMA/133
[   38.001816] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-2
[   38.001834] usbcore: registered new interface driver usbhid
[   38.001838] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   38.138090] ata4.00: ATA-7: Hitachi HDS721680PLA380, P21OABEA, max UDMA/133
[   38.138096] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.154102] ata4.00: configured for UDMA/133
[   38.154258] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600AABS-0 05.0 PQ: 0 ANSI: 5
[   38.154440] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[   38.161934] Driver 'sr' needs updating - please use bus_type methods
[   38.164446] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   38.164449] Uniform CD-ROM driver Revision: 3.20
[   38.164493] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   38.169750] Driver 'sd' needs updating - please use bus_type methods
[   38.169819] sd 0:0:1:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   38.169830] sd 0:0:1:0: [sda] Write Protect is off
[   38.169833] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   38.169849] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.169896] sd 0:0:1:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   38.169905] sd 0:0:1:0: [sda] Write Protect is off
[   38.169907] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   38.169922] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.169926]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   38.171654] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   38.171672] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[   38.171688] scsi 3:0:0:0: Attached scsi generic sg3 type 0
[   38.176455]  sda1
[   38.176511] sd 0:0:1:0: [sda] Attached SCSI disk
[   38.176565] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   38.176576] sd 2:0:0:0: [sdb] Write Protect is off
[   38.176578] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.176594] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.176632] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   38.176642] sd 2:0:0:0: [sdb] Write Protect is off
[   38.176644] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.176659] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.176662]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
[   38.231164] sd 2:0:0:0: [sdb] Attached SCSI disk
[   38.231236] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   38.231253] sd 3:0:0:0: [sdc] Write Protect is off
[   38.231257] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   38.231282] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.231342] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   38.231356] sd 3:0:0:0: [sdc] Write Protect is off
[   38.231359] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   38.231383] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.231387]  sdc: sdc1 sdc2 < sdc5 >
[   38.277803] sd 3:0:0:0: [sdc] Attached SCSI disk
[   38.551389] Attempting manual resume
[   38.551392] swsusp: Resume From Partition 8:37
[   38.551393] PM: Checking swsusp image.
[   38.551522] PM: Resume from disk failed.
[   38.604982] kjournald starting.  Commit interval 5 seconds
[   38.604990] EXT3-fs: mounted filesystem with ordered data mode.
[   43.624000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.646743] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.666621] Linux agpgart interface v0.102
[   43.849227] input: Power Button (FF) as /devices/virtual/input/input3
[   43.875970] ACPI: Power Button (FF) [PWRF]
[   43.876048] input: Sleep Button (CM) as /devices/virtual/input/input4
[   43.906455] ACPI: Sleep Button (CM) [SLPB]
[   44.357094] nvidia: module license 'NVIDIA' taints kernel.
[   44.833954] iTCO_vendor_support: vendor-support=0
[   44.920335] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   44.920410] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   44.920442] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   44.989193] intel_rng: Firmware space is locked read-only. If you can't or
[   44.989195] intel_rng: don't want to disable this in firmware setup, and if
[   44.989197] intel_rng: you are certain that your system has a functional
[   44.989198] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   45.131673] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.131683] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   45.131787] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   45.209760] Linux video capture interface: v2.00
[   45.268374] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   45.268403] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   45.297739] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   45.299648] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   45.305800] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   45.511805] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   45.511861] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   45.511914] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   45.511915] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   45.511916] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   45.511917] cx88[0]: the TV card.  Best regards,
[   45.511918] cx88[0]:         -- tux
[   45.511920] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   45.511923] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   45.511924] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   45.511926] cx88[0]:    card=2 -> GDI Black Gold
[   45.511928] cx88[0]:    card=3 -> PixelView
[   45.511929] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   45.511931] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   45.511933] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   45.511935] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   45.511936] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   45.511938] cx88[0]:    card=9 -> Leadtek PVR 2000
[   45.511940] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   45.511942] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   45.511943] cx88[0]:    card=12 -> ASUS PVR-416
[   45.511945] cx88[0]:    card=13 -> MSI TV-@nywhere
[   45.511947] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   45.511948] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   45.511950] cx88[0]:    card=16 -> KWorld LTV883RF
[   45.511952] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   45.511954] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   45.511955] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   45.511957] cx88[0]:    card=20 -> Provideo PV259
[   45.511959] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   45.511961] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   45.511963] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   45.511965] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   45.511967] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   45.511969] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   45.511971] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   45.511973] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   45.511974] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   45.511976] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   45.511978] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   45.511980] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   45.511982] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   45.511984] cx88[0]:    card=34 -> ATI HDTV Wonder
[   45.511986] cx88[0]:    card=35 -> WinFast DTV1000-T
[   45.511987] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   45.511989] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   45.511991] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   45.511993] cx88[0]:    card=39 -> KWorld DVB-S 100
[   45.511994] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   45.511997] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   45.511999] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   45.512001] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   45.512003] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   45.512005] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   45.512006] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   45.512008] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   45.512010] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   45.512012] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   45.512014] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   45.512016] cx88[0]:    card=51 -> WinFast DTV2000 H
[   45.512017] cx88[0]:    card=52 -> Geniatech DVB-S
[   45.512019] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   45.512021] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   45.512023] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   45.512025] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   45.512027] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   45.512030] cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   45.512032] cx88[0]: TV tuner type -1, Radio tuner type -1
[   45.631024] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   45.631036] cx88[0]/0: found at 0000:05:05.0, rev: 5, irq: 17, latency: 32, mmio: 0x50000000
[   45.747863] All bytes are equal. It is not a TEA5767
[   45.747868] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   45.748095] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   45.757427] cx88[0]/0: registered device video0 [v4l2]
[   45.757448] cx88[0]/0: registered device vbi0
[   45.757465] tuner 0-0060: tuner type not set
[   45.942613] NET: Registered protocol family 10
[   45.942830] lo: Disabled Privacy Extensions
[   46.105156] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   46.156657] parport_pc 00:07: reported by Plug and Play ACPI
[   46.156685] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   46.621302] lp0: using parport0 (interrupt-driven).
[   46.666618] Adding 3020180k swap on /dev/sdc5.  Priority:-1 extents:1 across:3020180k
[   47.201335] EXT3 FS on sdc1, internal journal
[   48.279017] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.560736] PPP generic driver version 2.4.2
[   48.582157] NET: Registered protocol family 17
[   48.921237] No dock devices found.
[   49.068790] NET: Registered protocol family 24
[   49.824659] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   49.824664] apm: disabled - APM is not SMP safe.
[   49.995528] ppdev: user-space parallel port driver
[   50.177387] audit(1211779958.623:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5359 profile="/usr/sbin/cupsd" namespace="default"
[   55.774637] Bluetooth: Core ver 2.11
[   55.775189] NET: Registered protocol family 31
[   55.775193] Bluetooth: HCI device and connection manager initialized
[   55.775197] Bluetooth: HCI socket layer initialized
[   55.787569] Bluetooth: L2CAP ver 2.9
[   55.787575] Bluetooth: L2CAP socket layer initialized
[   55.841014] Bluetooth: RFCOMM socket layer initialized
[   55.841029] Bluetooth: RFCOMM TTY layer initialized
[   55.841032] Bluetooth: RFCOMM ver 1.8
[   56.519636] eth0: no IPv6 routers present
[   95.656638] UDF-fs: No VRS found
[   95.680323] ISO 9660 Extensions: Microsoft Joliet Level 3
[   95.694408] ISOFS: changing to secondary root
[  340.585358] ACPI: PCI interrupt for device 0000:05:08.0 disabled
[  341.935477] PM: suspend-to-disk mode set to 'platform'
[  341.935541] swsusp: Marking nosave pages: 000000000008f000 - 0000000000100000
[  341.935549] swsusp: Basic memory bitmaps created
[  341.935550] Syncing filesystems ... done.
[  341.935573] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  341.936166] Freezing remaining freezable tasks ... (elapsed 0.85 seconds) done.
[  342.788153] Shrinking memory... done (0 pages freed)
[  342.819255] Freed 0 kbytes in 0.03 seconds (0.00 MB/s)
[  342.819257] Suspending console(s)
[  342.819294] sd 3:0:0:0: [sdc] Synchronizing SCSI cache
[  342.819454] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
[  342.819744] sd 0:0:1:0: [sda] Synchronizing SCSI cache
[  342.820443] serial 00:0a: disabled
[  342.820562] parport_pc 00:07: disabled
[  342.820645] ACPI handle has no context!
[  342.836161] ACPI handle has no context!
[  342.836193] NVRM: RmPowerManagement: 3
[  343.047935] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  343.061116] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[  343.061236] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  343.077091] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[  343.077123] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  343.077155] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  343.077187] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  343.093044] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  343.109586] Disabling non-boot CPUs ...
[  343.109605] CPU0 attaching NULL sched-domain.
[  343.109606] CPU1 attaching NULL sched-domain.
[  343.223943] CPU 1 is now offline
[  343.223947] SMP alternatives: switching to UP code
[  343.225326] CPU0 attaching sched-domain:
[  343.225329]  domain 0: span 01
[  343.225330]   groups: 01
[  343.225529] CPU1 is down
[  343.225699] swsusp: critical section: 
[  343.245692] swsusp: Need to copy 117167 pages
[  343.245696] swsusp: Normal pages needed: 117034 + 1024 + 24, available pages: 144138
[   53.684511] Enabling non-boot CPUs ...
[   53.684572] CPU0 attaching NULL sched-domain.
[   53.694808] SMP alternatives: switching to SMP code
[   53.695965] Booting processor 1/1 eip 3000
[   53.706126] Initializing CPU#1
[   53.786628] Calibrating delay using timer specific routine.. 3591.19 BogoMIPS (lpj=7182392)
[   53.786635] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   53.786641] monitor/mwait feature present.
[   53.786644] CPU: L1 I cache: 32K, L1 D cache: 32K
[   53.786646] CPU: L2 cache: 2048K
[   53.786648] CPU: Physical Processor ID: 0
[   53.786649] CPU: Processor Core ID: 1
[   53.786651] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   53.787232] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[   53.787262] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   53.807289] CPU0 attaching sched-domain:
[   53.807292]  domain 0: span 03
[   53.807293]   groups: 01 02
[   53.807296] CPU1 attaching sched-domain:
[   53.807297]  domain 0: span 03
[   53.807299]   groups: 02 01
[   53.807648] CPU1 is up
[   53.807908] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   53.811298] Switched to high resolution mode on CPU 1
[   53.823685] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100006, writing 100002)
[   53.823708] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   53.823716] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   53.920400] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   53.920449] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   53.920498] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   53.920505] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   53.920511] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   53.920554] usb usb1: root hub lost power or was reset
[   53.920570] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   53.920574] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   53.920616] usb usb2: root hub lost power or was reset
[   53.920633] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   53.920639] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   53.920680] usb usb3: root hub lost power or was reset
[   53.920695] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   53.920700] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   53.920741] usb usb4: root hub lost power or was reset
[   53.935599] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   53.935606] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   53.935650] usb usb5: root hub lost power or was reset
[   53.939539] ehci_hcd 0000:00:1d.7: debug port 1
[   53.939544] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   54.059570] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   54.059637] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2880001, writing 2880005)
[   54.059649] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   54.059655] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   54.059697] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00001, writing 2b00005)
[   54.059713] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   54.059719] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   54.059821] NVRM: RmPowerManagement: 5
[   54.060626] ata2: port disabled. ignoring.
[   54.223281] ata4.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   54.223349] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   54.223415] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   54.223418] ata1.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
[   54.223420] ata1.01: ACPI cmd f5/00:00:00:00:00:b0 filtered out
[   54.238829] ata4.00: configured for UDMA/133
[   54.238902] sd 3:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[   54.238920] sd 3:0:0:0: [sdc] Write Protect is off
[   54.238923] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   54.238949] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.264454] ata3.00: configured for UDMA/133
[   54.371828] parport_pc 00:07: activated
[   54.371838] i8042 aux 00:08: activation failed
[   54.371846] i8042 kbd 00:09: activation failed
[   54.372115] serial 00:0a: activated
[   54.386724] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   54.386726] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[   54.386729] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   54.558582] ata1.00: configured for UDMA/33
[   54.567628] ata1.01: configured for UDMA/33
[   54.567669] sd 0:0:1:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   54.567690] sd 0:0:1:0: [sda] Write Protect is off
[   54.567693] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   54.567729] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.567766] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   54.567785] sd 2:0:0:0: [sdb] Write Protect is off
[   54.567788] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   54.567822] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.567856] sd 0:0:1:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   54.567874] sd 0:0:1:0: [sda] Write Protect is off
[   54.567877] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   54.567909] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   55.921630] sd 0:0:1:0: [sda] Starting disk
[   55.924879] sd 2:0:0:0: [sdb] Starting disk
[   55.928602] sd 3:0:0:0: [sdc] Starting disk
[   55.962135] PM: Image restored successfully.
[   55.997896] Restarting tasks ... <6>usb 2-2: USB disconnect, address 3
[   55.999490] done.
[   55.999497] swsusp: Basic memory bitmaps freed
[   56.114132] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   56.114136] e100: Copyright(c) 1999-2006 Intel Corporation
[   56.114197] PCI: Enabling device 0000:05:08.0 (0000 -> 0003)
[   56.114203] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   56.114267] PCI: Setting latency timer of device 0000:05:08.0 to 64
[   56.138237] e100: eth0: e100_probe: addr 0x51000000, irq 21, MAC addr 00:19:d1:76:ef:78
[   56.173485] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   56.174841] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.176804] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   56.282324] usb 2-2: new low speed USB device using uhci_hcd and address 4
[   56.474387] usb 2-2: configuration #1 chosen from 1 choice
[   56.491482] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input7
[   56.610286] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-2
[   66.847724] eth0: no IPv6 routers present
[ 2148.111397] tuner 0-0060: tuner type not set
[ 2148.373790] tuner 0-0060: tuner type not set
[ 2154.065311] tuner 0-0060: tuner type not set
[ 2154.710341] tuner 0-0060: tuner type not set
[ 2155.350023] tuner 0-0060: tuner type not set
[ 2155.949738] tuner 0-0060: tuner type not set
[ 2181.430975] tuner 0-0060: tuner type not set
[ 2181.433770] tuner 0-0060: tuner type not set
[ 2183.799483] cx88[0]: video y / packed - dma channel status dump
[ 2183.799491] cx88[0]:   cmds: initial risc: 0x05734000
[ 2183.799495] cx88[0]:   cmds: cdt base    : 0x00180440
[ 2183.799499] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 2183.799502] cx88[0]:   cmds: iq base     : 0x00180400
[ 2183.799506] cx88[0]:   cmds: iq size     : 0x00000010
[ 2183.799510] cx88[0]:   cmds: risc pc     : 0x054b8034
[ 2183.799513] cx88[0]:   cmds: iq wr ptr   : 0x0000010a
[ 2183.799517] cx88[0]:   cmds: iq rd ptr   : 0x0000010e
[ 2183.799520] cx88[0]:   cmds: cdt current : 0x00000498
[ 2183.799524] cx88[0]:   cmds: pci target  : 0x0571a800
[ 2183.799528] cx88[0]:   cmds: line / byte : 0x03200000
[ 2183.799531] cx88[0]:   risc0: 0x80008000 [ sync resync count=0 ]
[ 2183.799538] cx88[0]:   risc1: 0x1c0005a0 [ write sol eol count=1440 ]
[ 2183.799545] cx88[0]:   risc2: 0x0571c000 [ arg #1 ]
[ 2183.799549] cx88[0]:   risc3: 0x180004c0 [ write sol count=1216 ]
[ 2183.799555] cx88[0]:   iq 0: 0x180004c0 [ write sol count=1216 ]
[ 2183.799561] cx88[0]:   iq 1: 0x0571cb40 [ arg #1 ]
[ 2183.799564] cx88[0]:   iq 2: 0x140000e0 [ write eol count=224 ]
[ 2183.799570] cx88[0]:   iq 3: 0x0571d000 [ arg #1 ]
[ 2183.799574] cx88[0]:   iq 4: 0x1c0005a0 [ write sol eol count=1440 ]
[ 2183.799580] cx88[0]:   iq 5: 0x0571d680 [ arg #1 ]
[ 2183.799584] cx88[0]:   iq 6: 0x1c0005a0 [ write sol eol count=1440 ]
[ 2183.799590] cx88[0]:   iq 7: 0x0571e1c0 [ arg #1 ]
[ 2183.799594] cx88[0]:   iq 8: 0x18000300 [ write sol count=768 ]
[ 2183.799600] cx88[0]:   iq 9: 0x0571ed00 [ arg #1 ]
[ 2183.799603] cx88[0]:   iq a: 0x1c0005a0 [ write sol eol count=1440 ]
[ 2183.799610] cx88[0]:   iq b: 0x0571a260 [ arg #1 ]
[ 2183.799613] cx88[0]:   iq c: 0x71010000 [ jump irq1 cnt0 count=0 ]
[ 2183.799620] cx88[0]:   iq d: 0x80008000 [ arg #1 ]
[ 2183.799623] cx88[0]:   iq e: 0x1c0005a0 [ write sol eol count=1440 ]
[ 2183.799630] cx88[0]:   iq f: 0x0571c000 [ arg #1 ]
[ 2183.799632] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 2183.799635] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 2183.799638] cx88[0]:   ptr1_reg: 0x00180c00
[ 2183.799641] cx88[0]:   ptr2_reg: 0x00180448
[ 2183.799645] cx88[0]:   cnt1_reg: 0x00000004
[ 2183.799648] cx88[0]:   cnt2_reg: 0x00000000
[ 2183.799656] cx88[0]/0: [f70b5000/2] timeout - dma=0x054b8000
[ 2183.799660] cx88[0]/0: [f70b5300/3] timeout - dma=0x05734000

```



Please help me in how to solve this. i am a newbie user in Linux.:confused:

---

### Post by frmneo999 on 2008-05-27
[-o<[-o<[-o< Help me any one.. :( u have an important show to record.. :((pleaaaasseeee

---

### Post by cariboo on 2008-05-27
I've got a MSI tv@nywhere and it was not detected properly either, what I had to do is figure out what type of card it was and then add a file to /etc/modprobe.d. In your case dmesg gives you enough information to make it fairly easy to get it to work. You are going to have to do most of this in a terminal so here goes. The terminal is located in Applications|Accressories.

Step 1:

```
sudo touch /etc/modprobe.d/mercury
```

Step 2:

```
sudo gedit /etc/modprobe.d/mercury
```

Step 3:

In gedit type the following:

```
alias char-major-81 videodev
alias char-major-81-0 cx88
options cx88 card=X
```

where X= card number as shown in dmesg, I'd probably try 0 first.
Save the file


Step 4:

In a terminal

```
sudo rmmod cx88
sudo modprobe cx88
```

Step 5:

Try tvtime, if it doesn't work you have to try some of the other card numbers in dmesg

Good luck

Jim

---

### Post by frmneo999 on 2008-05-27
Thanks cariboo! :) I tried your method..  Everything fine upto step 3 with crad number as 0.

step 4 gave following error.. 

```
neo@neo-desktop:~$ sudo rmmod cx88
ERROR: Module cx88 does not exist in /proc/modules
neo@neo-desktop:~$ sudo modprobe cx88
FATAL: Module cx88 not found.
neo@neo-desktop:~$ 


```

What to do now??

---

### Post by frmneo999 on 2008-05-27
Scanning tvtime gave following error..

```
neo@neo-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/neo/.tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Can't get tuner info: Invalid argument
videoinput: Driver refuses to start streaming: Device or resource busy.
videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument
videoinput: Driver refuses to start streaming: Device or resource busy.
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

videoinput: Driver refuses to stop streaming: Invalid argument.
videoinput: Can't free frame 0: Invalid argument
videoinput: Can't free frame 1: Invalid argument
videoinput: Can't free frame 2: Invalid argument
videoinput: Can't free frame 3: Invalid argument
neo@neo-desktop:~$ 

```

---

### Post by frmneo999 on 2008-05-29
no one?? :(

---

### Post by Fir3chi3f on 2008-10-23
try adding 00 to that, ie:

```
sudo rmmod cx8800
sudo modprobe cx8800
```

good luck

---

