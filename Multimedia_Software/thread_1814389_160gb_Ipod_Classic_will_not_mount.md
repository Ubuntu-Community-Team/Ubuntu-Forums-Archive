---
title: "160gb Ipod Classic will not mount"
date: 2011-07-29
forum: Multimedia Software
---

### Post by robo2400 on 2011-07-29
Hello. Hoping someone will come across this and please help me out!
I have searched forums finding no answers.

The version of **Ubuntu** that i am running on is **11.04(Natty)** with **Gnome** desktop.
My Ipod is the **160gb Classic** from about 5 years ago.

From the get-go my Ipod has mounted and un-moutned just fine. All of a sudden it no longer will mount or show on the desktop.

I just want to add some music. The only program that has worked for me is Rhythmbox. Since ejecting my Ipod yesterday from Rhythmbox it will no longer mount it seems. :confused:

I have reset my Ipod many times, used different USB ports, and reset my computer. I even installed gtkpod with Synaptic and tried some commands in a terminal... it seems the pod is nowhere to be found?

Here's the humongous command line:
```

[    0.525651] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.525727] isapnp: Scanning for PnP cards...
[    0.618829] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.640754] Linux agpgart interface v0.103
[    0.640862] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    0.640905] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.641103] agpgart-intel 0000:00:00.0: detected 1024K stolen memory
[    0.641302] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.643481] brd: module loaded
[    0.648748] loop: module loaded
[    0.648981] i2c-core: driver [adp5520] using legacy suspend method
[    0.648985] i2c-core: driver [adp5520] using legacy resume method
[    0.649227] ata_piix 0000:00:1f.1: version 2.13
[    0.649278] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.649363] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.696080] scsi0 : ata_piix
[    0.696361] scsi1 : ata_piix
[    0.696443] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.696449] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.697232] Fixed MDIO Bus: probed
[    0.697319] PPP generic driver version 2.4.2
[    0.697451] tun: Universal TUN/TAP device driver, 1.6
[    0.697454] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.697626] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.697685] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.697719] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.697727] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.697811] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.697868] ehci_hcd 0000:00:1d.7: debug port 1
[    0.701749] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.708360] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    0.728357] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.728694] hub 1-0:1.0: USB hub found
[    0.728703] hub 1-0:1.0: 6 ports detected
[    0.728839] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.728871] uhci_hcd: USB Universal Host Controller Interface driver
[    0.728986] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.729003] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.729009] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.729102] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.729161] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.729395] hub 2-0:1.0: USB hub found
[    0.729404] hub 2-0:1.0: 2 ports detected
[    0.729507] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.729517] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.729523] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.729615] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.729662] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.729876] hub 3-0:1.0: USB hub found
[    0.729884] hub 3-0:1.0: 2 ports detected
[    0.729982] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.729992] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.729998] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.730065] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.730107] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.730322] hub 4-0:1.0: USB hub found
[    0.730330] hub 4-0:1.0: 2 ports detected
[    0.730527] i8042: PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[    0.730532] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.731367] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.736623] mousedev: PS/2 mouse device common for all mice
[    0.736939] rtc_cmos 00:05: RTC can wake from S4
[    0.737029] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.737065] rtc0: alarms up to one day, 242 bytes nvram
[    0.737255] device-mapper: uevent: version 1.0.3
[    0.737399] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.737548] device-mapper: multipath: version 1.2.0 loaded
[    0.737553] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.737704] EISA: Probing bus 0 at eisa.0
[    0.737746] EISA: Detected 0 cards.
[    0.740165] cpuidle: using governor ladder
[    0.740172] cpuidle: using governor menu
[    0.740662] TCP cubic registered
[    0.740908] NET: Registered protocol family 10
[    0.741900] NET: Registered protocol family 17
[    0.741948] Registering the dns_resolver key type
[    0.742039] Using IPI No-Shortcut mode
[    0.742272] PM: Hibernation image not present or could not be loaded.
[    0.742307] registered taskstats version 1
[    0.742551]   Magic number: 3:175:379
[    0.742687] rtc_cmos 00:05: setting system clock to 2011-07-29 11:23:24 UTC (1311938604)
[    0.742693] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.742697] EDD information not available.
[    0.799426] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.981533] ata1.00: ATA-5: WDC WD400EB-75CPF0, 06.04G06, max UDMA/100
[    0.981541] ata1.00: 78165360 sectors, multi 8: LBA 
[    1.033435] ata1.00: configured for UDMA/100
[    1.083833] isapnp: No Plug & Play device found
[    1.084105] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-75CP 06.0 PQ: 0 ANSI: 5
[    1.084462] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.084609] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.084706] sd 0:0:0:0: [sda] Write Protect is off
[    1.084711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.084753] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.113188] ata2.00: ATAPI: Lite-On LTN486S 48x Max, YDS8, max UDMA/33
[    1.113264] ata2.01: ATAPI: SONY    CD-RW  CRX216E, PD01, max UDMA/33
[    1.113933] ata2.00: configured for UDMA/33
[    1.128550] ata2.01: configured for UDMA/33
[    1.139554]  sda: sda1 sda2 < sda5 >
[    1.140229] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.151862] scsi 1:0:0:0: CD-ROM            Lite-On  LTN486S 48x Max  YDS8 PQ: 0 ANSI: 5
[    1.154664] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.154674] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.154960] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.155123] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.171710] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX216E   PD01 PQ: 0 ANSI: 5
[    1.195184] sr1: scsi3-mmc drive: 219x/48x writer cd/rw xa/form2 cdda tray
[    1.195457] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.195613] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.224213] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.357860] Freeing initrd memory: 12564k freed
[    1.384915] Freeing unused kernel memory: 700k freed
[    1.386288] Write protecting the kernel text: 5192k
[    1.386336] Write protecting the kernel read-only data: 2148k
[    1.416128] Refined TSC clocksource calibration: 2192.884 MHz.
[    1.416143] Switching to clocksource tsc
[    1.435957] <30>udev[64]: starting version 167
[    1.835186] FDC 0 is a post-1991 82077
[    1.880089] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.899737] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.916055] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    1.916065] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    1.916074] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    1.956298] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    1.956903] b44: b44.c:v2.0
[    1.977343] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:50:69:f2
[    2.116184] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[    2.116597] generic-usb 0003:045E:0053.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-1/input0
[    2.116995] usbcore: registered new interface driver usbhid
[    2.117001] usbhid: USB HID core driver
[    2.127612] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   22.717478] Adding 1307644k swap on /dev/sda5.  Priority:-1 extents:1 across:1307644k 
[   22.729723] <30>udev[247]: starting version 167
[   22.806332] lp: driver loaded but no devices found
[   22.937039] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.301811] intel_rng: FWH not detected
[   23.397547] type=1400 audit(1311953027.150:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=386 comm="apparmor_parser"
[   23.403676] type=1400 audit(1311953027.154:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=386 comm="apparmor_parser"
[   23.419752] type=1400 audit(1311953027.170:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=386 comm="apparmor_parser"
[   23.758346] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.004136] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.242673] parport_pc 00:09: reported by Plug and Play ACPI
[   24.242734] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   24.349193] lp0: using parport0 (interrupt-driven).
[   25.030114] type=1400 audit(1311953028.782:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=558 comm="apparmor_parser"
[   25.038712] [drm] Initialized drm 1.1.0 20060810
[   25.064740] type=1400 audit(1311953028.818:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=559 comm="apparmor_parser"
[   25.065821] type=1400 audit(1311953028.818:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=559 comm="apparmor_parser"
[   25.069047] type=1400 audit(1311953028.822:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=559 comm="apparmor_parser"
[   25.114712] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.133495] type=1400 audit(1311953028.886:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=560 comm="apparmor_parser"
[   25.171820] type=1400 audit(1311953028.922:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=560 comm="apparmor_parser"
[   25.202357] type=1400 audit(1311953028.954:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=560 comm="apparmor_parser"
[   25.288130] cfg80211: Calling CRDA to update world regulatory domain
[   26.071940] ppdev: user-space parallel port driver
[   26.096837] cfg80211: World regulatory domain updated:
[   26.096846] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.096853] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.096858] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.096863] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.096868] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.096873] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.651522] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.651536] i915 0000:00:02.0: setting latency timer to 64
[   26.720130] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   26.769023] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   26.769030] [drm] Driver supports precise vblank timestamp query.
[   26.831971] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   26.859643] [drm] initialized overlay support
[   27.056509] fbcon: inteldrmfb (fb0) is primary device
[   27.058277] Console: switching to colour frame buffer device 128x48
[   27.058319] fb0: inteldrmfb frame buffer device
[   27.058322] drm: registered panic notifier
[   27.058584] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   27.058679] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.058738] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.556089] intel8x0_measure_ac97_clock: measured 55816 usecs (2689 samples)
[   27.556096] intel8x0: clocking to 48000
[   28.032182] usbcore: registered new interface driver ar9170usb
[   28.055217] usbcore: registered new interface driver carl9170
[   28.547964] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.771800] ath: EEPROM regdomain: 0x0
[   28.771807] ath: EEPROM indicates default country code should be used
[   28.771811] ath: doing EEPROM country->regdmn map search
[   28.771816] ath: country maps to regdmn code: 0x3a
[   28.771820] ath: Country alpha2 being used: US
[   28.771823] ath: Regpair used: 0x3a
[   28.771831] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.771837] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771841] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.771846] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771851] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.771856] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771860] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.771865] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771869] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.771874] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771879] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.771884] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771888] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.771893] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771897] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.771902] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771906] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.771911] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771915] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.771921] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771925] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.771930] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   28.771934] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   28.771939] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   28.771943] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   28.772155] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.772162] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772168] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.772174] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772179] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.772185] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772189] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.772196] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772200] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.772206] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772211] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.772217] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772222] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.772228] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772233] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.772239] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772243] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.772249] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772254] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.772260] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772265] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.772271] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772276] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   28.772282] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772287] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   28.772293] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.772298] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   28.772304] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   28.860135] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   28.863480] cfg80211: Calling CRDA for country: US
[   28.865458] Registered led device: ar9170-phy0::tx
[   28.865505] Registered led device: ar9170-phy0::assoc
[   28.865513] usb 1-1: Atheros AR9170 is registered as 'phy0'
[   28.934584] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.934593] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934598] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.934604] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934609] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.934614] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934618] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.934624] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934628] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.934633] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934637] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.934643] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934647] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.934653] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934657] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.934662] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934667] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.934672] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934676] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.934681] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934686] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.934691] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   28.934695] cfg80211: Disabling freq 2467 MHz
[   28.934698] cfg80211: Disabling freq 2472 MHz
[   28.934701] cfg80211: Disabling freq 2484 MHz
[   28.934708] cfg80211: Regulatory domain changed to country: US
[   28.934711] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.934717] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   28.934722] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   28.934727] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.934732] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.934738] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.934743] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   30.262162] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.907028] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   46.865956] wlan0: authenticate with 00:22:3f:bc:81:b0 (try 1)
[   46.868152] wlan0: authenticated
[   46.868382] wlan0: associate with 00:22:3f:bc:81:b0 (try 1)
[   46.871156] wlan0: RX AssocResp from 00:22:3f:bc:81:b0 (capab=0x411 status=0 aid=2)
[   46.871164] wlan0: associated
[   46.883369] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.981991] Intel AES-NI instructions are not detected.
[   46.989169] padlock_aes: VIA PadLock not detected.
[   57.680018] wlan0: no IPv6 routers present
[   65.168051] usb 1-6: new high speed USB device using ehci_hcd and address 4
[   65.360876] usbcore: registered new interface driver uas
[   65.393143] Initializing USB Mass Storage driver...
[   65.393392] scsi2 : usb-storage 1-6:1.0
[   65.395341] usbcore: registered new interface driver usb-storage
[   65.395351] USB Mass Storage support registered.
[   66.407212] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   66.414528] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   66.417586] sd 2:0:0:0: [sdb] Spinning up disk....ready
[   71.040729] sd 2:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[   71.041215] sd 2:0:0:0: [sdb] Write Protect is off
[   71.041221] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
[   71.041226] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   71.044628] sd 2:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[   71.045216] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   71.229421]  sdb: sdb1
[   71.232932] sd 2:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[   71.233568] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   71.233579] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   76.360506] FAT: Filesystem error (dev sdb1)
[   76.360517]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360524] FAT: Filesystem has been set read-only
[   76.360572] FAT: Filesystem error (dev sdb1)
[   76.360576]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360591] FAT: Filesystem error (dev sdb1)
[   76.360594]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360601] FAT: Filesystem error (dev sdb1)
[   76.360604]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360616] FAT: Filesystem error (dev sdb1)
[   76.360620]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360627] FAT: Filesystem error (dev sdb1)
[   76.360630]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360641] FAT: Filesystem error (dev sdb1)
[   76.360644]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360651] FAT: Filesystem error (dev sdb1)
[   76.360654]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360669] FAT: Filesystem error (dev sdb1)
[   76.360673]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[   76.360680] FAT: Filesystem error (dev sdb1)
[   76.360683]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[  350.372027] usb 1-6: USB disconnect, address 4
[  369.840043] usb 1-6: new high speed USB device using ehci_hcd and address 5
[  369.980437] scsi3 : usb-storage 1-6:1.0
[  370.984889] scsi 3:0:0:0: Direct-Access     Seagate  FreeAgent Go     0142 PQ: 0 ANSI: 4
[  370.991095] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  370.991610] sd 3:0:0:0: [sdc] 976773166 512-byte logical blocks: (500 GB/465 GiB)
[  370.992212] sd 3:0:0:0: [sdc] Write Protect is off
[  370.992221] sd 3:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[  370.992227] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  370.993747] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  371.057927]  sdc: sdc1
[  371.059396] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  371.059408] sd 3:0:0:0: [sdc] Attached SCSI disk
[  373.762001] FAT: Directory bread(block 19082) failed
[  373.762029] FAT: Directory bread(block 19083) failed
[  373.762049] FAT: Directory bread(block 19084) failed
[  373.762071] FAT: Directory bread(block 19085) failed
[  373.762245] FAT: Directory bread(block 19082) failed
[  373.762267] FAT: Directory bread(block 19083) failed
[  373.762288] FAT: Directory bread(block 19084) failed
[  373.762309] FAT: Directory bread(block 19085) failed
[  390.335044] scsi 3:0:0:0: [sdc] Unhandled error code
[  390.335051] scsi 3:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[  390.335058] scsi 3:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 bf 00 00 08 00
[  390.335072] end_request: I/O error, dev sdc, sector 191
[  390.335081] quiet_error: 15 callbacks suppressed
[  390.335086] Buffer I/O error on device sdc1, logical block 16
[  390.336844] WARNING! power/level is deprecated; use power/control instead
[  390.416538] usb 1-6: USB disconnect, address 5
[  462.600350] exe (1862): /proc/1862/oom_adj is deprecated, please use /proc/1862/oom_score_adj instead.
[ 1125.280041] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 1125.428746] scsi4 : usb-storage 1-6:1.0
[ 1126.439769] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1126.447419] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 1126.450501] sd 4:0:0:0: [sdc] Spinning up disk....ready
[ 1131.248806] sd 4:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 1131.249290] sd 4:0:0:0: [sdc] Write Protect is off
[ 1131.249296] sd 4:0:0:0: [sdc] Mode Sense: 68 00 00 08
[ 1131.249301] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1131.252693] sd 4:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 1131.253290] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1131.504825]  sdc: sdc1
[ 1131.510042] sd 4:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 1131.510649] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1131.510660] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 1136.464159] FAT: Filesystem error (dev sdc1)
[ 1136.464168]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464175] FAT: Filesystem has been set read-only
[ 1136.464246] FAT: Filesystem error (dev sdc1)
[ 1136.464250]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464262] FAT: Filesystem error (dev sdc1)
[ 1136.464265]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464302] FAT: Filesystem error (dev sdc1)
[ 1136.464305]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464316] FAT: Filesystem error (dev sdc1)
[ 1136.464319]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464326] FAT: Filesystem error (dev sdc1)
[ 1136.464330]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464340] FAT: Filesystem error (dev sdc1)
[ 1136.464343]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464350] FAT: Filesystem error (dev sdc1)
[ 1136.464353]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464365] FAT: Filesystem error (dev sdc1)
[ 1136.464368]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
[ 1136.464375] FAT: Filesystem error (dev sdc1)
[ 1136.464378]     fat_get_cluster: invalid cluster chain (i_pos 22512562)
bdsnapshot@Robo-2400:~$ sudo mkdir /media/IPOD
[sudo] password for bdsnapshot: 
Sorry, try again.
[sudo] password for bdsnapshot: 
bdsnapshot@Robo-2400:~$ sudo mount /dev/sdc2 /media/IPOD
mount: special device /dev/sdc2 does not exist
bdsnapshot@Robo-2400:~$ sudo mount /dev/sdc1 /media/IPOD
mount: /dev/sdc1 already mounted or /media/IPOD busy
bdsnapshot@Robo-2400:~$ sudo mount /dev/sdc2 /media/IPOD
mount: special device /dev/sdc2 does not exist
bdsnapshot@Robo-2400:~$ sudo umount /media/IPOD
umount: /media/IPOD: not mounted
bdsnapshot@Robo-2400:~$ 

```


Thank you for any help!

---

### Post by dez93_2000 on 2011-12-07
I think the command line print out has scared everyone off!

I'm in the same boat (i think) - disk utility says it's mounted under /tmp but it won't show up on desktop or in computer or be found by rhythmbox. Has something changed? And: WHY?!

Any help appreciated. Ta

---

