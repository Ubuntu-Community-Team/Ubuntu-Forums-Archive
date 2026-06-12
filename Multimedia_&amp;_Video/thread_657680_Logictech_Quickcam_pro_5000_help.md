---
title: "Logictech Quickcam pro 5000 help"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Hawk__0 on 2008-01-03
Hey guys, I have read these posts:
[http://ubuntuforums.org/showthread.php?t=585072&highlight=logitech+webcam+5000](http://ubuntuforums.org/showthread.php?t=585072&highlight=logitech+webcam+5000)
[http://ubuntuforums.org/showthread.php?t=524865](http://ubuntuforums.org/showthread.php?t=524865)

and looked here:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

and gotten this:
[http://packages.debian.org/testing/x11/luvcview](http://packages.debian.org/testing/x11/luvcview)

I have what seems to be a common problem, a video0 error with camorama.
When I try luvcview, I get this error, and im not really sure what it means:

steve@steve:~$ luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal 
steve@steve:~$ 

here is my dmesg, i know the errors at the bottom sure aren't good:
```
[   31.458789] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.458793] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   31.458799] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   31.458806] Boot video device is 0000:01:00.0
[   31.458859] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   31.458875] assign_interrupt_mode Found MSI capability
[   31.458878] Allocate Port Service[0000:00:0b.0:pcie00]
[   31.458921] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   31.458937] assign_interrupt_mode Found MSI capability
[   31.458938] Allocate Port Service[0000:00:0c.0:pcie00]
[   31.458976] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   31.458992] assign_interrupt_mode Found MSI capability
[   31.458994] Allocate Port Service[0000:00:0d.0:pcie00]
[   31.459032] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   31.459047] assign_interrupt_mode Found MSI capability
[   31.459049] Allocate Port Service[0000:00:0e.0:pcie00]
[   31.459124] isapnp: Scanning for PnP cards...
[   31.810919] isapnp: No Plug & Play device found
[   31.825087] Real Time Clock Driver v1.12ac
[   31.825158] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.825234] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.825609] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.826061] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.826212] input: Macintosh mouse button emulation as /class/input/input0
[   31.826280] PNP: No PS/2 controller found. Probing ports directly.
[   32.077574] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.077660] mice: PS/2 mouse device common for all mice
[   32.077727] EISA: Probing bus 0 at eisa.0
[   32.077739] Cannot allocate resource for EISA slot 4
[   32.077747] Cannot allocate resource for EISA slot 8
[   32.077748] EISA: Detected 0 cards.
[   32.077815] TCP cubic registered
[   32.077825] NET: Registered protocol family 1
[   32.077842] Using IPI No-Shortcut mode
[   32.077984]   Magic number: 3:648:543
[   32.078328] Freeing unused kernel memory: 364k freed
[   33.237815] AppArmor: AppArmor initialized<5>audit(1199122312.524:2):  type=1505 info="AppArmor initialized" pid=1239
[   33.244162] fuse init (API version 7.8)
[   33.247725] Failure registering capabilities with primary security module.
[   33.252924] ACPI: Fan [FAN] (on)
[   33.256084] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.257007] ACPI: Thermal Zone [THRM] (40 C)
[   33.675063] usbcore: registered new interface driver usbfs
[   33.675081] usbcore: registered new interface driver hub
[   33.675096] usbcore: registered new device driver usb
[   33.675553] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.675829] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   33.675837] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   33.675845] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.675848] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   33.675976] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   33.675990] ohci_hcd 0000:00:02.0: irq 16, io mem 0xd5003000
[   33.699780] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.699784] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.712642] SCSI subsystem initialized
[   33.715904] libata version 2.21 loaded.
[   33.731527] usb usb1: configuration #1 chosen from 1 choice
[   33.731547] hub 1-0:1.0: USB hub found
[   33.731556] hub 1-0:1.0: 10 ports detected
[   33.760296] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   33.833274] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   33.833283] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   33.833292] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   33.833295] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   33.833317] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   33.833341] ehci_hcd 0000:00:02.1: debug port 1
[   33.833344] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   33.833352] ehci_hcd 0000:00:02.1: irq 17, io mem 0xfeb00000
[   33.833357] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.833408] usb usb2: configuration #1 chosen from 1 choice
[   33.833430] hub 2-0:1.0: USB hub found
[   33.833436] hub 2-0:1.0: 10 ports detected
[   33.936718] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   33.936734] NFORCE-CK804: chipset revision 242
[   33.936736] NFORCE-CK804: not 100% native mode: will probe irqs later
[   33.936739] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[   33.936743] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   33.936749]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   33.936757]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   33.936762] Probing IDE interface ide0...
[   33.961123] Floppy drive(s): fd0 is 1.44M
[   33.987997] FDC 0 is a post-1991 82077
[   34.223897] hda: Maxtor 6Y160L0, ATA DISK drive
[   34.503203] hdb: ST3250824A, ATA DISK drive
[   34.559614] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.574031] Probing IDE interface ide1...
[   35.053742] usb 2-3: new high speed USB device using ehci_hcd and address 3
[   35.349575] usb 2-3: configuration #1 chosen from 1 choice
[   35.588484] hdd: LITE-ON COMBO SOHC-5232K, ATAPI CD/DVD-ROM drive
[   35.644737] ide1 at 0x170-0x177,0x376 on irq 15
[   35.647718] sata_nv 0000:00:07.0: version 3.4
[   35.648020] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   35.648028] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
[   35.648031] sata_nv 0000:00:07.0: Using ADMA mode
[   35.648061] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   35.648144] scsi0 : sata_nv
[   35.648174] scsi1 : sata_nv
[   35.648214] ata1: SATA max UDMA/133 cmd 0xf8840480 ctl 0xf88404a0 bmdma 0x0001d800 irq 18
[   35.648217] ata2: SATA max UDMA/133 cmd 0xf8840580 ctl 0xf88405a0 bmdma 0x0001d808 irq 18
[   35.654689] hda: max request size: 512KiB
[   35.662365] hda: 320173056 sectors (163928 MB) w/2048KiB Cache, CHS=19929/255/63, UDMA(133)
[   35.663657] hda: cache flushes supported
[   35.663696]  hda: hda1 hda2 < hda5 >
[   35.695860] hdb: max request size: 512KiB
[   35.726302] hdb: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   35.758883] hdb: cache flushes supported
[   35.758905]  hdb: hdb1 hdb2
[   35.786623] hdd: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.786630] Uniform CD-ROM driver Revision: 3.20
[   35.955488] ata1: SATA link down (SStatus 0 SControl 300)
[   36.130392] Attempting manual resume
[   36.130394] swsusp: Resume From Partition 3:5
[   36.130396] PM: Checking swsusp image.
[   36.130623] PM: Resume from disk failed.
[   36.139061] usb 2-10: new high speed USB device using ehci_hcd and address 7
[   36.142377] EXT3-fs: INFO: recovery required on readonly filesystem.
[   36.142381] EXT3-fs: write access will be enabled during recovery.
[   36.266715] ata2: SATA link down (SStatus 0 SControl 300)
[   36.267055] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   36.267063] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
[   36.267067] sata_nv 0000:00:08.0: Using ADMA mode
[   36.267101] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   36.267181] scsi2 : sata_nv
[   36.267225] scsi3 : sata_nv
[   36.267265] ata3: SATA max UDMA/133 cmd 0xf8864480 ctl 0xf88644a0 bmdma 0x0001c400 irq 19
[   36.267268] ata4: SATA max UDMA/133 cmd 0xf8864580 ctl 0xf88645a0 bmdma 0x0001c408 irq 19
[   36.271551] usb 2-10: configuration #1 chosen from 1 choice
[   36.573937] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   36.577928] ata3: SATA link down (SStatus 0 SControl 300)
[   36.800984] usb 1-2: configuration #1 chosen from 1 choice
[   36.889152] ata4: SATA link down (SStatus 0 SControl 300)
[   36.889554] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   36.889557] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   36.889562] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   36.889568] forcedeth: using HIGHDMA
[   37.112595] usb 1-4: new low speed USB device using ohci_hcd and address 3
[   37.326684] usb 1-4: configuration #1 chosen from 1 choice
[   37.408081] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0
[   37.408170] sata_sil 0000:05:0a.0: version 2.2
[   37.408411] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   37.408418] ACPI: PCI Interrupt 0000:05:0a.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   37.408431] sata_sil 0000:05:0a.0: Applying R_ERR on DMA activate FIS errata fix
[   37.408480] scsi4 : sata_sil
[   37.408511] scsi5 : sata_sil
[   37.408531] scsi6 : sata_sil
[   37.408554] scsi7 : sata_sil
[   37.408572] ata5: SATA max UDMA/100 cmd 0xf8850080 ctl 0xf885008a bmdma 0xf8850000 irq 20
[   37.408575] ata6: SATA max UDMA/100 cmd 0xf88500c0 ctl 0xf88500ca bmdma 0xf8850008 irq 20
[   37.408578] ata7: SATA max UDMA/100 cmd 0xf8850280 ctl 0xf885028a bmdma 0xf8850200 irq 20
[   37.408582] ata8: SATA max UDMA/100 cmd 0xf88502c0 ctl 0xf88502ca bmdma 0xf8850208 irq 20
[   37.631291] usb 1-7: new low speed USB device using ohci_hcd and address 4
[   37.719073] ata5: SATA link down (SStatus 0 SControl 310)
[   37.853380] usb 1-7: configuration #1 chosen from 1 choice
[   38.030296] ata6: SATA link down (SStatus 0 SControl 310)
[   38.079059] kjournald starting.  Commit interval 5 seconds
[   38.079069] EXT3-fs: hda1: orphan cleanup on readonly fs
[   38.079075] ext3_orphan_cleanup: deleting unreferenced inode 4997869
[   38.079111] ext3_orphan_cleanup: deleting unreferenced inode 10567688
[   38.079119] ext3_orphan_cleanup: deleting unreferenced inode 10567687
[   38.079124] ext3_orphan_cleanup: deleting unreferenced inode 10567686
[   38.079130] ext3_orphan_cleanup: deleting unreferenced inode 10567685
[   38.079135] ext3_orphan_cleanup: deleting unreferenced inode 10567684
[   38.079140] EXT3-fs: hda1: 6 orphan inodes deleted
[   38.079141] EXT3-fs: recovery complete.
[   38.115650] EXT3-fs: mounted filesystem with ordered data mode.
[   38.157979] usb 1-8: new low speed USB device using ohci_hcd and address 5
[   38.341517] ata7: SATA link down (SStatus 0 SControl 310)
[   38.378096] usb 1-8: configuration #1 chosen from 1 choice
[   38.381134] usbcore: registered new interface driver libusual
[   38.381250] usbcore: registered new interface driver hiddev
[   38.395133] input: Darfon USB Combo Keyboard as /class/input/input1
[   38.395142] input: USB HID v1.10 Keyboard [Darfon USB Combo Keyboard] on usb-0000:00:02.0-2
[   38.417965] input: Darfon USB Combo Keyboard as /class/input/input2
[   38.417969] input: USB HID v1.10 Device [Darfon USB Combo Keyboard] on usb-0000:00:02.0-2
[   38.423999] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   38.424010] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-4
[   38.808361] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   38.972190] ata8.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB01, max UDMA/100
[   39.143762] ata8.00: configured for UDMA/100
[   39.144472] scsi 7:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB01 PQ: 0 ANSI: 5
[   39.144811] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   39.144819] ACPI: PCI Interrupt 0000:05:0b.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   39.194529] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d4009000-d40097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   39.194805] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   39.194811] ACPI: PCI Interrupt 0000:05:0c.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[   39.194839] skge 1.11 addr 0xd4004000 irq 22 chip Yukon-Lite rev 7
[   39.194927] skge eth1: addr 00:11:d8:5c:4c:33
[   39.381885] Initializing USB Mass Storage driver...
[   39.381944] scsi8 : SCSI emulation for USB Mass Storage devices
[   39.381980] usb-storage: device found at 7
[   39.381981] usb-storage: waiting for device to settle before scanning
[   40.460286] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000004121a]
[   44.366585] usb-storage: device scan complete
[   44.370468] scsi 8:0:0:0: Direct-Access     OEI-USB2 StorageVault HD  1.19 PQ: 0 ANSI: 0
[   46.401825] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   46.401845] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   47.016895] Linux video capture interface: v2.00
[   47.058347] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[   47.100668] sd 8:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   47.158889] sd 8:0:0:0: [sda] Write Protect is off
[   47.158892] sd 8:0:0:0: [sda] Mode Sense: 0b 00 00 08
[   47.158894] sd 8:0:0:0: [sda] Assuming drive cache: write through
[   47.318599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.350219] sd 8:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   47.370676] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.399468] sd 8:0:0:0: [sda] Write Protect is off
[   47.399472] sd 8:0:0:0: [sda] Mode Sense: 0b 00 00 08
[   47.399474] sd 8:0:0:0: [sda] Assuming drive cache: write through
[   47.399479]  sda: sda1
[   47.482673]  sda: p1 exceeds device capacity
[   47.482769] sd 8:0:0:0: [sda] Attached SCSI disk
[   47.702668] scsi 7:0:0:0: Attached scsi generic sg0 type 5
[   47.702692] sd 8:0:0:0: Attached scsi generic sg1 type 0
[   47.796494] attempt to access beyond end of device
[   47.796498] sda: rw=0, want=488407970, limit=488397168
[   47.796501] Buffer I/O error on device sda1, logical block 61050928
[   47.796505] attempt to access beyond end of device
[   47.796507] sda: rw=0, want=488407970, limit=488397168
[   47.796509] Buffer I/O error on device sda1, logical block 61050928
[   47.796519] attempt to access beyond end of device
[   47.796521] sda: rw=0, want=488408122, limit=488397168
[   47.796522] Buffer I/O error on device sda1, logical block 61050947
[   47.796525] attempt to access beyond end of device
[   47.796527] sda: rw=0, want=488408122, limit=488397168
[   47.796528] Buffer I/O error on device sda1, logical block 61050947
[   47.799638] attempt to access beyond end of device
[   47.799642] sda: rw=0, want=488408130, limit=488397168
[   47.799644] Buffer I/O error on device sda1, logical block 61050948
[   47.799648] attempt to access beyond end of device
[   47.799649] sda: rw=0, want=488408130, limit=488397168
[   47.799651] Buffer I/O error on device sda1, logical block 61050948
[   47.799657] attempt to access beyond end of device
[   47.799659] sda: rw=0, want=488408130, limit=488397168
[   47.799660] Buffer I/O error on device sda1, logical block 61050948
[   47.799665] attempt to access beyond end of device
[   47.799667] sda: rw=0, want=488408130, limit=488397168
[   47.799669] Buffer I/O error on device sda1, logical block 61050948
[   47.799673] attempt to access beyond end of device
[   47.799675] sda: rw=0, want=488408130, limit=488397168
[   47.799677] Buffer I/O error on device sda1, logical block 61050948
[   47.799681] attempt to access beyond end of device
[   47.799683] sda: rw=0, want=488408130, limit=488397168
[   47.799685] Buffer I/O error on device sda1, logical block 61050948
[   47.799690] attempt to access beyond end of device
[   47.799692] sda: rw=0, want=488408130, limit=488397168
[   47.799697] attempt to access beyond end of device
[   47.799699] sda: rw=0, want=488408074, limit=488397168
[   47.799704] attempt to access beyond end of device
[   47.799705] sda: rw=0, want=488408122, limit=488397168
[   47.799710] attempt to access beyond end of device
[   47.799712] sda: rw=0, want=488408130, limit=488397168
[   47.799717] attempt to access beyond end of device
[   47.799719] sda: rw=0, want=488408130, limit=488397168
[   47.800556] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   47.800622] sr 7:0:0:0: Attached scsi CD-ROM sr0
[   47.820309] parport_pc 00:09: reported by Plug and Play ACPI
[   47.820356] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   47.924956] input: PC Speaker as /class/input/input4
[   48.142910] Linux agpgart interface v0.102 (c) Dave Jones
[   48.258884] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   48.261181] Audigy2 value: Special config.
[   48.408449] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   48.408462] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   48.408521] input: Logitech Logitech Dual Action as /class/input/input5
[   48.408545] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:02.0-7
[   48.454698] nvidia: module license 'NVIDIA' taints kernel.
[   48.729891] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   48.729900] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 23
[   48.729907] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.730094] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   58.391985] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   58.391992] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   58.392163] input: Logitech Logitech Dual Action as /class/input/input6
[   58.392279] input: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:02.0-8
[   58.392292] usbcore: registered new interface driver usbhid
[   58.392294] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   58.392375] usbcore: registered new interface driver xpad
[   58.392377] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   58.410973] usbcore: registered new interface driver uvcvideo
[   58.410976] USB Video Class driver (v0.1.0)
[   58.414006] usbcore: registered new interface driver snd-usb-audio
[   58.421302] usbcore: registered new interface driver usb-storage
[   58.421307] USB Mass Storage support registered.
[   58.773125] lp0: using parport0 (interrupt-driven).
[   58.841906] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
[   59.059283] EXT3 FS on hda1, internal journal
[   61.796209] No dock devices found.
[   61.842466] input: Power Button (FF) as /class/input/input7
[   61.845883] ACPI: Power Button (FF) [PWRF]
[   61.871262] input: Power Button (CM) as /class/input/input8
[   61.874627] ACPI: Power Button (CM) [PWRB]
[   62.196263] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   62.196290] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   62.196292] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   62.197764] powernow-k8: ph2 null fid transition 0xa
[   63.433047] skge eth0: enabling interface
[   63.583138] eth1: no link during initialization.
[   63.618787] NET: Registered protocol family 10
[   63.618951] lo: Disabled Privacy Extensions
[   63.619174] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   63.619187] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.343015] attempt to access beyond end of device
[   64.343021] sda: rw=0, want=488407970, limit=488397168
[   64.343023] printk: 5 messages suppressed.
[   64.343026] Buffer I/O error on device sda1, logical block 61050928
[   64.343684] attempt to access beyond end of device
[   64.343687] sda: rw=0, want=488407970, limit=488397168
[   64.343689] Buffer I/O error on device sda1, logical block 61050928
[   64.344165] attempt to access beyond end of device
[   64.344167] sda: rw=0, want=488408122, limit=488397168
[   64.344169] Buffer I/O error on device sda1, logical block 61050947
[   64.344662] attempt to access beyond end of device
[   64.344665] sda: rw=0, want=488408122, limit=488397168
[   64.347042] attempt to access beyond end of device
[   64.347045] sda: rw=0, want=488408130, limit=488397168
[   64.347353] attempt to access beyond end of device
[   64.347356] sda: rw=0, want=488408130, limit=488397168
[   64.347681] attempt to access beyond end of device
[   64.347683] sda: rw=0, want=488408130, limit=488397168
[   64.348004] attempt to access beyond end of device
[   64.348007] sda: rw=0, want=488408130, limit=488397168
[   64.348334] attempt to access beyond end of device
[   64.348337] sda: rw=0, want=488408130, limit=488397168
[   64.348660] attempt to access beyond end of device
[   64.348662] sda: rw=0, want=488408130, limit=488397168
[   64.348967] attempt to access beyond end of device
[   64.348969] sda: rw=0, want=488408130, limit=488397168
[   64.349269] attempt to access beyond end of device
[   64.349272] sda: rw=0, want=488408074, limit=488397168
[   64.349570] attempt to access beyond end of device
[   64.349572] sda: rw=0, want=488408122, limit=488397168
[   64.349871] attempt to access beyond end of device
[   64.349874] sda: rw=0, want=488408130, limit=488397168
[   64.350172] attempt to access beyond end of device
[   64.350175] sda: rw=0, want=488408130, limit=488397168
[   64.613976] ppdev: user-space parallel port driver
[   64.758033] audit(1199151144.697:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5208 profile="/usr/sbin/cupsd"
[   66.433943] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   66.434633] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   66.873278] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   66.873282] apm: overridden by ACPI.
[   68.269151] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   68.538298] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   68.555341] NFSD: starting 90-second grace period
[   39.336000] Marking TSC unstable due to: cpufreq changes.
[   39.340000] Time: acpi_pm clocksource has been installed.
[   39.552000] Clocksource tsc unstable (delta = -97384149 ns)
[   39.868000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.868000] vboxdrv: Successfully done.
[   40.752000] Failure registering capabilities with primary security module.
[   46.700000] NET: Registered protocol family 17
[  122.676000] eth0: no IPv6 routers present
[10798.032000] usb 1-1: new full speed USB device using ohci_hcd and address 6
[10798.280000] usb 1-1: configuration #1 chosen from 2 choices
[10798.384000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[10798.392000] usbcore: registered new interface driver cdc_acm
[10798.392000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[11012.204000] usb 1-1: USB disconnect, address 6
[11014.872000] usb 1-1: new full speed USB device using ohci_hcd and address 7
[11015.112000] usb 1-1: configuration #1 chosen from 2 choices
[11015.128000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[11383.320000] usb 1-1: USB disconnect, address 7
[12408.404000] usb 1-1: new full speed USB device using ohci_hcd and address 8
[12408.992000] usb 1-1: device not accepting address 8, error -62
[13188.604000] usb 1-1: new full speed USB device using ohci_hcd and address 10
[13188.844000] usb 1-1: configuration #1 chosen from 2 choices
[13188.860000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[13536.160000] usb 1-1: USB disconnect, address 10
[26563.060000] usb 1-1: new full speed USB device using ohci_hcd and address 11
[26563.304000] usb 1-1: configuration #1 chosen from 2 choices
[26563.320000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[26673.120000] usb 1-1: USB disconnect, address 11
[27660.968000] usb 1-1: new full speed USB device using ohci_hcd and address 12
[27661.220000] usb 1-1: configuration #1 chosen from 2 choices
[27661.232000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[31768.056000] usb 1-1: USB disconnect, address 12
[32827.080000] printk: 12 messages suppressed.
[32827.080000] UDP: short packet: From 207.214.83.38:32125 25649/73 to 10.0.0.2:9112
[60488.676000] UDP: short packet: From 76.208.213.81:32125 25649/73 to 10.0.0.2:9112
[68177.192000] usb 1-1: new full speed USB device using ohci_hcd and address 13
[68177.432000] usb 1-1: configuration #1 chosen from 2 choices
[68177.448000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[71415.644000] cdrom: This disc doesn't have any tracks I recognize!
[71590.756000] ata8.00: 16 bytes trailing data
[71590.908000] ata8.00: 16 bytes trailing data
[71645.676000] ata8.00: 16 bytes trailing data
[71913.280000] ata8.00: 16 bytes trailing data
[73922.176000] usb 1-1: USB disconnect, address 13
[85522.036000] UDP: short packet: From 207.214.83.38:32125 25649/73 to 10.0.0.2:9112
[96393.176000] UDP: short packet: From 207.214.83.38:32125 25649/73 to 10.0.0.2:9112
[98969.620000] cdrom: hdd: mrw address space DMA selected
[98969.776000] cdrom: hdd: mrw address space DMA selected
[98969.828000] UDF-fs: No VRS found
[98969.852000] ISO 9660 Extensions: Microsoft Joliet Level 3
[98969.892000] ISO 9660 Extensions: RRIP_1991A
[99064.984000] cdrom: hdd: mrw address space DMA selected
[99065.016000] cdrom: hdd: mrw address space DMA selected
[99065.060000] UDF-fs: No VRS found
[99065.088000] ISO 9660 Extensions: Microsoft Joliet Level 3
[99065.088000] ISO 9660 Extensions: RRIP_1991A
[170322.032000] UDP: short packet: From 207.214.83.38:32125 25649/73 to 10.0.0.2:9112
[173016.148000] usb 1-1: new full speed USB device using ohci_hcd and address 14
[173016.388000] usb 1-1: configuration #1 chosen from 2 choices
[173016.404000] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
[182775.932000] usb 1-1: USB disconnect, address 14
[256253.068000] usb 2-1: new high speed USB device using ehci_hcd and address 16
[256253.200000] usb 2-1: configuration #1 chosen from 1 choice
[256253.200000] scsi9 : SCSI emulation for USB Mass Storage devices
[256253.200000] usb-storage: device found at 16
[256253.200000] usb-storage: waiting for device to settle before scanning
[256258.200000] usb-storage: device scan complete
[256258.200000] scsi 9:0:0:0: Direct-Access     COWON    D2               0100 PQ: 0 ANSI: 0
[256258.200000] scsi 9:0:0:1: Direct-Access     COWON    D2               0100 PQ: 0 ANSI: 0
[256258.204000] sd 9:0:0:0: [sdb] 7815168 512-byte hardware sectors (4001 MB)
[256258.204000] sd 9:0:0:0: [sdb] Write Protect is off
[256258.204000] sd 9:0:0:0: [sdb] Mode Sense: 37 00 00 08
[256258.204000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[256258.212000] sd 9:0:0:0: [sdb] 7815168 512-byte hardware sectors (4001 MB)
[256258.212000] sd 9:0:0:0: [sdb] Write Protect is off
[256258.212000] sd 9:0:0:0: [sdb] Mode Sense: 37 00 00 08
[256258.212000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[256258.212000]  sdb: unknown partition table
[256258.216000] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[256258.216000] sd 9:0:0:0: Attached scsi generic sg2 type 0
[256258.220000] sd 9:0:0:1: [sdc] Attached SCSI removable disk
[256258.220000] sd 9:0:0:1: Attached scsi generic sg3 type 0
[261941.436000] uvcvideo: Failed to query (130) UVC control 9 (unit 2) : -32 (exp. 2).
[262062.296000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[264100.720000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[264101.720000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).

```

what does it mean, unable to set format 5? it says video0 is available.. so im confused.  anyone know how to fix this?
thank you in advance

---

### Post by thveillon on 2008-02-08
Hi, it might be because your webcam doesn't support the defaut luvcview format mjpeg, try : 
```
luvcview -f yuv
```

and see if it helps.

---

### Post by ecs_pf5 on 2008-04-26
Similar problem here on Kubuntu 8.04

I got luvcview via the repositories & that fires up & runs perfectly - with either 

luvcview -f yuv or 
luvcview -f jpg

But camorama gives popup window error:

> 
Could not connect to video device (/dev/video0).
Please check connection.
and in dmesg, at the point where camorama is attempting to start, there is:

```

[ 2955.630016] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[ 2957.625607] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[ 2958.144455] usb 5-8: device not accepting address 10, error -71
[ 2958.256213] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[ 2960.615007] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[ 2966.122865] usb 5-8: device not accepting address 10, error -110
[ 2966.234604] usb 5-8: reset high speed USB device using ehci_hcd and address 10
[ 2966.486056] usb 5-8: reset high speed USB device using ehci_hcd and address 10

```

---

