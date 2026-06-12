---
title: "Linux Mint D-Link DWA-140"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by kbz1960 on 2011-02-04
I purchased this usb wireless card because I read here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)
that it is supported out of the box. Well it works for a couple minutes and then drops the connection then asking for my security key again and never connecting again unless I unplug it and plug it back in and the loop starts again, connect, disconnect and don't connect again.

I've tried different usb ports, no change. So here is the info you would like to see and hope someone can help.

**1 ) Machine Brand and Model (PC/Laptop)**:
My system is a put together one I got from my brother-in-law. It's an intel D975XBX2 motherboard with an intel core 2 duo chip, nVidia GeForce 7300 GT video card, 2gig of ram

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]```
 $ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[B]3 ) check interface:
[/B]```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:67:08:77  
          inet6 addr: fe80::219:d1ff:fe67:877/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2666356 (2.6 MB)  TX bytes:559039 (559.0 KB)
          Interrupt:17 Memory:92100000-92120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19208 (19.2 KB)  TX bytes:19208 (19.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:91:7e:fa:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=2 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```[B]4 ) Check for modules:
[/B]```
lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  0 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
dm_crypt               13381  0 
rt2870sta             445182  0 
arc4                    1497  2 
rt2800usb               9955  0 
rt2800lib              31970  1 rt2800usb
rt2x00usb              11316  2 rt2800usb,rt2800lib
rt2x00lib              31575  2 rt2800lib,rt2x00usb
nvidia              10221046  38 
mac80211              266657  2 rt2x00usb,rt2x00lib
ipt_REJECT              2440  1 
ipt_LOG                 5394  5 
xt_limit                2204  7 
xt_tcpudp               2627  7 
ipt_addrtype            2175  4 
xt_state                1386  7 
ip6table_filter         1719  1 
ip6_tables             20633  1 ip6table_filter
nf_nat_irc              1601  0 
nf_conntrack_irc        4501  1 nf_nat_irc
nf_nat_ftp              1831  0 
nf_nat                 20067  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13143  9 nf_nat
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
nf_conntrack_ftp        7158  1 nf_nat_ftp
nf_conntrack           75238  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_hda_codec_idt      64667  1 
cfg80211              170293  2 rt2x00lib,mac80211
snd_hda_intel          26019  1 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1778  1 
ip_tables              19107  1 iptable_filter
x_tables               24423  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
ppdev                   6804  0 
crc_ccitt               1699  2 rt2870sta,rt2800usb
snd                    64117  11 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             30086  1 
i82975x_edac            3183  0 
psmouse                62080  0 
serio_raw               4910  0 
led_class               3393  1 rt2x00lib
soundcore               1240  1 snd
lp                     10201  0 
edac_core              46822  1 i82975x_edac
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
parport                37032  3 ppdev,parport_pc,lp
dm_raid45              75026  0 
usbhid                 42062  0 
hid                    84678  1 usbhid
xor                     4709  1 dm_raid45
btrfs                 506518  0 
zlib_deflate           21866  1 btrfs
crc32c                  3007  1 
libcrc32c               1268  1 btrfs
firewire_ohci          24679  0 
floppy                 65299  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
e1000e                151787  0 

```[B]5 ) Kernel boot messages
[/B]```
[    0.495746] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    0.496136] Fixed MDIO Bus: probed
[    0.496178] PPP generic driver version 2.4.2
[    0.496237] tun: Universal TUN/TAP device driver, 1.6
[    0.496239] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.496343] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.496364]   alloc irq_desc for 23 on node -1
[    0.496367]   alloc kstat_irqs on node -1
[    0.496374] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.496393] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.496397] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.496440] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.496463] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.496474] ehci_hcd 0000:00:1d.7: debug port 1
[    0.500343] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.500359] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x92204400
[    0.504428] ata2: port disabled. ignoring.
[    0.515000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.515154] hub 1-0:1.0: USB hub found
[    0.515162] hub 1-0:1.0: 8 ports detected
[    0.515253] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.515276] uhci_hcd: USB Universal Host Controller Interface driver
[    0.515339] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.515349] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.515354] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.515407] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.515436] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.515585] hub 2-0:1.0: USB hub found
[    0.515591] hub 2-0:1.0: 2 ports detected
[    0.515660] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.515667] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.515672] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.515718] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.515743] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.515883] hub 3-0:1.0: USB hub found
[    0.515890] hub 3-0:1.0: 2 ports detected
[    0.515961] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.515968] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.515972] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.516014] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.516048] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.516192] hub 4-0:1.0: USB hub found
[    0.516199] hub 4-0:1.0: 2 ports detected
[    0.516271] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.516278] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.516282] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.516324] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.516357] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    0.516506] hub 5-0:1.0: USB hub found
[    0.516513] hub 5-0:1.0: 2 ports detected
[    0.516668] PNP: No PS/2 controller found. Probing ports directly.
[    0.519746] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.519754] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.519886] mice: PS/2 mouse device common for all mice
[    0.520036] rtc_cmos 00:03: RTC can wake from S4
[    0.520081] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.520106] rtc0: alarms up to one month, 114 bytes nvram
[    0.520242] device-mapper: uevent: version 1.0.3
[    0.520332] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.520415] device-mapper: multipath: version 1.1.1 loaded
[    0.520418] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.520614] cpuidle: using governor ladder
[    0.520617] cpuidle: using governor menu
[    0.520994] TCP cubic registered
[    0.521155] NET: Registered protocol family 10
[    0.521598] lo: Disabled Privacy Extensions
[    0.521876] NET: Registered protocol family 17
[    0.522428] PM: Resume from disk failed.
[    0.522446] registered taskstats version 1
[    0.522697]   Magic number: 15:686:385
[    0.522703] usb usb3: hash matches
[    0.522717] thermal cooling_device0: hash matches
[    0.522789] rtc_cmos 00:03: setting system clock to 2011-02-04 15:22:51 UTC (1296832971)
[    0.522792] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.522794] EDD information not available.
[    0.677960] ata1.01: ATAPI: CREATIVE CD5233E-N,  0.20, max UDMA/33
[    0.695333] ata1.01: configured for UDMA/33
[    0.696052] scsi 0:0:1:0: CD-ROM            CREATIVE  CD5233E-N       0.20 PQ: 0 ANSI: 5
[    0.698271] sr0: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[    0.698275] Uniform CD-ROM driver Revision: 3.20
[    0.698396] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.698459] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    0.753657] Freeing initrd memory: 16580k freed
[    0.805699] ata3.00: ATA-6: ST3120026AS, 3.18, max UDMA/133
[    0.805704] ata3.00: 234441648 sectors, multi 16: LBA48 
[    0.845731] ata3.00: configured for UDMA/133
[    0.845834] scsi 2:0:0:0: Direct-Access     ATA      ST3120026AS      3.18 PQ: 0 ANSI: 5
[    0.845982] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.846029] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.846122] sd 2:0:0:0: [sda] Write Protect is off
[    0.846126] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.846158] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.846404]  sda: sda1 sda2 < sda5 >
[    0.870790] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.870827] Freeing unused kernel memory: 908k freed
[    0.871221] Write protecting the kernel read-only data: 10240k
[    0.871426] Freeing unused kernel memory: 416k freed
[    0.871811] Freeing unused kernel memory: 1644k freed
[    0.896760] udev[84]: starting version 163
[    0.955714] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.013533] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.013537] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.013567] e1000e 0000:03:00.0: Disabling ASPM  L1
[    1.013591] e1000e 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.013613] e1000e 0000:03:00.0: setting latency timer to 64
[    1.013803]   alloc irq_desc for 43 on node -1
[    1.013805]   alloc kstat_irqs on node -1
[    1.013827] e1000e 0000:03:00.0: irq 43 for MSI/MSI-X
[    1.014313] e1000e 0000:03:00.0: Disabling ASPM L0s 
[    1.026835] Floppy drive(s): fd0 is 1.44M
[    1.033820] firewire_ohci 0000:04:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.049378] FDC 0 is a post-1991 82077
[    1.085768] firewire_ohci: Added fw-ohci device 0000:04:04.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.170648] e1000e 0000:03:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:67:08:77
[    1.170653] e1000e 0000:03:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.170726] e1000e 0000:03:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    1.410039] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.600296] firewire_core: created device fw0: GUID 0090270001c4d663, S400
[    1.614337] Btrfs loaded
[    1.621246] xor: automatically using best checksumming function: generic_sse
[    1.661258]    generic_sse:  4881.200 MB/sec
[    1.661261] xor: using function: generic_sse (4881.200 MB/sec)
[    1.663527] usbcore: registered new interface driver hiddev
[    1.665104] device-mapper: dm-raid45: initialized v0.2594b
[    1.678780] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[    1.678914] generic-usb 0003:03F0:0024.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.678941] usbcore: registered new interface driver usbhid
[    1.678943] usbhid: USB HID core driver
[    1.810029] end_request: I/O error, dev fd0, sector 0
[    1.906698] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.910085] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    2.103631] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
[    2.103739] generic-usb 0003:046D:C018.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[   16.151167] udev[399]: starting version 163
[   16.216143] Adding 4805628k swap on /dev/sda5.  Priority:-1 extents:1 across:4805628k 
[   16.336309] leds_ss4200: no LED devices found
[   16.362650] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   16.421115] EDAC i82975x: ECC disabled on both channels.
[   16.446899] lp: driver loaded but no devices found
[   16.517998] parport_pc 00:09: reported by Plug and Play ACPI
[   16.518029] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   16.551544] ppdev: user-space parallel port driver
[   16.573663] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.595118] lp0: using parport0 (interrupt-driven).
[   16.600861] nvidia: module license 'NVIDIA' taints kernel.
[   16.600867] Disabling lock debugging due to kernel taint
[   16.605512] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.675065]   alloc irq_desc for 22 on node -1
[   16.675070]   alloc kstat_irqs on node -1
[   16.675079] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.675128]   alloc irq_desc for 44 on node -1
[   16.675130]   alloc kstat_irqs on node -1
[   16.675142] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   16.675175] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.793250] cfg80211: Calling CRDA to update world regulatory domain
[   16.841210] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.842612] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.842617] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   16.842619] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.874034] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   17.076633] cfg80211: World regulatory domain updated:
[   17.076638]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.076642]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.076646]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.076650]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.076653]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.076655]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.390172] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   17.390278] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   17.390353] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   17.390424] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.390507] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.390579] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.390653] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.588963] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.588974] nvidia 0000:01:00.0: setting latency timer to 64
[   17.588980] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.589288] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   17.730356] e1000e 0000:03:00.0: irq 43 for MSI/MSI-X
[   17.790142] e1000e 0000:03:00.0: irq 43 for MSI/MSI-X
[   17.790756] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.942495] phy0: Selected rate control algorithm 'minstrel'
[   17.943391] Registered led device: rt2800usb-phy0::radio
[   17.943415] Registered led device: rt2800usb-phy0::assoc
[   17.943440] Registered led device: rt2800usb-phy0::quality
[   17.943818] usbcore: registered new interface driver rt2800usb
[   18.009962] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.015954] rtusb init --->
[   18.016004] usbcore: registered new interface driver rt2870
[   18.483538] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.538013] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   32.482705] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[   32.484322] wlan0: authenticated
[   32.484348] wlan0: associate with 00:25:9c:9d:1e:2d (try 1)
[   32.500323] wlan0: RX AssocResp from 00:25:9c:9d:1e:2d (capab=0x431 status=0 aid=2)
[   32.500328] wlan0: associated
[   32.533451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.608028] Intel AES-NI instructions are not detected.
[   32.640423] padlock: VIA PadLock not detected.
[   42.561261] wlan0: no IPv6 routers present
[  116.741904] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:00:22:64:46:4d:72:08:00 SRC=192.168.1.102 DST=192.168.1.103 LEN=88 TOS=0x00 PREC=0x00 TTL=64 ID=7570 PROTO=UDP SPT=161 DPT=35751 LEN=68 
[  223.951272] No probe response from AP 00:25:9c:9d:1e:2d after 500ms, disconnecting.
[  224.101318] cfg80211: All devices are disconnected, going to restore regulatory settings
[  224.101325] cfg80211: Restoring regulatory settings
[  224.101331] cfg80211: Calling CRDA to update world regulatory domain
[  224.106754] cfg80211: World regulatory domain updated:
[  224.106760]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  224.106766]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  224.106770]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  224.106774]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  224.106778]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  224.106782]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  225.666577] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[  225.860016] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 2)
[  226.060017] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 3)
[  226.260026] wlan0: authentication with 00:25:9c:9d:1e:2d timed out
[  237.193949] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  237.390018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  237.590018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  237.790019] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  240.774114] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  240.971361] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  241.170023] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  241.370017] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  252.223975] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  252.421267] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  252.620017] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  252.821266] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  263.683956] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  263.880017] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  264.080037] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  264.280032] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  275.143937] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  275.341269] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  275.541270] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  275.741270] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  286.594663] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  286.790033] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  286.990035] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  287.190034] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  298.063907] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  298.261291] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  298.461286] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  298.661285] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  341.583637] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  341.780035] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  341.980034] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  342.180035] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  353.053881] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  353.250018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  353.450017] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  353.650016] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  364.513864] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  364.710018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  364.910021] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  365.110017] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  376.053209] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  376.250036] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  376.451269] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  376.651302] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  612.252968] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  612.451274] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  612.651273] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  612.850018] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  623.723961] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  623.921278] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  624.121286] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  624.321267] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  635.183763] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  635.380024] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  635.580020] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  635.780032] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  646.653672] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  646.851269] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  647.050045] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  647.250037] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  658.123914] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  658.321279] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  658.521286] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  658.721284] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  669.584355] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  669.780026] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  669.980034] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  670.180030] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  679.053166] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  679.250036] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  679.450032] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  679.650025] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  690.523917] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  690.720019] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  690.920019] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  691.120017] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  702.004390] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  702.201274] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  702.400017] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  702.601274] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  738.743918] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  738.940023] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  739.140028] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  739.340016] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  750.204153] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  750.400019] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  750.600018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  750.800018] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  761.664378] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  761.860021] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  762.060036] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  762.260026] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  773.132981] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  773.330018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  773.530024] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  773.730027] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  813.355297] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  813.550086] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  813.750036] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  813.950033] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  824.823915] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  825.020027] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  825.220022] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  825.420016] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  836.293899] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  836.491268] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  836.690017] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  836.890016] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  848.221766] usb 1-7: USB disconnect, address 4
[  866.770022] usb 1-8: new high speed USB device using ehci_hcd and address 5
[  866.969944] phy1: Selected rate control algorithm 'minstrel'
[  866.971158] Registered led device: rt2800usb-phy1::radio
[  866.971189] Registered led device: rt2800usb-phy1::assoc
[  866.971220] Registered led device: rt2800usb-phy1::quality
[  867.211744] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  882.602036] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[  882.603660] wlan0: authenticated
[  882.603687] wlan0: associate with 00:25:9c:9d:1e:2d (try 1)
[  882.619682] wlan0: RX AssocResp from 00:25:9c:9d:1e:2d (capab=0x31 status=0 aid=2)
[  882.619690] wlan0: associated
[  882.654777] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  893.341263] wlan0: no IPv6 routers present
[  897.400194] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22715 DF PROTO=TCP SPT=50575 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[  897.400436] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22716 DF PROTO=TCP SPT=50576 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[  897.400811] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22717 DF PROTO=TCP SPT=50577 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[  897.401060] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22718 DF PROTO=TCP SPT=50578 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  897.401434] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22719 DF PROTO=TCP SPT=50579 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[  897.401810] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22720 DF PROTO=TCP SPT=50580 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[  903.049436] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22749 DF PROTO=TCP SPT=50577 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[  903.049804] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22750 DF PROTO=TCP SPT=50575 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[  903.050059] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22751 DF PROTO=TCP SPT=50576 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[  903.050305] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=22752 DF PROTO=TCP SPT=50578 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[  926.751278] No probe response from AP 00:25:9c:9d:1e:2d after 500ms, disconnecting.
[  926.921326] cfg80211: All devices are disconnected, going to restore regulatory settings
[  926.921335] cfg80211: Restoring regulatory settings
[  926.921341] cfg80211: Calling CRDA to update world regulatory domain
[  926.927151] cfg80211: World regulatory domain updated:
[  926.927157]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  926.927163]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  926.927167]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  926.927171]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  926.927175]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  926.927179]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  928.503967] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[  928.700018] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 2)
[  928.900031] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 3)
[  929.100017] wlan0: authentication with 00:25:9c:9d:1e:2d timed out
[  940.044939] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  940.240022] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  940.440027] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  940.640024] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  943.463619] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  943.660018] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  943.861267] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  944.060018] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  955.233967] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[  955.431285] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[  955.630034] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[  955.830034] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[  971.831353] usb 1-8: USB disconnect, address 5
[ 1485.040051] usb 2-1: USB disconnect, address 2
[ 1487.970023] usb 3-2: new low speed USB device using uhci_hcd and address 2
[ 1488.170384] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input11
[ 1488.170525] generic-usb 0003:03F0:0024.0003: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.1-2/input0
[ 1519.710022] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 1519.909933] phy2: Selected rate control algorithm 'minstrel'
[ 1519.911182] Registered led device: rt2800usb-phy2::radio
[ 1519.911221] Registered led device: rt2800usb-phy2::assoc
[ 1519.911255] Registered led device: rt2800usb-phy2::quality
[ 1520.151731] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1523.132052] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[ 1523.133672] wlan0: authenticated
[ 1523.134412] wlan0: associate with 00:25:9c:9d:1e:2d (try 1)
[ 1523.150173] wlan0: RX AssocResp from 00:25:9c:9d:1e:2d (capab=0x31 status=0 aid=2)
[ 1523.150178] wlan0: associated
[ 1523.183552] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1533.651263] wlan0: no IPv6 routers present
[ 1536.070058] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=26496 DF PROTO=TCP SPT=50636 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1536.070408] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=26497 DF PROTO=TCP SPT=50632 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1536.070777] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=26498 DF PROTO=TCP SPT=50633 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1536.071408] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=26499 DF PROTO=TCP SPT=50634 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1536.072030] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=26500 DF PROTO=TCP SPT=50635 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1536.072905] [UFW BLOCK] IN=wlan0 OUT= MAC=00:21:91:7e:fa:4c:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.103 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=26502 DF PROTO=TCP SPT=50637 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1645.711290] No probe response from AP 00:25:9c:9d:1e:2d after 500ms, disconnecting.
[ 1645.821352] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1645.821362] cfg80211: Restoring regulatory settings
[ 1645.821367] cfg80211: Calling CRDA to update world regulatory domain
[ 1645.826695] cfg80211: World regulatory domain updated:
[ 1645.826701]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1645.826706]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1645.826711]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1645.826715]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1645.826719]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1645.826723]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1647.383950] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 1)
[ 1647.580033] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 2)
[ 1647.780042] wlan0: authenticate with 00:25:9c:9d:1e:2d (try 3)
[ 1647.980039] wlan0: authentication with 00:25:9c:9d:1e:2d timed out
[ 1658.837646] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1659.031318] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1659.230039] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1659.430039] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1662.472877] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1662.671286] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1662.871275] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1663.071281] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1673.957102] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1674.150042] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1674.351276] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1674.550112] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1685.446989] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1685.640079] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1685.841287] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1686.040057] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1696.933924] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1697.131278] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1697.331275] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1697.531270] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1708.458040] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1708.651301] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1708.853991] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1709.051290] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1719.924967] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 1)
[ 1720.120028] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 2)
[ 1720.321287] wlan0: direct probe to 00:25:9c:9d:1e:2d (try 3)
[ 1720.521285] wlan0: direct probe to 00:25:9c:9d:1e:2d timed out
[ 1733.257763] usb 1-3: USB disconnect, address 7
[ 2953.222551] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 2953.222558] e1000e 0000:03:00.0: eth0: 10/100 speed: disabling TSO
[ 2953.222922] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2960.241447] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1862 DF PROTO=TCP SPT=50706 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2960.242401] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1863 DF PROTO=TCP SPT=50707 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2960.242443] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1864 DF PROTO=TCP SPT=50708 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2960.242485] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1865 DF PROTO=TCP SPT=50709 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2960.242525] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1866 DF PROTO=TCP SPT=50710 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2960.242564] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1867 DF PROTO=TCP SPT=50711 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2963.242192] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1885 DF PROTO=TCP SPT=50708 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2963.243167] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1886 DF PROTO=TCP SPT=50710 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2963.243209] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1887 DF PROTO=TCP SPT=50709 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2963.243251] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=1888 DF PROTO=TCP SPT=50711 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2963.680009] eth0: no IPv6 routers present
[ 3609.034979] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5489 DF PROTO=TCP SPT=50747 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3609.036948] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=52 TOS=0x00 PREC=0x00 TTL=128 ID=5490 DF PROTO=TCP SPT=50748 DPT=9100 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3609.036989] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5491 DF PROTO=TCP SPT=50749 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3609.037029] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5492 DF PROTO=TCP SPT=50750 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3609.037070] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5493 DF PROTO=TCP SPT=50751 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3609.037110] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5494 DF PROTO=TCP SPT=50752 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3612.040240] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5519 DF PROTO=TCP SPT=50751 DPT=443 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3612.040289] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5520 DF PROTO=TCP SPT=50747 DPT=515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3612.041231] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5522 DF PROTO=TCP SPT=50749 DPT=2191 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3612.041275] [UFW BLOCK] IN=eth0 OUT= MAC=00:19:d1:67:08:77:90:4c:e5:6f:7a:6f:08:00 SRC=192.168.1.100 DST=192.168.1.104 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=5523 DF PROTO=TCP SPT=50752 DPT=81 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 3868.370141] e1000e: eth0 NIC Link is Down
[ 3879.410080] usb 1-7: new high speed USB device using ehci_hcd and address 8
[ 3879.609619] phy3: Selected rate control algorithm 'minstrel'
[ 3879.610904] Registered led device: rt2800usb-phy3::radio
[ 3879.610936] Registered led device: rt2800usb-phy3::assoc
[ 3879.610966] Registered led device: rt2800usb-phy3::quality
[ 3879.883156] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```[B]6 ) Network configuration
[/B]```
sudo lshw -C network
[sudo] password for kevin: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:19:d1:67:08:77
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.5-7 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:92100000-9211ffff ioport:1000(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 00:21:91:7e:fa:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```[B]7 ) Scan for networks:
[/B]```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:06:5A:00:98:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=51 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005370f6e181
                    Extra: Last beacon: 6810ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: D7185A0407104531433736325330313231000000000008020300
          Cell 02 - Address: 00:06:5A:40:98:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=52 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005370f91181
                    Extra: Last beacon: 6670ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    IE: Unknown: D7185A0407104531433736325330313231000000000008020300
          Cell 03 - Address: 00:06:5A:81:22:AD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=57 dBm  
                    Encryption key:off
                    ESSID:"RMUeznet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000052f23e0732
                    Extra: Last beacon: 6640ms ago
                    IE: Unknown: 0008524D55657A6E6574
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 04 - Address: 00:25:9C:9D:1E:2D
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=18 dBm  
                    Encryption key:on
                    ESSID:"zwireforus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003644ca205
                    Extra: Last beacon: 5960ms ago
                    IE: Unknown: 000A7A77697265666F727573
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16090F0A00000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259C9D1E2D102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304A3948313337311054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 05 - Address: 00:06:5A:41:22:AD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=55 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000052f23c8da3
                    Extra: Last beacon: 6740ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050600010E000402
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: D7185A0407104531433736415830353230000000000008020300
          Cell 06 - Address: 00:06:5A:01:22:AD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=56 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000052f23bc181
                    Extra: Last beacon: 6790ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050600010E000402
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: D7185A0407104531433736415830353230000000000008020300
          Cell 07 - Address: 00:06:5A:80:98:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=53 dBm  
                    Encryption key:off
                    ESSID:"RMUeznet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005370fa6b54
                    Extra: Last beacon: 6580ms ago
                    IE: Unknown: 0008524D55657A6E6574
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 0708555320010B1B0000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C

```**8 ) Mint Version: **
```
lsb_release -d
Description:    Linux Mint 10 Julia

```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
 uname -mr
2.6.35-22-generic x86_64

```[B]10 ) Restarting the network:
[/B]```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```Thanks for any help!

EDIT: An update, I installed it on my windows 7 laptop and it's working better than my built in wireless!

---

### Post by kbz1960 on 2011-02-05
Wow so I'm just screwed and bought a card that doesn't work????

---

### Post by bkratz on 2011-02-05
> **kbz1960 said:**
> Wow so I'm just screwed and bought a card that doesn't work????

You might find what you want in this thread

[http://ubuntuforums.org/showthread.php?t=1638334](http://ubuntuforums.org/showthread.php?t=1638334)

---

### Post by TBABill on 2011-02-05
> **bkratz said:**
> You might find what you want in this thread

[http://ubuntuforums.org/showthread.php?t=1638334](http://ubuntuforums.org/showthread.php?t=1638334)

Yes, so you need to do all those steps. As you see from your lsmod there are several RT28xx codes listed. All those need to be blacklisted because they are not for your card. Blacklisting makes them basically ignored. So...

```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add this to the end of the file > blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
Once that is done you need to edit your modules (drivers the system initiates on startup by doing ```
sudo gedit /etc/modules
``` and add the following to the end of that file ```
rt2870sta
``` No need to remove the others that we blacklisted. I think a restart will take care of that. Reboot and see if it works for you.

---

### Post by kbz1960 on 2011-02-05
OK so before I saw anyone replied I followed this [http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)
And I did get errors in the "make" part and the :make install". But I went ahead and followed the rest and my wireless is working now but only 54mbs. I'm posting from the computer.

So I didn't have to go thru all of that? Should I start all over, cause it's an install I'm just playing with, or is there no way to get N speeds?

Thanks

---

### Post by TBABill on 2011-02-05
Honestly, no idea. I scrolled through all that and it is quite lengthy and installs the driver from source. Ubuntu already has the driver available for use precompiled so they may be different.

---

### Post by kbz1960 on 2011-02-05
So if I reinstall and follow the link above do I just follow that link or do I follow the link in the link?

---

### Post by kbz1960 on 2011-02-05
Oh and if I reinstall do I need to have the dlink usb in or leave it out?

---

### Post by TBABill on 2011-02-05
I think it would not matter plugged in or not. If you plug it in you will need to follow the steps I listed. If you do it without it plugged in I am not sure how the system behaves to detect it and add the info to modules and blacklist. I have never tried it that way.

---

### Post by kbz1960 on 2011-02-05
I think part of the problem is that it is rev.B1 and any idea if my using a 64bit OS has anything to do with it?

---

### Post by TBABill on 2011-02-05
No 64 bit won't matter. I only use 64 bit and my RT2860 Realtek and my Broadcom BCM4312 don't have issues.

---

### Post by kbz1960 on 2011-02-05
OK since I was reinstalling I changed to Mint KDE 32bit. So far all I did was the blacklist and added the rt2870sta line and I'm back to where I  was connected but at 54mbits. So at least I have wireless again but still would like to figure out how to get the better speed.

---

### Post by kbz1960 on 2011-02-07
Just an update I installed Ubuntu 10.04 LTS, updated and did video drivers. All before I ever put the stick in. With the stick still out I followed post #4, I rebooted. Stick still out I followed [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
and made the changes for my dlink dwa-140 rev b1. I rebooted again and then put the stick in and the 54mb/s speed as before.

Then I followed this [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
with the stick out and rebooted when I was done. Put the stick in and now I'm getting 135mb/s.

If someone could point me in the right direction of how to mark this solved I will do it.

---

