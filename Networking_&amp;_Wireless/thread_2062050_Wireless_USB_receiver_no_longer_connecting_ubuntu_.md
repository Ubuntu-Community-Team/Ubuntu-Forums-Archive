---
title: "Wireless USB receiver no longer connecting ubuntu 12.04"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by Cinnabuntu on 2012-09-24
Hey guys,

So i finally installed Ubuntu 12.04 and am dual booting with windows 7 x86. When booting into ubuntu, I experienced problems getting my usb wireless receiver to connect. Through many searches and many forum threads, I was lead to believe it was a driver issue. I am currently using this [receiver ]("http://www.monoprice.com/products/product.asp?c_id=105&cp_id=10501&cs_id=1050108&p_id=8072&seq=1&format=2")if anyone is curious. It is marked as compatible with linux, but evidently not in a 'plug and play' type of way. To make a long story short every method I tried to get the receiver to work failed, until I followed the steps found in this [forum]("http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux"). It was the only time I received wireless internet on Ubuntu. Unfortunately, when I booted up the next day, I was unable to receive wireless again. Please help!

here is lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 004 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 004 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard

```and iwconfig:
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```Thank you for taking the time to read this; and if you take the time to help me, I thank you even more.

Cheers!

---

### Post by einonm on 2012-09-24
Hi there and welcome,

From the output to lsusb, I can see the device's usb vendor and device ID (0bda:8176). From looking through the kernel code, it appears that this device should be supported (by one of the rtl8192 drivers) without the need to build the driver yourself.

To get a little bit more info about your setup, can you please run these commands from a terminal and post the output?

rfkill list
lsmod

Also, what is shown in the network connection menu (right of the top menu bar) under 'wireless networks'?

---

### Post by Cinnabuntu on 2012-09-25
Hi einonm, thank you for replying to my query.

here is rfkill list:
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

and lsmod:
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_realtek   174313  1 
snd_usb_audio         101566  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_timer              28931  2 snd_pcm,snd_seq
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
cfg80211              178679  2 rtlwifi,mac80211
psmouse                72919  0 
uvcvideo               67203  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_seq,snd_rawmidi
videodev               86588  1 uvcvideo
mac_hid                13077  0 
snd                    62064  19 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
i915                  414817  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56321  0 

```

As a side not. When I booted into ubuntu just now, it indicated that I was connected to my home network. Unfortunately, there was no data transfer between my computer and my modem. The behavior that I've been experiencing is weird to say the least. Anyway, thanks for your help.

---

### Post by einonm on 2012-09-25
Ok, so lets take a look at the connection details of the wireless device. Can you post the output of 'dmesg' (use pastebin if it's too big) and also 'ifconfig'?

---

### Post by Cinnabuntu on 2012-09-25
Here's dmesg:
```

[    0.261958] thermal LNXTHERM:00: registered as thermal_zone0
[    0.261960] ACPI: Thermal Zone [THRM] (40 C)
[    0.261995] ERST: Table is not found!
[    0.261996] GHES: HEST is not enabled!
[    0.262062] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.282425] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.282637] isapnp: Scanning for PnP cards...
[    0.400396] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.426617] Freeing initrd memory: 13828k freed
[    0.635473] isapnp: No Plug & Play device found
[    0.688455] Linux agpgart interface v0.103
[    0.688544] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.688603] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.689415] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.689534] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.690918] brd: module loaded
[    0.691616] loop: module loaded
[    0.691774] ata_piix 0000:00:1f.2: version 2.13
[    0.691787] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.691792] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.691825] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.692103] scsi0 : ata_piix
[    0.692176] scsi1 : ata_piix
[    0.692628] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
[    0.692633] ata2: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
[    0.692655] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.692661] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.692688] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.692873] scsi2 : ata_piix
[    0.692935] scsi3 : ata_piix
[    0.693127] ata3: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xed00 irq 19
[    0.693130] ata4: SATA max UDMA/133 cmd 0xef00 ctl 0xee00 bmdma 0xed08 irq 19
[    0.693469] Fixed MDIO Bus: probed
[    0.693488] tun: Universal TUN/TAP device driver, 1.6
[    0.693489] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.693535] PPP generic driver version 2.4.2
[    0.693632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.693646] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.693660] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.693663] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.693704] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.693725] ehci_hcd 0000:00:1a.7: debug port 1
[    0.697608] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.697621] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    0.712016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.712162] hub 1-0:1.0: USB hub found
[    0.712166] hub 1-0:1.0: 6 ports detected
[    0.712232] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.712241] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.712244] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.712286] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.712305] ehci_hcd 0000:00:1d.7: debug port 1
[    0.716198] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.716210] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    0.732016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732149] hub 2-0:1.0: USB hub found
[    0.732153] hub 2-0:1.0: 6 ports detected
[    0.732217] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732229] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732243] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.732249] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.732252] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.732292] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.732320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
[    0.732430] hub 3-0:1.0: USB hub found
[    0.732433] hub 3-0:1.0: 2 ports detected
[    0.732490] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.732496] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.732499] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.732539] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.732567] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fd00
[    0.732675] hub 4-0:1.0: USB hub found
[    0.732678] hub 4-0:1.0: 2 ports detected
[    0.732733] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.732739] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.732742] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.732779] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.732799] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fc00
[    0.732908] hub 5-0:1.0: USB hub found
[    0.732912] hub 5-0:1.0: 2 ports detected
[    0.732967] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.732972] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.732975] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.733015] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.733035] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fb00
[    0.733144] hub 6-0:1.0: USB hub found
[    0.733147] hub 6-0:1.0: 2 ports detected
[    0.733203] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.733209] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.733212] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.733253] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.733273] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fa00
[    0.733381] hub 7-0:1.0: USB hub found
[    0.733384] hub 7-0:1.0: 2 ports detected
[    0.733441] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.733448] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.733451] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.733492] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.733512] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f900
[    0.733625] hub 8-0:1.0: USB hub found
[    0.733628] hub 8-0:1.0: 2 ports detected
[    0.733730] usbcore: registered new interface driver libusual
[    0.733775] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.734113] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.734119] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.734229] mousedev: PS/2 mouse device common for all mice
[    0.734359] rtc_cmos 00:04: RTC can wake from S4
[    0.734451] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.734473] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.734522] device-mapper: uevent: version 1.0.3
[    0.734587] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.734617] EISA: Probing bus 0 at eisa.0
[    0.734618] EISA: Cannot allocate resource for mainboard
[    0.734620] Cannot allocate resource for EISA slot 1
[    0.734622] Cannot allocate resource for EISA slot 2
[    0.734624] Cannot allocate resource for EISA slot 3
[    0.734625] Cannot allocate resource for EISA slot 4
[    0.734627] Cannot allocate resource for EISA slot 5
[    0.734628] Cannot allocate resource for EISA slot 6
[    0.734630] Cannot allocate resource for EISA slot 7
[    0.734631] Cannot allocate resource for EISA slot 8
[    0.734633] EISA: Detected 0 cards.
[    0.734640] cpufreq-nforce2: No nForce2 chipset.
[    0.734642] cpuidle: using governor ladder
[    0.734643] cpuidle: using governor menu
[    0.734645] EFI Variables Facility v0.08 2004-May-17
[    0.734873] TCP cubic registered
[    0.734979] NET: Registered protocol family 10
[    0.735466] NET: Registered protocol family 17
[    0.735470] Registering the dns_resolver key type
[    0.735485] Using IPI No-Shortcut mode
[    0.735581] PM: Hibernation image not present or could not be loaded.
[    0.735590] registered taskstats version 1
[    0.740916]   Magic number: 12:803:951
[    0.740947] tty tty8: hash matches
[    0.740990] rtc_cmos 00:04: setting system clock to 2012-09-25 19:55:45 UTC (1348602945)
[    0.741391] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.741393] EDD information not available.
[    1.022561] ata3: SATA link down (SStatus 0 SControl 300)
[    1.033117] ata4: SATA link down (SStatus 0 SControl 300)
[    1.144057] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[    1.236015] Refined TSC clocksource calibration: 2659.999 MHz.
[    1.236021] Switching to clocksource tsc
[    1.388014] usb 2-2: new high-speed USB device number 2 using ehci_hcd
[    1.496060] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.496077] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.500062] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.500081] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.500090] ata2.01: link offline, clearing class 3 to NONE
[    1.504407] ata1.00: ATA-8: WDC WD3200AAKS-75L9A0, 01.03E01, max UDMA/133
[    1.504411] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.508122] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7200S, 102A, max UDMA/100
[    1.520413] ata1.00: configured for UDMA/133
[    1.520536] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-7 01.0 PQ: 0 ANSI: 5
[    1.520643] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.520670] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.520687] sd 0:0:0:0: [sda] Write Protect is off
[    1.520690] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.520709] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.524126] ata2.00: configured for UDMA/100
[    1.526310] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7200S 102A PQ: 0 ANSI: 5
[    1.528588] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.528592] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.528700] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.528806] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.579317]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.579665] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.579718] Freeing unused kernel memory: 740k freed
[    1.579946] Write protecting the kernel text: 5820k
[    1.579961] Write protecting the kernel read-only data: 2376k
[    1.579962] NX-protecting the kernel data: 4420k
[    1.593338] udevd[93]: starting version 175
[    1.638840] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.638860] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.638886] r8169 0000:03:00.0: setting latency timer to 64
[    1.638939] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.639394] r8169 0000:03:00.0: eth0: RTL8168c/8111c at 0xf8418000, 00:21:9b:26:88:a2, XID 1c4000c0 IRQ 43
[    1.639397] r8169 0000:03:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.668564] firewire_ohci 0000:04:02.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.668570] firewire_ohci 0000:04:02.0: setting latency timer to 64
[    1.724085] firewire_ohci: Added fw-ohci device 0000:04:02.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    1.780016] usb 4-1: new low-speed USB device number 2 using uhci_hcd
[    1.968081] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input2
[    1.968261] generic-usb 0003:0461:4D22.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.1-1/input0
[    1.968277] usbcore: registered new interface driver usbhid
[    1.968279] usbhid: USB HID core driver
[    2.053432] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.188017] usb 4-2: new low-speed USB device number 3 using uhci_hcd
[    2.224106] firewire_core: created device fw0: GUID 00219b80002688a2, S400
[    2.463024] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3
[    2.463100] generic-usb 0003:413C:2105.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-2/input0
[   10.388515] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.412773] udevd[320]: starting version 175
[   10.444865] Adding 2084860k swap on /dev/sda5.  Priority:-1 extents:1 across:2084860k 
[   10.452952] lp: driver loaded but no devices found
[   10.515981] [drm] Initialized drm 1.1.0 20060810
[   10.524020] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.524026] i915 0000:00:02.0: setting latency timer to 64
[   10.555979] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   10.555985] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.555987] [drm] Driver supports precise vblank timestamp query.
[   10.556060] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.582256] Linux video capture interface: v2.00
[   10.582703] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62e0)
[   10.588242] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   10.597363] [drm] initialized overlay support
[   10.610673] type=1400 audit(1348628155.366:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=508 comm="apparmor_parser"
[   10.611042] type=1400 audit(1348628155.366:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   10.611248] type=1400 audit(1348628155.366:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   10.616352] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input4
[   10.616457] usbcore: registered new interface driver uvcvideo
[   10.616460] USB Video Class driver (1.1.1)
[   10.630088] cfg80211: Calling CRDA to update world regulatory domain
[   10.674215] fbcon: inteldrmfb (fb0) is primary device
[   10.675495] Console: switching to colour frame buffer device 210x65
[   10.675533] fb0: inteldrmfb frame buffer device
[   10.675535] drm: registered panic notifier
[   10.675554] No ACPI video bus found
[   10.675613] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.675659] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.675721] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   10.675744] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   10.694513] 2:3:1: cannot get freq at ep 0x84
[   10.697598] usbcore: registered new interface driver snd-usb-audio
[   10.712192] hda_codec: ALC888: BIOS auto-probing.
[   10.721543] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   10.721746] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   10.721876] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   10.721996] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.722105] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.722230] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.722347] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.722476] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.805482] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.807547] rtl8192cu: MAC address: 00:9e:95:9b:63:f0
[   10.807552] rtl8192cu: Board Type 0
[   10.866456] ppdev: user-space parallel port driver
[   10.877043] init: failsafe main process (634) killed by TERM signal
[   10.906682] Bluetooth: Core ver 2.16
[   10.906700] NET: Registered protocol family 31
[   10.906702] Bluetooth: HCI device and connection manager initialized
[   10.906704] Bluetooth: HCI socket layer initialized
[   10.906706] Bluetooth: L2CAP socket layer initialized
[   10.906711] Bluetooth: SCO socket layer initialized
[   10.920747] cfg80211: World regulatory domain updated:
[   10.920749] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.920752] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.920755] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.920757] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.920759] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.920761] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.921733] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.921735] Bluetooth: BNEP filters: protocol multicast
[   10.955123] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   10.955129] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.955131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955133] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.955136] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955138] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.955140] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955142] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.955144] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955146] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.955149] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955151] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.955153] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955155] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.955157] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955159] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.955161] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955163] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.955166] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955168] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.955170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955172] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.955174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.955176] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.955178] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.955180] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   10.955254] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.958237] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.958783] usbcore: registered new interface driver rtl8192cu
[   10.987408] Bluetooth: RFCOMM TTY layer initialized
[   10.987413] Bluetooth: RFCOMM socket layer initialized
[   10.987414] Bluetooth: RFCOMM ver 1.11
[   10.988420] type=1400 audit(1348628155.746:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=759 comm="apparmor_parser"
[   10.988932] type=1400 audit(1348628155.746:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=759 comm="apparmor_parser"
[   11.041659] type=1400 audit(1348628155.798:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=799 comm="apparmor_parser"
[   11.044813] type=1400 audit(1348628155.802:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=798 comm="apparmor_parser"
[   11.046851] type=1400 audit(1348628155.802:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=799 comm="apparmor_parser"
[   11.047059] type=1400 audit(1348628155.802:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=799 comm="apparmor_parser"
[   11.054083] type=1400 audit(1348628155.810:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=800 comm="apparmor_parser"
[   11.086048] rtl8192cu: MAC auto ON okay!
[   11.136811] rtl8192cu: Tx queue select: 0x05
[   11.137444] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   11.181470] rtw driver version=v3.4.4_xxxx.20120730 
[   11.181473] Build at: Sep 22 2012 16:40:43
[   11.181477] Error: Driver 'rtl8192cu' is already registered, aborting...
[   11.542963] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.543290] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.548980] r8169 0000:03:00.0: eth0: link down
[   11.550631] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.550958] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.488151] 2:3:1: cannot get freq at ep 0x84
[   13.519274] 2:3:1: cannot get freq at ep 0x84
[   13.868372] wlan0: authenticate with 00:1f:b3:02:08:d9 (try 1)
[   13.871329] wlan0: authenticated
[   13.871485] wlan0: associate with 00:1f:b3:02:08:d9 (try 1)
[   13.875825] wlan0: RX AssocResp from 00:1f:b3:02:08:d9 (capab=0x431 status=0 aid=2)
[   13.875828] wlan0: associated
[   13.876941] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.877019] cfg80211: Calling CRDA for country: US
[   13.881284] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.881288] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881290] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.881293] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881295] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.881297] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881299] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.881301] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881303] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.881305] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881307] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.881310] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881312] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.881314] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881316] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.881318] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881320] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.881322] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881324] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.881327] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881329] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.881331] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881333] cfg80211: Disabling freq 2467 MHz
[   13.881334] cfg80211: Disabling freq 2472 MHz
[   13.881336] cfg80211: Disabling freq 2484 MHz
[   13.881340] cfg80211: Regulatory domain changed to country: US
[   13.881341] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.881344] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   13.881346] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   13.881348] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.881350] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.881352] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.881354] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   23.899351] wlan0: disassociating from 00:1f:b3:02:08:d9 by local choice (reason=3)
[   23.900207] cfg80211: All devices are disconnected, going to restore regulatory settings
[   23.900211] cfg80211: Restoring regulatory settings
[   23.900444] cfg80211: Calling CRDA to update world regulatory domain
[   23.900961] wlan0: deauthenticating from 00:1f:b3:02:08:d9 by local choice (reason=3)
[   23.904320] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   23.904323] cfg80211: World regulatory domain updated:
[   23.904325] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.904327] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.904330] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.904332] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.904334] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.904336] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.636074] wlan0: authenticate with 00:1f:b3:02:08:d9 (try 1)
[   24.836017] wlan0: authenticate with 00:1f:b3:02:08:d9 (try 2)
[   25.036023] wlan0: authenticate with 00:1f:b3:02:08:d9 (try 3)
[   25.236014] wlan0: authentication with 00:1f:b3:02:08:d9 timed out
[   31.238614] 2:3:1: cannot get freq at ep 0x84
[   31.276740] 2:3:1: cannot get freq at ep 0x84
[  199.892023] usb 2-4: new high-speed USB device number 3 using ehci_hcd
[  200.068595] Initializing USB Mass Storage driver...
[  200.068736] scsi4 : usb-storage 2-4:1.0
[  200.068821] usbcore: registered new interface driver usb-storage
[  200.068823] USB Mass Storage support registered.
[  200.078920] usbcore: registered new interface driver uas
[  201.068698] scsi 4:0:0:0: Direct-Access     Memorex  Mini TD 001B     PMAP PQ: 0 ANSI: 0 CCS
[  201.070169] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  201.303807] sd 4:0:0:0: [sdb] 2013184 512-byte logical blocks: (1.03 GB/983 MiB)
[  201.304303] sd 4:0:0:0: [sdb] Write Protect is off
[  201.304307] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  201.304799] sd 4:0:0:0: [sdb] No Caching mode page present
[  201.304803] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  201.307671] sd 4:0:0:0: [sdb] No Caching mode page present
[  201.307676] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  201.308500]  sdb: sdb1
[  201.310799] sd 4:0:0:0: [sdb] No Caching mode page present
[  201.310804] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  201.310809] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

Here is ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:21:9b:26:88:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6560 (6.5 KB)  TX bytes:6560 (6.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:9e:95:9b:63:f0  
          inet6 addr: fe80::29e:95ff:fe9b:63f0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:226 (226.0 B)  TX bytes:306 (306.0 B)

```

Thanks again for your help.

---

### Post by mikewhatever on 2012-09-26
See [this thread]("http://ubuntuforums.org/showthread.php?t=2057048&highlight=rtl8192cu"). Hope that helps.

---

### Post by Cinnabuntu on 2012-09-27
Mikewhatever,

I used the advice you provided on thread you suggested and it worked! When I rebooted it did not connect, however. I ran the shell script again for my driver and it is working again. The real test will be tonight when i get home and boot up again. If it connects without me having to do anything extra, i'll mark this thread as solved. Thanks again for your helped though, hopefully the fix was permanent!

---

### Post by Cinnabuntu on 2012-09-27
Yay it works now! Currently writing this message from Ubuntu.  Thanks Mike for helping out, I appreciate it. Thanks to einonm for trying to help me out too.

Cheers!

---

### Post by mikewhatever on 2012-09-28
Glad it worked for you. Keep that folder at hand, cause you'll need to re-run the installation script after kernel updates.

---

