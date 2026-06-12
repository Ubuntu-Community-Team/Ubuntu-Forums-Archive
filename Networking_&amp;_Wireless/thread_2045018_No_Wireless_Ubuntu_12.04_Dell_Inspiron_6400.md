---
title: "No Wireless Ubuntu 12.04 Dell Inspiron 6400"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by T Bone on 2012-08-20
Hi, 

I upgraded my fiancees Dell Inspiron 6400 with Ubuntu 12.04 from Windows and immediately had no wireless. I have virtually no technical knowledge but trawled the forums for advice and somehow (by an unknown combination of botched efforts to follow other threads) managed to get it up and running last night. 

On startup today though, same problem- Ubuntu doesn't seem to recognise that this device has wireless capability. I tried following the same threads, but to no avail. Can anyone talk me through solving this, if possible?

As requested elsewhere, here are the results of various commands...

lspci

"00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
laura@laura-MM061:~$ "

lsusb...

"Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub"


ifconfig....

"eth0      Link encap:Ethernet  HWaddr 00:1d:09:ae:6b:0a  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feae:6b0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2010688 (2.0 MB)  TX bytes:294814 (294.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18162 (18.1 KB)  TX bytes:18162 (18.1 KB)"

iwconfig....

"lo        no wireless extensions.

eth0      no wireless extensions."

dmesg...

"[    0.530625] NET: Registered protocol family 17
[    0.530631] Registering the dns_resolver key type
[    0.530670] Using IPI No-Shortcut mode
[    0.530950] PM: Hibernation image not present or could not be loaded.
[    0.530964] registered taskstats version 1
[    0.534902] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.620796] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[    0.624695] ata1.00: ATA-8: TOSHIBA MK1246GSX, LB212D, max UDMA/100
[    0.624700] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.633127] ata1.00: configured for UDMA/100
[    0.636364] ata2.00: configured for UDMA/33
[    1.047643] isapnp: No Plug & Play device found
[    1.047852] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    1.048114] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.048356] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.048421] sd 0:0:0:0: [sda] Write Protect is off
[    1.048425] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.048453] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.052161] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[    1.057115] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.057120] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.057300] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.057493] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.101986] Freeing initrd memory: 13820k freed
[    1.110799]  sda: sda1 sda2 < sda5 >
[    1.111428] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.120390]   Magic number: 8:145:292
[    1.120441] tty tty25: hash matches
[    1.120518] rtc_cmos 00:06: setting system clock to 2012-08-20 18:15:38 UTC (1345486538)
[    1.120540] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.120542] EDD information not available.
[    1.120750] Freeing unused kernel memory: 712k freed
[    1.121070] Write protecting the kernel text: 5616k
[    1.121110] Write protecting the kernel read-only data: 2324k
[    1.146671] udevd[85]: starting version 175
[    1.383747] sdhci: Secure Digital Host Controller Interface driver
[    1.383751] sdhci: Copyright(c) Pierre Ossman
[    1.399694] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.399729] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.400784] mmc0: no vmmc regulator found
[    1.401822] Registered led device: mmc0::
[    1.423149] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.423198] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.487413] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.629240] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.988151] firewire_core: created device fw0: GUID 464fc0001a213470, S400
[   12.662682] udevd[298]: starting version 175
[   12.729408] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k 
[   12.740861] lp: driver loaded but no devices found
[   12.770547] cfg80211: Calling CRDA to update world regulatory domain
[   12.934808] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.934813] Copyright(c) 2003-2011 Intel Corporation
[   13.090400] wmi: Mapper loaded
[   13.124324] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.408366] Bluetooth: Core ver 2.16
[   13.408440] lib80211: common routines for IEEE802.11 drivers
[   13.408444] lib80211_crypt: registered algorithm 'NULL'
[   13.412087] NET: Registered protocol family 31
[   13.412092] Bluetooth: HCI device and connection manager initialized
[   13.412097] Bluetooth: HCI socket layer initialized
[   13.412099] Bluetooth: L2CAP socket layer initialized
[   13.412109] Bluetooth: SCO socket layer initialized
[   13.414472] ppdev: user-space parallel port driver
[   13.437576] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.437581] Bluetooth: BNEP filters: protocol multicast
[   13.462902] Bluetooth: RFCOMM TTY layer initialized
[   13.462909] Bluetooth: RFCOMM socket layer initialized
[   13.462912] Bluetooth: RFCOMM ver 1.11
[   13.580360] intel_rng: FWH not detected
[   13.581993] acpi device:28: registered as cooling_device1
[   13.582398] leds_ss4200: no LED devices found
[   13.616460] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[   13.616599] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   13.616635] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   13.617036] type=1400 audit(1345486550.993:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=561 comm="apparmor_parser"
[   13.617755] type=1400 audit(1345486550.993:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=561 comm="apparmor_parser"
[   13.659433] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.659445] r592 0000:03:01.2: setting latency timer to 64
[   13.695050] r592: driver successfully loaded
[   13.697190] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.697202] r852 0000:03:01.3: setting latency timer to 64
[   13.701410] r852: Non dma capable device detected, dma disabled
[   13.701429] r852: driver loaded successfully
[   13.712448] [drm] Initialized drm 1.1.0 20060810
[   13.719722] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.719727] Disabling lock debugging due to kernel taint
[   13.816444] cfg80211: World regulatory domain updated:
[   13.816449] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.816453] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.816457] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.816461] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.816464] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.816468] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.818312] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.818320] i915 0000:00:02.0: setting latency timer to 64
[   13.823426] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.823437] wl 0000:0b:00.0: setting latency timer to 64
[   13.832410] malloc in abgphy done
[   13.832561] eth%d: 5.100.82.38 driver failed with code 21
[   13.871285] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.871290] [drm] Driver supports precise vblank timestamp query.
[   13.934917] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.965797] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   14.032230] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   14.032247] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   14.032261] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   14.032271] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   14.125263] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   14.126034] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.126290] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.296366] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   14.296376] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   14.296385] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   14.348253] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   14.348319] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[   14.356265] type=1400 audit(1345486551.733:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=643 comm="apparmor_parser"
[   14.356871] type=1400 audit(1345486551.733:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
[   14.357210] type=1400 audit(1345486551.733:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=643 comm="apparmor_parser"
[   14.365416] [drm] initialized overlay support
[   14.385106] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:ae:6b:0a
[   14.538249] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   14.575602] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   14.581769] init: failsafe main process (652) killed by TERM signal
[   14.809304] type=1400 audit(1345486552.185:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=756 comm="apparmor_parser"
[   14.813499] type=1400 audit(1345486552.189:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=761 comm="apparmor_parser"
[   14.819875] type=1400 audit(1345486552.193:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=761 comm="apparmor_parser"
[   14.826222] type=1400 audit(1345486552.201:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=761 comm="apparmor_parser"
[   14.878792] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.880618] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.913888] type=1400 audit(1345486552.289:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=762 comm="apparmor_parser"
[   14.936862] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   15.134041] fbcon: inteldrmfb (fb0) is primary device
[   15.134237] Console: switching to colour frame buffer device 160x50
[   15.134276] fb0: inteldrmfb frame buffer device
[   15.134278] drm: registered panic notifier
[   15.134340] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.134396] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.134489] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   15.134527] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.348474] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.356289] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.434028] init: alsa-restore main process (848) terminated with status 19
[   17.816218] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   17.816223] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   17.816529] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.688029] eth0: no IPv6 routers present"

Network Configuration...

[    0.181441] pnp 00:01: [mem 0x40000000-0xefffffff window]
[    0.181444] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
[    0.181447] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
[    0.181450] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
[    0.181453] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
[    0.181457] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.181460] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.181538] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.181562] pnp 00:02: [io  0x0092]
[    0.181565] pnp 00:02: [io  0x00b2]
[    0.181568] pnp 00:02: [io  0x0020-0x0021]
[    0.181571] pnp 00:02: [io  0x00a0-0x00a1]
[    0.181574] pnp 00:02: [irq 0 disabled]
[    0.181577] pnp 00:02: [io  0x04d0-0x04d1]
[    0.181583] pnp 00:02: [io  0x1000-0x1005]
[    0.181586] pnp 00:02: [io  0x1008-0x100f]
[    0.181602] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181606] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181654] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.181658] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.181682] pnp 00:03: [io  0xf400-0xf4fe]
[    0.181685] pnp 00:03: [io  0x0086]
[    0.181688] pnp 00:03: [io  0x00b3]
[    0.181690] pnp 00:03: [io  0x1006-0x1007]
[    0.181693] pnp 00:03: [io  0x100a-0x1059]
[    0.181696] pnp 00:03: [io  0x1060-0x107f]
[    0.181699] pnp 00:03: [io  0x1080-0x10bf]
[    0.181702] pnp 00:03: [io  0x10c0-0x10df]
[    0.181704] pnp 00:03: [io  0x1010-0x102f]
[    0.181707] pnp 00:03: [io  0x0809]
[    0.181723] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181728] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181732] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181736] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.181782] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.181786] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.181794] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.181797] system 00:03: [io  0x0809] has been reserved
[    0.181802] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.181838] pnp 00:04: [irq 12]
[    0.181879] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.181901] pnp 00:05: [io  0x0060]
[    0.181904] pnp 00:05: [io  0x0064]
[    0.181906] pnp 00:05: [io  0x0062]
[    0.181909] pnp 00:05: [io  0x0066]
[    0.181915] pnp 00:05: [irq 1]
[    0.181952] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.181973] pnp 00:06: [io  0x0070-0x0071]
[    0.181980] pnp 00:06: [irq 8]
[    0.181982] pnp 00:06: [io  0x0072-0x0077]
[    0.182022] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.182045] pnp 00:07: [io  0x0061]
[    0.182048] pnp 00:07: [io  0x0063]
[    0.182050] pnp 00:07: [io  0x0065]
[    0.182053] pnp 00:07: [io  0x0067]
[    0.182090] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.182110] pnp 00:08: [io  0x0c80-0x0cff]
[    0.182114] pnp 00:08: [io  0x0910-0x091f]
[    0.182116] pnp 00:08: [io  0x0920-0x092f]
[    0.182119] pnp 00:08: [io  0x0cb0-0x0cbf]
[    0.182122] pnp 00:08: [io  0x0930-0x097f]
[    0.182184] system 00:08: [io  0x0c80-0x0cff] could not be reserved
[    0.182188] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.182192] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.182195] system 00:08: [io  0x0cb0-0x0cbf] has been reserved
[    0.182199] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.182203] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.182227] pnp 00:09: [dma 4]
[    0.182230] pnp 00:09: [io  0x0000-0x000f]
[    0.182233] pnp 00:09: [io  0x0080-0x0085]
[    0.182236] pnp 00:09: [io  0x0087-0x008f]
[    0.182239] pnp 00:09: [io  0x00c0-0x00df]
[    0.182241] pnp 00:09: [io  0x0010-0x001f]
[    0.182244] pnp 00:09: [io  0x0090-0x0091]
[    0.182247] pnp 00:09: [io  0x0093-0x009f]
[    0.182288] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.182309] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.182316] pnp 00:0a: [irq 13]
[    0.182355] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.182414] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.182475] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.182480] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.182840] pnp: PnP ACPI: found 12 devices
[    0.182843] ACPI: ACPI bus type pnp unregistered
[    0.182847] PnPBIOS: Disabled by ACPI PNP
[    0.219925] PCI: max bus depth: 1 pci_try_num: 2
[    0.219973] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
[    0.219978] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.219982] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.219987] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.219995] pci 0000:00:1c.0:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.220014] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
[    0.220024] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
[    0.220029] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.220037] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefcfffff]
[    0.220043] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.220053] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.220061] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
[    0.220095] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.220103] pci 0000:00:1c.0: setting latency timer to 64
[    0.220117] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.220123] pci 0000:00:1c.3: setting latency timer to 64
[    0.220133] pci 0000:00:1e.0: setting latency timer to 64
[    0.220139] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.220142] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.220146] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.220149] pci_bus 0000:0b: resource 1 [mem 0xefd00000-0xefdfffff]
[    0.220153] pci_bus 0000:0b: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.220156] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
[    0.220159] pci_bus 0000:0c: resource 1 [mem 0xefa00000-0xefcfffff]
[    0.220163] pci_bus 0000:0c: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.220167] pci_bus 0000:03: resource 1 [mem 0xef900000-0xef9fffff]
[    0.220170] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.220173] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.220226] NET: Registered protocol family 2
[    0.220305] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.220572] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.221145] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.221527] TCP: Hash tables configured (established 131072 bind 65536)
[    0.221530] TCP reno registered
[    0.221534] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.221550] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.221685] NET: Registered protocol family 1
[    0.221713] pci 0000:00:02.0: Boot video device
[    0.221759] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.221783] pci 0000:00:1d.0: PCI INT A disabled
[    0.221797] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.221820] pci 0000:00:1d.1: PCI INT B disabled
[    0.221834] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.221857] pci 0000:00:1d.2: PCI INT C disabled
[    0.221871] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.221894] pci 0000:00:1d.3: PCI INT D disabled
[    0.221906] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.221946] pci 0000:00:1d.7: PCI INT A disabled
[    0.221980] PCI: CLS 64 bytes, default 64
[    0.222080] Simple Boot Flag at 0x79 set to 0x1
[    0.222533] audit: initializing netlink socket (disabled)
[    0.222548] type=2000 audit(1345486537.216:1): initialized
[    0.252852] Trying to unpack rootfs image as initramfs...
[    0.290794] highmem bounce pool size: 64 pages
[    0.290803] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.308170] VFS: Disk quotas dquot_6.5.2
[    0.308268] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.309059] fuse init (API version 7.17)
[    0.309191] msgmni has been set to 1702
[    0.324285] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.324337] io scheduler noop registered
[    0.324340] io scheduler deadline registered
[    0.324351] io scheduler cfq registered (default)
[    0.324517] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.324588] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.324688] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.324750] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    0.324872] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.324904] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.324994] intel_idle: MWAIT substates: 0x1110
[    0.324997] intel_idle: does not run on family 6 model 15
[    0.325492] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.325962] ACPI: AC Adapter [AC] (on-line)
[    0.326986] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.327460] ACPI: Lid Switch [LID]
[    0.327523] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.327529] ACPI: Power Button [PBTN]
[    0.327588] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.327593] ACPI: Sleep Button [SBTN]
[    0.327750] Marking TSC unstable due to TSC halts in idle
[    0.327764] ACPI: acpi_idle registered with cpuidle
[    0.338720] thermal LNXTHERM:00: registered as thermal_zone0
[    0.338725] ACPI: Thermal Zone [THM] (55 C)
[    0.338756] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.338775] ACPI: Battery Slot [BAT0] (battery present)
[    0.338856] ERST: Table is not found!
[    0.338858] GHES: HEST is not enabled!
[    0.338975] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.352311] isapnp: Scanning for PnP cards...
[    0.427443] Linux agpgart interface v0.103
[    0.427538] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.427614] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.427843] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.427994] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.429958] brd: module loaded
[    0.436784] loop: module loaded
[    0.437002] ata_piix 0000:00:1f.2: version 2.13
[    0.437039] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.437047] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.437099] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.440143] scsi0 : ata_piix
[    0.440250] scsi1 : ata_piix
[    0.453873] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.453878] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.454443] Fixed MDIO Bus: probed
[    0.454474] tun: Universal TUN/TAP device driver, 1.6
[    0.454476] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.454587] PPP generic driver version 2.4.2
[    0.454729] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.454757] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.454784] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.454789] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.454844] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.454870] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.454885] ehci_hcd 0000:00:1d.7: debug port 1
[    0.458769] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.458796] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.462751] ACPI: Battery Slot [BAT0] (battery present)
[    0.520052] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.520275] hub 1-0:1.0: USB hub found
[    0.520281] hub 1-0:1.0: 8 ports detected
[    0.520403] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.520425] uhci_hcd: USB Universal Host Controller Interface driver
[    0.520467] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.520482] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.520487] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.520547] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.520585] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.520756] hub 2-0:1.0: USB hub found
[    0.520761] hub 2-0:1.0: 2 ports detected
[    0.520845] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.520855] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.520860] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.520914] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.520962] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.521130] hub 3-0:1.0: USB hub found
[    0.521140] hub 3-0:1.0: 2 ports detected
[    0.521218] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.521228] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.521233] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.521288] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.521331] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.521491] hub 4-0:1.0: USB hub found
[    0.521496] hub 4-0:1.0: 2 ports detected
[    0.521576] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.521586] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.521591] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.521640] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.521683] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.521855] hub 5-0:1.0: USB hub found
[    0.521860] hub 5-0:1.0: 2 ports detected
[    0.522003] usbcore: registered new interface driver libusual
[    0.522084] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.528479] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.528492] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.528681] mousedev: PS/2 mouse device common for all mice
[    0.528900] rtc_cmos 00:06: RTC can wake from S4
[    0.529065] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.529101] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.529212] device-mapper: uevent: version 1.0.3
[    0.529307] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.529352] EISA: Probing bus 0 at eisa.0
[    0.529361] Cannot allocate resource for EISA slot 1
[    0.529364] Cannot allocate resource for EISA slot 2
[    0.529391] EISA: Detected 0 cards.
[    0.529403] cpufreq-nforce2: No nForce2 chipset.
[    0.529451] cpuidle: using governor ladder
[    0.529520] cpuidle: using governor menu
[    0.529523] EFI Variables Facility v0.08 2004-May-17
[    0.529818] TCP cubic registered
[    0.529990] NET: Registered protocol family 10
[    0.530625] NET: Registered protocol family 17
[    0.530631] Registering the dns_resolver key type
[    0.530670] Using IPI No-Shortcut mode
[    0.530950] PM: Hibernation image not present or could not be loaded.
[    0.530964] registered taskstats version 1
[    0.534902] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.620796] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[    0.624695] ata1.00: ATA-8: TOSHIBA MK1246GSX, LB212D, max UDMA/100
[    0.624700] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.633127] ata1.00: configured for UDMA/100
[    0.636364] ata2.00: configured for UDMA/33
[    1.047643] isapnp: No Plug & Play device found
[    1.047852] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    1.048114] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.048356] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.048421] sd 0:0:0:0: [sda] Write Protect is off
[    1.048425] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.048453] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.052161] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[    1.057115] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.057120] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.057300] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.057493] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.101986] Freeing initrd memory: 13820k freed
[    1.110799]  sda: sda1 sda2 < sda5 >
[    1.111428] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.120390]   Magic number: 8:145:292
[    1.120441] tty tty25: hash matches
[    1.120518] rtc_cmos 00:06: setting system clock to 2012-08-20 18:15:38 UTC (1345486538)
[    1.120540] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.120542] EDD information not available.
[    1.120750] Freeing unused kernel memory: 712k freed
[    1.121070] Write protecting the kernel text: 5616k
[    1.121110] Write protecting the kernel read-only data: 2324k
[    1.146671] udevd[85]: starting version 175
[    1.383747] sdhci: Secure Digital Host Controller Interface driver
[    1.383751] sdhci: Copyright(c) Pierre Ossman
[    1.399694] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.399729] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.400784] mmc0: no vmmc regulator found
[    1.401822] Registered led device: mmc0::
[    1.423149] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.423198] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.487413] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.629240] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.988151] firewire_core: created device fw0: GUID 464fc0001a213470, S400
[   12.662682] udevd[298]: starting version 175
[   12.729408] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k 
[   12.740861] lp: driver loaded but no devices found
[   12.770547] cfg80211: Calling CRDA to update world regulatory domain
[   12.934808] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.934813] Copyright(c) 2003-2011 Intel Corporation
[   13.090400] wmi: Mapper loaded
[   13.124324] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.408366] Bluetooth: Core ver 2.16
[   13.408440] lib80211: common routines for IEEE802.11 drivers
[   13.408444] lib80211_crypt: registered algorithm 'NULL'
[   13.412087] NET: Registered protocol family 31
[   13.412092] Bluetooth: HCI device and connection manager initialized
[   13.412097] Bluetooth: HCI socket layer initialized
[   13.412099] Bluetooth: L2CAP socket layer initialized
[   13.412109] Bluetooth: SCO socket layer initialized
[   13.414472] ppdev: user-space parallel port driver
[   13.437576] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.437581] Bluetooth: BNEP filters: protocol multicast
[   13.462902] Bluetooth: RFCOMM TTY layer initialized
[   13.462909] Bluetooth: RFCOMM socket layer initialized
[   13.462912] Bluetooth: RFCOMM ver 1.11
[   13.580360] intel_rng: FWH not detected
[   13.581993] acpi device:28: registered as cooling_device1
[   13.582398] leds_ss4200: no LED devices found
[   13.616460] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[   13.616599] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   13.616635] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   13.617036] type=1400 audit(1345486550.993:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=561 comm="apparmor_parser"
[   13.617755] type=1400 audit(1345486550.993:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=561 comm="apparmor_parser"
[   13.659433] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.659445] r592 0000:03:01.2: setting latency timer to 64
[   13.695050] r592: driver successfully loaded
[   13.697190] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.697202] r852 0000:03:01.3: setting latency timer to 64
[   13.701410] r852: Non dma capable device detected, dma disabled
[   13.701429] r852: driver loaded successfully
[   13.712448] [drm] Initialized drm 1.1.0 20060810
[   13.719722] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.719727] Disabling lock debugging due to kernel taint
[   13.816444] cfg80211: World regulatory domain updated:
[   13.816449] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.816453] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.816457] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.816461] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.816464] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.816468] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.818312] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.818320] i915 0000:00:02.0: setting latency timer to 64
[   13.823426] wl 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.823437] wl 0000:0b:00.0: setting latency timer to 64
[   13.832410] malloc in abgphy done
[   13.832561] eth%d: 5.100.82.38 driver failed with code 21
[   13.871285] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.871290] [drm] Driver supports precise vblank timestamp query.
[   13.934917] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.965797] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[   14.032230] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   14.032247] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   14.032261] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   14.032271] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   14.125263] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   14.126034] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.126290] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.296366] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   14.296376] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   14.296385] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   14.348253] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   14.348319] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[   14.356265] type=1400 audit(1345486551.733:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=643 comm="apparmor_parser"
[   14.356871] type=1400 audit(1345486551.733:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
[   14.357210] type=1400 audit(1345486551.733:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=643 comm="apparmor_parser"
[   14.365416] [drm] initialized overlay support
[   14.385106] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1d:09:ae:6b:0a
[   14.538249] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   14.575602] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   14.581769] init: failsafe main process (652) killed by TERM signal
[   14.809304] type=1400 audit(1345486552.185:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=756 comm="apparmor_parser"
[   14.813499] type=1400 audit(1345486552.189:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=761 comm="apparmor_parser"
[   14.819875] type=1400 audit(1345486552.193:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=761 comm="apparmor_parser"
[   14.826222] type=1400 audit(1345486552.201:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=761 comm="apparmor_parser"
[   14.878792] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.880618] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.913888] type=1400 audit(1345486552.289:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=762 comm="apparmor_parser"
[   14.936862] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   15.134041] fbcon: inteldrmfb (fb0) is primary device
[   15.134237] Console: switching to colour frame buffer device 160x50
[   15.134276] fb0: inteldrmfb frame buffer device
[   15.134278] drm: registered panic notifier
[   15.134340] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.134396] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.134489] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   15.134527] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.348474] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.356289] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.434028] init: alsa-restore main process (848) terminated with status 19
[   17.816218] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   17.816223] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   17.816529] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.688029] eth0: no IPv6 routers present
laura@laura-MM061:~$ sudo lshw -C network
[sudo] password for laura: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ae:6b:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

iwlist scan..

"lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning."

kernel/architecture...

"3.2.0-29-generic i686"

on restarting the network...

" * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] "


I know that is a lot of information, hopefully covers everything as asked for in the "How to Post a Wireless Issue" guide. I would be hugely grateful if someone could assist!

---

### Post by chili555 on 2012-08-20
You seem to have two conflicting wireless drivers in place:> [ 13.719722] wl: module license 'MIXED/Proprietary' taints kernel.
<snip>
[ 13.965797] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64Before we jump the gun, let's confirm your exact device. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by T Bone on 2012-08-20
Hi, and thanks...

The two conflicting drivers might be a result of me being an idiot and trying various fixes last night, gleaned from various threads, based on my lack of knowledge; though it did work for at least an hour.

I ran what you suggested and I got..

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by chili555 on 2012-08-20
Been there and done that, my friend!!

Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```After it's done, reboot and let us hear your report.

---

### Post by T Bone on 2012-08-20
Working like a dream! 

Many, many thanks Chili555! I will now be able to relax, been stressing out about this for a day and a half now! If you fancy a pint of awful Scottish beer I'll be glad to shout you one or three.

Cheers!

---

### Post by chili555 on 2012-08-20
Awesome! Reach up there to thread tools at the top and mark Solved, please. By the way, i 10v3 c01d b33r.

---

### Post by T Bone on 2012-08-20
Now marked solved. If you ever find yourself in this neck of the woods, I'll be happy to indulge your taste for beer :)

---

### Post by waleedahmed121 on 2012-09-13
> **chili555 said:**
> Been there and done that, my friend!!

Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```After it's done, reboot and let us hear your report.
hay [chili555]("http://ubuntuforums.org/member.php?u=35909"), I run the command, restart my laptop, but after restart, its saying that wireless is diabled by hardware switch.  the wireless switch is (fn+f2). I try to enable it by these keys, but nothing happens. I also have windows 7 on this machine, its working fine on it.

---

### Post by chili555 on 2012-09-13
Let's see:```
lsb_release -d
rfkill list all
lspci -nn | grep 0280
```Thanks.

---

### Post by jz5168 on 2012-10-16
Hi,

I have the identical laptop (Dell Inspiron 6400) and I followed this thread and ran this command: 

lspci -nn | grep 0280


and I got identical result:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Can you please post the solution?  That was not clear after reading this whole thread.  Thank you.

---

### Post by jz5168 on 2012-10-16
All I did is installed Ubuntu 12.04 (with Ethernet cable connected when installing), and I got no wireless connection when I remove the cable.  I also ran this command:

sudo rfkill list all

and the output is:

dell-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

I disabled Fn+F2 at the boot level, so only wifi is on and bluetooth is off and Fn+F2 has no effect (so it is always on).

Please post the solution, I really need it, thanks

---

### Post by chili555 on 2012-10-16
> 0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] (rev 01)
Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```It may or may not be there to be removed; that's fine, please continue.```
sudo apt-get install linux-firmware-nonfree
```Reboot and enjoy your wireless.

---

### Post by ahallubuntu on 2012-10-16
As an alternative: I should point out that I've upgraded the wireless cards in a couple of 6400's (same as E1505).  My E1505 came with an Intel 3945ABG card that worked automatically in all the newer versions of Ubuntu, but I upgraded it to an Intel 5100 (full height not half height) card to get 802.11n speeds.  There are some reports of issues with 802.11n with this card but I have never had a problem with Ubuntu running on this card at full speed.

You can buy a used Intel 5100 full height card for under $10 USD  shipped on eBay.  (Don't buy a "new" one shipped from Asia - I've had bad luck with those, seem to be a lot of engineering samples or something.)  You don't have to get a "Dell" card, but make sure you DON'T get the HP or Lenovo version!  It actually will work in Linux but not if you ever try to boot Windows again...

To replace the card, pop off the cover above the keyboard with a flat screwdriver and remove the keyboard - the card is in the upper right corner above the keyboard.  Pop off the two antenna wires (carefully), replace the card and the wires and that's it.

---

### Post by Raiyan Kamal on 2012-10-17
I have the same machine and faced the same problem. 
rfkill list all showed hard blocked: Yes. 
I pressed Fn+F2 once, the small LED in the front that indicates wifi status blinked once. 
I pressed Fn+F2 once again, the indicator LED stayed ON. I chekced with rfkill list all again, this time all the bloked were "no". Not sure why, but pressing Fn+F2 twice helped in my case.

---

### Post by lavallie on 2012-10-25
> **chili555 said:**
> Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```It may or may not be there to be removed; that's fine, please continue.```
sudo apt-get install linux-firmware-nonfree
```Reboot and enjoy your wireless.
This did the trick for me!!!  Thanks for your help.....

---

