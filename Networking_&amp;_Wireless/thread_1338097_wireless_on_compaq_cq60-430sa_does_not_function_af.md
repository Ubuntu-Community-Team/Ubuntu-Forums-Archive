---
title: "wireless on compaq cq60-430sa does not function after installing windows"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by jonnywombat on 2009-11-26
Hi There...

I have a compac cq60-430sa laptop which I have had only a couple for a few weeks. Ever since I had it I reformatted the HDD and have been using Karmic 64bit without issue. Wireless has worked correctly "out of the box".

Last night I was playing around, and after getting frustrated with flakey usb support in virtual box I decided to install XP in a dual boot with Karmic.

I installed XP and as expected not much worked, I did not even have any ethernet to connect to the net with. I kind of expected this so I re installed karmic to fix grub (direct and not from a live session, and keeping the same /home partition), and then prepared to download the windows drivers I needed.

However when I rebooted into karmic my wireless no longer worked. The network manager shows that wireless is enabled, but disconnected and it cannot see my network.

Ethernet works fine, and a usb wireless stick works fine too.

I nuked my HDD, removing windows, fresh install of Karmic into a fresh / partition, but again keeping my old /home partition... rebooted and wireless was still the same.

I have also tried live sessions in both karmic 64 and 32 bit editions (both of which worked flawlessly before) and wireless is exactly the same.

As it was the early hours I decided to get some sleep. I removed the battery and power supply thinking a good long power down might help, but things are still the same.

lspci returns

> jonny@jonny-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
 

iwconfig wlan0 returns

> jonny@jonny-laptop:~$ iwconfig wlan0
wlan0     No such device

dmesg returns

> [    0.364424] pci 0000:00:14.0: PME# disabled
[    0.364656] pci 0000:00:08.0: transparent bridge
[    0.364688] pci 0000:02:00.0: reg 10 32bit mmio: [0xc1000000-0xc1ffffff]
[    0.364697] pci 0000:02:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.364704] pci 0000:02:00.0: reg 1c 64bit mmio: [0xc4000000-0xc5ffffff]
[    0.364709] pci 0000:02:00.0: reg 24 io port: [0x4000-0x407f]
[    0.364715] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.364759] pci 0000:00:0b.0: bridge io port: [0x4000-0x4fff]
[    0.364762] pci 0000:00:0b.0: bridge 32bit mmio: [0xc1000000-0xc1ffffff]
[    0.364767] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xc4000000-0xdfffffff]
[    0.364821] pci 0000:07:00.0: reg 10 64bit mmio: [0xc2000000-0xc200ffff]
[    0.364954] pci 0000:00:14.0: bridge 32bit mmio: [0xc2000000-0xc20fffff]
[    0.364993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.365110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.365217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.388023] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.388206] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.388385] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.388564] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.388743] ACPI: PCI Interrupt Link [Z012] (IRQs 19 20 21 22 23) *10
[    0.388921] ACPI: PCI Interrupt Link [Z013] (IRQs 19 20 21 22 23) *0, disabled.
[    0.389100] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled.
[    0.389282] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled.
[    0.389460] ACPI: PCI Interrupt Link [LSMB] (IRQs 18) *10
[    0.389633] ACPI: PCI Interrupt Link [LUS0] (IRQs 17) *11
[    0.389808] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7
[    0.390009] ACPI: PCI Interrupt Link [LMAC] (IRQs 19 20 21 22 23) *11
[    0.390189] ACPI: PCI Interrupt Link [LAZA] (IRQs 19 20 21 22 23) *10
[    0.390368] ACPI: PCI Interrupt Link [LGPU] (IRQs 19 20 21 22 23) *10
[    0.390547] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled.
[    0.390725] ACPI: PCI Interrupt Link [LSI0] (IRQs 19 20 21 22 23) *11
[    0.390904] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled.
[    0.391084] ACPI: PCI Interrupt Link [Z010] (IRQs 16) *5
[    0.391267] ACPI: PCI Interrupt Link [Z011] (IRQs 16) *10
[    0.391445] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[    0.391635] SCSI subsystem initialized
[    0.391655] libata version 3.00 loaded.
[    0.391655] usbcore: registered new interface driver usbfs
[    0.391655] usbcore: registered new interface driver hub
[    0.391655] usbcore: registered new device driver usb
[    0.391655] ACPI: WMI: Mapper loaded
[    0.391655] PCI: Using ACPI for IRQ routing
[    0.420007] Bluetooth: Core ver 2.15
[    0.420015] NET: Registered protocol family 31
[    0.420017] Bluetooth: HCI device and connection manager initialized
[    0.420020] Bluetooth: HCI socket layer initialized
[    0.420023] NetLabel: Initializing
[    0.420025] NetLabel:  domain hash size = 128
[    0.420026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420041] NetLabel:  unlabeled traffic allowed by default
[    0.420098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.420103] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.440014] Switched to high resolution mode on CPU 0
[    0.440655] Switched to high resolution mode on CPU 1
[    0.462665] pnp: PnP ACPI init
[    0.462685] ACPI: bus type pnp registered
[    0.471490] pnp: PnP ACPI: found 12 devices
[    0.471493] ACPI: ACPI bus type pnp unregistered
[    0.471505] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.471513] system 00:03: ioport range 0x360-0x361 has been reserved
[    0.471516] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.471519] system 00:03: iomem range 0xff800000-0xff800fff has been reserved
[    0.471526] system 00:0a: ioport range 0x1000-0x107f has been reserved
[    0.471529] system 00:0a: ioport range 0x1080-0x10ff has been reserved
[    0.471532] system 00:0a: ioport range 0x1200-0x127f has been reserved
[    0.471535] system 00:0a: ioport range 0x1280-0x12ff has been reserved
[    0.471538] system 00:0a: ioport range 0x1400-0x147f has been reserved
[    0.471541] system 00:0a: ioport range 0x1480-0x14ff has been reserved
[    0.471546] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.471550] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.471553] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.471556] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.471559] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.476257] AppArmor: AppArmor Filesystem Enabled
[    0.476311] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.476313] pci 0000:00:08.0:   IO window: disabled
[    0.476318] pci 0000:00:08.0:   MEM window: disabled
[    0.476321] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.476329] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.476332] pci 0000:00:0b.0:   IO window: 0x4000-0x4fff
[    0.476337] pci 0000:00:0b.0:   MEM window: 0xc1000000-0xc1ffffff
[    0.476341] pci 0000:00:0b.0:   PREFETCH window: 0x000000c4000000-0x000000dfffffff
[    0.476570] pci 0000:00:14.0: PCI bridge, secondary bus 0000:07
[    0.476572] pci 0000:00:14.0:   IO window: disabled
[    0.476583] pci 0000:00:14.0:   MEM window: 0xc2000000-0xc20fffff
[    0.476591] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.476605] pci 0000:00:08.0: setting latency timer to 64
[    0.476613] pci 0000:00:0b.0: setting latency timer to 64
[    0.476937] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23
[    0.476941]   alloc irq_desc for 23 on node -1
[    0.476944]   alloc kstat_irqs on node -1
[    0.476954] pci 0000:00:14.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[    0.476963] pci 0000:00:14.0: setting latency timer to 64
[    0.476971] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.476973] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.476976] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.476979] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.476982] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.476984] pci_bus 0000:02: resource 1 mem: [0xc1000000-0xc1ffffff]
[    0.476987] pci_bus 0000:02: resource 2 pref mem [0xc4000000-0xdfffffff]
[    0.476990] pci_bus 0000:07: resource 1 mem: [0xc2000000-0xc20fffff]
[    0.477034] NET: Registered protocol family 2
[    0.477226] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.478947] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.483692] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.484243] TCP: Hash tables configured (established 524288 bind 65536)
[    0.484247] TCP reno registered
[    0.484355] NET: Registered protocol family 1
[    0.484432] Trying to unpack rootfs image as initramfs...
[    0.673946] Freeing initrd memory: 7685k freed
[    0.678194] Simple Boot Flag at 0x38 set to 0x1
[    0.678387] Scanning for low memory corruption every 60 seconds
[    0.678533] audit: initializing netlink socket (disabled)
[    0.678548] type=2000 audit(1259225505.672:1): initialized
[    0.687733] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.689227] VFS: Disk quotas dquot_6.5.2
[    0.689281] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.689936] fuse init (API version 7.12)
[    0.690019] msgmni has been set to 7419
[    0.690311] alg: No test for stdrng (krng)
[    0.690326] io scheduler noop registered
[    0.690329] io scheduler anticipatory registered
[    0.690331] io scheduler deadline registered
[    0.690371] io scheduler cfq registered (default)
[    0.690647] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.690770] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.690905] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.691046] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    0.691190] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.691268] pci 0000:02:00.0: Boot video device
[    0.691601]   alloc irq_desc for 24 on node -1
[    0.691604]   alloc kstat_irqs on node -1
[    0.691626] pcieport-driver 0000:00:14.0: irq 24 for MSI/MSI-X
[    0.691648] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    0.691827] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.691851] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.695477] ACPI: AC Adapter [ADP1] (on-line)
[    0.695545] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.695549] ACPI: Power Button [PWRF]
[    0.695603] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.698789] ACPI: Lid Switch [LID0]
[    0.698833] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.698839] ACPI: Sleep Button [SLPB]
[    0.698897] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    0.698900] ACPI: Power Button [PWRB]
[    0.699170] processor LNXCPU:00: registered as cooling_device0
[    0.699203] processor LNXCPU:01: registered as cooling_device1
[    0.740936] thermal LNXTHERM:01: registered as thermal_zone0
[    0.740944] ACPI: Thermal Zone [TZS0] (53 C)
[    0.754795] thermal LNXTHERM:02: registered as thermal_zone1
[    0.754802] ACPI: Thermal Zone [TZS1] (51 C)
[    0.756090] Linux agpgart interface v0.103
[    0.756105] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.757275] brd: module loaded
[    0.757722] loop: module loaded
[    0.757809] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.757898] ahci 0000:00:09.0: version 3.0
[    0.758268] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 22
[    0.758274]   alloc irq_desc for 22 on node -1
[    0.758276]   alloc kstat_irqs on node -1
[    0.758288] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 22 (level, low) -> IRQ 22
[    0.758345]   alloc irq_desc for 25 on node -1
[    0.758347]   alloc kstat_irqs on node -1
[    0.758356] ahci 0000:00:09.0: irq 25 for MSI/MSI-X
[    0.758402] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl IDE mode
[    0.758406] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.758411] ahci 0000:00:09.0: setting latency timer to 64
[    0.758632] scsi0 : ahci
[    0.759343] scsi1 : ahci
[    0.759420] ata1: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004100 irq 25
[    0.759423] ata2: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004180 irq 25
[    0.759714] pata_amd 0000:00:06.0: version 0.4.1
[    0.759756] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.760227] scsi2 : pata_amd
[    0.760314] scsi3 : pata_amd
[    0.760353] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    0.760356] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    0.761051] Fixed MDIO Bus: probed
[    0.761197] PPP generic driver version 2.4.2
[    0.761313] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.761659] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17
[    0.761664]   alloc irq_desc for 17 on node -1
[    0.761666]   alloc kstat_irqs on node -1
[    0.761677] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17
[    0.761699] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.761702] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.761764] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.761800] ehci_hcd 0000:00:02.1: debug port 1
[    0.761805] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.761827] ehci_hcd 0000:00:02.1: irq 17, io mem 0xc0007000
[    0.764994] ACPI: Battery Slot [BAT0] (battery absent)
[    0.782686] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.782771] usb usb1: configuration #1 chosen from 1 choice
[    0.782801] hub 1-0:1.0: USB hub found
[    0.782812] hub 1-0:1.0: 3 ports detected
[    0.783162] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16
[    0.783165]   alloc irq_desc for 16 on node -1
[    0.783167]   alloc kstat_irqs on node -1
[    0.783177] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z011] -> GSI 16 (level, low) -> IRQ 16
[    0.783190] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.783193] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.783229] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.783263] ehci_hcd 0000:00:04.1: debug port 1
[    0.783268] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.783288] ehci_hcd 0000:00:04.1: irq 16, io mem 0xc0007400
[    0.800568] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.800634] usb usb2: configuration #1 chosen from 1 choice
[    0.800660] hub 2-0:1.0: USB hub found
[    0.800667] hub 2-0:1.0: 4 ports detected
[    0.800726] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.801037] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    0.801041] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    0.801052] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.801055] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.801093] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.801107] ohci_hcd 0000:00:02.0: irq 17, io mem 0xc0006000
[    0.862337] usb usb3: configuration #1 chosen from 1 choice
[    0.862362] hub 3-0:1.0: USB hub found
[    0.862372] hub 3-0:1.0: 3 ports detected
[    0.862721] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16
[    0.862725] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z010] -> GSI 16 (level, low) -> IRQ 16
[    0.862737] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.862740] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.862772] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.862784] ohci_hcd 0000:00:04.0: irq 16, io mem 0xc0008000
[    0.922363] usb usb4: configuration #1 chosen from 1 choice
[    0.922388] hub 4-0:1.0: USB hub found
[    0.922397] hub 4-0:1.0: 4 ports detected
[    0.922457] uhci_hcd: USB Universal Host Controller Interface driver
[    0.922589] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.940867] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.952577] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.952585] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.952588] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.952591] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.952595] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.952665] mice: PS/2 mouse device common for all mice
[    0.952807] rtc_cmos 00:06: RTC can wake from S4
[    0.952848] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.952905] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.953003] device-mapper: uevent: version 1.0.3
[    0.953114] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.953182] device-mapper: multipath: version 1.1.0 loaded
[    0.953186] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.953344] cpuidle: using governor ladder
[    0.953347] cpuidle: using governor menu
[    0.953775] TCP cubic registered
[    0.953909] NET: Registered protocol family 10
[    0.954344] lo: Disabled Privacy Extensions
[    0.954618] NET: Registered protocol family 17
[    0.954642] Bluetooth: L2CAP ver 2.13
[    0.954644] Bluetooth: L2CAP socket layer initialized
[    0.954647] Bluetooth: SCO (Voice Link) ver 0.6
[    0.954649] Bluetooth: SCO socket layer initialized
[    0.954709] Bluetooth: RFCOMM TTY layer initialized
[    0.954716] Bluetooth: RFCOMM socket layer initialized
[    0.954717] Bluetooth: RFCOMM ver 1.11
[    0.954740] powernow-k8: Found 1 AMD Turion Dual-Core RM-72 processors (2 cpu cores) (version 2.20.00)
[    0.954788] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.954791] powernow-k8:    1 : pstate 1 (1050 MHz)
[    0.954793] powernow-k8:    2 : pstate 2 (525 MHz)
[    0.956059] PM: Resume from disk failed.
[    0.956078] registered taskstats version 1
[    0.956224]   Magic number: 1:172:878
[    0.956364] rtc_cmos 00:06: setting system clock to 2009-11-26 08:51:47 UTC (1259225507)
[    0.956367] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.956369] EDD information not available.
[    0.976244] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.000335] Clocksource tsc unstable (delta = 4397484128212 ns)
[    1.100019] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.272095] usb 1-1: configuration #1 chosen from 1 choice
[    1.290034] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.290050] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.291817] ata2.00: ATA-8: ST9250315AS, 0003HPM1, max UDMA/100
[    1.291821] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.294158] ata2.00: configured for UDMA/100
[    1.303723] ata1.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    1.317258] ata1.00: configured for UDMA/100
[    1.319121] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    1.325721] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.325725] Uniform CD-ROM driver Revision: 3.20
[    1.325827] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.325873] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.325956] scsi 1:0:0:0: Direct-Access     ATA      ST9250315AS      0003 PQ: 0 ANSI: 5
[    1.326057] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.326101] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.326147] sd 1:0:0:0: [sda] Write Protect is off
[    1.326150] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.326174] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.326297]  sda:
[    1.326374] ata4: port disabled. ignoring.
[    1.330746]  sda1 sda2 < sda5 sda6 >
[    1.379074] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.379093] Freeing unused kernel memory: 660k freed
[    1.379431] Write protecting the kernel read-only data: 7580k
[    1.392538] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.510354] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.510733] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.510738]   alloc irq_desc for 21 on node -1
[    1.510741]   alloc kstat_irqs on node -1
[    1.510754] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.510760] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.588772] usb 2-2: configuration #1 chosen from 1 choice
[    1.626774] Initializing USB Mass Storage driver...
[    1.627206] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.627374] usbcore: registered new interface driver usb-storage
[    1.627378] USB Mass Storage support registered.
[    1.627452] acpi device:13: registered as cooling_device2
[    1.627585] usb-storage: device found at 2
[    1.627587] usb-storage: waiting for device to settle before scanning
[    1.627595] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/device:11/input/input6
[    1.627638] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.992801] usb 4-3: new low speed USB device using ohci_hcd and address 2
[    2.043859] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:16:d9:76:ac
[    2.043863] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt lnktim msi desc-v3
[    2.221410] usb 4-3: configuration #1 chosen from 1 choice
[    2.242603] usbcore: registered new interface driver hiddev
[    2.249706] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input7
[    2.249797] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.0-3/input0
[    2.249816] usbcore: registered new interface driver usbhid
[    2.249819] usbhid: v2.6:USB HID core driver
[    3.183559] PM: Starting manual resume from disk
[    3.183565] PM: Resume from partition 8:6
[    3.183567] PM: Checking hibernation image.
[    3.183842] PM: Resume from disk failed.
[    3.219963] EXT4-fs (sda1): barriers enabled
[    3.238283] kjournald2 starting: pid 398, dev sda1:8, commit interval 5 seconds
[    3.238309] EXT4-fs (sda1): delayed allocation enabled
[    3.238313] EXT4-fs: file extents enabled
[    3.249167] EXT4-fs: mballoc enabled
[    3.249185] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.895618] type=1505 audit(1259225510.436:2): operation="profile_load" pid=421 name=/usr/share/gdm/guest-session/Xsession
[    3.898884] type=1505 audit(1259225510.436:3): operation="profile_load" pid=422 name=/sbin/dhclient3
[    3.899174] type=1505 audit(1259225510.436:4): operation="profile_load" pid=422 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.899337] type=1505 audit(1259225510.436:5): operation="profile_load" pid=422 name=/usr/lib/connman/scripts/dhclient-script
[    3.932864] type=1505 audit(1259225510.476:6): operation="profile_load" pid=423 name=/usr/bin/evince
[    3.937429] type=1505 audit(1259225510.476:7): operation="profile_load" pid=423 name=/usr/bin/evince-previewer
[    3.940167] type=1505 audit(1259225510.476:8): operation="profile_load" pid=423 name=/usr/bin/evince-thumbnailer
[    3.960272] type=1505 audit(1259225510.496:9): operation="profile_load" pid=425 name=/usr/lib/cups/backend/cups-pdf
[    5.118613] Adding 1518100k swap on /dev/sda6.  Priority:-1 extents:1 across:1518100k 
[    5.236392] udev: starting version 147
[    6.069812] Linux video capture interface: v2.00
[    6.080867] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    6.182591] cfg80211: Calling CRDA to update world regulatory domain
[    6.197382] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    6.197451] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    6.197454] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    6.197457] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    6.197459]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    6.197460]     Might be a BIOS bug, if BIOS says ECC is enabled
[    6.197461]     Use of the override can cause unknown side effects.
[    6.197471] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.358550] uvcvideo: Found UVC 1.00 device HP Webcam-101 (0c45:62c0)
[    6.451296] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[    6.451320] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[    6.455302] lp: driver loaded but no devices found
[    6.456778] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.482077] input: HP Webcam-101 as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8
[    6.482138] usbcore: registered new interface driver uvcvideo
[    6.482142] USB Video Class driver (v0.1.0)
[    6.630365] usb-storage: device scan complete
[    6.632825] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.633255] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.640821] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.316445] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000
[    7.376753] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
[    7.473520] EXT4-fs (sda1): internal journal on sda1:8
[    7.913099] nvidia: module license 'NVIDIA' taints kernel.
[    7.913105] Disabling lock debugging due to kernel taint
[    8.169989] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 20
[    8.169996]   alloc irq_desc for 20 on node -1
[    8.169999]   alloc kstat_irqs on node -1
[    8.170025] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 20 (level, low) -> IRQ 20
[    8.170033] nvidia 0000:02:00.0: setting latency timer to 64
[    8.170342] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    8.351932] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.378333] ath_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[    8.378347] ath_pci 0000:07:00.0: setting latency timer to 64
[    8.456047] cfg80211: World regulatory domain updated:
[    8.456052] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.456056] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.456058] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.456061] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.456064] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.456066] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.775311] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[    8.775318]   alloc irq_desc for 19 on node -1
[    8.775321]   alloc kstat_irqs on node -1
[    8.775335] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 19 (level, low) -> IRQ 19
[    8.775410] HDA Intel 0000:00:07.0: setting latency timer to 64
[    8.873281] MadWifi: ath_attach: Switching rfkill capability off.
[    8.876917] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[    8.881024] ath_pci: wifi0: Atheros 5424/2424: mem=0xc2000000, irq=23
[    9.137017] EXT4-fs (sda5): barriers enabled
[    9.137374] kjournald2 starting: pid 822, dev sda5:8, commit interval 5 seconds
[    9.137829] EXT4-fs (sda5): internal journal on sda5:8
[    9.137833] EXT4-fs (sda5): delayed allocation enabled
[    9.137836] EXT4-fs: file extents enabled
[    9.160411] EXT4-fs: mballoc enabled
[    9.160430] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   10.440136] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
[   10.440227] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
[   10.440300] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input12
[   10.517897] __ratelimit: 6 callbacks suppressed
[   10.517902] type=1505 audit(1259225517.053:12): operation="profile_replace" pid=903 name=/usr/share/gdm/guest-session/Xsession
[   10.520079] type=1505 audit(1259225517.063:13): operation="profile_replace" pid=904 name=/sbin/dhclient3
[   10.520371] type=1505 audit(1259225517.063:14): operation="profile_replace" pid=904 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.520542] type=1505 audit(1259225517.063:15): operation="profile_replace" pid=904 name=/usr/lib/connman/scripts/dhclient-script
[   10.525464] type=1505 audit(1259225517.063:16): operation="profile_replace" pid=905 name=/usr/bin/evince
[   10.530109] type=1505 audit(1259225517.073:17): operation="profile_replace" pid=905 name=/usr/bin/evince-previewer
[   10.532888] type=1505 audit(1259225517.073:18): operation="profile_replace" pid=905 name=/usr/bin/evince-thumbnailer
[   10.539050] type=1505 audit(1259225517.073:19): operation="profile_replace" pid=909 name=/usr/lib/cups/backend/cups-pdf
[   10.539410] type=1505 audit(1259225517.073:20): operation="profile_replace" pid=909 name=/usr/sbin/cupsd
[   10.541811] type=1505 audit(1259225517.083:21): operation="profile_replace" pid=910 name=/usr/sbin/tcpdump
[   13.178443] usplash:361 freeing invalid memtype ffffffffc5000000-ffffffffc5e00000
[   13.356687]   alloc irq_desc for 26 on node -1
[   13.356692]   alloc kstat_irqs on node -1
[   13.356705] forcedeth 0000:00:0a.0: irq 26 for MSI/MSI-X
[   14.102213] ppdev: user-space parallel port driver
[   23.852512] ath0: no IPv6 routers present
[   24.242525] eth0: no IPv6 routers present
jonny@jonny-laptop:~$ 


sorry about the length... but i'm kinda keen to get this solved

Many thanks

Jonny

---

### Post by coffeeaddict22 on 2009-11-26
Hi, 
Flakey USB in Virtualbox?  There's a catch with the repository version; if you install the PUEL version from the website it shouldn't be a problem.

wrt your wireless, can you post back the output of ```
nm-tool
``` and ```
lshw -C network
```

---

### Post by jonnywombat on 2009-11-26
Yeah I was using version 3.0.12 downloaded direct from virtualbox.org. Sometime when I started a virtual machine usb devices could be selected fine, other times they could not be selected, but that's another story.....

nm-tool returns

> jonny@jonny-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1F:16:D9:76:AC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:24:2C:2C:37:E2

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


lshw -C network returns

> jonny@jonny-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:d9:76:ac
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:2c:37:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff


Thanks for your help...

---

### Post by jonnywombat on 2009-11-26
I have also noticed that if you disable wireless in network manager then it will not enable again.

I am really stuck here, and it is beyond me why installing xp would stop my wireless working, especially after it had been removed, and searching here about is not revealing much :( And why after working flawlessly on live cd, does wireless not work using the very same cd?? It makes no sense to me.

The only plan I can think of (as a last resort) is to find all the xp drivers for my laptop and save them to a pendrive.

Format my HDD, totally nuke it.

Install XP and all drivers and see then if my wireless works again.

Then **IF** it works again in XP re-install Karmic as dual boot.


right i guess it's back to google for jonny

---

### Post by coffeeaddict22 on 2009-11-26
Hi,
You didn't turn off the wireless in Windows by any chance?

Another thing to check is whether you've got permissions- look in System/Administration/Users and Groups and make sure "Use Wireless" is checked.

What's the output of ```
route -n
```

---

### Post by jonnywombat on 2009-11-26
When I installed XP there was no driver installed for the wireless, in fact i did not even have ethernet.

Then wireless was not turned on let alone turned off, however there is a toggle button on the laptop for the wireless, which I can't remember pressing, but equally I cannot say for sure I did not press it. Assuming the device was "on" by default then it may be turned "off", but I can't say for certain it was 3am local time... I was tired and had had a few vodkas...lol. 
However I guess from the nature of the enquiry that it is at least feasible that windows turned the device off (either coz it could not talk to it, or coz I inadvertently toggled it off) and that this turn off is persistent. is this right?

ok now for the info..

route -n returns

> jonny@jonny-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jonny@jonny-laptop:~$ 


Thanks again for your time. 

Jonny

---

### Post by coffeeaddict22 on 2009-11-26
OK.  What about ```
sudo iwlist scan
```
nm-tool seems to imply the card is working OK, although the output of ```
ifconfig
``` would be nice to confirm that.

---

### Post by jonnywombat on 2009-11-27
iwlist scan returns

> jonny@jonny-laptop:~$ sudo iwlist scan
[sudo] password for jonny: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

jonny@jonny-laptop:~$ 

ifconfig returns

> jonny@jonny-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:d9:76:ac  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fed9:76ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:513883 (513.8 KB)  TX bytes:94863 (94.8 KB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:2c:37:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-2C-37-E2-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


thanks again.

if your ever in the uk i'll buy you a beer :p

---

### Post by coffeeaddict22 on 2009-11-27
Can you check your permissions?  System/Administration/Users and Groups; select your name and check that the box for "Use wireless" is checked.
What happens if you try ```
sudo ifconfig wlan0 up
```
And what's the output of ```
lsmod
```

---

### Post by jonnywombat on 2009-11-27
I checked the user thing, and the box for wireless was not checked, but my usb stick has been working fine, so I guess that don't mean much.

Wlan up did nothing obvious and did not cause my on board wireless to spring to life.

the output of lsmod is 

> jonny@jonny-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_conexant    25376  1 
joydev                 13088  0 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ath5k                 136680  0 
mac80211              210104  1 ath5k
led_class               5256  1 ath5k
ath                    10304  1 ath5k
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
nvidia              10316904  38 
psmouse                57124  0 
serio_raw               6596  0 
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
cfg80211              109144  3 ath5k,mac80211,ath
snd                    77096  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37756  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
parport                40528  2 ppdev,lp
i2c_nforce2             8168  0 
usbhid                 43968  0 
usb_storage            65984  0 
video                  23612  0 
output                  3680  1 video
forcedeth              61292  0 


I may not be around much this weekend as I am working from 8am saturday until 11pm sunday. I will take my laptop, and if oppurtunity arises I'll have a tinker.

Thanks for sticking with me mate, I think the time to try installing windows again, install the windows drivers and see if I can get it working that way is drawing nigh.

---

### Post by jonnywombat on 2009-11-30
Ok I have now figured this out... although I'm not 100% on what happened.

To fix I re installed windows xp and pressed the wireless toggle button ONCE.

Even tho no windows drivers were installed, and device manger did not even recognize the wireless, the toggle button evidently still functions. 

Why ubuntu cannot turn the device back on I don't know either, but I'm all fixed up now.

Thanks for your help

Jonny

---

### Post by coffeeaddict22 on 2009-11-30
I've lost the thread I saw it in, but on some laptops there's apparently a chip on the board that stores the hardware state; unfortunately it's unaccessible in Linux, so you can't modify the settings stored on the chip unless you're in the OS they were set in.  I don't understand it fully myself, but it's probably something along the lines in [this post]("http://ubuntuforums.org/showthread.php?t=1036051&page=20").

---

