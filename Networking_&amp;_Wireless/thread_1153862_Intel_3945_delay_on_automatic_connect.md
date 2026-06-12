---
title: "Intel 3945 delay on automatic connect"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by elw on 2009-05-09
I have switched from Windows Vista to Ubuntu a while ago and so far I am very happy with Ubuntu! Since 9.04 I have one annoying problem that keeps bugging me.

Once Ubuntu has booted I have to wait +- 2 minutes until it starts connecting to my wireless connection. Today I found out that if I click "Connect to hidden Wireless connection" and then select my wireless connection from the dropbox "Connection:" it connects straight away!

I tried deleting the connection and setting it up again but it didnt make any difference. 

Any way to make it connect automatic right away?

(I read the start post and maybe this is of use? dmesg command in terminal)
```

[    1.118909] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    1.119072] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    1.119235] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    1.119589] ACPI: WMI: Mapper loaded
[    1.119635] SCSI subsystem initialized
[    1.119635] libata version 3.00 loaded.
[    1.119635] usbcore: registered new interface driver usbfs
[    1.119635] usbcore: registered new interface driver hub
[    1.119635] usbcore: registered new device driver usb
[    1.120020] PCI: Using ACPI for IRQ routing
[    1.132011] Bluetooth: Core ver 2.13
[    1.132024] NET: Registered protocol family 31
[    1.132024] Bluetooth: HCI device and connection manager initialized
[    1.132024] Bluetooth: HCI socket layer initialized
[    1.132024] NET: Registered protocol family 8
[    1.132024] NET: Registered protocol family 20
[    1.132036] NetLabel: Initializing
[    1.132038] NetLabel:  domain hash size = 128
[    1.132039] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.132053] NetLabel:  unlabeled traffic allowed by default
[    1.132087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.132091] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.136066] AppArmor: AppArmor Filesystem Enabled
[    1.140012] Switched to high resolution mode on CPU 0
[    1.140540] Switched to high resolution mode on CPU 1
[    1.148010] pnp: PnP ACPI init
[    1.148018] ACPI: bus type pnp registered
[    1.149219] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 7 (0x1000-0x1fff), disabling
[    1.172483] pnp: PnP ACPI: found 10 devices
[    1.172485] ACPI: ACPI bus type pnp unregistered
[    1.172495] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.172498] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.172500] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.172503] system 00:01: ioport range 0x810-0x817 has been reserved
[    1.172505] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.172507] system 00:01: ioport range 0x500-0x53f has been reserved
[    1.172510] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    1.172513] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.172515] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    1.172518] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.172521] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.172523] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.172526] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.172528] system 00:01: iomem range 0x32000000-0x320000ff could not be reserved
[    1.177248] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    1.177251] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.177254] pci 0000:00:01.0:   IO window: 0x5000-0x5fff
[    1.177258] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd2ffffff
[    1.177261] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.177266] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.177269] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    1.177276] pci 0000:00:1c.0:   MEM window: 0xda300000-0xdb2fffff
[    1.177280] pci 0000:00:1c.0:   PREFETCH window: 0x000000d3000000-0x000000d3ffffff
[    1.177289] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    1.177292] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    1.177298] pci 0000:00:1c.1:   MEM window: 0xd9300000-0xda2fffff
[    1.177303] pci 0000:00:1c.1:   PREFETCH window: 0x000000d4000000-0x000000d4ffffff
[    1.177311] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    1.177314] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    1.177321] pci 0000:00:1c.2:   MEM window: 0xd8200000-0xd92fffff
[    1.177326] pci 0000:00:1c.2:   PREFETCH window: 0x000000d5000000-0x000000d5ffffff
[    1.177334] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    1.177337] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    1.177343] pci 0000:00:1c.3:   MEM window: 0xd7100000-0xd81fffff
[    1.177348] pci 0000:00:1c.3:   PREFETCH window: 0x000000d6000000-0x000000d6ffffff
[    1.177357] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    1.177358] pci 0000:00:1e.0:   IO window: disabled
[    1.177364] pci 0000:00:1e.0:   MEM window: 0xd7000000-0xd70fffff
[    1.177369] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.177384] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.177388] pci 0000:00:01.0: setting latency timer to 64
[    1.177396] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.177401] pci 0000:00:1c.0: setting latency timer to 64
[    1.177411] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.177416] pci 0000:00:1c.1: setting latency timer to 64
[    1.177426] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.177431] pci 0000:00:1c.2: setting latency timer to 64
[    1.177441] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.177446] pci 0000:00:1c.3: setting latency timer to 64
[    1.177454] pci 0000:00:1e.0: setting latency timer to 64
[    1.177459] bus: 00 index 0 io port: [0x00-0xffff]
[    1.177461] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    1.177463] bus: 01 index 0 io port: [0x5000-0x5fff]
[    1.177465] bus: 01 index 1 mmio: [0xd0000000-0xd2ffffff]
[    1.177466] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.177468] bus: 01 index 3 mmio: [0x0-0x0]
[    1.177470] bus: 02 index 0 io port: [0x4000-0x4fff]
[    1.177472] bus: 02 index 1 mmio: [0xda300000-0xdb2fffff]
[    1.177474] bus: 02 index 2 mmio: [0xd3000000-0xd3ffffff]
[    1.177475] bus: 02 index 3 mmio: [0x0-0x0]
[    1.177477] bus: 04 index 0 io port: [0x3000-0x3fff]
[    1.177479] bus: 04 index 1 mmio: [0xd9300000-0xda2fffff]
[    1.177481] bus: 04 index 2 mmio: [0xd4000000-0xd4ffffff]
[    1.177482] bus: 04 index 3 mmio: [0x0-0x0]
[    1.177484] bus: 05 index 0 io port: [0x2000-0x2fff]
[    1.177486] bus: 05 index 1 mmio: [0xd8200000-0xd92fffff]
[    1.177488] bus: 05 index 2 mmio: [0xd5000000-0xd5ffffff]
[    1.177489] bus: 05 index 3 mmio: [0x0-0x0]
[    1.177491] bus: 06 index 0 io port: [0x1000-0x1fff]
[    1.177493] bus: 06 index 1 mmio: [0xd7100000-0xd81fffff]
[    1.177495] bus: 06 index 2 mmio: [0xd6000000-0xd6ffffff]
[    1.177496] bus: 06 index 3 mmio: [0x0-0x0]
[    1.177498] bus: 07 index 0 mmio: [0x0-0x0]
[    1.177500] bus: 07 index 1 mmio: [0xd7000000-0xd70fffff]
[    1.177501] bus: 07 index 2 mmio: [0x0-0x0]
[    1.177503] bus: 07 index 3 io port: [0x00-0xffff]
[    1.177505] bus: 07 index 4 mmio: [0x000000-0xffffffffffffffff]
[    1.177513] NET: Registered protocol family 2
[    1.212056] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.212610] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    1.214563] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.215113] TCP: Hash tables configured (established 262144 bind 65536)
[    1.215116] TCP reno registered
[    1.224120] NET: Registered protocol family 1
[    1.224245] checking if image is initramfs... it is
[    1.969395] Freeing initrd memory: 7760k freed
[    1.973456] audit: initializing netlink socket (disabled)
[    1.973476] type=2000 audit(1241874856.972:1): initialized
[    1.982656] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.983941] VFS: Disk quotas dquot_6.5.1
[    1.983994] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.984569] fuse init (API version 7.10)
[    1.984647] msgmni has been set to 7787
[    1.984808] alg: No test for stdrng (krng)
[    1.984817] io scheduler noop registered
[    1.984820] io scheduler anticipatory registered
[    1.984822] io scheduler deadline registered
[    1.984861] io scheduler cfq registered (default)
[    1.985239] pci 0000:01:00.0: Boot video device
[    1.985278] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    1.985420] ACPI Warning (nspredef-0252): \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, expected 4 [20080926]
[    2.008394] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.032465] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.032501] pcieport-driver 0000:00:01.0: found MSI capability
[    2.032524] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    2.032534] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.032548] pci_express 0000:00:01.0:pcie02: allocate port service
[    2.032560] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.032611] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.032662] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.032696] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    2.032713] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.032728] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.032740] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.032816] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.032866] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.032900] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    2.032916] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.032928] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.032940] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.033021] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.033071] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.033106] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    2.033122] pci_express 0000:00:1c.2:pcie00: allocate port service
[    2.033135] pci_express 0000:00:1c.2:pcie02: allocate port service
[    2.033149] pci_express 0000:00:1c.2:pcie03: allocate port service
[    2.033225] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.033276] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.033310] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[    2.033326] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.033338] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.033350] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.033436] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.033449] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.033602] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.033748] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.033892] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.034036] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    2.034179] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.038078] ACPI: AC Adapter [AC] (on-line)
[    2.344113] ACPI: Battery Slot [BAT0] (battery present)
[    2.344194] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.344197] ACPI: Power Button (FF) [PWRF]
[    2.344245] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C0C:00/input/input1
[    2.344248] ACPI: Power Button (CM) [PWRB]
[    2.344297] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C0D:00/input/input2
[    2.344357] ACPI: Lid Switch [LID0]
[    2.344404] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/PNP0C0E:00/input/input3
[    2.344407] ACPI: Sleep Button (CM) [SLPB]
[    2.345069] ACPI: SSDT BFE74C90, 022C (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.345642] ACPI: SSDT BFE73610, 05D7 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.348207] Monitor-Mwait will be used to enter C-1 state
[    2.348210] Monitor-Mwait will be used to enter C-2 state
[    2.348212] Monitor-Mwait will be used to enter C-3 state
[    2.348226] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.348250] processor ACPI_CPU:00: registered as cooling_device0
[    2.348254] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.348638] ACPI: SSDT BFE74F10, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.349082] ACPI: SSDT BFE76D10, 0083 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.350059] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.350078] processor ACPI_CPU:01: registered as cooling_device1
[    2.350082] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.382758] thermal LNXTHERM:01: registered as thermal_zone0
[    2.399243] ACPI: Thermal Zone [TZ01] (0 C)
[    2.440247] Linux agpgart interface v0.103
[    2.440256] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.441219] brd: module loaded
[    2.441544] loop: module loaded
[    2.441605] Fixed MDIO Bus: probed
[    2.441610] PPP generic driver version 2.4.2
[    2.441671] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.441697] Driver 'sd' needs updating - please use bus_type methods
[    2.441706] Driver 'sr' needs updating - please use bus_type methods
[    2.441746] ahci 0000:00:1f.2: version 3.0
[    2.441759] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.441799] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    2.441865] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    2.441869] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    2.441874] ahci 0000:00:1f.2: setting latency timer to 64
[    2.442114] scsi0 : ahci
[    2.442204] scsi1 : ahci
[    2.442258] scsi2 : ahci
[    2.442378] ata1: SATA max UDMA/133 abar m2048@0xdb304000 port 0xdb304100 irq 2298
[    2.442382] ata2: SATA max UDMA/133 abar m2048@0xdb304000 port 0xdb304180 irq 2298
[    2.442385] ata3: SATA max UDMA/133 abar m2048@0xdb304000 port 0xdb304200 irq 2298
[    2.760021] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.760877] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.792403] ata1.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[    2.792406] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.793334] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.793455] ata1.00: configured for UDMA/133
[    3.128018] ata2: SATA link down (SStatus 0 SControl 300)
[    3.464017] ata3: SATA link down (SStatus 0 SControl 300)
[    3.480097] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[    3.480192] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.480209] sd 0:0:0:0: [sda] Write Protect is off
[    3.480211] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.480238] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.480297] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.480312] sd 0:0:0:0: [sda] Write Protect is off
[    3.480314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.480339] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.480342]  sda: sda1 sda2 sda3 sda4
[    3.543279] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.543323] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.543375] ata_piix 0000:00:1f.1: version 2.12
[    3.543383] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.543419] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.543501] scsi3 : ata_piix
[    3.543563] scsi4 : ata_piix
[    3.544228] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x60e0 irq 14
[    3.544230] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x60e8 irq 15
[    3.708418] ata4.00: ATAPI: Optiarc DVD RW AD-7560A, DX06, max UDMA/33
[    3.724366] ata4.00: configured for UDMA/33
[    3.892155] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DX06 PQ: 0 ANSI: 5
[    3.897326] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.897329] Uniform CD-ROM driver Revision: 3.20
[    3.897416] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.897453] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.898081] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.898099] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.898114] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.898118] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.898172] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.902083] ehci_hcd 0000:00:1a.7: debug port 1
[    3.902090] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.902104] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdb304c00
[    3.916010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.916081] usb usb1: configuration #1 chosen from 1 choice
[    3.916106] hub 1-0:1.0: USB hub found
[    3.916113] hub 1-0:1.0: 4 ports detected
[    3.916215] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.916226] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.916230] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.916276] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.920182] ehci_hcd 0000:00:1d.7: debug port 1
[    3.920188] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.920200] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdb304800
[    3.936010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.936070] usb usb2: configuration #1 chosen from 1 choice
[    3.936096] hub 2-0:1.0: USB hub found
[    3.936102] hub 2-0:1.0: 6 ports detected
[    3.936200] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.936215] uhci_hcd: USB Universal Host Controller Interface driver
[    3.936235] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.936242] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.936245] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.936284] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.936321] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000060c0
[    3.936396] usb usb3: configuration #1 chosen from 1 choice
[    3.936419] hub 3-0:1.0: USB hub found
[    3.936425] hub 3-0:1.0: 2 ports detected
[    3.936510] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.936519] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.936522] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.936563] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.936598] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000060a0
[    3.936671] usb usb4: configuration #1 chosen from 1 choice
[    3.936694] hub 4-0:1.0: USB hub found
[    3.936700] hub 4-0:1.0: 2 ports detected
[    3.936786] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.936793] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.936796] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.936843] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.936871] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00006080
[    3.936941] usb usb5: configuration #1 chosen from 1 choice
[    3.936967] hub 5-0:1.0: USB hub found
[    3.936973] hub 5-0:1.0: 2 ports detected
[    3.937054] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.937060] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.937063] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.937104] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.937140] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006060
[    3.937211] usb usb6: configuration #1 chosen from 1 choice
[    3.937236] hub 6-0:1.0: USB hub found
[    3.937242] hub 6-0:1.0: 2 ports detected
[    3.937326] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.937333] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.937336] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.937377] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.937404] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    3.937478] usb usb7: configuration #1 chosen from 1 choice
[    3.937506] hub 7-0:1.0: USB hub found
[    3.937512] hub 7-0:1.0: 2 ports detected
[    3.937644] usbcore: registered new interface driver libusual
[    3.937674] usbcore: registered new interface driver usbserial
[    3.937686] USB Serial support registered for generic
[    3.937700] usbcore: registered new interface driver usbserial_generic
[    3.937702] usbserial: USB Serial Driver core
[    3.937746] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    3.974304] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.974310] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.985037] mice: PS/2 mouse device common for all mice
[    4.045066] rtc_cmos 00:03: RTC can wake from S4
[    4.045103] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.045135] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.045190] device-mapper: uevent: version 1.0.3
[    4.045276] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.045346] device-mapper: multipath: version 1.0.5 loaded
[    4.045349] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.045505] cpuidle: using governor ladder
[    4.045613] cpuidle: using governor menu
[    4.046018] TCP cubic registered
[    4.046082] NET: Registered protocol family 10
[    4.046470] lo: Disabled Privacy Extensions
[    4.046760] NET: Registered protocol family 17
[    4.046777] Bluetooth: L2CAP ver 2.11
[    4.046779] Bluetooth: L2CAP socket layer initialized
[    4.046782] Bluetooth: SCO (Voice Link) ver 0.6
[    4.046783] Bluetooth: SCO socket layer initialized
[    4.046814] Bluetooth: RFCOMM socket layer initialized
[    4.046820] Bluetooth: RFCOMM TTY layer initialized
[    4.046822] Bluetooth: RFCOMM ver 1.10
[    4.047137] Marking TSC unstable due to TSC halts in idle
[    4.047413] registered taskstats version 1
[    4.047546]   Magic number: 9:215:230
[    4.047593] acpi device:4a: hash matches
[    4.047671] rtc_cmos 00:03: setting system clock to 2009-05-09 13:14:19 UTC (1241874859)
[    4.047673] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.047675] EDD information not available.
[    4.047742] Freeing unused kernel memory: 536k freed
[    4.047953] Write protecting the kernel read-only data: 6708k
[    4.066346] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.267330] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    4.392873] tg3.c:v3.94 (August 14, 2008)
[    4.392935] tg3 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.392951] tg3 0000:05:00.0: setting latency timer to 64
[    4.437810] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:59:b7:36
[    4.437814] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.437816] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.486522] ohci1394 0000:07:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.486532] ohci1394 0000:07:00.0: setting latency timer to 64
[    4.539298] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d7000000-d70007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.732178] usb 2-4: configuration #1 chosen from 1 choice
[    4.904803] PM: Starting manual resume from disk
[    4.904806] PM: Resume from partition 8:3
[    4.904807] PM: Checking hibernation image.
[    4.905082] PM: Resume from disk failed.
[    4.923805] EXT4-fs: barriers enabled
[    4.943902] kjournald2 starting.  Commit interval 5 seconds
[    4.943910] EXT4-fs: delayed allocation enabled
[    4.943912] EXT4-fs: file extents enabled
[    4.952137] EXT4-fs: mballoc enabled
[    4.952141] EXT4-fs: mounted filesystem with ordered data mode.
[    5.840156] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[b641323e00023f79]
[    8.783299] udev: starting version 141
[    9.175957] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    9.180628] cfg80211: Calling CRDA to update world regulatory domain
[    9.480147] nvidia: module license 'NVIDIA' taints kernel.
[    9.561075] iTCO_vendor_support: vendor-support=0
[    9.562576] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.562844] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[    9.562929] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.585986] cfg80211: World regulatory domain updated:
[    9.585990]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.585992]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.585994]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.585996]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.585999]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.586001]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.627119] acer-wmi: Acer Laptop ACPI-WMI Extras
[    9.639050] acer-wmi: Brightness must be controlled by generic video driver
[    9.639146] acer-wmi: software RFKILL enabled
[    9.666498] Linux video capture interface: v2.00
[    9.700503] sdhci: Secure Digital Host Controller Interface driver
[    9.700506] sdhci: Copyright(c) Pierre Ossman
[    9.702079] sdhci-pci 0000:07:00.1: SDHCI controller found [1180:0822] (rev 22)
[    9.702099] sdhci-pci 0000:07:00.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    9.705206] mmc0: SDHCI controller on PCI [0000:07:00.1] using PIO
[    9.718301] ricoh-mmc: Ricoh MMC Controller disabling driver
[    9.718304] ricoh-mmc: Copyright(c) Philip Langdale
[    9.718329] ricoh-mmc: Ricoh MMC controller found at 0000:07:00.2 [1180:0843] (rev 12)
[    9.718347] ricoh-mmc: Controller is now disabled.
[    9.735587] nvidia 0000:01:00.0: power state changed by ACPI to D0
[    9.735599] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.735607] nvidia 0000:01:00.0: setting latency timer to 64
[    9.735788] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[    9.765774] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.817403] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam  (5986:0102)
[    9.818273] input: Acer Crystal Eye webcam  as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[    9.833142] usbcore: registered new interface driver uvcvideo
[    9.833167] USB Video Class driver (v0.1.0)
[    9.844362] acpi device:37: registered as cooling_device2
[    9.844672] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:34/device:35/input/input8
[    9.868298] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.868301] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.868385] iwl3945 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.868399] iwl3945 0000:06:00.0: setting latency timer to 64
[    9.868446] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.871854] iwl3945 0000:06:00.0: irq 2297 for MSI/MSI-X
[    9.881153] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.926682] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.927561] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.056376] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.056457] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.494908] lp: driver loaded but no devices found
[   10.628439] Adding 6144852k swap on /dev/sda3.  Priority:-1 extents:1 across:6144852k
[   10.882542] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04713/0x204000
[   10.972333] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   11.004027] Clocksource tsc unstable (delta = -179289178 ns)
[   11.166534] EXT4 FS on sda2, internal journal on sda2:8
[   12.053150] EXT4-fs: barriers enabled
[   12.066740] kjournald2 starting.  Commit interval 5 seconds
[   12.066748] EXT4-fs warning: maximal mount count reached, running e2fsck is recommended
[   12.067045] EXT4 FS on sda4, internal journal on sda4:8
[   12.067048] EXT4-fs: delayed allocation enabled
[   12.067049] EXT4-fs: file extents enabled
[   12.072693] EXT4-fs: mballoc enabled
[   12.072696] EXT4-fs: mounted filesystem with ordered data mode.
[   12.280573] type=1505 audit(1241867667.732:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2118
[   12.319499] type=1505 audit(1241867667.768:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2122
[   12.319608] type=1505 audit(1241867667.768:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2122
[   12.319644] type=1505 audit(1241867667.768:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2122
[   12.319676] type=1505 audit(1241867667.768:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2122
[   12.426546] type=1505 audit(1241867667.876:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2127
[   12.426696] type=1505 audit(1241867667.876:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2127
[   12.451336] type=1505 audit(1241867667.900:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2131
[   15.099882] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   15.099885] vboxdrv: Successfully done.
[   15.099887] vboxdrv: Found 2 processor cores.
[   15.100834] VBoxDrv: dbg - g_abExecMemory=ffffffffa0ae0f00
[   15.100904] vboxdrv: fAsync=0 offMin=0x1a7 offMax=0xa6d1
[   15.100967] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.100969] vboxdrv: Successfully loaded version 2.2.2 (interface 0x000a0009).
[   15.358193] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c80bc0
[   16.441978] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.441981] Bluetooth: BNEP filters: protocol multicast
[   16.464988] Bridge firewalling registered
[   17.634410] ppdev: user-space parallel port driver
[   20.553060] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   20.732848] usb 6-1: configuration #1 chosen from 1 choice
[   20.758733] usbcore: registered new interface driver hiddev
[   20.762596] input: USB Multi-Smart Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input10
[   21.128099] generic-usb 0003:04FC:0801.0001: input,hidraw0: USB HID v1.11 Mouse [USB Multi-Smart Mouse] on usb-0000:00:1d.1-1/input0
[   21.128119] usbcore: registered new interface driver usbhid
[   21.128122] usbhid: v2.6:USB HID core driver
[   21.548442] tg3 0000:05:00.0: irq 2296 for MSI/MSI-X
[   21.765283] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.781783] iwl3945 0000:06:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   21.887136] Registered led device: iwl-phy0:radio
[   21.887156] Registered led device: iwl-phy0:assoc
[   21.887216] Registered led device: iwl-phy0:RX
[   21.887232] Registered led device: iwl-phy0:TX
[   21.899036] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.186669] wlan0: authenticate with AP 00:1a:92:b3:19:01
[   49.188459] wlan0: authenticated
[   49.188462] wlan0: associate with AP 00:1a:92:b3:19:01
[   49.190763] wlan0: RX AssocResp from 00:1a:92:b3:19:01 (capab=0x411 status=0 aid=3)
[   49.190766] wlan0: associated
[   49.196584] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.149056] wlan0: no IPv6 routers present
[  118.021684] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  390.866361] CE: hpet increasing min_delta_ns to 15000 nsec

```

Also booting wlan0 seems to take ages?

It is an Intel 3945 wireless card in an Acer Aspire 5720 laptop.

---

### Post by elw on 2009-05-11
Hmm no reactions. Anyway I fixed it by changing from the default Network Manager to WICD.

---

### Post by Mickser_52 on 2009-05-18
Thanks for the post. I was having a similar problem but WICD seems to have sorted it.

---

