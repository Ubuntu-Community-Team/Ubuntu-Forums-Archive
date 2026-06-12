---
title: "RTL8187SE Wireless LAN Controller on Ubuntu 10.04. LTS (Advent Roma C900)"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by benjkitz on 2010-08-30
Hi all, 

I've only been using Ubuntu for a couple of days on an Advent Roma C900 laptop with a RealTek RTL8187SE wireless card.  The wireless was working fine, until today when the wireless stopped being detected and I don't know why.  

I am still able to get internet via ethernet cable and other WiFi enabled devices are able to use the wireless with no issues.  

Below is all the information I can get from the codes in the How To sticky, I apologise that there is so much, but I don't yet know what is relevant in this situation:

**Wireless Brand, Model and chipset**
> 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

**Code: $ ifconfig**
> eth0      Link encap:Ethernet  HWaddr 00:03:0d:d1:f3:a6  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fed1:f3a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9116875 (9.1 MB)  TX bytes:1440933 (1.4 MB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4084978 (4.0 MB)  TX bytes:4084978 (4.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:24:21:c6:77:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f85a8000-f85a8100 

**Code: $ lsmod**
> Module                  Size  Used by
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_intel          21941  4 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  285076  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  20 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
intel_agp              24119  2 i915
rtl8187se             159435  0 
drm                   162409  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32200  2 
r8169                  34076  0 
mii                     4381  1 r8169


**Code: $ dmesg**
> [    0.312360] hub 1-0:1.0: 6 ports detected
[    0.312464]   alloc irq_desc for 23 on node -1
[    0.312466]   alloc kstat_irqs on node -1
[    0.312472] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.312490] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.312493] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.312522] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.312551] ehci_hcd 0000:00:1d.7: debug port 1
[    0.316453] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.318416] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe704c00
[    0.340102] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.340213] usb usb2: configuration #1 chosen from 1 choice
[    0.340238] hub 2-0:1.0: USB hub found
[    0.340246] hub 2-0:1.0: 6 ports detected
[    0.340303] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.340316] uhci_hcd: USB Universal Host Controller Interface driver
[    0.340355] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.340363] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.340366] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.340394] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.340431] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.340502] usb usb3: configuration #1 chosen from 1 choice
[    0.340524] hub 3-0:1.0: USB hub found
[    0.340530] hub 3-0:1.0: 2 ports detected
[    0.340566]   alloc irq_desc for 21 on node -1
[    0.340568]   alloc kstat_irqs on node -1
[    0.340573] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.340579] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.340582] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.340606] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.340638] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.340711] usb usb4: configuration #1 chosen from 1 choice
[    0.340731] hub 4-0:1.0: USB hub found
[    0.340737] hub 4-0:1.0: 2 ports detected
[    0.340776] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.340782] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.340785] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.340808] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.340834] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.340913] usb usb5: configuration #1 chosen from 1 choice
[    0.340933] hub 5-0:1.0: USB hub found
[    0.340938] hub 5-0:1.0: 2 ports detected
[    0.340979] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.340984] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.340988] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.341013] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.341038] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.341107] usb usb6: configuration #1 chosen from 1 choice
[    0.341127] hub 6-0:1.0: USB hub found
[    0.341132] hub 6-0:1.0: 2 ports detected
[    0.341169] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.341175] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.341179] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.341201] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.341227] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.341295] usb usb7: configuration #1 chosen from 1 choice
[    0.341315] hub 7-0:1.0: USB hub found
[    0.341320] hub 7-0:1.0: 2 ports detected
[    0.341357]   alloc irq_desc for 18 on node -1
[    0.341358]   alloc kstat_irqs on node -1
[    0.341362] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.341368] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.341371] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.341395] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.341427] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.341497] usb usb8: configuration #1 chosen from 1 choice
[    0.341517] hub 8-0:1.0: USB hub found
[    0.341523] hub 8-0:1.0: 2 ports detected
[    0.341601] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.344036] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.349719] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.349729] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.349758] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.349778] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.349795] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.349900] mice: PS/2 mouse device common for all mice
[    0.350085] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.350115] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.350212] device-mapper: uevent: version 1.0.3
[    0.352381] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.353023] device-mapper: multipath: version 1.1.0 loaded
[    0.353026] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.356183] EISA: Probing bus 0 at eisa.0
[    0.356190] Cannot allocate resource for EISA slot 1
[    0.356192] Cannot allocate resource for EISA slot 2
[    0.356194] Cannot allocate resource for EISA slot 3
[    0.356196] Cannot allocate resource for EISA slot 4
[    0.356212] EISA: Detected 0 cards.
[    0.356279] cpuidle: using governor ladder
[    0.356315] cpuidle: using governor menu
[    0.356643] TCP cubic registered
[    0.356764] NET: Registered protocol family 10
[    0.357093] lo: Disabled Privacy Extensions
[    0.357322] NET: Registered protocol family 17
[    0.357362] Using IPI No-Shortcut mode
[    0.357428] PM: Resume from disk failed.
[    0.357440] registered taskstats version 1
[    0.357882]   Magic number: 6:18:533
[    0.357898] bdi 1:11: hash matches
[    0.357964] rtc_cmos 00:06: setting system clock to 2010-08-30 12:31:01 UTC (1283171461)
[    0.357966] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.357968] EDD information not available.
[    0.423755] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.537047] Freeing initrd memory: 7789k freed
[    0.715390] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    0.758983] isapnp: No Plug & Play device found
[    0.759000] Freeing unused kernel memory: 660k freed
[    0.759358] Write protecting the kernel text: 4680k
[    0.759380] Write protecting the kernel read-only data: 1844k
[    0.775137] udev: starting version 151
[    0.932556] usb 2-4: configuration #1 chosen from 1 choice
[    0.962330] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.962353] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.962397] r8169 0000:05:00.0: setting latency timer to 64
[    0.962452]   alloc irq_desc for 27 on node -1
[    0.962454]   alloc kstat_irqs on node -1
[    0.962469] r8169 0000:05:00.0: irq 27 for MSI/MSI-X
[    0.962933] eth0: RTL8168d/8111d at 0xf8092000, 00:03:0d:d1:f3:a6, XID 081000c0 IRQ 27
[    1.009515] ahci 0000:00:1f.2: version 3.0
[    1.009531] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.009572]   alloc irq_desc for 28 on node -1
[    1.009573]   alloc kstat_irqs on node -1
[    1.009584] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.009671] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.009675] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    1.009680] ahci 0000:00:1f.2: setting latency timer to 64
[    1.014038] scsi0 : ahci
[    1.014921] scsi1 : ahci
[    1.017747] scsi2 : ahci
[    1.017865] scsi3 : ahci
[    1.017952] scsi4 : ahci
[    1.018040] scsi5 : ahci
[    1.018083] ata1: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704100 irq 28
[    1.018086] ata2: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704180 irq 28
[    1.018088] ata3: DUMMY
[    1.018089] ata4: DUMMY
[    1.018092] ata5: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704300 irq 28
[    1.018095] ata6: SATA max UDMA/133 abar m2048@0xfe704000 port 0xfe704380 irq 28
[    1.336045] ata6: SATA link down (SStatus 0 SControl 300)
[    1.336067] ata5: SATA link down (SStatus 0 SControl 300)
[    1.500056] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.500074] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.514602] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TM00, max UDMA/100, ATAPI AN
[    1.514616] ata2.00: applying bridge limits
[    1.528706] ata2.00: configured for UDMA/100
[    1.545251] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001J, max UDMA/100
[    1.545254] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.546121] ata1.00: configured for UDMA/100
[    1.546213] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.546337] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.546541] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.546580] sd 0:0:0:0: [sda] Write Protect is off
[    1.546582] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.546602] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.546712]  sda:
[    1.548649] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TM00 PQ: 0 ANSI: 5
[    1.554304] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.554307] Uniform CD-ROM driver Revision: 3.20
[    1.554387] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.554430] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.599140]  sda1 sda2 < sda5 >
[    1.621995] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.969949] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.969953] EXT4-fs (sda1): write access will be enabled during recovery
[    4.398967] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.398976] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085159
[    4.399034] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085152
[    4.399047] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085121
[    4.399058] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085060
[    4.399069] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085244
[    4.399080] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085184
[    4.399086] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085175
[    4.399096] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085167
[    4.399106] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085164
[    4.399112] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085160
[    4.399123] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7085039
[    4.399129] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7080401
[    4.399136] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5112012
[    4.399148] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 5111925
[    4.399160] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3409861
[    4.399181] EXT4-fs (sda1): 15 orphan inodes deleted
[    4.399184] EXT4-fs (sda1): recovery complete
[    4.535960] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   13.280625] udev: starting version 151
[   13.366707] Adding 8954872k swap on /dev/sda5.  Priority:-1 extents:1 across:8954872k 
[   13.426480] lp: driver loaded but no devices found
[   13.528150] Linux agpgart interface v0.103
[   13.739336] rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   13.745815] ieee80211_crypt: registered algorithm 'NULL'
[   13.745818] ieee80211_crypt: registered algorithm 'TKIP'
[   13.745820] ieee80211_crypt: registered algorithm 'CCMP'
[   13.745821] ieee80211_crypt: registered algorithm 'WEP'
[   13.745823] 
[   13.745823] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   13.745825] Copyright (c) 2004-2005, Andrea Merello
[   13.745826] r8180: Initializing module
[   13.745827] r8180: Wireless extensions version 22
[   13.745829] r8180: Initializing proc filesystem
[   13.745853] r8180: Configuring chip resources
[   13.745871] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.745878] r8180 0000:04:00.0: setting latency timer to 64
[   13.749603] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   13.749893] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   13.779799] Linux video capture interface: v2.00
[   13.781691] [drm] Initialized drm 1.1.0 20060810
[   13.793367] r8180: Channel plan is 2
[   13.793369] 
[   13.793371] Dot11d_Init()
[   13.793375] r8180: MAC controller is a RTL8187SE b/g
[   13.793376] r8180: This is a PCI NIC
[   13.795819] r8180: usValue is 0x0
[   13.795820] 
[   13.851957] r8180: EEPROM version 104
[   13.856842] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   13.857331] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   13.874465] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input6
[   13.874512] usbcore: registered new interface driver uvcvideo
[   13.874515] USB Video Class driver (v0.1.0)
[   13.920960] type=1505 audit(1283171475.062:2):  operation="profile_load" pid=629 name="/sbin/dhclient3"
[   13.921579] type=1505 audit(1283171475.062:3):  operation="profile_load" pid=629 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.921991] type=1505 audit(1283171475.062:4):  operation="profile_load" pid=629 name="/usr/lib/connman/scripts/dhclient-script"
[   13.959079] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.011383] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.011388] i915 0000:00:02.0: setting latency timer to 64
[   14.042193]   alloc irq_desc for 29 on node -1
[   14.042196]   alloc kstat_irqs on node -1
[   14.042204] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[   14.042210] [drm] set up 31M of stolen space
[   14.205305] r8180: IRQ 17
[   14.205977] r8180: Driver probe completed
[   14.205978] 
[   14.292201] type=1505 audit(1283171475.434:5):  operation="profile_load" pid=758 name="/usr/share/gdm/guest-session/Xsession"
[   14.295731] type=1505 audit(1283171475.434:6):  operation="profile_replace" pid=759 name="/sbin/dhclient3"
[   14.300749] type=1505 audit(1283171475.442:7):  operation="profile_replace" pid=759 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.301088] type=1505 audit(1283171475.442:8):  operation="profile_replace" pid=759 name="/usr/lib/connman/scripts/dhclient-script"
[   14.307475] type=1505 audit(1283171475.446:9):  operation="profile_load" pid=760 name="/usr/bin/evince"
[   14.351630] type=1505 audit(1283171475.490:10):  operation="profile_load" pid=760 name="/usr/bin/evince-previewer"
[   14.363575] type=1505 audit(1283171475.502:11):  operation="profile_load" pid=760 name="/usr/bin/evince-thumbnailer"
[   14.885543] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   14.922634] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.984138] fb0: inteldrmfb frame buffer device
[   14.984141] registered panic notifier
[   15.061252] ppdev: user-space parallel port driver
[   15.384126] acpi device:06: registered as cooling_device1
[   15.384328] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   15.384375] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.384400] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.385951] vga16fb: initializing
[   15.385954] vga16fb: mapped to 0xc00a0000
[   15.385957] vga16fb: not registering due to another framebuffer present
[   15.386531]   alloc irq_desc for 22 on node -1
[   15.386533]   alloc kstat_irqs on node -1
[   15.386539] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.386576] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.499398] hda_codec: ALC662 rev1: BIOS auto-probing.
[   15.500707] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   15.543901] Console: switching to colour frame buffer device 170x48
[ 1208.832187] PM: Syncing filesystems ... done.
[ 1208.848063] PM: Preparing system for mem sleep
[ 1208.848067] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 1208.851370] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 1208.851426] PM: Entering mem sleep
[ 1208.851438] Suspending console(s) (use no_console_suspend to debug)
[ 1208.851739] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1208.902104] sd 0:0:0:0: [sda] Stopping disk
[ 1209.506689] PM: suspend of drv:sd dev:0:0:0:0 complete after 654.946 msecs
[ 1209.887059] PM: suspend of drv:psmouse dev:serio4 complete after 366.946 msecs
[ 1210.244048] PM: suspend of drv:atkbd dev:serio0 complete after 356.977 msecs
[ 1210.246163] ACPI handle has no context!
[ 1210.246295] r8180 0000:04:00.0: PCI INT A disabled
[ 1210.340061] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 1210.340070] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 1210.340079] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 1210.340087] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1210.548117] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1210.564049] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.948 msecs
[ 1210.564058] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 1210.564066] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[ 1210.564074] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 1210.564083] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1210.648267] PM: suspend of devices complete after 1796.696 msecs
[ 1210.648270] PM: suspend devices took 1.800 seconds
[ 1210.648725] r8169 0000:05:00.0: PME# enabled
[ 1210.696229] PM: late suspend of devices complete after 47.955 msecs
[ 1210.696372] ACPI: Preparing to enter system sleep state S3
[ 1210.732130] Disabling non-boot CPUs ...
[ 1210.732180] Extended CMOS year: 2000
[ 1210.732180] Back to C!
[ 1210.732180] CPU0: Thermal monitoring enabled (TM1)
[ 1210.732180] Extended CMOS year: 2000
[ 1210.732180] ACPI: Waking up from system sleep state S3
[ 1210.844172] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 1210.844183] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 1210.844210] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 1210.844244] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844285] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844326] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844373] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 1210.844408] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1210.844428] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1210.844435] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100102)
[ 1210.844467] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[ 1210.844479] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f001)
[ 1210.844484] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f800)
[ 1210.844489] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[ 1210.844494] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30200)
[ 1210.844502] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1210.844508] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 1210.844555] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x40205)
[ 1210.844567] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf3f1f201)
[ 1210.844573] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
[ 1210.844582] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1210.844588] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 1210.844636] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x4040a)
[ 1210.844648] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf7f1f401)
[ 1210.844655] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
[ 1210.844664] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1210.844670] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 1210.844731] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844771] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844811] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 1210.844859] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 1210.844886] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
[ 1210.844897] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 1210.844902] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 1210.844907] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[ 1210.844919] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1210.844996] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 1210.845019] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 1210.845071] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xc0000004)
[ 1210.845110] r8180 0000:04:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[ 1210.845134] r8180 0000:04:00.0: restoring config space at offset 0x5 (was 0x0, writing 0xfa000000)
[ 1210.845141] r8180 0000:04:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x3001)
[ 1210.845147] r8180 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1210.845155] r8180 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 1210.845216] r8169 0000:05:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
[ 1210.845234] r8169 0000:05:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xf400000c)
[ 1210.845242] r8169 0000:05:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xf600000c)
[ 1210.845250] r8169 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x4001)
[ 1210.845257] r8169 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1210.845265] r8169 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 1210.845654] PM: early resume of devices complete after 1.594 msecs
[ 1210.902220] i915 0000:00:02.0: setting latency timer to 64
[ 1211.044198] PM: resume of drv:i915 dev:0000:00:02.0 complete after 141.985 msecs
[ 1211.044212] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1211.044218] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1211.044242] usb usb3: root hub lost power or was reset
[ 1211.044263] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 1211.044269] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 1211.044291] usb usb4: root hub lost power or was reset
[ 1211.044311] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 1211.044317] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 1211.044339] usb usb5: root hub lost power or was reset
[ 1211.044360] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 1211.044366] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 1211.044379] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1211.044385] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1211.044417] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1211.044423] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1211.044446] usb usb6: root hub lost power or was reset
[ 1211.044466] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 1211.044472] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1211.044494] usb usb7: root hub lost power or was reset
[ 1211.044514] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 1211.044519] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1211.044542] usb usb8: root hub lost power or was reset
[ 1211.044561] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1211.044567] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 1211.044593] pci 0000:00:1e.0: setting latency timer to 64
[ 1211.044609] ahci 0000:00:1f.2: setting latency timer to 64
[ 1211.044730] r8180 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1211.044746] r8169 0000:05:00.0: PME# disabled
[ 1211.204048] PM: resume of drv:usb dev:usb2 complete after 131.971 msecs
[ 1211.316059] usb 2-4: reset high speed USB device using ehci_hcd and address 2
[ 1211.364051] ata6: SATA link down (SStatus 0 SControl 300)
[ 1211.364075] ata5: SATA link down (SStatus 0 SControl 300)
[ 1211.504771] PM: resume of drv:usb dev:2-4 complete after 297.035 msecs
[ 1211.504815] sd 0:0:0:0: [sda] Starting disk
[ 1211.528044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1211.790103] ata2.00: configured for UDMA/100
[ 1212.368051] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1212.369583] ata1.00: configured for UDMA/100
[ 1212.399047] PM: resume of drv:sd dev:0:0:0:0 complete after 894.232 msecs
[ 1212.399241] PM: resume of devices complete after 1553.558 msecs
[ 1212.399330] PM: resume devices took 1.552 seconds
[ 1212.399357] PM: Finishing wakeup.
[ 1212.399358] Restarting tasks ... done.
[ 1212.689621] r8180: Bringing up iface
[ 1212.888086] r8180: Card successfully reset
[ 1213.625992] r8180: WIRELESS_MODE_G
[ 1213.625993] 
[ 1213.960262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1213.975935] r8169: eth0: link up
[ 1224.228024] eth0: no IPv6 routers present
[ 1253.124645] r8169: eth0: link down
[ 1278.637617] r8169: eth0: link up
[ 3349.731029] r8169: eth0: link down
[ 3383.293848] r8169: eth0: link up


**Code: $ sudo lshw -C network**
> 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 22
       serial: 00:24:21:c6:77:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:17 ioport:3000(size=256) memory:fa000000-fa003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 00:03:0d:d1:f3:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.67 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:4000(size=256) memory:f6000000-f6000fff(prefetchable) memory:f4000000-f4003fff(prefetchable) memory:f4020000-f403ffff(prefetchable)


**Code: $ iwlist scan**
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results


**Code: $ uname -mr**
> 2.6.32-24-generic i686

**Code: $ sudo /etc/init.d/networking restart**
> * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]


Thanks and kind regards,
Ben

---

### Post by xX(TFM)Xx on 2010-09-11
From What I understand it is solved by going back to karmic 9.10  ):P

---

### Post by knuckleheadTech on 2010-10-12
I am researching how to get this to work in Arch and am not impressed with the answer given. Since I don't see any other responses here that are helpful I will post my results if I find any in my digging.
 
If you have already solved your problem please post your results.
 
xX(TFM)Xx - If there is no way to get this to work in 10.04, or now 10.10 then you could say that, but to give an answer like that is not the way to treat new Linux users.

---

### Post by snippyv on 2011-03-19
I have an Advent with a RTL8187Se....and had problems with wifi dropping.

I solved it by using the Ndiswrapper GUI and the Windows XP driver.

No problems since.

---

