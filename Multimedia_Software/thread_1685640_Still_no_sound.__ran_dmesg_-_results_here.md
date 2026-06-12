---
title: "Still no sound.  ran dmesg - results here"
date: 2011-02-11
forum: Multimedia Software
---

### Post by G. Ross on 2011-02-11
I have a z62jm and I am loving my ubuntu experience, but no sound.  I have re-installed again so as to be fresh.  Do I always have to re-install completely, or is there another way?

Anyway, here is the results of dmesg:


[    0.300542] ACPI: Sleep Button [SLPB]
[    0.300590] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.300593] ACPI: Power Button [PWRF]
[    0.300926] ACPI: acpi_idle registered with cpuidle
[    0.301229] Marking TSC unstable due to TSC halts in idle
[    0.304604] Switching to clocksource hpet
[    0.307118] thermal LNXTHERM:01: registered as thermal_zone0
[    0.307130] ACPI: Thermal Zone [THRM] (53 C)
[    0.307216] ERST: Table is not found!
[    0.307364] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.309179] brd: module loaded
[    0.309798] loop: module loaded
[    0.309993] ata_piix 0000:00:1f.2: version 2.13
[    0.310013]   alloc irq_desc for 19 on node -1
[    0.310016]   alloc kstat_irqs on node -1
[    0.310024] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.310030] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.310075] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.310153] scsi0 : ata_piix
[    0.310234] scsi1 : ata_piix
[    0.311723] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.311727] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.312092] Fixed MDIO Bus: probed
[    0.312128] PPP generic driver version 2.4.2
[    0.312170] tun: Universal TUN/TAP device driver, 1.6
[    0.312172] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.312263] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.312284]   alloc irq_desc for 23 on node -1
[    0.312286]   alloc kstat_irqs on node -1
[    0.312291] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.312315] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.312319] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.312356] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.312378] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.312391] ehci_hcd 0000:00:1d.7: debug port 1
[    0.316283] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.316301] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebfbc00
[    0.320275] isapnp: Scanning for PnP cards...
[    0.333015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.333151] hub 1-0:1.0: USB hub found
[    0.333157] hub 1-0:1.0: 8 ports detected
[    0.333261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.333278] uhci_hcd: USB Universal Host Controller Interface driver
[    0.333312] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.333321] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.333325] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.333362] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.333391] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
[    0.333521] hub 2-0:1.0: USB hub found
[    0.333525] hub 2-0:1.0: 2 ports detected
[    0.333593] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.333600] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.333604] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.333639] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.333677] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[    0.333813] hub 3-0:1.0: USB hub found
[    0.333817] hub 3-0:1.0: 2 ports detected
[    0.333887]   alloc irq_desc for 18 on node -1
[    0.333889]   alloc kstat_irqs on node -1
[    0.333895] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.333902] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.333906] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.333941] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.333977] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.334102] hub 4-0:1.0: USB hub found
[    0.334108] hub 4-0:1.0: 2 ports detected
[    0.334176] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.334183] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.334187] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.334222] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.334258] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e480
[    0.334388] hub 5-0:1.0: USB hub found
[    0.334393] hub 5-0:1.0: 2 ports detected
[    0.334555] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.336088] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.337628] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.337635] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.337664] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.337690] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.337715] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.337828] mice: PS/2 mouse device common for all mice
[    0.338011] rtc_cmos 00:03: RTC can wake from S4
[    0.338050] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.338083] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.338195] device-mapper: uevent: version 1.0.3
[    0.338296] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.338366] device-mapper: multipath: version 1.1.1 loaded
[    0.338369] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.338486] EISA: Probing bus 0 at eisa.0
[    0.338493] Cannot allocate resource for EISA slot 1
[    0.338495] Cannot allocate resource for EISA slot 2
[    0.338521] EISA: Detected 0 cards.
[    0.338657] cpuidle: using governor ladder
[    0.338748] cpuidle: using governor menu
[    0.339094] TCP cubic registered
[    0.339235] NET: Registered protocol family 10
[    0.339644] lo: Disabled Privacy Extensions
[    0.339910] NET: Registered protocol family 17
[    0.353819] Using IPI No-Shortcut mode
[    0.353896] PM: Resume from disk failed.
[    0.353908] registered taskstats version 1
[    0.354245]   Magic number: 15:245:763
[    0.354249] serio serio1: hash matches
[    0.354332] rtc_cmos 00:03: setting system clock to 2011-02-11 02:47:42 UTC (1297392462)
[    0.354335] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.354337] EDD information not available.
[    0.373532] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.482376] Freeing initrd memory: 10512k freed
[    0.488717] ata2.00: ATAPI: UJDA770 DVD/CDRW, 1.00, max UDMA/33
[    0.488908] ata1.00: ATA-8: FUJITSU MHW2080BJ G2, 0000001A, max UDMA/100
[    0.488912] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.505639] ata2.00: configured for UDMA/33
[    0.505887] ata1.00: configured for UDMA/100
[    0.542833] ACPI: Battery Slot [BAT0] (battery present)
[    0.674589] isapnp: No Plug & Play device found
[    0.674782] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[    0.674929] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.674974] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.674993] sd 0:0:0:0: [sda] Write Protect is off
[    0.674996] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.675022] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.675306]  sda: sda1 sda2 <
[    0.676544] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA770 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    0.679927] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.679933] Uniform CD-ROM driver Revision: 3.20
[    0.680149] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.680247] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.704181]  sda5 >
[    0.704770] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.704796] Freeing unused kernel memory: 684k freed
[    0.705281] Write protecting the kernel text: 4932k
[    0.705336] Write protecting the kernel read-only data: 1976k
[    0.723477] udev[81]: starting version 163
[    0.756061] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    0.824967] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.824995] r8169 0000:04:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.825026] r8169 0000:04:07.0: (unregistered net_device): no PCI Express capability
[    0.825621] r8169 0000:04:07.0: eth0: RTL8169sb/8110sb at 0xf80a4c00, 00:18:f3:60:72:33, XID 10000000 IRQ 16
[    0.840914] firewire_ohci 0000:04:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.846494] sdhci: Secure Digital Host Controller Interface driver
[    0.846497] sdhci: Copyright(c) Pierre Ossman
[    0.992042] firewire_ohci: Added fw-ohci device 0000:04:01.1, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x0
[    0.992091] sdhci-pci 0000:04:01.2: SDHCI controller found [1180:0822] (rev 17)
[    0.992121] sdhci-pci 0000:04:01.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.993162] sdhci-pci 0000:04:01.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.994196] Registered led device: mmc0::
[    0.995226] mmc0: SDHCI controller on PCI [0000:04:01.2] using DMA
[    1.009161] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.136052] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.484168] firewire_core: created device fw0: GUID 00e01800036abeac, S400
[    9.467061] udev[343]: starting version 163
[    9.573671] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
[    9.579464] lp: driver loaded but no devices found
[    9.580549] asus_laptop: Asus Laptop Support version 0.42
[    9.584242] asus_laptop:   Z62JM model detected
[    9.688162] intel_rng: FWH not detected
[    9.702206] leds_ss4200: no LED devices found
[    9.731308] Linux agpgart interface v0.103
[    9.773906] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5
[    9.774408] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/LNXVIDEO:00/input/input6
[    9.774444] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.774932] parport_pc 00:08: disabled
[    9.774937] parport_pc: probe of 00:08 failed with error -22
[    9.776701] tpm_tis 00:0c: 1.2 TPM (device-id 0xB, rev-id 16)
[    9.783222] Bluetooth: Core ver 2.15
[    9.783272] NET: Registered protocol family 31
[    9.783274] Bluetooth: HCI device and connection manager initialized
[    9.783277] Bluetooth: HCI socket layer initialized
[    9.788338] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    9.813561] usbcore: registered new interface driver btusb
[    9.816675] yenta_cardbus 0000:04:01.0: CardBus bridge found [1043:1297]
[    9.817053] Registered led device: asus::mail
[    9.835238] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.841659] cfg80211: Calling CRDA to update world regulatory domain
[    9.843000] Linux video capture interface: v2.00
[    9.850008] gspca: main v2.9.0 registered
[    9.854354] gspca: probing 0ac8:0321
[    9.856061] vc032x: vc0321 check sensor header 2c
[    9.875270] ppdev: user-space parallel port driver
[    9.887687] type=1400 audit(1297392472.026:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=641 comm="apparmor_parser"
[    9.888715] type=1400 audit(1297392472.026:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=641 comm="apparmor_parser"
[    9.888723] [drm] Initialized drm 1.1.0 20060810
[    9.889332] type=1400 audit(1297392472.030:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=641 comm="apparmor_parser"
[    9.895049] cfg80211: World regulatory domain updated:
[    9.895052]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.895056]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.895059]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.895062]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.895065]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.895068]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.945800] yenta_cardbus 0000:04:01.0: ISA IRQ mask 0x0cb8, PCI irq 17
[    9.945805] yenta_cardbus 0000:04:01.0: Socket status: 30000006
[    9.945810] pci_bus 0000:04: Raising subordinate bus# of parent bus (#04) from #05 to #08
[    9.945820] yenta_cardbus 0000:04:01.0: pcmcia: parent PCI bridge window: [io  0xc000-0xdfff]
[    9.945824] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xdfff: excluding 0xc000-0xc0ff 0xc3b0-0xc3df 0xc400-0xc4ff 0xc7b0-0xc7df 0xcbb0-0xcbdf 0xcfb0-0xcfdf
[    9.960277] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    9.960281] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    9.960363] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.960378] iwl3945 0000:03:00.0: setting latency timer to 64
[   10.023171]  0xd3b0-0xd3df 0xd7b0-0xd7df 0xd800-0xd8ff 0xdbb0-0xdbdf
[   10.026079] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.026172]   alloc irq_desc for 43 on node -1
[   10.026175]   alloc kstat_irqs on node -1
[   10.026199] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   10.026266] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.027074]  0xdfb0-0xdfdf
[   10.027114] yenta_cardbus 0000:04:01.0: pcmcia: parent PCI bridge window: [mem 0xfe200000-0xfeafffff]
[   10.027118] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfe200000-0xfeafffff: excluding 0xfe200000-0xfe28ffff 0xfea70000-0xfeafffff
[   10.027136] yenta_cardbus 0000:04:01.0: pcmcia: parent PCI bridge window: [mem 0xddf00000-0xdfefffff 64bit pref]
[   10.027139] pcmcia_socket pcmcia_socket0: cs: memory probe 0xddf00000-0xdfefffff: excluding 0xddf00000-0xdfefffff
[   10.049637] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.049644] nouveau 0000:01:00.0: setting latency timer to 64
[   10.051316] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.051323] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   10.051467]   alloc irq_desc for 44 on node -1
[   10.051469]   alloc kstat_irqs on node -1
[   10.051505] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   10.052921] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x046700a3)
[   10.055472] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   10.071378] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.081937] vc032x: Sensor ID 7660 (7)
[   10.081940] vc032x: Find Sensor OV7660
[   10.083245] gspca: video0 created
[   10.083268] usbcore: registered new interface driver vc032x
[   10.083270] vc032x: registered
[   10.084955] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x250-0x25f 0x370-0x37f
[   10.088326] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x400-0x41f 0x480-0x4bf 0x4d0-0x4d7
[   10.089272] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x820-0x87f
[   10.089979] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.091266] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   10.091332] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   10.091397] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   10.091469] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: excluding 0xa00-0xa0f
[   10.141304] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   10.141310] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   10.141313] [drm] nouveau 0000:01:00.0: Bios version 05.72.22.41
[   10.141317] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[   10.141319] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[   10.141322] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   10.141326] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 03005323 00000004
[   10.141329] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01010300 00000028
[   10.141332] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 020223f1 00c0c080
[   10.141336] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[   10.141339] [drm] nouveau 0000:01:00.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   10.141343] [drm] nouveau 0000:01:00.0:   1: 0x00001130: type 0x30 idx 1 tag 0x07
[   10.141346] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   10.141349] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   10.141352] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   10.141355] [drm] nouveau 0000:01:00.0:   5: 0x00000340: type 0x40 idx 5 tag 0xff
[   10.141358] [drm] nouveau 0000:01:00.0:   6: 0x00002431: type 0x31 idx 6 tag 0x08
[   10.141370] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xE118
[   10.141422] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE447
[   10.213264] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE9E5
[   10.213300] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xEB60
[   10.221240] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEDB9
[   10.221251] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM
[   10.236598] [TTM] Zone  kernel: Available graphics memory: 443212 kiB.
[   10.236601] [TTM] Zone highmem: Available graphics memory: 512720 kiB.
[   10.236603] [TTM] Initializing pool allocator.
[   10.238856] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   10.240011] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   10.241244] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   10.241253] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   10.241260] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   10.303712] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[   10.405992] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   10.406199] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   10.407971] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[   10.407977] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[   10.407981] [drm] nouveau 0000:01:00.0: 0xD259: Parsing digital output script table
[   10.408023] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   10.420109] type=1400 audit(1297392472.558:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=863 comm="apparmor_parser"
[   10.420895] type=1400 audit(1297392472.558:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
[   10.421312] type=1400 audit(1297392472.562:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=863 comm="apparmor_parser"
[   10.425154] type=1400 audit(1297392472.566:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=862 comm="apparmor_parser"
[   10.435114] type=1400 audit(1297392472.574:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=870 comm="apparmor_parser"
[   10.435798] type=1400 audit(1297392472.574:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=873 comm="apparmor_parser"
[   10.436712] type=1400 audit(1297392472.574:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=873 comm="apparmor_parser"
[   10.494681] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.505693] r8169 0000:04:07.0: eth0: link down
[   10.505889] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.521146] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008/0x0
[   10.560951] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   10.676047] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   10.676056] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[   10.707181] Bluetooth: L2CAP ver 2.14
[   10.707183] Bluetooth: L2CAP socket layer initialized
[   10.716270] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.716274] Bluetooth: BNEP filters: protocol multicast
[   10.726038] Bluetooth: SCO (Voice Link) ver 0.6
[   10.726041] Bluetooth: SCO socket layer initialized
[   10.764724] [drm] nouveau 0000:01:00.0: allocated 1280x800 fb: 0x49000, bo f3216a00
[   10.776240] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 0 using output A
[   10.776244] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[   10.776247] [drm] nouveau 0000:01:00.0: 0xD2BA: Parsing digital output script table
[   10.924053] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[   10.924060] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[   10.924076] [drm] nouveau 0000:01:00.0: 0xD24A: Parsing digital output script table
[   10.924085] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 0 using output A
[   10.925522] Console: switching to colour frame buffer device 160x50
[   10.927237] fb0: nouveaufb frame buffer device
[   10.927239] drm: registered panic notifier
[   10.927242] Slow work thread pool: Starting up
[   10.927311] Slow work thread pool: Ready
[   10.927320] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   11.024862] Bluetooth: RFCOMM TTY layer initialized
[   11.024869] Bluetooth: RFCOMM socket layer initialized
[   11.024872] Bluetooth: RFCOMM ver 1.11
[   12.232598] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   12.233757] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   15.360065] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  126.532558] wlan0: authenticate with 00:26:62:3d:a2:0d (try 1)
[  126.534569] wlan0: authenticated
[  126.535120] wlan0: associate with 00:26:62:3d:a2:0d (try 1)
[  126.538312] wlan0: RX AssocResp from 00:26:62:3d:a2:0d (capab=0x31 status=0 aid=1)
[  126.538320] wlan0: associated
[  126.540616] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.552116] cfg80211: Calling CRDA for country: US
[  126.556629] cfg80211: Received country IE:
[  126.556633] cfg80211: Regulatory domain: US
[  126.556635]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  126.556639]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 2700 mBm)
[  126.556642] cfg80211: CRDA thinks this should applied:
[  126.556645] cfg80211: Regulatory domain: US
[  126.556647]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  126.556651]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  126.556654]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  126.556658]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  126.556662]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  126.556665]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  126.556669]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  126.556671] cfg80211: We intersect both of these and get:
[  126.556674] cfg80211: Regulatory domain: 98
[  126.556676]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  126.556679]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  126.556685] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[  126.556688] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[  126.556692] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[  126.556695] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[  126.556698] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[  126.556701] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[  126.556704] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[  126.556708] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[  126.556711] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[  126.556714] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[  126.556717] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[  126.556720] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[  126.556723] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[  126.556728] cfg80211: Current regulatory domain updated by AP to: US
[  126.556730]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  126.556733]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  136.640034] wlan0: no IPv6 routers present
[  197.972334] UDF-fs: Partition marked readonly; forcing readonly mount
[  197.972667] UDF-fs INFO UDF: Mounting volume 'THE_AMERICAN_DREAM', timestamp 2010/11/02 05:18 (1e20)
[ 2194.960853] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 2194.960862] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[ 2194.960869] [drm] nouveau 0000:01:00.0: 0xD259: Parsing digital output script table
[ 3779.542905] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 3779.542913] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[ 3779.542921] [drm] nouveau 0000:01:00.0: 0xD2BA: Parsing digital output script table
[ 3779.693048] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[ 3779.693055] [drm] nouveau 0000:01:00.0: 0xD24A: Parsing digital output script table
[ 3805.919222] lo: Disabled Privacy Extensions
[ 3857.805069] CE: hpet increased min_delta_ns to 7500 nsec
[ 4955.843372] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 4955.843381] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[ 4955.843388] [drm] nouveau 0000:01:00.0: 0xD259: Parsing digital output script table
[ 7441.768966] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 7441.768974] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[ 7441.768981] [drm] nouveau 0000:01:00.0: 0xD2BA: Parsing digital output script table
[ 7441.916074] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[ 7441.916080] [drm] nouveau 0000:01:00.0: 0xD24A: Parsing digital output script table
[ 8618.846666] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 8618.846674] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[ 8618.846682] [drm] nouveau 0000:01:00.0: 0xD259: Parsing digital output script table
[11017.644699] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[11017.644707] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[11017.644714] [drm] nouveau 0000:01:00.0: 0xD2BA: Parsing digital output script table
[11017.792060] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[11017.792067] [drm] nouveau 0000:01:00.0: 0xD24A: Parsing digital output script table
[12218.929036] show_signal_msg: 9 callbacks suppressed
[12218.929042] indicator-appli[1542]: segfault at 6179612f ip 00fbe4ab sp bfd06d3c error 4 in libc-2.12.1.so[ea2000+157000]
[12516.173302] lo: Disabled Privacy Extensions


Tell me if that helps.

Or a good route to go through.  The card is (apparently) a "Microsoft family" or some such.  I heard about installing the older sound manager instead of the newer one that might help.  If you can't tell, I have not been using linux for a while.  In fact the last time was Unix in '92 - I want to come back to Linux now.

Thanks for the help people!

G. Ross

---

