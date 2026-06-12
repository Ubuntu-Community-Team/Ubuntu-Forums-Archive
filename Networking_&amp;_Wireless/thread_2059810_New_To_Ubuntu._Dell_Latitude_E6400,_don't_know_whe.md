---
title: "New To Ubuntu. Dell Latitude E6400, don't know where to start."
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by Dtruffles on 2012-09-18
Hello,

I was just given a Dell Latitude E6400 without an operating system, so I decided to install the newest Ubuntu onto it. I'm not used to any operating system other than windows, so any information I look up sounds like another language to me. If someone could please explain what I should do in order to have wireless on here, I would really appreciate it. It says "device not ready" firmware missing. So I don't know what to do. I'm posting everything that is asked for in the HOWTO post a wireless issue page.

Thanks,
Dtruffles


Dell Latitude E6400 Laptop


[B]2 ) Wireless Brand, Model and Wireless Chipset:

[/B]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63f8 Microdia Sonix Integrated Webcam
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card


[B]3 ) check interface:
[/B]
eth0      Link encap:Ethernet  HWaddr 00:21:70:de:44:82  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fede:4482/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14826886 (14.8 MB)  TX bytes:526852 (526.8 KB)
          Interrupt:22 Memory:f6ae0000-f6b00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12236 (12.2 KB)  TX bytes:12236 (12.2 KB)
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.**4 ) Check for modules:**Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  12 
joydev                 17393  0 
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
pcmcia                 39791  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
arc4                   12473  2 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
wmi                    18744  1 dell_wmi
b43                   342643  0 
mac_hid                13077  0 
mac80211              436455  1 b43
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414817  3 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
cfg80211              178679  2 b43,mac80211
psmouse                72919  0 
serio_raw              13027  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
bcma                   25651  1 b43
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
e1000e                140005  0 
ssb                    50691  1 b43
[B]5 ) Kernel boot messages

[/B][    0.952659] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.968297] Linux agpgart interface v0.103
[    0.968419] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[    0.968483] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.969566] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.969697] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    0.971285] brd: module loaded
[    0.972121] loop: module loaded
[    0.972294] ata_piix 0000:00:1f.2: version 2.13
[    0.972309] ata_piix 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.972317] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.972359] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.972605] scsi0 : ata_piix
[    0.972695] scsi1 : ata_piix
[    0.974032] ata1: SATA max UDMA/133 cmd 0x6e70 ctl 0x6e78 bmdma 0x6ea0 irq 19
[    0.974037] ata2: SATA max UDMA/133 cmd 0x6e80 ctl 0x6e88 bmdma 0x6ea8 irq 19
[    0.974059] ata_piix 0000:00:1f.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.974070] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.128033] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.128252] scsi2 : ata_piix
[    1.128330] scsi3 : ata_piix
[    1.129648] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 19
[    1.129653] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 19
[    1.130022] Fixed MDIO Bus: probed
[    1.130043] tun: Universal TUN/TAP device driver, 1.6
[    1.130045] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.130106] PPP generic driver version 2.4.2
[    1.130217] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.130236] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.130253] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.130256] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.130308] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.130333] ehci_hcd 0000:00:1a.7: debug port 1
[    1.134226] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.134241] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.148020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.148150] hub 1-0:1.0: USB hub found
[    1.148155] hub 1-0:1.0: 6 ports detected
[    1.148233] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.148245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.148248] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.148299] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.148322] ehci_hcd 0000:00:1d.7: debug port 1
[    1.152205] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.152221] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.168019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.168135] hub 2-0:1.0: USB hub found
[    1.168139] hub 2-0:1.0: 6 ports detected
[    1.168216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.168230] uhci_hcd: USB Universal Host Controller Interface driver
[    1.168245] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.168253] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.168257] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.168303] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.168330] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    1.168458] hub 3-0:1.0: USB hub found
[    1.168462] hub 3-0:1.0: 2 ports detected
[    1.168529] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.168537] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.168540] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.168586] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.168621] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    1.168744] hub 4-0:1.0: USB hub found
[    1.168748] hub 4-0:1.0: 2 ports detected
[    1.168815] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.168823] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.168826] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.168874] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.168900] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    1.169027] hub 5-0:1.0: USB hub found
[    1.169031] hub 5-0:1.0: 2 ports detected
[    1.169098] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.169107] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.169110] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.169154] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.169179] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    1.169305] hub 6-0:1.0: USB hub found
[    1.169309] hub 6-0:1.0: 2 ports detected
[    1.169375] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.169382] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.169386] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.169437] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.169462] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    1.169598] hub 7-0:1.0: USB hub found
[    1.169602] hub 7-0:1.0: 2 ports detected
[    1.169669] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.169677] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.169681] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.169725] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.169749] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.169873] hub 8-0:1.0: USB hub found
[    1.169877] hub 8-0:1.0: 2 ports detected
[    1.169997] usbcore: registered new interface driver libusual
[    1.170053] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.170643] i8042: Warning: Keylock active
[    1.173730] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.173736] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.173865] mousedev: PS/2 mouse device common for all mice
[    1.174056] rtc_cmos 00:03: RTC can wake from S4
[    1.174174] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.174203] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.174262] device-mapper: uevent: version 1.0.3
[    1.174337] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.174381] EISA: Probing bus 0 at eisa.0
[    1.174383] EISA: Cannot allocate resource for mainboard
[    1.174385] Cannot allocate resource for EISA slot 1
[    1.174387] Cannot allocate resource for EISA slot 2
[    1.174389] Cannot allocate resource for EISA slot 3
[    1.174391] Cannot allocate resource for EISA slot 4
[    1.174393] Cannot allocate resource for EISA slot 5
[    1.174394] Cannot allocate resource for EISA slot 6
[    1.174396] Cannot allocate resource for EISA slot 7
[    1.174398] Cannot allocate resource for EISA slot 8
[    1.174399] EISA: Detected 0 cards.
[    1.174408] cpufreq-nforce2: No nForce2 chipset.
[    1.174468] cpuidle: using governor ladder
[    1.174574] cpuidle: using governor menu
[    1.174577] EFI Variables Facility v0.08 2004-May-17
[    1.174843] TCP cubic registered
[    1.174960] NET: Registered protocol family 10
[    1.175521] NET: Registered protocol family 17
[    1.175525] Registering the dns_resolver key type
[    1.175542] Using IPI No-Shortcut mode
[    1.175718] PM: Hibernation image not present or could not be loaded.
[    1.175729] registered taskstats version 1
[    1.176062] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.185278]   Magic number: 12:84:353
[    1.185339]  rapidio: hash matches
[    1.185379] rtc_cmos 00:03: setting system clock to 2012-09-18 23:19:11 UTC (1348010351)
[    1.186870] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.186872] EDD information not available.
[    1.448254] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.448439] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.459287] ata4: SATA link down (SStatus 4 SControl 300)
[    1.459656] ata2.00: ATAPI: PLDS DVD+/-RW DU-8A2S, 4D12, max UDMA/100
[    1.470411] ata3: SATA link down (SStatus 4 SControl 300)
[    1.470470] ata1.00: ATA-8: ST980310AS, DE05, max UDMA/133
[    1.470473] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.476400] ata2.00: configured for UDMA/100
[    1.484747] ata1.00: configured for UDMA/133
[    1.484950] scsi 0:0:0:0: Direct-Access     ATA      ST980310AS       DE05 PQ: 0 ANSI: 5
[    1.485093] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.485108] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.485141] sd 0:0:0:0: [sda] Write Protect is off
[    1.485144] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.485170] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.488304] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DU-8A2S  4D12 PQ: 0 ANSI: 5
[    1.494390] sr0: scsi3-mmc drive: 24x/6x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    1.494394] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.494557] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.494680] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.692049] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.776957]  sda: sda1 sda2 < sda5 >
[    1.777639] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.777727] Freeing unused kernel memory: 740k freed
[    1.778019] Write protecting the kernel text: 5820k
[    1.778045] Write protecting the kernel read-only data: 2376k
[    1.778047] NX-protecting the kernel data: 4420k
[    1.793648] udevd[99]: starting version 175
[    1.873212] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.873230] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.878447] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.878450] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.878480] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.878492] e1000e 0000:00:19.0: setting latency timer to 64
[    1.878617] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    1.886681] sdhci: Secure Digital Host Controller Interface driver
[    1.886683] sdhci: Copyright(c) Pierre Ossman
[    1.886949] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 21)
[    1.886965] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.890928] mmc0: no vmmc regulator found
[    1.891954] Registered led device: mmc0::
[    1.893311] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.893328] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.893345] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.893362] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.894723] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[    1.898961] firewire_ohci 0000:03:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.960116] firewire_ohci: Added fw-ohci device 0000:03:01.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.968304] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    2.098684] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:21:70:de:44:82
[    2.098688] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.098716] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1004FF-0FF
[    2.115203] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.285882] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.296447] hub 3-1:1.0: USB hub found
[    2.298386] hub 3-1:1.0: 3 ports detected
[    2.460200] firewire_core: created device fw0: GUID 4a4fc0000ee569a1, S400
[    2.540042] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[    2.721119] usb 5-1: config 0 descriptor??
[    2.805391] usb 3-1.1: new full-speed USB device number 3 using uhci_hcd
[    3.001392] usb 3-1.2: new full-speed USB device number 4 using uhci_hcd
[   14.339165] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.371562] udevd[334]: starting version 175
[   14.509761] type=1400 audit(1348010364.822:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=366 comm="apparmor_parser"
[   14.510160] type=1400 audit(1348010364.822:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=366 comm="apparmor_parser"
[   14.510391] type=1400 audit(1348010364.822:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=366 comm="apparmor_parser"
[   14.536754] Adding 2046972k swap on /dev/sda5.  Priority:-1 extents:1 across:2046972k 
[   14.551612] lp: driver loaded but no devices found
[   14.552925] [drm] Initialized drm 1.1.0 20060810
[   14.562134] Linux video capture interface: v2.00
[   14.562691] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_0.3M (0c45:63f8)
[   14.586249] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input4
[   14.586828] generic-usb 0003:413C:8157.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0
[   14.593124] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input5
[   14.594500] generic-usb 0003:413C:8158.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
[   14.594546] usbcore: registered new interface driver usbhid
[   14.594549] usbhid: USB HID core driver
[   14.595322] input: Laptop_Integrated_Webcam_0.3M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
[   14.595439] usbcore: registered new interface driver uvcvideo
[   14.595442] USB Video Class driver (1.1.1)
[   14.616349] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.634273] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.634279] i915 0000:00:02.0: setting latency timer to 64
[   14.660295] cfg80211: Calling CRDA to update world regulatory domain
[   14.693436] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   14.693440] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   14.694532] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   14.694538] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.694539] [drm] Driver supports precise vblank timestamp query.
[   14.694578] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.773698] wmi: Mapper loaded
[   14.780163] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0233]
[   14.782106] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.241234] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.241237] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241240] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.241243] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241245] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.241248] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241250] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.241252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241254] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.241257] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241259] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.241262] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241264] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.241267] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241269] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.241271] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241274] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.241276] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241278] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.241281] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241283] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.241286] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.241288] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.241291] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.241293] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.241295] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.241297] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.241300] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   15.261323] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   15.261327] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   15.261331] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   15.261340] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   15.261343] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff
[   15.264113] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.264740] Registered led device: b43-phy0::tx
[   15.264760] Registered led device: b43-phy0::rx
[   15.264782] Registered led device: b43-phy0::radio
[   15.264796] Broadcom 43xx driver loaded [ Features: PNL ]
[   15.265739]  0x2400-0x24ff
[   15.270856] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xf6800000-0xf68fffff]
[   15.270861] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf6800000-0xf68fffff: excluding 0xf68f0000-0xf68fffff
[   15.270874] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   15.270877] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   15.275203] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   15.294610] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.294614] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294616] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.294619] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294621] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.294624] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294626] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.294628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294630] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.294633] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294635] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.294638] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294640] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.294642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294644] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.294647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294649] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.294652] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294654] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.294656] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294659] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.294661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294663] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.294666] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.294668] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.294671] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.294673] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.294676] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.294678] cfg80211: World regulatory domain updated:
[   15.294680] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.294683] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294685] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.294688] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.294690] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.294692] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.429401] fbcon: inteldrmfb (fb0) is primary device
[   15.429500] Console: switching to colour frame buffer device 160x50
[   15.429526] fb0: inteldrmfb frame buffer device
[   15.429527] drm: registered panic notifier
[   15.455452] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x2f8-0x2ff
[   15.457692] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.458574] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.459281] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xcbf
[   15.459882] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   15.459914] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   15.459941] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   15.459973] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.517397] usb 3-1.3: new full-speed USB device number 5 using uhci_hcd
[   15.567013] acpi device:3c: registered as cooling_device2
[   15.567477] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   15.567523] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.567542] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   15.567599] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.567636] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.567705] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.567734] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.613368] HDMI status: Codec=2 Pin=3 Presence_Detect=0 ELD_Valid=0
[   15.613509] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.613672] input: HDA Intel Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.613812] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.613951] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.614094] input: HDA Intel Dock Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   15.647403] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input14
[   15.659228] Bluetooth: Core ver 2.16
[   15.659302] NET: Registered protocol family 31
[   15.659304] Bluetooth: HCI device and connection manager initialized
[   15.659307] Bluetooth: HCI socket layer initialized
[   15.659309] Bluetooth: L2CAP socket layer initialized
[   15.659512] Bluetooth: SCO socket layer initialized
[   15.659973] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.661456] usbcore: registered new interface driver btusb
[   15.664492] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input15
[   16.197458] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.536217] init: failsafe main process (782) killed by TERM signal
[   16.632959] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.632963] Bluetooth: BNEP filters: protocol multicast
[   16.634594] Bluetooth: RFCOMM TTY layer initialized
[   16.634599] Bluetooth: RFCOMM socket layer initialized
[   16.634601] Bluetooth: RFCOMM ver 1.11
[   16.684875] type=1400 audit(1348010366.998:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=882 comm="apparmor_parser"
[   16.686918] type=1400 audit(1348010366.998:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=881 comm="apparmor_parser"
[   16.687766] type=1400 audit(1348010366.998:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=882 comm="apparmor_parser"
[   16.688017] type=1400 audit(1348010367.002:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=882 comm="apparmor_parser"
[   16.701202] type=1400 audit(1348010367.014:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=883 comm="apparmor_parser"
[   16.703030] type=1400 audit(1348010367.014:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=885 comm="apparmor_parser"
[   16.703514] type=1400 audit(1348010367.014:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=885 comm="apparmor_parser"
[   16.858438] ppdev: user-space parallel port driver
[   17.232321] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.288122] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   17.288365] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.288708] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.429698] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   17.429702] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   17.429705] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   17.430069] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.840918] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.840923] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   18.841085] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.176205] eth0: no IPv6 routers present
[B]6 ) Network configuration
 [/B] *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:de:44:82
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.7-7 ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:54:18:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-30-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

[B]7 ) Scan for networks:

[/B]Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
[B]8 ) Ubuntu Version: 

[/B]Description:    Ubuntu 12.04.1 LTS

[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B]3.2.0-30-generic-pae i686

[B]10 ) Restarting the network:

 [/B]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... 



Thanks in advance for any help!!

---

### Post by Luigi2012SM64DS on 2012-09-18
Hey. Is there a possible way you could connect to internet using lan or something?
once you get internet you need to install these 2 packages:
[http://packages.ubuntu.com/precise/b43-fwcutter](http://packages.ubuntu.com/precise/b43-fwcutter)
[http://packages.ubuntu.com/precise/firmware-b43-installer](http://packages.ubuntu.com/precise/firmware-b43-installer)

---

### Post by Dtruffles on 2012-09-19
Alright, I have installed the two programs. Where do I go from here?

Thank you so much for the reply!

---

### Post by Luigi2012SM64DS on 2012-09-19
just choose your network from the place it says firmware not ready.

---

