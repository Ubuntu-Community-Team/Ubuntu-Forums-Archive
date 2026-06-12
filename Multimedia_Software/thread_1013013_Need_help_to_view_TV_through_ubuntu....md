---
title: "Need help to view TV through ubuntu..."
date: 2008-12-16
forum: Multimedia Software
---

### Post by dimis80 on 2008-12-16
Friends, i have an AverMedia card installed on one PCI slot on my PC that I am trying to fix in order to have TV on my ubuntu OS.

I installed TV Time but when it is open a blue flash is showing and then... nothing but black screen.... i cannot search for channels, nothing..

I will post the codes below that might be of help...
code lspci -nn:
```
mitsakos@mitsakos-beast:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IB (ICH9) LPC Interface Controller [8086:2918] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller [8086:2921] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
05:01.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
05:02.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
05:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev c0)

```

and dmesg:
```
[    0.401578] pci 0000:05:03.0: PME# disabled
[    0.401608] pci 0000:00:1e.0: transparent bridge
[    0.401611] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.401613] PCI: bridge 0000:00:1e.0 32bit mmio: [f8000000, febfffff]
[    0.401632] bus 00 -> node 0
[    0.401636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.401821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.401904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.402045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.402132] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.402225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.416417] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.416417] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.416417] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.416429] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.416531] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.416633] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.416735] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.416838] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.416884] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 57, should be 4E [20080609]
[    0.416884] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.416884] pnp: PnP ACPI init
[    0.416884] ACPI: bus type pnp registered
[    0.420288] pnp: PnP ACPI: found 15 devices
[    0.420290] ACPI: ACPI bus type pnp unregistered
[    0.420292] PnPBIOS: Disabled by ACPI PNP
[    0.420301] PCI: Using ACPI for IRQ routing
[    0.428035] NET: Registered protocol family 8
[    0.428038] NET: Registered protocol family 20
[    0.428052] NetLabel: Initializing
[    0.428052] NetLabel:  domain hash size = 128
[    0.428052] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.428058] NetLabel:  unlabeled traffic allowed by default
[    0.428064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.428069] hpet0: 4 64-bit timers, 14318180 Hz
[    0.429656] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.429658]    actual entries 65620
[    0.429703] AppArmor: AppArmor Filesystem Enabled
[    0.429718] ACPI: RTC can wake from S4
[    0.436044] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.436053] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.436059] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.436062] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.436065] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.436068] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.436071] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.436076] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.436079] system 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[    0.436082] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.436085] system 00:08: iomem range 0xffe00000-0xffefffff has been reserved
[    0.436088] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[    0.436095] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.436098] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.436105] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.436110] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.436113] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.436116] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.436119] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.470960] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.470963] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.470965] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf7dfffff
[    0.470967] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.470971] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.470972] pci 0000:00:1c.0:   IO window: disabled
[    0.470975] pci 0000:00:1c.0:   MEM window: disabled
[    0.470978] pci 0000:00:1c.0:   PREFETCH window: 0x000000f2f00000-0x000000f2ffffff
[    0.470983] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.470985] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.470989] pci 0000:00:1c.4:   MEM window: 0xf7f00000-0xf7ffffff
[    0.470991] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.470996] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.470997] pci 0000:00:1c.5:   IO window: disabled
[    0.471000] pci 0000:00:1c.5:   MEM window: 0xf7e00000-0xf7efffff
[    0.471003] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.471008] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.471010] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.471013] pci 0000:00:1e.0:   MEM window: 0xf8000000-0xfebfffff
[    0.471016] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.471025] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.471027] pci 0000:00:01.0: setting latency timer to 64
[    0.471032] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.471035] pci 0000:00:1c.0: setting latency timer to 64
[    0.471040] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.471043] pci 0000:00:1c.4: setting latency timer to 64
[    0.471048] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.471051] pci 0000:00:1c.5: setting latency timer to 64
[    0.471055] pci 0000:00:1e.0: setting latency timer to 64
[    0.471058] bus: 00 index 0 io port: [0, ffff]
[    0.471059] bus: 00 index 1 mmio: [0, ffffffff]
[    0.471061] bus: 01 index 0 io port: [c000, cfff]
[    0.471062] bus: 01 index 1 mmio: [f4000000, f7dfffff]
[    0.471063] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.471065] bus: 01 index 3 mmio: [0, 0]
[    0.471066] bus: 04 index 0 mmio: [0, 0]
[    0.471067] bus: 04 index 1 mmio: [0, 0]
[    0.471068] bus: 04 index 2 mmio: [f2f00000, f2ffffff]
[    0.471069] bus: 04 index 3 mmio: [0, 0]
[    0.471071] bus: 03 index 0 io port: [d000, dfff]
[    0.471072] bus: 03 index 1 mmio: [f7f00000, f7ffffff]
[    0.471073] bus: 03 index 2 mmio: [0, 0]
[    0.471074] bus: 03 index 3 mmio: [0, 0]
[    0.471075] bus: 02 index 0 mmio: [0, 0]
[    0.471077] bus: 02 index 1 mmio: [f7e00000, f7efffff]
[    0.471078] bus: 02 index 2 mmio: [0, 0]
[    0.471079] bus: 02 index 3 mmio: [0, 0]
[    0.471080] bus: 05 index 0 io port: [e000, efff]
[    0.471082] bus: 05 index 1 mmio: [f8000000, febfffff]
[    0.471083] bus: 05 index 2 mmio: [0, 0]
[    0.471084] bus: 05 index 3 io port: [0, ffff]
[    0.471085] bus: 05 index 4 mmio: [0, ffffffff]
[    0.471090] NET: Registered protocol family 2
[    0.484074] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.484230] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.484441] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.484543] TCP: Hash tables configured (established 131072 bind 65536)
[    0.484545] TCP reno registered
[    0.488085] NET: Registered protocol family 1
[    0.488167] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.504029] Switched to high resolution mode on CPU 0
[    0.707790]  it is
[    0.943532] Freeing initrd memory: 8011k freed
[    0.944283] audit: initializing netlink socket (disabled)
[    0.944298] type=2000 audit(1229450018.944:1): initialized
[    0.948314] highmem bounce pool size: 64 pages
[    0.948317] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.949790] VFS: Disk quotas dquot_6.5.1
[    0.949844] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.949916] msgmni has been set to 1721
[    0.949994] io scheduler noop registered
[    0.949996] io scheduler anticipatory registered
[    0.949998] io scheduler deadline registered
[    0.950005] io scheduler cfq registered (default)
[    0.950120] pci 0000:01:00.0: Boot video device
[    0.950199] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.950221] pcieport-driver 0000:00:01.0: found MSI capability
[    0.950240] pci_express 0000:00:01.0:pcie00: allocate port service
[    0.950267] pci_express 0000:00:01.0:pcie03: allocate port service
[    0.950322] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.950346] pcieport-driver 0000:00:1c.0: found MSI capability
[    0.950370] pci_express 0000:00:1c.0:pcie00: allocate port service
[    0.950400] pci_express 0000:00:1c.0:pcie02: allocate port service
[    0.950425] pci_express 0000:00:1c.0:pcie03: allocate port service
[    0.950486] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.950510] pcieport-driver 0000:00:1c.4: found MSI capability
[    0.950534] pci_express 0000:00:1c.4:pcie00: allocate port service
[    0.950561] pci_express 0000:00:1c.4:pcie02: allocate port service
[    0.950586] pci_express 0000:00:1c.4:pcie03: allocate port service
[    0.950647] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.950671] pcieport-driver 0000:00:1c.5: found MSI capability
[    0.950695] pci_express 0000:00:1c.5:pcie00: allocate port service
[    0.950721] pci_express 0000:00:1c.5:pcie02: allocate port service
[    0.950746] pci_express 0000:00:1c.5:pcie03: allocate port service
[    0.950957] isapnp: Scanning for PnP cards...
[    1.303663] isapnp: No Plug & Play device found
[    1.324088] hpet_resources: 0xfed00000 is busy
[    1.324147] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.324240] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.324685] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.325737] brd: module loaded
[    1.325782] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.325854] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.325856] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.326353] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.326486] mice: PS/2 mouse device common for all mice
[    1.326563] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.326581] rtc0: alarms up to one month, y3k, hpet irqs
[    1.326662] EISA: Probing bus 0 at eisa.0
[    1.326682] EISA: Detected 0 cards.
[    1.326685] cpuidle: using governor ladder
[    1.326686] cpuidle: using governor menu
[    1.327002] TCP cubic registered
[    1.327019] Using IPI No-Shortcut mode
[    1.327129] registered taskstats version 1
[    1.327219]   Magic number: 4:382:896
[    1.327228] tty ptyy6: hash matches
[    1.327257] rtc_cmos 00:03: setting system clock to 2008-12-16 17:53:40 UTC (1229450020)
[    1.327259] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.327260] EDD information not available.
[    1.327397] Freeing unused kernel memory: 424k freed
[    1.327421] Write protecting the kernel text: 2576k
[    1.327438] Write protecting the kernel read-only data: 936k
[    1.386448] fuse init (API version 7.9)
[    1.400638] ACPI: SSDT CFF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.400902] processor ACPI0007:00: registered as cooling_device0
[    1.401091] ACPI: SSDT CFF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.401337] processor ACPI0007:01: registered as cooling_device1
[    1.563011] usbcore: registered new interface driver usbfs
[    1.563025] usbcore: registered new interface driver hub
[    1.563046] usbcore: registered new device driver usb
[    1.564807] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.564815] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.564818] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.564841] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.568724] ehci_hcd 0000:00:1a.7: debug port 1
[    1.568729] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.568737] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3fffc00
[    1.574089] USB Universal Host Controller Interface driver v3.0
[    1.577778] No dock devices found.
[    1.584505] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    1.584587] usb usb1: configuration #1 chosen from 1 choice
[    1.584606] hub 1-0:1.0: USB hub found
[    1.584610] hub 1-0:1.0: 6 ports detected
[    1.593427] SCSI subsystem initialized
[    1.615319] libata version 3.00 loaded.
[    1.792676] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.792683] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.792686] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.792702] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    1.792727] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    1.792785] usb usb2: configuration #1 chosen from 1 choice
[    1.792804] hub 2-0:1.0: USB hub found
[    1.792808] hub 2-0:1.0: 2 ports detected
[    2.000151] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.000156] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.000158] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.000172] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    2.000195] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    2.000250] usb usb3: configuration #1 chosen from 1 choice
[    2.000267] hub 3-0:1.0: USB hub found
[    2.000270] hub 3-0:1.0: 2 ports detected
[    2.112008] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.208280] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.208285] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.208287] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.208377] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 4
[    2.208396] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    2.208534] usb usb4: configuration #1 chosen from 1 choice
[    2.208554] hub 4-0:1.0: USB hub found
[    2.208558] hub 4-0:1.0: 2 ports detected
[    2.310909] usb 2-2: configuration #1 chosen from 1 choice
[    2.312172] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.312182] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.312184] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.312202] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.316101] ehci_hcd 0000:00:1d.7: debug port 1
[    2.316106] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.316113] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3fff800
[    2.424010] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    2.436010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.436084] usb usb5: configuration #1 chosen from 1 choice
[    2.436115] hub 5-0:1.0: USB hub found
[    2.436119] hub 5-0:1.0: 6 ports detected
[    2.609404] usb 3-2: configuration #1 chosen from 1 choice
[    2.644154] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.644158] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.644161] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.644175] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.644192] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    2.644245] usb usb6: configuration #1 chosen from 1 choice
[    2.644261] hub 6-0:1.0: USB hub found
[    2.644265] hub 6-0:1.0: 2 ports detected
[    2.852133] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.852137] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.852139] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.852153] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.852174] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    2.852228] usb usb7: configuration #1 chosen from 1 choice
[    2.852244] hub 7-0:1.0: USB hub found
[    2.852248] hub 7-0:1.0: 2 ports detected
[    2.956635] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.956640] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.956642] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.956656] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.956674] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    2.956727] usb usb8: configuration #1 chosen from 1 choice
[    2.956744] hub 8-0:1.0: USB hub found
[    2.956748] hub 8-0:1.0: 2 ports detected
[    2.964009] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    3.060783] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.060789] atl1 0000:02:00.0: setting latency timer to 64
[    3.060800] atl1 0000:02:00.0: version 2.1.3
[    3.060812] ahci 0000:03:00.0: version 3.0
[    3.060821] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.076819] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    3.076822] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    3.076827] ahci 0000:03:00.0: setting latency timer to 64
[    3.076924] scsi0 : ahci
[    3.076989] scsi1 : ahci
[    3.077037] ata1: SATA max UDMA/133 abar m8192@0xf7ffe000 port 0xf7ffe100 irq 16
[    3.077041] ata2: SATA max UDMA/133 abar m8192@0xf7ffe000 port 0xf7ffe180 irq 16
[    3.143295] usb 6-1: configuration #1 chosen from 1 choice
[    3.146390] usbcore: registered new interface driver libusual
[    3.146392] usbcore: registered new interface driver hiddev
[    3.150828] Initializing USB Mass Storage driver...
[    3.150874] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.150915] usb-storage: device found at 2
[    3.150916] usb-storage: waiting for device to settle before scanning
[    3.161413] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb3/3-2/3-2:1.0/input/input1
[    3.164054] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.1-2
[    3.192227] Fixing up Logitech keyboard report descriptor
[    3.192724] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb3/3-2/3-2:1.1/input/input2
[    3.196597] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
[    3.226266] input: Logitech Logitech RumblePad 2 USB as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
[    3.226297] input,hidraw2: USB HID v1.10 Joystick [Logitech Logitech RumblePad 2 USB] on usb-0000:00:1d.0-1
[    3.226328] usbcore: registered new interface driver usb-storage
[    3.226330] USB Mass Storage support registered.
[    3.226389] usbcore: registered new interface driver usbhid
[    3.226391] usbhid: v2.6:USB HID core driver
[    3.400024] ata1: SATA link down (SStatus 0 SControl 300)
[    3.736022] ata2: SATA link down (SStatus 0 SControl 300)
[    3.754085] ohci1394 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.807410] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.812943] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.812961] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    3.812969] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    3.812979] pata_acpi 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.812990] pata_acpi 0000:00:1f.5: setting latency timer to 64
[    3.812996] pata_acpi 0000:00:1f.5: PCI INT B disabled
[    3.813008] pata_acpi 0000:03:00.1: enabling device (0000 -> 0001)
[    3.813011] pata_acpi 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.813027] pata_acpi 0000:03:00.1: setting latency timer to 64
[    3.813036] pata_acpi 0000:03:00.1: PCI INT B disabled
[    3.815426] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.815444] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    3.817527] scsi3 : pata_jmicron
[    3.817568] scsi4 : pata_jmicron
[    3.818132] ata3: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    3.818134] ata4: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    3.980497] ata3.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[    3.996499] ata3.00: configured for UDMA/33
[    4.172700] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    4.172802] scsi 3:0:0:0: Attached scsi generic sg0 type 5
[    4.172817] ata_piix 0000:00:1f.2: version 2.12
[    4.172821] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.172823] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.172850] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.172881] scsi5 : ata_piix
[    4.172919] scsi6 : ata_piix
[    4.173908] ata5: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
[    4.173910] ata6: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
[    4.183605] Driver 'sr' needs updating - please use bus_type methods
[    4.199635] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    4.199638] Uniform CD-ROM driver Revision: 3.20
[    4.199717] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.648041] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.656282] ata5.00: ATA-7: WDC WD1600JS-00NCB1, 10.02E02, max UDMA/133
[    4.656285] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.664285] ata5.00: configured for UDMA/133
[    5.084292] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000011e6a5]
[    5.140039] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.148278] ata6.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    5.148281] ata6.00: 488397168 sectors, multi 16: LBA48 
[    5.156286] ata6.00: configured for UDMA/133
[    5.156366] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600JS-00N 10.0 PQ: 0 ANSI: 5
[    5.156457] scsi 5:0:0:0: Attached scsi generic sg1 type 0
[    5.156507] scsi 6:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    5.156559] scsi 6:0:0:0: Attached scsi generic sg2 type 0
[    5.156573] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    5.156576] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    5.156605] ata_piix 0000:00:1f.5: setting latency timer to 64
[    5.158230] scsi7 : ata_piix
[    5.158273] scsi8 : ata_piix
[    5.159273] ata7: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
[    5.159276] ata8: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
[    5.632041] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.640174] ata7.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100
[    5.656178] ata7.00: configured for UDMA/100
[    6.132040] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.140598] ata8.00: ATA-8: WDC WD5002ABYS-01B1B0, 02.03B02, max UDMA/133
[    6.140601] ata8.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.148574] ata8.00: configured for UDMA/133
[    6.149204] scsi 7:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    6.152566] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.152635] sr 7:0:0:0: Attached scsi CD-ROM sr1
[    6.152675] sr 7:0:0:0: Attached scsi generic sg3 type 5
[    6.152725] scsi 8:0:0:0: Direct-Access     ATA      WDC WD5002ABYS-0 02.0 PQ: 0 ANSI: 5
[    6.152787] scsi 8:0:0:0: Attached scsi generic sg4 type 0
[    6.172518] Driver 'sd' needs updating - please use bus_type methods
[    6.172570] sd 5:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.172582] sd 5:0:0:0: [sda] Write Protect is off
[    6.172584] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.172656] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.172698] sd 5:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.172710] sd 5:0:0:0: [sda] Write Protect is off
[    6.172712] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.172732] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.172735]  sda: sda1
[    6.191714] sd 5:0:0:0: [sda] Attached SCSI disk
[    6.191767] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.191779] sd 6:0:0:0: [sdb] Write Protect is off
[    6.191780] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.191801] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.191838] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.191849] sd 6:0:0:0: [sdb] Write Protect is off
[    6.191851] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.191872] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.191875]  sdb: sdb1 sdb2 < sdb5 >
[    6.225226] sd 6:0:0:0: [sdb] Attached SCSI disk
[    6.225268] sd 8:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    6.225280] sd 8:0:0:0: [sdc] Write Protect is off
[    6.225281] sd 8:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.225302] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.225338] sd 8:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    6.225350] sd 8:0:0:0: [sdc] Write Protect is off
[    6.225352] sd 8:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.225372] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.225375]  sdc: sdc1
[    6.245155] sd 8:0:0:0: [sdc] Attached SCSI disk
[    6.480566] PM: Starting manual resume from disk
[    6.480568] PM: Resume from partition 8:21
[    6.480569] PM: Checking hibernation image.
[    6.480711] PM: Resume from disk failed.
[    6.533296] kjournald starting.  Commit interval 5 seconds
[    6.533308] EXT3-fs: mounted filesystem with ordered data mode.
[    8.149792] usb-storage: device scan complete
[    8.152794] scsi 2:0:0:0: Direct-Access     HP       Photosmart 8100  1.00 PQ: 0 ANSI: 2
[    8.157851] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[    8.157916] sd 2:0:0:0: Attached scsi generic sg5 type 0
[   11.787854] udevd version 124 started
[   12.074695] iTCO_vendor_support: vendor-support=0
[   12.094286] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.145636] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.153353] Linux agpgart interface v0.103
[   12.225880] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.236050] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.236956] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   12.237027] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.252535] ACPI: Power Button (FF) [PWRF]
[   12.252609] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.284506] ACPI: Power Button (CM) [PWRB]
[   12.582842] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0xBA02
[   12.582862] usbcore: registered new interface driver usblp
[   12.737496] nvidia: module license 'NVIDIA' taints kernel.
[   12.991785] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.991791] nvidia 0000:01:00.0: setting latency timer to 64
[   12.991873] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   12.999224] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.159021] Linux video capture interface: v2.00
[   13.420803] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.420837] saa7134 0000:05:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.420841] saa7133[0]: found at 0000:05:02.0, rev: 209, irq: 18, latency: 64, mmio: 0xfe9ff800
[   13.420846] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.420854] saa7133[0]: board init: gpio is 40000
[   13.510290] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.510302] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.575373] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   13.575381] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.575388] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[   13.575394] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575401] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[   13.575407] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575416] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575422] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575429] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575435] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575442] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575448] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575455] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575461] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575468] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575474] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.575818] saa7133[0]: registered device video0 [v4l2]
[   13.575850] saa7133[0]: registered device vbi0
[   13.585514] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   13.585516] saa7134_alsa: Unknown symbol snd_ctl_add
[   13.585578] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   13.585579] saa7134_alsa: Unknown symbol snd_pcm_new
[   13.585688] saa7134_alsa: disagrees about version of symbol snd_card_register
[   13.585689] saa7134_alsa: Unknown symbol snd_card_register
[   13.585798] saa7134_alsa: disagrees about version of symbol snd_card_free
[   13.585799] saa7134_alsa: Unknown symbol snd_card_free
[   13.585904] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   13.585905] saa7134_alsa: Unknown symbol snd_pcm_stop
[   13.586026] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   13.586027] saa7134_alsa: Unknown symbol snd_ctl_new1
[   13.586303] saa7134_alsa: disagrees about version of symbol snd_card_new
[   13.586304] saa7134_alsa: Unknown symbol snd_card_new
[   13.586357] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.586359] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   13.586521] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   13.586522] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   13.586696] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   13.586697] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   13.586950] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   13.586952] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   13.587005] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   13.587007] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   14.815091] lp: driver loaded but no devices found
[   14.915695] Adding 9871900k swap on /dev/sdb5.  Priority:-1 extents:1 across:9871900k
[   15.172492] EXT3 FS on sdb1, internal journal
[   15.478403] type=1505 audit(1229450034.767:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4317
[   15.580185] type=1505 audit(1229450034.868:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4322
[   15.580274] type=1505 audit(1229450034.868:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4322
[   15.703597] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.140823] ACPI: WMI: Mapper loaded
[   16.687321] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.713154] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   16.713157] apm: disabled - APM is not SMP safe.
[   16.836179] ppdev: user-space parallel port driver
[   19.511525] Bluetooth: Core ver 2.13
[   19.511683] NET: Registered protocol family 31
[   19.511687] Bluetooth: HCI device and connection manager initialized
[   19.511690] Bluetooth: HCI socket layer initialized
[   19.634023] Bluetooth: L2CAP ver 2.11
[   19.634028] Bluetooth: L2CAP socket layer initialized
[   19.662094] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.662099] Bluetooth: BNEP filters: protocol multicast
[   19.715173] Bridge firewalling registered
[   19.715366] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   19.722487] Bluetooth: SCO (Voice Link) ver 0.6
[   19.722492] Bluetooth: SCO socket layer initialized
[   19.745515] Bluetooth: RFCOMM socket layer initialized
[   19.745526] Bluetooth: RFCOMM TTY layer initialized
[   19.745528] Bluetooth: RFCOMM ver 1.10
[   23.832548] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   24.048604] NET: Registered protocol family 17
[   53.513090] UDF-fs: Partition marked readonly; forcing readonly mount
[   53.537541] UDF-fs INFO UDF: Mounting volume 'GTA IV Disc 1', timestamp 2008/11/16 01:40 (1078)
[  191.119144] NET: Registered protocol family 10
[  191.120209] lo: Disabled Privacy Extensions
[  201.792007] eth0: no IPv6 routers present

```

??? any ideas ???:(

---

### Post by wolfen69 on 2008-12-16
try using vlc to view tv. open vlc and go to file>open capture device>dvb tab>OK. let us know what happens. also try the video4linux tab, and the pvr tab then OK.

---

### Post by wolfen69 on 2008-12-16
also see [this]("http://www.linuxtv.org/wiki/index.php/Main_Page") page for more help. also, there is a chance your card is not supported. if you have the money it will be worth your while to get a Hauppage PVR150, 250, or 350. they work perfectly in ubuntu with vlc.

---

### Post by cariboo on 2008-12-16
To get my Phillips saa7134 based TV tuner card to work I have to add the following to /etc/modprobe.d

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

I saved the above as saa7134, and then whenever I do a new installation I just copy the file:

```
sudo cp saa7134 /etc/modprobe.d/
```

You will probably have to change the card number to make yours work, there is a list of card numbers [here]("http://en.gentoo-wiki.com/wiki/HARDWARE_saa7134").

Jim

---

