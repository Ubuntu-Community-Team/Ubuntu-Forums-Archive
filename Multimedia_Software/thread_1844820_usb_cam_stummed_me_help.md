---
title: "usb cam stummed me help"
date: 2011-09-15
forum: Multimedia Software
---

### Post by thatstrangeguy on 2011-09-15
**Hello long time user but i haven't posted really because i have figured out a lot from others post i have two questions one ill post here and the other in another category but any way i bought my usb envision web cam a while ago ie three years or so. i haven't had the need to use it till now. now i installed skype and cheeze With cheeze the program will start up and ill see my cam plain as day for under a sec. during that second you can see that my web can is functioning but the program shuts down instantly no messages just dies out once the vid just starts up. and with skype it offers me to vid chat so it knows there is a web cam connected but i click on it i receive but not send video. i believe that the problem is in the driver for the cam because of the fact that it goes between two different programs is there any advise out there**

---

### Post by thatstrangeguy on 2011-09-15
no one knows what is happening here

---

### Post by no2498 on 2011-09-16
open a terminal copy/paste
dmesg
click enter
that should find the cam load a grabber and say what driver it loaded
now type lsusb click enter
that should give a number and name of the cam
this is for 32 bit only
in a terminal copy/past
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
click enter
did cheese stay running
if not unplug the cam open cheese look in help FAQ'S
you may try this for skype also
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
skype is a 32 bit program

---

### Post by no2498 on 2011-09-16
i just started seeing that skype or some web cam program looks to be set to auto start at a reboot
look in your system startup programs turn them off and do a restart

---

### Post by thatstrangeguy on 2011-09-16
[HTML][    0.836553] pci_bus 0000:06: resource 0 [io  0xe000-0xefff]
[    0.836555] pci_bus 0000:06: resource 1 [mem 0xfdf00000-0xfdffffff]
[    0.836557] pci_bus 0000:06: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.836597] NET: Registered protocol family 2
[    0.836834] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.838557] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.842829] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.843344] TCP: Hash tables configured (established 524288 bind 65536)
[    0.843347] TCP reno registered
[    0.843363] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.843445] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.843632] NET: Registered protocol family 1
[    0.880144] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.880249] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.880500] pci 0000:02:00.0: Boot video device
[    0.880510] PCI: CLS 64 bytes, default 64
[    0.881930] PCI-DMA: Disabling AGP.
[    0.882035] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.882037] PCI-DMA: using GART IOMMU.
[    0.882041] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.886216] audit: initializing netlink socket (disabled)
[    0.886235] type=2000 audit(1316199786.880:1): initialized
[    0.898259] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.899822] VFS: Disk quotas dquot_6.5.2
[    0.899871] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.900471] fuse init (API version 7.16)
[    0.900543] msgmni has been set to 11920
[    0.900813] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.900846] io scheduler noop registered
[    0.900848] io scheduler deadline registered
[    0.900881] io scheduler cfq registered (default)
[    0.901661] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.901683] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.901850] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.010024] ACPI: Power Button [PWRB]
[    1.010076] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.010079] ACPI: Power Button [PWRF]
[    1.010250] ACPI: acpi_idle registered with cpuidle
[    1.012529] thermal LNXTHERM:00: registered as thermal_zone0
[    1.012531] ACPI: Thermal Zone [THRM] (30 C)
[    1.012575] ERST: Table is not found!
[    1.012676] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.033213] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.033371] Freeing initrd memory: 19600k freed
[    1.210737] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.211112] Linux agpgart interface v0.103
[    1.212061] brd: module loaded
[    1.212492] loop: module loaded
[    1.212569] i2c-core: driver [adp5520] using legacy suspend method
[    1.212571] i2c-core: driver [adp5520] using legacy resume method
[    1.212763] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.213145] Fixed MDIO Bus: probed
[    1.213174] PPP generic driver version 2.4.2
[    1.213244] tun: Universal TUN/TAP device driver, 1.6
[    1.213246] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.213332] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.213532] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[    1.213550] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 23 (level, low) -> IRQ 23
[    1.213573] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.213576] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.213624] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.260050] ehci_hcd 0000:00:02.1: debug port 1
[    1.260057] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.260078] ehci_hcd 0000:00:02.1: irq 23, io mem 0xf9f7ec00
[    1.280014] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.280117] hub 1-0:1.0: USB hub found
[    1.280122] hub 1-0:1.0: 6 ports detected
[    1.280371] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 22
[    1.280382] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 22 (level, low) -> IRQ 22
[    1.280391] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.280394] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.280429] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.280472] ehci_hcd 0000:00:04.1: debug port 1
[    1.280480] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.280498] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf9f7e800
[    1.300015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.300100] hub 2-0:1.0: USB hub found
[    1.300103] hub 2-0:1.0: 6 ports detected
[    1.300175] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.300353] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    1.300363] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    1.300373] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.300376] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.300413] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.300457] ohci_hcd 0000:00:02.0: irq 21, io mem 0xf9f7f000
[    1.362090] hub 3-0:1.0: USB hub found
[    1.362094] hub 3-0:1.0: 6 ports detected
[    1.362327] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 20
[    1.362337] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 20 (level, low) -> IRQ 20
[    1.362346] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.362349] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.362380] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.362422] ohci_hcd 0000:00:04.0: irq 20, io mem 0xf9f7d000
[    1.422090] hub 4-0:1.0: USB hub found
[    1.422095] hub 4-0:1.0: 6 ports detected
[    1.422166] uhci_hcd: USB Universal Host Controller Interface driver
[    1.422255] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.425358] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.425369] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.425515] mousedev: PS/2 mouse device common for all mice
[    1.425627] rtc_cmos 00:07: RTC can wake from S4
[    1.510052] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.510105] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.510197] device-mapper: uevent: version 1.0.3
[    1.510260] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.510326] device-mapper: multipath: version 1.2.0 loaded
[    1.510329] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.510443] cpuidle: using governor ladder
[    1.510445] cpuidle: using governor menu
[    1.510655] TCP cubic registered
[    1.510758] NET: Registered protocol family 10
[    1.511176] NET: Registered protocol family 17
[    1.511190] Registering the dns_resolver key type
[    1.511229] powernow-k8: Found 1 AMD Phenom(tm) 9750 Quad-Core Processor (4 cpu cores) (version 2.20.00)
[    1.511262] powernow-k8:    0 : pstate 0 (2400 MHz)
[    1.511264] powernow-k8:    1 : pstate 1 (1200 MHz)
[    1.511573] PM: Hibernation image not present or could not be loaded.
[    1.511584] registered taskstats version 1
[    1.512001]   Magic number: 11:748:91
[    1.512141] rtc_cmos 00:07: setting system clock to 2011-09-16 19:03:08 UTC (1316199788)
[    1.512144] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.512145] EDD information not available.
[    1.513713] Freeing unused kernel memory: 956k freed
[    1.514049] Write protecting the kernel read-only data: 10240k
[    1.514770] Freeing unused kernel memory: 184k freed
[    1.519401] Freeing unused kernel memory: 1440k freed
[    1.536607] <30>udev[112]: starting version 167
[    1.581757] pata_amd 0000:00:06.0: version 0.4.1
[    1.581799] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.582704] scsi0 : pata_amd
[    1.583681] scsi1 : pata_amd
[    1.584602] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.584604] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.586055] ahci 0000:00:09.0: version 3.0
[    1.586234] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.586239] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.586293] ahci 0000:00:09.0: irq 40 for MSI/MSI-X
[    1.586299] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.586365] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.586368] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio boh 
[    1.586372] ahci 0000:00:09.0: setting latency timer to 64
[    1.587215] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.587246] r8169 0000:06:00.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    1.587268] r8169 0000:06:00.0: setting latency timer to 64
[    1.587307] r8169 0000:06:00.0: irq 41 for MSI/MSI-X
[    1.587712] r8169 0000:06:00.0: eth0: RTL8168c/8111c at 0xffffc9001178c000, 00:25:11:3e:70:b2, XID 1c4000c0 IRQ 41
[    1.587748] scsi2 : ahci
[    1.587845] scsi3 : ahci
[    1.587960] scsi4 : ahci
[    1.588207] scsi5 : ahci
[    1.588280] scsi6 : ahci
[    1.588359] scsi7 : ahci
[    1.588518] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 40
[    1.588521] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 40
[    1.588523] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 40
[    1.588526] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 40
[    1.588528] ata7: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 40
[    1.588531] ata8: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 40
[    1.720035] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.880038] Refined TSC clocksource calibration: 2400.000 MHz.
[    1.880045] Switching to clocksource tsc
[    1.930012] ata6: SATA link down (SStatus 0 SControl 300)
[    1.930031] ata7: SATA link down (SStatus 0 SControl 300)
[    1.930046] ata8: SATA link down (SStatus 0 SControl 300)
[    1.930062] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.930082] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.930099] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.930939] ata3.00: ATA-8: WDC WD7500AADS-00M2B0, 01.00A01, max UDMA/133
[    1.930942] ata3.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.931842] ata3.00: configured for UDMA/133
[    1.944992] ata4.00: ATA-8: WDC WD4000AAJS-00YFA0, 12.01C02, max UDMA/133
[    1.944994] ata4.00: 781422768 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.945709] ata4.00: configured for UDMA/133
[    1.970519] ata5.00: ATA-7: ST3160815AS, 3.AAD, max UDMA/133
[    1.970521] ata5.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.028827] ata5.00: configured for UDMA/133
[    2.040396] ata1.00: ATAPI: HL-DT-STDVD-RAM GSA-H54L, 1.00, max UDMA/66
[    2.040402] ata1.01: ATAPI: ATAPI   DVD D  DH16D2P, HP57, max UDMA/33
[    2.040409] ata1: nv_mode_filter: 0x1f39f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x15)
[    2.040414] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x15)
[    2.080314] ata1.00: configured for UDMA/33
[    2.140227] ata1.01: configured for UDMA/33
[    2.143226] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H54L 1.00 PQ: 0 ANSI: 5
[    2.145815] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.145818] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.145934] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.146012] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.148477] scsi 0:0:1:0: CD-ROM            ATAPI    DVD D  DH16D2P   HP57 PQ: 0 ANSI: 5
[    2.149847] sr1: scsi3-mmc drive: 47x/47x cd/rw xa/form2 cdda tray
[    2.149928] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    2.149987] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.150126] ata2: port disabled. ignoring.
[    2.150257] scsi 2:0:0:0: Direct-Access     ATA      WDC WD7500AADS-0 01.0 PQ: 0 ANSI: 5
[    2.150401] sd 2:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.150432] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.150558] scsi 3:0:0:0: Direct-Access     ATA      WDC WD4000AAJS-0 12.0 PQ: 0 ANSI: 5
[    2.150562] sd 2:0:0:0: [sda] Write Protect is off
[    2.150565] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.150602] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.150734] sd 3:0:0:0: [sdb] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    2.150777] sd 3:0:0:0: [sdb] Write Protect is off
[    2.150779] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.150783] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.150799] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.150910] scsi 4:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[    2.151038] sd 4:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.151053] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    2.151111] sd 4:0:0:0: [sdc] Write Protect is off
[    2.151114] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.151151] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.157148]  sdb: sdb1 sdb2
[    2.157392] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.179040]  sdc: sdc1 sdc2 < sdc5 > sdc3
[    2.179320] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.450008] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.628723]  sda: sda1
[    2.628924] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.955183] generic-usb 0003:051D:0002.0001: hiddev0,hidraw0: USB HID v1.10 Device [APC Back-UPS ES 550 FW:843.K2 .D USB FW:K2 ] on usb-0000:00:04.0-1/input0
[    2.955207] usbcore: registered new interface driver usbhid
[    2.955209] usbhid: USB HID core driver
[    3.040035] usb 4-4: new low speed USB device using ohci_hcd and address 3
[    3.180571] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[    3.310098] input: 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/input/input2
[    3.310184] generic-usb 0003:04F3:01A4.0002: input,hidraw1: USB HID v1.10 Keyboard [2.4G RF Keyboard & Mouse] on usb-0000:00:04.0-4/input0
[    3.320416] input: 2.4G RF Keyboard & Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.1/input/input3
[    3.320516] generic-usb 0003:04F3:01A4.0003: input,hiddev0,hidraw2: USB HID v1.10 Mouse [2.4G RF Keyboard & Mouse] on usb-0000:00:04.0-4/input1
[    3.660014] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    4.239162] generic-usb 0003:043D:0140.0004: hiddev0,hidraw3: USB HID v1.00 Device [Lexmark  Z2400 Series] on usb-0000:00:02.0-1/input1
[    4.570010] usb 3-4: new full speed USB device using ohci_hcd and address 3
[    4.808052] hub 3-4:1.0: USB hub found
[    4.811026] hub 3-4:1.0: 3 ports detected
[    5.111029] usb 3-4.1: new full speed USB device using ohci_hcd and address 4
[    5.250099] input: HID 0a5c:4502 as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4.1/3-4.1:1.0/input/input4
[    5.250202] generic-usb 0003:0A5C:4502.0005: input,hidraw4: USB HID v1.11 Keyboard [HID 0a5c:4502] on usb-0000:00:02.0-4.1/input0
[    5.331027] usb 3-4.2: new full speed USB device using ohci_hcd and address 5
[    5.466235] input: HID 0a5c:4503 as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4.2/3-4.2:1.0/input/input5
[    5.466318] generic-usb 0003:0A5C:4503.0006: input,hidraw5: USB HID v1.11 Mouse [HID 0a5c:4503] on usb-0000:00:02.0-4.2/input0
[    5.551025] usb 3-4.3: new full speed USB device using ohci_hcd and address 6
[   10.906551] <30>udev[410]: starting version 167
[   10.922567] lp: driver loaded but no devices found
[   10.995558] i2c i2c-0: nForce2 SMBus adapter at 0x2d00
[   10.995564] ACPI: resource nForce2_smbus [io  0x2e00-0x2e3f] conflicts with ACPI region SM00 [io 0x2e00-0x2e3f]
[   10.995566] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.022103] Linux video capture interface: v2.00
[   11.026277] Bluetooth: Core ver 2.15
[   11.026310] NET: Registered protocol family 31
[   11.026312] Bluetooth: HCI device and connection manager initialized
[   11.026315] Bluetooth: HCI socket layer initialized
[   11.028321] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   11.030769] gspca: v2.12.0 registered
[   11.032193] gspca: probing 0c45:6242
[   11.040800] usbcore: registered new interface driver btusb
[   11.044828] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.054845] sn9c20x: MT9M111 sensor detected
[   11.054945] input: sn9c20x as /devices/pci0000:00/0000:00:02.1/usb1/1-2/input/input6
[   11.055126] gspca: video0 created
[   11.055177] usbcore: registered new interface driver sn9c20x
[   11.067344] MCE: In-kernel MCE decoding enabled.
[   11.071196] nvidia: module license 'NVIDIA' taints kernel.
[   11.071200] Disabling lock debugging due to kernel taint
[   11.074327] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[   11.074434] type=1400 audit(1316214198.054:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=617 comm="apparmor_parser"
[   11.074774] type=1400 audit(1316214198.054:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=617 comm="apparmor_parser"
[   11.074989] type=1400 audit(1316214198.054:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=617 comm="apparmor_parser"
[   11.095369] EDAC MC: Ver: 2.1.0 Jul 29 2011
[   11.151103] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   11.151109] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   11.151285] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   11.151290] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   11.151293] hda_intel: Disable MSI for Nvidia chipset
[   11.151335] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.152144] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0140
[   11.152813] usbcore: registered new interface driver usblp
[   11.162216] EDAC amd64_edac: v3.3.0
[   11.464339] nvidia 0000:02:00.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[   11.464352] nvidia 0000:02:00.0: setting latency timer to 64
[   11.464357] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.464381] EXT4-fs (sdc3): re-mounted. Opts: errors=remount-ro
[   11.464586] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   14.530100] input: HDA NVidia Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input7
[   14.530215] input: HDA NVidia Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
[   14.530286] input: HDA NVidia Mic at Sep Front Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   14.530343] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
[   14.530406] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
[   14.530467] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
[   14.530523] input: HDA NVidia Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
[   14.530587] input: HDA NVidia HP Out at Sep Front Jack as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
[   14.530972] EDAC amd64: DRAM ECC disabled.
[   14.530981] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.530982]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.530983]  (Note that use of the override may cause unknown side effects.)
[   14.531016] HDA Intel 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[   16.061138] vesafb: framebuffer at 0xfb000000, mapped to 0xffffc90014480000, using 5120k, total 5120k
[   16.061142] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   16.061144] vesafb: scrolling: redraw
[   16.061147] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.061378] Console: switching to colour frame buffer device 160x64
[   16.077399] fb0: VESA VGA frame buffer device
[   16.144023] Intel AES-NI instructions are not detected.
[   16.181063] padlock_aes: VIA PadLock not detected.
[   16.236206] padlock_sha: VIA PadLock Hash Engine not detected.
[   16.395347] Adding 7909372k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:7909372k 
[   32.333889] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   32.459036] type=1400 audit(1316214219.434:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1044 comm="apparmor_parser"
[   32.459393] type=1400 audit(1316214219.434:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1044 comm="apparmor_parser"
[   32.459614] type=1400 audit(1316214219.434:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1044 comm="apparmor_parser"
[   32.459801] type=1400 audit(1316214219.434:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1043 comm="apparmor_parser"
[   32.466535] type=1400 audit(1316214219.444:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1054 comm="apparmor_parser"
[   32.468124] type=1400 audit(1316214219.444:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1053 comm="apparmor_parser"
[   32.468560] type=1400 audit(1316214219.444:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1053 comm="apparmor_parser"
[   32.470308] type=1400 audit(1316214219.454:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1045 comm="apparmor_parser"
[   32.475975] type=1400 audit(1316214219.454:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1045 comm="apparmor_parser"
[   32.478655] type=1400 audit(1316214219.454:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1045 comm="apparmor_parser"
[   32.510814] ppdev: user-space parallel port driver
[   32.540566] r8169 0000:06:00.0: eth0: link down
[   32.541554] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.735774] Bluetooth: L2CAP ver 2.15
[   32.735778] Bluetooth: L2CAP socket layer initialized
[   32.742636] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.742639] Bluetooth: BNEP filters: protocol multicast
[   32.746486] Bluetooth: SCO (Voice Link) ver 0.6
[   32.746489] Bluetooth: SCO socket layer initialized
[   32.786980] Bluetooth: RFCOMM TTY layer initialized
[   32.786987] Bluetooth: RFCOMM socket layer initialized
[   32.786989] Bluetooth: RFCOMM ver 1.11
[   34.939680] r8169 0000:06:00.0: eth0: link up
[   34.940786] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.273731] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   35.511658] EXT4-fs (sdc3): re-mounted. Opts: errors=remount-ro,commit=0
[   35.515032] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   38.097830] EXT4-fs (sdc3): re-mounted. Opts: errors=remount-ro,commit=0
[   38.100674] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   41.565541] hda-intel: Invalid position buffer, using LPIB read method instead.
[   41.574289] hda-intel: Invalid position buffer, using LPIB read method instead.
[   44.779132] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[   45.890007] eth0: no IPv6 routers present
[   67.533234] ISO 9660 Extensions: Microsoft Joliet Level 3
[   67.552488] ISOFS: changing to secondary root[/HTML]
[SIZE=2]This is what i got with the first code the dmes[/SIZE]

[HTML]Bus 004 Device 003: ID 04f3:01a4 Elan Microelectronics Corp. 
Bus 004 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 002: ID 043d:0140 Lexmark International, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6242 Microdia PC Camera (SN9C201 + MI1310)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jon@jon-GeForce-8000-series:~$ lsusb
Bus 004 Device 003: ID 04f3:01a4 Elan Microelectronics Corp. 
Bus 004 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 002: ID 043d:0140 Lexmark International, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6242 Microdia PC Camera (SN9C201 + MI1310)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/HTML][SIZE=2]Ill try and do the unpluging atemp right now thank you for your time

[/SIZE]

---

### Post by thatstrangeguy on 2011-09-16
[SIZE=2]Also when i ran cheeze got this

[/SIZE][HTML]jon@jon-GeForce-8000-series:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
Segmentation fault
jon@jon-GeForce-8000-series:~$ [/HTML][SIZE=2]

I highlighted the fault not sure what it means
[/SIZE]

---

### Post by thatstrangeguy on 2011-09-16
just started seeing that skype or some web cam program looks to be set to auto start at a reboot
look in your system startup programs turn them off and do a restart


like wich one of these

---

### Post by no2498 on 2011-09-17
we can only run 1 program at a time
so no cam program's should be in the startup
this makes it look like its running and will not let any program use the cam

---

