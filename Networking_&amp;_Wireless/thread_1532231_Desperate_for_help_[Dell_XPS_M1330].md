---
title: "Desperate for help [Dell XPS M1330]"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by DeadParrot on 2010-07-16
Firstly, I would like to point out that I am completely new to Linux, regretfully, I've been using Windows all my life. But I recently got fed up with Vista and installed 10.04 (lucid).

 I'm extremely happy with the UI and how lightweight it is, but I'm experiencing problems with my wireless connection, namely the speed. In Vista, I was able to enjoy average download speed of 700 kb/s whilst it only goes up to 100 kb/s on Ubuntu. I'm positive that it's not my ISP, because I can still reach 700 kb/s on my stationary PC and the decrease in speed coincided with the installation of Ubuntu

I would really appreciate some piece of advice as I love ubuntu, but I subconsciously deduct brownie points from it as I am not able to get the most out of my internet connection. 

I have a Wireless 802.11a/b/g Network Card.

---

### Post by DeadParrot on 2010-07-16
Only read HOWTO post a wireless thread. Sorry. 

> [    0.453096] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.453104] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.453110] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.453119] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.453127] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.453139] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.453144] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.453154] pci 0000:00:1c.1:   MEM window: 0xf1f00000-0xf1ffffff
[    0.453162] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
[    0.453173] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.453179] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.453188] pci 0000:00:1c.3:   MEM window: 0xf1c00000-0xf1efffff
[    0.453196] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.453207] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.453213] pci 0000:00:1c.5:   IO window: 0x4000-0x4fff
[    0.453222] pci 0000:00:1c.5:   MEM window: 0xf1b00000-0xf1bfffff
[    0.453230] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0600000-0x000000c07fffff
[    0.453242] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.453246] pci 0000:00:1e.0:   IO window: disabled
[    0.453255] pci 0000:00:1e.0:   MEM window: 0xf1a00000-0xf1afffff
[    0.453262] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.453287]   alloc irq_desc for 16 on node -1
[    0.453291]   alloc kstat_irqs on node -1
[    0.453301] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.453308] pci 0000:00:01.0: setting latency timer to 64
[    0.453323] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.453330] pci 0000:00:1c.0: setting latency timer to 64
[    0.453345]   alloc irq_desc for 17 on node -1
[    0.453348]   alloc kstat_irqs on node -1
[    0.453354] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.453362] pci 0000:00:1c.1: setting latency timer to 64
[    0.453377]   alloc irq_desc for 19 on node -1
[    0.453380]   alloc kstat_irqs on node -1
[    0.453386] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.453394] pci 0000:00:1c.3: setting latency timer to 64
[    0.453409] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.453417] pci 0000:00:1c.5: setting latency timer to 64
[    0.453430] pci 0000:00:1e.0: setting latency timer to 64
[    0.453437] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.453441] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.453446] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.453450] pci_bus 0000:01: resource 1 mem: [0xf2000000-0xf6efffff]
[    0.453455] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.453459] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.453464] pci_bus 0000:0b: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.453468] pci_bus 0000:0b: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.453473] pci_bus 0000:0c: resource 0 io:  [0x3000-0x3fff]
[    0.453477] pci_bus 0000:0c: resource 1 mem: [0xf1f00000-0xf1ffffff]
[    0.453481] pci_bus 0000:0c: resource 2 pref mem [0xc0400000-0xc05fffff]
[    0.453486] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.453490] pci_bus 0000:0d: resource 1 mem: [0xf1c00000-0xf1efffff]
[    0.453494] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.453499] pci_bus 0000:09: resource 0 io:  [0x4000-0x4fff]
[    0.453503] pci_bus 0000:09: resource 1 mem: [0xf1b00000-0xf1bfffff]
[    0.453507] pci_bus 0000:09: resource 2 pref mem [0xc0600000-0xc07fffff]
[    0.453512] pci_bus 0000:03: resource 1 mem: [0xf1a00000-0xf1afffff]
[    0.453516] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.453520] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.453579] NET: Registered protocol family 2
[    0.453740] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.454270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.454830] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.455106] TCP: Hash tables configured (established 131072 bind 65536)
[    0.455109] TCP reno registered
[    0.455220] NET: Registered protocol family 1
[    0.455453] pci 0000:01:00.0: Boot video device
[    0.455510] Simple Boot Flag at 0x79 set to 0x1
[    0.455776] cpufreq-nforce2: No nForce2 chipset.
[    0.455817] Scanning for low memory corruption every 60 seconds
[    0.455980] audit: initializing netlink socket (disabled)
[    0.455994] type=2000 audit(1279269884.455:1): initialized
[    0.472731] highmem bounce pool size: 64 pages
[    0.472740] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.475375] VFS: Disk quotas dquot_6.5.2
[    0.475475] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476425] fuse init (API version 7.13)
[    0.476568] msgmni has been set to 1664
[    0.476901] alg: No test for stdrng (krng)
[    0.476988] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.476993] io scheduler noop registered
[    0.476996] io scheduler anticipatory registered
[    0.476999] io scheduler deadline registered
[    0.477068] io scheduler cfq registered (default)
[    0.477317]   alloc irq_desc for 24 on node -1
[    0.477320]   alloc kstat_irqs on node -1
[    0.477333] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.477343] pcieport 0000:00:01.0: setting latency timer to 64
[    0.477536]   alloc irq_desc for 25 on node -1
[    0.477539]   alloc kstat_irqs on node -1
[    0.477552] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.477567] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.477780]   alloc irq_desc for 26 on node -1
[    0.477783]   alloc kstat_irqs on node -1
[    0.477796] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.477811] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.478029]   alloc irq_desc for 27 on node -1
[    0.478032]   alloc kstat_irqs on node -1
[    0.478045] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.478060] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.478274]   alloc irq_desc for 28 on node -1
[    0.478277]   alloc kstat_irqs on node -1
[    0.478289] pcieport 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.478304] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.478460] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.478688] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.478877] ACPI: AC Adapter [AC] (off-line)
[    0.479007] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.479581] ACPI: Lid Switch [LID]
[    0.479665] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.479674] ACPI: Power Button [PBTN]
[    0.479747] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.479751] ACPI: Sleep Button [SBTN]
[    0.480817] ACPI: SSDT bfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.481598] ACPI: SSDT bfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.482226] Monitor-Mwait will be used to enter C-1 state
[    0.482266] Monitor-Mwait will be used to enter C-2 state
[    0.482302] Monitor-Mwait will be used to enter C-3 state
[    0.482312] Marking TSC unstable due to TSC halts in idle
[    0.482395] processor LNXCPU:00: registered as cooling_device0
[    0.482912] ACPI: SSDT bfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.483442] ACPI: SSDT bfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.483898] Switching to clocksource hpet
[    0.488066] processor LNXCPU:01: registered as cooling_device1
[    0.498397] thermal LNXTHERM:01: registered as thermal_zone0
[    0.498412] ACPI: Thermal Zone [THM] (31 C)
[    0.500869] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.503140] brd: module loaded
[    0.503942] loop: module loaded
[    0.504092] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.504234] ata_piix 0000:00:1f.1: version 2.13
[    0.504252] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.504307] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.504414] scsi0 : ata_piix
[    0.504523] scsi1 : ata_piix
[    0.505496] isapnp: Scanning for PnP cards...
[    0.553920] Freeing initrd memory: 7772k freed
[    0.554711] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.554717] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.554787] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.554796] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.610756] ACPI: Battery Slot [BAT0] (battery present)
[    0.612530] ata2: port disabled. ignoring.
[    0.709062] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.709416] scsi2 : ata_piix
[    0.709518] scsi3 : ata_piix
[    0.710462] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.710472] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.711065] Fixed MDIO Bus: probed
[    0.711122] PPP generic driver version 2.4.2
[    0.711213] tun: Universal TUN/TAP device driver, 1.6
[    0.711216] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.711367] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.711402]   alloc irq_desc for 22 on node -1
[    0.711405]   alloc kstat_irqs on node -1
[    0.711414] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.711438] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.711443] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.711494] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.711536] ehci_hcd 0000:00:1a.7: debug port 1
[    0.715429] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.715525] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.719930] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-857G, Z111, max UDMA/33
[    0.733020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.733160] usb usb1: configuration #1 chosen from 1 choice
[    0.733206] hub 1-0:1.0: USB hub found
[    0.733220] hub 1-0:1.0: 4 ports detected
[    0.733307]   alloc irq_desc for 20 on node -1
[    0.733311]   alloc kstat_irqs on node -1
[    0.733318] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.733334] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.733339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.733391] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.733429] ehci_hcd 0000:00:1d.7: debug port 1
[    0.737310] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.737804] ata1.00: configured for UDMA/33
[    0.737907] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.753018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.753154] usb usb2: configuration #1 chosen from 1 choice
[    0.753198] hub 2-0:1.0: USB hub found
[    0.753209] hub 2-0:1.0: 6 ports detected
[    0.753307] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.753334] uhci_hcd: USB Universal Host Controller Interface driver
[    0.753391] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.753400] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.753406] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.753456] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.753491] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.753636] usb usb3: configuration #1 chosen from 1 choice
[    0.753678] hub 3-0:1.0: USB hub found
[    0.753689] hub 3-0:1.0: 2 ports detected
[    0.753763]   alloc irq_desc for 21 on node -1
[    0.753766]   alloc kstat_irqs on node -1
[    0.753773] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.753785] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.753790] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.753840] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.753884] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.754030] usb usb4: configuration #1 chosen from 1 choice
[    0.754073] hub 4-0:1.0: USB hub found
[    0.754083] hub 4-0:1.0: 2 ports detected
[    0.754160] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.754170] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.754175] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.754230] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.754264] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.754403] usb usb5: configuration #1 chosen from 1 choice
[    0.754446] hub 5-0:1.0: USB hub found
[    0.754456] hub 5-0:1.0: 2 ports detected
[    0.754530] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.754540] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.754545] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.754594] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.754627] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.754784] usb usb6: configuration #1 chosen from 1 choice
[    0.754829] hub 6-0:1.0: USB hub found
[    0.754839] hub 6-0:1.0: 2 ports detected
[    0.754908] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.754918] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.754923] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.754971] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.755005] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.755143] usb usb7: configuration #1 chosen from 1 choice
[    0.755189] hub 7-0:1.0: USB hub found
[    0.755199] hub 7-0:1.0: 2 ports detected
[    0.755355] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.758528] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.758539] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.758660] mice: PS/2 mouse device common for all mice
[    0.758850] rtc_cmos 00:03: RTC can wake from S4
[    0.758906] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.758944] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.759108] device-mapper: uevent: version 1.0.3
[    0.759260] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.759356] device-mapper: multipath: version 1.1.0 loaded
[    0.759361] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.759533] EISA: Probing bus 0 at eisa.0
[    0.759599] EISA: Mainboard NG_FFFF detected.
[    0.759622] Cannot allocate resource for EISA slot 1
[    0.759626] Cannot allocate resource for EISA slot 2
[    0.759629] Cannot allocate resource for EISA slot 3
[    0.759632] Cannot allocate resource for EISA slot 4
[    0.759656] EISA: Detected 0 cards.
[    0.759885] cpuidle: using governor ladder
[    0.760079] cpuidle: using governor menu
[    0.760832] TCP cubic registered
[    0.761105] NET: Registered protocol family 10
[    0.761897] lo: Disabled Privacy Extensions
[    0.762490] NET: Registered protocol family 17
[    0.763279] Using IPI No-Shortcut mode
[    0.763362] PM: Resume from disk failed.
[    0.763373] registered taskstats version 1
[    0.764053]   Magic number: 2:738:725
[    0.764061] block loop5: hash matches
[    0.764085] pci 0000:01:00.0: hash matches
[    0.764140] rtc_cmos 00:03: setting system clock to 2010-07-16 08:44:45 UTC (1279269885)
[    0.764143] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.764144] EDD information not available.
[    0.767781] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.874237] isapnp: No Plug & Play device found
[    0.878084] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-857G  Z111 PQ: 0 ANSI: 5
[    0.889336] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    0.889340] Uniform CD-ROM driver Revision: 3.20
[    0.889495] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.889569] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.308050] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    1.445335] usb 2-6: configuration #1 chosen from 1 choice
[    1.508144] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.508167] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.516406] ata3.00: ATA-8: FUJITSU MJA2160BH G2, 00850019, max UDMA/100
[    1.516409] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.532422] ata3.00: configured for UDMA/100
[    1.532528] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MJA2160B 0085 PQ: 0 ANSI: 5
[    1.532645] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.532653] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.532699] sd 2:0:0:0: [sda] Write Protect is off
[    1.532702] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.532725] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.532846]  sda: sda1 sda2 < sda5 >
[    1.592474] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.684068] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.856666] usb 3-2: configuration #1 chosen from 1 choice
[    1.858611] hub 3-2:1.0: USB hub found
[    1.860574] hub 3-2:1.0: 3 ports detected
[    2.060068] ata4.01: failed to resume link (SControl 0)
[    2.060125] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.060152] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.060252] Freeing unused kernel memory: 660k freed
[    2.060635] Write protecting the kernel text: 4680k
[    2.060691] Write protecting the kernel read-only data: 1840k
[    2.075907] udev: starting version 151
[    2.108074] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    2.216343] tg3.c:v3.102 (September 1, 2009)
[    2.216376] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.216392] tg3 0000:09:00.0: setting latency timer to 64
[    2.228583] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.287132] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.288252] usb 7-1: configuration #1 chosen from 1 choice
[    2.365572] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    2.445078] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.497704] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.538227] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:15:c5:7d:eb:63
[    2.538230] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    2.538233] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    2.538234] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.573571] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    2.703668] usb 3-2.2: configuration #1 chosen from 1 choice
[    2.781585] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    2.911678] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.561224] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc0000e8bd181]
[   14.425271] udev: starting version 151
[   14.467316] Adding 6384632k swap on /dev/sda5.  Priority:-1 extents:1 across:6384632k 
[   14.540594] vga16fb: initializing
[   14.540599] vga16fb: mapped to 0xc00a0000
[   14.540650] fb0: VGA16 VGA frame buffer device
[   14.543427] Linux agpgart interface v0.103
[   14.588305] lp: driver loaded but no devices found
[   14.640077] sdhci: Secure Digital Host Controller Interface driver
[   14.640079] sdhci: Copyright(c) Pierre Ossman
[   14.641462] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   14.641481]   alloc irq_desc for 18 on node -1
[   14.641483]   alloc kstat_irqs on node -1
[   14.641490] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   14.643544] Registered led device: mmc0::
[   14.644569] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   14.646432] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.654502] Linux video capture interface: v2.00
[   14.659213] cfg80211: Calling CRDA to update world regulatory domain
[   14.720697] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   14.721426] Bluetooth: Core ver 2.15
[   14.730986] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   14.733076] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input5
[   14.733136] usbcore: registered new interface driver uvcvideo
[   14.733139] USB Video Class driver (v0.1.0)
[   14.742127] NET: Registered protocol family 31
[   14.742129] Bluetooth: HCI device and connection manager initialized
[   14.742133] Bluetooth: HCI socket layer initialized
[   14.743655] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.743763] usbcore: registered new interface driver btusb
[   14.783930] acpi device:30: registered as cooling_device2
[   14.799786] cfg80211: World regulatory domain updated:
[   14.799789]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.799792]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.799794]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.799797]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.799799]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.799801]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.816464] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2d/LNXVIDEO:00/input/input6
[   14.816557] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   14.823896] type=1505 audit(1279259099.555:2):  operation="profile_load" pid=703 name="/sbin/dhclient3"
[   14.824523] type=1505 audit(1279259099.559:3):  operation="profile_load" pid=703 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.824859] type=1505 audit(1279259099.559:4):  operation="profile_load" pid=703 name="/usr/lib/connman/scripts/dhclient-script"
[   15.238113] type=1505 audit(1279259099.971:5):  operation="profile_load" pid=791 name="/usr/share/gdm/guest-session/Xsession"
[   15.239641] type=1505 audit(1279259099.971:6):  operation="profile_replace" pid=792 name="/sbin/dhclient3"
[   15.240311] type=1505 audit(1279259099.975:7):  operation="profile_replace" pid=792 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.240654] type=1505 audit(1279259099.975:8):  operation="profile_replace" pid=792 name="/usr/lib/connman/scripts/dhclient-script"
[   15.346220] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04753/0x200000
[   15.382154] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   15.400802]   alloc irq_desc for 29 on node -1
[   15.400805]   alloc kstat_irqs on node -1
[   15.400835] tg3 0000:09:00.0: irq 29 for MSI/MSI-X
[   15.433287] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.473094] type=1505 audit(1279259100.207:9):  operation="profile_load" pid=793 name="/usr/bin/evince"
[   15.480562] type=1505 audit(1279259100.215:10):  operation="profile_load" pid=793 name="/usr/bin/evince-previewer"
[   15.485233] type=1505 audit(1279259100.219:11):  operation="profile_load" pid=793 name="/usr/bin/evince-thumbnailer"
[   15.696657] nvidia: module license 'NVIDIA' taints kernel.
[   15.696662] Disabling lock debugging due to kernel taint
[   16.388344] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.388347] ricoh-mmc: Copyright(c) Philip Langdale
[   16.388373] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   16.388390] ricoh-mmc: Controller is now disabled.
[   16.611935] Console: switching to colour frame buffer device 80x30
[   16.637724] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   16.692889] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.692901] nvidia 0000:01:00.0: setting latency timer to 64
[   16.692906] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.693219] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   16.701249] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.701252] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.701341] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.701359] iwlagn 0000:0c:00.0: setting latency timer to 64
[   16.701412] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   16.710981] usbcore: registered new interface driver hiddev
[   16.711938] Bluetooth: L2CAP ver 2.14
[   16.711940] Bluetooth: L2CAP socket layer initialized
[   16.750341] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input9
[   16.750413] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[   16.754823] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input10
[   16.754912] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[   16.754938] usbcore: registered new interface driver usbhid
[   16.754941] usbhid: v2.6:USB HID core driver
[   16.765881] iwlagn 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.765957]   alloc irq_desc for 30 on node -1
[   16.765959]   alloc kstat_irqs on node -1
[   16.765983] iwlagn 0000:0c:00.0: irq 30 for MSI/MSI-X
[   16.772387] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.772390] Bluetooth: BNEP filters: protocol multicast
[   16.785874] Bridge firewalling registered
[   16.800925] Bluetooth: SCO (Voice Link) ver 0.6
[   16.800927] Bluetooth: SCO socket layer initialized
[   16.822642] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.822678] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.823941] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.832509] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   16.901505] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   16.921504] Bluetooth: RFCOMM TTY layer initialized
[   16.921508] Bluetooth: RFCOMM socket layer initialized
[   16.921510] Bluetooth: RFCOMM ver 1.11
[   16.944793] iwlagn 0000:0c:00.0: loaded firmware version 228.61.2.24
[   16.972379] ppdev: user-space parallel port driver
[   17.116302] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.116396] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   17.116460] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   17.176403] Registered led device: iwl-phy0::radio
[   17.176422] Registered led device: iwl-phy0::assoc
[   17.176438] Registered led device: iwl-phy0::RX
[   17.176454] Registered led device: iwl-phy0::TX
[   17.218200] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.882513] wlan0: deauthenticating from 00:1c:a2:f2:6f:39 by local choice (reason=3)
[   34.882535] wlan0: direct probe to AP 00:1c:a2:f2:6f:39 (try 1)
[   34.886030] wlan0: direct probe responded
[   34.886034] wlan0: authenticate with AP 00:1c:a2:f2:6f:39 (try 1)
[   34.888144] wlan0: authenticated
[   34.888248] wlan0: associate with AP 00:1c:a2:f2:6f:39 (try 1)
[   34.890702] wlan0: RX AssocResp from 00:1c:a2:f2:6f:39 (capab=0x411 status=0 aid=1)
[   34.890707] wlan0: associated
[   34.913736] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.002586] UDF-fs: Partition marked readonly; forcing readonly mount
[   35.034607] UDF-fs INFO UDF: Mounting volume '070526_1530', timestamp 2007/05/26 15:30 (10b4)
[   45.760037] wlan0: no IPv6 routers present
[  766.001140] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2015.285162] CE: hpet increasing min_delta_ns to 22500 nsec
[ 2041.815691] __ratelimit: 9 callbacks suppressed
[ 2041.815694] type=1505 audit(1279261123.816:15):  operation="profile_replace" pid=3125 name="/usr/bin/evince"
[ 2041.816949] type=1505 audit(1279261123.820:16):  operation="profile_replace" pid=3125 name="/usr/bin/evince-previewer"
[ 2041.817590] type=1505 audit(1279261123.820:17):  operation="profile_replace" pid=3125 name="/usr/bin/evince-thumbnailer"
[ 4963.559087] plugin-containe[1880]: segfault at a85be51 ip 0a85be51 sp 0a85be51 error 4 in libnss_dns-2.11.1.so[ab9a000+4000]
lukas@DellXPS:~$ 

---

### Post by Iowan on 2010-07-16
[Here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") is a help page for IPv6 - which has been reported to cause sluggish networks...

---

### Post by simosx on 2010-07-16
You mention speeds to 700kb/s and 100kb/s.

In Windows software it is common to report 'Kb/s' (Kilobit per second) while in Linux it is 'KB/s' (also shown as 'KiB/s', KiloByte per second).

Therefore, the Linux speed of 100KB/s is actually 800Kb/s.

---

### Post by Tiberion on 2010-07-16
what drivers are you using for your wireless, many nic cards use Broadcom chipsets and these typically have the best results when you use the proprietary drivers found under System/Admin/Hardware drivers.  You will need to have a wired connection the first time if all you have is the wireless.

---

### Post by DeadParrot on 2010-07-17
> 
Therefore, the Linux speed of 100KB/s is actually 800Kb/s.

Definitely not, the change in internet speed is evident.


> what drivers are you using for your wireless, many nic cards use  Broadcom chipsets and these typically have the best results when you use  the proprietary drivers found under System/Admin/Hardware drivers.  You  will need to have a wired connection the first time if all you have is  the wireless. 	

It only shows two drivers and those are nvidia ones, does that mean that I'm using ubuntu default drivers?

---

### Post by Tiberion on 2010-08-04
NVidia drivers are typically display drivers.  Regarding wireless you may see something like this.
Notice that the Network controller is one listing, then ethernet, then wireless.  Go ahead and post your results.
jwpc@jwpc-laptop:~$ sudo lshw -C network
[sudo] password for jwpc: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:c5:cc:bc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:ba:a3:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.5.101 multicast=yes wireless=IEEE 802.11bg

---

### Post by DeadParrot on 2010-08-10
That's what came up. 

*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:a6:a2:59
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.230 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7d:eb:63
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f1bf0000-f1bfffff

---

