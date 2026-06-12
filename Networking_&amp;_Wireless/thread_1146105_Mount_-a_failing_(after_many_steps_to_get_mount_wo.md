---
title: "Mount -a failing (after many steps to get mount working)"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by pluMmet on 2009-05-02
When I type mount -a I get

wrong fs type, bad option, bad superblock on //storage/PUBLIC,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here is my fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md0 during installation
UUID=807e431d-1e23-46bf-813a-ac8507ef8d33 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=06827695-5f6a-4b9c-8a75-115b85cfcc48 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=2aead1f6-6094-4752-b117-5d7143a044b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//storage/PUBLIC  /media/ScanBay  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

It says I can't post because I have 10 images and limit is 8 but I have no images so I'm breaking this post up into 2 posts.

I'm so close to getting everything running 

Linux Noob of course.

---

### Post by pluMmet on 2009-05-02
and here is my dmesg

[    1.488014] pci_express 0000:00:04.0:pcie01: allocate port service
[    1.488065] pcieport-driver 0000:02:00.0: setting latency timer to 64
[    1.488102] pci_express 0000:02:00.0:pcie11: allocate port service
[    1.488167] pcieport-driver 0000:03:00.0: setting latency timer to 64
[    1.488193] pcieport-driver 0000:03:00.0: found MSI capability
[    1.488214] pcieport-driver 0000:03:00.0: irq 2300 for MSI/MSI-X
[    1.488233] pci_express 0000:03:00.0:pcie21: allocate port service
[    1.488288] pcieport-driver 0000:03:02.0: setting latency timer to 64
[    1.488313] pcieport-driver 0000:03:02.0: found MSI capability
[    1.488333] pcieport-driver 0000:03:02.0: irq 2299 for MSI/MSI-X
[    1.488342] pci_express 0000:03:02.0:pcie21: allocate port service
[    1.489396] aer 0000:00:02.0:pcie01: AER service couldn't init device: no _OSC support
[    1.490388] aer 0000:00:03.0:pcie01: AER service couldn't init device: no _OSC support
[    1.491358] aer 0000:00:04.0:pcie01: AER service couldn't init device: no _OSC support
[    1.491367] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.491385] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.491521] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.491523] ACPI: Power Button (FF) [PWRF]
[    1.491570] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1
[    1.491572] ACPI: Power Button (CM) [PWRB]
[    1.492068] processor ACPI_CPU:00: registered as cooling_device0
[    1.492073] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.492452] processor ACPI_CPU:01: registered as cooling_device1
[    1.492458] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.492926] processor ACPI_CPU:02: registered as cooling_device2
[    1.492931] ACPI: Processor [CPU2] (supports 8 throttling states)
[    1.493383] processor ACPI_CPU:03: registered as cooling_device3
[    1.493387] ACPI: Processor [CPU3] (supports 8 throttling states)
[    1.493766] processor ACPI_CPU:04: registered as cooling_device4
[    1.493770] ACPI: Processor [CPU4] (supports 8 throttling states)
[    1.494146] processor ACPI_CPU:05: registered as cooling_device5
[    1.494152] ACPI: Processor [CPU5] (supports 8 throttling states)
[    1.494597] processor ACPI_CPU:06: registered as cooling_device6
[    1.494601] ACPI: Processor [CPU6] (supports 8 throttling states)
[    1.494925] processor ACPI_CPU:07: registered as cooling_device7
[    1.494931] ACPI: Processor [CPU7] (supports 8 throttling states)
[    1.515616] Linux agpgart interface v0.103
[    1.515621] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.515716] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.515818] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.516094] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.516223] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.517066] brd: module loaded
[    1.517470] loop: module loaded
[    1.517538] Fixed MDIO Bus: probed
[    1.517543] PPP generic driver version 2.4.2
[    1.517603] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.517626] Driver 'sd' needs updating - please use bus_type methods
[    1.517635] Driver 'sr' needs updating - please use bus_type methods
[    1.517695] ahci 0000:00:1f.2: version 3.0
[    1.517711] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.517851] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.517853] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
[    1.517857] ahci 0000:00:1f.2: setting latency timer to 64
[    1.518364] scsi0 : ahci
[    1.518519] scsi1 : ahci
[    1.518606] scsi2 : ahci
[    1.518735] scsi3 : ahci
[    1.518850] scsi4 : ahci
[    1.518963] scsi5 : ahci

---

### Post by pluMmet on 2009-05-02
[    1.519006] ata1: SATA max UDMA/133 abar m1024@0xd3404400 port 0xd3404500 irq 19
[    1.519008] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    1.519011] ata3: SATA max UDMA/133 abar m1024@0xd3404400 port 0xd3404600 irq 19
[    1.519013] ata4: SATA max UDMA/133 abar m1024@0xd3404400 port 0xd3404680 irq 19
[    1.519016] ata5: SATA max UDMA/133 abar m1024@0xd3404400 port 0xd3404700 irq 19
[    1.519018] ata6: SATA max UDMA/133 abar m1024@0xd3404400 port 0xd3404780 irq 19
[    1.977231] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.999440] ata1.00: ATA-7: WDC WD1600YS-01SHB1, 20.06C06, max UDMA/133
[    1.999443] ata1.00: 321672960 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.000212] ata1.00: configured for UDMA/133
[    2.897411] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.909078] ata2.00: ATA-7: WDC WD1600YS-01SHB1, 20.06C06, max UDMA/133
[    2.909081] ata2.00: 321672960 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.909858] ata2.00: configured for UDMA/133
[    3.237162] ata3: SATA link down (SStatus 0 SControl 300)
[    3.564231] ata4: SATA link down (SStatus 0 SControl 300)
[    3.890412] ata5: SATA link down (SStatus 0 SControl 300)
[    4.218164] ata6: SATA link down (SStatus 0 SControl 300)
[    4.240308] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600YS-01S 20.0 PQ: 0 ANSI: 5
[    4.240429] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    4.240455] sd 0:0:0:0: [sda] Write Protect is off
[    4.240457] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.240487] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.240553] sd 0:0:0:0: [sda] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    4.240566] sd 0:0:0:0: [sda] Write Protect is off
[    4.240567] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.240590] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.240594]  sda: sda1 sda2 sda3
[    4.271016] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.271106] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.271183] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600YS-01S 20.0 PQ: 0 ANSI: 5
[    4.271261] sd 1:0:0:0: [sdb] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    4.271274] sd 1:0:0:0: [sdb] Write Protect is off
[    4.271276] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.271308] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271360] sd 1:0:0:0: [sdb] 321672960 512-byte hardware sectors: (164 GB/153 GiB)
[    4.271372] sd 1:0:0:0: [sdb] Write Protect is off
[    4.271374] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.271396] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271398]  sdb: sdb1 sdb2 sdb3
[    4.296211] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.296280] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.296361] ata_piix 0000:00:1f.1: version 2.12
[    4.296371] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.296401] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.296621] scsi6 : ata_piix
[    4.296760] scsi7 : ata_piix
[    4.297277] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    4.297279] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    4.497269] ata7.00: ATA-7: ST3750640A, 3.AAE, max UDMA/100
[    4.497272] ata7.00: 1465149168 sectors, multi 16: LBA48 
[    4.572110] ata7.00: configured for UDMA/100
[    4.583119] ata8: port disabled. ignoring.
[    4.594394] scsi 6:0:0:0: Direct-Access     ATA      ST3750640A       3.AA PQ: 0 ANSI: 5
[    4.594513] sd 6:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.594529] sd 6:0:0:0: [sdc] Write Protect is off
[    4.594531] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.594559] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.594630] sd 6:0:0:0: [sdc] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    4.594643] sd 6:0:0:0: [sdc] Write Protect is off
[    4.594644] sd 6:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.594666] sd 6:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.594680]  sdc: sdc1 sdc2 < sdc5 > sdc3 sdc4
[    4.653245] sd 6:0:0:0: [sdc] Attached SCSI disk
[    4.653306] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.654020] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.654047] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.654067] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.654070] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.654132] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.658047] ehci_hcd 0000:00:1d.7: debug port 1
[    4.658052] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.658124] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd3404000
[    4.668218] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.668329] usb usb1: configuration #1 chosen from 1 choice
[    4.668374] hub 1-0:1.0: USB hub found
[    4.668380] hub 1-0:1.0: 8 ports detected
[    4.668494] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.668518] uhci_hcd: USB Universal Host Controller Interface driver
[    4.668550] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.668556] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.668558] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.668603] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.668624] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001800
[    4.668684] usb usb2: configuration #1 chosen from 1 choice
[    4.668707] hub 2-0:1.0: USB hub found
[    4.668712] hub 2-0:1.0: 2 ports detected
[    4.668786] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.668790] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.668793] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.668834] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.668854] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    4.668913] usb usb3: configuration #1 chosen from 1 choice
[    4.668934] hub 3-0:1.0: USB hub found
[    4.668939] hub 3-0:1.0: 2 ports detected
[    4.669007] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.669011] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.669013] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.669055] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.669142] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    4.669233] usb usb4: configuration #1 chosen from 1 choice
[    4.669260] hub 4-0:1.0: USB hub found
[    4.669266] hub 4-0:1.0: 2 ports detected
[    4.669354] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.669360] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.669362] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.669415] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.669507] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    4.669595] usb usb5: configuration #1 chosen from 1 choice
[    4.669617] hub 5-0:1.0: USB hub found
[    4.669622] hub 5-0:1.0: 2 ports detected
[    4.669762] usbcore: registered new interface driver libusual
[    4.669795] usbcore: registered new interface driver usbserial
[    4.669804] USB Serial support registered for generic
[    4.669817] usbcore: registered new interface driver usbserial_generic
[    4.669818] usbserial: USB Serial Driver core
[    4.669863] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.672338] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.672344] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.684449] mice: PS/2 mouse device common for all mice
[    4.720471] rtc_cmos 00:04: RTC can wake from S4
[    4.720512] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.720586] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.720638] device-mapper: uevent: version 1.0.3
[    4.720778] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    4.721814] device-mapper: multipath: version 1.0.5 loaded
[    4.721817] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.721912] cpuidle: using governor ladder
[    4.721914] cpuidle: using governor menu
[    4.722357] TCP cubic registered
[    4.722404] NET: Registered protocol family 10
[    4.722861] lo: Disabled Privacy Extensions
[    4.723139] NET: Registered protocol family 17
[    4.723170] Bluetooth: L2CAP ver 2.11
[    4.723171] Bluetooth: L2CAP socket layer initialized
[    4.723173] Bluetooth: SCO (Voice Link) ver 0.6
[    4.723174] Bluetooth: SCO socket layer initialized
[    4.723251] Bluetooth: RFCOMM socket layer initialized
[    4.723258] Bluetooth: RFCOMM TTY layer initialized
[    4.723259] Bluetooth: RFCOMM ver 1.10
[    4.723501] p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.723505] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.723658] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.723807] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.723956] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.724115] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.724274] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.724433] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
[    4.724590] PCORE - MSR_FSB_FREQ undefined valueregistered taskstats version 1
[    4.724970]   Magic number: 9:160:120
[    4.724972] misc device-mapper: hash matches
[    4.725075] rtc_cmos 00:04: setting system clock to 2009-05-02 09:08:48 UTC (1241255328)
[    4.725077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.725078] EDD information not available.
[    4.725138] Freeing unused kernel memory: 528k freed
[    4.725397] Write protecting the kernel read-only data: 6816k
[    4.864514] md: linear personality registered for level -1
[    4.866757] md: multipath personality registered for level -4
[    4.868638] md: raid0 personality registered for level 0
[    4.871371] md: raid1 personality registered for level 1
[    4.873264] xor: automatically using best checksumming function: generic_sse
[    4.877315]    generic_sse:  9388.000 MB/sec
[    4.877316] xor: using function: generic_sse (9388.000 MB/sec)
[    4.878173] async_tx: api initialized (async)
[    4.897331] raid6: int64x1   2128 MB/s
[    4.914324] raid6: int64x2   2917 MB/s
[    4.931330] raid6: int64x4   2351 MB/s
[    4.948348] raid6: int64x8   1980 MB/s
[    4.965334] raid6: sse2x1    2921 MB/s
[    4.982341] raid6: sse2x2    6984 MB/s
[    4.999320] raid6: sse2x4    7894 MB/s
[    4.999321] raid6: using algorithm sse2x4 (7894 MB/s)
[    4.999324] md: raid6 personality registered for level 6
[    4.999325] md: raid5 personality registered for level 5
[    4.999326] md: raid4 personality registered for level 4
[    5.005163] md: raid10 personality registered for level 10
[    5.042223] Floppy drive(s): fd0 is 1.44M
[    5.050982] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    5.050985] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    5.051049] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.051058] e1000e 0000:05:00.0: setting latency timer to 64
[    5.051198] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[    5.057925] FDC 0 is a post-1991 82077
[    5.123427] 0000:05:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:30:48:7a:3a:c2
[    5.123431] 0000:05:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.123509] 0000:05:00.0: eth0: MAC: 4, PHY: 5, PBA No: ffffff-0ff
[    5.123552] e1000e 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.123561] e1000e 0000:05:00.1: setting latency timer to 64
[    5.123703] e1000e 0000:05:00.1: irq 2297 for MSI/MSI-X
[    5.213635] md: bind<sda2>
[    5.227346] 0000:05:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:30:48:7a:3a:c3
[    5.227349] 0000:05:00.1: eth1: Intel(R) PRO/1000 Network Connection
[    5.227424] 0000:05:00.1: eth1: MAC: 4, PHY: 5, PBA No: ffffff-0ff
[    5.248442] md: bind<sdb2>
[    5.250340] raid1: raid set md0 active with 2 out of 2 mirrors
[    5.252038]  md0: unknown partition table
[    5.282252] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.666643] PM: Starting manual resume from disk
[    5.666647] PM: Resume from partition 8:3
[    5.666648] PM: Checking hibernation image.
[    5.666835] PM: Resume from disk failed.
[    5.688078] kjournald starting.  Commit interval 5 seconds
[    5.688127] EXT3-fs: mounted filesystem with ordered data mode.
[    5.816864] usb 2-2: configuration #1 chosen from 1 choice
[    6.067037] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    6.207146] usb 3-1: configuration #1 chosen from 1 choice
[    6.210061] hub 3-1:1.0: USB hub found
[    6.212026] hub 3-1:1.0: 4 ports detected
[    6.424104] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    6.587151] usb 3-2: configuration #1 chosen from 1 choice
[    6.659071] usb 3-1.1: new low speed USB device using uhci_hcd and address 4
[    6.833175] usb 3-1.1: configuration #1 chosen from 1 choice
[    6.909084] usb 3-1.2: new full speed USB device using uhci_hcd and address 5
[    7.003093] usb 3-1.2: not running at top speed; connect to a high speed hub
[    7.032195] usb 3-1.2: configuration #1 chosen from 1 choice
[    7.104111] usb 3-1.3: new full speed USB device using uhci_hcd and address 6
[    7.168936] Initializing USB Mass Storage driver...
[    7.169183] scsi8 : SCSI emulation for USB Mass Storage devices
[    7.169331] usb-storage: device found at 5
[    7.169335] usb-storage: waiting for device to settle before scanning
[    7.169355] usbcore: registered new interface driver usb-storage
[    7.169358] USB Mass Storage support registered.
[    7.239176] usb 3-1.3: configuration #1 chosen from 1 choice
[   10.646839] udev: starting version 141
[   10.721853] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.165856] nvidia: module license 'NVIDIA' taints kernel.
[   11.198207] EDAC MC: Ver: 2.1.0 Apr 17 2009
[   11.212932] intel_rng: FWH not detected
[   11.271581] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x263E
[   11.271619] usbcore: registered new interface driver usblp
[   11.365055] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   11.377101] usbcore: registered new interface driver hiddev
[   11.387124] EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
[   11.387156] EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
[   11.400903] parport_pc 00:0c: reported by Plug and Play ACPI
[   11.401007] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   11.412463] iTCO_vendor_support: vendor-support=0
[   11.421843] nvidia 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.421849] nvidia 0000:07:00.0: setting latency timer to 64
[   11.422178] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   11.423866] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.428888] iTCO_wdt: Found a 631xESB/632xESB TCO device (Version=2, TCOBASE=0x1060)
[   11.428984] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.430816] ppdev: user-space parallel port driver
[   11.487391] input: 3Dconnexion Spaceball 5000 USB as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[   11.493410] generic-usb 0003:046D:C621.0001: input,hidraw0: USB HID v1.10 Multi-Axis Controller [3Dconnexion Spaceball 5000 USB] on usb-0000:00:1d.0-2/input0
[   11.527868] input: ATEN CS-1734A V3.0.291 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
[   11.542336] generic-usb 0003:0557:2213.0002: input,hidraw1: USB HID v1.00 Keyboard [ATEN CS-1734A V3.0.291] on usb-0000:00:1d.1-1.1/input0
[   11.569799] input: ATEN CS-1734A V3.0.291 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.1/3-1.1:1.1/input/input6
[   11.586395] generic-usb 0003:0557:2213.0003: input,hidraw2: USB HID v1.00 Mouse [ATEN CS-1734A V3.0.291] on usb-0000:00:1d.1-1.1/input1
[   11.589815] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/input/input7
[   11.604565] generic-usb 0003:046D:C51A.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input0
[   11.611753] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.1/input/input8
[   11.621940] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.622030] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.625624] generic-usb 0003:046D:C51A.0005: input,hiddev96,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input1
[   11.625676] usbcore: registered new interface driver usbhid
[   11.625678] usbhid: v2.6:USB HID core driver
[   11.631902] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.861447] lp0: using parport0 (interrupt-driven).
[   11.974391] Adding 3951980k swap on /dev/sda3.  Priority:-1 extents:1 across:3951980k
[   12.002580] Adding 3951980k swap on /dev/sdb3.  Priority:-2 extents:1 across:3951980k
[   12.169603] usb-storage: device scan complete
[   12.175561] scsi 8:0:0:0: Direct-Access     Canon    MP Memory Card   0100 PQ: 0 ANSI: 2
[   12.187547] sd 8:0:0:0: [sdd] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[   12.212544] sd 8:0:0:0: [sdd] Write Protect is off
[   12.212547] sd 8:0:0:0: [sdd] Mode Sense: 3f 00 00 08
[   12.212549] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[   12.236548] sd 8:0:0:0: [sdd] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[   12.262548] sd 8:0:0:0: [sdd] Write Protect is off
[   12.262551] sd 8:0:0:0: [sdd] Mode Sense: 3f 00 00 08
[   12.262552] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[   12.262558]  sdd: sdd1
[   12.283356] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[   12.284336] sd 8:0:0:0: Attached scsi generic sg3 type 0
[   12.591448] EXT3 FS on md0, internal journal
[   13.896632] type=1505 audit(1241269737.671:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2591
[   13.928138] type=1505 audit(1241269737.702:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2599
[   13.928260] type=1505 audit(1241269737.702:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2599
[   13.928302] type=1505 audit(1241269737.702:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2599
[   13.928333] type=1505 audit(1241269737.703:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2599
[   14.012921] type=1505 audit(1241269737.787:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2604
[   14.013062] type=1505 audit(1241269737.787:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2604
[   14.034631] type=1505 audit(1241269737.809:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2608
[   15.139693] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[   15.191212] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[   15.194159] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.257927] e1000e 0000:05:00.1: irq 2297 for MSI/MSI-X
[   15.308532] e1000e 0000:05:00.1: irq 2297 for MSI/MSI-X
[   15.311373] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.057314] 0000:05:00.1: eth1: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   17.057317] 0000:05:00.1: eth1: 10/100 speed: disabling TSO
[   17.059845] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   17.914187] 0000:05:00.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   17.916692] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.830786] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.830789] vboxdrv: Successfully done.
[   19.830790] vboxdrv: Found 8 processor cores.
[   19.831186] VBoxDrv: dbg - g_abExecMemory=ffffffffa0acef60
[   19.831428] vboxdrv: fAsync=0 offMin=0x6c8 offMax=0xe7f0
[   19.832109] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.832111] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   20.038714] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c6ec60
[   21.603417] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.603419] Bluetooth: BNEP filters: protocol multicast
[   21.616656] Bridge firewalling registered
[   21.777095] CIFS: Unknown mount option codepage
[   21.777099] CIFS: Unknown mount option unicode
[   21.777101]  CIFS VFS: No username specified
[   21.777104]  CIFS VFS: cifs_mount failed w/return code = -22
[   23.476629] ppdev0: registered pardevice
[   23.518363] ppdev0: unregistered pardevice
[   27.221157] eth1: no IPv6 routers present
[   28.255030] eth0: no IPv6 routers present
[   30.715720] CIFS: Unknown mount option codepage
[   30.715723] CIFS: Unknown mount option unicode
[   30.715726]  CIFS VFS: No username specified
[   30.715729]  CIFS VFS: cifs_mount failed w/return code = -22
[  371.954566] usb 3-1.2: USB disconnect, address 5
[  371.954811] usblp0: removed
[  372.071523] usb 3-1.3: USB disconnect, address 6
[  420.114607] usb 3-1.2: new full speed USB device using uhci_hcd and address 7
[  420.207566] usb 3-1.2: not running at top speed; connect to a high speed hub
[  420.232008] usb 3-1.2: configuration #1 chosen from 1 choice
[  420.238617] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x263E
[  420.246099] scsi9 : SCSI emulation for USB Mass Storage devices
[  420.246241] usb-storage: device found at 7
[  420.246245] usb-storage: waiting for device to settle before scanning
[  420.427476] usb 3-1.3: new full speed USB device using uhci_hcd and address 8
[  420.559856] usb 3-1.3: configuration #1 chosen from 1 choice
[  420.567861] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.0/input/input9
[  420.581478] generic-usb 0003:046D:C51A.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input0
[  420.587522] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1.3/3-1.3:1.1/input/input10
[  420.600309] generic-usb 0003:046D:C51A.0007: input,hiddev96,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1.3/input1
[  421.616866] ppdev0: registered pardevice
[  421.657665] ppdev0: unregistered pardevice
[  425.247596] usb-storage: device scan complete
[  425.253505] scsi 9:0:0:0: Direct-Access     Canon    MP Memory Card   0100 PQ: 0 ANSI: 2
[  425.265500] sd 9:0:0:0: [sdd] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[  425.288951] sd 9:0:0:0: [sdd] Write Protect is off
[  425.288956] sd 9:0:0:0: [sdd] Mode Sense: 3f 00 00 08
[  425.288959] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  425.316459] sd 9:0:0:0: [sdd] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[  425.339460] sd 9:0:0:0: [sdd] Write Protect is off
[  425.339463] sd 9:0:0:0: [sdd] Mode Sense: 3f 00 00 08
[  425.339465] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[  425.339468]  sdd: sdd1
[  425.360677] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[  425.360770] sd 9:0:0:0: Attached scsi generic sg3 type 0
[  843.843963] CIFS: Unknown mount option codepage
[  843.843966] CIFS: Unknown mount option unicode
[  843.843968]  CIFS VFS: No username specified
[  843.843970]  CIFS VFS: cifs_mount failed w/return code = -22

---

### Post by pluMmet on 2009-05-02
I installed smbfs

I have a new error:

~$ sudo mount -a
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


and my smbtree is not what I expected:
MAXMANIA
	\\WORKSTATION    		workstation server (Samba, Ubuntu)
		\\WORKSTATION\print$         	Printer Drivers
		\\WORKSTATION\IPC$           	IPC Service (workstation server (Samba, Ubuntu))
	\\STORAGE-0F05 

to windows my share drive is //storage/PUBLIC which is not in my smbtree but \\STORAGE-0F05 is (what ever that is)

This is an NAS btw

---

### Post by pluMmet on 2009-05-03
Well finally got it :guitar:

fstab addition is:
//STORAGE-0F05/PUBLIC /media/ScanBay/ cifs nounix,uid=eric,gid=eric,file_mode=0777,dir_mode=0777 0 0


peace.

---

