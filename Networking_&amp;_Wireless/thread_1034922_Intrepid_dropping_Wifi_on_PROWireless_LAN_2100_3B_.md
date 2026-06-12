---
title: "Intrepid dropping Wifi on PRO/Wireless LAN 2100 3B Mini PCI Adapter"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by inspired on 2009-01-09
Hi folks,
I have recently installed ubuntu 8.10 (intrepid) onto an HP compaq nx7010 laptop. I was very happy to discover that everything worked out of the box. No messing around. Wonderful.

I have, however, found that the wireless connection is unstable. Usually when I first boot up it works for a while. But then it starts to drop out a lot and won't reconnect. Whilst trying to reconnect it will often prompt me for the WPA key again.

I have now plugged in a PCMCIA Wifi card and that works without any issues, even though it gets a signal of about 12% coming in and the built in wifi gets one at about 90%.

Here is the built in wifi info:
```
description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1
                version: 04
                serial: 00:0c:f1:27:f6:24
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=128 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
```

The security uses "WPA & WPA2 Personal".

Let me know if there is any other info that would be helpful.

I read some old info related to Ubuntu 7.10 about a similar issue. The suggested solution there was updating the driver because apparently the one shipping with that version of Ubuntu was outdated. I had no way of figuring out if that was still the case, so I figure it best I ask here.

I'd appreciate any help in sorting this out.

With thanks,

Jonathan

---

### Post by inspired on 2009-01-09
UPDATE: I've since discovered it has trouble with the PCMCIA Wifi too. It appears to be related to the distance from the Wifi station. I have no problem when using the same PCMCIA on a windows machine. Just on this one. So perhaps Ubuntu networking is not so good at handling transmission errors or dropouts, if that's what's causing this issue. When I come close to the station so far it does not seem to lose connection.

---

### Post by inspired on 2009-01-10
UPDATE:
I've continued trying to sort this issue out. I have now got the signal stronger by repositioning the Wifi station.
I have tested the PCMCIA wifi card on an XP laptop located right next to this Ubuntu one. It has no connection issues.

On this Ubuntu machine the connection will start up fine. It shows a signal strength of about 80 to 90%. It fluctuates between these levels for perhaps 20 to 30 seconds and then drops to 0% and many times will disconnect very briefly and then it will reconnect and jump back up to 80-90%.

Sometimes the disconnects are a little longer (perhaps a second as opposed to just milliseconds) in which case it breaks a page downloading in Firefox or a file downloading in firefox, etc.

I think it seems to certainly be something to do with Ubuntu because the same hardware on XP is fine. Any thoughts? Is there anything I can do to make the connection more stable? I'd really like to...

Much thanks,

Jonathan

PS. I've now read [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

So here is the info suggested:
```
Model: HP Compac nx7010
Part Number: DJ344A#AK8

```

Network adapter info
```
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)

and also this adapter is another one I am trying, which seems to be okay

Bus 001 Device 003: ID 0b3b:5630 Tekram Technology Co., Ltd ZD1211
```

This is the config details for the one causing the most trouble (the intel one built into the laptop... the first in the above two mentioned)

```
eth1 Link encap:Ethernet HWaddr 00:0c:f1:27:f6:24
inet addr:192.168.0.215 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::20c:f1ff:fe27:f624/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:63849 errors:141 dropped:119 overruns:0 frame:0
TX packets:47138 errors:0 dropped:0 overruns:0 carrier:2
collisions:0 txqueuelen:1000
RX bytes:82816321 (82.8 MB) TX bytes:3909939 (3.9 MB)
Interrupt:5 Base address:0x6000 Memory:90000000-90000fff 
```

and

```
wlan0 Link encap:Ethernet HWaddr 00:01:e3:44:65:a4
inet addr:192.168.0.220 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::201:e3ff:fe44:65a4/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:24770 errors:0 dropped:0 overruns:0 frame:0
TX packets:12211 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:34941064 (34.9 MB) TX bytes:1140532 (1.1 MB)

```

OTher wireless config info

```
eth1 IEEE 802.11b ESSID:"Kiwi2" Nickname:"Kiwi-Wireless"
Mode:Managed Frequency:2.462 GHz Access Point: 00:01:E3:4B:A8:C0
Bit Rate=5.5 Mb/s Tx-Power:16 dBm
Retry short limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=81/100 Signal level=-77 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:184 Missed beacon:22


wlan0 IEEE 802.11bg ESSID:"Kiwi2"
Mode:Managed Frequency:2.462 GHz Access Point: 00:01:E3:4B:A8:C0
Bit Rate=11 Mb/s Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality=94/100 Signal level:24/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

Here is the module info. Sorry, I couldn't figure out how to only get wifi related module info.
```
Module                  Size  Used by
af_packet              25728  6 
radeon                147616  2 
drm                    86056  3 radeon
binfmt_misc            16904  1 
rfcomm                 44432  2 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  16 rfcomm,bnep
vboxnetflt             92040  0 
vboxdrv               118824  1 vboxnetflt
ipv6                  263972  12 
ppdev                  15620  0 
speedstep_centrino     15360  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
lp                     17156  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
pcmcia                 43052  0 
zd1211rw               53124  0 
mac80211              216820  1 zd1211rw
joydev                 18368  0 
evdev                  17696  9 
btusb                  19736  3 
cfg80211               32392  1 mac80211
bluetooth              61924  11 rfcomm,sco,bnep,l2cap,btusb
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
psmouse                45200  0 
serio_raw              13444  0 
wbsd                   22280  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
mmc_core               58268  1 wbsd
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
container              11520  0 
video                  25104  0 
output                 11008  1 video
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
ipw2100                78384  0 
snd_seq_dummy          10884  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              38088  1 ipw2100
ieee80211_crypt        13572  1 ieee80211
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
battery                18436  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac                     12292  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  1 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  2 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
libusual               27156  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ohci1394               37936  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
8139cp                 27520  0 
ehci_hcd               43276  0 
ieee1394               96324  2 sbp2,ohci1394
uhci_hcd               30736  0 
8139too                31616  0 
mii                    13440  2 8139cp,8139too
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  7 zd1211rw,btusb,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fuse                   60828  3 
vesafb                 13828  1 
fbcon                  47648  72 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```


The output from dmesg is :

```
[    3.720659] hub 4-0:1.0: USB hub found
[    3.720668] hub 4-0:1.0: 2 ports detected
[    3.805280] Marking TSC unstable due to TSC halts in idle
[    3.929335] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.929348] pata_acpi 0000:00:1f.1: PCI INT A -> Link[C0C4] -> GSI 5 (level, low) -> IRQ 5
[    3.929391] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.929408] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.929494] 8139too 0000:02:01.0: This (id 10ec:8139 rev 20) is an enhanced 8139C+ chip
[    3.929498] 8139too 0000:02:01.0: Use the "8139cp" driver for improved performance and stability.
[    3.929513] 8139too 0000:02:01.0: PCI INT A -> Link[C0C3] -> GSI 10 (level, low) -> IRQ 10
[    3.929523] 8139too 0000:02:01.0: unknown chip version, assuming RTL-8139
[    3.929527] 8139too 0000:02:01.0: TxConfig = 0x74800000
[    3.930256] eth0: RealTek RTL8139 at 0x2000, 00:02:3f:6f:f0:1a, IRQ 10
[    3.930259] eth0:  Identified 8139 chip type 'RTL-8139'
[    3.937052] ohci1394 0000:02:00.0: PCI INT A -> Link[C0C2] -> GSI 10 (level, low) -> IRQ 10
[    3.989808] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[90200000-902007ff]  Max Packet=[1024]  IR/IT contexts=[4/8]
[    3.994833] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    3.995646] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.005857] ata_piix 0000:00:1f.1: version 2.12
[    4.005877] ata_piix 0000:00:1f.1: PCI INT A -> Link[C0C4] -> GSI 5 (level, low) -> IRQ 5
[    4.005928] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.006508] scsi0 : ata_piix
[    4.006649] scsi1 : ata_piix
[    4.007777] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4c40 irq 14
[    4.007781] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4c48 irq 15
[    4.125137] usb 1-5: configuration #1 chosen from 1 choice
[    4.218869] ata1.00: ATA-8: WDC WD1200BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.218874] ata1.00: 234441648 sectors, multi 16: LBA48
[    4.232628] ata1.00: configured for UDMA/100
[    4.308388] usb 1-1.4: new high speed USB device using ehci_hcd and address 5
[    4.396366] ata2.00: ATAPI: PIONEER DVD-RW  DVR-K17, 1.00, max UDMA/33
[    4.412313] ata2.00: configured for UDMA/33
[    4.412460] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.419333] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K17  1.00 PQ: 0 ANSI: 5
[    4.440218] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.440276] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.468787] Driver 'sd' needs updating - please use bus_type methods
[    4.468959] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.468986] sd 0:0:0:0: [sda] Write Protect is off
[    4.468989] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.469030] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.469129] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.469151] sd 0:0:0:0: [sda] Write Protect is off
[    4.469154] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.469194] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.469200]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.479248]  sda1 sda2 < sda5 sda6 sda7 >
[    4.530260] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.543185] sr0: scsi3-mmc drive: 31x/31x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.543192] Uniform CD-ROM driver Revision: 3.20
[    4.543324] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.608779] usb 1-1.4: configuration #1 chosen from 1 choice
[    4.848057] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.047389] usb 4-2: configuration #1 chosen from 1 choice
[    5.056162] usbcore: registered new interface driver libusual
[    5.071551] Initializing USB Mass Storage driver...
[    5.075928] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.080720] usbcore: registered new interface driver usb-storage
[    5.080726] USB Mass Storage support registered.
[    5.080863] usb-storage: device found at 5
[    5.080866] usb-storage: waiting for device to settle before scanning
[    5.268918] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f434a007a0e]
[   10.080213] usb-storage: device scan complete
[   10.158669] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   10.197013] EXT3-fs: INFO: recovery required on readonly filesystem.
[   10.197018] EXT3-fs: write access will be enabled during recovery.
[   10.548352] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   10.549099] hub 1-1:1.0: cannot reset port 4 (err = -71)
[   10.904291] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   11.384041] usb 1-1.4: device not accepting address 5, error -71
[   11.456360] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   11.595809] kjournald starting.  Commit interval 5 seconds
[   11.595829] EXT3-fs: sda6: orphan cleanup on readonly fs
[   11.595837] ext3_orphan_cleanup: deleting unreferenced inode 53048
[   11.595883] ext3_orphan_cleanup: deleting unreferenced inode 53014
[   11.595894] ext3_orphan_cleanup: deleting unreferenced inode 52278
[   11.595911] EXT3-fs: sda6: 3 orphan inodes deleted
[   11.595914] EXT3-fs: recovery complete.
[   11.603607] EXT3-fs: mounted filesystem with ordered data mode.
[   11.624427] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   12.108038] usb 1-1.4: device not accepting address 5, error -71
[   12.180325] usb 1-1.4: reset high speed USB device using ehci_hcd and address 5
[   18.469823] udevd version 124 started
[   19.304077] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.364418] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.461768] Linux agpgart interface v0.103
[   19.531929] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   19.657697] iTCO_vendor_support: vendor-support=0
[   19.682891] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[   19.711923] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   19.712109] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   19.712331] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.941730] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.956093] ACPI: Power Button (FF) [PWRF]
[   19.956346] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.972069] ACPI: Power Button (CM) [C1BE]
[   19.972256] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   19.972381] ACPI: Lid Switch [C136]
[   19.977659] intel_rng: FWH not detected
[   19.996000] ACPI: AC Adapter [C134] (on-line)
[   20.166771] ACPI: Battery Slot [C11F] (battery present)
[   20.869112] ieee80211_crypt: registered algorithm 'NULL'
[   20.931040] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.931045] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.131233] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   21.131238] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   21.140055] ipw2100 0000:02:02.0: PCI INT A -> Link[C0C5] -> GSI 5 (level, low) -> IRQ 5
[   21.140404] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   21.140420] firmware: requesting ipw2100-1.3.fw
[   21.741710] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[   21.753641] ACPI: Video Device [C0D0] (multi-head: yes  rom: no  post: no)
[   22.271099] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   22.271103] wbsd: Copyright(c) Pierre Ossman
[   22.272108] wbsd 00:02: activated
[   22.296026] mmc0: W83L51xD id 7112 at 0x248 irq 6 dma 2 PnP
[   23.233595] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   23.478017] Bluetooth: Core ver 2.13
[   23.479123] NET: Registered protocol family 31
[   23.479126] Bluetooth: HCI device and connection manager initialized
[   23.479131] Bluetooth: HCI socket layer initialized
[   23.663910] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   23.664866] usbcore: registered new interface driver btusb
[   23.874918] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   23.926571] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   23.944990] parport_pc 00:05: reported by Plug and Play ACPI
[   23.945041] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.076718] Intel ICH 0000:00:1f.5: PCI INT B -> Link[C0C3] -> GSI 10 (level, low) -> IRQ 10
[   26.076755] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.076788] Yenta: CardBus bridge found at 0000:02:04.0 [0e11:0860]
[   26.076808] Yenta: Using CSCINT to route CSC interrupts to PCI
[   26.076811] Yenta: Routing CardBus interrupts to PCI
[   26.076816] Yenta TI: socket 0000:02:04.0, mfunc 0x001c1112, devctl 0x44
[   26.308400] Yenta: ISA IRQ mask 0x0818, PCI irq 5
[   26.308405] Socket status: 30000006
[   26.308409] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   26.308418] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   26.308422] cs: IO port probe 0x2000-0x2fff: clean.
[   26.308682] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x903fffff
[   26.308686] pcmcia: parent PCI bridge Memory window: 0x70000000 - 0x73ffffff
[   26.320102] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[   26.461824] phy0: Selected rate control algorithm 'pid'
[   26.567718] zd1211rw 1-5:1.0: phy0
[   26.567753] usbcore: registered new interface driver zd1211rw
[   26.631159] cs: IO port probe 0x100-0x3af: clean.
[   26.633086] cs: IO port probe 0x3e0-0x4ff: clean.
[   26.633813] cs: IO port probe 0x820-0x8ff: clean.
[   26.634454] cs: IO port probe 0xc00-0xcf7: clean.
[   26.635275] cs: IO port probe 0xa00-0xaff: clean.
[   27.000043] intel8x0_measure_ac97_clock: measured 55416 usecs
[   27.000047] intel8x0: clocking to 48000
[   30.314716] lp0: using parport0 (interrupt-driven).
[   30.965361] EXT3 FS on sda6, internal journal
[   36.100614] kjournald starting.  Commit interval 5 seconds
[   36.100964] EXT3 FS on sda5, internal journal
[   36.100971] EXT3-fs: mounted filesystem with ordered data mode.
[   36.455716] type=1505 audit(1231605455.299:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4170
[   36.709164] type=1505 audit(1231605455.555:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4175
[   36.709540] type=1505 audit(1231605455.555:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4175
[   36.867344] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.515580] ACPI: WMI: Mapper loaded
[   38.663013] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   38.759470] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.759479] apm: overridden by ACPI.
[   38.953250] ppdev: user-space parallel port driver
[   42.124043] Clocksource tsc unstable (delta = -185453352 ns)
[   44.592514] NET: Registered protocol family 10
[   44.594772] lo: Disabled Privacy Extensions
[   45.627138] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   45.627161] vboxdrv: Successfully done.
[   45.627168] vboxdrv: Found 1 processor cores.
[   45.633254] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   45.633273] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   49.871671] Bluetooth: L2CAP ver 2.11
[   49.871690] Bluetooth: L2CAP socket layer initialized
[   49.906594] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   49.906613] Bluetooth: BNEP filters: protocol multicast
[   49.947165] Bluetooth: RFCOMM socket layer initialized
[   49.947447] Bluetooth: RFCOMM TTY layer initialized
[   49.947454] Bluetooth: RFCOMM ver 1.10
[   49.979290] Bridge firewalling registered
[   49.979702] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   50.008521] Bluetooth: SCO (Voice Link) ver 0.6
[   50.008530] Bluetooth: SCO socket layer initialized
[   51.014927] pci 0000:01:00.0: PCI INT A -> Link[C0C2] -> GSI 10 (level, low) -> IRQ 10
[   51.343796] [drm] Initialized drm 1.1.0 20060810
[   51.383181] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   51.591361] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   51.591416] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   51.591484] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   51.840096] [drm] Setting GART location based on new memory map
[   51.840112] [drm] Loading R200 Microcode
[   51.840168] [drm] writeback test succeeded in 2 usecs
[   54.120600] eth0: link down
[   54.121145] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.241404] firmware: requesting zd1211/zd1211_ub
[   54.259840] firmware: requesting zd1211/zd1211_uphr
[   54.341180] zd1211rw 1-5:1.0: firmware version 4605
[   54.381176] zd1211rw 1-5:1.0: zd1211 chip 0b3b:5630 v4330 high 00-01-e3 RF2959_RF pa0 -----
[   54.441075] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.506521] NET: Registered protocol family 17
[   55.341824] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[   55.343547] wlan0: authenticated
[   55.343565] wlan0: associate with AP 00:01:e3:4b:a8:c0
[   55.345547] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[   55.345563] wlan0: associated
[   55.347946] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.349454] wlan0: disassociating by local choice (reason=3)
[   64.964039] eth1: no IPv6 routers present
[   66.068040] wlan0: no IPv6 routers present
[  111.813922] UDF-fs: Partition marked readonly; forcing readonly mount
[  111.964876] UDF-fs INFO UDF: Mounting volume 'Adobe CS4 Maste', timestamp 2008/10/21 10:00 (1078)
[  130.608280] ieee80211_crypt: registered algorithm 'CCMP'
[  131.005504] padlock: VIA PadLock not detected.
[  131.048965] ieee80211_crypt: registered algorithm 'TKIP'
[  141.264097] usb 4-2: USB disconnect, address 2
[  141.267614] btusb_intr_complete: hci0 urb ef6d0d00 failed to resubmit (19)
[  141.272545] btusb_send_frame: hci0 urb ef5f2280 submission failed
[  143.496090] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  143.705472] usb 4-2: configuration #1 chosen from 1 choice
[  150.967228] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  150.969073] wlan0: authenticated
[  150.969094] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  150.971770] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  150.971789] wlan0: associated
[  150.974611] wlan0: disassociating by local choice (reason=3)
[  151.891862] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  151.896707] wlan0: authenticated
[  151.896733] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  151.899884] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  151.899903] wlan0: associated
[  187.546898] ppdev0: registered pardevice
[  187.596874] ppdev0: unregistered pardevice
[  188.408408] ppdev0: registered pardevice
[  188.456897] ppdev0: unregistered pardevice
[  188.566944] ppdev0: registered pardevice
[  188.616086] ppdev0: unregistered pardevice
[  229.954809] wlan0: disassociating by local choice (reason=3)
[  229.984792] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  229.987197] wlan0: authenticated
[  229.987210] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  229.989488] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  229.989498] wlan0: associated
[  229.990655] wlan0: disassociating by local choice (reason=3)
[  230.908635] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  230.911276] wlan0: authenticated
[  230.911288] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  230.914329] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  230.914338] wlan0: associated
[  241.120373] wlan0: disassociating by local choice (reason=3)
[  241.161688] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  241.163649] wlan0: authenticated
[  241.163662] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  241.165567] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  241.165577] wlan0: associated
[  242.075389] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  242.272212] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  242.276108] wlan0: authenticated
[  242.276123] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  242.278243] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  242.278252] wlan0: associated
[  270.102456] ipw2100: Fatal interrupt. Scheduling firmware restart.
[  270.133104] ipw2100: Fatal interrupt. Scheduling firmware restart.
[  389.056117] ipw2100: exit - failed to send CARD_DISABLE command
[  389.547346] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  441.737824] wlan0: disassociating by local choice (reason=3)
[  441.775233] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  441.776979] wlan0: authenticated
[  441.776988] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  441.779199] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  441.779207] wlan0: associated
[  441.781320] wlan0: disassociating by local choice (reason=3)
[  442.743037] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  442.758544] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  442.758586] wlan0: authenticated
[  442.758590] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  442.763529] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  442.763539] wlan0: associated
[  474.488276] wlan0: disassociating by local choice (reason=3)
[  474.525622] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[  474.527388] wlan0: authenticated
[  474.527398] wlan0: associate with AP 00:01:e3:4b:a8:c0
[  474.529613] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[  474.529623] wlan0: associated
[  474.530962] wlan0: disassociating by local choice (reason=3)
[  475.475365] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  475.476981] wlan0: authenticated
[  475.476999] wlan0: associate with AP 00:1c:f0:5f:89:23
[  475.479859] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  475.479875] wlan0: associated
[  485.484166] wlan0: disassociating by local choice (reason=3)
[  486.108313] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  486.109939] wlan0: authenticated
[  486.109947] wlan0: associate with AP 00:1c:f0:5f:89:23
[  486.113061] wlan0: RX ReassocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  486.113069] wlan0: associated
[  555.364850] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  555.367886] wlan0: authenticated
[  555.367902] wlan0: associate with AP 00:1c:f0:5f:89:23
[  555.370642] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  555.370652] wlan0: associated
[  555.472139] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  565.376223] wlan0: disassociating by local choice (reason=3)
[  565.662465] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  565.664460] wlan0: authenticated
[  565.664480] wlan0: associate with AP 00:1c:f0:5f:89:23
[  565.667337] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  565.667355] wlan0: associated
[  565.668926] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  570.038650] ieee80211_crypt: registered algorithm 'WEP'
[  575.672267] wlan0: disassociating by local choice (reason=3)
[  575.674537] wlan0: deauthenticated
[  575.904056] wlan0: no IPv6 routers present
[  576.672255] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  576.674026] wlan0: authenticated
[  576.674037] wlan0: associate with AP 00:1c:f0:5f:89:23
[  576.676846] wlan0: RX ReassocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  576.676855] wlan0: associated
[  577.586226] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  577.587952] wlan0: authenticated
[  577.587966] wlan0: associate with AP 00:1c:f0:5f:89:23
[  577.590702] wlan0: RX ReassocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  577.590715] wlan0: associated
[  674.559067] wlan0: disassociating by local choice (reason=3)
[  674.561281] wlan0: deauthenticated
[  675.581011] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[  675.582622] wlan0: authenticated
[  675.582641] wlan0: associate with AP 00:1c:f0:5f:89:23
[  675.585393] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=5)
[  675.585411] wlan0: associated
[ 1116.122879] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[ 1116.193582] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1136.575531] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1157.637632] wlan0: disassociating by local choice (reason=3)
[ 1158.574489] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[ 1158.576101] wlan0: authenticated
[ 1158.576119] wlan0: associate with AP 00:1c:f0:5f:89:23
[ 1158.578964] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=4)
[ 1158.578981] wlan0: associated
[ 1158.581668] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1168.596179] wlan0: disassociating by local choice (reason=3)
[ 1169.102751] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[ 1169.104600] wlan0: authenticated
[ 1169.104617] wlan0: associate with AP 00:1c:f0:5f:89:23
[ 1169.107478] wlan0: RX ReassocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=4)
[ 1169.107494] wlan0: associated
[ 1169.408042] wlan0: no IPv6 routers present
[ 1179.112184] wlan0: disassociating by local choice (reason=3)
[ 1179.744003] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[ 1179.745828] wlan0: authenticated
[ 1179.745846] wlan0: associate with AP 00:1c:f0:5f:89:23
[ 1179.748585] wlan0: RX ReassocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=4)
[ 1179.748601] wlan0: associated
[ 1225.742815] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1231.891002] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1242.348042] eth1: no IPv6 routers present
[ 1549.122246] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 1551.907876] ipw2100: Fatal interrupt. Scheduling firmware restart.
[ 2885.223200] GlobalMenu.Pane[5808]: segfault at c ip b7388488 sp bfdd01a0 error 4 in libgmarkupdoc-base.so.0.0.0[b7385000+c000]
[ 4842.110969] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 4 bytes away.
[20309.203967] wlan0: disassociating by local choice (reason=3)
[20310.176240] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[20310.178198] wlan0: authenticated
[20310.178216] wlan0: associate with AP 00:01:e3:4b:a8:c0
[20310.180333] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[20310.180350] wlan0: associated
[20310.183196] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20320.672044] wlan0: no IPv6 routers present
[20369.067692] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[20369.069578] wlan0: authenticated
[20369.069590] wlan0: associate with AP 00:01:e3:4b:a8:c0
[20369.073046] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[20369.073061] wlan0: associated
[20369.153545] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20372.134846] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20431.768624] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20434.421305] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20543.880937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20551.398172] wlan0: disassociating by local choice (reason=3)
[20552.335096] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[20552.336995] wlan0: authenticated
[20552.337013] wlan0: associate with AP 00:01:e3:4b:a8:c0
[20552.339123] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[20552.339140] wlan0: associated
[20552.341217] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20563.080047] wlan0: no IPv6 routers present
[22150.237838] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[22150.237851] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[22150.237855] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[23064.207019] wlan0: disassociating by local choice (reason=3)
[23064.246445] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23064.248216] wlan0: authenticated
[23064.248227] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23064.250703] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x1 status=0 aid=4)
[23064.250713] wlan0: associated
[23064.251688] wlan0: disassociating by local choice (reason=3)
[23065.180831] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23065.203915] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23065.203976] wlan0: authenticated
[23065.203986] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23065.207981] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x1 status=0 aid=4)
[23065.208000] wlan0: associated
[23314.867059] wlan0: deauthenticated
[23315.211862] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23329.310006] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23329.318507] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23329.320501] wlan0: authenticated
[23329.320512] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23329.322745] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x1 status=0 aid=4)
[23329.322752] wlan0: associated
[23329.323419] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23340.308050] wlan0: no IPv6 routers present
[23734.559207] wlan0: deauthenticated
[23735.556065] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23735.557807] wlan0: authenticated
[23735.557826] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23735.560826] wlan0: RX ReassocResp from 00:01:e3:4b:a8:c0 (capab=0x1 status=0 aid=4)
[23735.560842] wlan0: associated
[23765.930211] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23765.938717] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23765.940724] wlan0: authenticated
[23765.940732] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23765.942843] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x1 status=0 aid=4)
[23765.942850] wlan0: associated
[23765.943668] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23776.060043] wlan0: no IPv6 routers present
[23776.277293] wlan0: authenticate with AP 00:1c:f0:5f:89:23
[23776.279312] wlan0: authenticated
[23776.279331] wlan0: associate with AP 00:1c:f0:5f:89:23
[23776.282018] wlan0: RX AssocResp from 00:1c:f0:5f:89:23 (capab=0x431 status=0 aid=2)
[23776.282035] wlan0: associated
[23784.948045] eth1: no IPv6 routers present
[23844.785793] wlan0: disassociating by local choice (reason=3)
[23844.788459] wlan0: deauthenticated
[23845.734670] wlan0: authenticate with AP 00:01:e3:4b:a8:c0
[23845.736548] wlan0: authenticated
[23845.736562] wlan0: associate with AP 00:01:e3:4b:a8:c0
[23845.738694] wlan0: RX AssocResp from 00:01:e3:4b:a8:c0 (capab=0x401 status=0 aid=4)
[23845.738703] wlan0: associated

```

NETWORK CONFIGURATION
*-network:1
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth1
version: 04
serial: 00:0c:f1:27:f6:24
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.215 latency=128 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
*-network:0
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:01:e3:44:65:a4
capabilities: ethernet physical wireless
configuration: broadcast=yes ip=192.168.0.220 multicast=yes wireless=IEEE 802.11bg


```
Ubuntu version is 8.10
Kernel is 2.6.27-9-generic i686 32bit
```

When I tried to restart the networking I got this output
* Reconfiguring network interfaces... Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth1=eth1.

---

