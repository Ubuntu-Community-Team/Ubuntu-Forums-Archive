---
title: "extremely slow wireless 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by LieToPurify3 on 2010-04-30
I did a clean install of 10.04 yesterday, and now my wifi is extremely slow. Web pages either take a long time to load, or dont load at all. However, IRC and chat clients stay connected. It seems that anything that requires a larger data transfer will fail, but things that dont require fast connections will be fine. My wifi card in my laptop uses the atheros AR2413 chipset.

lspci:
```
john@Darwin:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```

dmesg:
[    0.137054] pci 0000:00:12.0: supports D1 D2
[    0.137116] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0005000-0xc0005fff]
[    0.137252] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0006000-0xc0006fff]
[    0.137399] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0007000-0xc0007fff]
[    0.137489] pci 0000:00:13.2: supports D1 D2
[    0.137492] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.137499] pci 0000:00:13.2: PME# disabled
[    0.137552] pci 0000:00:14.0: reg 10 io port: [0x8450-0x845f]
[    0.137563] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0004400-0xc00047ff]
[    0.137610] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.137669] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.137680] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.137691] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.137702] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.137714] pci 0000:00:14.1: reg 20 io port: [0x8460-0x846f]
[    0.137839] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0000000-0xc0003fff]
[    0.137920] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.137926] pci 0000:00:14.2: PME# disabled
[    0.138146] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.138153] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.138160] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.138177] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.138196] pci 0000:01:05.0: supports D1 D2
[    0.138228] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.138233] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.138238] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.138316] pci 0000:02:04.0: reg 10 32bit mmio: [0xc0200000-0xc020ffff]
[    0.138482] pci 0000:02:06.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.138521] pci 0000:02:06.0: supports D1 D2
[    0.138524] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.138532] pci 0000:02:06.0: PME# disabled
[    0.138600] pci 0000:02:07.0: reg 10 io port: [0xa000-0xa0ff]
[    0.138614] pci 0000:02:07.0: reg 14 32bit mmio: [0xc0211000-0xc02110ff]
[    0.138699] pci 0000:02:07.0: supports D1 D2
[    0.138702] pci 0000:02:07.0: PME# supported from D1 D2 D3hot
[    0.138709] pci 0000:02:07.0: PME# disabled
[    0.138780] pci 0000:00:14.4: transparent bridge
[    0.138791] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.138799] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.138849] pci_bus 0000:00: on NUMA node 0
[    0.138854] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.139063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.139221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.141422] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.141547] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.141669] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.141789] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.141910] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.142031] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.142152] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.142273] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.142408] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.142413] vgaarb: loaded
[    0.142585] SCSI subsystem initialized
[    0.142673] libata version 3.00 loaded.
[    0.142769] usbcore: registered new interface driver usbfs
[    0.142786] usbcore: registered new interface driver hub
[    0.142818] usbcore: registered new device driver usb
[    0.142997] ACPI: WMI: Mapper loaded
[    0.143000] PCI: Using ACPI for IRQ routing
[    0.143206] NetLabel: Initializing
[    0.143209] NetLabel:  domain hash size = 128
[    0.143211] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.143232] NetLabel:  unlabeled traffic allowed by default
[    0.143275] Switching to clocksource tsc
[    0.144001] AppArmor: AppArmor Filesystem Enabled
[    0.144001] pnp: PnP ACPI init
[    0.144001] ACPI: bus type pnp registered
[    0.158819] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:12.0 BAR 6 (0x0-0x7ffff), disabling
[    0.158832] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.158887] pnp: PnP ACPI: found 10 devices
[    0.158890] ACPI: ACPI bus type pnp unregistered
[    0.158896] PnPBIOS: Disabled by ACPI PNP
[    0.158913] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.158924] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.158928] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.158932] system 00:08: ioport range 0x400-0x401 has been reserved
[    0.158936] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.158939] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.158943] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.158947] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.158950] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.158954] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.158958] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.158962] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.158965] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.158969] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.158973] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.158977] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.158981] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.158984] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.158988] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.158992] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.158999] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.159004] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.159007] system 00:09: iomem range 0xc0004800-0xc0004fff has been reserved
[    0.193795] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.193800] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.193806] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.193811] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.193820] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.193823] pci 0000:02:06.0:   IO window: 0x00a400-0x00a4ff
[    0.193831] pci 0000:02:06.0:   IO window: 0x00a800-0x00a8ff
[    0.193839] pci 0000:02:06.0:   PREFETCH window: 0x38000000-0x3bffffff
[    0.193847] pci 0000:02:06.0:   MEM window: 0x40000000-0x43ffffff
[    0.193855] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.193860] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.193869] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.193876] pci 0000:00:14.4:   PREFETCH window: 0x38000000-0x3bffffff
[    0.193915] pci 0000:02:06.0: enabling device (0004 -> 0007)
[    0.193925]   alloc irq_desc for 23 on node -1
[    0.193928]   alloc kstat_irqs on node -1
[    0.193936] pci 0000:02:06.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.193947] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.193950] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.193954] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.193957] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.193961] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.193965] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.193968] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.193972] pci_bus 0000:02: resource 2 pref mem [0x38000000-0x3bffffff]
[    0.193975] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.193979] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.193982] pci_bus 0000:03: resource 0 io:  [0xa400-0xa4ff]
[    0.193986] pci_bus 0000:03: resource 1 io:  [0xa800-0xa8ff]
[    0.193989] pci_bus 0000:03: resource 2 pref mem [0x38000000-0x3bffffff]
[    0.193993] pci_bus 0000:03: resource 3 mem: [0x40000000-0x43ffffff]
[    0.194043] NET: Registered protocol family 2
[    0.194166] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.194656] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.196578] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.197905] TCP: Hash tables configured (established 131072 bind 65536)
[    0.197911] TCP reno registered
[    0.198124] NET: Registered protocol family 1
[    0.198179] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.872804] pci 0000:01:05.0: Boot video device
[    0.873089] cpufreq-nforce2: No nForce2 chipset.
[    0.873134] Scanning for low memory corruption every 60 seconds
[    0.873301] audit: initializing netlink socket (disabled)
[    0.873333] type=2000 audit(1272646429.872:1): initialized
[    0.886407] Trying to unpack rootfs image as initramfs...
[    0.901303] highmem bounce pool size: 64 pages
[    0.901313] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.909009] VFS: Disk quotas dquot_6.5.2
[    0.909136] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.909986] fuse init (API version 7.13)
[    0.910106] msgmni has been set to 1719
[    0.910404] alg: No test for stdrng (krng)
[    0.910487] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.910492] io scheduler noop registered
[    0.910494] io scheduler anticipatory registered
[    0.910497] io scheduler deadline registered
[    0.910557] io scheduler cfq registered (default)
[    0.910717] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.910747] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.925447] ACPI: AC Adapter [ADP0] (on-line)
[    0.925584] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.925590] ACPI: Power Button [PWRB]
[    0.925649] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.925702] ACPI: Lid Switch [LID]
[    0.925771] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.925774] ACPI: Power Button [PWRF]
[    0.926231] fan PNP0C0B:00: registered as cooling_device0
[    0.926238] ACPI: Fan [FAN1] (off)
[    0.926641] Marking TSC unstable due to TSC halts in idle
[    0.926740] processor LNXCPU:00: registered as cooling_device1
[    0.930795] Switching to clocksource acpi_pm
[    1.148278] thermal LNXTHERM:01: registered as thermal_zone0
[    1.148299] ACPI: Thermal Zone [TZCR] (49 C)
[    1.150342] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.156486] brd: module loaded
[    1.157130] loop: module loaded
[    1.157285] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.157544] pata_acpi 0000:00:12.0: enabling device (0005 -> 0007)
[    1.157558]   alloc irq_desc for 22 on node -1
[    1.157560]   alloc kstat_irqs on node -1
[    1.157571] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.157673]   alloc irq_desc for 16 on node -1
[    1.157675]   alloc kstat_irqs on node -1
[    1.157681] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.157707] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.158112] Fixed MDIO Bus: probed
[    1.158164] PPP generic driver version 2.4.2
[    1.158228] tun: Universal TUN/TAP device driver, 1.6
[    1.158231] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.158338] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.158362]   alloc irq_desc for 19 on node -1
[    1.158364]   alloc kstat_irqs on node -1
[    1.158369] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.158399] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.158439] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    1.158521] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0007000
[    1.158579] isapnp: Scanning for PnP cards...
[    1.168234] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.168414] usb usb1: configuration #1 chosen from 1 choice
[    1.168455] hub 1-0:1.0: USB hub found
[    1.168471] hub 1-0:1.0: 8 ports detected
[    1.168578] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.168606] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.168633] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.168683] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.168711] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0005000
[    1.232553] usb usb2: configuration #1 chosen from 1 choice
[    1.232596] hub 2-0:1.0: USB hub found
[    1.232617] hub 2-0:1.0: 4 ports detected
[    1.232708] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.232740] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.232800] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.232839] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0006000
[    1.248454] Freeing initrd memory: 7774k freed
[    1.315261] usb usb3: configuration #1 chosen from 1 choice
[    1.315307] hub 3-0:1.0: USB hub found
[    1.315340] hub 3-0:1.0: 4 ports detected
[    1.315453] uhci_hcd: USB Universal Host Controller Interface driver
[    1.315608] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.361802] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.361812] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.361961] mice: PS/2 mouse device common for all mice
[    1.362786] ACPI Error: Could not disable RealTimeClock events (20090903/evxfevnt-373)
[    1.362794] rtc_cmos 00:04: RTC can wake from S4
[    1.362856] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.362891] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.363051] device-mapper: uevent: version 1.0.3
[    1.363439] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.363515] device-mapper: multipath: version 1.1.0 loaded
[    1.363520] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.363701] EISA: Probing bus 0 at eisa.0
[    1.363712] Cannot allocate resource for EISA slot 1
[    1.363744] Cannot allocate resource for EISA slot 8
[    1.363747] EISA: Detected 0 cards.
[    1.363863] cpuidle: using governor ladder
[    1.363941] cpuidle: using governor menu
[    1.364534] TCP cubic registered
[    1.364739] NET: Registered protocol family 10
[    1.365303] lo: Disabled Privacy Extensions
[    1.365681] NET: Registered protocol family 17
[    1.365763] Using IPI No-Shortcut mode
[    1.365879] PM: Resume from disk failed.
[    1.365898] registered taskstats version 1
[    1.366550]   Magic number: 6:279:895
[    1.366691] rtc_cmos 00:04: setting system clock to 2010-04-30 16:53:50 UTC (1272646430)
[    1.366696] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.366698] EDD information not available.
[    1.585173] isapnp: No Plug & Play device found
[    1.585289] Freeing unused kernel memory: 656k freed
[    1.586074] Write protecting the kernel text: 4676k
[    1.586119] Write protecting the kernel read-only data: 1840k
[    1.587969] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.609766] udev: starting version 151
[    1.668386] ACPI: Battery Slot [BAT0] (battery present)
[    1.832088] scsi0 : pata_atiixp
[    1.842749] scsi1 : pata_atiixp
[    1.844460] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[    1.844465] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[    1.844694] sata_sil 0000:00:12.0: version 2.4
[    1.845635] scsi2 : sata_sil
[    1.847617] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.847647] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.847782] scsi3 : sata_sil
[    1.848252] ata3: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc0004080 irq 22
[    1.848258] ata4: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc00040c0 irq 22
[    2.168089] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.177121] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.50, max UDMA/33
[    2.177291] ata3.00: ATA-7: FUJITSU MHV2080BH, 00000028, max UDMA/100
[    2.177296] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.193092] ata2.00: configured for UDMA/33
[    2.193218] ata3.00: configured for UDMA/100
[    2.197090] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.50 PQ: 0 ANSI: 5
[    2.205839] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.205844] Uniform CD-ROM driver Revision: 3.20
[    2.206153] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.206320] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    2.206546] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 0000 PQ: 0 ANSI: 5
[    2.206692] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.206986] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.207045] sd 2:0:0:0: [sda] Write Protect is off
[    2.207049] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.207080] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.207244]  sda: sda1 sda2 < sda5 >
[    2.263201] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.524068] ata4: SATA link down (SStatus 0 SControl 300)
[    2.531962] 8139too Fast Ethernet driver 0.9.28
[    2.532076]   alloc irq_desc for 20 on node -1
[    2.532080]   alloc kstat_irqs on node -1
[    2.532090] 8139too 0000:02:07.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.536258] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:2e:b1:12, IRQ 20
[    2.799955] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.799961] EXT4-fs (sda1): write access will be enabled during recovery
[    8.529687] EXT4-fs (sda1): recovery complete
[    8.531208] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   20.102702] udev: starting version 151
[   20.184714] Adding 2621432k swap on /dev/sda5.  Priority:-1 extents:1 across:2621432k 
[   20.312088] lp: driver loaded but no devices found
[   20.372209] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8450, revision 0
[   20.439680] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.570188] Linux agpgart interface v0.103
[   20.818349] cfg80211: Calling CRDA to update world regulatory domain
[   20.882785] cfg80211: World regulatory domain updated:
[   20.882791] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.882795] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.882799] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.882802] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.882806] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.882809] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.896915] type=1505 audit(1272646450.029:2):  operation="profile_load" pid=527 name="/sbin/dhclient3"
[   20.897683] type=1505 audit(1272646450.029:3):  operation="profile_load" pid=527 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.898090] type=1505 audit(1272646450.029:4):  operation="profile_load" pid=527 name="/usr/lib/connman/scripts/dhclient-script"
[   20.971681] yenta_cardbus 0000:02:06.0: CardBus bridge found [1179:ff10]
[   20.971719] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   20.971728] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   20.971731] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   20.971740] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01111122, devctl 0x44
[   20.972429] [drm] Initialized drm 1.1.0 20060810
[   21.200973] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0ef8, PCI irq 23
[   21.200980] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   21.200992] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   21.200997] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   21.201307] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   21.201311] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
[   21.212472] ath5k 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.212550] ath5k 0000:02:04.0: registered as 'phy0'
[   21.759093] type=1505 audit(1272646450.889:5):  operation="profile_load" pid=614 name="/usr/share/gdm/guest-session/Xsession"
[   21.772077] type=1505 audit(1272646450.905:6):  operation="profile_replace" pid=615 name="/sbin/dhclient3"
[   21.783419] type=1505 audit(1272646450.913:7):  operation="profile_replace" pid=615 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.783852] type=1505 audit(1272646450.913:8):  operation="profile_replace" pid=615 name="/usr/lib/connman/scripts/dhclient-script"
[   21.803138] [drm] radeon defaulting to kernel modesetting.
[   21.803145] [drm] radeon kernel modesetting enabled.
[   21.803232]   alloc irq_desc for 17 on node -1
[   21.803235]   alloc kstat_irqs on node -1
[   21.803246] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.819351] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   21.819362] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[   21.830657] [drm] radeon: Initializing kernel modesetting.
[   21.831616] type=1505 audit(1272646450.961:9):  operation="profile_load" pid=616 name="/usr/bin/evince"
[   21.837036] [drm] register mmio base: 0xC0100000
[   21.837041] [drm] register mmio size: 65536
[   21.837393] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   21.837422] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   21.837482] [drm] Generation 2 PCI interface, using max accessible memory
[   21.837486] [drm] radeon: VRAM 128M
[   21.837488] [drm] radeon: VRAM from 0x38000000 to 0x3FFFFFFF
[   21.837491] [drm] radeon: GTT 32M
[   21.837493] [drm] radeon: GTT from 0x40000000 to 0x41FFFFFF
[   21.837544] [drm] radeon: irq initialized.
[   21.837810] [drm] Detected VRAM RAM=128M, BAR=256M
[   21.837815] [drm] RAM width 128bits DDR
[   21.852047] [TTM] Zone  kernel: Available graphics memory: 444468 kiB.
[   21.852052] [TTM] Zone highmem: Available graphics memory: 447864 kiB.
[   21.852080] [drm] radeon: 128M of VRAM memory ready
[   21.852083] [drm] radeon: 32M of GTT memory ready.
[   21.852109] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   21.852936] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   21.853286] [drm] radeon: cp idle (0x10000C03)
[   21.853426] [drm] Loading R300 Microcode
[   21.853842] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   21.855804] eth0: link down
[   21.861119] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   21.868426] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.871475] [drm] radeon: ring at 0x0000000040000000
[   21.871504] [drm] ring test succeeded in 2 usecs
[   21.871673] [drm] radeon: ib pool ready.
[   21.871754] [drm] ib test succeeded in 0 usecs
[   21.871810] [drm] Default TV standard: NTSC
[   21.871813] [drm] 14.318180000 MHz TV ref clk
[   21.871908] [drm] Panel ID String: LPL                     
[   21.871911] [drm] Panel Size 1280x800
[   21.871972] [drm] Default TV standard: NTSC
[   21.871974] [drm] 14.318180000 MHz TV ref clk
[   21.874289] [drm] Radeon Display Connectors
[   21.874294] [drm] Connector 0:
[   21.874297] [drm]   VGA
[   21.874300] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   21.874302] [drm]   Encoders:
[   21.874305] [drm]     CRT1: INTERNAL_DAC2
[   21.874307] [drm] Connector 1:
[   21.874309] [drm]   LVDS
[   21.874312] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   21.874314] [drm]   Encoders:
[   21.874316] [drm]     LCD1: INTERNAL_LVDS
[   21.874319] [drm] Connector 2:
[   21.874320] [drm]   S-video
[   21.874322] [drm]   Encoders:
[   21.874324] [drm]     TV1: INTERNAL_DAC2
[   21.993525] type=1505 audit(1272646451.125:10):  operation="profile_load" pid=616 name="/usr/bin/evince-previewer"
[   22.014234] type=1505 audit(1272646451.145:11):  operation="profile_load" pid=616 name="/usr/bin/evince-thumbnailer"
[   22.187276] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.198784] [drm] fb mappable at 0xD0040000
[   22.198787] [drm] vram apper at 0xD0000000
[   22.198790] [drm] size 4096000
[   22.198792] [drm] fb depth is 24
[   22.198794] [drm]    pitch is 5120
[   22.202204] fb0: radeondrmfb frame buffer device
[   22.202209] registered panic notifier
[   22.202219] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   22.210972] vga16fb: initializing
[   22.210979] vga16fb: mapped to 0xc00a0000
[   22.210987] vga16fb: not registering due to another framebuffer present
[   22.234276] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   22.240742] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   22.241782] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.242650] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.243585] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   22.376776] Console: switching to colour frame buffer device 160x50
[   22.396371] hda_codec: ALC861: BIOS auto-probing.
[   22.397219] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   22.738671] ppdev: user-space parallel port driver
[   22.914698] ath: EEPROM regdomain: 0x64
[   22.914704] ath: EEPROM indicates we should expect a direct regpair map
[   22.914711] ath: Country alpha2 being used: 00
[   22.914713] ath: Regpair used: 0x64
[   22.957680] phy0: Selected rate control algorithm 'minstrel'
[   22.958557] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   23.137944] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.305534] wlan0: deauthenticating from 00:18:01:f7:31:dc by local choice (reason=3)
[   34.314608] wlan0: direct probe to AP 00:18:01:f7:31:dc (try 1)
[   34.317637] wlan0: direct probe responded
[   34.317641] wlan0: authenticate with AP 00:18:01:f7:31:dc (try 1)
[   34.321231] wlan0: authenticated
[   34.321255] wlan0: associate with AP 00:18:01:f7:31:dc (try 1)
[   34.330108] wlan0: RX AssocResp from 00:18:01:f7:31:dc (capab=0x431 status=0 aid=2)
[   34.330116] wlan0: associated
[   34.333833] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.335455] cfg80211: Calling CRDA for country: US
[   34.338718] cfg80211: Received country IE:
[   34.338724] cfg80211: Regulatory domain: US
[   34.338726] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.338730] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   34.338733] cfg80211: CRDA thinks this should applied:
[   34.338735] cfg80211: Regulatory domain: US
[   34.338737] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.338741] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   34.338745] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   34.338748] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.338752] 	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.338755] 	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   34.338759] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   34.338761] cfg80211: We intersect both of these and get:
[   34.338763] cfg80211: Regulatory domain: 98
[   34.338765] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.338769] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   34.338777] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   34.338780] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   34.338783] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   34.338790] cfg80211: Current regulatory domain updated by AP to: US
[   34.338792] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   34.338796] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   35.420132] padlock: VIA PadLock not detected.
[   45.004038] wlan0: no IPv6 routers present

```

---

### Post by LieToPurify3 on 2010-04-30
bump

---

### Post by moonlighter on 2010-05-02
Ditto have exactly the same problem :(

---

### Post by axelsvag on 2010-05-02
I also had that problem. Then I activated backports for wireless. linux-backports-modules-wireless-generic and I got the feeling everything got better. or maybe the router was in better mode afterwards

---

### Post by mitsumits on 2010-05-02
Having the same problem. Wireless was fine with previous version. I only had to install an extra driver from the cd to make it work. Now I did an online update, it's working but it's very slow.

---

### Post by hsoJoshFTW on 2010-05-02
Having the same problem. In OS X the wireless I get is full signal strength, But on Ubuntu 10.4 , it's about half the strength. Not sure, Also I cannot seem to be able to turn UP the fan speed because it's running so hot.

---

### Post by kelver69 on 2010-05-02
my wireless is noticeably slower as well.  I don't feel like trouble-shooting right now.  I'm going back to 9.10 for the time being.  Cheers.

---

### Post by elclanrs on 2010-05-02
me too... on karmic it was ok but on lucid is extremely slow...like 20kb/s... when it should be like 300kb/s

---

### Post by tifff on 2010-05-04
After original lucid install: Simple ping looses up to 80% of messages and made ssh connect impossible. Often html page display using firefox never completed.  
Using backports kernel  2.6.32-21-generic-pae improved situation (only 20% loss).
iwconfig rts setting reduced it further to only some failures. Now performance in near range (same room) is similar as it was with karmic. Reason why AR2413 got that bad performance  in lucid is unclear, impo: Transmit power too low?

---

### Post by LieToPurify3 on 2010-05-05
has anyone figured out how to fix this? seems to be a common problem

---

### Post by phillip2 on 2010-05-06
> **LieToPurify3 said:**
> has anyone figured out how to fix this? seems to be a common problem

I've had this problem for several days -- or a related one. In my case, web browsing is impossible, but some forms of connection (ssh for instance) are fine. 

My machine updated today with a number of kernel updates. This seems to have solved the problems with a slow connection by virtue of disabling the device entirely. I can get no network connectivity at all now over wireless. 

Not a happy experience, with lucid so far, as another computer wireless adaptor of mine has failed also. I'm seriously considering doing a fresh install to 9.10 or Debian stable at this point. 

Anyone else with the same problem? 

Phil

---

### Post by jar112 on 2010-05-06
Similar problem here too, but on Thinkpad T41 (Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter). My problems already began in 9.10 after some recent update. The wireless connection went really slow (had been working fine in 9.04 and 9.10 until ~ two weeks ago) and started to loose connection every other minute. Especially if downloading something. And this happens even 2 m from the router. Wired connection is ok.

iwconfig gives:

eth1    IEEE 802.11b  ESSID:"Hoblaa"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:66:E6:8C
          Bit Rate=5.5 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:362  Invalid misc:55   Missed beacon:12

I've got nothing... Anyone?

---

### Post by novusperdiem on 2010-05-06
Hey all,

I recently installed Lucid Lynx on my Macbook 3,1. My connection speed on OSX is normally 2000kbps constant, but in Lucid it tents to fluctuate from at least 40kbps to maximum 800kbps. I also tried changing from WPA to WEP on my router as I've heard it has worked for some people but sadly, no luck.

Kev

---

### Post by trpnblies7 on 2010-05-09
Mine is also very slow. I'm using the RT73USB driver.

---

### Post by Axlswe on 2010-05-09
I'm having the same problem. Slower and worse connection to my wireless than my other laptop (that doesn't have an Atheros AR2413).  Some websites takes a long time to load, and sometimes they don't load at all.

---

### Post by eltonw on 2010-05-09
Perhaps the following might be of help to many of you:
[http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922") [#136]

**OR** use *this* kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

HTH...

---

### Post by Neosano on 2010-05-10
A blind shot, but
try to set ubuntu in performance mode, instead of a powersave one :-S

---

### Post by trpnblies7 on 2010-05-10
I decided to go ahead and use ndiswrapper instead of the default rt72usb driver, and things seem a whole lot better so far. So maybe it was a driver issue for me.

---

### Post by trpnblies7 on 2010-05-19
Everything is back to being painfully slow. Ndiswrapper didn't do a damn thing.

---

### Post by JohnDoe365 on 2010-05-19
This is so common with Ubuntu 10.04. Please try the following:

Disable WiFi
Enable WiFi and wait for re-association with AP. Is speed back to normal?

If yes, PLEASE add a comment @ [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)

Sorry, this is no work-arround as
1. speed is acutally only better but still far from normal
2. it will fall back to unacceptible slow within random time

A huge amount of people have this issues and there is no know and confirmed work-around, hack, what so ever.

---

### Post by trpnblies7 on 2010-05-19
I can't tell if disabling and enabling WiFi makes a difference. Everything is still very slow. I've also been noticing that the reception from my router to my wireless adapter keeps going up and down sporadically, from around 12% to around 56%. It never used to do that. It used to always stay around 64% or so (which is a normal range considering the setup in my apartment), but it hasn't been consistent for quite awhile now.

---

### Post by trpnblies7 on 2010-05-19
I just tried disabling and enabling again, and I think it made a difference. But it doesn't last long.

---

### Post by Orestez on 2010-05-25
Got the same problem with a HP dv6000, broadcom wireless. I've tried several drivers (as far as I can tell), no difference. Even the same when I use several different wifi dongles, which is weird. Definitely not a router problem, as other computers on the same network do just fine. 

Connecting even takes ages.

---

### Post by moodle on 2010-06-03
I have the same issue in Ubuntu 10.04.  My wireless is painfully slow.  Never had the problem in Ubuntu before.

---

### Post by Zymous on 2010-06-04
I have this problem on my Toshiba Equium L100 with an Atheros AR2413 wireless card. Initially I updated from 9.10 and had the problem described above (very slow browsing with Firefox, Opera and Chrome, but good download speeds in Synaptic). I then tried a clean install and the problem persisted.

I've reverted to 9.10.

(My EeePC 701 is running UNE 10.04 without any problems).

-- 
Zym

---

### Post by novusperdiem on 2010-06-05
> **novusperdiem said:**
> Hey all,

I recently installed Lucid Lynx on my Macbook 3,1. My connection speed on OSX is normally 2000kbps constant, but in Lucid it tents to fluctuate from at least 40kbps to maximum 800kbps. I also tried changing from WPA to WEP on my router as I've heard it has worked for some people but sadly, no luck.

Kev

I ended up fixing this problem by installing the 'wicd' network manager, speeds are constant and a lot faster.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Hope the same works for anyone who experienced the same problem.

Kev.

---

### Post by Orestez on 2010-06-05
My issues with the HP dv6000 were solved by blacklisting conflicting drivers (rtx2 smth), in case anyone has similar hardware.

---

### Post by jakobl on 2010-06-06
I have experienced similar behavior using the rt73 driver for a GWL-122 WiFi adapter.

Disabling the WiFi automatic power management fixed the problem completely.

```
sudo iwconfig wlan0 power off
```

BTW. I was also affected by the "slow dns" problem which can be worked around by installing pdns-recursor.

---

### Post by TurinPT on 2010-06-08
> **jakobl said:**
> I have experienced similar behavior using the rt73 driver for a GWL-122 WiFi adapter.

Disabling the WiFi automatic power management fixed the problem completely.

```
sudo iwconfig wlan0 power off
```


THANK YOU! Solved it for me.

---

### Post by marianlibrarian on 2010-06-09
Does not work for me:
[FONT="Courier New"]sudoiwconfig wlan0 power off[/FONT]

This seems to be a problem that affects ALL wireless devices and has been a problem for quite some time.

There does not seem to be any kind of activity regarding a solution so I will have to abandon this 10.04 LTS and hope that 9.10 behaves better.

Why? Because my connection speed is so inconsistent that I am unable to do any kind of update. I left it yesterday with 54 MB of updates and it sat for 3.5 hours and was unable to download the first MB of anything. So I give up. 

This problem is weird as it seems to "creep" up on you. There are no messages. No warnings. Nothing. Just a jumping speed number that goes from 1 to 56. I wrote down a sequence of speed jumps over the period of about a minute or so:
53,42,54,1,54,36,Unknown,12,1,18,1, and I gave up.
The active connection percent during this sequence: 37% - 42%

OBTW - 10.04 was a "clean" install. the harddrive was blank from the manufacturer. 10.04 is the only operating system this computer has ever seen. Just in case it makes a difference. :)

---

### Post by giddyup306 on 2010-06-09
Hello all.  This is one of the many problems I've encountered with Lucid.  However, I think in my instance it is a Firefox issue.  It seems to not affect Opera.  I then uninstalled and reinstalled Firefox, and now it seems to be working fine. One thing that I noticed was that it was well over 100 MB when I uninstalled, but when I reinstalled, it was less than 30 MB. That's a lot of garbage...

:guitar:

---

### Post by marianlibrarian on 2010-06-09
I had one machine that had 9.10 on it already. I took it downstairs to my children's library and exchanged it for the offending 10.04 machine. I started it up and set up my wireless WUSB54GC - and it is working wonderfully. It took about 5 to 10 minutes to get it all done. 

I am putting the 10.04 one in our book processing area. It is wired network and I have not seen the problems there as I have seen with the wireless set up. 

WUSB54GC using rt73 driver does work out of the box on 9.10 Karmic Koala.

Maybe they get it fixed soon.

---

### Post by trpnblies7 on 2010-06-09
I can't begin to describe how frustrating this issue is. Wireless hasn't worked correctly for me since 9.04. I kept thinking with each release it would finally be fixed, but it never is. I'm almost positive it worked perfectly fine in 8.04 and 8.10, but it's been so long that I can't even remember now. Is it my wireless adapter (Asus W-167G)? My driver (rt73usb)? Or is it just a problem with Ubuntu that's continually ignored?

I've tried every imaginable solution, it seems, and one thing will work for a little while, but then it'll just stop out of nowhere and I'm stuck again. It's just so disheartening that an OS as great and easy to use as Ubuntu seems to have such a glaring flaw that won't go away. If I had a laptop, I would just plug into my router and ignore the issue. But I can't move my desktop out of its current room.

This just sucks.

---

### Post by giddyup306 on 2010-06-09
> **trpnblies7 said:**
> I can't begin to describe how frustrating this issue is. Wireless hasn't worked correctly for me since 9.04. I kept thinking with each release it would finally be fixed, but it never is. I'm almost positive it worked perfectly fine in 8.04 and 8.10, but it's been so long that I can't even remember now. Is it my wireless adapter (Asus W-167G)? My driver (rt73usb)? Or is it just a problem with Ubuntu that's continually ignored?



It might be your wireless card.  I had an Asus Eee PC and I could never get the wireless to work even though I found a few "fixes".  My desktop never had wireless so I bought the card in the link below. 

[http://cgi.ebay.com/Sabrent-802-11g-2-4GHz-Wireless-PCI-Network-Card-54mbp-/170460231010?cmd=ViewItem&pt=LH_DefaultDomain_0&hash=item27b038b562](http://cgi.ebay.com/Sabrent-802-11g-2-4GHz-Wireless-PCI-Network-Card-54mbp-/170460231010?cmd=ViewItem&pt=LH_DefaultDomain_0&hash=item27b038b562)


It supports Linux, and does have a tar.gz2 file for the software.  I couldn't get it to install, but all I had to do was plug-n-play.

IIRC I spent $22 for the card shipped!

---

### Post by trpnblies7 on 2010-06-09
I've considered a new adapter, but I'm wary of non-USB devices because I don't know if I'd get sufficient range because of how my desktop is situated. I might just have to try a different brand of USB adapter.

---

### Post by giddyup306 on 2010-06-10
> **trpnblies7 said:**
> I've considered a new adapter, but I'm wary of non-USB devices because I don't know if I'd get sufficient range because of how my desktop is situated. I might just have to try a different brand of USB adapter.


Well, it's up to you...  FWIW I'd look at the reviews on Egghead.  One guy said something along the lines of you will get reception unless you have a WWII bomb shelter that is lined with lead paint.  I had a Linksys that I bought at a big box store for 3X the price.  IMHO this one is much better.  Plus from what I understand, you can get a better antenna if need be.  



I'm not trying to persuade you in any direction, just letting you know what worked for me. 

:guitar:

---

### Post by Gravatas on 2010-09-01
sudo iwconfig eth1 power off  worked for me. everything is better, but not normal!

---

### Post by booch221 on 2010-09-02
I just installed Ubuntu today and I'm having the same problem. Some pages load with no problem (wsj.com) other's (washingtonpost.com) don't load at all or only partially. I downloaded Chrome and it does the same thing, so I don't think this is a Firefox issue.

**Update:**
I just downloaded Opera and it doesn't work at all. Can't go anywhere on the web.

Ubuntu is obviously not ready for Prime Time.

---

### Post by mbott on 2010-09-19
As many in this thread, I'm extremely disappointed in 10.04.1 LTS and its networking.  I completed the Distribution Upgrade which went well, but the wireless was not acceptable. Slooooow!  I restored 9.10 with Clonezilla and the wireless is back to decent speed.  Looks like I'll be waiting a bit longer until this issue is resolved.  

Oh, and it's just not the wireless communications that are the issue.  Hard wired to my network router is no better than the wireless. 

:(

-- 
Mike

---

### Post by netpigs on 2010-10-02
I'm also experiencing the same issue as all here. I have a Toshiba Satellite L25 with an Atheros AR2413. I've tried installing the [MadWiFi]("http://madwifi.org/") drivers and [wcid]("http://wicd.sourceforge.net/"), but no luck with either. Wired connection works flawlessly, but wireless is no go! Hope somebody can find a solution to this and end our misery!!!  ](*,)

Mark.

---

### Post by rixutin on 2010-10-12
I have AR2413bg NIC rev01. It works fine under Windows, Ubuntu 8.04 and old stuff like that. Problem is that in newer distros connection speed is so slow... I don't remember which Ubuntu version that change was, but I have discovered out the change from older ath_pci module to newer ath5k module made this. Under Arch Linux I have succesfully installed and used that older ath_pci and speed was good as in the old days. Older Ubuntu used ath0 (ath_pci module) and newer wlan0 (ath5k module). One thing that makes that fix harder for other distros than Arch is they dropped support for that old Madwifi(ath_pci). I hope this helps some one and hope you can even understand this mess what I'm writing :confused: Next I'm trying can I fix this with Ndiswrapper for others than Arch.

---

### Post by Diego Garcia Mendoza on 2010-11-02
Hey, i have your solution... I have a Satellite L35-SP1011 with that wireless card. I solved with
```
sudo modprobe -r ath5k
sudo modporbe ath5k nohwcrypt
```

that's for temporal test... if you want it permanent just
```
sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```

hope this helps

---

### Post by mbott on 2010-11-02
> **mbott said:**
> As many in this thread, I'm extremely disappointed in 10.04.1 LTS and its networking.  I completed the Distribution Upgrade which went well, but the wireless was not acceptable. Slooooow!  I restored 9.10 with Clonezilla and the wireless is back to decent speed.  Looks like I'll be waiting a bit longer until this issue is resolved.  

Oh, and it's just not the wireless communications that are the issue.  Hard wired to my network router is no better than the wireless.

The solution to my issue turned out to be pretty simple: through the network manager, change the settings for DNS to 8.8.8.8 and 8.8.4.4.  That's all it took.

-- 
Mike

---

### Post by rixutin on 2010-11-02
> **Diego Garcia Mendoza said:**
> Hey, i have your solution... I have a Satellite L35-SP1011 with that wireless card. I solved with
```
sudo modprobe -r ath5k
sudo modporbe ath5k nohwcrypt
```that's for temporal test... if you want it permanent just
```
sudo sh -c "echo 'options ath5k nohwcrypt' >/etc/modprobe.d/custom-wireless.conf"
```hope this helps
It really worked :) Thank you!

---

### Post by wormyblackburny on 2011-03-01
sudo iwconfig wlan0 power off

Worked for me instantaneously. Speedtest.net went from .36down/.60up to 1.85 down/.6 up
**God I hate Cox "High Speed" Internet**

---

### Post by Nattydread69 on 2011-03-23
Thanks Diego Garcia Mendoza your fix worked for me!

---

### Post by PhilLord on 2011-05-01
For me this problem persists in 11.04 (Natty) having just done a clean install. The fix suggested earlier -- switch hwcrypt off works, resulting in a massive improvement. Fool that I am, I forgot to write down the fix from last time, so just had to spend an hour finding this again (only possible because I have two computers at home!). 

I *think* I now have some idea of why the behaviour is so inconsistent. It seems to be that the driver doesn't like doing several things at once. Running ssh is fine, for instance, but running two ssh'es at once gets very slow. On the web, some web pages do lots of things at once, some don't. Just a thought. 

Phil

---

### Post by Orestez on 2011-05-01
Well, a year ago or so my problem was solved by turning off power management. Currently on 10.10 with the same kind of usb dongle (rt73 driver) that doesn't work anymore and the wireless just kind of lags from time to time, though when it works the speed is more or less acceptable (still not max of possible). I've tried some "new" ralink drivers, but to no avail.

---

