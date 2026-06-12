---
title: "TV Tuner Card Not Recognized"
date: 2012-10-21
forum: Multimedia Software
---

### Post by stonecold82 on 2012-10-21
Hi,

Please help me:

I bought new UMAX USBTV tuner card which is working fine in windows 7. I would like same it work somehow on my Ubuntu 12.04.

The TV Tuner is not getting recognized ,I have tried installing TVTime and MythTV and tweaking with it nothing has helped me.

here is "lsusb" out put

-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1f71:3301  
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


Hers is "dmesg" out put

[    0.380189] pnp: PnP ACPI init
[    0.380206] ACPI: bus type pnp registered
[    0.380302] pnp 00:00: [bus 00-ff]
[    0.380305] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.380308] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.380310] pnp 00:00: [io  0x0d00-0xffff window]
[    0.380312] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.380315] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.380317] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.380378] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.380388] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.380442] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.380446] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.380478] pnp 00:02: [dma 4]
[    0.380480] pnp 00:02: [io  0x0000-0x000f]
[    0.380482] pnp 00:02: [io  0x0081-0x0083]
[    0.380484] pnp 00:02: [io  0x0087]
[    0.380486] pnp 00:02: [io  0x0089-0x008b]
[    0.380488] pnp 00:02: [io  0x008f]
[    0.380490] pnp 00:02: [io  0x00c0-0x00df]
[    0.380517] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.380528] pnp 00:03: [io  0x0070-0x0071]
[    0.380538] pnp 00:03: [irq 8]
[    0.380568] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.380577] pnp 00:04: [io  0x0061]
[    0.380606] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.380615] pnp 00:05: [io  0x00f0-0x00ff]
[    0.380620] pnp 00:05: [irq 13]
[    0.380647] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.380935] pnp 00:06: [irq 6]
[    0.380939] pnp 00:06: [dma 2]
[    0.380941] pnp 00:06: [io  0x03f0-0x03f5]
[    0.380943] pnp 00:06: [io  0x03f7]
[    0.381001] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.381356] pnp 00:07: [irq 7]
[    0.381358] pnp 00:07: [dma 3]
[    0.381360] pnp 00:07: [io  0x0378-0x037f]
[    0.381363] pnp 00:07: [io  0x0778-0x077f]
[    0.381503] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.381533] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.381536] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.381538] pnp 00:08: [io  0x0290-0x0297]
[    0.381582] system 00:08: [io  0x0290-0x0297] has been reserved
[    0.381586] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381658] pnp 00:09: [io  0x0010-0x001f]
[    0.381660] pnp 00:09: [io  0x0022-0x003f]
[    0.381662] pnp 00:09: [io  0x0044-0x005f]
[    0.381664] pnp 00:09: [io  0x0062-0x0063]
[    0.381666] pnp 00:09: [io  0x0065-0x006f]
[    0.381668] pnp 00:09: [io  0x0072-0x007f]
[    0.381670] pnp 00:09: [io  0x0080]
[    0.381672] pnp 00:09: [io  0x0084-0x0086]
[    0.381674] pnp 00:09: [io  0x0088]
[    0.381676] pnp 00:09: [io  0x008c-0x008e]
[    0.381678] pnp 00:09: [io  0x0090-0x009f]
[    0.381680] pnp 00:09: [io  0x00a2-0x00bf]
[    0.381682] pnp 00:09: [io  0x00e0-0x00ef]
[    0.381684] pnp 00:09: [io  0x04d0-0x04d1]
[    0.381686] pnp 00:09: [io  0x0800-0x087f]
[    0.381688] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.381690] pnp 00:09: [io  0x0480-0x04bf]
[    0.381692] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
[    0.381694] pnp 00:09: [mem 0xfed20000-0xfed8ffff]
[    0.381752] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.381755] system 00:09: [io  0x0800-0x087f] has been reserved
[    0.381758] system 00:09: [io  0x0480-0x04bf] has been reserved
[    0.381761] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.381764] system 00:09: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.381767] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.381830] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.381860] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.381910] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.381912] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.381946] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.381986] pnp 00:0c: [mem 0xffc00000-0xffefffff]
[    0.382032] system 00:0c: [mem 0xffc00000-0xffefffff] has been reserved
[    0.382036] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.382080] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.382082] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.382127] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.382130] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.382133] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.382161] pnp 00:0e: [io  0x0060]
[    0.382163] pnp 00:0e: [io  0x0064]
[    0.382168] pnp 00:0e: [irq 1]
[    0.382208] pnp 00:0e: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.382250] pnp 00:0f: [irq 12]
[    0.382288] pnp 00:0f: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.382546] pnp 00:10: [irq 4]
[    0.382549] pnp 00:10: [dma 0 disabled]
[    0.382551] pnp 00:10: [io  0x03f8-0x03ff]
[    0.382626] pnp 00:10: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.382659] pnp 00:11: [mem 0xf0000000-0xf3ffffff]
[    0.382706] system 00:11: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.382710] system 00:11: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.382868] pnp 00:12: [mem 0x00000000-0x0009ffff]
[    0.382870] pnp 00:12: [mem 0x000c0000-0x000cffff]
[    0.382872] pnp 00:12: [mem 0x000e0000-0x000fffff]
[    0.382875] pnp 00:12: [mem 0x00100000-0x7fffffff]
[    0.382877] pnp 00:12: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.382936] system 00:12: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.382940] system 00:12: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.382942] system 00:12: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.382945] system 00:12: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.382949] system 00:12: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.383071] pnp: PnP ACPI: found 19 devices
[    0.383073] ACPI: ACPI bus type pnp unregistered
[    0.383077] PnPBIOS: Disabled by ACPI PNP
[    0.421119] PCI: max bus depth: 1 pci_try_num: 2
[    0.421160] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.421164] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.421167] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.421171] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.421174] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.421177] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.421181] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.421184] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.421189] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.421192] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.421197] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff]
[    0.421201] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.421206] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.421209] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.421214] pci 0000:00:1c.1:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.421218] pci 0000:00:1c.1:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.421224] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.421251] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.421255] pci 0000:00:01.0: setting latency timer to 64
[    0.421261] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.421265] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.421269] pci 0000:00:1c.0: setting latency timer to 64
[    0.421279] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.421282] pci 0000:00:1c.1: setting latency timer to 64
[    0.421289] pci 0000:00:1e.0: setting latency timer to 64
[    0.421293] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.421295] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.421297] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421300] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421302] pci_bus 0000:00: resource 8 [mem 0x80000000-0xffffffff]
[    0.421305] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.421307] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[    0.421310] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.421312] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.421315] pci_bus 0000:03: resource 1 [mem 0x80200000-0x803fffff]
[    0.421317] pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.421319] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.421322] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.421324] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.421327] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.421329] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.421331] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.421334] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.421336] pci_bus 0000:04: resource 8 [mem 0x80000000-0xffffffff]
[    0.421384] NET: Registered protocol family 2
[    0.421459] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.421682] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.422129] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.422357] TCP: Hash tables configured (established 131072 bind 65536)
[    0.422359] TCP reno registered
[    0.422361] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.422370] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.422441] NET: Registered protocol family 1
[    0.422479] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.422496] pci 0000:00:1d.0: PCI INT A disabled
[    0.422506] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.422522] pci 0000:00:1d.1: PCI INT B disabled
[    0.422532] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.422547] pci 0000:00:1d.2: PCI INT C disabled
[    0.422554] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.422571] pci 0000:00:1d.3: PCI INT D disabled
[    0.422578] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.422603] pci 0000:00:1d.7: PCI INT A disabled
[    0.422629] pci 0000:01:00.0: Boot video device
[    0.422634] PCI: CLS 32 bytes, default 64
[    0.423115] audit: initializing netlink socket (disabled)
[    0.423123] type=2000 audit(1350825768.416:1): initialized
[    0.444379] highmem bounce pool size: 64 pages
[    0.444384] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.446470] VFS: Disk quotas dquot_6.5.2
[    0.446529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.447110] fuse init (API version 7.17)
[    0.447217] msgmni has been set to 1685
[    0.447782] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.447818] io scheduler noop registered
[    0.447820] io scheduler deadline registered
[    0.447830] io scheduler cfq registered (default)
[    0.447937] pcieport 0000:00:01.0: setting latency timer to 64
[    0.447968] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.448031] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.448068] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.448126] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.448161] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.448243] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.448268] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.448347] intel_idle: MWAIT substates: 0x20
[    0.448349] intel_idle: does not run on family 6 model 15
[    0.448432] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.448438] ACPI: Power Button [PWRB]
[    0.448484] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.448487] ACPI: Power Button [PWRF]
[    0.450145] ERST: Table is not found!
[    0.450147] GHES: HEST is not enabled!
[    0.450244] isapnp: Scanning for PnP cards...
[    0.450275] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.470618] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.610606] Freeing initrd memory: 13828k freed
[    0.803184] isapnp: No Plug & Play device found
[    0.928661] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.964395] Linux agpgart interface v0.103
[    0.966662] brd: module loaded
[    0.967765] loop: module loaded
[    0.967931] ata_piix 0000:00:1f.1: version 2.13
[    0.967945] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.967982] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.968328] scsi0 : ata_piix
[    0.968443] scsi1 : ata_piix
[    0.969477] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.969480] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.969501] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.969506] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.969549] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.969882] scsi2 : ata_piix
[    0.969975] scsi3 : ata_piix
[    0.971173] ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 19
[    0.971176] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 19
[    0.971561] Fixed MDIO Bus: probed
[    0.971581] tun: Universal TUN/TAP device driver, 1.6
[    0.971583] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.971669] PPP generic driver version 2.4.2
[    0.971804] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.971832] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.971843] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.971847] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.971898] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.971914] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.971924] ehci_hcd 0000:00:1d.7: debug port 1
[    0.975790] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.975806] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9ffbc00
[    0.988023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.988214] hub 1-0:1.0: USB hub found
[    0.988219] hub 1-0:1.0: 8 ports detected
[    0.988295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988310] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988326] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.988332] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.988335] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.988405] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.988432] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c480
[    0.988590] hub 2-0:1.0: USB hub found
[    0.988594] hub 2-0:1.0: 2 ports detected
[    0.988658] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.988665] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.988668] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.988739] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.988765] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.988923] hub 3-0:1.0: USB hub found
[    0.988927] hub 3-0:1.0: 2 ports detected
[    0.988988] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.988994] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.988997] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.989069] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.989108] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c880
[    0.989265] hub 4-0:1.0: USB hub found
[    0.989269] hub 4-0:1.0: 2 ports detected
[    0.989330] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.989336] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.989339] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.989408] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.989442] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[    0.989602] hub 5-0:1.0: USB hub found
[    0.989606] hub 5-0:1.0: 2 ports detected
[    0.989709] usbcore: registered new interface driver libusual
[    0.989770] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.992482] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.992490] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.992646] mousedev: PS/2 mouse device common for all mice
[    0.992788] rtc_cmos 00:03: RTC can wake from S4
[    0.992883] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.992905] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.992971] device-mapper: uevent: version 1.0.3
[    0.993039] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.993083] EISA: Probing bus 0 at eisa.0
[    0.993085] EISA: Cannot allocate resource for mainboard
[    0.993087] Cannot allocate resource for EISA slot 1
[    0.993089] Cannot allocate resource for EISA slot 2
[    0.993091] Cannot allocate resource for EISA slot 3
[    0.993093] Cannot allocate resource for EISA slot 4
[    0.993094] Cannot allocate resource for EISA slot 5
[    0.993096] Cannot allocate resource for EISA slot 6
[    0.993098] Cannot allocate resource for EISA slot 7
[    0.993100] Cannot allocate resource for EISA slot 8
[    0.993101] EISA: Detected 0 cards.
[    0.993110] cpufreq-nforce2: No nForce2 chipset.
[    0.993112] cpuidle: using governor ladder
[    0.993114] cpuidle: using governor menu
[    0.993116] EFI Variables Facility v0.08 2004-May-17
[    0.993370] TCP cubic registered
[    0.993486] NET: Registered protocol family 10
[    0.994021] NET: Registered protocol family 17
[    0.994025] Registering the dns_resolver key type
[    0.994047] Using IPI No-Shortcut mode
[    0.994144] PM: Hibernation image not present or could not be loaded.
[    0.994155] registered taskstats version 1
[    1.001205]   Magic number: 0:803:382
[    1.001296] rtc_cmos 00:03: setting system clock to 2012-10-21 13:22:49 UTC (1350825769)
[    1.001825] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.001827] EDD information not available.
[    1.019042] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.124278] ata4.01: NODEV after polling detection
[    1.132119] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL02, max UDMA/100
[    1.135400] ata3.00: ATA-8: ST3500820AS, SD25, max UDMA/133
[    1.135404] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.148244] ata4.00: configured for UDMA/100
[    1.148578] ata3.00: configured for UDMA/133
[    1.148753] scsi 2:0:0:0: Direct-Access     ATA      ST3500820AS      SD25 PQ: 0 ANSI: 5
[    1.148905] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.148912] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.148951] sd 2:0:0:0: [sda] Write Protect is off
[    1.148954] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.148980] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.156801] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL02 PQ: 0 ANSI: 5
[    1.165938] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.165943] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.166114] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.166200] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.249444]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    1.250138] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.250247] Freeing unused kernel memory: 740k freed
[    1.250533] Write protecting the kernel text: 5820k
[    1.250563] Write protecting the kernel read-only data: 2376k
[    1.250565] NX-protecting the kernel data: 4420k
[    1.267120] udevd[103]: starting version 175
[    1.291402] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.291414] ATL1E 0000:02:00.0: setting latency timer to 64
[    1.300074] usb 1-2: new high-speed USB device number 2 using ehci_hcd
[    1.305727] Floppy drive(s): fd0 is 1.44M
[    1.323754] FDC 0 is a post-1991 82077
[    1.420040] Refined TSC clocksource calibration: 2399.536 MHz.
[    1.420046] Switching to clocksource tsc
[    1.439371] usb 1-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[    1.880040] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    2.379622] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[    5.448312] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.624173] udevd[419]: starting version 175
[    5.712884] Adding 3906556k swap on /dev/sda9.  Priority:-1 extents:1 across:3906556k 
[    6.502246] lp: driver loaded but no devices found
[    6.630043] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro
[    6.808272] parport_pc 00:07: reported by Plug and Play ACPI
[    6.808382] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    6.904160] lp0: using parport0 (interrupt-driven).
[    6.944804] ppdev: user-space parallel port driver
[    7.140188] intel_rng: FWH not detected
[    7.320359] leds_ss4200: no LED devices found
[    8.014180] psmouse serio1: logips2pp: Detected unknown Logitech mouse model 106
[    8.213072] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.213119] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    8.213147] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    8.283549] Bluetooth: Core ver 2.16
[    8.283569] NET: Registered protocol family 31
[    8.283571] Bluetooth: HCI device and connection manager initialized
[    8.283574] Bluetooth: HCI socket layer initialized
[    8.283576] Bluetooth: L2CAP socket layer initialized
[    8.283581] Bluetooth: SCO socket layer initialized
[    8.318566] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    8.318748] usbcore: registered new interface driver btusb
[    8.512604] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[    8.532664] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    8.532759] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    8.532839] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    8.532922] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    8.532999] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    8.533078] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    8.533156] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    8.533231] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    8.618164] nvidia: module license 'NVIDIA' taints kernel.
[    8.618167] Disabling lock debugging due to kernel taint
[    9.101809] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.101818] nvidia 0000:01:00.0: setting latency timer to 64
[    9.101828] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.101943] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.35  Thu May 31 12:00:16 PDT 2012
[   10.788814] type=1400 audit(1350805979.283:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=629 comm="apparmor_parser"
[   10.788824] type=1400 audit(1350805979.283:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=628 comm="apparmor_parser"
[   10.789219] type=1400 audit(1350805979.283:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=629 comm="apparmor_parser"
[   10.789229] type=1400 audit(1350805979.283:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   10.789459] type=1400 audit(1350805979.283:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   10.789467] type=1400 audit(1350805979.283:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=629 comm="apparmor_parser"
[   11.991247] type=1400 audit(1350805980.487:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=710 comm="apparmor_parser"
[   12.617587] type=1400 audit(1350805981.111:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=740 comm="apparmor_parser"
[   12.618069] type=1400 audit(1350805981.111:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=740 comm="apparmor_parser"
[   12.799208] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.799211] Bluetooth: BNEP filters: protocol multicast
[   12.853855] Bluetooth: RFCOMM TTY layer initialized
[   12.853860] Bluetooth: RFCOMM socket layer initialized
[   12.853862] Bluetooth: RFCOMM ver 1.11
[   13.166387] type=1400 audit(1350805981.663:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=709 comm="apparmor_parser"
[   13.612982] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   13.612985] vesafb: scrolling: redraw
[   13.612987] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   13.616009] vesafb: framebuffer at 0xfb000000, mapped to 0xf8680000, using 1216k, total 1216k
[   13.616247] Console: switching to colour frame buffer device 80x30
[   13.616260] fb0: VESA VGA frame buffer device
[   15.912761] init: failsafe main process (766) killed by TERM signal
[   16.773644] type=1400 audit(1350805985.267:12): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=864 comm="apparmor_parser"
[   16.774065] type=1400 audit(1350805985.267:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=864 comm="apparmor_parser"
[   16.774295] type=1400 audit(1350805985.267:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=864 comm="apparmor_parser"
[   16.777511] type=1400 audit(1350805985.271:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=868 comm="apparmor_parser"
[   16.778006] type=1400 audit(1350805985.271:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=868 comm="apparmor_parser"
[   16.802955] type=1400 audit(1350805985.295:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=863 comm="apparmor_parser"
[   16.805310] type=1400 audit(1350805985.299:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=870 comm="apparmor_parser"
[   16.834384] type=1400 audit(1350805985.327:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=872 comm="apparmor_parser"
[   16.835522] type=1400 audit(1350805985.327:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=867 comm="apparmor_parser"
[   16.836007] type=1400 audit(1350805985.327:21): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=867 comm="apparmor_parser"
[   17.183425] ATL1E 0000:02:00.0: irq 44 for MSI/MSI-X
[   17.183553] ATL1E 0000:02:00.0: eth0: NIC Link is Up <100 Mbps Full Duplex>
[   17.183633] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.183771] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.728018] eth0: no IPv6 routers present
[  228.333762] Linux video capture interface: v2.00
[  228.435670] IR NEC protocol handler initialized
[  228.472413] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[  228.478549] IR RC5(x) protocol handler initialized
[  228.484557] saa7134 ALSA driver for DMA sound loaded
[  228.484560] saa7134 ALSA: no saa7134 cards found
[  228.497245] IR RC6 protocol handler initialized
[  228.499087] IR JVC protocol handler initialized
[  228.505452] IR Sony protocol handler initialized
[  228.507566] IR MCE Keyboard/mouse protocol handler initialized
[  228.509610] lirc_dev: IR Remote Control driver registered, major 251 
[  228.518835] IR LIRC bridge handler initialized
[  457.887260] usb 1-2: USB disconnect, device number 2
[  461.224025] usb 1-2: new high-speed USB device number 4 using ehci_hcd
[  461.359427] usb 1-2: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256

---

### Post by bijeeshvs on 2012-11-04
Same story here. I tried almost every guide on the forums, still no luck 

Windows identifies this device as "Gadmei" and its probably an em28xx chip

---

### Post by bijeeshvs on 2012-11-04
I just opened the tuner, and these are the images 
can anybody help ?????????

---

### Post by bijeeshvs on 2012-11-05
Anyone ??

---

### Post by budhus on 2012-11-05
Hey Mate!

Try this link and installation. Hopefully everything should work!

Link: ***[http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)***

Regards,

Budhus

---

### Post by bijeeshvs on 2012-11-06
Thanks for the help mate, I already tried it......... not working

---

### Post by BicyclerBoy on 2012-11-06
A longshot ..
[http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380)
could be the same/similar h/w in a different form factor..

---

### Post by bijeeshvs on 2012-11-07
> **BicyclerBoy said:**
> A longshot ..
[http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV380)
could be the same/similar h/w in a different form factor..

This looks promising, Thank you

---

