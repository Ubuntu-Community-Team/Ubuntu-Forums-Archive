---
title: "Sony digital camera compatability"
date: 2009-09-20
forum: Multimedia Software
---

### Post by jfloria on 2009-09-20
Hi 
I have a Sony digital camera and my I have ubuntu 9.04.
When I plug in my camera nothing happens. I tried searching for my camera and my system does not have it on the list. 
Any direction will help.
Thanks 
Joe

---

### Post by blackened on 2009-09-21
Plug the camera in, then cut and paste the output of 
```
dmesg
```

---

### Post by jfloria on 2009-09-22
I have a sony model # DSC-H1 it is a class B
Still no luck. code did not work
Joe

---

### Post by blackened on 2009-09-22
The terminal command I gave was not meant to solve the problem, but to help diagnose it. Please enter that command into a terminal window (Applications -> Accessories -> Terminal) then cut and paste the output into your next message, preferably wrapped in code tags.

---

### Post by jfloria on 2009-09-24
Well here it is ... thanks.
I dont know how to wrap in code tags
Joe
[    0.506326] ACPI: No dock devices found.
[    0.506338] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.506419] pci 0000:00:02.0: reg 10 32bit mmio: [0xfdf00000-0xfdf7ffff]
[    0.506425] pci 0000:00:02.0: reg 14 io port: [0xff00-0xff07]
[    0.506430] pci 0000:00:02.0: reg 18 32bit mmio: [0xe0000000-0xefffffff]
[    0.506435] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfdf80000-0xfdfbffff]
[    0.506508] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.506537] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.506541] pci 0000:00:1b.0: PME# disabled
[    0.506584] pci 0000:00:1d.0: reg 20 io port: [0xfe00-0xfe1f]
[    0.506630] pci 0000:00:1d.1: reg 20 io port: [0xfd00-0xfd1f]
[    0.506677] pci 0000:00:1d.2: reg 20 io port: [0xfc00-0xfc1f]
[    0.506723] pci 0000:00:1d.3: reg 20 io port: [0xfb00-0xfb1f]
[    0.506768] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.506806] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.506811] pci 0000:00:1d.7: PME# disabled
[    0.506944] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.506951] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.506957] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.506964] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.506970] pci 0000:00:1f.1: reg 20 io port: [0xfa00-0xfa0f]
[    0.507015] pci 0000:00:1f.2: reg 10 io port: [0xf900-0xf907]
[    0.507021] pci 0000:00:1f.2: reg 14 io port: [0xf800-0xf803]
[    0.507027] pci 0000:00:1f.2: reg 18 io port: [0xf700-0xf707]
[    0.507033] pci 0000:00:1f.2: reg 1c io port: [0xf600-0xf603]
[    0.507039] pci 0000:00:1f.2: reg 20 io port: [0xf500-0xf50f]
[    0.507045] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.507059] pci 0000:00:1f.2: PME# supported from D3hot
[    0.507063] pci 0000:00:1f.2: PME# disabled
[    0.507110] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.507167] pci 0000:01:01.0: reg 10 32bit mmio: [0xfdeff000-0xfdefffff]
[    0.507205] pci 0000:01:01.0: supports D1 D2
[    0.507208] pci 0000:01:01.0: PME# supported from D0 D1 D2 D3hot
[    0.507212] pci 0000:01:01.0: PME# disabled
[    0.507247] pci 0000:01:04.0: reg 10 32bit mmio: [0xfdee0000-0xfdeeffff]
[    0.507255] pci 0000:01:04.0: reg 14 io port: [0xef00-0xef07]
[    0.507288] pci 0000:01:04.0: PME# supported from D3hot D3cold
[    0.507292] pci 0000:01:04.0: PME# disabled
[    0.507329] pci 0000:01:08.0: reg 10 32bit mmio: [0xfdefe000-0xfdefefff]
[    0.507336] pci 0000:01:08.0: reg 14 io port: [0xee00-0xee3f]
[    0.507369] pci 0000:01:08.0: supports D1 D2
[    0.507372] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.507376] pci 0000:01:08.0: PME# disabled
[    0.507412] pci 0000:00:1e.0: transparent bridge
[    0.507416] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.507421] pci 0000:00:1e.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.507432] bus 00 -> node 0
[    0.507440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.507713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.519157] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.519290] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.519422] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.519552] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.519684] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.519817] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.519949] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.520087] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.520349] ACPI: WMI: Mapper loaded
[    0.520406] SCSI subsystem initialized
[    0.520406] libata version 3.00 loaded.
[    0.520406] usbcore: registered new interface driver usbfs
[    0.520406] usbcore: registered new interface driver hub
[    0.520406] usbcore: registered new device driver usb
[    0.520406] PCI: Using ACPI for IRQ routing
[    0.528011] Bluetooth: Core ver 2.13
[    0.528028] NET: Registered protocol family 31
[    0.528028] Bluetooth: HCI device and connection manager initialized
[    0.528028] Bluetooth: HCI socket layer initialized
[    0.528028] NET: Registered protocol family 8
[    0.528028] NET: Registered protocol family 20
[    0.528041] NetLabel: Initializing
[    0.528044] NetLabel:  domain hash size = 128
[    0.528046] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.528060] NetLabel:  unlabeled traffic allowed by default
[    0.528075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.528081] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.532075] AppArmor: AppArmor Filesystem Enabled
[    0.536013] Switched to high resolution mode on CPU 0
[    0.536761] Switched to high resolution mode on CPU 1
[    0.540053] pnp: PnP ACPI init
[    0.540063] ACPI: bus type pnp registered
[    0.542194] pnp: PnP ACPI: found 13 devices
[    0.542196] ACPI: ACPI bus type pnp unregistered
[    0.542200] PnPBIOS: Disabled by ACPI PNP
[    0.542209] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.542212] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.542215] system 00:01: ioport range 0x294-0x297 has been reserved
[    0.542218] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.542226] system 00:09: ioport range 0x400-0x4bf has been reserved
[    0.542233] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.542239] system 00:0c: iomem range 0xd0800-0xd3fff has been reserved
[    0.542242] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.542245] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.542248] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.542251] system 00:0c: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.542254] system 00:0c: iomem range 0x7f6e0000-0x7f6fffff could not be reserved
[    0.542257] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.542260] system 00:0c: iomem range 0x100000-0x7f6dffff could not be reserved
[    0.542263] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.542265] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.542268] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.542271] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.542274] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.576967] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.576971] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.576976] pci 0000:00:1e.0:   MEM window: 0xfde00000-0xfdefffff
[    0.576980] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.576992] pci 0000:00:1e.0: setting latency timer to 64
[    0.576995] bus: 00 index 0 io port: [0x00-0xffff]
[    0.576998] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.577000] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.577003] bus: 01 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.577005] bus: 01 index 2 mmio: [0x0-0x0]
[    0.577007] bus: 01 index 3 io port: [0x00-0xffff]
[    0.577009] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.577017] NET: Registered protocol family 2
[    0.592082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.592342] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.592653] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.592817] TCP: Hash tables configured (established 131072 bind 65536)
[    0.592820] TCP reno registered
[    0.600124] NET: Registered protocol family 1
[    0.600254] checking if image is initramfs... it is
[   12.799782] Freeing initrd memory: 7384k freed
[   12.800019] cpufreq: No nForce2 chipset.
[   12.800173] audit: initializing netlink socket (disabled)
[   12.800199] type=2000 audit(1253723588.800:1): initialized
[   12.807803] highmem bounce pool size: 64 pages
[   12.807809] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[   12.809230] VFS: Disk quotas dquot_6.5.1
[   12.809291] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.809922] fuse init (API version 7.10)
[   12.810009] msgmni has been set to 1698
[   12.810200] alg: No test for stdrng (krng)
[   12.810213] io scheduler noop registered
[   12.810216] io scheduler anticipatory registered
[   12.810218] io scheduler deadline registered
[   12.810232] io scheduler cfq registered (default)
[   12.810243] pci 0000:00:02.0: Boot video device
[   12.810343] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[   12.812390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.812399] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   12.812548] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   12.812551] ACPI: Power Button (FF) [PWRF]
[   12.812595] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   12.812598] ACPI: Power Button (CM) [PWRB]
[   12.812651] fan PNP0C0B:00: registered as cooling_device0
[   12.812657] ACPI: Fan [FAN] (on)
[   12.813081] ACPI Error (psparse-0524): Method parse/execution failed [\_PR_.CPU0._PDC] (Node f6c1d0d8), AE_ALREADY_EXISTS
[   12.813089] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[   12.813142] processor ACPI_CPU:00: registered as cooling_device1
[   12.813304] ACPI: SSDT 7F6E8410, 00CE (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[   12.813541] processor ACPI_CPU:01: registered as cooling_device2
[   12.815526] thermal LNXTHERM:01: registered as thermal_zone0
[   12.815832] ACPI: Thermal Zone [THRM] (33 C)
[   12.815883] isapnp: Scanning for PnP cards...
[   13.168851] isapnp: No Plug & Play device found
[   13.176762] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   13.177890] brd: module loaded
[   13.178220] loop: module loaded
[   13.178290] Fixed MDIO Bus: probed
[   13.178295] PPP generic driver version 2.4.2
[   13.178354] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[   13.178383] Driver 'sd' needs updating - please use bus_type methods
[   13.178392] Driver 'sr' needs updating - please use bus_type methods
[   13.178433] ahci 0000:00:1f.2: version 3.0
[   13.178449] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.178480] ahci 0000:00:1f.2: irq 2303 for MSI/MSI-X
[   13.178544] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   13.178547] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
[   13.178551] ahci 0000:00:1f.2: setting latency timer to 64
[   13.178820] scsi0 : ahci
[   13.178904] scsi1 : ahci
[   13.178969] scsi2 : ahci
[   13.179031] scsi3 : ahci
[   13.179130] ata1: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 2303
[   13.179133] ata2: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 2303
[   13.179136] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 2303
[   13.179139] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 2303
[   13.496035] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   13.519151] ata1.00: ATA-8: WDC WD3200AAJS-00VWA0, 12.01B02, max UDMA/133
[   13.519155] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   13.519941] ata1.00: configured for UDMA/133
[   13.836033] ata2: SATA link down (SStatus 0 SControl 300)
[   14.156034] ata3: SATA link down (SStatus 0 SControl 300)
[   14.476033] ata4: SATA link down (SStatus 0 SControl 300)
[   14.476156] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[   14.476277] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   14.476294] sd 0:0:0:0: [sda] Write Protect is off
[   14.476297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.476323] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.476384] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   14.476399] sd 0:0:0:0: [sda] Write Protect is off
[   14.476402] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.476427] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.476431]  sda: sda1 sda2 < sda5 >
[   14.509567] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.509614] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.509675] ata_piix 0000:00:1f.1: version 2.12
[   14.509684] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.509715] ata_piix 0000:00:1f.1: setting latency timer to 64
[   14.509785] scsi4 : ata_piix
[   14.509847] scsi5 : ata_piix
[   14.510256] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[   14.510259] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[   14.672365] ata5.00: ATAPI: TSSTcorpCD/DVDW TS-H652M, 0414, max UDMA/33
[   14.688321] ata5.00: configured for UDMA/33
[   14.688804] ata6: port disabled. ignoring.
[   14.689628] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H652M 0414 PQ: 0 ANSI: 5
[   14.696194] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.696198] Uniform CD-ROM driver Revision: 3.20
[   14.696301] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   14.696344] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   14.696999] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   14.697018] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.697030] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   14.697034] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.697098] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   14.701012] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   14.701025] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[   14.716041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   14.716128] usb usb1: configuration #1 chosen from 1 choice
[   14.716164] hub 1-0:1.0: USB hub found
[   14.716172] hub 1-0:1.0: 8 ports detected
[   14.716310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.716325] uhci_hcd: USB Universal Host Controller Interface driver
[   14.716344] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.716350] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   14.716353] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.716396] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   14.716418] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[   14.716488] usb usb2: configuration #1 chosen from 1 choice
[   14.716514] hub 2-0:1.0: USB hub found
[   14.716521] hub 2-0:1.0: 2 ports detected
[   14.716603] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.716609] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   14.716612] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.716653] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   14.716680] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[   14.716750] usb usb3: configuration #1 chosen from 1 choice
[   14.716777] hub 3-0:1.0: USB hub found
[   14.716783] hub 3-0:1.0: 2 ports detected
[   14.716866] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   14.716872] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   14.716875] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.716916] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   14.716943] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[   14.717014] usb usb4: configuration #1 chosen from 1 choice
[   14.717040] hub 4-0:1.0: USB hub found
[   14.717046] hub 4-0:1.0: 2 ports detected
[   14.717126] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[   14.717132] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   14.717135] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   14.717182] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   14.717209] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[   14.717281] usb usb5: configuration #1 chosen from 1 choice
[   14.717306] hub 5-0:1.0: USB hub found
[   14.717316] hub 5-0:1.0: 2 ports detected
[   14.717459] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.719685] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.719692] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.720064] mice: PS/2 mouse device common for all mice
[   14.720220] rtc_cmos 00:04: RTC can wake from S4
[   14.720256] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[   14.720291] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[   14.720349] device-mapper: uevent: version 1.0.3
[   14.720434] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[   14.720513] device-mapper: multipath: version 1.0.5 loaded
[   14.720517] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.720593] EISA: Probing bus 0 at eisa.0
[   14.720621] EISA: Detected 0 cards.
[   14.720671] cpuidle: using governor ladder
[   14.720673] cpuidle: using governor menu
[   14.721193] TCP cubic registered
[   14.721292] NET: Registered protocol family 10
[   14.721737] lo: Disabled Privacy Extensions
[   14.722084] NET: Registered protocol family 17
[   14.722101] Bluetooth: L2CAP ver 2.11
[   14.722102] Bluetooth: L2CAP socket layer initialized
[   14.722106] Bluetooth: SCO (Voice Link) ver 0.6
[   14.722108] Bluetooth: SCO socket layer initialized
[   14.722139] Bluetooth: RFCOMM socket layer initialized
[   14.722146] Bluetooth: RFCOMM TTY layer initialized
[   14.722147] Bluetooth: RFCOMM ver 1.10
[   14.723800] Using IPI No-Shortcut mode
[   14.723889] registered taskstats version 1
[   14.724012]   Magic number: 9:920:540
[   14.724077] rtc_cmos 00:04: setting system clock to 2009-09-23 16:33:11 UTC (1253723591)
[   14.724080] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.724082] EDD information not available.
[   14.724258] Freeing unused kernel memory: 532k freed
[   14.724389] Write protecting the kernel text: 4116k
[   14.724436] Write protecting the kernel read-only data: 1528k
[   14.757311] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   14.960764] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[   14.960767] e100: Copyright(c) 1999-2006 Intel Corporation
[   14.960818] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   14.989892] e100 0000:01:08.0: PME# disabled
[   14.995439] e100: eth0: e100_probe: addr 0xfdefe000, irq 20, MAC addr 00:1a:92:b5:1e:bb
[   14.995462] ohci1394 0000:01:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.047187] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[   15.164536] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   15.252022] PM: Starting manual resume from disk
[   15.252026] PM: Resume from partition 8:5
[   15.252028] PM: Checking hibernation image.
[   15.252155] PM: Resume from disk failed.
[   15.295959] kjournald starting.  Commit interval 5 seconds
[   15.295967] EXT3-fs: mounted filesystem with ordered data mode.
[   15.297984] usb 1-3: configuration #1 chosen from 1 choice
[   15.305566] Initializing USB Mass Storage driver...
[   15.307081] scsi6 : SCSI emulation for USB Mass Storage devices
[   15.308141] usbcore: registered new interface driver usb-storage
[   15.308145] USB Mass Storage support registered.
[   15.308210] usb-storage: device found at 3
[   15.308212] usb-storage: waiting for device to settle before scanning
[   15.464018] usb 1-7: new high speed USB device using ehci_hcd and address 5
[   15.613918] usb 1-7: configuration #1 chosen from 1 choice
[   15.614562] scsi7 : SCSI emulation for USB Mass Storage devices
[   15.614645] usb-storage: device found at 5
[   15.614649] usb-storage: waiting for device to settle before scanning
[   15.852051] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   16.022557] usb 2-2: configuration #1 chosen from 1 choice
[   16.264033] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   16.328157] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800012fa6bc]
[   16.440818] usb 3-2: configuration #1 chosen from 1 choice
[   20.309039] usb-storage: device scan complete
[   20.309478] scsi 6:0:0:0: Direct-Access     HP       Officejet 6310   1.00 PQ: 0 ANSI: 2
[   20.310539] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   20.310596] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   20.613309] usb-storage: device scan complete
[   20.619785] scsi 7:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   20.626365] scsi 7:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   20.633879] scsi 7:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   20.640617] scsi 7:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   20.641803] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   20.641862] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   20.642784] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   20.642828] sd 7:0:0:1: Attached scsi generic sg4 type 0
[   20.644278] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   20.644324] sd 7:0:0:2: Attached scsi generic sg5 type 0
[   20.645286] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   20.645330] sd 7:0:0:3: Attached scsi generic sg6 type 0
[   20.690583] udev: starting version 141
[   20.940079] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5311
[   20.940106] usbcore: registered new interface driver usblp
[   20.979471] iTCO_vendor_support: vendor-support=0
[   20.980914] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   20.981177] iTCO_wdt: Found a ICH7DH TCO device (Version=2, TCOBASE=0x0460)
[   20.981230] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.995655] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   21.005948] usbcore: registered new interface driver hiddev
[   21.018825] Linux agpgart interface v0.103
[   21.021205] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[   21.034768] Linux video capture interface: v2.00
[   21.040644] generic-usb 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.1-2/input0
[   21.066995] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input6
[   21.069063] generic-usb 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.1-2/input1
[   21.069086] usbcore: registered new interface driver usbhid
[   21.069090] usbhid: v2.6:USB HID core driver
[   21.115850] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[   21.116911] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   21.120152] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   21.122775] gspca: main v2.3.0 registered
[   21.129358] gspca: probing 041e:401c
[   21.195153] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   21.271508] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.271559] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.301935] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   21.363610] zc3xx: probe sif 0x0007
[   21.367611] zc3xx: probe sensor -> 0f
[   21.367613] zc3xx: Find Sensor PAS106
[   21.373130] gspca: probe ok
[   21.373155] usbcore: registered new interface driver zc3xx
[   21.373158] zc3xx: registered
[   21.541263] lp: driver loaded but no devices found
[   21.613420] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k
[   21.670344] psmouse serio1: ID: 10 00 64<6>EXT3 FS on sda1, internal journal
[   22.197814] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   23.210118] type=1505 audit(1253723599.983:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2113
[   23.256485] type=1505 audit(1253723600.031:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2117
[   23.256574] type=1505 audit(1253723600.031:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2117
[   23.256612] type=1505 audit(1253723600.031:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2117
[   23.256651] type=1505 audit(1253723600.031:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2117
[   23.385728] type=1505 audit(1253723600.159:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2122
[   23.385874] type=1505 audit(1253723600.159:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2122
[   23.413332] type=1505 audit(1253723600.187:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2126
[   45.238505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.238508] Bluetooth: BNEP filters: protocol multicast
[   45.256249] Bridge firewalling registered
[   45.868045] ppdev: user-space parallel port driver
[   46.838520] [drm] Initialized drm 1.1.0 20060810
[   46.843663] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   46.843668] pci 0000:00:02.0: setting latency timer to 64
[   46.843802] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   46.845829] [drm:i915_setparam] *ERROR* unknown parameter 4
[   46.845851] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   47.394145] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   50.241130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.244140] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   50.247156] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   55.816283] usblp0: removed
[   55.928025] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[   56.061743] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5311
[   60.572020] eth0: no IPv6 routers present
[   70.954016] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  218.233720] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  218.236621] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  218.241427] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  228.320009] eth0: no IPv6 routers present
[  233.549635] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  233.552619] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  233.557225] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  244.204510] eth0: no IPv6 routers present
[  305.804625] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  305.808118] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  305.808376] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  316.180007] eth0: no IPv6 routers present
[  412.000304] e100: eth0: e100_watchdog: link down
[  736.000114] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  799.013130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  799.016619] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  799.020226] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  809.084008] eth0: no IPv6 routers present
[  920.613642] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  920.616620] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  920.623103] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  931.452008] eth0: no IPv6 routers present
[ 1773.864573] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2500.403085] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 3681.808372] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 6670.737142] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6670.740619] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 6670.744928] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6681.348009] eth0: no IPv6 routers present
[ 7404.328477] [drm:i915_getparam] *ERROR* Unknown parameter 6
[11117.486241] [drm:i915_getparam] *ERROR* Unknown parameter 6
[13001.091309] [drm:i915_getparam] *ERROR* Unknown parameter 6
[16302.662194] [drm:i915_getparam] *ERROR* Unknown parameter 6
[29593.010882] [drm:i915_getparam] *ERROR* Unknown parameter 6
[39516.601804] [drm:i915_getparam] *ERROR* Unknown parameter 6
[81013.464258] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[81013.484004] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[81013.508020] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[81182.517554] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[84347.976729] [drm:drm_wait_vblank] *ERROR* failed to acquire vblank counter, -22
[87703.976703] usblp0: removed
floriant@floriant-desktop:~$

---

