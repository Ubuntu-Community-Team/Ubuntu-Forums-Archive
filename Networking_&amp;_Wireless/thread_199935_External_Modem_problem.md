---
title: "External Modem problem"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by cubdukat on 2006-06-19
I just installed Breezy Badger about a week ago, and generally I am happy with it, except I am unable to get online.

It cannot detect my modem, and seems not to have activated my serial ports either.

Here is the dmesg entry. I'm not sure what other logs I should have presented, but I hope this works. I am not able to mount my XP drive, so in order to be able to mail this, I had to save it onto a DVD-RW.

d: 16 RAM disks of 65536K size 1024 blocksize
[4294671.920000] EISA: Probing bus 0 at eisa.0
[4294671.920000] Cannot allocate resource for EISA slot 1
[4294671.920000] EISA: Detected 0 cards.
[4294671.920000] NET: Registered protocol family 2
[4294672.076000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294672.076000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294672.076000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.076000] TCP: Hash tables configured (established 32768 bind 32768)
[4294672.076000] NET: Registered protocol family 8
[4294672.076000] NET: Registered protocol family 20
[4294672.076000] ACPI wakeup devices: 
[4294672.076000] PCI0 HUB0 USB0 USB1 USB2 USB3 USBE 
[4294672.076000] ACPI: (supports S0 S1 S4 S5)
[4294672.076000] Freeing unused kernel memory: 224k freed
[4294672.122000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294672.125000] vga16fb: initializing
[4294672.125000] vga16fb: mapped to 0xc00a0000
[4294672.524000] Console: switching to colour frame buffer device 80x30
[4294672.524000] fb0: VGA16 VGA frame buffer device
[4294673.809000] Capability LSM initialized
[4294673.820000] NET: Registered protocol family 1
[4294673.835000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.835000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.835000] ACPI: bus type ide registered
[4294673.845000] SCSI subsystem initialized
[4294673.846000] libata version 1.11 loaded.
[4294673.847000] ata_piix version 1.03
[4294673.847000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[4294673.847000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.848000] ata1: SATA max UDMA/133 cmd 0xC000 ctl 0xC402 bmdma 0xD000 irq 18
[4294673.848000] ata2: SATA max UDMA/133 cmd 0xC800 ctl 0xCC02 bmdma 0xD008 irq 18
[4294673.848000] ata1: SATA port has no device.
[4294673.848000] scsi0 : ata_piix
[4294674.002000] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3468 86:3c01 87:4003 88:207f
[4294674.002000] ata2: dev 0 ATA, max UDMA/133, 312579695 sectors: lba48
[4294674.002000] ata2: dev 0 configured for UDMA/133
[4294674.002000] scsi1 : ata_piix
[4294674.003000]   Vendor: ATA       Model: ST3160827AS       Rev: 3.42
[4294674.003000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294674.011000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[4294674.011000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294674.011000] ICH5: chipset revision 2
[4294674.011000] ICH5: not 100% native mode: will probe irqs later
[4294674.011000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[4294674.011000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[4294674.011000] Probing IDE interface ide0...
[4294674.275000] hda: Maxtor 5T060H6, ATA DISK drive
[4294674.530000] hdb: Maxtor 6Y120L0, ATA DISK drive
[4294674.581000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.581000] Probing IDE interface ide1...
[4294675.253000] hdc: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
[4294675.865000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.865000] Probing IDE interface ide2...
[4294676.378000] Probing IDE interface ide3...
[4294676.890000] Probing IDE interface ide4...
[4294677.402000] Probing IDE interface ide5...
[4294677.917000] hda: max request size: 128KiB
[4294677.918000] hda: Host Protected Area detected.
[4294677.918000] 	current capacity is 120101087 sectors (61491 MB)
[4294677.918000] 	native  capacity is 120103200 sectors (61492 MB)
[4294677.918000] hda: Host Protected Area disabled.
[4294677.918000] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294677.918000] hda: cache flushes not supported
[4294677.918000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294677.922000] hdb: max request size: 128KiB
[4294677.923000] hdb: Host Protected Area detected.
[4294677.923000] 	current capacity is 240119615 sectors (122941 MB)
[4294677.923000] 	native  capacity is 240121728 sectors (122942 MB)
[4294677.954000] hdb: Host Protected Area disabled.
[4294677.954000] hdb: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294677.954000] hdb: cache flushes supported
[4294677.954000]  /dev/ide/host0/bus0/target1/lun0: p1
[4294677.982000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294677.982000] Uniform CD-ROM driver Revision: 3.20
[4294677.989000] SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
[4294677.989000] SCSI device sda: drive cache: write back
[4294677.989000] SCSI device sda: 312579695 512-byte hdwr sectors (160041 MB)
[4294677.989000] SCSI device sda: drive cache: write back
[4294677.989000]  /dev/scsi/host1/bus0/target0/lun0: p1 p2 p3 < p5 >
[4294678.026000] Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
[4294678.318000] Attempting manual resume
[4294678.319000] swsusp: Suspend partition has wrong signature?
[4294678.341000] usbcore: registered new driver usbfs
[4294678.341000] usbcore: registered new driver hub
[4294678.342000] USB Universal Host Controller Interface driver v2.2
[4294678.342000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294678.342000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294678.342000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
[4294678.404000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294678.404000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bc00
[4294678.404000] hub 1-0:1.0: USB hub found
[4294678.404000] hub 1-0:1.0: 2 ports detected
[4294678.407000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294678.407000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294678.407000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
[4294678.469000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294678.469000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[4294678.469000] hub 2-0:1.0: USB hub found
[4294678.469000] hub 2-0:1.0: 2 ports detected
[4294678.472000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294678.472000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294678.472000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI #3
[4294678.534000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294678.534000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[4294678.534000] hub 3-0:1.0: USB hub found
[4294678.534000] hub 3-0:1.0: 2 ports detected
[4294678.537000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[4294678.537000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294678.537000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
[4294678.599000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294678.599000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[4294678.599000] hub 4-0:1.0: USB hub found
[4294678.599000] hub 4-0:1.0: 2 ports detected
[4294678.630000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[4294678.630000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294678.630000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
[4294678.630000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294678.631000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdf100000
[4294678.634000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294678.634000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294678.635000] hub 5-0:1.0: USB hub found
[4294678.635000] hub 5-0:1.0: 8 ports detected
[4294678.641000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[4294678.746000] r8169 Gigabit Ethernet driver 2.2LK loaded
[4294678.746000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294678.747000] eth0: Identified chip type is 'RTL8169s/8110s'.
[4294678.747000] eth0: RTL8169 at 0xe08c2000, 00:14:85:b1:ea:d0, IRQ 20
[4294679.138000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[4294681.512000] ACPI: Fan [FAN] (on)
[4294681.515000] ACPI: CPU0 (power states: C1[C1])
[4294681.516000] ACPI: Thermal Zone [THRM] (22 C)
[4294681.881000] Attempting manual resume
[4294681.881000] swsusp: Suspend partition has wrong signature?
[4294681.890000] kjournald starting.  Commit interval 5 seconds
[4294681.890000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.737000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.520000] Adding 931728k swap on /dev/sda5.  Priority:-1 extents:1
[4294686.925000] EXT3 FS on sda2, internal journal
[4294693.364000] parport: PnPBIOS parport detected.
[4294693.364000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[4294693.450000] lp0: using parport0 (interrupt-driven).
[4294693.472000] mice: PS/2 mouse device common for all mice
[4294693.545000] ieee1394: Initialized config rom entry `ip1394'
[4294693.552000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294693.748000] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[4294694.454000] ts: Compaq touchscreen protocol output
[4294696.901000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294697.991000] cdrom: open failed.
[4294700.758000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.766000] agpgart: Detected an Intel 865 Chipset.
[4294700.786000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294700.862000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.872000] shpchp: shpc_init : shpc_cap_offset == 0
[4294700.872000] shpchp: shpc_init : shpc_cap_offset == 0
[4294700.873000] shpchp: shpc_init : shpc_cap_offset == 0
[4294700.873000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294701.199000] hw_random: RNG not detected
[4294701.602000] Linux video capture interface: v1.00
[4294701.643000] bttv: driver version 0.9.15 loaded
[4294701.643000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294701.647000] bttv: Bt8xx card found (0).
[4294701.647000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294701.647000] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 21, latency: 32, mmio: 0xdf000000
[4294701.647000] bttv0: subsystem: 18ac:d210 (UNKNOWN)
[4294701.647000] please mail id, board name and the correct card= insmod option to [email]kraxel@bytesex.org[/email]
[4294701.647000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[4294701.647000] bttv0: gpio: en=00000000, out=00000000 in=00fffff7 [init]
[4294701.759000] bttv0: using tuner=-1
[4294701.759000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294701.761000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294701.763000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294701.765000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294701.793000] bttv0: registered device video0
[4294701.808000] bttv0: registered device vbi0
[4294701.904000] bt878: AUDIO driver version 0.0.0 loaded
[4294701.908000] bt878: Bt878 AUDIO function found (0).
[4294701.908000] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 21 (level, low) -> IRQ 21
[4294701.908000] bt878(0): Bt878 (rev 17) at 02:01.1, irq: 21, latency: 32, memory: 0xdf001000
[4294702.096000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294702.099000] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[4294703.020000] gameport: EMU10K1 is pci0000:02:03.1/gameport0, io 0xa400, speed 1147kHz
[4294703.149000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294703.149000] ACPI: PCI Interrupt 0000:02:03.2[B] -> GSI 18 (level, low) -> IRQ 18
[4294703.203000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[de005000-de0057ff]  Max Packet=[2048]
[4294703.203000] ACPI: PCI Interrupt 0000:03:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294703.258000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dc004000-dc0047ff]  Max Packet=[2048]
[4294703.566000] cx2388x v4l2 driver version 0.0.4 loaded
[4294703.569000] ACPI: PCI Interrupt 0000:03:0d.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294703.569000] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[4294703.569000] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[4294703.569000] cx88[0]: workaround that.  Redirect complaints to the vendor of
[4294703.569000] cx88[0]: the TV card.  Best regards,
[4294703.569000] cx88[0]:         -- tux
[4294703.570000] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[4294703.570000] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[4294703.570000] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[4294703.570000] cx88[0]:    card=2 -> GDI Black Gold
[4294703.570000] cx88[0]:    card=3 -> PixelView
[4294703.570000] cx88[0]:    card=4 -> ATI TV Wonder Pro
[4294703.570000] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[4294703.570000] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[4294703.570000] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[4294703.570000] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[4294703.570000] cx88[0]:    card=9 -> Leadtek PVR 2000
[4294703.570000] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[4294703.570000] cx88[0]:    card=11 -> Prolink PlayTV PVR
[4294703.570000] cx88[0]:    card=12 -> ASUS PVR-416
[4294703.570000] cx88[0]:    card=13 -> MSI TV-@nywhere
[4294703.570000] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[4294703.570000] cx88[0]:    card=15 -> DVICO FusionHDTV DVB-T1
[4294703.570000] cx88[0]:    card=16 -> KWorld LTV883RF
[4294703.570000] cx88[0]:    card=17 -> DViCO - FusionHDTV 3 Gold
[4294703.570000] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[4294703.570000] cx88[0]:    card=19 -> Conexant DVB-T reference design
[4294703.570000] cx88[0]:    card=20 -> Provideo PV259
[4294703.570000] cx88[0]:    card=21 -> DVICO FusionHDTV DVB-T Plus
[4294703.570000] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[4294703.570000] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[4294703.570000] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[4294703.570000] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[4294703.570000] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[4294703.570000] cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294703.685000] tveeprom(cx88xx internal): Huh, no eeprom present (err=-121)?
[4294703.685000] cx88[0]/0: found at 0000:03:0d.0, rev: 5, irq: 21, latency: 32, mmio: 0xdb000000
[4294703.702000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294703.799000] cx88[0]/0: registered device video1 [v4l2]
[4294703.815000] cx88[0]/0: registered device vbi1
[4294704.461000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0151038931]
[4294704.721000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0009080000009fc8]
[4294705.449000] usbcore: registered new driver snd-usb-audio
[4294705.825000] Real Time Clock Driver v1.12
[4294705.905000] input: PC Speaker
[4294705.985000] Floppy drive(s): fd0 is 1.44M
[4294706.009000] FDC 0 is a post-1991 82077
[4294707.143000] CSLIP: code copyright 1989 Regents of the University of California
[4294707.145000] PPP generic driver version 2.4.2
[4294707.169000] NET: Registered protocol family 10
[4294707.169000] Disabled Privacy Extensions on device c02eb280(lo)
[4294707.169000] IPv6 over IPv4 tunneling driver
[4294708.325000] NET: Registered protocol family 17

---

### Post by zxee on 2006-06-19
What have you tried to configure dial up? I'm presuming this is dial-up phone line connection through your isp. The 1st step is to open a shell and type pppconfig >enter> then, hopefully, after you complete the configuration, you can use modem monitor, wvdial, or pon to connect.

---

### Post by cubdukat on 2006-06-19
[QUOTE=zxee]What have you tried to configure dial up? I'm presuming this is dial-up phone line connection through your isp. The 1st step is to open a shell and type pppconfig >enter> then, hopefully, after you complete the configuration, you can use modem monitor, wvdial, or pon to connect.[/QUOTE]

I tried using pppconfig first and it picked up both serial ports, but selected "Manual." The modem was on, so I have no idea why it didn't see it.

The modem is a Zoom 2949L circa 1998, but I don't think that would be it, because allegedly all hardware modems are supposed to work. Right now I'm wondering if this might not be some issue in the 2.6.13 kernel, because this has happened with every distro I've used so far that has it (Mandriva, FC5, Suse 10.0), and it's only worked once with Suse 10, and then inconsistently.

I may use this as an excuse to get a new modem

---

### Post by zxee on 2006-06-21
> I tried using pppconfig first and it picked up both serial ports, but selected "Manual." The modem was on, so I have no idea why it didn't see it.

After pppconfig asks you to manually select your modem-did you? Often that's just a small snag. If you choose the correct modem device which is probably /dev/ttyS0 then it might just work. BTW in linux external modems are almost always ttyS0 or ttyS1 so try S1 if S0 doesn't work. Hope that helps.

---

### Post by cubdukat on 2006-06-22
Yeah, I tried that. I set up a link to ttyS1, since that corresponds to COM 2, which is what it's hooked up to in XP, but that didn't work.

I'll try setting it up again, but I recently cross-graded to Kubuntu 6.06, but it seems that the procedure is still the same.

So far I'm not overly impressed with it, so I may go back to Ubuntu 5.10, since I don't have to download that one.

---

### Post by cubdukat on 2006-06-22
[QUOTE=cubdukat]Yeah, I tried that. I set up a link to ttyS1, since that corresponds to COM 2, which is what it's hooked up to in XP, but that didn't work.

I'll try setting it up again, but I recently cross-graded to Kubuntu 6.06, but it seems that the procedure is still the same.

So far I'm not overly impressed with it, so I may go back to Ubuntu 5.10, since I don't have to download that one.[/QUOTE]

Okay, I reinstalled Ubuntu 5.10, and I'm right back where I was before. I used pppconfig to set things up, but after it's done, it doesn't even attempt to connect when I type "sudo pon provider."

I know that the modem responds because I also did a "echo 'AT&F' > /dev/ttyS1" and a light on the front panel flashed. So, it's like it knows it's there, but it's refusing to acknowledge it. If it couldn't detect the modem at all, it wouldn't even respond, would it?

If it turns out that it's some option in the kernel that isn't switched on (doubtful, but possible), how would I go about switching it on? Would I have to recompile the kernel?

---

### Post by zxee on 2006-06-22
Try using wvdial or opening gnome-ppp from the terminal, and then copy and paste the terminal output here-that also can give you info to work with-it's how I've learned to troubleshoot ppp problems. And, no, you should not need to recompile the kernel to get an external modem working.

---

### Post by cubdukat on 2006-06-22
[QUOTE=zxee]Try using wvdial or opening gnome-ppp from the terminal, and then copy and paste the terminal output here-that also can give you info to work with-it's how I've learned to troubleshoot ppp problems. And, no, you should not need to recompile the kernel to get an external modem working.[/QUOTE]

Tried using gnome-ppp, but it doesn't seem to be installed, and I couldn't add it because it doesn't appear to be on the 5.10 CD. I could download it, but I would end up having to download a lot of other stuff as well, since I have no idea if the other things it depends on are already installed or not. This is what sucks about not having a working modem.

I tried pppconfig again, and this time, it polled the serial ports, and the modem responded (one of the lights came on and stayed on until the screen changed) but it still gave me the manual option. I'm wondering if the fact that it's an older model (V.90) might have something to do with it. Since I'm going to end up replacing the thing anyways, I might experiment with flashing it up to V.92 and see if that works. If not, I still have my laptop.

---

### Post by cubdukat on 2006-06-23
Well, I went ahead and flashed the modem to V.92, and it works perfectly...in XP, that is. 

Sadly, it's still inactive in Ubuntu, and I have no explanation for why that is. There's no earthly reason why it shouldn't work, and yet it doesn't.

The modem's on COM 2, according to XP, which translates into ttyS1 in Ubuntu, and whenever I do an echo "AT&F" > /dev/ttyS1, it responds, but when I do wvdial, it refuses to show up, and doing pppconfig is no better. I'm coming to the conclusion that apparently not all serial modems work in Linux, contrary to pouplar belief, and I no longer have the patience to deal with it.

I've been through five different distros, and I've only gotten the damn thing to work once, and even then never consistently. If I could get broadband, this wouldn't even be an issue, but I can't.

I even tried modem-monitor, and that didn't work either. It just sat there like an idiot and didn't even attempt to dial.

I don't know what could be going on here, but I've had it. Ubuntu will probably be coming off the drive this weekend, since I'm not overly impressed with it otherwise.

---

### Post by Slim Odds on 2006-06-23
A couple of things:

Breezy is old, try Dapper.

Serial modems usually need a symbolic link named **modem** that points to the actual device: like /dev/modem -> /dev/ttyS1

Most software that want to do modem stuff does not want to guess which device to use, so they default to using the device called modem.

Good luck

---

### Post by zxee on 2006-06-23
As a long time linux dial up user there really is little excuse for the problems you're having. Except that over the last couple of years more people, including developers are using broadband. 
There's no reason to create symbolic links if pppconfig sets up the configuration files in /etc/ppp correctly. And while it might sound argumentative switching to dapper will not help you. I've been using ubuntu since hoary on both macs and pcs dapper has major problems with dial up. Sorry but that's my experiance and that of quite a few others here on the forums.
There are so many things to try and it could be any one that's causing the problem. The last thing I would suggest is checking permissions on the modem > ls -la  /dev/ttyS1 and pppd itself > ls -la  /usr/sbin/pppd Note: there should be a space after the ls -la the way it gets formatted here doesn't show that clearly.
And if that doesn't work try and let the developers know about your experiances. 
You could try pclinuxos too.

---

### Post by cubdukat on 2006-06-23
Thanks for mentioning permissions. I keep forgetting that you actually have to do things like that in Linux.

I'll take a look at that. 

One thing, though--if it was a matter of permissions, wouldn't it tell me outright that I didn't have permission to access the modem instead of just ignoring me?

Also, is it possible to set permissions for either a symbolic link and/or a device?

---

### Post by zxee on 2006-06-24
[QUOTE=cubdukat]Thanks for mentioning permissions. I keep forgetting that you actually have to do things like that in Linux.

I'll take a look at that. 

One thing, though--if it was a matter of permissions, wouldn't it tell me outright that I didn't have permission to access the modem instead of just ignoring me?

Also, is it possible to set permissions for either a symbolic link and/or a device?[/QUOTE]

Normally for the device I'd say yes-although in ubuntu because of the way sudo is set up maybe not...
The pppd file is another matter.  I've seem plenty of cases where the group that pppd is in is not one the user can access and it totally prevents connection. 
Here's my pppd permissions:
:~$ ls -la /usr/sbin/pppd
-r-xr-xr-x  1 root root 234072 2005-03-14 20:40 /usr/sbin/pppd*
and the modem:
crw-rw----  1 root uucp 4, 64 2006-06-24 02:22 /dev/ttyS0

BTW I'm not in ubuntu because I've had some drop outs (crumby phone lines and or isp)
the above is from frugalware Once my connection drops in ubuntu I have to reboot to reconnect, but I'll post my ubuntu permissions when I'm back in that again. IMO the thing that often gets messed up is owner and/or group of pppd.

Added 6-24-06
I believe that the default dapper install sets up pppd so that the user can't run it.

compare the 1st pppd, below (working) with the 2nd one (not-working)

root@runecaster:/mnt/hdf1/usr/sbin# ls -la pppd
-rwsr-x---  1 john 1000 378632 2005-09-04 13:27 pppd

root@runecaster:/mnt/hdf1/usr/sbin# ls -la pppd.old
-rwxrwxrwx  1 root daemon 257720 2006-02-23 11:33 pppd.old
root@runecaster:/mnt/hdf1/usr/sbin#

File ownership is the problem I think. Making my user and the group one the user belongs to in the working pppd seems to have made the difference between connecting and not.

---

### Post by cubdukat on 2006-06-24
So, just to make sure I have this right:

If I'm in group dialout, but pppd belongs to group dip, I have to change the group ownership of pppd to dialout? (I actually belong to both.)

Last night I experimented with ownership. I changed the ownership of both the /dev/modem link and /dev/ttyS1 over to my user and the dialout group and I did the same for pppd. 

Unfortunately, that didn't work either. I'll try to grab some screenshots of what I did, but I'm not very optimistic at this point.

---

### Post by zxee on 2006-06-24
dip or dialout; as long as you belong to both then it doesn't matter.
Since I have seen ownership of pppd be the problem I thought that might be the solution for you-sorry. I don't know what else to try either.

---

### Post by cubdukat on 2006-07-02
I found something very interesting while poking around. i suspect that the serial port driver is not being loaded for whatever reason. I checked the boot logs, and there's no mention of it, then I did an lsmod, and it wasn't there either.

The only thing is that if that was the case, why would the modem respond to an echo "AT&F" > /dev/ttyS1 command? It should be as if there was nothing there.

Another possibility I might have found is that the modem cable is not the same cable it came with. I suspect that I may have picked up a regular 25-pin to 9-pin cable, and not a true modem cable. But if that was the case, wouldn't that also cause the modem not to work in XP as well? And if so, how is it that both Mandriva and Suse picked it up?

All I can say is that it's looking more and more like I should consider getting a new modem. I'm getting tired of screwing around with something that should work already.

One other place I'm thinking of looking is in the BIOS settings of my board. Right now the two serial ports are set on Auto. I tried setting one on Com 1 and the other on Com 2, but it knocked out my sound card. As far as I can see, neither of the two IRQs are being shared by anything else in the system, so a conflict couldn't be it, unless it's a conflict within Ubuntu.

As soon as I can, I'll post the logs.

---

