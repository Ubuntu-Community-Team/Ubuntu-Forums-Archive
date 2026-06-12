---
title: "Wired connection gone after 9.04 upgrade"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by nierdoi_sseaurou on 2009-04-30
Last night I upgraded to Jaunty. Since then the wired connection is dead. I have had no problems whatsoever of this kind before last night. I have searched all over the internet for assistance but I haven't found a solution and help would be greatly appreciated. Just tell me what Terminal output you need and I'll post it asap.

---

### Post by sir_nasty on 2009-04-30
run 'dmesg' and post the output, also what brand/model is your adapter/computer?

---

### Post by nierdoi_sseaurou on 2009-04-30
Computer is a Dell Inspiron 5100.
Network adapter is an Intel 82801G (I think).

dmesg output:

[    1.320980] system 00:07: ioport range 0x2e00-0x2efe has been reserved 
[    1.320983] system 00:07: ioport range 0x2f00-0x2ffe has been reserved 
[    1.320987] system 00:07: ioport range 0x5000-0x50fe has been reserved 
[    1.320990] system 00:07: ioport range 0x5100-0x51fe has been reserved 
[    1.320993] system 00:07: ioport range 0x5200-0x52fe has been reserved 
[    1.320997] system 00:07: ioport range 0x5300-0x53fe has been reserved 
[    1.321000] system 00:07: ioport range 0x5400-0x54fe has been reserved 
[    1.321004] system 00:07: ioport range 0x5500-0x55fe has been reserved 
[    1.321007] system 00:07: ioport range 0x5600-0x56fe has been reserved 
[    1.321010] system 00:07: ioport range 0x5700-0x57fe has been reserved 
[    1.321014] system 00:07: ioport range 0x5800-0x58fe has been reserved 
[    1.321017] system 00:07: ioport range 0x5900-0x59fe has been reserved 
[    1.321021] system 00:07: ioport range 0x5a00-0x5afe has been reserved 
[    1.321024] system 00:07: ioport range 0x5b00-0x5bfe has been reserved 
[    1.321028] system 00:07: ioport range 0x5c00-0x5cfe has been reserved 
[    1.321031] system 00:07: ioport range 0x5d00-0x5dfe has been reserved 
[    1.321035] system 00:07: ioport range 0x5e00-0x5efe has been reserved 
[    1.321039] system 00:07: ioport range 0x5f00-0x5ffe has been reserved 
[    1.321042] system 00:07: ioport range 0x6000-0x60fe has been reserved 
[    1.321046] system 00:07: ioport range 0x6100-0x61fe has been reserved 
[    1.321049] system 00:07: ioport range 0x6200-0x62fe has been reserved 
[    1.321053] system 00:07: ioport range 0x6300-0x63fe has been reserved 
[    1.321056] system 00:07: ioport range 0x6400-0x64fe has been reserved 
[    1.321060] system 00:07: ioport range 0x6500-0x65fe has been reserved 
[    1.321063] system 00:07: ioport range 0x6600-0x66fe has been reserved 
[    1.321067] system 00:07: ioport range 0x6700-0x67fe has been reserved 
[    1.321070] system 00:07: ioport range 0x6800-0x68fe has been reserved 
[    1.321074] system 00:07: ioport range 0x6900-0x69fe has been reserved 
[    1.321077] system 00:07: ioport range 0x6a00-0x6afe has been reserved 
[    1.321081] system 00:07: ioport range 0x6b00-0x6bfe has been reserved 
[    1.321084] system 00:07: ioport range 0x6c00-0x6cfe has been reserved 
[    1.321088] system 00:07: ioport range 0x6d00-0x6dfe has been reserved 
[    1.321091] system 00:07: ioport range 0x6e00-0x6efe has been reserved 
[    1.321095] system 00:07: ioport range 0x6f00-0x6ffe has been reserved 
[    1.321098] system 00:07: ioport range 0xa000-0xa0fe has been reserved 
[    1.321102] system 00:07: ioport range 0xa100-0xa1fe has been reserved 
[    1.321106] system 00:07: ioport range 0xa200-0xa2fe has been reserved 
[    1.321110] system 00:07: ioport range 0xa300-0xa3fe has been reserved 
[    1.321113] system 00:07: ioport range 0xa400-0xa4fe has been reserved 
[    1.321117] system 00:07: ioport range 0xa500-0xa5fe has been reserved 
[    1.321121] system 00:07: ioport range 0xa600-0xa6fe has been reserved 
[    1.321125] system 00:07: ioport range 0xa700-0xa7fe has been reserved 
[    1.321129] system 00:07: ioport range 0xa800-0xa8fe has been reserved 
[    1.321132] system 00:07: ioport range 0xa900-0xa9fe has been reserved 
[    1.321136] system 00:07: ioport range 0xaa00-0xaafe has been reserved 
[    1.321140] system 00:07: ioport range 0xab00-0xabfe has been reserved 
[    1.321144] system 00:07: ioport range 0xac00-0xacfe has been reserved 
[    1.321148] system 00:07: ioport range 0xad00-0xadfe has been reserved 
[    1.321152] system 00:07: ioport range 0xae00-0xaefe has been reserved 
[    1.321156] system 00:07: ioport range 0xaf00-0xaffe has been reserved 
[    1.321160] system 00:07: iomem range 0xf0000000-0xf3ffffff has been reserved 
[    1.321163] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved 
[    1.355935] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    1.355938] pci 0000:00:01.0:   IO window: disabled 
[    1.355944] pci 0000:00:01.0:   MEM window: 0xefd00000-0xefdfffff 
[    1.355948] pci 0000:00:01.0:   PREFETCH window: disabled 
[    1.355954] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02 
[    1.355957] pci 0000:00:1c.0:   IO window: disabled 
[    1.355963] pci 0000:00:1c.0:   MEM window: 0xefc00000-0xefcfffff 
[    1.355968] pci 0000:00:1c.0:   PREFETCH window: disabled 
[    1.355975] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03 
[    1.355979] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff 
[    1.355985] pci 0000:00:1e.0:   MEM window: 0xefb00000-0xefbfffff 
[    1.355990] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    1.356021] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.356027] pci 0000:00:01.0: setting latency timer to 64 
[    1.356037] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.356042] pci 0000:00:1c.0: setting latency timer to 64 
[    1.356051] pci 0000:00:1e.0: setting latency timer to 64 
[    1.356056] bus: 00 index 0 io port: [0x00-0xffff] 
[    1.356059] bus: 00 index 1 mmio: [0x000000-0xffffffff] 
[    1.356062] bus: 01 index 0 mmio: [0x0-0x0] 
[    1.356064] bus: 01 index 1 mmio: [0xefd00000-0xefdfffff] 
[    1.356067] bus: 01 index 2 mmio: [0x0-0x0] 
[    1.356069] bus: 01 index 3 mmio: [0x0-0x0] 
[    1.356072] bus: 02 index 0 mmio: [0x0-0x0] 
[    1.356074] bus: 02 index 1 mmio: [0xefc00000-0xefcfffff] 
[    1.356077] bus: 02 index 2 mmio: [0x0-0x0] 
[    1.356079] bus: 02 index 3 mmio: [0x0-0x0] 
[    1.356082] bus: 03 index 0 io port: [0xd000-0xdfff] 
[    1.356084] bus: 03 index 1 mmio: [0xefb00000-0xefbfffff] 
[    1.356087] bus: 03 index 2 mmio: [0x0-0x0] 
[    1.356089] bus: 03 index 3 io port: [0x00-0xffff] 
[    1.356092] bus: 03 index 4 mmio: [0x000000-0xffffffff] 
[    1.356104] NET: Registered protocol family 2 
[    1.368088] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[    1.368390] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
[    1.368448] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[    1.368505] TCP: Hash tables configured (established 16384 bind 16384) 
[    1.368509] TCP reno registered 
[    1.376096] NET: Registered protocol family 1 
[    1.376267] checking if image is initramfs... it is 
[    2.008623] Freeing initrd memory: 7358k freed 
[    2.008670] Simple Boot Flag at 0x7a set to 0x1 
[    2.008707] cpufreq: No nForce2 chipset. 
[    2.008896] audit: initializing netlink socket (disabled) 
[    2.008917] type=2000 audit(1241109737.008:1): initialized 
[    2.017522] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    2.019201] VFS: Disk quotas dquot_6.5.1 
[    2.019289] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    2.020166] fuse init (API version 7.10) 
[    2.020275] msgmni has been set to 975 
[    2.020725] alg: No test for stdrng (krng) 
[    2.020746] io scheduler noop registered 
[    2.020751] io scheduler anticipatory registered 
[    2.020755] io scheduler deadline registered 
[    2.020783] io scheduler cfq registered (default) 
[    2.020803] pci 0000:00:02.0: Boot video device 
[    2.020926] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling 
[    2.044915] pcieport-driver 0000:00:01.0: setting latency timer to 64 
[    2.044960] pcieport-driver 0000:00:01.0: found MSI capability 
[    2.044992] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X 
[    2.045006] pci_express 0000:00:01.0:pcie00: allocate port service 
[    2.045076] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[    2.045114] pcieport-driver 0000:00:1c.0: found MSI capability 
[    2.045144] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X 
[    2.045160] pci_express 0000:00:1c.0:pcie00: allocate port service 
[    2.045178] pci_express 0000:00:1c.0:pcie02: allocate port service 
[    2.045264] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    2.051656] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    2.051827] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0 
[    2.051831] ACPI: Power Button (FF) [PWRF] 
[    2.051893] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1 
[    2.051902] ACPI: Power Button (CM) [VBTN] 
[    2.052699] processor ACPI_CPU:00: registered as cooling_device0 
[    2.052753] processor ACPI_CPU:01: registered as cooling_device1 
[    2.101000] isapnp: Scanning for PnP cards... 
[    2.452689] isapnp: No Plug & Play device found 
[    2.464177] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    2.465496] brd: module loaded 
[    2.465969] loop: module loaded 
[    2.466081] Fixed MDIO Bus: probed 
[    2.466088] PPP generic driver version 2.4.2 
[    2.466167] input: Macintosh mouse button emulation as /devices/virtual/input/input2 
[    2.466208] Driver 'sd' needs updating - please use bus_type methods 
[    2.466222] Driver 'sr' needs updating - please use bus_type methods 
[    2.466319] ata_piix 0000:00:1f.1: version 2.12 
[    2.466334] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    2.466386] ata_piix 0000:00:1f.1: setting latency timer to 64 
[    2.466503] scsi0 : ata_piix 
[    2.466644] scsi1 : ata_piix 
[    2.466698] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14 
[    2.466701] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15 
[    2.660354] ata1.00: ATAPI: HL-DT-ST GCE-8487B, F109, max UDMA/33 
[    2.660402] ata1.01: ATAPI: TSSTcorpCD/DVDW SH-W162C, TS10, max UDMA/33 
[    2.692307] ata1.00: configured for UDMA/33 
[    2.732309] ata1.01: configured for UDMA/33 
[    2.734029] ata2: port disabled. ignoring. 
[    2.734415] scsi 0:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8487B  F109 PQ: 0 ANSI: 5 
[    2.737096] sr0: scsi3-mmc drive: 52x/48x writer cd/rw xa/form2 cdda tray 
[    2.737100] Uniform CD-ROM driver Revision: 3.20 
[    2.737228] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[    2.737293] sr 0:0:0:0: Attached scsi generic sg0 type 5 
[    2.738320] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-W162C TS10 PQ: 0 ANSI: 5 
[    2.747850] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray 
[    2.747935] sr 0:0:1:0: Attached scsi CD-ROM sr1 
[    2.747986] sr 0:0:1:0: Attached scsi generic sg1 type 5 
[    2.748032] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20 
[    2.748038] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[    2.904027] ata_piix 0000:00:1f.2: setting latency timer to 64 
[    2.904112] scsi2 : ata_piix 
[    2.904202] scsi3 : ata_piix 
[    2.904257] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20 
[    2.904261] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20 
[    3.133158] ata3.00: ATA-7: Maxtor 6L080M0, BANC1G10, max UDMA/133 
[    3.133162] ata3.00: 156250000 sectors, multi 8: LBA NCQ (not used) 
[    3.133493] ata3.01: ATA-6: ST3120026AS, 3.05, max UDMA/133 
[    3.133497] ata3.01: 234441648 sectors, multi 8: LBA48 
[    3.149184] ata3.00: configured for UDMA/133 
[    3.164445] ata3.01: configured for UDMA/133 
[    5.000167] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L080M0   BANC PQ: 0 ANSI: 5 
[    5.000303] sd 2:0:0:0: [sda] 156250000 512-byte hardware sectors: (80.0 GB/74.5 GiB) 
[    5.000330] sd 2:0:0:0: [sda] Write Protect is off 
[    5.000334] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.000374] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.000453] sd 2:0:0:0: [sda] 156250000 512-byte hardware sectors: (80.0 GB/74.5 GiB) 
[    5.000475] sd 2:0:0:0: [sda] Write Protect is off 
[    5.000479] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.000519] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.000524]  sda: sda1 sda2 < sda5 > 
[    5.047062] sd 2:0:0:0: [sda] Attached SCSI disk 
[    5.047118] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[    5.047221] scsi 2:0:1:0: Direct-Access     ATA      ST3120026AS      3.05 PQ: 0 ANSI: 5 
[    5.047344] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB) 
[    5.047367] sd 2:0:1:0: [sdb] Write Protect is off 
[    5.047371] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00 
[    5.047412] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.047485] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB) 
[    5.047508] sd 2:0:1:0: [sdb] Write Protect is off 
[    5.047512] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00 
[    5.047551] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.047556]  sdb: sdb1 
[    5.065238] sd 2:0:1:0: [sdb] Attached SCSI disk 
[    5.065292] sd 2:0:1:0: Attached scsi generic sg3 type 0 
[    5.066192] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    5.066222] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    5.066253] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    5.066258] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    5.066335] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
[    5.070257] ehci_hcd 0000:00:1d.7: debug port 1 
[    5.070265] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported 
[    5.070283] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800 
[    5.084014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    5.084113] usb usb1: configuration #1 chosen from 1 choice 
[    5.084157] hub 1-0:1.0: USB hub found 
[    5.084169] hub 1-0:1.0: 8 ports detected 
[    5.084321] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    5.084343] uhci_hcd: USB Universal Host Controller Interface driver 
[    5.084387] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
[    5.084397] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    5.084401] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    5.084466] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    5.084491] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80 
[    5.084589] usb usb2: configuration #1 chosen from 1 choice 
[    5.084624] hub 2-0:1.0: USB hub found 
[    5.084639] hub 2-0:1.0: 2 ports detected 
[    5.084768] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22 
[    5.084776] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    5.084779] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    5.084836] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
[    5.084869] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60 
[    5.084960] usb usb3: configuration #1 chosen from 1 choice 
[    5.084996] hub 3-0:1.0: USB hub found 
[    5.085005] hub 3-0:1.0: 2 ports detected 
[    5.085116] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[    5.085124] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[    5.085128] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[    5.085193] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
[    5.085225] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40 
[    5.085318] usb usb4: configuration #1 chosen from 1 choice 
[    5.085353] hub 4-0:1.0: USB hub found 
[    5.085362] hub 4-0:1.0: 2 ports detected 
[    5.085470] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23 
[    5.085478] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[    5.085482] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[    5.085542] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
[    5.085578] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20 
[    5.085669] usb usb5: configuration #1 chosen from 1 choice 
[    5.085703] hub 5-0:1.0: USB hub found 
[    5.085712] hub 5-0:1.0: 2 ports detected 
[    5.085875] usbcore: registered new interface driver libusual 
[    5.085921] usbcore: registered new interface driver usbserial 
[    5.085936] USB Serial support registered for generic 
[    5.085958] usbcore: registered new interface driver usbserial_generic 
[    5.085961] usbserial: USB Serial Driver core 
[    5.086028] PNP: No PS/2 controller found. Probing ports directly. 
[    5.088640] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    5.088649] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    5.092069] mice: PS/2 mouse device common for all mice 
[    5.104099] rtc_cmos 00:05: RTC can wake from S4 
[    5.104148] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0 
[    5.104177] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs 
[    5.104267] device-mapper: uevent: version 1.0.3 
[    5.104403] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email] 
[    5.104527] device-mapper: multipath: version 1.0.5 loaded 
[    5.104533] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    5.104653] EISA: Probing bus 0 at eisa.0 
[    5.104657] EISA: Cannot allocate resource for mainboard 
[    5.104664] Cannot allocate resource for EISA slot 2 
[    5.104676] Cannot allocate resource for EISA slot 5 
[    5.104678] Cannot allocate resource for EISA slot 6 
[    5.104689] EISA: Detected 0 cards. 
[    5.104765] cpuidle: using governor ladder 
[    5.104770] cpuidle: using governor menu 
[    5.105537] TCP cubic registered 
[    5.105634] NET: Registered protocol family 10 
[    5.106269] lo: Disabled Privacy Extensions 
[    5.106788] NET: Registered protocol family 17 
[    5.106813] Bluetooth: L2CAP ver 2.11 
[    5.106816] Bluetooth: L2CAP socket layer initialized 
[    5.106819] Bluetooth: SCO (Voice Link) ver 0.6 
[    5.106822] Bluetooth: SCO socket layer initialized 
[    5.106876] Bluetooth: RFCOMM socket layer initialized 
[    5.106894] Bluetooth: RFCOMM TTY layer initialized 
[    5.106899] Bluetooth: RFCOMM ver 1.10 
[    5.106978] Using IPI No-Shortcut mode 
[    5.107100] registered taskstats version 1 
[    5.107251]   Magic number: 5:623:743 
[    5.107345] rtc_cmos 00:05: setting system clock to 2009-04-30 16:42:20 UTC (1241109740) 
[    5.107349] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    5.107352] EDD information not available. 
[    5.107762] Freeing unused kernel memory: 532k freed 
[    5.107933] Write protecting the kernel text: 4128k 
[    5.107994] Write protecting the kernel read-only data: 1532k 
[    5.527245] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI 
[    5.527251] e100: Copyright(c) 1999-2006 Intel Corporation 
[    5.527321] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    5.551771] e100 0000:03:08.0: PME# disabled 
[    5.551807] usb 1-3: new high speed USB device using ehci_hcd and address 4 
[    5.590406] e100: eth0: e100_probe: addr 0xefbff000, irq 20, MAC addr 00:12:3f:9b:bd:b8 
[    5.691446] usb 1-3: configuration #1 chosen from 1 choice 
[    5.709527] Initializing USB Mass Storage driver... 
[    5.749214] scsi4 : SCSI emulation for USB Mass Storage devices 
[    5.751892] usbcore: registered new interface driver usb-storage 
[    5.751900] USB Mass Storage support registered. 
[    5.751981] usb-storage: device found at 4 
[    5.751986] usb-storage: waiting for device to settle before scanning 
[    5.812100] usb 1-4: new high speed USB device using ehci_hcd and address 5 
[    5.945568] usb 1-4: configuration #1 chosen from 1 choice 
[    5.945920] scsi5 : SCSI emulation for USB Mass Storage devices 
[    5.946476] usb-storage: device found at 5 
[    5.946483] usb-storage: waiting for device to settle before scanning 
[    6.056119] usb 1-6: new high speed USB device using ehci_hcd and address 6 
[    6.183435] PM: Starting manual resume from disk 
[    6.183440] PM: Resume from partition 8:5 
[    6.183443] PM: Checking hibernation image. 
[    6.183623] PM: Resume from disk failed. 
[    6.190346] usb 1-6: configuration #1 chosen from 1 choice 
[    6.207235] scsi6 : SCSI emulation for USB Mass Storage devices 
[    6.215077] usb-storage: device found at 6 
[    6.215082] usb-storage: waiting for device to settle before scanning 
[    6.216352] kjournald starting.  Commit interval 5 seconds 
[    6.216373] EXT3-fs: mounted filesystem with ordered data mode. 
[    6.452037] usb 2-1: new low speed USB device using uhci_hcd and address 2 
[    6.627822] usb 2-1: configuration #1 chosen from 1 choice 
[    6.868043] usb 2-2: new low speed USB device using uhci_hcd and address 3 
[    7.042724] usb 2-2: configuration #1 chosen from 1 choice 
[   10.748255] usb-storage: device scan complete 
[   10.750100] scsi 4:0:0:0: Direct-Access     Samsung  CF Card       CF 1.6E PQ: 0 ANSI: 0 CCS 
[   10.751968] scsi 4:0:0:1: Direct-Access     Samsung  MS Card       MS 1.6E PQ: 0 ANSI: 0 CCS 
[   10.753845] scsi 4:0:0:2: Direct-Access     Samsung  SD Card   MMC/SD 1.6E PQ: 0 ANSI: 0 CCS 
[   10.755717] scsi 4:0:0:3: Direct-Access     Samsung  SM/XD Card    SM 1.6E PQ: 0 ANSI: 0 CCS 
[   10.757319] sd 4:0:0:0: [sdc] Attached SCSI removable disk 
[   10.757411] sd 4:0:0:0: Attached scsi generic sg4 type 0 
[   10.758411] sd 4:0:0:1: [sdd] Attached SCSI removable disk 
[   10.758468] sd 4:0:0:1: Attached scsi generic sg5 type 0 
[   10.759542] sd 4:0:0:2: [sde] Attached SCSI removable disk 
[   10.759598] sd 4:0:0:2: Attached scsi generic sg6 type 0 
[   10.760661] sd 4:0:0:3: [sdf] Attached SCSI removable disk 
[   10.760728] sd 4:0:0:3: Attached scsi generic sg7 type 0 
[   10.944126] usb-storage: device scan complete 
[   10.944607] scsi 5:0:0:0: Direct-Access     WD       5000AAK External 1.06 PQ: 0 ANSI: 0 
[   10.945714] sd 5:0:0:0: [sdg] 976773168 512-byte hardware sectors: (500 GB/465 GiB) 
[   10.946461] sd 5:0:0:0: [sdg] Write Protect is off 
[   10.946465] sd 5:0:0:0: [sdg] Mode Sense: 00 00 00 00 
[   10.946468] sd 5:0:0:0: [sdg] Assuming drive cache: write through 
[   10.947085] sd 5:0:0:0: [sdg] 976773168 512-byte hardware sectors: (500 GB/465 GiB) 
[   10.947834] sd 5:0:0:0: [sdg] Write Protect is off 
[   10.947838] sd 5:0:0:0: [sdg] Mode Sense: 00 00 00 00 
[   10.947840] sd 5:0:0:0: [sdg] Assuming drive cache: write through 
[   10.947845]  sdg: sdg1 
[   10.961355] sd 5:0:0:0: [sdg] Attached SCSI disk 
[   10.961443] sd 5:0:0:0: Attached scsi generic sg8 type 0 
[   11.212136] usb-storage: device scan complete 
[   11.212618] scsi 6:0:0:0: Direct-Access     WD       10EAVS External  1.05 PQ: 0 ANSI: 4 
[   11.213724] sd 6:0:0:0: [sdh] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB) 
[   11.214595] sd 6:0:0:0: [sdh] Write Protect is off 
[   11.214599] sd 6:0:0:0: [sdh] Mode Sense: 21 00 00 00 
[   11.214602] sd 6:0:0:0: [sdh] Assuming drive cache: write through 
[   11.215222] sd 6:0:0:0: [sdh] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB) 
[   11.215969] sd 6:0:0:0: [sdh] Write Protect is off 
[   11.215973] sd 6:0:0:0: [sdh] Mode Sense: 21 00 00 00 
[   11.215975] sd 6:0:0:0: [sdh] Assuming drive cache: write through 
[   11.215980]  sdh: sdh1 
[   11.239735] sd 6:0:0:0: [sdh] Attached SCSI disk 
[   11.239815] sd 6:0:0:0: Attached scsi generic sg9 type 0 
[   13.066314] udev: starting version 141 
[   13.205945] usbcore: registered new interface driver hiddev 
[   13.220475] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3 
[   13.237033] Linux agpgart interface v0.103 
[   13.243812] agpgart-intel 0000:00:00.0: Intel 945G Chipset 
[   13.244340] agpgart-intel 0000:00:00.0: detected 7932K stolen memory 
[   13.247892] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000 
[   13.252853] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1/input0 
[   13.253182] usbcore: registered new interface driver usbhid 
[   13.253250] usbhid: v2.6:USB HID core driver 
[   13.375569] intel_rng: Firmware space is locked read-only. If you can't or 
[   13.375573] intel_rng: don't want to disable this in firmware setup, and if 
[   13.375576] intel_rng: you are certain that your system has a functional 
[   13.375579] intel_rng: RNG, try using the 'no_fwh_detect' option. 
[   13.482935] iTCO_vendor_support: vendor-support=0 
[   13.486197] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05 
[   13.486364] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860) 
[   13.486466] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   13.527501] input: PC Speaker as /devices/platform/pcspkr/input/input4 
[   13.903018] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
[   13.967395] input: DELL DELL USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5 
[   13.970680] dell 0003:413C:2005.0002: input,hidraw1: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:1d.0-2/input0 
[   14.201141] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   14.319371] C-Media PCI 0000:03:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[   14.350422] nf_conntrack version 0.5.0 (8040 buckets, 32160 max) 
[   14.351788] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use 
[   14.351795] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or 
[   14.351800] sysctl net.netfilter.nf_conntrack_acct=1 to enable it. 
[   14.388777] CA0106 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[   14.388818] snd-ca0106: Model 1007 Rev 00000000 Serial 10071102 
[   14.637967] lp: driver loaded but no devices found 
[   14.790210] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k 
[   15.357473] EXT3 FS on sda1, internal journal 
[   19.332272] type=1505 audit(1241109754.724:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2297 
[   19.387272] type=1505 audit(1241109754.776:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2301 
[   19.387433] type=1505 audit(1241109754.776:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2301 
[   19.387490] type=1505 audit(1241109754.776:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2301 
[   19.387547] type=1505 audit(1241109754.776:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2301 
[   19.547246] type=1505 audit(1241109754.936:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2306 
[   19.547466] type=1505 audit(1241109754.936:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2306 
[   19.637516] type=1505 audit(1241109755.028:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2320 
[   19.670368] type=1505 audit(1241109755.060:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2324 
[   19.748278] type=1503 audit(1241109755.140:11): operation="capable" name="dac_override" pid=2345 profile="/sbin/dhclient-script" 
[   28.390499] [drm] Initialized drm 1.1.0 20060810 
[   28.414754] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   28.414764] pci 0000:00:02.0: setting latency timer to 64 
[   28.414963] [drm] Initialized i915 1.6.0 20080730 on minor 0 
[   28.418363] [drm:i915_setparam] *ERROR* unknown parameter 4 
[   28.418412] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   28.965707] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   52.048545] ppdev: user-space parallel port driver 
[   83.610842] __ratelimit: 3 callbacks suppressed 
[   83.610848] type=1503 audit(1241109819.001:13): operation="capable" name="dac_override" pid=4076 profile="/sbin/dhclient-script" 
[   83.610861] type=1503 audit(1241109819.001:14): operation="capable" name="dac_read_search" pid=4076 profile="/sbin/dhclient-script" 
[  339.627029] type=1503 audit(1241110075.017:15): operation="capable" name="dac_override" pid=4252 profile="/sbin/dhclient-script" 
[  339.627039] type=1503 audit(1241110075.017:16): operation="capable" name="dac_read_search" pid=4252 profile="/sbin/dhclient-script" 
[  406.998128] e1000: Unknown parameter `eeprom_bad_csum_allow' 
[  706.619421] type=1503 audit(1241110442.010:17): operation="capable" name="dac_override" pid=4885 profile="/sbin/dhclient-script" 
[  706.619431] type=1503 audit(1241110442.010:18): operation="capable" name="dac_read_search" pid=4885 profile="/sbin/dhclient-script" 
[  769.065195] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  769.068122] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex 
[  769.068777] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[  779.772011] eth0: no IPv6 routers present 
[  936.778813] type=1503 audit(1241110672.169:19): operation="capable" name="dac_override" pid=4905 profile="/sbin/dhclient-script" 
[  936.778822] type=1503 audit(1241110672.169:20): operation="capable" name="dac_read_search" pid=4905 profile="/sbin/dhclient-script" 
[ 2270.223176] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[ 7002.556032] usb 1-7: new high speed USB device using ehci_hcd and address 7 
[ 7002.692469] usb 1-7: configuration #1 chosen from 3 choices 
[ 7158.238493] usb 1-7: USB disconnect, address 7 
[ 7227.396026] usb 1-7: new high speed USB device using ehci_hcd and address 8 
[ 7227.532275] usb 1-7: configuration #1 chosen from 1 choice 
[ 7227.533324] scsi7 : SCSI emulation for USB Mass Storage devices 
[ 7227.533636] usb-storage: device found at 8 
[ 7227.533642] usb-storage: waiting for device to settle before scanning 
[ 7232.532635] usb-storage: device scan complete 
[ 7232.533985] scsi 7:0:0:0: Direct-Access     USB NAND FLASH DISK       1.00 PQ: 0 ANSI: 2 
[ 7232.537486] sd 7:0:0:0: [sdi] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 7232.540997] sd 7:0:0:0: [sdi] Write Protect is off 
[ 7232.541004] sd 7:0:0:0: [sdi] Mode Sense: 0b 00 00 08 
[ 7232.541009] sd 7:0:0:0: [sdi] Assuming drive cache: write through 
[ 7232.559992] sd 7:0:0:0: [sdi] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 7232.561237] sd 7:0:0:0: [sdi] Write Protect is off 
[ 7232.561245] sd 7:0:0:0: [sdi] Mode Sense: 0b 00 00 08 
[ 7232.561250] sd 7:0:0:0: [sdi] Assuming drive cache: write through 
[ 7232.561262]  sdi: sdi1 
[ 7232.616021] sd 7:0:0:0: [sdi] Attached SCSI removable disk 
[ 7232.616197] sd 7:0:0:0: Attached scsi generic sg10 type 0 
[ 7291.796474] usb 1-7: USB disconnect, address 8 
[ 7895.505949] [drm:i915_getparam] *ERROR* Unknown parameter 6

---

### Post by bboyshane on 2009-04-30
I am also having the same issue, and here is my dmesg output as well. My wireless works fine, but my wired connection is not functioning. I have only included pertinent dmesg output, i trimmed some....

thanks in advance



[    0.494787] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.494790] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.494795] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
[    0.494798] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.494804] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.494806] pci 0000:00:06.0:   IO window: disabled
[    0.494810] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.494814] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.494819] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.494822] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.494827] pci 0000:00:07.0:   MEM window: 0xfe000000-0xfebfffff
[    0.494830] pci 0000:00:07.0:   PREFETCH window: 0x000000f6000000-0x000000f8ffffff
[    0.494843] pci 0000:00:01.0: setting latency timer to 64
[    0.494851] pci 0000:00:06.0: setting latency timer to 64
[    0.494859] pci 0000:00:07.0: setting latency timer to 64
[    0.494863] bus: 00 index 0 io port: [0x00-0xffff]
[    0.494864] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.494866] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.494868] bus: 01 index 1 mmio: [0xfa000000-0xfdefffff]
[    0.494869] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.494871] bus: 01 index 3 mmio: [0x0-0x0]
[    0.494872] bus: 02 index 0 mmio: [0x0-0x0]
[    0.494874] bus: 02 index 1 mmio: [0xfdf00000-0xfdffffff]
[    0.494875] bus: 02 index 2 mmio: [0x0-0x0]
[    0.494877] bus: 02 index 3 mmio: [0x0-0x0]
[    0.494878] bus: 03 index 0 io port: [0xe000-0xefff]
[    0.494880] bus: 03 index 1 mmio: [0xfe000000-0xfebfffff]
[    0.494881] bus: 03 index 2 mmio: [0xf6000000-0xf8ffffff]
[    0.494883] bus: 03 index 3 mmio: [0x0-0x0]
[    0.494889] NET: Registered protocol family 2
[    0.500694] Switched to high resolution mode on CPU 1
[    0.504004] Switched to high resolution mode on CPU 0
[    0.508041] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.508222] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.508625] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.508867] TCP: Hash tables configured (established 131072 bind 65536)
[    0.508870] TCP reno registered
[    0.512055] NET: Registered protocol family 1
[    0.512147] checking if image is initramfs... it is
[    1.022918] Freeing initrd memory: 7363k freed
[    1.022981] Simple Boot Flag at 0x71 set to 0x1
[    1.023225] cpufreq: No nForce2 chipset.
[    1.023398] audit: initializing netlink socket (disabled)
[    1.023443] type=2000 audit(1241099612.021:1): initialized
[    1.029713] highmem bounce pool size: 64 pages
[    1.029719] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.030866] VFS: Disk quotas dquot_6.5.1
[    1.030917] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.031450] fuse init (API version 7.10)
[    1.031519] msgmni has been set to 1672
[    1.031701] alg: No test for stdrng (krng)
[    1.031711] io scheduler noop registered
[    1.031713] io scheduler anticipatory registered
[    1.031715] io scheduler deadline registered
[    1.031726] io scheduler cfq registered (default)
[    1.092042] pci 0000:01:00.0: Boot video device
[    1.093933] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.093967] pcieport-driver 0000:00:01.0: found MSI capability
[    1.093999] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.094009] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.094067] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.094113] pcieport-driver 0000:00:06.0: found MSI capability
[    1.094137] pcieport-driver 0000:00:06.0: irq 2302 for MSI/MSI-X
[    1.094149] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.094211] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.094257] pcieport-driver 0000:00:07.0: found MSI capability
[    1.094282] pcieport-driver 0000:00:07.0: irq 2301 for MSI/MSI-X
[    1.094293] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.094303] pci_express 0000:00:07.0:pcie02: allocate port service
[    1.094371] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.094572] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.094733] ACPI: AC Adapter [AC0] (on-line)
[    1.095072] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.133471] ACPI: Battery Slot [BAT0] (battery present)
[    1.133534] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.133536] ACPI: Power Button (FF) [PWRF]
[    1.133580] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.133582] ACPI: Power Button (CM) [PWRB]
[    1.133614] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.133619] ACPI: Sleep Button (CM) [SLPB]
[    1.133653] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.143559] ACPI: Lid Switch [LID]
[    1.144075] ACPI: SSDT BFFBE390, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.144460] ACPI: SSDT BFFBE630, 06D9 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.144921] Monitor-Mwait will be used to enter C-1 state
[    1.144924] Monitor-Mwait will be used to enter C-2 state
[    1.144938] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.144960] processor ACPI_CPU:00: registered as cooling_device0
[    1.144963] ACPI: Processor [P001] (supports 8 throttling states)
[    1.145273] ACPI: SSDT BFFBE2C0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    1.145604] ACPI: SSDT BFFBE5A0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    1.146118] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.146133] processor ACPI_CPU:01: registered as cooling_device1
[    1.146136] ACPI: Processor [P002] (supports 8 throttling states)
[    1.151370] thermal LNXTHERM:01: registered as thermal_zone0
[    1.152483] ACPI: Thermal Zone [THRM] (68 C)
[    1.152524] isapnp: Scanning for PnP cards...
[    1.505962] isapnp: No Plug & Play device found
[    1.517200] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.518086] brd: module loaded
[    1.518345] loop: module loaded
[    1.518400] Fixed MDIO Bus: probed
[    1.518406] PPP generic driver version 2.4.2
[    1.518454] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.518477] Driver 'sd' needs updating - please use bus_type methods
[    1.518484] Driver 'sr' needs updating - please use bus_type methods
[    1.518609] sata_sis 0000:00:05.0: version 1.0
[    1.518624] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.518629] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    1.518725] scsi0 : sata_sis
[    1.518789] scsi1 : sata_sis
[    1.519286] ata1: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    1.519289] ata2: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    1.709987] ata1.00: ATA-8: ST9320421AS, SD14, max UDMA/133
[    1.709989] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.769956] ata1.00: configured for UDMA/133
[    1.932212] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RR07, max UDMA/133
[    1.948228] ata2.00: configured for UDMA/133
[    1.950610] scsi 0:0:0:0: Direct-Access     ATA      ST9320421AS      SD14 PQ: 0 ANSI: 5
[    1.950688] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    1.950702] sd 0:0:0:0: [sda] Write Protect is off
[    1.950704] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.950724] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.950777] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    1.950789] sd 0:0:0:0: [sda] Write Protect is off
[    1.950791] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.950810] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.950812]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.985354] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.985390] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.988390] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RR07 PQ: 0 ANSI: 5
[    1.999534] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.999537] Uniform CD-ROM driver Revision: 3.20
[    1.999606] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.999633] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.999962] pata_sis 0000:00:02.5: version 0.5.2
[    2.000042] scsi2 : pata_sis
[    2.000091] scsi3 : pata_sis
[    2.000562] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    2.000564] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    2.156075] ata4: port disabled. ignoring.
[    2.156154] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.156170] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.156183] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    2.156228] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.156268] ehci_hcd 0000:00:03.3: irq 22, io mem 0xf9ffd000
[    2.168006] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    2.168075] usb usb1: configuration #1 chosen from 1 choice
[    2.168097] hub 1-0:1.0: USB hub found
[    2.168105] hub 1-0:1.0: 8 ports detected
[    2.168186] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.168197] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.168204] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.168240] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.168255] ohci_hcd 0000:00:03.0: irq 20, io mem 0xf9fff000
[    2.226036] usb usb2: configuration #1 chosen from 1 choice
[    2.226054] hub 2-0:1.0: USB hub found
[    2.226062] hub 2-0:1.0: 4 ports detected
[    2.226137] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.226148] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.226180] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.226200] ohci_hcd 0000:00:03.1: irq 21, io mem 0xf9ffe000
[    2.282035] usb usb3: configuration #1 chosen from 1 choice
[    2.282059] hub 3-0:1.0: USB hub found
[    2.282066] hub 3-0:1.0: 4 ports detected
[    2.282128] uhci_hcd: USB Universal Host Controller Interface driver
[    2.282167] usbcore: registered new interface driver libusual
[    2.282192] usbcore: registered new interface driver usbserial
[    2.282201] USB Serial support registered for generic
[    2.282211] usbcore: registered new interface driver usbserial_generic
[    2.282213] usbserial: USB Serial Driver core
[    2.282252] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.285254] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.286584] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.286589] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.286591] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.286593] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.286594] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.289028] mice: PS/2 mouse device common for all mice
[    2.309048] rtc_cmos 00:08: RTC can wake from S4
[    2.309075] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.309094] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    2.309135] device-mapper: uevent: version 1.0.3
[    2.309204] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.309264] device-mapper: multipath: version 1.0.5 loaded
[    2.309266] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.309323] EISA: Probing bus 0 at eisa.0
[    2.309332] Cannot allocate resource for EISA slot 2
[    2.309352] EISA: Detected 0 cards.
[    2.309431] cpuidle: using governor ladder
[    2.309501] cpuidle: using governor menu
[    2.309901] TCP cubic registered
[    2.309981] NET: Registered protocol family 10
[    2.310328] lo: Disabled Privacy Extensions
[    2.310587] NET: Registered protocol family 17
[    2.310601] Bluetooth: L2CAP ver 2.11
[    2.310603] Bluetooth: L2CAP socket layer initialized
[    2.310605] Bluetooth: SCO (Voice Link) ver 0.6
[    2.310606] Bluetooth: SCO socket layer initialized
[    2.310629] Bluetooth: RFCOMM socket layer initialized
[    2.310634] Bluetooth: RFCOMM TTY layer initialized
[    2.310635] Bluetooth: RFCOMM ver 1.10
[    2.310878] Marking TSC unstable due to TSC halts in idle
[    2.311029] Using IPI No-Shortcut mode
[    2.311082] registered taskstats version 1
[    2.311160]   Magic number: 5:958:888
[    2.311221] rtc_cmos 00:08: setting system clock to 2009-04-30 13:53:33 UTC (1241099613)
[    2.311224] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.311226] EDD information not available.
[    2.311518] Freeing unused kernel memory: 532k freed
[    2.311613] Write protecting the kernel text: 4128k
[    2.311647] Write protecting the kernel read-only data: 1532k
[    2.349664] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.537018] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    2.769271] usb 1-5: configuration #1 chosen from 1 choice
[    3.005017] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    3.218124] usb 3-2: configuration #1 chosen from 1 choice
[    3.224849] usbcore: registered new interface driver hiddev
[    3.230226] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input6
[    3.245096] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:03.1-2/input0
[    3.245115] usbcore: registered new interface driver usbhid
[    3.245118] usbhid: v2.6:USB HID core driver
[    3.273785] PM: Starting manual resume from disk
[    3.273788] PM: Resume from partition 8:5
[    3.273789] PM: Checking hibernation image.
[    3.274057] PM: Resume from disk failed.
[    3.302834] EXT4-fs: barriers enabled
[    3.318496] kjournald2 starting.  Commit interval 5 seconds
[    3.318506] EXT4-fs: delayed allocation enabled
[    3.318507] EXT4-fs: file extents enabled
[    3.328991] EXT4-fs: mballoc enabled
[    3.328995] EXT4-fs: mounted filesystem with ordered data mode.
[    6.839987] udev: starting version 141
[    7.094582] acpi device:19: registered as cooling_device2
[    7.094723] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/input/input7
[    7.097107] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    7.133474] Linux agpgart interface v0.103
[    7.185408] Linux video capture interface: v2.00
[    7.222909] asus-laptop: Asus Laptop Support version 0.42
[    7.227522] asus-laptop:   F50SV model detected
[    7.233151] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[    7.248579] input: PC Speaker as /devices/platform/pcspkr/input/input8
[    7.304065] cfg80211: Calling CRDA to update world regulatory domain
[    7.417460] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[    7.418928] input: CNF7129 as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.0/input/input9
[    7.421275] usbcore: registered new interface driver uvcvideo
[    7.421279] USB Video Class driver (v0.1.0)
[    7.457080] cfg80211: World regulatory domain updated:
[    7.457083] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.457085] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.457087] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.457089] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.457091] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.457092] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.637770] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    7.683119] nvidia: module license 'NVIDIA' taints kernel.
[    7.936764] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.936774] nvidia 0000:01:00.0: setting latency timer to 64
[    7.937154] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    8.003692] sis190 Gigabit Ethernet driver 1.2 loaded.
[    8.003714] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.003724] sis190 0000:00:04.0: setting latency timer to 64
[    8.003753] 0000:00:04.0: Read MAC address from EEPROM
[    8.003755] 0000:00:04.0: Error EEPROM read 0.
[    8.003757] 0000:00:04.0: Read MAC address from APC.
[    8.024692] ath9k: 0.1
[    8.024729] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.024739] ath9k 0000:02:00.0: setting latency timer to 64
[    8.033015] 0000:00:04.0: Unknown PHY transceiver at address 0.
[    8.460891] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    8.526196] Registered led device: ath9k-phy0:radio
[    8.526209] Registered led device: ath9k-phy0:assoc
[    8.526221] Registered led device: ath9k-phy0:tx
[    8.526234] Registered led device: ath9k-phy0:rx
[    8.526656] phy0: Atheros 9280: mem=0xf7d80000, irq=16
[    8.565016] 0000:00:04.0: Using transceiver at address 1 as default.
[    8.582029] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[    8.596710] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f7c96c00 (IRQ: 19), 00:23:54:5f:9f:6e
[    8.596713] eth0: RGMII mode.
[    8.596718] eth0: Enabling Auto-negotiation.
[    8.627928] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[    8.629076] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.629143] HDA Intel 0000:00:0f.0: setting latency timer to 64
[    8.805954] lp: driver loaded but no devices found
[    8.859811] Adding 4883752k swap on /dev/sda5.  Priority:-1 extents:1 across:4883752k
[    9.389514] EXT4 FS on sda6, internal journal on sda6:8
[   10.273431] type=1505 audit(1241121221.460:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2021
[   10.308906] type=1505 audit(1241121221.496:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2025
[   10.308989] type=1505 audit(1241121221.496:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2025
[   10.309028] type=1505 audit(1241121221.496:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2025
[   10.309060] type=1505 audit(1241121221.496:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2025
[   10.408492] type=1505 audit(1241121221.593:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2030
[   10.408717] type=1505 audit(1241121221.593:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2030
[   10.430877] type=1505 audit(1241121221.617:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2034
[   12.429403] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   12.429406] vboxdrv: Successfully done.
[   12.429408] vboxdrv: Found 2 processor cores.
[   12.430150] vboxdrv: fAsync=0 offMin=0x183 offMax=0x2ed4
[   12.430190] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   12.430191] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   13.108130] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.108133] Bluetooth: BNEP filters: protocol multicast
[   13.134164] Bridge firewalling registered
[   14.558378] ppdev: user-space parallel port driver
[   18.811692] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.823882] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.543102] wlan0: direct probe to AP 00:c0:02:d2:d3:14 try 1
[   19.740031] wlan0: direct probe to AP 00:c0:02:d2:d3:14 try 2
[   19.944027] wlan0: direct probe to AP 00:c0:02:d2:d3:14 try 3
[   20.140029] wlan0: direct probe to AP 00:c0:02:d2:d3:14 timed out
[   26.758987] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   34.340536] wlan0: direct probe to AP 00:c0:02:d2:d3:14 try 1
[   34.349069] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   34.548027] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   34.752417] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   34.948028] wlan0: authentication with AP 00:11:95:4d:92:8b timed out
[   45.060560] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   45.068992] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   45.268029] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   45.468028] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   45.668581] wlan0: authentication with AP 00:11:95:4d:92:8b timed out
[   56.008579] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   56.017078] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   56.216025] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   56.416021] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   56.616024] wlan0: authentication with AP 00:11:95:4d:92:8b timed out
[   67.048525] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   67.050757] wlan0: authenticated
[   67.050761] wlan0: associate with AP 00:11:95:4d:92:8b
[   67.052203] wlan0: RX AssocResp from 00:11:95:4d:92:8b (capab=0x411 status=43 aid=0)
[   67.052207] wlan0: AP denied association (code=43)
[   67.248028] wlan0: associate with AP 00:11:95:4d:92:8b
[   67.250621] wlan0: RX AssocResp from 00:11:95:4d:92:8b (capab=0x411 status=0 aid=1)
[   67.250624] wlan0: associated
[   67.262326] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.111153] padlock: VIA PadLock not detected.
[   77.760018] wlan0: no IPv6 routers present
[   90.412282] wlan0: authenticate with AP 00:11:95:4d:92:8b
[   90.416571] wlan0: authenticated
[   90.416577] wlan0: associate with AP 00:11:95:4d:92:8b
[   90.425565] wlan0: RX AssocResp from 00:11:95:4d:92:8b (capab=0x411 status=0 aid=1)
[   90.425568] wlan0: associated
[  150.465772] wlan0 direct probe responded
[  150.465781] wlan0: authenticate with AP 00:11:95:4d:92:8b
[  150.471024] wlan0: authenticated
[  150.471030] wlan0: associate with AP 00:11:95:4d:92:8b
[  150.481867] wlan0: RX ReassocResp from 00:11:95:4d:92:8b (capab=0x411 status=0 aid=1)
[  150.481871] wlan0: associated
[  160.378606] wlan0: deauthenticated
[  161.376032] wlan0: direct probe to AP 00:11:95:4d:92:8b try 1
[  161.377141] wlan0 direct probe responded
[  161.377145] wlan0: authenticate with AP 00:11:95:4d:92:8b
[  161.380590] wlan0: authenticated
[  161.380593] wlan0: associate with AP 00:11:95:4d:92:8b
[  161.389555] wlan0: RX ReassocResp from 00:11:95:4d:92:8b (capab=0x411 status=0 aid=1)
[  161.389558] wlan0: associated
[ 2079.836026] usb 2-1: new low speed USB device using ohci_hcd and address 2
[ 2080.071173] usb 2-1: configuration #1 chosen from 1 choice

[ 2089.826948] usb 2-1: USB disconnect, address 2
[ 2168.892026] usb 2-1: new low speed USB device using ohci_hcd and address 3
[ 2169.121439] usb 2-1: configuration #1 chosen from 1 choice
[ 2169.137000] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input13
[ 2169.153113] generic-usb 0003:045E:00DD.0004: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:03.0-1/input0

[ 2219.470691] usb 2-1: USB disconnect, address 3
[ 2226.576028] usb 2-1: new low speed USB device using ohci_hcd and address 4
[ 2226.809158] usb 2-1: configuration #1 chosen from 1 choice
[ 2226.829557] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:03.0/usb2/2-1/2-1:1.0/input/input15
[ 2226.837115] generic-usb 0003:045E:00DD.0006: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:03.0-1/input0

[ 2232.345574] usb 2-1: USB disconnect, address 4
[ 2240.908022] usb 2-1: new low speed USB device using ohci_hcd and address 5
[ 2241.141425] usb 2-1: configuration #1 chosen from 1 choice

[ 2585.110106] usb 2-1: USB disconnect, address 8
shane@shane-laptop:~$ 



Any advice appreciated

---

### Post by sir_nasty on 2009-04-30
looks like you're having the same issue as found here:

[http://www.linuxquestions.org/questions/linux-networking-3/unable-to-dhcp-after-installing-ubuntu-jaunty-rc-amd64-720047/](http://www.linuxquestions.org/questions/linux-networking-3/unable-to-dhcp-after-installing-ubuntu-jaunty-rc-amd64-720047/)

from dmesg here's the evidence of the issue: 
[ 18.811692] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by nierdoi_sseaurou on 2009-05-01
That didn't help me at all. Does anyone have any idea how to fix this?

---

