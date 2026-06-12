---
title: "skystar2"
date: 2010-05-04
forum: Multimedia Software
---

### Post by mahdi.alkhatib on 2010-05-04
[SIZE=5]Hello,
I'm so happy that I have moved to Ubuntu and to be in Linux world
and I was on windows 7
I have installed Ubuntu 10.04, and I have a skystar 2, I think that Ubuntu recognize my card, and there are programs installed with it called:
1- xine
2- movie player not sure if it's the same name of "mplayer"
and I have installed freevo
and when I click on it from 
Application->Sound & Video->freevo
doesn't start so what is the problem
I'm frustrated because I had opened a lot of web pages trying to figure out what's the problem:(
Pleaaaaaaaas help!
Thanks again.
 
[/SIZE]

---

### Post by mahdi.alkhatib on 2010-05-04
**no reply...**

---

### Post by mahdi.alkhatib on 2010-05-05
where are you guys...

---

### Post by realzippy on 2010-05-05
Have you installed *video4linux*?
Have you installed the driver from *Technisat*?

---

### Post by mahdi.alkhatib on 2010-05-05
I read that ubuntu 10.04 already has the driver of skystar2, but anyway I will try to install both of what you ask?

about freevo It's a general media player which play videos and music and even display pictures, WHY IT DOES NOT OPEN!!!

---

### Post by xc3RnbFO8P on 2010-05-06
In Terminal, show the output of: 
> dmesg

---

### Post by mahdi.alkhatib on 2010-05-07
```

[    0.671304] pci 0000:04:00.0: supports D1 D2
[    0.671306] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.671312] pci 0000:04:00.0: PME# disabled
[    0.671368] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.671372] pci 0000:00:1c.5: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
[    0.671400] pci 0000:05:00.0: reg 10 32bit mmio: [0xea100000-0xea10ffff]
[    0.671407] pci 0000:05:00.0: reg 14 io port: [0xd000-0xd01f]
[    0.671469] pci 0000:05:01.0: reg 10 32bit mmio: [0xea110000-0xea11ffff]
[    0.671477] pci 0000:05:01.0: reg 14 io port: [0xd100-0xd107]
[    0.671518] pci 0000:05:01.0: PME# supported from D3hot D3cold
[    0.671522] pci 0000:05:01.0: PME# disabled
[    0.671562] pci 0000:05:06.0: reg 10 32bit mmio: [0xea124000-0xea1247ff]
[    0.671570] pci 0000:05:06.0: reg 14 32bit mmio: [0xea120000-0xea123fff]
[    0.671613] pci 0000:05:06.0: supports D1 D2
[    0.671615] pci 0000:05:06.0: PME# supported from D0 D1 D2 D3hot
[    0.671620] pci 0000:05:06.0: PME# disabled
[    0.671662] pci 0000:00:1e.0: transparent bridge
[    0.671666] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.671670] pci 0000:00:1e.0: bridge 32bit mmio: [0xea100000-0xea1fffff]
[    0.671698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.671855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.671923] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.671993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.672049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.691650] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.691759] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.691867] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.691974] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.692081] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.692189] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.692295] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.692402] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.692529] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.692536] vgaarb: loaded
[    0.692659] SCSI subsystem initialized
[    0.692701] libata version 3.00 loaded.
[    0.692701] usbcore: registered new interface driver usbfs
[    0.692701] usbcore: registered new interface driver hub
[    0.692701] usbcore: registered new device driver usb
[    0.692701] ACPI: WMI: Mapper loaded
[    0.692701] PCI: Using ACPI for IRQ routing
[    0.692701] NetLabel: Initializing
[    0.692701] NetLabel:  domain hash size = 128
[    0.692701] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.692701] NetLabel:  unlabeled traffic allowed by default
[    0.692701] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.692701] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.730006] Switching to clocksource tsc
[    0.732264] AppArmor: AppArmor Filesystem Enabled
[    0.732289] pnp: PnP ACPI init
[    0.732310] ACPI: bus type pnp registered
[    0.735347] pnp: PnP ACPI: found 13 devices
[    0.735349] ACPI: ACPI bus type pnp unregistered
[    0.735363] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.735366] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.735370] system 00:01: ioport range 0x800-0x805 has been reserved
[    0.735373] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.735376] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.735384] system 00:09: ioport range 0x400-0x4bf could not be reserved
[    0.735391] system 00:0a: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.735398] system 00:0b: iomem range 0xcd000-0xcffff has been reserved
[    0.735401] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.735404] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.735407] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.735410] system 00:0b: iomem range 0xbfee0000-0xbfefffff could not be reserved
[    0.735414] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.735417] system 00:0b: iomem range 0x100000-0xbfedffff could not be reserved
[    0.735420] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.735424] system 00:0b: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.735427] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.735430] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.735433] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.735436] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.735439] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.740231] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.740235] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.740239] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe7ffffff
[    0.740243] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.740248] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.740251] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.740256] pci 0000:00:1c.0:   MEM window: 0xea300000-0xea4fffff
[    0.740260] pci 0000:00:1c.0:   PREFETCH window: 0x000000ea500000-0x000000ea6fffff
[    0.740266] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.740270] pci 0000:00:1c.4:   IO window: 0xb000-0xbfff
[    0.740274] pci 0000:00:1c.4:   MEM window: 0xea000000-0xea0fffff
[    0.740279] pci 0000:00:1c.4:   PREFETCH window: 0x000000ea700000-0x000000ea8fffff
[    0.740286] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.740289] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.740294] pci 0000:00:1c.5:   MEM window: 0xe8000000-0xe9ffffff
[    0.740299] pci 0000:00:1c.5:   PREFETCH window: 0xea900000-0xeaafffff
[    0.740305] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.740308] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.740313] pci 0000:00:1e.0:   MEM window: 0xea100000-0xea1fffff
[    0.740317] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.740330]   alloc irq_desc for 16 on node -1
[    0.740333]   alloc kstat_irqs on node -1
[    0.740339] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740344] pci 0000:00:01.0: setting latency timer to 64
[    0.740352] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740356] pci 0000:00:1c.0: setting latency timer to 64
[    0.740364] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740368] pci 0000:00:1c.4: setting latency timer to 64
[    0.740376]   alloc irq_desc for 17 on node -1
[    0.740378]   alloc kstat_irqs on node -1
[    0.740381] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.740385] pci 0000:00:1c.5: setting latency timer to 64
[    0.740392] pci 0000:00:1e.0: setting latency timer to 64
[    0.740397] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.740399] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.740402] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.740405] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe7ffffff]
[    0.740407] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xdfffffff]
[    0.740410] pci_bus 0000:02: resource 0 io:  [0x9000-0x9fff]
[    0.740413] pci_bus 0000:02: resource 1 mem: [0xea300000-0xea4fffff]
[    0.740415] pci_bus 0000:02: resource 2 pref mem [0xea500000-0xea6fffff]
[    0.740418] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.740420] pci_bus 0000:03: resource 1 mem: [0xea000000-0xea0fffff]
[    0.740423] pci_bus 0000:03: resource 2 pref mem [0xea700000-0xea8fffff]
[    0.740426] pci_bus 0000:04: resource 0 io:  [0xc000-0xcfff]
[    0.740428] pci_bus 0000:04: resource 1 mem: [0xe8000000-0xe9ffffff]
[    0.740431] pci_bus 0000:04: resource 2 pref mem [0xea900000-0xeaafffff]
[    0.740434] pci_bus 0000:05: resource 0 io:  [0xd000-0xdfff]
[    0.740436] pci_bus 0000:05: resource 1 mem: [0xea100000-0xea1fffff]
[    0.740439] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.740441] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.740480] NET: Registered protocol family 2
[    0.740685] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.742067] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.746212] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.746758] TCP: Hash tables configured (established 524288 bind 65536)
[    0.746761] TCP reno registered
[    0.746892] NET: Registered protocol family 1
[    0.747078] pci 0000:01:00.0: Boot video device
[    0.747495] Scanning for low memory corruption every 60 seconds
[    0.747663] audit: initializing netlink socket (disabled)
[    0.747674] type=2000 audit(1273222087.739:1): initialized
[    0.758415] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.760059] VFS: Disk quotas dquot_6.5.2
[    0.760117] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.760828] fuse init (API version 7.13)
[    0.760917] msgmni has been set to 7910
[    0.761266] alg: No test for stdrng (krng)
[    0.761330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.761333] io scheduler noop registered
[    0.761335] io scheduler anticipatory registered
[    0.761337] io scheduler deadline registered
[    0.761379] io scheduler cfq registered (default)
[    0.761543]   alloc irq_desc for 24 on node -1
[    0.761546]   alloc kstat_irqs on node -1
[    0.761555] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.761562] pcieport 0000:00:01.0: setting latency timer to 64
[    0.761660]   alloc irq_desc for 25 on node -1
[    0.761662]   alloc kstat_irqs on node -1
[    0.761669] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.761677] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.761790]   alloc irq_desc for 26 on node -1
[    0.761792]   alloc kstat_irqs on node -1
[    0.761799] pcieport 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.761807] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.761923]   alloc irq_desc for 27 on node -1
[    0.761925]   alloc kstat_irqs on node -1
[    0.761932] pcieport 0000:00:1c.5: irq 27 for MSI/MSI-X
[    0.761940] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.762027] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.762131] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.762246] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.762251] ACPI: Power Button [PWRB]
[    0.762315] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.762317] ACPI: Power Button [PWRF]
[    0.762693] processor LNXCPU:00: registered as cooling_device0
[    0.762792] processor LNXCPU:01: registered as cooling_device1
[    0.762874] processor LNXCPU:02: registered as cooling_device2
[    0.763025] processor LNXCPU:03: registered as cooling_device3
[    0.769870] Linux agpgart interface v0.103
[    0.769907] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.770004] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.770360] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.771517] brd: module loaded
[    0.772033] loop: module loaded
[    0.772119] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.772212] ata_piix 0000:00:1f.2: version 2.13
[    0.772227]   alloc irq_desc for 19 on node -1
[    0.772229]   alloc kstat_irqs on node -1
[    0.772237] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.772242] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.772286] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.780208] scsi0 : ata_piix
[    0.780307] scsi1 : ata_piix
[    0.781037] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.781043] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.781080] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.781085] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.781128] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.781208] scsi2 : ata_piix
[    0.781299] scsi3 : ata_piix
[    0.781864] ata3: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    0.781868] ata4: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    0.781948] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    0.781954] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.781982] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.781996] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.782315] Fixed MDIO Bus: probed
[    0.782352] PPP generic driver version 2.4.2
[    0.782407] tun: Universal TUN/TAP device driver, 1.6
[    0.782409] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.782505] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.782522]   alloc irq_desc for 18 on node -1
[    0.782524]   alloc kstat_irqs on node -1
[    0.782530] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.782550] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.782554] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.782589] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.786478] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.786490] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xea205000
[    0.810288] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.810377] usb usb1: configuration #1 chosen from 1 choice
[    0.810407] hub 1-0:1.0: USB hub found
[    0.810414] hub 1-0:1.0: 6 ports detected
[    0.810473]   alloc irq_desc for 23 on node -1
[    0.810475]   alloc kstat_irqs on node -1
[    0.810480] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.810491] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.810494] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.810531] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.814439] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.814452] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xea204000
[    0.830353] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.830430] usb usb2: configuration #1 chosen from 1 choice
[    0.830458] hub 2-0:1.0: USB hub found
[    0.830464] hub 2-0:1.0: 6 ports detected
[    0.830525] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.830541] uhci_hcd: USB Universal Host Controller Interface driver
[    0.830564] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.830570] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.830574] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.830607] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.830637] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    0.830725] usb usb3: configuration #1 chosen from 1 choice
[    0.830753] hub 3-0:1.0: USB hub found
[    0.830759] hub 3-0:1.0: 2 ports detected
[    0.830807]   alloc irq_desc for 21 on node -1
[    0.830809]   alloc kstat_irqs on node -1
[    0.830813] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.830819] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.830822] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.830859] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.830889] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[    0.830985] usb usb4: configuration #1 chosen from 1 choice
[    0.831012] hub 4-0:1.0: USB hub found
[    0.831018] hub 4-0:1.0: 2 ports detected
[    0.831064] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.831070] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.831073] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.831115] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.831137] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[    0.831225] usb usb5: configuration #1 chosen from 1 choice
[    0.831252] hub 5-0:1.0: USB hub found
[    0.831258] hub 5-0:1.0: 2 ports detected
[    0.831302] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.831308] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.831311] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.831348] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.831370] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[    0.831453] usb usb6: configuration #1 chosen from 1 choice
[    0.831483] hub 6-0:1.0: USB hub found
[    0.831489] hub 6-0:1.0: 2 ports detected
[    0.831532] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.831540] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.831544] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.831581] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.831603] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[    0.831686] usb usb7: configuration #1 chosen from 1 choice
[    0.831716] hub 7-0:1.0: USB hub found
[    0.831722] hub 7-0:1.0: 2 ports detected
[    0.831765] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.831771] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.831774] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.831808] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.831830] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[    0.831921] usb usb8: configuration #1 chosen from 1 choice
[    0.831949] hub 8-0:1.0: USB hub found
[    0.831955] hub 8-0:1.0: 2 ports detected
[    0.832054] PNP: No PS/2 controller found. Probing ports directly.
[    0.832421] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.832432] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.832592] mice: PS/2 mouse device common for all mice
[    0.832726] rtc_cmos 00:03: RTC can wake from S4
[    0.832790] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.832814] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.832962] device-mapper: uevent: version 1.0.3
[    0.833079] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.833262] device-mapper: multipath: version 1.1.0 loaded
[    0.833266] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.833620] cpuidle: using governor ladder
[    0.833622] cpuidle: using governor menu
[    0.833998] TCP cubic registered
[    0.834136] NET: Registered protocol family 10
[    0.834625] lo: Disabled Privacy Extensions
[    0.834928] NET: Registered protocol family 17
[    0.835093] PM: Resume from disk failed.
[    0.835107] registered taskstats version 1
[    0.835596]   Magic number: 10:153:826
[    0.835693] rtc_cmos 00:03: setting system clock to 2010-05-07 08:48:08 UTC (1273222088)
[    0.835697] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.835699] EDD information not available.
[    0.865329] Freeing initrd memory: 8134k freed
[    1.150771] ata3: SATA link down (SStatus 0 SControl 300)
[    1.161457] ata4: SATA link down (SStatus 0 SControl 300)
[    1.410033] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.596907] usb 3-1: configuration #1 chosen from 1 choice
[    1.640130] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.640144] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.640155] ata2.01: link offline, clearing class 3 to NONE
[    1.640333] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.640343] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.660368] ata1.00: ATA-7: WDC WD3200AAJS-65RYA0, 12.01B01, max UDMA/133
[    1.660372] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.660456] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    1.700388] ata2.00: configured for UDMA/100
[    1.700460] ata1.00: configured for UDMA/133
[    1.700573] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 12.0 PQ: 0 ANSI: 5
[    1.700731] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.700770] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.700838] sd 0:0:0:0: [sda] Write Protect is off
[    1.700841] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.700883] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.701092]  sda:
[    1.701713] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    1.705920] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.705925] Uniform CD-ROM driver Revision: 3.20
[    1.706033] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.706110] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.711205]  sda1 sda2 < sda5 >
[    1.743896] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.743921] Freeing unused kernel memory: 876k freed
[    1.744244] Write protecting the kernel read-only data: 7680k
[    1.762453] udev: starting version 151
[    1.809980] ahci 0000:03:00.0: version 3.0
[    1.810012] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.821217] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.821243] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.821306] r8169 0000:04:00.0: setting latency timer to 64
[    1.821368]   alloc irq_desc for 28 on node -1
[    1.821370]   alloc kstat_irqs on node -1
[    1.821386] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
[    1.821508] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.821514] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.821521] ahci 0000:03:00.0: setting latency timer to 64
[    1.822021] eth0: RTL8168b/8111b at 0xffffc90000676000, 00:1a:4d:46:4b:ee, XID 18000000 IRQ 28
[    1.823817] ohci1394 0000:05:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.826931] Floppy drive(s): fd0 is 1.44M
[    1.829872] scsi4 : ahci
[    1.831095] usbcore: registered new interface driver hiddev
[    1.834233] scsi5 : ahci
[    1.834380] ata5: SATA max UDMA/133 abar m8192@0xea000000 port 0xea000100 irq 16
[    1.834385] ata6: SATA max UDMA/133 abar m8192@0xea000000 port 0xea000180 irq 16
[    1.834477] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.834515] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.838456] scsi6 : pata_jmicron
[    1.839331] scsi7 : pata_jmicron
[    1.840127] ata7: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 17
[    1.840130] ata8: PATA max UDMA/100 cmd 0xb200 ctl 0xb300 bmdma 0xb408 irq 17
[    1.846267] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
[    1.846387] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1/input0
[    1.846418] usbcore: registered new interface driver usbhid
[    1.846421] usbhid: v2.6:USB HID core driver
[    1.853864] FDC 0 is a post-1991 82077
[    1.872576] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    1.883911] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ea124000-ea1247ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.066046] usb 3-2: configuration #1 chosen from 1 choice
[    2.083318] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4
[    2.083417] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1a.0-2/input0
[    2.107117] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input5
[    2.107182] generic-usb 0003:045E:00DD.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1a.0-2/input1
[    2.125750] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.182573] ata6: SATA link down (SStatus 0 SControl 300)
[    2.190133] ata5: SATA link down (SStatus 0 SControl 300)
[    3.200426] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c351cf00001a4d]
[   12.993098] udev: starting version 151
[   13.004974] lp: driver loaded but no devices found
[   13.031182] Adding 11890680k swap on /dev/sda5.  Priority:-1 extents:1 across:11890680k 
[   13.117175] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   13.118931] flexcop-pci: will use the HW PID filter.
[   13.118937] flexcop-pci: card revision 2
[   13.118949]   alloc irq_desc for 20 on node -1
[   13.118951]   alloc kstat_irqs on node -1
[   13.118959] b2c2_flexcop_pci 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.123312] parport_pc 00:08: reported by Plug and Play ACPI
[   13.123362] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.125056] vga16fb: initializing
[   13.125060] vga16fb: mapped to 0xffff8800000a0000
[   13.125120] fb0: VGA16 VGA frame buffer device
[   13.166829] nvidia: module license 'NVIDIA' taints kernel.
[   13.166834] Disabling lock debugging due to kernel taint
[   13.171504] DVB: registering new adapter (FlexCop Digital TV device)
[   13.173165] b2c2-flexcop: MAC address = 00:d0:d7:15:f8:e3
[   13.173822] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[   13.173860] CX24123: wrong demod revision: 87
[   13.190855] type=1505 audit(1273211300.846:2):  operation="profile_load" pid=641 name="/sbin/dhclient3"
[   13.191577] type=1505 audit(1273211300.846:3):  operation="profile_load" pid=641 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.191965] type=1505 audit(1273211300.846:4):  operation="profile_load" pid=641 name="/usr/lib/connman/scripts/dhclient-script"
[   13.210191] lp0: using parport0 (interrupt-driven).
[   13.358706] type=1505 audit(1273211301.016:5):  operation="profile_load" pid=758 name="/usr/share/gdm/guest-session/Xsession"
[   13.360669] type=1505 audit(1273211301.016:6):  operation="profile_replace" pid=759 name="/sbin/dhclient3"
[   13.361399] type=1505 audit(1273211301.016:7):  operation="profile_replace" pid=759 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.361794] type=1505 audit(1273211301.016:8):  operation="profile_replace" pid=759 name="/usr/lib/connman/scripts/dhclient-script"
[   13.364758] type=1505 audit(1273211301.026:9):  operation="profile_load" pid=760 name="/usr/bin/evince"
[   13.373850] type=1505 audit(1273211301.036:10):  operation="profile_load" pid=760 name="/usr/bin/evince-previewer"
[   13.379524] type=1505 audit(1273211301.036:11):  operation="profile_load" pid=760 name="/usr/bin/evince-thumbnailer"
[   13.557112] r8169: eth0: link up
[   13.557121] r8169: eth0: link up
[   13.621105] ppdev: user-space parallel port driver
[   13.697565]   alloc irq_desc for 22 on node -1
[   13.697568]   alloc kstat_irqs on node -1
[   13.697578] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.697600] hda_intel: position_fix set to 1 for device 1458:a022
[   13.697767] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.761878] Console: switching to colour frame buffer device 80x30
[   13.838908] hda_codec: ALC889A: BIOS auto-probing.
[   13.840263] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.849010] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[   13.849023] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[   13.849291] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[   13.850417] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.850428] nvidia 0000:01:00.0: setting latency timer to 64
[   13.850433] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.850656] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   22.714697] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   23.730032] eth0: no IPv6 routers present
[   32.458679] end_request: I/O error, dev fd0, sector 0
[   44.869061] end_request: I/O error, dev fd0, sector 0
[  123.290047] usb 3-2: USB disconnect, address 3
[  132.820024] usb 3-2: new low speed USB device using uhci_hcd and address 4
[  133.006937] usb 3-2: configuration #1 chosen from 1 choice
[  133.024186] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input7
[  133.024284] generic-usb 0003:045E:00DD.0004: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1a.0-2/input0
[  133.048002] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input8
[  133.048155] generic-usb 0003:045E:00DD.0005: input,hidraw2: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1a.0-2/input1


```

---

### Post by xc3RnbFO8P on 2010-05-07
Try Kaffeine, (Ubuntu Software Center).

---

### Post by mahdi.alkhatib on 2010-05-07
thank you very much it's solved,
but not all channels over there
and the codec is not good as eclard by progdvb on windows so is there help for these two upcoming problems
thank you so much again...

---

