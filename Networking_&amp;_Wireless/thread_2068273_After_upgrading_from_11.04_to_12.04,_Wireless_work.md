---
title: "After upgrading from 11.04 to 12.04, Wireless works intermidantly..."
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by TMundo on 2012-10-08
Have tried many times in the forum to get help with this issue to no  avail...  After prodding a bit, it seems to be a somewhat common issue  with internet working intermittantly and then needing to be reset.  This  is followed by the network card thinking that there are other networks  in the area with names similar to mine but with odd spelling variations  that include asian characters, etc.  Here is the description of the  issue. Below it are the code entries and responses for the general info:

     Started with 10.04.  Had a Linksys E1000 wireless router.  Was told I needed to buy a **Penguin Wireless N USB Adapter** (actually an Atheros card.)    off of the ThinkPenguin website.  I did, but I couldn't get things    working until 11.04 came out.  After that all issues were solved and    things worked great.  When 12.04 came out, I thought about upgrading    and the problems it could create, but finally figured it wouldn't be the    Ubuntu Team's plan to move backward, so I upgraded.  Things worked  fine   for a little while and then web pages stopped loading.

      If I reset my internet connection in the Ubuntu menu in the upper right    hand corner (I log off, then log back on)  things work fine again for a    good 10-15 minutes.

      It would seem that this problem occurs faster on sites that are    trafficing more info, for example, it takes a youtube video about 5    minutes to stop loading, or I simply open another youtube video at the    same time and the browser cannot connect to it until I reset the    connection.  A regular site containing only reading information with    limited animation doesn't give me trouble as fast.  As I am typing this I    have 2 other sites open containing only readable info, and yet I am    having no issues navigating the forum, but eventually I will have to    reset the internet connection.

      The people at ThinkPenguin seem to think the wireless card is    malfunctioning, and that it isn't a result of the new upgrade to 12.04.     They also said that the card I bought from them gets more complaints    with my modem than its cheaper sister version, the **Penguin Wireless G USB Adapter****.**    I bought the Wireless N Adapter(atheros) because they initially told me it was    faster than the Wireless G Adapter and was only $10.00 more.  Now I'm    being told to buy the cheaper one too.  That's a bit annoying, so I    figured I'd check the forum before shelling out more cash.  It isn't a    lot of money, but I'd still like to know a little more before I buy    another Wireless card.

Updating the package files? It doesn't  finish doing so, althoug it seemed to help a litlle, in fact, restarting  the system usually helps a little but eventually the internet stops and  I have to turn the wrieless off and on again.

please explain how to fix this if you can...

Here are the terminal code entries (highlighted) and their responses (not highlighted):

**lspci**

 ```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44 [Quadro NVS 285] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
05:04.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE/SATA Controller (rev 50) 
```

**lsusb**

 ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170] 
```

**ifconfig**

 ```
 eth0      Link encap:Ethernet  HWaddr 00:1a:a0:31:e2:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4461790 (4.4 MB)  TX bytes:4461790 (4.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:2d:bf:f2:bb  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:2dff:febf:f2bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2451803 (2.4 MB)  TX bytes:306067 (306.0 KB) 
```

**iwconfig**

 ```
 lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TMundo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:90:59:C0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1013  Invalid misc:59   Missed beacon:0

eth0      no wireless extensions. 
```

**lsmod**

 ```
Module                  Size  Used by
arc4                   12473  2 
carl9170               77667  0 
mac80211              436455  1 carl9170
ath                    19387  1 carl9170
cfg80211              178679  3 carl9170,mac80211,ath
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158438  10 bnep,rfcomm
snd_usb_audio         101566  1 
snd_usbmidi_lib        24603  1 snd_usb_audio
ppdev                  12849  0 
binfmt_misc            17292  1 
dcdbas                 14098  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
nouveau               708198  2 
psmouse                87213  0 
serio_raw              13027  0 
usbhid                 41906  0 
gspca_zc3xx            51066  0 
gspca_main             27654  1 gspca_zc3xx
snd_seq_midi           13132  0 
hid                    77367  1 usbhid
videodev               86588  1 gspca_main
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
parport_pc             32114  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ttm                    65344  1 nouveau
snd_timer              28931  2 snd_pcm,snd_seq
drm_kms_helper         45466  1 nouveau
mac_hid                13077  0 
drm                   197692  4 nouveau,ttm,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i82975x_edac           12911  0 
i2c_algo_bit           13199  1 nouveau
snd                     62064  19  snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
edac_core              46858  1 i82975x_edac
video                  19068  1 nouveau
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
sata_via               13495  0 
tg3                   137273  0 
```

**dmesg**

 ```
[    2.008827] hub 2-0:1.0: 2 ports detected
[    2.008932] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.008942] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.008946] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.009037] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.009076] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    2.009283] hub 3-0:1.0: USB hub found
[    2.009289] hub 3-0:1.0: 2 ports detected
[    2.009394] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.009405] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.009409] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.009487] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.009530] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.009747] hub 4-0:1.0: USB hub found
[    2.009754] hub 4-0:1.0: 2 ports detected
[    2.009857] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.009867] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.009872] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.009949] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.009988] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    2.010203] hub 5-0:1.0: USB hub found
[    2.010210] hub 5-0:1.0: 2 ports detected
[    2.010391] usbcore: registered new interface driver libusual
[    2.010464] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.013288] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.013299] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.013528] mousedev: PS/2 mouse device common for all mice
[    2.013794] rtc_cmos 00:05: RTC can wake from S4
[    2.013942] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.013972] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.014079] device-mapper: uevent: version 1.0.3
[    2.014208] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.014266] EISA: Probing bus 0 at eisa.0
[    2.014273] Cannot allocate resource for EISA slot 1
[    2.014276] Cannot allocate resource for EISA slot 2
[    2.014278] Cannot allocate resource for EISA slot 3
[    2.014297] EISA: Detected 0 cards.
[    2.014309] cpufreq-nforce2: No nForce2 chipset.
[    2.014312] cpuidle: using governor ladder
[    2.014315] cpuidle: using governor menu
[    2.014318] EFI Variables Facility v0.08 2004-May-17
[    2.014743] TCP cubic registered
[    2.014935] NET: Registered protocol family 10
[    2.015988] NET: Registered protocol family 17
[    2.016036] Registering the dns_resolver key type
[    2.016061] Using IPI No-Shortcut mode
[    2.016263] PM: Hibernation image not present or could not be loaded.
[    2.016281] registered taskstats version 1
[    2.025480]   Magic number: 0:228:432
[    2.025531] pci 0000:04:00.0: hash matches
[    2.025580] rtc_cmos 00:05: setting system clock to 2012-10-06 13:24:18 UTC (1349529858)
[    2.025610] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.025613] EDD information not available.
[    2.152608] ata5.00: ATAPI: PHILIPS DVD+/-RW DVD8801, AD21, max UDMA/33
[    2.168478] ata5.00: configured for UDMA/33
[    2.304045] ata2: SATA link down (SStatus 0 SControl 300)
[    2.304077] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.304106] ata3: SATA link down (SStatus 0 SControl 300)
[    2.304132] ata4: SATA link down (SStatus 0 SControl 300)
[    2.305115] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OAB3A, max UDMA/133
[    2.305121] ata1.00: 156250000 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    2.306303] ata1.00: configured for UDMA/133
[    2.306517] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    2.306738] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.306821] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.306858] sd 0:0:0:0: [sda] Write Protect is off
[    2.306867] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.306921] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.309321] scsi 4:0:0:0: CD-ROM            PHILIPS  DVD+-RW DVD8801  AD21 PQ: 0 ANSI: 5
[    2.313249] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.313255] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.313454] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.313638] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.350058]  sda: sda1 sda2 < sda5 >
[    2.350686] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.350723] Freeing unused kernel memory: 712k freed
[    2.351128] Write protecting the kernel text: 5628k
[    2.351200] Write protecting the kernel read-only data: 2324k
[    2.374281] udevd[95]: starting version 175
[    2.472049] Refined TSC clocksource calibration: 2992.502 MHz.
[    2.472062] Switching to clocksource tsc
[    2.495637] tg3.c:v3.121 (November 2, 2011)
[    2.495661] tg3 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.495677] tg3 0000:04:00.0: setting latency timer to 64
[    2.510710] sata_via 0000:05:04.0: version 2.6
[    2.510734] sata_via 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.510790] sata_via 0000:05:04.0: routed to hard irq line 11
[    2.511794] scsi6 : sata_via
[    2.512071] scsi7 : sata_via
[    2.512229] scsi8 : sata_via
[    2.512349] ata7: SATA max UDMA/133 port i16@0xd8a0 bmdma 0xd8e0 irq 16
[    2.512357] ata8: SATA max UDMA/133 port i16@0xd8b0 bmdma 0xd8e8 irq 16
[    2.512364] ata9: PATA max UDMA/133 port i16@0xd8c0 bmdma 0xd8f0 irq 16
[    2.535096] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM95754) rev b002] (PCI Express) MAC address 00:1a:a0:31:e2:ef
[    2.535107] tg3 0000:04:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.535116] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.535123] tg3 0000:04:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.672047] usb 2-2: new low-speed USB device number 2 using uhci_hcd
[    2.716839] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.843020] ata7: SATA link down (SStatus 0 SControl 310)
[    3.084021] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    3.170992] ata8: SATA link down (SStatus 0 SControl 310)
[    3.356631] ata9.01: ATA-5: ST340016A, 3.75, max UDMA/100
[    3.356638] ata9.01: 78165360 sectors, multi 0: LBA 
[    3.364534] ata9.01: configured for UDMA/100
[    3.364729] scsi 8:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[    3.365057] sd 8:0:1:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    3.365089] sd 8:0:1:0: Attached scsi generic sg2 type 0
[    3.365192] sd 8:0:1:0: [sdb] Write Protect is off
[    3.365199] sd 8:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.365262] sd 8:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.379872]  sdb: sdb1
[    3.380368] sd 8:0:1:0: [sdb] Attached SCSI disk
[    3.512033] usb 4-2: new low-speed USB device number 2 using uhci_hcd
[   16.563425] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.002933] udevd[306]: starting version 175
[   17.031535] Adding 520188k swap on /dev/sda5.  Priority:-1 extents:1 across:520188k 
[   17.071382] lp: driver loaded but no devices found
[   17.164324] wmi: Mapper loaded
[   17.167505] EDAC MC: Ver: 2.1.0
[   17.184331] EDAC i82975x: ECC disabled on both channels.
[   17.253789] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.284733] [drm] Initialized drm 1.1.0 20060810
[    17.387046] type=1400 audit(1349529873.858:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=461  comm="apparmor_parser"
[   17.388065] type=1400  audit(1349529873.862:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=461  comm="apparmor_parser"
[   17.388619] type=1400  audit(1349529873.862:4): apparmor="STATUS" operation="profile_load"  name="/usr/lib/connman/scripts/dhclient-script" pid=461  comm="apparmor_parser"
[   17.412130] parport_pc 00:06: reported by Plug and Play ACPI
[   17.412196] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.413525] intel_rng: Firmware space is locked read-only. If you can't or
[   17.413529] intel_rng: don't want to disable this in firmware setup, and if
[   17.413531] intel_rng: you are certain that your system has a functional
[   17.413533] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.442132] Linux video capture interface: v2.00
[   17.442954] gspca_main: v2.14.0 registered
[   17.443737] gspca_main: zc3xx-2.14.0 probing 046d:08d7
[   17.445930] leds_ss4200: no LED devices found
[   17.468167] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    17.468736] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID  v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[   17.487204] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
[    17.487512] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID  v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2/input0
[   17.487598] usbcore: registered new interface driver usbhid
[   17.487603] usbhid: USB HID core driver
[   17.500258] lp0: using parport0 (interrupt-driven).
[   17.525530] VGA switcheroo: detected Optimus DSM method \ handle
[   17.525586] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.525599] nouveau 0000:01:00.0: setting latency timer to 64
[   17.539160] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x044500a2)
[   17.551450] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   17.566000] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.566008] hda_intel: position_fix set to 1 for device 1028:01de
[   17.566143] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.566205] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   17.637799] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   17.637810] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   17.637817] [drm] nouveau 0000:01:00.0: Bios version 05.44.02.63
[   17.637825] [drm] nouveau 0000:01:00.0: TMDS table version 1.1
[   17.637830] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   17.637838] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00000028
[   17.637845] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00000000
[   17.637851] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 02011310 00000028
[   17.637857] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 04011312 00000000
[   17.637864] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 7 2
[   17.637870] [drm] nouveau 0000:01:00.0:   0: 0x00001038: type 0x38 idx 0 tag 0x07
[   17.637875] [drm] nouveau 0000:01:00.0: unknown type, using 0x30
[   17.637881] [drm] nouveau 0000:01:00.0:   1: 0x00002039: type 0x39 idx 1 tag 0x08
[   17.637886] [drm] nouveau 0000:01:00.0: unknown type, using 0xff
[   17.637892] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   17.637900] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   17.637906] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   17.637918] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xB1C9
[   17.638390] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xB52E
[   17.651545] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xBA68
[   17.651574] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xBBBD
[   17.652709] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xBD67
[   17.652720] [drm] nouveau 0000:01:00.0: mem timing table length unknown: 14
[   17.718646] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   17.719016] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   17.719362] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   17.719728] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.770813] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.851396] [drm] nouveau 0000:01:00.0: 1 available performance level(s)
[   17.851410] [drm] nouveau 0000:01:00.0: 0: core 275MHz shader 275MHz memory 600MHz fanspeed 100%
[   17.851423] [drm] nouveau 0000:01:00.0: c: core 200MHz memory 401MHz
[   17.858122] [TTM] Zone  kernel: Available graphics memory: 252766 kiB.
[   17.858128] [TTM] Initializing pool allocator.
[   17.858154] [drm] nouveau 0000:01:00.0: Detected 128MiB VRAM
[   17.871991] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   17.879982] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.879990] [drm] No driver support for vblank timestamp query.
[   17.880054] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   17.880062] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   17.880072] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[   17.880079] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[   18.010061] init: failsafe main process (618) killed by TERM signal
[   18.231030] ppdev: user-space parallel port driver
[   18.248777] [drm] nouveau 0000:01:00.0: allocated 1360x768 fb: 0x49000, bo da79e400
[   18.248991] fbcon: nouveaufb (fb0) is primary device
[   18.250048] Console: switching to colour frame buffer device 170x48
[   18.250107] fb0: nouveaufb frame buffer device
[   18.250112] drm: registered panic notifier
[   18.250127] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[    18.314562] type=1400 audit(1349529874.786:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=733  comm="apparmor_parser"
[   18.322834] type=1400  audit(1349529874.794:6): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=733  comm="apparmor_parser"
[   18.323380] type=1400  audit(1349529874.794:7): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=733  comm="apparmor_parser"
[   18.464625] type=1400  audit(1349529874.938:8): apparmor="STATUS" operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=732  comm="apparmor_parser"
[   18.608499] type=1400  audit(1349529875.082:9): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince" pid=735 comm="apparmor_parser"
[   18.615576]  type=1400 audit(1349529875.086:10): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince//launchpad_integration"  pid=735 comm="apparmor_parser"
[   18.617262] type=1400  audit(1349529875.090:11): apparmor="STATUS" operation="profile_load"  name="/usr/bin/evince//sanitized_helper" pid=735 comm="apparmor_parser"
[   18.649239] input: zc3xx as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/input/input8
[   18.649797] usbcore: registered new interface driver zc3xx
[   18.744839] usbcore: registered new interface driver snd-usb-audio
[   18.832036] Bluetooth: Core ver 2.16
[   18.832709] NET: Registered protocol family 31
[   18.832716] Bluetooth: HCI device and connection manager initialized
[   18.832722] Bluetooth: HCI socket layer initialized
[   18.832727] Bluetooth: L2CAP socket layer initialized
[   18.833841] Bluetooth: SCO socket layer initialized
[   18.859436] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.859444] Bluetooth: BNEP filters: protocol multicast
[   18.871066] Bluetooth: RFCOMM TTY layer initialized
[   18.871080] Bluetooth: RFCOMM socket layer initialized
[   18.871086] Bluetooth: RFCOMM ver 1.11
[   18.975340] tg3 0000:04:00.0: irq 46 for MSI/MSI-X
[   19.024173] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.024929] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.275868] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
[   21.275879] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[   21.509252] init: plymouth-stop pre-start process (1084) terminated with status 1
[201750.272039] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[201751.987533] cfg80211: Calling CRDA to update world regulatory domain
[201752.620036] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[201752.788632] usbcore: registered new interface driver carl9170
[201752.821503] cfg80211: World regulatory domain updated:
[201752.821509] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[201752.821513] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201752.821517] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[201752.821521] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[201752.821525] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201752.821529] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201752.859128] usb 1-8: driver   API: 1.9.4 2011-08-15 [1-1]
[201752.859138] usb 1-8: firmware API: 1.9.4 2011-06-30
[201752.859144] usb 1-8: Unprotected firmware image.
[201753.213300] ath: EEPROM regdomain: 0x809c
[201753.213305] ath: EEPROM indicates we should expect a country code
[201753.213309] ath: doing EEPROM country->regdmn map search
[201753.213313] ath: country maps to regdmn code: 0x52
[201753.213317] ath: Country alpha2 being used: CN
[201753.213320] ath: Regpair used: 0x52
[201753.213326] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[201753.213332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213337] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[201753.213342] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213346] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[201753.213351] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213355] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[201753.213360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213364] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[201753.213369] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213378] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[201753.213382] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213385] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[201753.213390] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213393] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[201753.213397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213400] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[201753.213404] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213408] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[201753.213412] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213415] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[201753.213419] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.213422] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[201753.213426] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[201753.213430] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[201753.213504] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[201753.213511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213517] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[201753.213523] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213529] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[201753.213535] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213541] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[201753.213548] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213553] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[201753.213559] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213565] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[201753.213571] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213576] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[201753.213583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213588] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[201753.213594] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213599] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[201753.213606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213611] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[201753.213617] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213622] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[201753.213629] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[201753.213634] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[201753.213641] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[201753.213647] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[201753.213653] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[201753.213659] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[201753.213665] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[201753.545603] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[201753.547541] cfg80211: Calling CRDA for country: CN
[201753.548638] Registered led device: carl9170-phy0::tx
[201753.548760] input: phy0 WPS Button as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/ieee80211/phy0/input9
[201753.550409] usb 1-8: Atheros AR9170 is registered as 'phy0'
[201753.558440] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[201753.558446] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558450] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[201753.558454] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558458] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[201753.558462] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558465] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[201753.558469] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558473] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[201753.558477] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558480] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[201753.558484] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558488] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[201753.558492] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558495] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[201753.558499] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558502] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[201753.558506] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558510] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[201753.558514] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558517] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[201753.558521] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558525] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[201753.558529] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558532] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[201753.558536] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[201753.558539] cfg80211: Disabling freq 2484 MHz
[201753.558545] cfg80211: Regulatory domain changed to country: CN
[201753.558548] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[201753.558552] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[201753.558555] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[201754.696600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[201754.697227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[201759.654045] wlan0: authenticate with 98:fc:11:90:59:c0 (try 1)
[201759.655678] wlan0: authenticated
[201759.775857] wlan0: associate with 98:fc:11:90:59:c0 (try 1)
[201759.780483] wlan0: RX AssocResp from 98:fc:11:90:59:c0 (capab=0x411 status=0 aid=1)
[201759.780492] wlan0: associated
[201759.885203] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[201771.680025] wlan0: no IPv6 routers present
[201771.880910] ieee80211 phy0: rx stream does not start with a first_mpdu frame tag.
[201772.687913] ieee80211 phy0: rx stream does not start with a first_mpdu frame tag.
[201772.688413] ieee80211 phy0: rx stream does not start with a first_mpdu frame tag. 
```[B]

sudo lshw -C network[/B]

 ```
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:31:e2:ef
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.121 firmware=5754-v3.13 latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:46 memory:ecef0000-ecefffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 00:22:2d:bf:f2:bb
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=carl9170  driverversion=3.2.0-24-generic firmware=1.9.4 ip=192.168.1.142 link=yes  multicast=yes wireless=IEEE 802.11bgn

```

**iwlist scan**

 ```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:90:59:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"TMundo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf9cb1a19a
                    Extra: Last beacon: 32172ms ago
                    IE: Unknown: 0006544D756E646F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                     IE: Unknown:  DD700050F204104A00011010440001021041000100103B000103104700108B16DAE3AD888310C63399C4B4965314102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning. 
```

**lsb_release -d**

 ```
 Description:    Ubuntu 12.04 LTS 
```

**uname -mr**

 ```
 3.2.0-24-generic i686 
```

---

### Post by TMundo on 2012-10-08
Also...

     Here is the output from

sudo /etc/init.d/networking restart

 ```
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 
```

---

### Post by Bucky Ball on 2012-10-08
@ TMundo: Please refrain from duplicate posting. It is against forum rules (see Code of Conduct). Your other thread in ***General Help*** has been deleted.

Thanks.
BB

---

### Post by varunendra on 2012-10-08
@ TMundo,
Please make it a habit to post the outputs of commands within [noparse]```
<put the output code here>
```[/noparse] tags. This not only preserves the formatting, but also prevents certain parts of code from turning into smileys, and puts the code in a nice box with scrollbars making the post neat and more readable.

To do so just click on **#** at the top of edit box to auto-generate those tags, then copy or cut-paste the output codes in-between the tags.
(Please do it now by editing your post, in advance mode, or by manually adding those tags in the beginning and end of outputs)


Onto the problem.
You already seem to have the correct driver for the chip (carl9170). However, as per [Linux Wireless]("http://wireless.kernel.org/en/users/Drivers/ar9170") website, you "may" need to manually get the correct firmware ([http://wireless.kernel.org/en/users/Drivers/ar9170#caveats](http://wireless.kernel.org/en/users/Drivers/ar9170#caveats)).

So please follow the above link to get the details, and go to the "[official device firmware]("http://wireless.kernel.org/en/users/Drivers/ar9170#official_device_firmware")" section (it is closed-source, but 'ready-to-use' official fw from atheros) to get the correct firmware for your adapter. Then copy (overwrite) them to you /lib/firmware/ directory (those already existing must be the open-source versions, and may be suffering from some bugs yet to be rectified).

Reboot, and hope for the best. Good luck!

---

### Post by TMundo on 2012-10-09
sorry

---

### Post by TMundo on 2012-10-09
thanx, I hope it works, and thanks for the forum tips.

---

### Post by TMundo on 2012-10-09
> **Bucky Ball said:**
> @ TMundo: Please refrain from duplicate posting. It is against forum rules (see Code of Conduct). Your other thread in ***General Help*** has been deleted.

sorry 'bout that

---

### Post by TMundo on 2012-10-09
[QUOTE=you "may" need to manually get the correct firmware ([http://wireless.kernel.org/en/users/Drivers/ar9170#caveats](http://wireless.kernel.org/en/users/Drivers/ar9170#caveats)).

So please follow the above link to get the details, and go to the "[official device firmware]("http://wireless.kernel.org/en/users/Drivers/ar9170#official_device_firmware")" section (it is closed-source, but 'ready-to-use' official fw from atheros) to get the correct firmware for your adapter. Then copy (overwrite) them to you /lib/firmware/ directory.[/QUOTE]

Okay, a few issues;

1. In the link you provided the:
**one stage**: *adds support for AVM FRITZ!WLAN USB Stick N and AVM FRITZ!WLAN USB Stick 2.4*:[I][ ar9170.fw]("http://www.kernel.org/pub/linux/kernel/people/mcgrof/firmware/ar9170/ar9170.fw")

was listed as: 404 Not Found 

Is there another site where it can be taken directly from atheros or somewhere else?

2. I got the files listed as: [/I]
**two stage**: *legacy firmware* 
* [ar9170-1.fw]("http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=blob_plain;f=ar9170-1.fw"), [ar9170-2.fw]("http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=blob_plain;f=ar9170-2.fw")*

I copied those over the original ones and (although they claimed to copy %95 for the first one and %100 for the 2nd) I got this message:

```
ar9170-1.fw: Error opening file '/lib/firmware/ar9170-1.fw': Permission denied
ar9170-2.fw: Error opening file '/lib/firmware/ar9170-2.fw': Permission denied
```

I can't undo the overwrite so I will restart and see what happens so far.

---

### Post by varunendra on 2012-10-10
TMundo,
A big sorry for being an utter stupid and sending you in the wrong direction.

I just realized that this driver (carl9170) doesn't use those firmware at all! It uses carl9170-1.fw, which again, already exists in the default packages. But before trying anything else, I think you should read [this page]("http://linuxwireless.org/en/users/Drivers/carl9170") thoroughly, especially if you are going to use n-channel, as the compatibility and performance of this particular chip is not very promising - to say the least. Some excerpts:
> Users should be aware that these devices might go mad from time to time. Because these BUGs seem to occur too randomly to be identified, but happen often enough to be really annoying, the firmware and driver come with some convenient features to keep the overall downtime at a minimum and without requiring any user intervention. But as mention before there is a caveat: The user has to setup everything properly!
..
..
It's worth mentioning that the chip was designed, produced and sold in the early 802.11n-draft period. Compatibility **will always be an issue**.
..
the device is **not suitable for any serious 802.11n setup**.


If you wish to try the firmware provided on that site (there's a minor size difference, so i assume it is different from the one already existing in /lib/firmware), please backup the current one:
```

sudo modprobe -rfv carl9170
cd /lib/firmware
sudo mv carl9170-1.fw carl9170-1.fw.bak
```
then download this one from the same page: [http://linuxwireless.org/en/users/Drivers/carl9170/fw1.9.6?action=AttachFile&do=get&target=carl9170-1.fw](http://linuxwireless.org/en/users/Drivers/carl9170/fw1.9.6?action=AttachFile&do=get&target=carl9170-1.fw)

Copy it to your /lib/firmware directory:
(assuming the downloaded file is in your 'Downloads' directory)-
```
cd Downloads
sudo cp carl9170-1.fw /lib/firmware
```
and reboot. Afterwards, as recommended on the same page, load the driver with nohwcrypt=1 parameter:
```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 nohwcrypt=1
```
Then try to connect. If it seems better this time, we'll make it permanent.

---

### Post by TMundo on 2012-10-10
[B]That's okay, because when I copied the two files into lib/firmware

two stage[/B]: *legacy firmware* 
* [ar9170-1.fw]("http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=blob_plain;f=ar9170-1.fw"), [ar9170-2.fw]("http://git.kernel.org/?p=linux/kernel/git/firmware/linux-firmware.git;a=blob_plain;f=ar9170-2.fw")*

I basically overwrote the existing ones of the same name, and even though it said there were errors, when I reset, everything seemed to work right.  We will see if it stops in the next few days, I was able to update about 512 update files which have been building up over time.  strangely 17 of them would not update, I have to investigate this issue further.  I don't know why overwriting two files you said were the wrong ones would cause it to work better unless it reset some kind of glitch.

Unless it's only because I reset the computer that it seems to be working, in which case it will eventually stop working I will keep an eye on it the next few days

Thinkpenguin later informed me that the Wireless N is difficult to work with, (shrugs) they didn't tell me that when I first bought it.

Let me see what happens over the next few days and I'll let you know if it stops working again.  If it stops I will try your other directions.

-Thanks for your help

-TMundo

---

### Post by varunendra on 2012-10-11
> **TMundo said:**
> [B]I don't know why overwriting two files you said were the wrong ones would cause it to work better unless it reset some kind of glitch.

Umm.. a bit confusing to me also but the result of:
```
modinfo carl9170
```clearly shows that it uses only carl9170-1.fw firmware.

Since that firmware also pre-exists in the /lib/firmware directory, I think it's just a matter of chance that it got connected.

I guess it's time to search for a command to figure out the firmware in use ;)

---

### Post by TMundo on 2012-10-17
looks like it finally went back to it's old behavior, it took some bit of time, but it eventually did.  I will try the next step you posted and let you know what happens.

---

### Post by varunendra on 2012-10-18
If you wish to try post #9, then in order to make the nohwcrypt=1 parameter permanent, do this:
```
echo "options carl9170 nohwcrypt=1" | sudo tee /etc/modprobe.d/carl9170.conf
```

If it doesn't seem to help, you can simply delete the /etc/modprobe.d/carl9170.conf file, or just comment out the line by adding a # in its beginning :
> # options carl9170 nohwcrypt=1

---

### Post by TMundo on 2012-10-19
Okay:

     I downloaded the carl9170 and installed it following your directions.  It is still giving some intermittant trouble but seems to work much longer.  It always seems to work long after I reset the computer, so I'm not sure if the firmware made it operate a bit longer or or not.  It's hard to tell how much time I'll get out of it before it malfunctions, but I gues the point is, it still malfunctions eventually.  As per your instructions, here is the output to the codes: (when it is working)

```
iwconfig iwlist scan
```

```
iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TMundo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:90:59:C0   
          Bit Rate=19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13812  Invalid misc:806   Missed beacon:0

eth0      no wireless extensions.

tmundo@tmundo-Precision-WorkStation-390:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:90:59:C0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"TMundo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001af41036183
                    Extra: Last beacon: 83752ms ago
                    IE: Unknown: 0006544D756E646F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B000103104700108B16DAE3AD888310C63399C4B4965314102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.
```I will wait until it stops working to post the rest of the code response you gave me.

Which is, (for anyone else who is reading this:)

```
dmesg | grep -e wlan -e carl9170
```

---

### Post by varunendra on 2012-10-20
Hmm.. here's my latest finding : [http://ubuntuforums.org/showpost.php?p=12305169](http://ubuntuforums.org/showpost.php?p=12305169)

Accordingly, I think you should try 12.10 using a live cd/usb and test it for stability of wifi (+ other things). If it really proves to be as stable as the post states, consider doing a fresh install of 12.10 on your system (to avoid carrying any misconfiguration from the current setup).

Apart from above, two other things come to mind which you can try beforehand.

1) Since you are not using high speeds anyway, try disabling the n-channel in your router.

2) Try disabling IPv6 by adding the following lines to your /etc/sysctl.conf file :
> # force-disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
To do it quickly, you can just copy-paste the following command in terminal:
```
echo -e "\n# force-disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Reboot and check the connection stability.

If neither these nor the new 12.10 solve the problem, then I guess it's time to honour the warning I quoted earlier in post#9, and get a better supported card :(

Fingers crossed, awaiting the result of this 'last' shot..[-o<
8-[

---

### Post by TMundo on 2012-10-23
hmmm, I haven't tried the latest instructions yet, because I was waiting for the connectivity to stop. so I could give you the results of

```
dmesg | grep -e wlan -e carl9170 
``` 

want to give you as much info as possible.

However, connectivity did not stop for the next three days.  I was waiting with the command pasted in the terminal so I could run it as soon as connectivity stopped, but after a day or so I must have closed it.  I'm sure I reset the computer at some point as well.  Anyway.  This time I will keep the code more handy.

As for the:

```
echo -e "\n# force-disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

I would like to give you the info from the other code first (when connectivity stops) unless of course one issue has nothing to do with the other.  Should this not work, is there any way to reverse it? (should it not connect at all.)

Also, now that the carl9170.fw is installed, even though it is not permanent, does that mean... well, what does 'not-permanent' mean exactly?  It doesn't go back to the original settings after a reset, does it?

---

### Post by TMundo on 2012-10-23
Okay, the plot thickens

When connectivity stopped, I entered:

```
dmesg | grep -e wlan -e carl9170 	
```

and the output was:

```
[   21.994656] usbcore: registered new interface driver [COLOR=#ff0000]carl9170 [/COLOR] 
 [   22.645723] Registered led device: [COLOR=#ff0000]carl9170[/COLOR]-phy0::tx  
 [   23.152869] ADDRCONF(NETDEV_UP): [COLOR=#ff0000]wlan[/COLOR]0: link is not ready  
 [   23.153580] ADDRCONF(NETDEV_UP): [COLOR=#ff0000]wlan[/COLOR]0: link is not ready  
 [   26.589535] [COLOR=#ff0000]wlan[/COLOR]0: authenticate with 98:fc:11:90:59:c0 (try 1)  
 [   26.591291] [COLOR=#ff0000]wlan[/COLOR]0: authenticated  
 [   26.718793] [COLOR=#ff0000]wlan[/COLOR]0: associate with 98:fc:11:90:59:c0 (try 1)  
 [   26.722946] [COLOR=#ff0000]wlan[/COLOR]0: RX AssocResp from 98:fc:11:90:59:c0 (capab=0x411 status=0 aid=1)  
 [   26.722954] [COLOR=#ff0000]wlan[/COLOR]0: associated  
 [   26.826977] ADDRCONF(NETDEV_CHANGE): [COLOR=#ff0000]wlan[/COLOR]0: link becomes ready  
 [   37.952025] [COLOR=#ff0000]wlan[/COLOR]0: no IPv6 routers present
```
Also, it must be noted, and this is very strange, after I had finished copying and pasting the code into Libre Office, and prepared to reboot the computer or unplug the card, I went and refreshed one of the pages that wouldn't load when connectivity halted, and voila, all of a sudden connectivity was working again.  I don't know if and when connectivity stops, whether it is only for a few minutes, or whether it is for much longer, because in the past, I never really went to do another task on the computer when connectivity would stop, I would simply pull the card out and then plug it back in.  Don't know if this gives us any more useful info.


-TMundo

---

### Post by Bucky Ball on 2012-10-23
Run the code to switch of IPv6. Set to 'Ignore' in Network Manager also.

---

### Post by varunendra on 2012-10-25
> **TMundo said:**
> Should this not work, is there any way to reverse it? (should it not connect at all.)Yes, we always can revert the changes we make. That said, IPv6 is still used very rarely, so it is okay (or sometimes even better) to leave it disabled (of-course unless it is the one that is being used for connection in your router - which is, as I said, still a very rare case).

> **TMundo said:**
> Also, now that the carl9170.fw is installed, even though it is not permanent, does that mean... well, what does 'not-permanent' mean exactly?  It doesn't go back to the original settings after a reset, does it?
'Temporary' is the parameter (nohwcrypt=1) that you are using with the carl9170 module, not the firmware file (carl9170.fw). It is just a file which is there now, and is permanent unless you (or an update) replace it with the backup or a new one. Also, even the parameter is permanent if you have put it in the '.conf' file as I wrote earlier. But making that parameter permanent is of no use (or may even be harmful) if it is not helping the stability.

> **TMundo said:**
> 
Also, it must be noted, and this is very strange, after I had finished copying and pasting the code into Libre Office, and prepared to reboot the computer or unplug the card, I went and refreshed one of the pages that wouldn't load when connectivity halted, and voila, all of a sudden connectivity was working again.
^That behaviour can be (not necessarily though) caused by unnecessary IPv6 requests while the actual connection is IPv4-only. Accordingly, please try what *Bucky Ball* suggested above (that is- disable IPv6 as I suggested, then also set it to 'Ignore' in NM).

---

### Post by TMundo on 2012-10-26
okay, executed that command, and switched the setting to ignore, will see what happens, thanks guys!

---

### Post by TMundo on 2012-11-16
Okay, nope, we are back to square one, still the same behavior, although I must admit, everything I tried that you all suggested seemed to make things run better and for longer, but that may just be the fact that I reset the computer each time.  Reseting the computer always makes the wireless run uninterrupted or longer periods.

-TMundo

---

### Post by varunendra on 2012-11-16
Hi,
I consulted a much more knowledgeable senior of mine and he immediately caught a very big mistake I made -
> **varunendra said:**
> ```
echo [COLOR=Red]**"nohwcrypt=1"**[/COLOR] | sudo tee  /etc/modprobe.d/carl9170.conf
```
It should have been [COLOR=Navy]**"options carl9170 nohwcrypt=1"**[/COLOR]. I feel really embarassed how I made that mistake *(not that I don't do it often, but that I got caught in clear daylight.. :D)*, and how I kept overlooking it for so long.

Please correct it immediately. You can do it in one step by (you may simply copy-paste in terminal) -
```
sudo sed -i 's/^nohwcr/options carl9170 &/' /etc/moprobe.d/carl9170.conf
```If doing this alone doesn't help, there is another advice based on dmesg indication in your very first post -
> [201772.688413] ieee80211 phy0: rx stream does not start with a first_mpdu frame tag.To take care of above, please try (only if the above correction doesn't help)-
```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170 noht=1
```If it seems to help, we can include it in permanent options.

And.. there is yet another advice to try 'G' channel in your router instead of 'N', plus make sure the encryption is set to **[COLOR=DarkRed]WPA2[/COLOR]** only, not WPA/WPA2 mix mode.

Let us hope for miracles this time, but to be honest, the only person I could find happy with this chip was the poster of [this post]("http://ubuntuforums.org/showpost.php?p=12305169") I linked to earlier. I hope you become the next one!

---

### Post by TMundo on 2012-11-19
**After entering code:**
```

sudo sed -i 's/^nohwcr/options carl9170 &/' /etc/moprobe.d/carl9170.conf
```
**Output is:**
```

sed: can't read /etc/moprobe.d/carl9170.conf: No such file or directory

```

Not sure why, but I assume that didn't work (shrugs)

**So I input the other codes:**
```


sudo modprobe -rfv carl9170
```
**Output**:
```
rmmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/net/wireless/cfg80211.ko

```
```

sudo modprobe -v carl9170 noht=1
```
**Output**:
```

insmod /lib/modules/3.2.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko noht=1

```

With  the second codes, after the first line it shut the wireless off and  after the second one it turned the wireless back on again.  We will see  what happens in the next few days.

Thanks again

-TMundo

---

### Post by varunendra on 2012-11-19
> **TMundo said:**
> ```

sed: can't read /etc/m[COLOR=Red]**op**[/COLOR]robe.d/carl9170.conf: [COLOR=Red]**No such file or directory**[/COLOR]

```[s]Which means either the file was not created at all, or it might have been mis-named. To confirm, please post -[/s]
```
ls  -l /etc/m**[COLOR=Red]op[/COLOR]**robe.d/
```[COLOR=Red][Edit : repeated typo. It should have been "mo[COLOR=DarkRed]**d**[/COLOR]probe", not moprobe][/COLOR]
If it is not there, we can create it now with the correct command this time (you may copy-paste commands to avoid errors) -
```
echo "options carl9170 nohwcrypt=1" | sudo tee  /etc/modprobe.d/carl9170.conf
```> **TMundo said:**
> ```

insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/[COLOR=DarkRed]**carl9170.ko noht=1**[/COLOR]
``` Had the .conf file been in effect, the above line would have looked like -
```
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/[COLOR=DarkRed]**carl9170.ko [COLOR=Red]nohwcrypt=1[/COLOR] noht=1**[/COLOR]
```Which is what I was expecting. As per the description on linuxwireless.org, the *nohwcrypt=1* option is more important. So please create the .conf file as suggested above, then retry the last two *modprobe* commands to see if it goes as expected. I doubt if the* noht=1* option alone can make it any better.

---

### Post by TMundo on 2012-11-23
Okay:

I confirmed that the file is not there

After: 

```
 echo "options carl9170 nohwcrypt=1" | sudo tee  /etc/modprobe.d/carl9170.conf
```

There is no output

I then ran:

```
sudo modprobe -rfv carl9170
```

and got output:

```
rmmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-24-generic/kernel/net/wireless/cfg80211.ko

```

Wireless signal shuts off:

Then I input:

```
sudo modprobe -v carl9170 noht=1
```

Output is:
```

insmod /lib/modules/3.2.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko nohwcrypt=1 noht=1
```

so it looks like the:  [COLOR=Red]nohwcrypt=1[/COLOR]  is in there, however after putting in the command:

```
ls  -l /etc/moprobe.d/
```

The file is still not found, I then realized there was a typo in the code, 

so I entered:


```
ls  -l /etc/modprobe.d/
```

not really sure if the .d is supposed to be there or if it is part of the typo, but the results were:


```
total 44
-rw-r--r-- 1 root root 2507 May  5  2011 alsa-base.conf
-rw-r--r-- 1 root root  325 Jun 15  2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Jun 15  2011 blacklist.conf
-rw-r--r-- 1 root root  210 Jun 15  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Jun 15  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 May  5  2011 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 May  5  2012 [COLOR=Cyan]blacklist-oss.conf[/COLOR] -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Jun 15  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Jun 15  2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root   29 Nov 23 19:29 carl9170.conf
-rw-r--r-- 1 root root  127 Apr 22  2012 dkms.conf
-rw-r--r-- 1 root root   30 May 18  2012 vmwgfx-fbdev.conf

```

and so, it looks like we are now getting somewhere, although I am not sure where.
it  is also necessary to note that even though the previous time I entered  the two modprobe codes the file was not even there, connectivity was  still running uninterrupted for a few days, I now beleive this is  regardless of reseting the computer.   Whenever we try to mess with it  in the manner we have been using, it seems to jolt the system in such a  way as to make the connectivity work uninterrupted for about 3 days.   Not sure if this info is pertinent, but it seemed worth mentioning.  As  usual, will see what happens in the next few days.

Thanx again

---

### Post by varunendra on 2012-11-24
Hmm.., looks like I'm on my way to create some kind of record of 'Making Typos' this month ! Funny and embarrassing at the same time. I wonder if yet another sorry is sufficient.

Anyway, now that it's fixed, I'd prefer to shamelessly move on.

Although this sounds a bit odd to me -
> **TMundo said:**
> ```
 echo "options carl9170 nohwcrypt=1" | sudo tee  /etc/modprobe.d/carl9170.conf
```[COLOR=Red]**There is no output**[/COLOR] Well, I just copy-pasted the above command to verify, and I did see an output - "[COLOR=DarkRed]**options carl9170 nohwcrypt=1**[/COLOR]".

So I think that string would have appeared on the terminal, you just didn't notice it. Although it doesn't really matter if the string is returned or not on the screen as long as it is written correctly in the target file, but just for your info, this is how '*tee*' command works. It both displays the supplied string on the terminal, AND drops it in the target file.

But anyway, we don't need to worry about it since the output of *modprobe -v* shows that everything has been done correctly this time -
> ```
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko [COLOR=DarkRed]**nohwcrypt=1 noht=1**[/COLOR]
```Oh, one more thing, not very important though -
>  not really sure if the .d is supposed to be there or if it is part of the typo, It IS supposed to be there. The 'modprobe.d' is a directory we had to put the .conf file in.


By the way, now that you seem to care about these things (and I'm getting worse on typos), may I give you a tip to avoid some mistakes while typing commands or addresses (and make it easier too!) -

While typing a command, just type a few initial characters, then press 'Tab' key. The rest of the command will be auto-completed. Same goes for typing addresses. For example, if you only type -
[COLOR=DarkRed]**/et**[/COLOR]
and press '[COLOR=DarkRed]**Tab**[/COLOR]', it will automatically be completed to -
[COLOR=DarkRed]**/etc/**[/COLOR] [COLOR=DarkSlateGray][I](because terminal knows there is one and only one object at location '/' that starts with 'et', and that it is a folder - "etc")
[/I][/COLOR]Now after /etc/, type only "mo" like this -
[COLOR=DarkRed]**/etc/mo**[/COLOR]
and press 'Tab' again, it will auto-complete to -
[COLOR=DarkRed]**/etc/modprobe.d/ **[/COLOR][COLOR=DarkSlateGray]*(because again, there is one and only one object in "etc" directory that starts with "mo" and it again is a folder)*[/COLOR]
Again, if immediately after that *(where the terminal's cursor is - waiting for more input)* you type "ca" and press 'Tab' I hope you've already guessed what will happen :) Of course, it'll become -
[COLOR=DarkRed]**/etc/modprobe.d/carl9170.conf**[/COLOR] [COLOR=DarkSlateGray]*(unless there are more than one objects that start with "ca")*[/COLOR]
But this time the terminal's cursor will also put a '**space**' after the completed address. Why?? Because it knows that *carl9170.conf* is a file, and so you can not go "into" it.
But it does expect that you may want to type another filename or a command option or a parameter 'After' the filename, which are things that are typed after a space.

But if, after /etc, you type "de" and press 'Tab' -
[COLOR=DarkRed]**/etc/de**[/COLOR]
Nothing will happen, although there is a directory named -"**default**". Why?? Because there is another directory in /etc/ that starts with "de", that is - "**depmod.d**". So you'll have to type more characters until it becomes a unique pattern to look for. In this example, typing just one more character "f" is sufficient -
[COLOR=DarkRed]**/etc/def**[/COLOR]
press 'Tab' and you'll have [COLOR=DarkRed]**/etc/default/**[/COLOR] auto-completed on your terminal.

If you don't know how many files/directories/commands exist that start with the pattern you have typed so far, just press 'Tab' twice. Unless they are in hundreds, terminal will immediately suggest you the available options by displaying them in a new line/paragraph, and will again return in a new line to wait for your further input. Like this -
:~$ **[COLOR=DarkRed]/etc/ap[/COLOR]**
**[COLOR=Navy]apache2/    apm/        apparmor/   apparmor.d/ apport/     apt/[/COLOR]**
:~$ [COLOR=DarkRed]**/etc/ap**[/COLOR]
where -
* the first line was when you [COLOR=DarkRed]pressed tab[/COLOR] (twice),
* the second line is [COLOR=Navy]available options[/COLOR] that the terminal suggested to you,
* the third line is where terminal immediately moved its [COLOR=DarkRed]input prompt[/COLOR] after suggesting the available options, waiting for you to type more characters.

However, if by mistake you type -
[COLOR=Red]**/etc/mop**[/COLOR]
and press 'Tab', guess what....... Nothing will happen, no matter you press 'Tab' two times or two-hundred times. Why ?? Because there is nothing at location /etc/ that starts with "**mop**" !! And so you immediately realize - [FONT=Comic Sans MS][COLOR=DarkRed]**"Eureka !! We have a T-Y-P-O..! :D"**
[/COLOR][/FONT]
Hope that compensates the yet another typo on my part
*[COLOR=DarkSlateGray](Phew....!! Mommy ! A [s]glass[/s] .. BIG Jug of water please..!!..)[/COLOR]*

If the connection gets finally stable this time, we can really consider it a great achievement - given how disheartening the driver/chip's description on [linuxwireless.org]("http://linuxwireless.org/en/users/Drivers/carl9170") was -
> Users should be aware that these devices might go mad from time to time.  Because these BUGs seem to occur too randomly to be identified, but  happen often enough to be really annoying, the firmware and driver come  with some convenient features to keep the overall downtime at a minimum  and without requiring any user intervention. But as mention before there  is a caveat: The user has to setup everything properly!Shall very curiously await your feedback, hoping for the best !

---

