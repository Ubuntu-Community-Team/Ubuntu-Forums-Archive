---
title: "Azurewave Wireless Non Existing in my LTSP"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by zenriko on 2013-07-08
Greets,

Attemping to intoduce Azurewave Wireless into my already established LTSP environment. The notebooks 1005P's which have a ar5b95 wireless card are not working only can connect through cable - no good.

> Get it from your product information - cmd not found
> ladmin@svr:~$ lspci -nn
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a3)
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: NVIDIA Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
ladmin@svr:~$ 


> ladmin@svr:~$ iwconfig wlan0
wlan0     No such device

ladmin@svr:~$ 


[spoiler]> [    0.192353] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.192419] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.192485] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.192551] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.192617] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
[    0.192686] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
[    0.192751] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
[    0.192817] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
[    0.192883] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[    0.192949] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
[    0.193015] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
[    0.193081] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
[    0.193147] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
[    0.193213] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
[    0.193279] ACPI: PCI Interrupt Link [APSJ] (IRQs 21) *0
[    0.193398] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.193402] vgaarb: loaded
[    0.193403] vgaarb: bridge control possible 0000:00:0d.0
[    0.193648] SCSI subsystem initialized
[    0.196137] libata version 3.00 loaded.
[    0.196137] ACPI: bus type usb registered
[    0.196137] usbcore: registered new interface driver usbfs
[    0.196137] usbcore: registered new interface driver hub
[    0.196137] usbcore: registered new device driver usb
[    0.196240] PCI: Using ACPI for IRQ routing
[    0.197666] PCI: pci_cache_line_size set to 64 bytes
[    0.197717] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.197720] e820: reserve RAM buffer [mem 0xb7ee0000-0xb7ffffff]
[    0.197838] NetLabel: Initializing
[    0.197839] NetLabel:  domain hash size = 128
[    0.197840] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197852] NetLabel:  unlabeled traffic allowed by default
[    0.197938] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.197944] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.197948] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.208072] Switching to clocksource hpet
[    0.216456] AppArmor: AppArmor Filesystem Enabled
[    0.216500] pnp: PnP ACPI init
[    0.216521] ACPI: bus type pnp registered
[    0.216663] pnp 00:00: [bus 00-ff]
[    0.216666] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.216668] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.216671] pnp 00:00: [io  0x0d00-0xffff window]
[    0.216673] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.216675] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.216677] pnp 00:00: [mem 0xc0000000-0xfebfffff window]
[    0.216762] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.216779] pnp 00:01: [io  0x1000-0x107f]
[    0.216781] pnp 00:01: [io  0x1080-0x10ff]
[    0.216784] pnp 00:01: [io  0x1400-0x147f]
[    0.216786] pnp 00:01: [io  0x1480-0x14ff]
[    0.216788] pnp 00:01: [io  0x1800-0x187f]
[    0.216790] pnp 00:01: [io  0x1880-0x18ff]
[    0.216851] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.216854] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.216857] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.216859] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.216862] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.216864] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.216867] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.216914] pnp 00:02: [io  0x0010-0x001f]
[    0.216916] pnp 00:02: [io  0x0022-0x003f]
[    0.216918] pnp 00:02: [io  0x0044-0x005f]
[    0.216920] pnp 00:02: [io  0x0062-0x0063]
[    0.216922] pnp 00:02: [io  0x0065-0x006f]
[    0.216924] pnp 00:02: [io  0x0074-0x007f]
[    0.216926] pnp 00:02: [io  0x0091-0x0093]
[    0.216928] pnp 00:02: [io  0x00a2-0x00bf]
[    0.216930] pnp 00:02: [io  0x00e0-0x00ef]
[    0.216933] pnp 00:02: [io  0x04d0-0x04d1]
[    0.216935] pnp 00:02: [io  0x0800-0x087f]
[    0.216937] pnp 00:02: [io  0x0294-0x0297]
[    0.216985] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.216988] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.216991] system 00:02: [io  0x0294-0x0297] has been reserved
[    0.216993] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.217008] pnp 00:03: [dma 4]
[    0.217010] pnp 00:03: [io  0x0000-0x000f]
[    0.217012] pnp 00:03: [io  0x0080-0x0090]
[    0.217015] pnp 00:03: [io  0x0094-0x009f]
[    0.217017] pnp 00:03: [io  0x00c0-0x00df]
[    0.217047] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.217090] pnp 00:04: [irq 0 disabled]
[    0.217108] pnp 00:04: [irq 8]
[    0.217111] pnp 00:04: [mem 0xfefff000-0xfefff3ff]
[    0.217138] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.217160] pnp 00:05: [io  0x0070-0x0073]
[    0.217188] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.217195] pnp 00:06: [io  0x0061]
[    0.217225] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.217234] pnp 00:07: [io  0x00f0-0x00ff]
[    0.217242] pnp 00:07: [irq 13]
[    0.217270] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.217369] pnp 00:08: [irq 12]
[    0.217403] pnp 00:08: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.217422] pnp 00:09: [io  0x0060]
[    0.217424] pnp 00:09: [io  0x0064]
[    0.217432] pnp 00:09: [irq 1]
[    0.217469] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.217927] pnp 00:0a: [mem 0xf0000000-0xf3ffffff]
[    0.217980] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.217983] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.217998] ACPI Error: Field [ASSM] at 524320 exceeds Buffer [BUF0] size 880 (bits) (20120320/dsopcode-236)
[    0.218003] ACPI Error: Method parse/execution failed [\_SB_.MEM_._CRS] (Node f702c0c0), AE_AML_BUFFER_LIMIT (20120320/psparse-536)
[    0.218010] ACPI Error: Method execution failed [\_SB_.MEM_._CRS] (Node f702c0c0), AE_AML_BUFFER_LIMIT (20120320/uteval-103)
[    0.218017] pnp 00:0b: can't evaluate _CRS: 12298
[    0.218071] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218080] pnp: PnP ACPI: found 12 devices
[    0.218082] ACPI: ACPI bus type pnp unregistered
[    0.218085] PnPBIOS: Disabled by ACPI PNP
[    0.254222] pci 0000:00:0d.0: BAR 6: assigned [mem 0xc0000000-0xc001ffff pref]
[    0.254227] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.254230] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.254234] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.254237] pci 0000:00:04.0:   bridge window [mem 0xfde00000-0xfdefffff pref]
[    0.254241] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.254244] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    0.254247] pci 0000:00:09.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.254250] pci 0000:00:09.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.254253] pci 0000:00:0b.0: PCI bridge to [bus 03-03]
[    0.254256] pci 0000:00:0b.0:   bridge window [io  0xc000-0xcfff]
[    0.254259] pci 0000:00:0b.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.254262] pci 0000:00:0b.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.254265] pci 0000:00:0c.0: PCI bridge to [bus 04-04]
[    0.254267] pci 0000:00:0c.0:   bridge window [io  0xb000-0xbfff]
[    0.254271] pci 0000:00:0c.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.254273] pci 0000:00:0c.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.254283] pci 0000:00:04.0: setting latency timer to 64
[    0.254291] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.254293] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.254296] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.254298] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.254300] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xfebfffff]
[    0.254303] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.254305] pci_bus 0000:01: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.254307] pci_bus 0000:01: resource 2 [mem 0xfde00000-0xfdefffff pref]
[    0.254310] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.254312] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.254314] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.254317] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000dffff]
[    0.254319] pci_bus 0000:01: resource 8 [mem 0xc0000000-0xfebfffff]
[    0.254321] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.254323] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.254326] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.254328] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.254331] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.254333] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.254336] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.254338] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.254340] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.254385] NET: Registered protocol family 2
[    0.254452] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.254681] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.255467] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.255928] TCP: Hash tables configured (established 131072 bind 65536)
[    0.255931] TCP: reno registered
[    0.255934] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.255949] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.256082] NET: Registered protocol family 1
[    0.256328] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.256484] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.256546] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256593] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256645] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256698] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256752] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256810] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256872] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256937] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.256945] pci 0000:00:0d.0: Boot video device
[    0.256953] PCI: CLS 32 bytes, default 64
[    0.257404] audit: initializing netlink socket (disabled)
[    0.257417] type=2000 audit(1373298403.252:1): initialized
[    0.278036] highmem bounce pool size: 64 pages
[    0.278049] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.279900] VFS: Disk quotas dquot_6.5.2
[    0.279947] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.280545] fuse init (API version 7.19)
[    0.280624] msgmni has been set to 1662
[    0.280955] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.280982] io scheduler noop registered
[    0.280984] io scheduler deadline registered (default)
[    0.280990] io scheduler cfq registered
[    0.281143] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.281195] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.281241] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.281298] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.281318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.281469] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.281475] ACPI: Power Button [PWRB]
[    0.281530] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.281532] ACPI: Power Button [PWRF]
[    0.281585] ACPI: Fan [FAN] (on)
[    0.284551] ACPI Warning: For \_TZ_.THRM._PSL: Return Package has no elements (empty) (20120320/nspredef-463)
[    0.284557] ACPI: [Package] has zero elements (f72fb440)
[    0.284558] ACPI: Invalid passive threshold
[    0.284755] thermal LNXTHERM:00: registered as thermal_zone0
[    0.284757] ACPI: Thermal Zone [THRM] (29 C)
[    0.284793] GHES: HEST is not enabled!
[    0.284924] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.286067] Linux agpgart interface v0.103
[    0.287567] brd: module loaded
[    0.288267] loop: module loaded
[    0.288615] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    0.288679] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.288815] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    0.288837] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.289162] Fixed MDIO Bus: probed
[    0.289215] tun: Universal TUN/TAP device driver, 1.6
[    0.289217] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.289262] PPP generic driver version 2.4.2
[    0.289304] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.289336] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.289339] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.289349] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.289376] ehci_hcd 0000:00:02.1: debug port 1
[    0.289381] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    0.289406] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.289445] isapnp: Scanning for PnP cards...
[    0.338298] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.338343] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.338346] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.338348] usb usb1: Product: EHCI Host Controller
[    0.338350] usb usb1: Manufacturer: Linux 3.5.0-34-generic ehci_hcd
[    0.338352] usb usb1: SerialNumber: 0000:00:02.1
[    0.338459] hub 1-0:1.0: USB hub found
[    0.338464] hub 1-0:1.0: 10 ports detected
[    0.338542] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.338567] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.338570] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.338575] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.338604] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[    0.427396] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.427398] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.427400] usb usb2: Product: OHCI Host Controller
[    0.427402] usb usb2: Manufacturer: Linux 3.5.0-34-generic ohci_hcd
[    0.427404] usb usb2: SerialNumber: 0000:00:02.0
[    0.514297] hub 2-0:1.0: USB hub found
[    0.514303] hub 2-0:1.0: 10 ports detected
[    0.514367] uhci_hcd: USB Universal Host Controller Interface driver
[    0.514430] usbcore: registered new interface driver libusual
[    0.514476] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.565614] Freeing initrd memory: 20580k freed
[    0.584129] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.584142] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.584321] mousedev: PS/2 mouse device common for all mice
[    0.584466] rtc_cmos 00:05: RTC can wake from S4
[    0.584623] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.584663] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.584736] device-mapper: uevent: version 1.0.3
[    0.584797] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.584823] EISA: Probing bus 0 at eisa.0
[    0.584827] EISA: Cannot allocate resource for mainboard
[    0.584829] Cannot allocate resource for EISA slot 1
[    0.584831] Cannot allocate resource for EISA slot 2
[    0.584833] Cannot allocate resource for EISA slot 3
[    0.584834] Cannot allocate resource for EISA slot 4
[    0.584836] Cannot allocate resource for EISA slot 5
[    0.584838] Cannot allocate resource for EISA slot 6
[    0.584839] Cannot allocate resource for EISA slot 7
[    0.584841] Cannot allocate resource for EISA slot 8
[    0.584842] EISA: Detected 0 cards.
[    0.584854] cpuidle: using governor ladder
[    0.584855] cpuidle: using governor menu
[    0.584857] EFI Variables Facility v0.08 2004-May-17
[    0.585075] ashmem: initialized
[    0.585206] TCP: cubic registered
[    0.585312] NET: Registered protocol family 10
[    0.585496] NET: Registered protocol family 17
[    0.585517] Key type dns_resolver registered
[    0.585567] Using IPI No-Shortcut mode
[    0.585642] PM: Hibernation image not present or could not be loaded.
[    0.585659] registered taskstats version 1
[    0.588158] Key type trusted registered
[    0.590174] Key type encrypted registered
[    0.592471]   Magic number: 5:433:790
[    0.592602] rtc_cmos 00:05: setting system clock to 2013-07-08 15:46:44 UTC (1373298404)
[    0.592647] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 5200B (2 cpu cores) (version 2.20.00)
[    0.592690] powernow-k8: fid 0x13 (2700 MHz), vid 0x9
[    0.592692] powernow-k8: fid 0x12 (2600 MHz), vid 0xa
[    0.592694] powernow-k8: fid 0x10 (2400 MHz), vid 0xc
[    0.592695] powernow-k8: fid 0xe (2200 MHz), vid 0xe
[    0.592697] powernow-k8: fid 0xc (2000 MHz), vid 0x10
[    0.592698] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    0.592699] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.592771] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.592772] EDD information not available.
[    0.646902] isapnp: No Plug & Play device found
[    0.646971] Freeing unused kernel memory: 760k freed
[    0.647539] Write protecting the kernel text: 6056k
[    0.647559] Write protecting the kernel read-only data: 2476k
[    0.647560] NX-protecting the kernel data: 4184k
[    0.668597] udevd[91]: starting version 175
[    0.723527] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.723723] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.723731] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.960020] usb 2-3: new low-speed USB device number 2 using ohci_hcd
[    1.176425] usb 2-3: New USB device found, idVendor=0a81, idProduct=0101
[    1.176431] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.176434] usb 2-3: Product: USB Keyboard
[    1.176436] usb 2-3: Manufacturer: CHESEN
[    1.200467] usbcore: registered new interface driver usbhid
[    1.200472] usbhid: USB HID core driver
[    1.203316] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input2
[    1.203415] hid-generic 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:02.0-3/input0
[    1.205523] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input3
[    1.205651] hid-generic 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:02.0-3/input1
[    1.248759] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:22:64:26:f7:88
[    1.248765] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.248814] sata_nv 0000:00:08.0: version 3.5
[    1.248902] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.249189] scsi0 : sata_nv
[    1.249490] scsi1 : sata_nv
[    1.249621] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf700 irq 20
[    1.249623] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 20
[    1.249682] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.249905] scsi2 : sata_nv
[    1.250158] scsi3 : sata_nv
[    1.250293] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf200 irq 21
[    1.250296] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf208 irq 21
[    1.570230] ata3: SATA link down (SStatus 0 SControl 300)
[    1.716040] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.724126] ata1.00: ATA-8: ST3500620AS, HP12, max UDMA/100
[    1.724129] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.740118] ata1.00: configured for UDMA/100
[    1.740287] scsi 0:0:0:0: Direct-Access     ATA      ST3500620AS      HP12 PQ: 0 ANSI: 5
[    1.740481] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.740507] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.740529] sd 0:0:0:0: [sda] Write Protect is off
[    1.740533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.740553] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.741231]  sda: sda1 sda2
[    1.741594] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.208034] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.216119] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653Q, HC01, max UDMA/100
[    2.232115] ata2.00: configured for UDMA/100
[    2.233045] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Q  HC01 PQ: 0 ANSI: 5
[    2.236838] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.236841] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.236956] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.237102] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.558219] ata4: SATA link down (SStatus 0 SControl 300)
[    3.824857] vesafb: mode is 2048x1536x32, linelength=8192, pages=0
[    3.824863] vesafb: scrolling: redraw
[    3.824866] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.825756] vesafb: framebuffer at 0xe0000000, mapped to 0xf8500000, using 12288k, total 12288k
[    3.825982] Console: switching to colour frame buffer device 256x96
[    3.826047] fb0: VESA VGA frame buffer device
[    4.037092] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   12.036963] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.077226] udevd[449]: starting version 175
[   12.123035] lp: driver loaded but no devices found
[   12.147963] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   12.148071] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   12.161556] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   12.382245] Bluetooth: Core ver 2.16
[   12.382368] NET: Registered protocol family 31
[   12.382370] Bluetooth: HCI device and connection manager initialized
[   12.382373] Bluetooth: HCI socket layer initialized
[   12.382375] Bluetooth: L2CAP socket layer initialized
[   12.382381] Bluetooth: SCO socket layer initialized
[   12.395534] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.395539] Bluetooth: BNEP filters: protocol multicast
[   12.399105] Bluetooth: RFCOMM TTY layer initialized
[   12.399116] Bluetooth: RFCOMM socket layer initialized
[   12.399117] Bluetooth: RFCOMM ver 1.11
[   12.401782] ppdev: user-space parallel port driver
[   12.429897] type=1400 audit(1373294816.333:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=703 comm="apparmor_parser"
[   12.432998] type=1400 audit(1373294816.337:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=703 comm="apparmor_parser"
[   12.445110] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   12.510654] type=1400 audit(1373294816.413:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=752 comm="apparmor_parser"
[   12.511129] type=1400 audit(1373294816.413:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=752 comm="apparmor_parser"
[   12.511367] type=1400 audit(1373294816.413:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=752 comm="apparmor_parser"
[   12.598539] nvidia: module license 'NVIDIA' taints kernel.
[   12.598547] Disabling lock debugging due to kernel taint
[   12.643661] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   12.643680] nvidia 0000:00:0d.0: setting latency timer to 64
[   12.643687] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.644433] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.88  Wed Mar 27 14:31:12 PDT 2013
[   12.661574] microcode: AMD CPU family 0xf not supported
[   12.731683] kvm: disabled by bios
[   12.761502] microcode: AMD CPU family 0xf not supported
[   12.769718] kvm: disabled by bios
[   12.836273] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   12.836283] hda_intel: Disabling MSI
[   12.836317] snd_hda_intel 0000:00:05.0: setting latency timer to 64
[   12.881927] init: failsafe main process (867) killed by TERM signal
[   12.990000] type=1400 audit(1373294816.893:7): apparmor="STATUS" operation="profile_load" name="lxc-container-default" pid=974 comm="apparmor_parser"
[   12.990816] type=1400 audit(1373294816.893:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=973 comm="apparmor_parser"
[   12.997122] type=1400 audit(1373294816.901:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=975 comm="apparmor_parser"
[   12.998769] type=1400 audit(1373294816.901:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=975 comm="apparmor_parser"
[   12.999016] type=1400 audit(1373294816.901:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=975 comm="apparmor_parser"
[   13.011152] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   13.011184] forcedeth 0000:00:07.0: eth0: MSI enabled
[   13.289851] init: alsa-restore main process (1034) terminated with status 19
[   13.307875] Bridge firewalling registered
[   13.335488] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.352363] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.471076] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   13.524021] hda_codec: ALC1200: SKU not ready 0x411111f0
[   13.539203] init: isc-dhcp-server main process (1078) terminated with status 1
[   13.539242] init: isc-dhcp-server main process ended, respawning
[   13.615414] init: isc-dhcp-server main process (1174) terminated with status 1
[   13.615457] init: isc-dhcp-server main process ended, respawning
[   13.675074] init: isc-dhcp-server main process (1181) terminated with status 1
[   13.675119] init: isc-dhcp-server main process ended, respawning
[   13.741435] init: isc-dhcp-server main process (1188) terminated with status 1
[   13.741482] init: isc-dhcp-server main process ended, respawning
[   13.801270] init: isc-dhcp-server main process (1195) terminated with status 1
[   13.801316] init: isc-dhcp-server main process ended, respawning
[   13.854316] init: isc-dhcp-server main process (1202) terminated with status 1
[   13.854350] init: isc-dhcp-server main process ended, respawning
[   13.903971] init: isc-dhcp-server main process (1209) terminated with status 1
[   13.904041] init: isc-dhcp-server main process ended, respawning
[   13.963157] init: isc-dhcp-server main process (1216) terminated with status 1
[   13.963192] init: isc-dhcp-server main process ended, respawning
[   14.020621] init: isc-dhcp-server main process (1227) terminated with status 1
[   14.020664] init: isc-dhcp-server main process ended, respawning
[   14.104289] init: isc-dhcp-server main process (1235) terminated with status 1
[   14.104326] init: isc-dhcp-server main process ended, respawning
[   14.180280] init: isc-dhcp-server main process (1313) terminated with status 1
[   14.180317] init: isc-dhcp-server respawning too fast, stopped
[   14.704243] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   14.704407] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   14.704542] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   14.704676] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   14.704815] input: HDA NVidia Line Out as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   14.991682] init: plymouth-stop pre-start process (1586) terminated with status 1
[  432.665290] audit_printk_skb: 60 callbacks suppressed
[  432.665304] type=1400 audit(1373295236.200:32): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=705 comm="cupsd" pid=705 comm="cupsd" capability=36  capname="block_suspend"
ladmin@svr:~$ ^C
ladmin@svr:~$ 

[/spoiler]

> ladmin@svr:~$ sudo lshw -c network
[sudo] password for ladmin: 
ladmin@svr:~$ iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lxcbr0    Interface doesn't support scanning.

ladmin@svr:~$ ^C
ladmin@svr:~$ 



> ladmin@svr:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS
ladmin@svr:~$ 


> ladmin@svr:~$ uname -mr
3.5.0-34-generic i686
ladmin@svr:~$ 



I just want to install the wireless and get it to work with edu/linux

---

### Post by chili555 on 2013-07-08
Is it a USB device? Please run and post:```
lsusb
```We see no Atheros in your lspci. Thanks.

---

### Post by zenriko on 2013-07-09
Hi,
Its is not a usb, it is a mini internal wireless card adapter.

Can i assume that any additional drivers are to be installed on the central LTS? which then I assume are available on the image which thin clients will use?
I cannot seem to install the driver (only have XP version) to install - probably why the card is not being detected~

Edit: I am writing these commands on the notebook in question - logged in as the admin account - is this effectively logging my session as on the server instead of the notebook - perhaps why the wlan does not exist?

(I am a linux nubee)

---

### Post by chili555 on 2013-07-09
> I am writing these commands on the notebook in question - logged in as the admin account - is this effectively logging my session as on the server instead of the notebook - perhaps why the wlan does not exist?
Frankly, I don't know. I am not an LTSP person; I am a wireless driver person. I do think it's vital to make sure you are logged in to the server and not merely reading information from the laptop. 

Regardless of whether your wireless card had an associated driver, it will show up in lspci, lsusb or, in the olden days, lspcmcia. > Can i assume that any additional drivers are to be installed on the central LTS? which then I assume are available on the image which thin clients will use?From what little I understand about LTSP, I certainly think so. Each terminal doesn't have its own presence on the network and its own distinct IP address, does it? Or are these actually fat clients?

There are wireless devices that are attached to internal USB buses. Do you mind if we have a peek anyway, just to narrow the possibilities??```
lsusb
sudo lshw -C network
```

---

### Post by zenriko on 2013-07-10
Ok, Running this cmd [sudo lshw -C network] I see the following:  DMI, CPUID, PCI (sysfs. It scrolls through these then ends.

lsusb

> ladmin@svr:~$ lsusb
Bus 002 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ladmin@svr:~$ 


---

### Post by praseodym on 2013-07-10
Did you reset the BIOS to default?

---

### Post by zenriko on 2013-07-10
> **praseodym said:**
> Did you reset the BIOS to default?

No, should I have done so?

---

### Post by praseodym on 2013-07-10
Yes, maybe its not recognized.

---

### Post by zenriko on 2013-07-15
Apologies for a delayed response I was out of office, I have reset the bios and redone the previous commands and still receive the same outcome.

---

