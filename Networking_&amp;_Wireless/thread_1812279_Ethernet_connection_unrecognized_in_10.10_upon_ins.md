---
title: "Ethernet connection unrecognized in 10.10 upon install (LiveCD worked)"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by LupintheThird on 2011-07-26
Hello, everyone.

I have tried countless things and am at a complete loss. I'm pretty new to Ubuntu and Linux in general, just so everyone knows. 

Here's my problem: I can run the 10.10 install disc as a Live CD and have perfectly functional internet. However, when I install into a clean ext4 partition, I have zero internet support. I have Googled the heck out of this problem, too. I've tried tinkering with IPv6 settings, I've tried scouring my BIOS for anything relating to "Wake-on-LAN" (It's enabled in Windows 7, by the way, which is what I dual-boot into), and several other network-related ideas I've read online. None have had any effect. I am willing to welcome any diagnostic suggestions. Please and thank you for any and all help you can provide.

EDIT: Additional details: ethernet worked like a champ in 10.04, and in 10.10 when I did an upgrade instead of a clean install. I had this same ethernet problem in a clean 11.04 install (which also worked in Live CD form), too, which is why I tried 10.04 to begin with.

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal please
```
sudo lshw -C network
```
```
lspci -nn
```
```
lsmod
```
```
ifconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

This an ethernet problem only your wireless works correct?

What version of ubuntu are you using now?
Thank you

---

### Post by LupintheThird on 2011-07-26
I tried wireless with my 11.04 install attempt, but could not get a connection even with correct WiFi credentials. Because that failed, I didn't try installing my wireless drivers in 10.10 (i386), which is what I currently have installed.

Strangely, I might have misremembered which LiveCD worked. I tried running the 10.10 install CD with "Try Ubuntu" and left it overnight, and it never got past that screen (Try/Install). I may have damaged the CD-R while it's been out of the drive. I definitely had it working with an 11.04 install disc running as a LiveCD, however.

UPDATE: Just retried the 10.10 Install disc as a LiveCD and it's working fine and has ethernet connection.

```
lshw -C network :

  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:04:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:cfefe000-cfefffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:16:bc:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-30-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg


lspci -nn :

00:00.0 Host bridge [0600]: nVidia Corporation C55 Host Bridge [10de:03a2] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ac] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03aa] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a9] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ab] (rev a1)
00:00.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03a8] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b5] (rev a1)
00:00.7 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ad] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ae] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03af] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b0] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b1] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b2] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b3] (rev a1)
00:02.0 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03b6] (rev a1)
00:02.1 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03bc] (rev a1)
00:02.2 RAM memory [0500]: nVidia Corporation C55 Memory Controller [10de:03ba] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b7] (rev a1)
00:06.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03b9] (rev a1)
00:07.0 PCI bridge [0604]: nVidia Corporation C55 PCI Express bridge [10de:03bb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G71 [GeForce 7900 GS] [10de:0292] (rev a1)
04:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

lsmod :

Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40524  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218460  1 
binfmt_misc             6599  1 
arc4                    1165  2 
snd_hda_intel          22299  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
nouveau               518076  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   169225  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ttm                    56825  1 nouveau
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30200  1 nouveau
mac80211              231927  1 b43
usblp                  10651  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168796  4 nouveau,ttm,drm_kms_helper
cfg80211              144790  2 b43,mac80211
led_class               2633  1 b43
joydev                  8767  0 
agpgart                32107  2 ttm,drm
psmouse                59033  0 
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 nouveau
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
i2c_nforce2             5275  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
floppy                 54343  0 
ssb                    39352  1 b43
forcedeth              49753  0 
sata_nv                19420  4 
pata_amd                8746  1 

ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:04:4b:06:48:8f  
          inet6 addr: fe80::204:4bff:fe06:488f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127809 (127.8 KB)  TX bytes:7423 (7.4 KB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

---

### Post by wildmanne39 on 2011-07-26
Hi, rerun this command please
```
sudo lshw -C network
```
And post the output here.
Thank you

---

### Post by LupintheThird on 2011-07-26
Sorry, I actually did use "sudo" for the previous posting, I just didn't type it out with "sudo" in the little header. That said, I'll go do it again for you, if you like.

---

### Post by LupintheThird on 2011-07-26
Results of sudo lshw -C network :

```
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:04:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:cfefe000-cfefffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:16:bc:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-30-generic-pae firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg


```

---

### Post by wildmanne39 on 2011-07-26
Hi, I asked a friend who is the expert on these matters to help out.

It is strange that your wireless network is showing as your Network controller, I have not seen that before.

I do know that I can help you get your wireless card working after the ethernet problem is solved.

I have that same card and it works great.

---

### Post by LupintheThird on 2011-07-26
Thanks a lot! I really appreciate the help.

I'm going to try something in the meantime. I'm going to clear my CMOS settings to see if that might solve the problem.

---

### Post by wildmanne39 on 2011-07-26
Hi, that might help, also make sure that your lan is on in the bios, and while you have it open make sure the card is seated good.

---

### Post by LupintheThird on 2011-07-26
My CMOS battery is actually dead, so all I need to do to get defaults is kill the PSU for a minute. :) My LAN card is actually on-board, by the way. I have a BFG nVidia 650i Ultra motherboard. Unfortunately, I can't check to see if I have an up-to-date BIOS because BFG went under almost a year ago...sigh.

EDIT: As far as I can tell, the only LAN-related option I have in the BIOS is "Mac LAN," and that is set to "Auto" (the only other option is "Disabled").

---

### Post by wildmanne39 on 2011-07-26
Hi, run these commands in a terminal and see if you get any error messages.
```
dmesg |tail -n300
```
Thank you

---

### Post by LupintheThird on 2011-07-26
I got one. Here's all the output anyway:

```
[    0.594338]   alloc kstat_irqs on node -1
[    0.594343] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.594358] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.594366] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.594664] Fixed MDIO Bus: probed
[    0.594694] PPP generic driver version 2.4.2
[    0.594724] tun: Universal TUN/TAP device driver, 1.6
[    0.594726] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.594801] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.595060] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.595063]   alloc irq_desc for 21 on node -1
[    0.595065]   alloc kstat_irqs on node -1
[    0.595069] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.595078] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.595080] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.595114] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.595140] ehci_hcd 0000:00:0b.1: debug port 1
[    0.595148] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.595166] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xcfffe000
[    0.604563] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.604669] hub 1-0:1.0: USB hub found
[    0.604674] hub 1-0:1.0: 8 ports detected
[    0.604751] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.605012] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.605015]   alloc irq_desc for 20 on node -1
[    0.605017]   alloc kstat_irqs on node -1
[    0.605021] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.605029] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.605032] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.605065] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.605086] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xcffff000
[    0.663184] hub 2-0:1.0: USB hub found
[    0.663189] hub 2-0:1.0: 8 ports detected
[    0.663265] uhci_hcd: USB Universal Host Controller Interface driver
[    0.663350] PNP: No PS/2 controller found. Probing ports directly.
[    0.666315] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.666320] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.666388] mice: PS/2 mouse device common for all mice
[    0.666492] rtc_cmos 00:06: RTC can wake from S4
[    0.666530] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.666560] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.666644] device-mapper: uevent: version 1.0.3
[    0.666746] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.666868] device-mapper: multipath: version 1.1.1 loaded
[    0.666871] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.666973] EISA: Probing bus 0 at eisa.0
[    0.666976] EISA: Cannot allocate resource for mainboard
[    0.666978] Cannot allocate resource for EISA slot 1
[    0.666980] Cannot allocate resource for EISA slot 2
[    0.666981] Cannot allocate resource for EISA slot 3
[    0.666983] Cannot allocate resource for EISA slot 4
[    0.666985] Cannot allocate resource for EISA slot 5
[    0.666987] Cannot allocate resource for EISA slot 6
[    0.666988] Cannot allocate resource for EISA slot 7
[    0.666990] Cannot allocate resource for EISA slot 8
[    0.666992] EISA: Detected 0 cards.
[    0.667168] cpuidle: using governor ladder
[    0.667170] cpuidle: using governor menu
[    0.667451] TCP cubic registered
[    0.667568] NET: Registered protocol family 10
[    0.667909] lo: Disabled Privacy Extensions
[    0.668128] NET: Registered protocol family 17
[    0.668173] Using IPI No-Shortcut mode
[    0.668237] PM: Resume from disk failed.
[    0.668247] registered taskstats version 1
[    0.668509]   Magic number: 3:509:132
[    0.668528] acpi PNP0C02:04: hash matches
[    0.668541] acpi device:07: hash matches
[    0.668574] rtc_cmos 00:06: setting system clock to 2011-07-26 14:06:24 UTC (1311689184)
[    0.668577] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.668578] EDD information not available.
[    0.944293] isapnp: No Plug & Play device found
[    0.944342] Freeing unused kernel memory: 708k freed
[    0.944702] Write protecting the kernel text: 5100k
[    0.944799] Write protecting the kernel read-only data: 2016k
[    0.961953] udev[98]: starting version 163
[    0.970377] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.996369] sata_nv 0000:00:0e.0: version 3.5
[    0.996387] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.996389] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.996436] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.007617] scsi0 : sata_nv
[    1.008766] scsi1 : sata_nv
[    1.008955] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    1.008959] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    1.008992] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.008995] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.009038] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.009217] scsi2 : sata_nv
[    1.009309] scsi3 : sata_nv
[    1.009493] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
[    1.009497] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
[    1.009518] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.009804] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.009811] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.009816] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.009858] nv_probe: set workaround bit for reversed mac addr
[    1.010890] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    1.010895]   alloc irq_desc for 18 on node -1
[    1.010897]   alloc kstat_irqs on node -1
[    1.010904] b43-pci-bridge 0000:04:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    1.010932] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.010938] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.010944] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.010949] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.010955] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.014256] ssb: Sonics Silicon Backplane found on PCI device 0000:04:0a.0
[    1.052936] FDC 0 is a post-1991 82077
[    1.097858] hub 1-2:1.0: USB hub found
[    1.098213] hub 1-2:1.0: 4 ports detected
[    1.208021] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.316036] ata3: SATA link down (SStatus 0 SControl 300)
[    1.464166] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.468464] usb 1-2.1: new full speed USB device using ehci_hcd and address 5
[    1.477065] ata1.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    1.477070] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.486478] ata1.00: configured for UDMA/133
[    1.486628] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    1.486799] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.486881] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.486930] sd 0:0:0:0: [sda] Write Protect is off
[    1.486933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.486953] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.487177]  sda: sda1 < sda5 sda6 > sda2 sda3
[    1.504453] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.524760] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
[    1.524764] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    1.524798] pata_amd 0000:00:0d.0: version 0.4.1
[    1.524835] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.524932] scsi4 : pata_amd
[    1.525042] scsi5 : pata_amd
[    1.525843] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    1.525846] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    1.596991] usbcore: registered new interface driver hiddev
[    1.599103] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input2
[    1.599192] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:0b.1-2.1/input0
[    1.606058] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.1/input/input3
[    1.606183] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:0b.1-2.1/input1
[    1.623484] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.2/input/input4
[    1.623615] generic-usb 0003:045E:0745.0003: input,hiddev96,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v1.0] on usb-0000:00:0b.1-2.1/input2
[    1.623631] usbcore: registered new interface driver usbhid
[    1.623633] usbhid: USB HID core driver
[    1.644471] usb 1-2.2: new full speed USB device using ehci_hcd and address 6
[    1.766019] input:                 TabletPF1209 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input5
[    1.766117] input:                 TabletPF1209 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input6
[    1.766201] input:                 TabletPF1209 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.2/1-2.2:1.0/input/input7
[    1.766284] generic-usb 0003:5543:0042.0004: input,hidraw3: USB HID v1.10 Mouse [                TabletPF1209] on usb-0000:00:0b.1-2.2/input0
[    1.808339] ata2: SATA link down (SStatus 0 SControl 300)
[    1.817390] ata5.01: ATAPI: Memorex DVD16+/-DL4RWlD2, JWS6, max UDMA/66
[    1.817420] ata5: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc50000) ACPI=0x1f01f (600:30:0x1c)
[    1.833814] ata5.01: configured for UDMA/66
[    1.840468] usb 1-2.3: new high speed USB device using ehci_hcd and address 7
[    1.941979] Initializing USB Mass Storage driver...
[    1.942133] scsi6 : usb-storage 1-2.3:1.0
[    1.942278] usbcore: registered new interface driver usb-storage
[    1.942281] USB Mass Storage support registered.
[    2.040416] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.117600] ata4: SATA link down (SStatus 0 SControl 300)
[    2.118445] scsi 4:0:1:0: CD-ROM            Memorex  DVD16+/-DL4RWlD2 JWS6 PQ: 0 ANSI: 5
[    2.122138] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.122142] Uniform CD-ROM driver Revision: 3.20
[    2.122269] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    2.122340] sr 4:0:1:0: Attached scsi generic sg1 type 5
[    2.122452] ata6: port disabled. ignoring.
[    2.237573] usb 2-7: new low speed USB device using ohci_hcd and address 2
[    2.485679] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input8
[    2.485743] generic-usb 0003:06A3:8021.0005: input,hidraw4: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-7/input0
[    2.516228] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.1/input/input9
[    2.516358] generic-usb 0003:06A3:8021.0006: input,hiddev97,hidraw5: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-7/input1
[    2.943523] scsi 6:0:0:0: Direct-Access     Crucial  Gizmo! overdrive 2.00 PQ: 0 ANSI: 2
[    2.944043] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.944616] sd 6:0:0:0: [sdb] 1997312 512-byte logical blocks: (1.02 GB/975 MiB)
[    2.945369] sd 6:0:0:0: [sdb] Write Protect is off
[    2.945373] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    2.945376] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.948372] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.948388]  sdb:
[    2.951368] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.951372] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.741890] udev[408]: starting version 163
[   10.751770] lp: driver loaded but no devices found
[   10.829331] Adding 3380220k swap on /dev/sda6.  Priority:-1 extents:1 across:3380220k 
[   10.841062] Linux agpgart interface v0.103
[   10.841226] i2c i2c-0: nForce2 SMBus adapter at 0xfc00
[   10.841288] i2c i2c-1: nForce2 SMBus adapter at 0xf800
[   10.888666] WARNING! power/level is deprecated; use power/control instead
[   10.892969] [drm] Initialized drm 1.1.0 20060810
[   10.896750] cfg80211: Calling CRDA to update world regulatory domain
[   10.927659] cfg80211: World regulatory domain updated:
[   10.927662]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.927665]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.927667]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.927670]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.927672]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.927675]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.928650] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1734
[   10.928722] usbcore: registered new interface driver usblp
[   10.941095] type=1400 audit(1311710794.769:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=688 comm="apparmor_parser"
[   10.941714] type=1400 audit(1311710794.769:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=688 comm="apparmor_parser"
[   10.942051] type=1400 audit(1311710794.769:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=688 comm="apparmor_parser"
[   10.967344] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   10.967351]   alloc irq_desc for 16 on node -1
[   10.967353]   alloc kstat_irqs on node -1
[   10.967360] nouveau 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   10.967365] nouveau 0000:01:00.0: setting latency timer to 64
[   10.968734] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.970167] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x049200a2)
[   10.972195] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   11.011748] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   11.011752] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   11.011755] [drm] nouveau 0000:01:00.0: Bios version 05.71.22.41
[   11.011758] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[   11.011760] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[   11.011762] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   11.011765] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00000028
[   11.011768] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 03000302 00000000
[   11.011770] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   11.011772] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 0c011312 00000000
[   11.011774] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 020223f1 00c0c080
[   11.011778] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[   11.011780] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   11.011783] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   11.011786] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   11.011788] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   11.011790] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   11.011800] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD1A8
[   11.011848] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xDA9B
[   11.018429] ACPI: PCI Interrupt Link [APCI] enabled at IRQ 22
[   11.018434] HDA Intel 0000:00:10.1: PCI INT B -> Link[APCI] -> GSI 22 (level, low) -> IRQ 22
[   11.018437] hda_intel: Disable MSI for Nvidia chipset
[   11.018459] HDA Intel 0000:00:10.1: setting latency timer to 64
[   11.027062] phy0: Selected rate control algorithm 'minstrel'
[   11.027680] Registered led device: b43-phy0::tx
[   11.027701] Registered led device: b43-phy0::rx
[   11.027720] Registered led device: b43-phy0::radio
[   11.027789] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   11.039254] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   11.057088] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE4C9
[   11.057109] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE644
[   11.081080] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE7A0
[   11.081088] [drm] nouveau 0000:01:00.0: Detected 256MiB VRAM
[   11.096532] [TTM] Zone  kernel: Available graphics memory: 416700 kiB.
[   11.096534] [TTM] Zone highmem: Available graphics memory: 2056608 kiB.
[   11.096536] [TTM] Initializing pool allocator.
[   11.097625] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   11.099338] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   11.100705] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   11.100712] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   11.100718] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   11.138932] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   11.139035] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   11.139064] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   11.140364] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[   11.140367] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[   11.140370] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[   11.140372] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[   11.140375] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 4)
[   11.214027] type=1400 audit(1311710795.041:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=973 comm="apparmor_parser"
[   11.214645] type=1400 audit(1311710795.041:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=973 comm="apparmor_parser"
[   11.214982] type=1400 audit(1311710795.041:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=973 comm="apparmor_parser"
[   11.215311] type=1400 audit(1311710795.041:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=976 comm="apparmor_parser"
[   11.215957] type=1400 audit(1311710795.041:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=974 comm="apparmor_parser"
[   11.216208] type=1400 audit(1311710795.041:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=976 comm="apparmor_parser"
[   11.216443] type=1400 audit(1311710795.041:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=977 comm="apparmor_parser"
[   11.329919] [drm] nouveau 0000:01:00.0: allocated 1680x1050 fb: 0x49000, bo f6eb6400
[   11.340886] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[   11.340889] [drm] nouveau 0000:01:00.0: 0xC585: Parsing digital output script table
[   11.397033] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[   11.397036] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[   11.397694] Console: switching to colour frame buffer device 210x65
[   11.398269] fb0: nouveaufb frame buffer device
[   11.398271] drm: registered panic notifier
[   11.398274] Slow work thread pool: Starting up
[   11.398342] Slow work thread pool: Ready
[   11.398350] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   11.627066] hda_codec: ALC889A: BIOS auto-probing.
[   11.651343] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.651347] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.651350] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   12.190332] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   12.191753] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   12.284216] ppdev: user-space parallel port driver
[   12.501939] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   12.946617] usb 1-6: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   13.722038] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   22.336026] eth0: no IPv6 routers present
[  207.048296] usb 1-2.3: reset high speed USB device using ehci_hcd and address 7
[  207.157654] usb 1-2.3: USB disconnect, address 7
[  260.897006] usb 1-2.3: new high speed USB device using ehci_hcd and address 8
[  260.992241] scsi7 : usb-storage 1-2.3:1.0
[  261.994018] scsi 7:0:0:0: Direct-Access     Crucial  Gizmo! overdrive 2.00 PQ: 0 ANSI: 2
[  261.994510] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  261.996395] sd 7:0:0:0: [sdb] 1997312 512-byte logical blocks: (1.02 GB/975 MiB)
[  261.997879] sd 7:0:0:0: [sdb] Write Protect is off
[  261.997884] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  261.997887] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  262.000869] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  262.000876]  sdb:
[  262.002885] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  262.002888] sd 7:0:0:0: [sdb] Attached SCSI removable disk


```

Note: I tried to download and install the b43 firmware app recommended in the sticky thread up top, but it requires an internet connection to install, so it failed.

---

### Post by wildmanne39 on 2011-07-26
Hi, I am going to keep researching this issue in the mean time you can have a look at this link on how to install the firmware for your wireless card with out an internet connection if you want too.

Your card is the 4306. Just do not install bcmwl-kerrnel-source like it says too.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Thank you

---

### Post by LupintheThird on 2011-07-26
Heads-up: I'm going to try using the wireless card firmware install method outlined here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

EDIT: What a coincidence! Heh. Different tutorial, though, so I'll go with yours, instead.

This was what I did to install Wi-Fi on 11.04, but I still did not have internet access after successful install. I would like to try it again, though. Just to see.

FYI: No luck on the BIOS tweaks. Still getting "Wired Connection Disconnected" messages shortly after boot.

---

### Post by chili555 on 2011-07-26
> nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)That is the ethernet card. It uses the driver forcedeth. I suggest you look at:```
sudo cat /var/log/syslog | grep -e forcedeth -e 14.0
```In this case 14.0 is part of the bus number the ethernet card is on.

---

### Post by LupintheThird on 2011-07-26
> **chili555 said:**
> That is the ethernet card. It uses the driver forcedeth. I suggest you look at:```
sudo cat /var/log/syslog | grep -e forcedeth -e 14.0
```In this case 14.0 is part of the bus number the ethernet card is on.

Thanks, I ran this code, but the output is sooo huge (it's even showing time logs from the 14:00 hour) that I can't copy-paste it all--it's cut off at the top. Should I just try " -e forcedeth " instead?


EDIT: Here's the output with  just " -e forcedeth " at the end. Is there a way to display text in terminal that has scrolled past the top?

```
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.024927] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.025298] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.025303] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.544776] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.544780] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 01:28:50 reed-BFGRINF650iU NetworkManager[1153]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029245] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029522] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029527] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.549227] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.549230] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 08:06:04 reed-BFGRINF650iU NetworkManager[1098]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034057] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034355] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034359] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.554293] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.554297] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 11:23:57 reed-BFGRINF650iU NetworkManager[1104]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.989986] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.990298] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.990303] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    1.496838] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    1.496841] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 12:49:14 reed-BFGRINF650iU NetworkManager[1117]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.014830] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.015386] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.015390] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.520813] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.520817] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 12:50:59 reed-BFGRINF650iU NetworkManager[1124]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026480] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026753] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026758] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.549740] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.549744] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 13:46:10 reed-BFGRINF650iU NetworkManager[1134]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.030947] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.031266] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.031271] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.554275] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.554278] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 13:52:32 reed-BFGRINF650iU NetworkManager[1122]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009518] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009811] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009816] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524760] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524764] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033050] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033341] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033346] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552759] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552763] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
```

---

### Post by chili555 on 2011-07-26
I should have added that if there are numerous repeats, we only need to see one repeat; in your case 8-10 lines. However, if you ever wanted to see the last zillion lines, you can pipe it to a text file:```
some_command > lupin.txt
```The text file will be in your user directory and you can examine it with leisure.

In your case, we have many repeats of the same thing:> [    1.033050] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033341] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033346] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552759] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552763] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)It all looks perfectly normal! The driver loads without warning or error and an interface eth0 is created. So far, I see nothing to fix. Now look at:```
sudo cat /var/log/syslog | grep -e eth0 -e etwork
```If there are many lines of repeats, just post the last 8-10 lines that illustrate the sequence.

---

### Post by LupintheThird on 2011-07-26
What am I looking for, exactly? I'm copy-pasting everything that isn't displayed because of a timestamp or an obviously unrelated value. (EDIT: I figured out how to display unlimited previous lines after a bit of Googling.)

EDIT: Talk about crazy timing today. Heh. Following the next step now, but feel free to thumb through this to see if anything sticks out at you.

```
Jul 26 00:50:42 reed-BFGRINF650iU kernel: [ 2214.032061] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
Jul 26 00:50:42 reed-BFGRINF650iU kernel: [ 2214.032065] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.367348] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.367353] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.367382] pci 0000:00:14.0: supports D1 D2
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.367384] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.367388] pci 0000:00:14.0: PME# disabled
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.469327] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    0.469330] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.024927] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.025298] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.025303] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.544776] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [    1.544780] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   11.678220] type=1400 audit(1311665329.497:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=695 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   11.678835] type=1400 audit(1311665329.497:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   11.679189] type=1400 audit(1311665329.497:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.303778] type=1400 audit(1311665330.121:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1043 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.304032] type=1400 audit(1311665330.121:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1044 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.304676] type=1400 audit(1311665330.125:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1044 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.305019] type=1400 audit(1311665330.125:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1044 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.305228] type=1400 audit(1311665330.125:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1047 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.305266] type=1400 audit(1311665330.125:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1048 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU kernel: [   12.305832] type=1400 audit(1311665330.125:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1045 comm="apparmor_parser"
Jul 26 01:28:50 reed-BFGRINF650iU NetworkManager[1153]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 01:28:50 reed-BFGRINF650iU NetworkManager[1153]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 01:28:50 reed-BFGRINF650iU NetworkManager[1153]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.72 BogoMIPS (lpj=9601440)
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.358728] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.358733] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.358764] pci 0000:00:14.0: supports D1 D2
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.358766] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.358769] pci 0000:00:14.0: PME# disabled
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.457329] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    0.457332] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029245] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029522] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.029527] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.549227] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [    1.549230] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.320888] type=1400 audit(1311689163.148:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=675 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.321498] type=1400 audit(1311689163.148:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=675 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.321832] type=1400 audit(1311689163.152:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=675 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.658447] type=1400 audit(1311689163.488:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=983 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.659763] type=1400 audit(1311689163.488:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.660049] type=1400 audit(1311689163.488:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=988 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.660510] type=1400 audit(1311689163.488:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=987 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.661731] type=1400 audit(1311689163.492:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=985 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.669494] type=1400 audit(1311689163.496:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=985 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU kernel: [   12.674271] type=1400 audit(1311689163.504:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=985 comm="apparmor_parser"
Jul 26 08:06:03 reed-BFGRINF650iU NetworkManager[1098]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 08:06:03 reed-BFGRINF650iU NetworkManager[1098]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 08:06:04 reed-BFGRINF650iU NetworkManager[1098]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.358692] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.358698] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.358729] pci 0000:00:14.0: supports D1 D2
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.358731] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.358735] pci 0000:00:14.0: PME# disabled
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.461331] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.461333] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    0.461400] system 00:0d: [mem 0xfeff0000] has been reserved
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034057] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034355] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.034359] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.554293] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [    1.554297] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [   11.698052] type=1400 audit(1311701036.525:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=732 comm="apparmor_parser"
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [   11.698666] type=1400 audit(1311701036.525:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
Jul 26 11:23:56 reed-BFGRINF650iU kernel: [   11.699005] type=1400 audit(1311701036.525:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.192980] type=1400 audit(1311701037.017:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1000 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.193588] type=1400 audit(1311701037.021:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=999 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.193604] type=1400 audit(1311701037.021:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1000 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.193951] type=1400 audit(1311701037.021:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1000 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.194819] type=1400 audit(1311701037.021:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1001 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.195326] type=1400 audit(1311701037.021:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1004 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU kernel: [   12.195495] type=1400 audit(1311701037.021:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1003 comm="apparmor_parser"
Jul 26 11:23:57 reed-BFGRINF650iU NetworkManager[1104]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 11:23:57 reed-BFGRINF650iU NetworkManager[1104]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 11:23:57 reed-BFGRINF650iU NetworkManager[1104]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.358713] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.358718] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.358749] pci 0000:00:14.0: supports D1 D2
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.358751] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.358755] pci 0000:00:14.0: PME# disabled
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.457329] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.457332] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.989986] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.990298] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    0.990303] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    1.496838] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [    1.496841] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   13.639909] type=1400 audit(1311706153.465:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=702 comm="apparmor_parser"
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   13.640552] type=1400 audit(1311706153.469:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=702 comm="apparmor_parser"
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   13.640887] type=1400 audit(1311706153.469:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=702 comm="apparmor_parser"
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   14.073897] [drm] nouveau 0000:01:00.0: allocated 1680x1050 fb: 0x49000, bo f165ec00
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   14.084892] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   14.084896] [drm] nouveau 0000:01:00.0: 0xC585: Parsing digital output script table
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   14.141034] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
Jul 26 12:49:13 reed-BFGRINF650iU kernel: [   14.141039] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.179493] type=1400 audit(1311706154.005:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1012 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.179757] type=1400 audit(1311706154.005:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1013 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.180371] type=1400 audit(1311706154.005:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1013 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.180762] type=1400 audit(1311706154.009:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1016 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.180797] type=1400 audit(1311706154.009:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1013 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.181509] type=1400 audit(1311706154.009:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1016 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU kernel: [   14.183770] type=1400 audit(1311706154.009:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1017 comm="apparmor_parser"
Jul 26 12:49:14 reed-BFGRINF650iU NetworkManager[1117]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 12:49:14 reed-BFGRINF650iU NetworkManager[1117]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 12:49:14 reed-BFGRINF650iU NetworkManager[1117]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.358718] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.358724] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.358754] pci 0000:00:14.0: supports D1 D2
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.358756] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.358760] pci 0000:00:14.0: PME# disabled
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.461327] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    0.461329] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.014830] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.015386] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.015390] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.520813] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [    1.520817] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   12.949312] type=1400 audit(1311706258.775:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=725 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   12.949934] type=1400 audit(1311706258.779:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   12.950268] type=1400 audit(1311706258.779:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.441920] type=1400 audit(1311706259.271:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1018 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.442049] type=1400 audit(1311706259.271:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1017 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.442539] type=1400 audit(1311706259.271:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1018 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.442881] type=1400 audit(1311706259.271:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1018 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.443719] type=1400 audit(1311706259.271:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1021 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.444469] type=1400 audit(1311706259.271:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1021 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU kernel: [   13.444684] type=1400 audit(1311706259.271:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1022 comm="apparmor_parser"
Jul 26 12:50:59 reed-BFGRINF650iU NetworkManager[1124]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 12:50:59 reed-BFGRINF650iU NetworkManager[1124]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 12:50:59 reed-BFGRINF650iU NetworkManager[1124]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.358689] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.358694] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.358726] pci 0000:00:14.0: supports D1 D2
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.358728] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.358731] pci 0000:00:14.0: PME# disabled
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.461341] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.461344] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    0.461400] system 00:0d: [mem 0x00100000-0xafeeffff] could not be reserved
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026480] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026753] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.026758] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.549740] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [    1.549744] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.175443] type=1400 audit(1311709570.001:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=760 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.176059] type=1400 audit(1311709570.005:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=760 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.176394] type=1400 audit(1311709570.005:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=760 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.764620] type=1400 audit(1311709570.593:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1050 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.766373] type=1400 audit(1311709570.597:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1110 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.766712] type=1400 audit(1311709570.597:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1055 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.766877] type=1400 audit(1311709570.597:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1060 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.767132] type=1400 audit(1311709570.597:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1110 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.767338] type=1400 audit(1311709570.597:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1055 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU kernel: [   11.767678] type=1400 audit(1311709570.597:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1055 comm="apparmor_parser"
Jul 26 13:46:10 reed-BFGRINF650iU avahi-daemon[1028]: Server startup complete. Host name is reed-BFGRINF650iU.local. Local service cookie is 1828031400.
Jul 26 13:46:10 reed-BFGRINF650iU NetworkManager[1134]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 13:46:10 reed-BFGRINF650iU NetworkManager[1134]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 13:46:10 reed-BFGRINF650iU NetworkManager[1134]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.358706] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.358711] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.358743] pci 0000:00:14.0: supports D1 D2
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.358745] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.358748] pci 0000:00:14.0: PME# disabled
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.461328] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    0.461331] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.030947] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.031266] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.031271] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.554275] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [    1.554278] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.105119] type=1400 audit(1311709951.936:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=742 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.105733] type=1400 audit(1311709951.936:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=742 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.106071] type=1400 audit(1311709951.936:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=742 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.141090] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.141096]   alloc irq_desc for 16 on node -1
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.141099]   alloc kstat_irqs on node -1
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.630370] type=1400 audit(1311709952.460:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1017 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.630697] type=1400 audit(1311709952.460:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1018 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.631312] type=1400 audit(1311709952.460:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1018 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.631628] type=1400 audit(1311709952.460:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1021 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.631653] type=1400 audit(1311709952.460:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1018 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.632376] type=1400 audit(1311709952.460:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1021 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU kernel: [   13.633095] type=1400 audit(1311709952.464:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1022 comm="apparmor_parser"
Jul 26 13:52:32 reed-BFGRINF650iU NetworkManager[1122]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 13:52:32 reed-BFGRINF650iU NetworkManager[1122]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 13:52:32 reed-BFGRINF650iU NetworkManager[1122]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 13:52:34 reed-BFGRINF650iU anacron[1490]: Anacron 2.3 started on 2011-07-26
Jul 26 13:52:34 reed-BFGRINF650iU anacron[1490]: Normal exit (0 jobs run)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul 26 14:06:35 reed-BFGRINF650iU rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="941" x-info="http://www.rsyslog.com"] (re)start
Jul 26 14:06:35 reed-BFGRINF650iU rsyslogd: rsyslogd's groupid changed to 103
Jul 26 14:06:35 reed-BFGRINF650iU rsyslogd: rsyslogd's userid changed to 101
Jul 26 14:06:35 reed-BFGRINF650iU rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.000000] Linux version 2.6.35-30-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #54-Ubuntu SMP Tue Jun 7 20:28:33 UTC 2011 (Ubuntu 2.6.35-30.54-generic-pae 2.6.35.13)


Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356671] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356757] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356917] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356920] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356923] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356925] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.356928] pci_root PNP0A08:00: host bridge window [mem 0xaff00000-0xcfffffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357770] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357773] pci 0000:00:03.0: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357824] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357827] pci 0000:00:06.0: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357875] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.357878] pci 0000:00:07.0: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358119] pci 0000:00:0a.1: reg 20: [io  0xfc00-0xfc3f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358125] pci 0000:00:0a.1: reg 24: [io  0xf800-0xf83f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358152] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358158] pci 0000:00:0a.1: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358230] pci 0000:00:0b.0: reg 10: [mem 0xcffff000-0xcfffffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358265] pci 0000:00:0b.0: supports D1 D2
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358267] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358271] pci 0000:00:0b.0: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358296] pci 0000:00:0b.1: reg 10: [mem 0xcfffe000-0xcfffe0ff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358335] pci 0000:00:0b.1: supports D1 D2
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358336] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358340] pci 0000:00:0b.1: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358385] pci 0000:00:0d.0: reg 20: [io  0xf400-0xf40f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358431] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358436] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358442] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358447] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358452] pci 0000:00:0e.0: reg 20: [io  0xe000-0xe00f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358457] pci 0000:00:0e.0: reg 24: [mem 0xcfffd000-0xcfffdfff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358510] pci 0000:00:0f.0: reg 10: [io  0x09e0-0x09e7]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358515] pci 0000:00:0f.0: reg 14: [io  0x0be0-0x0be3]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358521] pci 0000:00:0f.0: reg 18: [io  0x0960-0x0967]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358526] pci 0000:00:0f.0: reg 1c: [io  0x0b60-0x0b63]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358531] pci 0000:00:0f.0: reg 20: [io  0xcc00-0xcc0f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358536] pci 0000:00:0f.0: reg 24: [mem 0xcfffc000-0xcfffcfff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358633] pci 0000:00:10.1: reg 10: [mem 0xcfff4000-0xcfff7fff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358675] pci 0000:00:10.1: PME# supported from D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358678] pci 0000:00:10.1: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358718] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358723] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358754] pci 0000:00:14.0: supports D1 D2
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358756] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358760] pci 0000:00:14.0: PME# disabled
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358827] pci 0000:01:00.0: reg 10: [mem 0xcc000000-0xccffffff]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358836] pci 0000:01:00.0: reg 14: [mem 0xb0000000-0xbfffffff 64bit pref]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358844] pci 0000:01:00.0: reg 1c: [mem 0xcd000000-0xcdffffff 64bit]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358850] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358855] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    0.358883] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'



Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.008995] sata_nv 0000:00:0f.0: Using SWNCQ mode
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009038] sata_nv 0000:00:0f.0: setting latency timer to 64
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009217] scsi2 : sata_nv
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009309] scsi3 : sata_nv
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009493] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009497] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009518] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009804] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009811] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009816] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.009858] nv_probe: set workaround bit for reversed mac addr
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010890] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010895]   alloc irq_desc for 18 on node -1
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010897]   alloc kstat_irqs on node -1
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010904] b43-pci-bridge 0000:04:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010932] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010938] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010944] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010949] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.010955] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.014256] ssb: Sonics Silicon Backplane found on PCI device 0000:04:0a.0
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.052936] FDC 0 is a post-1991 82077
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.097858] hub 1-2:1.0: USB hub found
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.098213] hub 1-2:1.0: 4 ports detected
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.208021] usb 1-6: new high speed USB device using ehci_hcd and address 3
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.316036] ata3: SATA link down (SStatus 0 SControl 300)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.464166] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.468464] usb 1-2.1: new full speed USB device using ehci_hcd and address 5
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.477065] ata1.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.477070] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486478] ata1.00: configured for UDMA/133
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486628] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486799] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486881] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486930] sd 0:0:0:0: [sda] Write Protect is off
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.486953] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.487177]  sda: sda1 < sda5 sda6 > sda2 sda3
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.504453] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524760] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524764] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524798] pata_amd 0000:00:0d.0: version 0.4.1
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524835] pata_amd 0000:00:0d.0: setting latency timer to 64
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524932] scsi4 : pata_amd
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.525042] scsi5 : pata_amd
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.525843] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.525846] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.596991] usbcore: registered new interface driver hiddev
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.599103] input: Microsoft Microsoft® Nano Transceiver v1.0 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input2



Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Option High-Speed
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin AnyData
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Novatel
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin MotoC
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Sierra
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin ZTE
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Ericsson MBM
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Huawei
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin SimTech
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Gobi
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Generic
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Longcheer
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: Loaded plugin Option
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jul 26 14:06:35 reed-BFGRINF650iU modem-manager: (tty/ttyS0): could not get port's parent device
Jul 26 14:06:35 reed-BFGRINF650iU cron[1129]: (CRON) INFO (Running @reboot jobs)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    Ifupdown: get unmanaged devices count: 0
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WWAN enabled by radio killswitch; disabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Networking is enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): now managed
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): bringing up device.
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   11.627066] hda_codec: ALC889A: BIOS auto-probing.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <warn> (wlan0): firmware may be missing.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): deactivating device (reason: 2).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): carrier is OFF
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   11.651343] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   11.651347] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   11.651350] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): now managed
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): bringing up device.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): preparing device.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): deactivating device (reason: 2).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): carrier now ON (device state 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> modem-manager is now available
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Trying to start the supplicant...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) starting connection 'Auto eth0'
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)



Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.000000]   1 base 140000000 mask FF0000000 write-back
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.358576] pci 0000:00:14.0: reg 10: [mem 0xcfffb000-0xcfffbfff]
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.358581] pci 0000:00:14.0: reg 14: [io  0xc800-0xc807]
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.358610] pci 0000:00:14.0: supports D1 D2
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.358612] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.358616] pci 0000:00:14.0: PME# disabled
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.461353] system 00:00: [io  0x1400-0x147f] has been reserved
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.461356] system 00:00: [io  0x1480-0x14ff] has been reserved
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    0.461400] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033050] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033341] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.033346] forcedeth 0000:00:14.0: setting latency timer to 64
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552759] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552763] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [   11.705602] type=1400 audit(1311712791.534:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=765 comm="apparmor_parser"
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [   11.706219] type=1400 audit(1311712791.534:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=765 comm="apparmor_parser"
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [   11.706553] type=1400 audit(1311712791.534:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=765 comm="apparmor_parser"
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [   11.714402] Registered led device: b43-phy0::rx
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.176399] type=1400 audit(1311712792.006:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1000 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.177019] type=1400 audit(1311712792.006:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1000 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.177376] type=1400 audit(1311712792.006:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1000 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.178984] type=1400 audit(1311712792.006:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=999 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.179832] type=1400 audit(1311712792.006:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1001 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.180408] type=1400 audit(1311712792.010:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1004 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.181977] type=1400 audit(1311712792.010:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1003 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
reed@reed-BFGRINF650iU:~$  

```

---

### Post by LupintheThird on 2011-07-26
All right, I did the latter one, and I'm afraid it's well over 8-10 lines for any one sequence. I'll give you the last couple of instances it pulled, is that okay? It's still heavily truncated, of course....

```
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [    1.524760] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   10.941714] type=1400 audit(1311710794.769:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=688 comm="apparmor_parser"
Jul 26 14:06:35 reed-BFGRINF650iU kernel: [   11.214645] type=1400 audit(1311710795.041:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=973 comm="apparmor_parser"
Jul 26 14:06:35 reed-BFGRINF650iU avahi-daemon[1005]: Network interface enumeration completed.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> NetworkManager (version 0.8.1) is starting...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> trying to start the modem manager...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: init!
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/net/wlan0, iface: wlan0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: end _init.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    Ifupdown: get unmanaged devices count: 0
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: (160537424) ... get_connections.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    SCPlugin-Ifupdown: (160537424) ... get_connections (managed=false): return empty list.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]:    Ifupdown: get unmanaged devices count: 0
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WWAN enabled by radio killswitch; disabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Networking is enabled by state file
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): now managed
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): bringing up device.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <warn> (wlan0): firmware may be missing.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): deactivating device (reason: 2).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): carrier is OFF
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): now managed
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): bringing up device.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): preparing device.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): deactivating device (reason: 2).
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): carrier now ON (device state 2)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> modem-manager is now available
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Trying to start the supplicant...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) starting connection 'Auto eth0'
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> dhclient started with pid 1215
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): supplicant manager state:  down -> idle
Jul 26 14:06:35 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 26 14:06:35 reed-BFGRINF650iU dhclient: Listening on LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:06:35 reed-BFGRINF650iU dhclient: Sending on   LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:06:35 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:06:36 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:06:37 reed-BFGRINF650iU avahi-daemon[1005]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::204:4bff:fe06:488f.
Jul 26 14:06:37 reed-BFGRINF650iU avahi-daemon[1005]: New relevant interface eth0.IPv6 for mDNS.
Jul 26 14:06:37 reed-BFGRINF650iU avahi-daemon[1005]: Registering new address record for fe80::204:4bff:fe06:488f on eth0.*.
Jul 26 14:06:39 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:06:45 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:06:46 reed-BFGRINF650iU kernel: [   22.336026] eth0: no IPv6 routers present
Jul 26 14:06:51 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:06:52 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:06:55 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:01 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:09 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:07:10 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:13 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:17 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <warn> (eth0): DHCPv4 request timed out.
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1215
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> Marking connection 'Auto eth0' invalid.
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <warn> Activation (eth0) failed.
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jul 26 14:07:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): deactivating device (reason: 0).
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) starting connection 'eth0'
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> dhclient started with pid 1723
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 14:07:24 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 26 14:07:24 reed-BFGRINF650iU dhclient: Listening on LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:07:24 reed-BFGRINF650iU dhclient: Sending on   LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:07:24 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:07:25 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:28 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:36 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:07:37 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:40 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:47 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:07:58 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:07:59 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:08:02 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:08:07 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <warn> (eth0): DHCPv4 request timed out.
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1723
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> Marking connection 'eth0' invalid.
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <warn> Activation (eth0) failed.
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jul 26 14:08:09 reed-BFGRINF650iU NetworkManager[1111]: <info> (eth0): deactivating device (reason: 0).
Jul 26 14:36:56 reed-BFGRINF650iU NetworkManager[1111]: <info> kernel firmware directory '/lib/firmware' changed
Jul 26 14:37:01 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): firmware may now be available
Jul 26 14:37:01 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): device state change: 2 -> 2 (reason 0)
Jul 26 14:37:01 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): bringing up device.
Jul 26 14:37:01 reed-BFGRINF650iU NetworkManager[1111]: <warn> (wlan0): firmware may be missing.
Jul 26 14:37:01 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): deactivating device (reason: 0).
Jul 26 14:38:17 reed-BFGRINF650iU NetworkManager[1111]: <info> kernel firmware directory '/lib/firmware' changed
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): firmware may now be available
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): device state change: 2 -> 2 (reason 0)
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): bringing up device.
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): preparing device.
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): deactivating device (reason: 0).
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): supplicant interface state:  starting -> ready
Jul 26 14:38:21 reed-BFGRINF650iU NetworkManager[1111]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [    1.552759] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:06:48:8f
Jul 26 14:39:51 reed-BFGRINF650iU kernel: [   11.706219] type=1400 audit(1311712791.534:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=765 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU kernel: [   12.177019] type=1400 audit(1311712792.006:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1000 comm="apparmor_parser"
Jul 26 14:39:52 reed-BFGRINF650iU avahi-daemon[987]: Network interface enumeration completed.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> NetworkManager (version 0.8.1) is starting...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> trying to start the modem manager...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: init!
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/net/wlan0, iface: wlan0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: end _init.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: (136411984) ... get_connections.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    SCPlugin-Ifupdown: (136411984) ... get_connections (managed=false): return empty list.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:10.0/0000:04:0a.0/ssb0:0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> WWAN enabled by radio killswitch; disabled by state file
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Networking is enabled by state file
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): now managed
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): bringing up device.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): preparing device.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): deactivating device (reason: 2).
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): carrier is OFF
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'forcedeth' ifindex: 2)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): now managed
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): bringing up device.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): preparing device.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): deactivating device (reason: 2).
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): carrier now ON (device state 2)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> modem-manager is now available
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Trying to start the supplicant...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) starting connection 'Auto eth0'
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> dhclient started with pid 1255
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant manager state:  down -> idle
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 26 14:39:52 reed-BFGRINF650iU dhclient: Listening on LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:39:52 reed-BFGRINF650iU dhclient: Sending on   LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:39:52 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:39:52 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant interface state:  starting -> ready
Jul 26 14:39:53 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:39:54 reed-BFGRINF650iU avahi-daemon[987]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::204:4bff:fe06:488f.
Jul 26 14:39:54 reed-BFGRINF650iU avahi-daemon[987]: New relevant interface eth0.IPv6 for mDNS.
Jul 26 14:39:54 reed-BFGRINF650iU avahi-daemon[987]: Registering new address record for fe80::204:4bff:fe06:488f on eth0.*.
Jul 26 14:39:56 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:02 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:03 reed-BFGRINF650iU kernel: [   23.233526] eth0: no IPv6 routers present
Jul 26 14:40:10 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:40:11 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:14 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:19 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:29 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:40:30 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:33 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:36 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:37 reed-BFGRINF650iU NetworkManager[1093]: <warn> (eth0): DHCPv4 request timed out.
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1255
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> Marking connection 'Auto eth0' invalid.
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <warn> Activation (eth0) failed.
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jul 26 14:40:38 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): deactivating device (reason: 0).
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) starting connection 'Auto Bubba'
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0/wireless): access point 'Auto Bubba' has security, but secrets are required.
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 6 -> 3 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): deactivating device (reason: 0).
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) starting connection 'Auto Bubba'
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0/wireless): access point 'Auto Bubba' has security, but secrets are required.
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jul 26 14:40:40 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) starting connection 'eth0'
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> dhclient started with pid 1711
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 14:40:41 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 26 14:40:41 reed-BFGRINF650iU dhclient: Listening on LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:40:41 reed-BFGRINF650iU dhclient: Sending on   LPF/eth0/00:04:4b:06:48:8f
Jul 26 14:40:41 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:40:42 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:45 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:48 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0/wireless): connection 'Auto Bubba' has security, and secrets exist.  No new secrets needed.
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Config: added 'ssid' value 'Bubba'
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Config: added 'scan_ssid' value '1'
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Config: added 'psk' value '<omitted>'
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> Config: set interface ap_scan to 1
Jul 26 14:40:48 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  associating -> associated
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Bubba'.
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> dhclient started with pid 1716
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 14:40:49 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 14:40:52 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:40:57 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:40:58 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:01 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:09 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:41:10 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:13 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.3 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:21 reed-BFGRINF650iU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 26 14:41:23 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:26 reed-BFGRINF650iU dhclient: DHCPREQUEST of 192.168.2.4 on eth0 to 255.255.255.255 port 67
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <warn> (eth0): DHCPv4 request timed out.
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1711
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 7 -> 9 (reason 5)
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> Marking connection 'eth0' invalid.
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <warn> Activation (eth0) failed.
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Jul 26 14:41:26 reed-BFGRINF650iU NetworkManager[1093]: <info> (eth0): deactivating device (reason: 0).
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <warn> (wlan0): DHCPv4 request timed out.
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1716
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <warn> Activation (wlan0) failed for access point (Bubba)
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Marking connection 'Auto Bubba' invalid.
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <warn> Activation (wlan0) failed.
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jul 26 14:41:35 reed-BFGRINF650iU NetworkManager[1093]: <info> (wlan0): deactivating device (reason: 0).


```

---

### Post by wildmanne39 on 2011-07-26
Hi, how is getting your wireless card to work going?

---

### Post by LupintheThird on 2011-07-26
> **wildmanne39 said:**
> Hi, how is getting your wireless card to work going?

Hey again, sorry for not saying sooner. I did the install as directed and the network menu now shows several available wireless connections. I tried connecting to my personal one with the correct password and it failed to connect.

Also, I tried deleting and recreating my "eth0" wired connection at one point. It started as "Auto eth0," and I deleted that. Then I created "eth0," which I later renamed to "Auto eth0." But now, there are apparently two: Auto eth0 and eth0. Looking through their settings, they appear to be identical other than in name. Is this even remotely noteworthy?

---

### Post by wildmanne39 on 2011-07-26
Hi, I am just looking at your wireless here so now that you have installed your driver and firmware please run these commands again.
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by LupintheThird on 2011-07-26
```
reed@reed-BFGRINF650iU:~$ sudo lshw -C network
[sudo] password for reed: 
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:04:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:18 memory:cfefe000-cfefffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:16:bc:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-30-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


reed@reed-BFGRINF650iU:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


reed@reed-BFGRINF650iU:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


reed@reed-BFGRINF650iU:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
parport_pc             26378  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   218460  1 
snd_hda_intel          22299  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
nouveau               518076  2 
arc4                    1165  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ttm                    56825  1 nouveau
drm_kms_helper         30200  1 nouveau
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168796  4 nouveau,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   169225  0 
usblp                  10651  0 
mac80211              231927  1 b43
agpgart                32107  2 ttm,drm
i2c_algo_bit            5168  1 nouveau
joydev                  8767  0 
cfg80211              144790  2 b43,mac80211
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2633  1 b43
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
i2c_nforce2             5275  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40524  0 
usbhid                 36978  0 
hid                    67742  1 usbhid
floppy                 54343  0 
ssb                    39352  1 b43
pata_amd                8746  0 
forcedeth              49753  0 
sata_nv                19420  2 


```

Thanks again!

---

### Post by chili555 on 2011-07-26
> **wildmanne39 said:**
> Hi, how is getting your wireless card to work going?Looks like his firmware is all set. It's trying to connect. It looks like it connected at one point because it knows what IP address to ask for. Would you please try the wireless again with the ethernet cable disconnected? Also please post:```
sudo nm-tool
```Thanks.

---

### Post by LupintheThird on 2011-07-26
No luck on the wireless connection with ethernet unplugged. It tries and, after about a minute or so, gives me the "Wireless Disconnected" message. Same as with the wired ethernet.

```

NetworkManager Tool

State: connecting

- Device: wlan0  [Auto Bubba] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:11:50:16:BC:B8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Bubba:           Infra, 00:0D:3A:26:56:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA
    caw guest:       Infra, FE:1E:DF:FA:A0:4D, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA2
    caw:             Infra, F8:1E:DF:FA:A0:4D, Freq 2457 MHz, Rate 54 Mb/s, Strength 51 WPA2
    myqwest9409:     Infra, 00:24:7B:68:83:82, Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    myqwest0421:     Infra, 00:24:7B:A8:9D:B6, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    RefusedPartyProgram: Infra, 00:25:9C:55:CD:E4, Freq 2437 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    @Home4648:       Infra, 00:1E:E5:B8:46:48, Freq 2437 MHz, Rate 54 Mb/s, Strength 75


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:04:4B:06:48:8F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by chili555 on 2011-07-26
Is your network Bubba set to WPA only or mixed WPA and WPA2 mode? When you try to connect to it, does it try? Does it just fail or what? Are you challenged for the WPA key?

---

### Post by LupintheThird on 2011-07-26
I'm pretty sure it's either just WPA or *maybe* WPA2, but I don't think the MN-700 (Microsoft router) supported WPA2, so I'm fairly sure it's just WPA. I can double-check when I get back home.

It definitely tries to connect. Before setting up the connection for the first time, but after first installing the wireless card's firmware, it showed "Bubba" in the list of available networks. I selected it from the list and it prompted me for the key in a pop-up. Even after setting up the connection with the key, if I right-click on the connection, it will do the little "wavy" effect on the wireless icon. But the result is always the same: a "Wireless Connection: Disconnected" message in the upper-right corner of the screen after a minute or so.

---

### Post by chili555 on 2011-07-26
I always have the best luck with all manual entries *removed*. Then I see my network in the drop-down and supply the encryption key when challenged. Network Manager usually does all the work correctly. Broadcoms are generally pretty reliable.

Off for the night; see you tomorrow.

---

### Post by nm_geo on 2011-07-26
After doing some research I think maybe you have the wrong wireless firmware.

Please do 
```

dmesg | grep firmware
```I believe you need the b43-fwcutter which I also believe you have ..
and firmware-b43-installer..  

OPen Synaptic and search on  _bcm_  ,,, 
If you have firmware-b43legacy-installer I would remove it..

I base this on the following.
04:0a.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [B][COLOR=Red][14e4:4320] (rev 03)

[/COLOR][/B][COLOR=Red][COLOR=Black]and this link..

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Check supported column.. for the info in red
[/COLOR][/COLOR]

---

### Post by wildmanne39 on 2011-07-26
Hi, that does look like the case nm-geo I thought all 4306 used legacy, that is a nice catch. I have saved that site it is a great resource.

We have actually be trying very hard to get his ehternet to work that I over looked it.

You know what also when you remove the legacy driver I think your ethernet connection well work also.
Thank you

---

### Post by LupintheThird on 2011-07-26
Thanks nm_geo and chili555. I'll try them both tonight.

I'm primarily having trouble with my wired ethernet connection. I would much prefer to use it than my wireless anyway. But, if the system updates I can get through wireless fix the ethernet problem, I'm willing to give it a shot.

Failing all that, I'll just reinstall 10.04 and immediately upgrade to 10.10, then install all the updates and such after the OS/kernel upgrade. That should (probably) fix the problem anyway.

EDIT: Wow, I'm getting beaten to the punch a lot in this thread. :) 

wildmanne39, nm_geo, how to you recommend going about removing the driver? Should I just do the blacklist command shown on the linked site?

---

### Post by nm_geo on 2011-07-26
> **wildmanne39 said:**
> Hi, that does look like the case nm-geo I thought all 4306 used legacy, that is a nice catch. I have saved that site it is a great resource.

We have actually be trying very hard to get his ehternet to work that I over looked it.

You know what also when you remove the legacy driver I think your ethernet connection well work also.
Thank you

Well he might have the correct firmware I was really just checking.. If he has legacy though I think he needs the straight firmware.  Who knows I am having trouble trying to install a driver in Maverick that I use on all other versions right now LOL..

---

### Post by wildmanne39 on 2011-07-26
Hi, I looked through his lsmod again and I did not see a legacy driver, so that may not be it.

Possibly problems with security, I would tune it off and see if you can connect then.

---

### Post by LupintheThird on 2011-07-26
> **wildmanne39 said:**
> Hi, I looked through his lsmod again and I did not see a legacy driver, so that may not be it.

Possibly problems with security, I would tune it off and see if you can connect then.

Turn off security? Do you mean a "Security" feature in Ubuntu, or my wireless AP's WPA security encryption?

---

### Post by wildmanne39 on 2011-07-26
Hi, your wireless AP's WPA security encryption just to see if it will connect, I am not saying to leave it off, but that will give us more information.

---

### Post by LupintheThird on 2011-07-26
Sure thing. I should have an answer for you in about an hour when I'm home.

---

### Post by LupintheThird on 2011-07-27
Tried deleting all existing connections and disabling wireless security (FYI, it is JUST WPA, not WPA2 or a combo). Double-clicked on the unlocked "Bubba" SSID in the corner menu to connect. Still got the same result: wireless icon "thinking" for a minute, then the message: "Wireless network - Disconnected - you are now offline." Any further tests I should try while I have WPA off?

---

### Post by wildmanne39 on 2011-07-27
Hi, I am not sure I am to tired tonight to think clearly, so one of us well be back on here tomorrow.

---

### Post by LupintheThird on 2011-07-27
I might just give up and install 10.04 after all, then upgrade to 10.10. I think finding out what the problem is might be valuable for me in the long run, but if I run into trouble still, I'll post in here again. Thanks for everyone's help. I may yet be back. :P

---

### Post by LupintheThird on 2011-07-27
Just wanted to report that installing 10.04 clean and upgrading to 10.10 seems to have remedied the problem--and my tablet works correctly now, too (which was my REAL problem with 10.04)!

However, now my wireless card/firmware is not setup at all. Which method should I use to do that correctly? Thanks!

---

### Post by nm_geo on 2011-07-27
> **LupintheThird said:**
> Just wanted to report that installing 10.04 clean and upgrading to 10.10 seems to have remedied the problem--and my tablet works correctly now, too (which was my REAL problem with 10.04)!
 
However, now my wireless card/firmware is not setup at all. Which method should I use to do that correctly? Thanks!
 
With ethernet connected  
In terminal
 
```
 
sudo apt-get update

```
```
 
sudo apt-get upgrade

```
```
 
sudo apt-get install b43-fwcutter

```
```
 
sudo apt-get install firmware-b43-installer 

```
 
Or in Synaptic.. Reload
do a search on _bcm_
 
_Find_ 
 
b43-fwcutter (mark for install)
firmware-b43-installer (mark for install)
Apply

---

### Post by wildmanne39 on 2011-07-27
Hi, glad to hear that you lan is working again. 

Let us know how your wireless issue comes out.

---

### Post by LupintheThird on 2011-07-29
I am currently typing this with my eth0 connection disabled via my wireless connection.

Thanks, everyone!

Suggestion for everyone who has my motherboard/BIOS: Upgrade immediately from 10.04 to 10.10 via ethernet. Don't try a direct 10.10 install using the standard i386 install CD.

Thanks again!

---

### Post by wildmanne39 on 2011-07-29
Hi, I am happy to hear that,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

