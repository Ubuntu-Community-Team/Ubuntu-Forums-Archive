---
title: "TV Tuner Not Recognized [12.04]"
date: 2012-08-24
forum: Multimedia Software
---

### Post by SanjiSasuke on 2012-08-24
So I found an old TV Tuner, Sony BTF-pa402z. I plugged it in, and tried it in a MythTV and it is not recognized.

Tried to get Windows drivers and install them, and it says smrt_m is installed but it sometimes says Yes or No to Hardware Present. (Most of the time no)

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 03f0:d407 Hewlett-Packard 
Bus 004 Device 003: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse

```lspci
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev ff)
```dmesg (It was too big to fit wholly in the terminal...)
```
[    0.545461] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.545475] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeafa000
[    0.560026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.560227] hub 1-0:1.0: USB hub found
[    0.560231] hub 1-0:1.0: 6 ports detected
[    0.560290] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.560300] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.560302] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.560337] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.560360] ehci_hcd 0000:00:1d.7: debug port 1
[    0.564229] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.564241] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaf8000
[    0.580021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.580207] hub 2-0:1.0: USB hub found
[    0.580210] hub 2-0:1.0: 6 ports detected
[    0.580269] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.580279] uhci_hcd: USB Universal Host Controller Interface driver
[    0.580293] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.580299] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.580302] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.580338] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.580366] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d880
[    0.580462] hub 3-0:1.0: USB hub found
[    0.580465] hub 3-0:1.0: 2 ports detected
[    0.580517] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.580522] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.580525] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.580565] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.580592] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d800
[    0.580692] hub 4-0:1.0: USB hub found
[    0.580695] hub 4-0:1.0: 2 ports detected
[    0.580743] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.580748] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.580750] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.580785] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.580805] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    0.580899] hub 5-0:1.0: USB hub found
[    0.580902] hub 5-0:1.0: 2 ports detected
[    0.580950] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.580956] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.580958] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.580991] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.581018] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d080
[    0.581115] hub 6-0:1.0: USB hub found
[    0.581118] hub 6-0:1.0: 2 ports detected
[    0.581166] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.581171] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.581173] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.581209] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.581229] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d000
[    0.581322] hub 7-0:1.0: USB hub found
[    0.581326] hub 7-0:1.0: 2 ports detected
[    0.581409] usbcore: registered new interface driver libusual
[    0.581441] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.581798] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.581809] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.582017] mousedev: PS/2 mouse device common for all mice
[    0.582183] rtc_cmos 00:03: RTC can wake from S4
[    0.582272] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.582294] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.582359] device-mapper: uevent: version 1.0.3
[    0.582417] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.582424] cpuidle: using governor ladder
[    0.582426] cpuidle: using governor menu
[    0.582427] EFI Variables Facility v0.08 2004-May-17
[    0.582615] TCP cubic registered
[    0.582702] NET: Registered protocol family 10
[    0.583067] NET: Registered protocol family 17
[    0.583071] Registering the dns_resolver key type
[    0.583178] PM: Hibernation image not present or could not be loaded.
[    0.583188] registered taskstats version 1
[    0.599670]   Magic number: 8:233:288
[    0.599726] tty tty21: hash matches
[    0.599788] rtc_cmos 00:03: setting system clock to 2012-08-24 16:16:45 UTC (1345825005)
[    0.600389] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.600391] EDD information not available.
[    0.860028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.861086] ata1.00: ATA-8: WDC WD5000AAKS-22V1A0, 05.01D05, max UDMA/133
[    0.861091] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    0.863059] ata1.00: configured for UDMA/133
[    0.863153] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-2 05.0 PQ: 0 ANSI: 5
[    0.863260] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.863280] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.863298] sd 0:0:0:0: [sda] Write Protect is off
[    0.863301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.863318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.905570]  sda: sda1 sda2 < sda5 >
[    0.905921] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.040022] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.180026] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.182468] ata2.00: ATAPI: PLDS DVD+/-RW DH-16ABS, PD11, max UDMA/100
[    1.183260] ata2.00: configured for UDMA/100
[    1.185170] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DH-16ABS PD11 PQ: 0 ANSI: 5
[    1.188953] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.188959] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.189143] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.189192] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.190507] Freeing unused kernel memory: 920k freed
[    1.190760] Write protecting the kernel read-only data: 12288k
[    1.194919] Freeing unused kernel memory: 1616k freed
[    1.198496] Freeing unused kernel memory: 1200k freed
[    1.212136] udevd[98]: starting version 175
[    1.244079] Refined TSC clocksource calibration: 2992.499 MHz.
[    1.244085] Switching to clocksource tsc
[    1.269124] [drm] Initialized drm 1.1.0 20060810
[    1.281223] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.281244] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.281271] r8169 0000:02:00.0: setting latency timer to 64
[    1.281323] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.281658] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc90000652000, b8:ac:6f:da:eb:4a, XID 081000c0 IRQ 43
[    1.281660] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.286212] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.286217] i915 0000:00:02.0: setting latency timer to 64
[    1.300031] usb 2-5: new high-speed USB device number 3 using ehci_hcd
[    1.333861] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    1.333866] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.333867] [drm] Driver supports precise vblank timestamp query.
[    1.333901] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.435694] Initializing USB Mass Storage driver...
[    1.435785] scsi6 : usb-storage 2-5:1.0
[    1.435842] usbcore: registered new interface driver usb-storage
[    1.435843] USB Mass Storage support registered.
[    1.513378] composite sync not supported
[    1.513380] composite sync not supported
[    1.519805] fbcon: inteldrmfb (fb0) is primary device
[    1.519859] Console: switching to colour frame buffer device 160x48
[    1.519877] fb0: inteldrmfb frame buffer device
[    1.519878] drm: registered panic notifier
[    1.519891] No ACPI video bus found
[    1.519941] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.680023] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.813214] composite sync not supported
[    1.813216] composite sync not supported
[    1.858928] input: HP HP Link-5 Micro Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
[    1.859001] generic-usb 0003:03F0:D407.0001: input,hidraw0: USB HID v1.11 Keyboard [HP HP Link-5 Micro Receiver] on usb-0000:00:1a.1-1/input0
[    1.864306] input: HP HP Link-5 Micro Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input3
[    1.864653] generic-usb 0003:03F0:D407.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [HP HP Link-5 Micro Receiver] on usb-0000:00:1a.1-1/input1
[    1.864763] usbcore: registered new interface driver usbhid
[    1.864766] usbhid: USB HID core driver
[    1.915282] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.092028] usb 4-2: new low-speed USB device number 3 using uhci_hcd
[    2.282963] input: Dell Premium USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
[    2.283048] generic-usb 0003:413C:3016.0003: input,hidraw2: USB HID v1.11 Mouse [Dell Premium USB Optical Mouse] on usb-0000:00:1a.1-2/input0
[    2.432701] scsi 6:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    2.433203] scsi 6:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    2.433697] scsi 6:0:0:2: Direct-Access     Generic- SM/xD Picture    1.02 PQ: 0 ANSI: 0
[    2.434195] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0
[    2.434568] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.434690] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    2.434792] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    2.434897] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    2.439558] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    2.440808] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.441432] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    2.442057] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    5.123501] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.400648] Adding 5919740k swap on /dev/sda5.  Priority:-1 extents:1 across:5919740k 
[    6.504303] udevd[352]: starting version 175
[    6.680230] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.517348] lp: driver loaded but no devices found
[    8.648024] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.707821] udevd[413]: renamed network interface eth0 to eth1
[   10.030015] Linux video capture interface: v2.00
[   10.193724] ivtv: Start initialization, version 1.4.3
[   10.193924] ivtv0: Initializing card 0
[   10.193927] ivtv0: Unknown card: vendor/device: [4444:0016]
[   10.193929] ivtv0:               subsystem vendor/device: [104d:801d]
[   10.193931] ivtv0:               cx23416 based
[   10.193932] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   10.193933] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   10.193935] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   10.193936] ivtv0: Prefix your subject line with [UNKNOWN IVTV CARD].
[   10.194053] ivtv 0000:03:01.0: enabling device (0000 -> 0002)
[   10.194061] ivtv 0000:03:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.194071] ivtv 0000:03:01.0: setting latency timer to 64
[   10.196447] tveeprom 15-0050: Huh, no eeprom present (err=-6)?
[   10.196450] tveeprom 15-0050: Encountered bad packet header [d0]. Corrupt or not a Hauppauge eeprom.
[   10.196451] ivtv0: Invalid EEPROM
[   10.221324] type=1400 audit(1345839415.120:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=627 comm="apparmor_parser"
[   10.221332] type=1400 audit(1345839415.120:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=686 comm="apparmor_parser"
[   10.221637] type=1400 audit(1345839415.120:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=627 comm="apparmor_parser"
[   10.221644] type=1400 audit(1345839415.120:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=686 comm="apparmor_parser"
[   10.221815] type=1400 audit(1345839415.120:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=627 comm="apparmor_parser"
[   10.221823] type=1400 audit(1345839415.120:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=686 comm="apparmor_parser"
[   10.605399] cx25840 15-0044: Unable to detect h/w, assuming cx23887
[   10.606357] cx25840 15-0044: cx23887 A/V decoder found @ 0x88 (ivtv i2c driver #0)
[   11.134003] type=1400 audit(1345839416.032:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=786 comm="apparmor_parser"
[   11.134011] type=1400 audit(1345839416.032:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=785 comm="apparmor_parser"
[   11.147431] i2c-core: driver [tuner] using legacy suspend method
[   11.147434] i2c-core: driver [tuner] using legacy resume method
[   11.349662] wm8775 15-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   11.352608] wm8775 15-001b: I2C: cannot write 000 to register R23
[   11.355467] wm8775 15-001b: I2C: cannot write 000 to register R7
[   11.358328] wm8775 15-001b: I2C: cannot write 021 to register R11
[   11.361188] wm8775 15-001b: I2C: cannot write 102 to register R12
[   11.364054] wm8775 15-001b: I2C: cannot write 000 to register R13
[   11.366912] wm8775 15-001b: I2C: cannot write 1d4 to register R14
[   11.369773] wm8775 15-001b: I2C: cannot write 1d4 to register R15
[   11.372632] wm8775 15-001b: I2C: cannot write 1bf to register R16
[   11.375490] wm8775 15-001b: I2C: cannot write 185 to register R17
[   11.378350] wm8775 15-001b: I2C: cannot write 0a2 to register R18
[   11.381226] wm8775 15-001b: I2C: cannot write 005 to register R19
[   11.384090] wm8775 15-001b: I2C: cannot write 07a to register R20
[   11.386948] wm8775 15-001b: I2C: cannot write 102 to register R21
[   11.397895] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   11.397951] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   11.397999] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   11.398027] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   11.398083] ivtv0: Registered device radio0 for encoder radio
[   11.398085] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   11.398103] ivtv: End initialization
[   12.133647] cfg80211: Calling CRDA to update world regulatory domain
[   12.645972] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.645979] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.645984] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.645995] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.645996] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.645998] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646000] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.646002] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646004] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.646006] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646007] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.646009] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646011] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.646013] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646015] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.646017] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646018] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.646020] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646022] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.646024] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646026] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.646028] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.646029] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.646031] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.646033] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.646035] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.646037] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.646039] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.961206] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.961257] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.961280] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.116021] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.116437] ieee80211 phy0: hwaddr 00:26:f2:b6:49:b3, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   13.136545] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   13.143813] rtl8187: Customer ID is 0x00
[   13.144031] Registered led device: rtl8187-phy0::radio
[   13.144096] Registered led device: rtl8187-phy0::tx
[   13.144789] Registered led device: rtl8187-phy0::rx
[   13.145552] rtl8187: wireless switch is on
[   13.145615] usbcore: registered new interface driver rtl8187
[   13.359844] ivtv0: Encoder mailbox not found
[   13.359849] ivtv0: Retry loading firmware
[   13.486050] hda_codec: ALC887: BIOS auto-probing.
[   13.523199] HDMI status: Codec=3 Pin=3 Presence_Detect=0 ELD_Valid=0
[   13.523315] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   13.523392] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   13.523445] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   13.523496] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   13.523549] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.523600] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.523650] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.523701] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.523756] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   13.826554] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.826558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826560] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.826562] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826563] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.826565] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826567] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.826569] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826571] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.826573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826574] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.826577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826578] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.826580] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826582] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.826584] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826585] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.826588] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826589] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.826591] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826593] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.826595] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826597] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.826599] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.826600] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.826602] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.826604] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.826606] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.826608] cfg80211: World regulatory domain updated:
[   13.826610] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.826612] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826613] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.826615] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.826617] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.826619] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.001820] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   14.223989] ivtv0: Encoder mailbox not found
[   14.223994] ivtv0: Failed to initialize on device video0
[   14.224005] ivtv0: Failed to initialize on device radio0
[   14.224097] ivtv0: Failed to initialize on device video32
[   14.224106] ivtv0: Failed to initialize on device vbi0
[   14.224452] ivtv0: Failed to initialize on device video24
[   14.288439] udevd[420]: renamed network interface wlan0 to wlan1
[   14.306056] init: failsafe main process (866) killed by TERM signal
[   17.170403] ppdev: user-space parallel port driver
[   17.445194] Bluetooth: Core ver 2.16
[   17.445215] NET: Registered protocol family 31
[   17.445216] Bluetooth: HCI device and connection manager initialized
[   17.445218] Bluetooth: HCI socket layer initialized
[   17.445220] Bluetooth: L2CAP socket layer initialized
[   17.445225] Bluetooth: SCO socket layer initialized
[   17.666962] Bluetooth: RFCOMM TTY layer initialized
[   17.666967] Bluetooth: RFCOMM socket layer initialized
[   17.666968] Bluetooth: RFCOMM ver 1.11
[   17.754047] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.754050] Bluetooth: BNEP filters: protocol multicast
[   17.834700] type=1400 audit(1345839422.732:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1065 comm="apparmor_parser"
[   17.835122] type=1400 audit(1345839422.732:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1065 comm="apparmor_parser"
[   19.109800] type=1400 audit(1345839424.008:12): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1086 comm="apparmor_parser"
[   19.111876] type=1400 audit(1345839424.008:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1088 comm="apparmor_parser"
[   19.112224] type=1400 audit(1345839424.012:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1088 comm="apparmor_parser"
[   19.112404] type=1400 audit(1345839424.012:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1088 comm="apparmor_parser"
[   19.138628] type=1400 audit(1345839424.036:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1087 comm="apparmor_parser"
[   19.951366] type=1400 audit(1345839424.848:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1091 comm="apparmor_parser"
[   19.951745] type=1400 audit(1345839424.848:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1091 comm="apparmor_parser"
[   19.955010] type=1400 audit(1345839424.852:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1095 comm="apparmor_parser"
[   21.438213] r8169 0000:02:00.0: eth1: link down
[   21.438569] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.438851] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   23.028627] init: gdm main process (1198) killed by TERM signal
[   23.324196] audit_printk_skb: 36 callbacks suppressed
[   23.324199] type=1400 audit(1345839428.224:32): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1226 comm="apparmor_parser"
[   25.258765] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.259030] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.777646] composite sync not supported
[   26.777650] composite sync not supported
[   26.905407] composite sync not supported
[   26.905410] composite sync not supported
[   36.317317] wlan1: authenticate with 30:46:9a:0d:83:98 (try 1)
[   36.320077] wlan1: authenticated
[   36.320379] wlan1: associate with 30:46:9a:0d:83:98 (try 1)
[   36.323698] wlan1: RX AssocResp from 30:46:9a:0d:83:98 (capab=0x421 status=0 aid=2)
[   36.323704] wlan1: associated
[   36.329363] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   37.213398] vboxdrv: Found 2 processor cores.
[   37.213624] vboxdrv: fAsync=0 offMin=0x23a offMax=0xd89
[   37.213680] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   37.213682] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   38.242731] vboxpci: IOMMU not found (not registered)
[   47.048011] wlan1: no IPv6 routers present
[   60.290002] composite sync not supported
[   60.290005] composite sync not supported
[   63.703230] init: plymouth-stop pre-start process (2448) terminated with status 1
[   82.953330] composite sync not supported
[   82.953332] composite sync not supported
[   83.573395] composite sync not supported
[   83.573398] composite sync not supported
[  102.849412] composite sync not supported
[  102.849415] composite sync not supported
[  189.169511] composite sync not supported
[  189.169514] composite sync not supported
[  189.297345] composite sync not supported
[  189.297348] composite sync not supported
[  201.957261] alarmclock[2596] general protection ip:7f9ac3a06fde sp:7f9a8e7fb920 error:0 in libc-2.15.so[7f9ac3987000+1b3000]
```

---

